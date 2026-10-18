---
tipo: teoria
tags: [sql, sqli, web, pentesting, entity-page]
actualizado: 2026-10-18
---

# SQL Injection

La inyección SQL aparece cuando una entrada controlada por el usuario altera la estructura de una consulta. El impacto depende del contexto sintáctico, del motor, del controlador y de los permisos de la cuenta SQL. No toda inyección permite las mismas operaciones.

## UNION, expresiones y sentencias apiladas

- **UNION SELECT:** combina resultados compatibles en número y tipos de columnas. Sirve para observar datos a través de una consulta existente; no demuestra por sí solo capacidad de escritura.
- **Expresiones en ORDER BY:** un parámetro de ordenación puede admitir expresiones donde se esperaba un nombre de columna. Los valores parametrizados no sustituyen la validación de identificadores SQL.
- **Stacked queries:** varias sentencias separadas por `;`, cuando el contexto y el controlador lo permiten. Su aceptación debe comprobarse por parámetro; no se deduce de que otra entrada admita UNION.
- **Pruebas temporales:** una demora controlada aporta evidencia de evaluación de una expresión. Conviene comparar contra una línea base y no atribuir cualquier latencia a ejecución SQL.

## Casos y transferencia entre rondas

| Caso | Evidencia | Conocimiento reutilizable |
|---|---|---|
| [[Writeup - Factura Fantasma]] | MariaDB, diez columnas, `UnIoN SeLeCt`, extracción desde `secrets` | Descubrir consulta, compatibilidad de columnas y campo visible; un filtro de palabras no reemplaza parametrización. |
| [[Writeup - La Receta]] | PostgreSQL, cuatro columnas en `q`, stacked queries en `sort`, permiso `INSERT` | Ampliar la investigación desde lectura hacia permisos reales; un `UPDATE` denegado no implica ausencia de escritura. |

En La Receta, insertar un administrador copiando un hash conocido permitió un login legítimo. No fue necesario romper JWT. [[Writeup - Pentra CMS]] y [[Writeup - VaultBridge]] mencionan SQLi como una vía no utilizada o sin éxito; no deben contarse como explotaciones SQLi confirmadas.

## Mitigación

1. Parametrizar valores; mapear columnas y direcciones de ordenación a una lista cerrada.
2. Deshabilitar múltiples sentencias donde no sean necesarias, sin usarlo como única defensa.
3. Aplicar [[3- Principio de privilegio mínimo]] a tablas, vistas y operaciones.
4. Separar búsquedas públicas de administración de identidades; no exponer errores internos.
5. Verificar autorización por objeto/rol además de la seguridad de la consulta.

## Navegación

- ⬆️ Carpeta: [[_Vista Curada]]
- 🏠 [[MOC - Web Pentesting OWASP]]

## Relacionadas

- [[SQL]] — sintaxis de consultas y escrituras.
- [[PostgreSQL]] — permisos por operación y tablas de identidad.
- [[Authentication]] — relación entre datos de identidad y autorización.
- [[PentraZE CTF 2026 - Ronda 2]] — origen de la ampliación con stacked queries.
