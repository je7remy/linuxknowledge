---
tipo: laboratorio
tags: [ctf, pentraze, crypto, easy]
Plataforma: "Pentraze CTF"
Categoría: "Crypto"
Dificultad: "Easy"
Estado: "Completado"
Puntos: "50"
Flag: "PENTRAZE{994f2f09964d40c5f2e164cad7b5d19a242644b8225b7f93b741cae65b39a9a7}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Crypto|Crypto]]
- **Dificultad:** [[CTF - Easy|Easy]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 50

# Writeup - MATRIOSKA

> [!info] Objetivo
> Descifrar diez muñecas anidadas; cada capa entrega la pista o la llave de la siguiente y la décima contiene la flag.

- **Target:** `http://34.135.253.132:35753`
- **Categoría de la clasificación:** Crypto
- **También toca:** Web/API, sesión y ofuscación de primer nivel
- **Dificultad de la clasificación final:** Easy
- **Nota de la ficha original:** la ficha descriptiva del reto lo clasificaba como Media; la lista final por dificultad lo cataloga como Easy.

## Resumen rápido de la cadena de ataque

1. `matrioska.js` revela la API y el nombre de campo `layer`.
2. Las capas 1–9 se resuelven con codificaciones, cifrados clásicos, transposición y una clave derivada de la capa anterior.
3. La capa 9 entrega `key = m4tr10sk4-nucl30` e `IV = v3ct0r-1n1c14l-0`.
4. La capa 10 se descifra con [[AES-CBC]] AES-128-CBC.
5. Se envía el plaintext descifrado a `POST /api/solve` y la respuesta devuelve `flag`.

## Vulnerabilidades explotadas

- **Divulgación del contrato de la API y del estado del juego** en el JavaScript público.
- **Rate limiting demasiado débil para la superficie interactiva:** los intentos incorrectos provocaban bloqueos, pero el progreso y los mensajes permitían automatizar la resolución.
- **Material criptográfico derivado de respuestas previas:** la llave y el IV se entregaban en una capa anterior, sin separación de secretos.
- **Estado de sesión débilmente aislado:** el progreso dependía de `PHPSESSID` y la API aceptaba el flujo de capas sin una autorización adicional visible.
- **Ausencia de una separación clara entre pistas y secretos de producción** en la respuesta de la interfaz.

## Paso a paso técnico

### API y reconocimiento

```text
GET  /api/status
GET  /api/doll/<N>
POST /api/solve  {"layer": N, "answer": "..."}
```

El progreso depende de `PHPSESSID`; todas las peticiones deben usar la misma sesión. El JavaScript `/static/matrioska.js` mostró que la respuesta correcta activa `victory` y entrega `r.flag`.

El servidor tenía un rate limiting agresivo: tres errores bloqueaban una muñeca durante 180 segundos. La estrategia fue `DELAY >= 5s`, pocas solicitudes y una sesión persistente.

## Capas de la muñeca

| Capa | Nombre | Técnica | Respuesta o resultado |
|---:|---|---|---|
| 1 | Semilla | [[ROT13]] | `bienvenido a la matrioska la primera cascara es solo el envoltorio` |
| 2 | Hilo | Base64 | `la segunda muneca es hilo que se desenrolla en base sesenta y cuatro` |
| 3 | Cinta | Base32 | `la tercera es cinta mayusculas y numeros del dos al siete` |
| 4 | Corteza | Hex | `la cuarta es corteza pares hexadecimales que esconden letras` |
| 5 | Rueda | [[Caesar Cipher]] | `la quinta es rueda gira cada letra siete pasos adelante` |
| 6 | Espejo | [[ROT47]] | `el espejo devuelve todo la llave siguiente es matrioska guardala bien` |
| 7 | Llave | [[Vigenère Cipher]] | `la septima es llave busca la palabra que abre la trenza` |
| 8 | Chispa | XOR de 1 byte | `la octava es chispa un solo byte la enciende` |
| 9 | Trenza | [[Rail Fence Cipher]] | `la novena es trenza de tres caminos llave m4tr10sk4-nucl30 centinela v3ct0r-1n1c14l-0` |
| 10 | Núcleo | [[AES-CBC]] | plaintext descifrado = flag |

Las pistas relevantes fueron: “13” para ROT13, el alfabeto Base64/Base32, pares hexadecimales, el desplazamiento de César, ROT47, la palabra `matrioska` como clave Vigenère, los tres raíles y finalmente la llave/IV de 16 bytes.

El ciphertext de la capa 10 era:

```text
fef3f1625a58cb66a7ab3a8f7254cbd3464cf12f5e3c9692dea2d477745559261de57d5cc082737c4a0426984da6846532913e8a04ad4bde617a7bfd7315d053b02d4ba98e37432177c5a9c4b4e188ce
```

La llave y el IV fueron, respectivamente, `m4tr10sk4-nucl30` y `v3ct0r-1n1c14l-0`.

## Script de resolución

```python
#!/usr/bin/env python3
import time

import requests
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad

BASE = "http://34.135.253.132:35753"
DELAY = 5
s = requests.Session()

ANSWERS = {
    1: "bienvenido a la matrioska la primera cascara es solo el envoltorio",
    2: "la segunda muneca es hilo que se desenrolla en base sesenta y cuatro",
    3: "la tercera es cinta mayusculas y numeros del dos al siete",
    4: "la cuarta es corteza pares hexadecimales que esconden letras",
    5: "la quinta es rueda gira cada letra siete pasos adelante",
    6: "el espejo devuelve todo la llave siguiente es matrioska guardala bien",
    7: "la septima es llave busca la palabra que abre la trenza",
    8: "la octava es chispa un solo byte la enciende",
    9: "la novena es trenza de tres caminos llave m4tr10sk4-nucl30 centinela v3ct0r-1n1c14l-0",
}

for layer, answer in ANSWERS.items():
    response = s.post(
        f"{BASE}/api/solve",
        json={"layer": layer, "answer": answer},
        timeout=15,
    )
    print(layer, response.status_code, response.text[:160])
    time.sleep(DELAY)

# La capa 10 requiere leer el ciphertext del servidor, descifrarlo y enviarlo.
doll = s.get(f"{BASE}/api/doll/10", timeout=15).json()
ciphertext = bytes.fromhex(doll["ct"])
key = b"m4tr10sk4-nucl30"
iv = b"v3ct0r-1n1c14l-0"
plaintext = unpad(
    AES.new(key, AES.MODE_CBC, iv).decrypt(ciphertext),
    AES.block_size,
).decode()

final = s.post(
    f"{BASE}/api/solve",
    json={"layer": 10, "answer": plaintext},
    timeout=15,
)
print(final.json().get("flag", plaintext))
```

Para una sesión que pueda bloquear una capa por error, no se debe insistir: hay que esperar el `retry_after` y mantener la misma cookie. La flag final se obtiene en `r.flag` cuando `victory` es verdadero.

## Flag

```text
PENTRAZE{994f2f09964d40c5f2e164cad7b5d19a242644b8225b7f93b741cae65b39a9a7}
```

## Lecciones aprendidas y mitigar

- Inspeccionar el frontend puede ahorrar mucho tiempo y revelar el contrato real de la API, pero no sustituye la validación del servidor.
- Las pistas encadenadas son un mapa de dependencias: cada respuesta debe conservarse como contexto de la siguiente.
- Aplicar decodificaciones y descifrados en el orden indicado, verificando la legibilidad antes de continuar.
- El rate limiting debe ser tolerante a errores de usuario, pero no permitir fuerza bruta: usar backoff, límites por sesión y telemetría.
- Mantener el estado de progresión en servidor y asociarlo a una sesión robusta; no aceptar `layer` o `answer` sin validar el tipo, estado y autorización.
- Para el desafío final, proteger la clave y el IV, rotarlos y usar una API de datos que no entregue material criptográfico a clientes no autorizados.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Crypto]]
- ⬅️ Anterior: [[Writeup - Xouroboros|Xouroboros]]
- ➡️ Siguiente: [[Writeup - Factura Fantasma|Factura Fantasma]]

## Relacionadas

- [[Cryptography]] — técnicas clásicas y modernas aplicadas en cascada.
- [[AES-CBC]] — descifrado de la capa final.
- [[Web API Security]] — contrato, sesión y validación de la API.
