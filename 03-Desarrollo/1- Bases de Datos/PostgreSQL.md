---
tipo: teoria
tags: [postgresql, sql, bases-de-datos, permisos, minimo-privilegio]
actualizado: 2026-10-18
---

# PostgreSQL — Permisos y seguridad de los datos

PostgreSQL es un motor relacional con tipos, esquemas, roles y privilegios por operación. Desde una aplicación, el impacto de una consulta manipulada está limitado —o ampliado— por los permisos de la cuenta de conexión.

## Privilegios por operación

`SELECT`, `INSERT`, `UPDATE` y `DELETE` son permisos diferentes. Carecer de `UPDATE` no implica una cuenta de solo lectura. `has_table_privilege()` permite consultar privilegios sobre tablas; el alcance de una evaluación incluye también roles heredados, esquemas, funciones y las rutas de acceso realmente usadas.

En [[Writeup - La Receta]], PostgreSQL 15.19 usaba la cuenta `app_la_receta` sobre `public.chefs`:

| Operación | Resultado documentado |
|---|---|
| SELECT | Demostrado |
| INSERT | Permitido |
| UPDATE | Denegado |
| DELETE | Denegado |

La inyección en `sort` admitía sentencias apiladas. El atacante insertó un usuario `admin` copiando el hash de una cuenta de contraseña conocida. No modificó al administrador existente ni obtuvo su contraseña.

## Valores predeterminados y confianza

`gen_random_uuid()` proporcionaba el identificador predeterminado; `role` tenía `member` como valor predeterminado. Un valor predeterminado se usa cuando la escritura no proporciona otro valor: no es una política que prohíba insertar `admin` explícitamente.

La autenticación HS256 posterior funcionó según los datos almacenados. Proteger una firma sin proteger la fuente de los roles deja incompleta la frontera de autorización.

## Diseño defensivo

- Aplicar [[3- Principio de privilegio mínimo]] y separar cuentas de búsqueda, registro y administración cuando el diseño lo permita.
- Parametrizar valores y validar identificadores/ordenación con listas permitidas; ver [[SQL Injection]].
- Restringir las rutas que pueden asignar roles privilegiados y auditar altas/cambios.
- Usar transacciones y restricciones para las invariantes de datos. En problemas de concurrencia, comprobar que el aislamiento y los bloqueos elegidos realmente preservan la invariante; ver [[Race Condition]].

## Navegación

- ⬆️ Carpeta: [[_1- Bases de Datos]]
- ⬅️ Anterior: [[SQL]]

## Relacionadas

- [[SQL]] — comandos esenciales.
- [[SQL Injection]] — diferencia entre UNION y sentencias apiladas.
- [[Writeup - La Receta]] — caso documentado de escalada por INSERT.
- [[Authentication]] — identidad y permisos dependen del estado confiable del servidor.
