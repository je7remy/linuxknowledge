---
tipo: cheatsheet
tags: [ctf, web-exploitation, cheatsheet, enumeracion, pentraze]
actualizado: 2026-08-09
---

# Archivos y rutas ocultas en retos web

Rutas a probar manualmente en la barra de direcciones cuando un reto web
no revela nada obvio a simple vista. Corresponde al primer movimiento del
[[Marco de ataque web - tres movimientos|marco de ataque web]]: lo que el
servidor entrega sin que se lo pidas explícitamente.

| Ruta | Qué es | Por qué importa |
|---|---|---|
| `/robots.txt` | Instrucciones para rastreadores de buscadores | La gente lo usa para *esconder* carpetas, pero al listarlas las publica en un archivo legible por cualquiera |
| `/sitemap.xml` | Mapa de páginas para buscadores | Revela páginas no enlazadas desde la navegación |
| `/.htaccess` | Configuración de servidor Apache | Redirecciones, control de acceso, rutas protegidas |
| `/.DS_Store` | Metadatos de carpeta generados por macOS | Contiene el listado de archivos de la carpeta, incluidos los no enlazados |
| `/.git/` | Repositorio Git expuesto | Permite reconstruir el código fuente completo |
| `/.env` | Variables de entorno | Contraseñas, llaves de API, cadenas de conexión |

## Nota didáctica

Estos nombres **no se deducen por lógica, se conocen por inventario**. No
hay forma de "razonar" que `/.DS_Store` existe si no se sabe de antemano
qué es. La lista se amplía reto a reto — cada writeup nuevo es candidato
a sumar una fila aquí.

<!-- PENDIENTE: ampliar tabla con rutas descubiertas en próximos retos -->

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Marco de ataque web - tres movimientos]]
- ➡️ Siguiente: [[Identificar codificaciones, cifrados y hashes]]

## Relacionadas

- [[Marco de ataque web - tres movimientos]] — movimiento 1 del marco general.
- [[Scavenger Hunt]] — reto donde `robots.txt` y `.htaccess` fueron pasos clave de la cadena.
- [[Identificar codificaciones, cifrados y hashes]] — qué hacer una vez que el archivo oculto aparece.
