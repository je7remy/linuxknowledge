---
tipo: teoria
tags: [websocket, protocolos, web, autenticacion, entity-page]
actualizado: 2026-10-18
---

# WebSocket

WebSocket mantiene una comunicación bidireccional basada en mensajes sobre una conexión persistente. En la negociación HTTP/1.1 de los retos documentados se solicita `Upgrade: websocket`; después se intercambian frames WebSocket, no JSON crudo directamente sobre TCP.

## Reconstruir el protocolo de aplicación

1. Localizar URL, ruta y negociación en el cliente o en sus cadenas.
2. Identificar el saludo, la respuesta y los identificadores de sesión.
3. Inventariar tipos de mensaje, campos, errores y acciones privilegiadas.
4. Separar conexión aceptada, usuario autenticado y autorización del comando.
5. Conservar la respuesta que demuestra el efecto, no solo que el envío terminó.

## Aplicación entre rondas de PentraZE

| Caso | Cliente analizado | Mensajes clave | Fallo de seguridad |
|---|---|---|---|
| [[Writeup - Eco Persistente]] | JavaScript público | `session.hello`, `auth.login`, `vault.read` | Un objeto NoSQL en `accessKey` permitió obtener rol administrativo. |
| [[Writeup - Data Del Más Allá]] | Windows PE32+ | `HELLO`, `HELLO_ACK`, `ADMIN_CMD` | El cliente contenía el secreto necesario para reconstruir el token administrativo. |

La biblioteca `websockets` usada en Eco y `websocket-client` usada en Data son paquetes diferentes. En Data, la importación es `import websocket`; no conviene sustituirla mecánicamente por `websockets`.

## Autorización por mensaje

Negociar WebSocket no concede privilegios. El servidor debe validar identidad, rol, esquema y acción de cada mensaje, así como vigencia y revocación de la sesión. TLS (`wss://`) protege el transporte, pero no corrige una credencial expuesta ni una comparación de autenticación vulnerable.

## Navegación

- ⬆️ Carpeta: [[_Vista Curada]]
- 🏠 [[MOC - Web Pentesting OWASP]]

## Relacionadas

- [[Authentication]] — identidad, sesiones y autorización.
- [[1- Protocolo HTTP]] — negociación inicial.
- [[Networking]] — TCP frente al protocolo de aplicación.
- [[Reversing - de leer código fuente a desensamblar binarios]] — reconstrucción desde un cliente compilado.
