---
tipo: laboratorio
Plataforma: Pentraze CTF
Ronda: 2
Fuente: '[[assets/PentraZE-2026-ronda-2/ctf.docx]]'
actualizado: 2026-10-18
tags: [ctf, pentraze, ronda-2, pwn, reverse-engineering, websocket, sha256, xor]
Categoría: PWN
Estado: Completado
Flag: PENTRAZE{d270e5e966d7302319843571d7f5a36426d8153b9f6c09552ec8d1285d0bb56f}
Estado_flag: Documentada en la fuente
---

- **Categoría Principal:** [[CTF - Binary Exploitation|PWN]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Ronda:** [[PentraZE CTF 2026 - Ronda 2|Segunda ronda]]
- **Estado:** Completado

# Writeup - Data Del Más Allá

> [!info] Objetivo
> Reconstruir desde el cliente Windows el token de sesión administrativo y solicitar la flag mediante WebSocket.

## Resumen rápido de la cadena de ataque

1. `file` identificó PE32+ x86-64; `strings` reveló mensajes administrativos y negociación WebSocket.
2. Se descartó la falsa flag de `PUBLIC_INFO` y se investigaron longitudes de `DATA` sin demostrar corrupción de heap.
3. Un error de autenticación reveló un token de 16 caracteres derivado de la sesión.
4. El análisis estático identificó SHA-256, el formato `%u%s` y XOR con `0x5A`.
5. Se recuperó `inferno_admin_2024` y se reconstruyó `SHA256(session_id_decimal || secret).hexdigest()[:16]`.
6. `HELLO_ACK → ADMIN_CMD(get_flag)` devolvió la flag real.

## Vulnerabilidades y hallazgos

- Secreto de autorización embebido en un cliente distribuido; XOR reversible no lo mantiene confidencial.
- Token administrativo reproducible desde un identificador de sesión público y el secreto recuperado.
- [[WebSocket]] transporta mensajes que requieren [[Authentication|autenticación y autorización]] por acción.
- [[Reversing - de leer código fuente a desensamblar binarios|Análisis estático PE32+]] y [[Cryptography|SHA-256 y XOR]]. **PWN es la categoría del evento; no hay explotación de heap confirmada.**

## Contexto documentado

Reto resuelto · Flag verificada

- **Categoría:** PWN
- **Autor:** Br0nco
- **Evento:** Pentraze CTF 2026
- **Sistema analizado:** Windows PE32+ x86-64
- **Técnicas:** Ingeniería inversa, análisis de WebSocket, desofuscación XOR, reconstrucción de SHA-256 y autenticación basada en sesiones.
- **Herramientas:** Fedora Linux, Python, objdump, strings, file y websocket-client.

## Paso a paso técnico

### 1. Descripción del desafío

Un cliente. Un servidor. Un heap que nadie auditó. El sistema sabe cuando lo observan. Demuestra que eres humano.

El reto proporcionaba un ejecutable llamado DataMasAlla.exe y un servicio accesible mediante TCP.

El objetivo consistía en analizar el funcionamiento del cliente, comprender su protocolo de comunicación y conseguir la flag protegida por el servidor.

Aunque la descripción sugería una posible vulnerabilidad de heap y mecanismos antidepuración, la solución demostrada terminó utilizando ingeniería inversa del mecanismo de autenticación administrativa, sin necesidad de explotar el heap.

### 2. Reconocimiento inicial

La primera conexión se realizó mediante:

```bash
nc -v 34.135.253.132 36154
```

El servidor aceptó la conexión, pero no mostró ningún banner ni respondió a comandos de texto.

Posteriormente, se identificó el archivo descargado:

```bash
file DataMasAlla.exe
```

Resultado:

```text
PE32+ executable for MS Windows 5.02 (GUI),
x86-64 (stripped to external PDB), 10 sections
```

Se trataba de un ejecutable de Windows de 64 bits, por lo que se inició un análisis estático en lugar de ejecutarlo directamente en Fedora.

### 3. Análisis de cadenas del ejecutable

Se utilizó strings para identificar mensajes, comandos y datos relevantes:

```bash
strings -a -n 4 DataMasAlla.exe
```

Entre los hallazgos destacaron:

```text
{"type":"PUBLIC_INFO"}

{"type":"HELLO","version":"1.3.3.7",
"client_id":"deadbeef-cafe-1337-b00b-c0ffee001337",
"client_ptr":"0x%llx"}

{"type":"DATA","payload_size":%u,
"data_len":%u,"data":"%s"}

{"type":"ADMIN_CMD","token":"%s","cmd":"get_flag"}
```

También se encontraron cadenas relacionadas con depuración y memoria, entre ellas IsDebuggerPresent, x64dbg.exe e InfernoAlloc.

La presencia de ADMIN_CMD con get_flag reveló una posible vía para obtener directamente el secreto.

### 4. Identificación del protocolo WebSocket

Al revisar los bytes próximos a las cadenas de comunicación, se encontró una solicitud HTTP con negociación WebSocket:

```http
GET / HTTP/1.1
Host: %s:%d
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Sec-WebSocket-Version: 13
```

Esto explicó por qué el servidor había cerrado una conexión anterior en la que se envió JSON directamente sobre TCP.

El flujo correcto de comunicación era:

```text
Conexión TCP
Negociación WebSocket
HELLO → HELLO_ACK
Obtención del Session ID
Cálculo del token administrativo
ADMIN_CMD → FLAG
```

Con la biblioteca websocket-client se consiguió establecer la comunicación correctamente:

```python
import websocket

ws = websocket.create_connection(
    "ws://34.135.253.132:36154/",
    timeout=8)
```

### 5. Descubrimiento de una flag falsa

Durante el reconocimiento se envió:

```json
{"type":"PUBLIC_INFO"}
```

El servidor respondió con información pública y una supuesta flag:

```json
{
  "type": "PUBLIC_INFO_ACK",
  "version": "1.3.3.7",
  "flag": "CTF{th1s_1s_n0t_th3_r34l_fl4g_k33p_d1gg1ng}",
  "status": "operational"
}
```

El contenido indicaba expresamente que no era la flag real y que debíamos continuar investigando.

Por tanto, se descartó como objetivo final.

### 6. Investigación del heap

Se analizaron los parámetros payload_size y data_len del comando DATA.

En una prueba se enviaron:

```json
{
  "type": "DATA",
  "payload_size": 8,
  "data_len": 64,
  "data": "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
}
```

El servidor respondió:

```json
{
  "type": "DATA_ACK",
  "status": "SUCCESS",
  "bytes_processed": 64,
  "checksum_verified": true
}
```

El servidor aceptó que la longitud declarada de los datos fuera superior al tamaño indicado del payload.

Este comportamiento era sospechoso y compatible con una posible validación insuficiente. Sin embargo, no se demostró una corrupción de memoria ni se utilizó una vulnerabilidad de heap en la explotación final.

La investigación continuó por la vía del comando administrativo.

### 7. Análisis de la autenticación administrativa

Inicialmente se probó el comando ADMIN_CMD utilizando una cadena encontrada en el ejecutable:

```json
{
  "type": "ADMIN_CMD",
  "token": "admin_token_2024_dev",
  "cmd": "get_flag"
}
```

El servidor respondió:

```json
{
  "type": "ERROR",
  "code": 403,
  "msg": "Token inválido",
  "expected_length": 16,
  "received_length": 20,
  "hint": "El token se deriva de datos de la sesión"
}
```

Esta respuesta reveló dos condiciones fundamentales: el token debía tener 16 caracteres y se derivaba de datos de la sesión actual.

Posteriormente, el análisis del código permitió identificar una función que construía el mensaje administrativo:

```asm
140005953: push rsi
140005954: push rbx
140005955: sub  rsp,0x128
14000595f: mov  r9,rdx
140005967: lea  r8,[rip+0x92aa]
140005976: call 0x14000c310
140005981: call 0x14000570f
```

Esta función recibía un token ya preparado, lo insertaba en el formato JSON y enviaba el mensaje.

### 8. Reconstrucción del algoritmo SHA-256

El análisis de otra rutina reveló las constantes iniciales características de SHA-256:

```asm
mov DWORD PTR [rsp+0x50],0x6a09e667
mov DWORD PTR [rsp+0x54],0xbb67ae85
mov DWORD PTR [rsp+0x58],0x3c6ef372
mov DWORD PTR [rsp+0x5c],0xa54ff53a
mov DWORD PTR [rsp+0x60],0x510e527f
mov DWORD PTR [rsp+0x64],0x9b05688c
mov DWORD PTR [rsp+0x68],0x1f83d9ab
mov DWORD PTR [rsp+0x6c],0x5be0cd19
```

La rutina procesaba una entrada formada por un valor numérico y una cadena interna. Después convertía los primeros 8 bytes del digest en 16 caracteres hexadecimales.

También se recuperó el formato:

```text
%u%s
```

Esto indicaba una concatenación del identificador de sesión en decimal con una cadena secreta.

### 9. Desofuscación de la clave mediante XOR

La clave no estaba almacenada directamente como texto legible. Se encontraba ofuscada mediante una operación XOR con el byte 0x5A.

El desensamblado contenía:

```asm
14000527a: mov eax,0x33
14000528e: xor eax,0x5a
```

El primer carácter se calculaba así:

$$
0x33\oplus0x5A=0x69
$$

0x69 corresponde a la letra i en ASCII.

Al reconstruir la secuencia completa, se obtuvo:

```text
inferno_admin_2024
```

La cadena tenía 18 bytes.

#### Script de extracción

> [!note] Formato reconstruido; extracción no reejecutada
> Se restauraron únicamente espacios y saltos de línea. Los offsets y el salto `raw[2:]` se conservan tal como aparecen en el Word; su correspondencia con el binario requiere cotejar `DataMasAlla.exe`. La longitud de 18 bytes y los dos tokens publicados sí se comprobaron con cálculos locales independientes, sin ejecutar este script.

```python
from pathlib import Path
import hashlib

data = Path("DataMasAlla.exe").read_bytes()
IMAGE_BASE = 0x140000000
RDATA_VA = 0xE000
RDATA_OFFSET = 0xBC00

def offset_pe(va):
    return RDATA_OFFSET + (va - IMAGE_BASE - RDATA_VA)

pos = offset_pe(0x14000EC4F)
raw = data[pos:pos + 128]
secret = bytearray([0x33 ^ 0x5A])
for b in raw[2:]:
    if b == 0:
        break
    secret.append(b ^ 0x5A)

print("Clave:", secret.decode())
print("Longitud:", len(secret))
session_id = 1018236300
message = str(session_id).encode() + bytes(secret)
token = hashlib.sha256(message).hexdigest()[:16]
print("Entrada:", message)
print("Token:", token)
```

Salida obtenida:

```text
Clave: inferno_admin_2024
Longitud: 18
Entrada: b'1018236300inferno_admin_2024'
Token: a075a8271175dcc8
```

### 10. Fórmula del token administrativo

Tras reconstruir el algoritmo, se obtuvo:

$$
\boxed{\text{Token}=\operatorname{SHA256}(\text{session\_id}\Vert\text{secret})_{\text{hex}}[:16]}
$$

Donde:

- session_id es el identificador decimal asignado por HELLO_ACK.

- secret es la cadena inferno_admin_2024.

- [:16] indica los primeros 16 caracteres hexadecimales del SHA-256.

Este token debe calcularse nuevamente para cada sesión, porque el identificador cambia.

La hipótesis fue finalmente validada cuando el servidor aceptó el token y devolvió una respuesta de tipo FLAG.

### 11. Exploit final

El siguiente script reproduce la explotación confirmada. Establece una sesión WebSocket, obtiene el session_id, genera el token administrativo y solicita la flag.

> [!warning] Fragmento final sin preámbulo
> El documento no incluye aquí los imports de `json`/`hashlib`, la asignación de `SECRET` ni la creación de `ws`. La conexión figura en un ejemplo anterior, pero no se ha unido a este fragmento como si fuese el script original completo. La sintaxis del fragmento es válida; ejecutarlo aisladamente produciría nombres no definidos.

```python
def request(data):
    ws.send(json.dumps(data))
    response = ws.recv()
    print("[RECV]", response)
    return json.loads(response)

try:
    print("[1] Estableciendo sesión")
    hello = request({
        "type": "HELLO",
        "version": "1.3.3.7",
        "client_id": "deadbeef-cafe-1337-b00b-c0ffee001337",
        "client_ptr": "0x0"
    })
    if hello.get("type") != "HELLO_ACK":
        raise RuntimeError("No se recibió HELLO_ACK")
    session_id = int(hello["session_id"])
    print("[2] Calculando token")
    message = f"{session_id}{SECRET}".encode()
    token = hashlib.sha256(message).hexdigest()[:16]
    print("[+] Session ID:", session_id)
    print("[+] Token:", token)
    print("[3] Solicitando flag")
    result = request({
        "type": "ADMIN_CMD",
        "token": token,
        "cmd": "get_flag"
    })
    if result.get("type") == "FLAG":
        print("\n[+] FLAG:", result.get("data"))
    else:
        print("\n[-] Respuesta:", result)
finally:
    ws.close()
```

Se ejecutó mediante:

```bash
python3 obtener_flag.py
```

### 12. Obtención de la flag real

La ejecución final produjo:

```text
[1] Estableciendo sesión
[RECV] {"type": "HELLO_ACK", "session_id": 3043438582,
"debug_ptr": "0x7fd8b5e04ce9", "client_echo": "0x0",
"server_time": 1792167329,
"motd": "Data del Más Allá v1.0"}

[2] Calculando token
[+] Session ID: 3043438582
[+] Token: 5297b1613add45e6

[3] Solicitando flag
[RECV] {"type": "FLAG",
"data": "PENTRAZE{d270e5e966d7302319843571d7f5a36426d8153b9f6c09552ec8d1285d0bb56f}"}
```

El tipo de respuesta FLAG confirmó que el servidor aceptó el token generado y entregó el secreto protegido.

### 13. Conclusión

Data Del Más Allá se resolvió mediante ingeniería inversa del cliente Windows y reconstrucción de un mecanismo de autenticación basado en SHA-256.

El problema de seguridad fundamental consistía en que el ejecutable distribuido al cliente contenía una clave interna ofuscada mediante XOR reversible. El token administrativo podía reproducirse utilizando esa clave y el identificador de sesión proporcionado por el propio servidor.

Aunque se encontraron indicios de un posible problema de gestión de memoria dinámica, no fue necesario explotar el heap. Tampoco fue necesario utilizar debug_ptr.

La explotación consistió en comprender el protocolo WebSocket, recuperar la clave, reproducir el algoritmo de token y enviar ADMIN_CMD con get_flag.

Resultado: acceso al comando administrativo conseguido y flag real obtenida.

La principal lección de este reto es que una clave secreta incorporada en un ejecutable cliente no puede considerarse confidencial. Ofuscarla mediante XOR no impide su recuperación mediante análisis estático, y utilizarla para derivar tokens privilegiados puede comprometer completamente el mecanismo de autorización.


## Flag

```text
PENTRAZE{d270e5e966d7302319843571d7f5a36426d8153b9f6c09552ec8d1285d0bb56f}
```

## Lecciones aprendidas y mitigar

- No colocar secretos de autorización global en clientes; la ofuscación no establece una frontera de confianza.
- El identificador de sesión no es una credencial administrativa. El servidor debe mantener y verificar los permisos del usuario.
- Usar mecanismos estándar de sesión, caducidad, revocación y verificación de mensajes privilegiados; cualquier clave de autenticación debe permanecer en el lado confiable.
- Un hash SHA-256 correcto puede formar parte de un diseño de autorización inseguro: la debilidad estaba en quién podía calcular el token.
- Las mitigaciones son conclusiones editoriales del caso; el documento no incluye una implementación corregida.

## Evidencia y revisión documental

El ejemplo de conexión, el extractor XOR y el fragmento final perdieron saltos de línea en Word; la reconstrucción conserva todos los caracteres no blancos. El script final sigue incompleto por ausencia de preámbulo. Los dos tokens del registro, el XOR inicial y la longitud del secreto se cotejaron mediante operaciones locales; no se ejecutó `DataMasAlla.exe` ni se conectó al servicio.

Fuente conservada: [[assets/PentraZE-2026-ronda-2/ctf.docx|ctf.docx original]]. Las descripciones, pruebas, payloads y salidas anteriores proceden de ese documento; no se han reejecutado. Las relaciones y mitigaciones adicionales son síntesis editorial. El Word no contiene imágenes incrustadas.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🏠 MOC: [[PentraZE CTF 2026 - MOC]]
- 🗂️ Ronda: [[PentraZE CTF 2026 - Ronda 2]]
- 🗂️ Categoría: [[CTF - Binary Exploitation]]
- ⬅️ Anterior: [[Writeup - SMBiablo]]

## Relacionadas

- [[Writeup - Eco Persistente]] — reutiliza descubrimiento de mensajes WebSocket y validación de respuestas; allí el acceso admin se obtuvo por un operador NoSQL y aquí por reconstrucción del token.
- [[Writeup - SoftDat Technology]] — los secretos accesibles desde el cliente comprometen administración: token expuesto en JavaScript frente a secreto XOR dentro de PE.
- [[Writeup - Xouroboros]] — la operación XOR es reversible en ambos casos, pero aquí desofusca un secreto fijo y allí recupera un keystream reutilizado; no son la misma vulnerabilidad.
- [[Writeup - SMBiablo]] — comparar ELF/PE, reconstrucción de protocolo y evidencia necesaria para confirmar corrupción de memoria.
- [[Identificar codificaciones, cifrados y hashes]] — hexadecimal del digest y truncamiento a 16 caracteres; el token no se obtuvo invirtiendo SHA-256.
