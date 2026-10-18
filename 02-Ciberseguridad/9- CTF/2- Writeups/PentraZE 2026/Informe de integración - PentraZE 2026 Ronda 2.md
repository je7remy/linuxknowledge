---
tipo: referencia
tags: [ctf, pentraze, ronda-2, integracion, validacion]
actualizado: 2026-10-18
---

# Informe de integración - PentraZE 2026 Ronda 2

## Resultado y alcance

Integración incremental de **cinco write-ups**, un índice de segunda ronda y seis notas técnicas en la estructura existente. Los nueve write-ups anteriores se conservan sin modificaciones. La navegación parte de [[_9- CTF]], continúa en [[PentraZE CTF 2026 - MOC]] y llega a [[PentraZE CTF 2026 - Ronda 2]].

| Entorno | Ruta absoluta | Comprobación |
|---|---|---|
| Trabajo | `/home/je7remy/linuxknowledge` | Directorio real, sin `.git`; único destino de contenido integrado |
| Publicación | `/home/je7remy/repos/linuxknowledge` | Directorio real independiente, con `.git`; inventario verificado sin cambios |
| Fuente | `/home/je7remy/Escritorio/ctf.docx` | Documento original conservado |
| Respaldo | `/home/je7remy/Documentos/Respaldos-Obsidian/pentraze-ronda2-20261018-110032` | Copia completa anterior y manifiestos de integridad |

Se comprobaron rutas reales, inodos diferentes, ausencia de enlaces simbólicos y ausencia de archivos compartidos mediante enlaces duros. No se ejecutaron operaciones Git ni scripts de explotación, y no se contactó con las antiguas instancias.

## Write-ups creados

Carpeta común: `02-Ciberseguridad/9- CTF/2- Writeups/PentraZE 2026/`.

| Archivo | Estado conservado | Observación |
|---|---|---|
| [[Writeup - La Receta]].md | Resuelto; flag documentada | SQLi UNION y stacked queries; INSERT permitió un login admin legítimo |
| [[Writeup - Lives 9, Backups 0]].md | **4/4 preguntas completadas** | Solo falta incorporar la flag final |
| [[Writeup - Nozama Store]].md | Resuelto; 100 puntos; flag documentada | Race condition con sesión PHP y solicitudes concurrentes |
| [[Writeup - SMBiablo]].md | Resuelto; flag documentada | Leak, stack overflow y ret2libc; script fuente truncado |
| [[Writeup - Data Del Más Allá]].md | Resuelto; flag documentada | Reversing y token administrativo; no heap exploit confirmado |

**Write-ups existentes actualizados: ninguno.** La búsqueda previa no encontró ninguno de estos cinco. El nombre de Lives omite los dos puntos en el archivo para facilitar portabilidad; conserva título original y alias YAML `Lives: 9, Backups: 0`. No se crearon variantes duplicadas.

## Otros archivos creados

| Ruta relativa | Función |
|---|---|
| `02-Ciberseguridad/9- CTF/2- Writeups/PentraZE 2026/PentraZE CTF 2026 - Ronda 2.md` | Índice único de segunda ronda |
| `02-Ciberseguridad/9- CTF/2- Writeups/PentraZE 2026/Informe de integración - PentraZE 2026 Ronda 2.md` | Este informe |
| `_Vista Curada/SQL Injection.md` | Une Factura Fantasma y La Receta; UNION frente a escritura |
| `_Vista Curada/Race Condition.md` | Atomicidad, concurrencia y comparación con HooKitty |
| `_Vista Curada/WebSocket.md` | Mensajes y autorización en Eco Persistente y Data |
| `02-Ciberseguridad/9- CTF/1- Metodologia/Stack Buffer Overflow y ret2libc.md` | ELF, GOT, libc, ASLR/NX, ROP y pwntools |
| `02-Ciberseguridad/6- Forense Digital/Volatility 3.md` | Flujo Windows de procesos, volcado y cadenas |
| `03-Desarrollo/1- Bases de Datos/PostgreSQL.md` | Permisos separados, valores predeterminados y roles |
| `assets/PentraZE-2026-ronda-2/ctf.docx` | Copia binaria idéntica de la fuente, enlazada desde las cinco notas |

Se reutilizaron las notas reales [[Authentication]], [[DNS]], [[Cryptography]], [[SQL]], [[9- SMB]], [[1- Protocolo HTTP]], [[1- Introducción a la Programación Concurrente]], [[3- Principio de privilegio mínimo]] y las metodologías existentes. JWT enlaza a su sección en Cryptography; Python a su MOC/curso. No se crearon páginas equivalentes con nombres alternativos.

## Archivos existentes modificados

Todas las rutas son relativas a la bóveda de trabajo. La carpeta del evento de la tabla anterior se abrevia aquí como `PentraZE/`.

| Archivo | Cambio |
|---|---|
| `PentraZE/PentraZE CTF 2026 - MOC.md` | 14 retos únicos; primera ronda preservada como vista histórica, segunda ronda y estadísticas generales |
| `PentraZE/_PentraZE 2026.md` | Acceso a ambas rondas y al informe |
| `PentraZE/CTF - Web.md` | Ocho retos principales y referencia secundaria a Lives |
| `PentraZE/CTF - Binary Exploitation.md` | Dos retos PWN; distingue categoría y técnica demostrada |
| `PentraZE/CTF - Forensics.md` | Lives con 4/4 preguntas; estado de la flag separado |
| `PentraZE/CTF - Easy.md` | La Receta, normalización Fácil → Easy |
| `PentraZE/CTF - Medium.md` | Nozama Store, 100 puntos |
| `PentraZE/CTF - Reversing.md` | Referencias técnicas a PWN, sin reclasificar los retos |
| `02-Ciberseguridad/9- CTF/_9- CTF.md` | Acceso a ronda 2 y conexión forense |
| `02-Ciberseguridad/9- CTF/2- Writeups/_2- Writeups.md` | Ruta de acceso a la segunda ronda |
| `02-Ciberseguridad/9- CTF/1- Metodologia/_1- Metodologia.md` | Nuevas referencias técnicas y ret2libc |
| `02-Ciberseguridad/9- CTF/1- Metodologia/Reversing - de leer código fuente a desensamblar binarios.md` | Casos ELF/PE y límites de evidencia |
| `02-Ciberseguridad/9- CTF/1- Metodologia/Identificar codificaciones, cifrados y hashes.md` | Base32, hexadecimal, XOR y SHA-256 truncado |
| `02-Ciberseguridad/6- Forense Digital/_6- Forense Digital.md` | Volatility y Lives |
| `03-Desarrollo/1- Bases de Datos/_1- Bases de Datos.md` | PostgreSQL |
| `_Vista Curada/_Vista Curada.md` | Tres nuevas páginas de conceptos |
| `_Vista Curada/Authentication.md` | Comparación de cinco casos de identidad y autorización |
| `_Vista Curada/DNS.md` | Rebinding frente a exfiltración |
| `_Vista Curada/MOC - Python para Ciberseguridad.md` | Automatización de ambas rondas |
| `_Vista Curada/MOC - Forense Digital end-to-end.md` | Volatility, Lives y reparación de referencia al caso de memoria existente |
| `index.md` | Catálogo actualizado y acceso a los cinco retos |
| `log.md` | Registro de integración y validación |

**Balance de archivos:** 14 creados (13 Markdown y un DOCX), 22 existentes modificados, 0 eliminados. No se movieron carpetas ni notas.

## Wikilinks y conexiones incorporadas

Cada nuevo write-up enlaza al MOC, a ronda 2, a su categoría, a notas técnicas y a casos comparables. Se añadieron enlaces de vuelta desde índices y desde conceptos compartidos; los backlinks restantes los genera Obsidian.

Las rutas transversales principales son:

1. Factura Fantasma → [[SQL Injection]] → La Receta → [[PostgreSQL]].
2. HooKitty → [[Race Condition]] → Nozama; DNS cambiante frente a saldo compartido.
3. Eco Persistente → [[WebSocket]] → Data Del Más Allá.
4. Pentra CMS / SoftDat → [[Authentication]] → La Receta / Data.
5. Caso forense de memoria → [[Volatility 3]] → Lives → [[DNS]].
6. GDB baby step 1 → metodología de reversing → [[Stack Buffer Overflow y ret2libc]] → SMBiablo.
7. Xouroboros → identificación de codificación/cifrado → XOR y SHA-256 de Data, conservando la diferencia entre ataques.

El inventario exhaustivo de enlaces añadidos, con nota de origen, destino escrito y ruta resuelta, se conserva en `wikilinks-nuevos.tsv` dentro del directorio de respaldo. No se usan enlaces a títulos hipotéticos para aumentar el grafo.

El cotejo registra **364 nuevas ocurrencias de wikilinks**, distribuidas en **330 combinaciones distintas de nota de origen y destino escrito**. Incluye navegación, referencias técnicas y enlaces de este informe. Se resolvieron o sustituyeron nueve relaciones antiguas sin destino dentro de CTF, además de la referencia reparada en el MOC forense.

## Enlaces rotos corregidos y deuda previa

- Las nuevas notas [[SQL Injection]] y [[WebSocket]] resuelven referencias antiguas sin editar los write-ups de primera ronda.
- En el MOC de PentraZE se sustituyeron cuatro referencias sin destino por enlaces a conceptos y casos realmente existentes.
- En el MOC forense se corrigió el enlace inexistente `_3- Caso Practico, Un hacker entró a mi equipo` para apuntar a [[4- Caso Practico, Un hacker entró a mi equipo]].
- Se escaparon los separadores de alias en las tablas de los índices modificados para que no se interpreten como nuevas columnas Markdown.

Permanecen **27 nombres de destino sin nota en enlaces antiguos del conjunto CTF**: `AEAD`, `AES-CBC`, `Caesar Cipher`, `Container Escape`, `DNS Rebinding`, `Database Security`, `Directory Traversal`, `IDOR`, `Information Disclosure`, `JWT`, `Keystream Reuse`, `Linux`, `Network Segmentation`, `NoSQL Injection`, `Nonce`, `Password Hashing`, `Privilege Escalation`, `ROT13`, `ROT47`, `Rail Fence Cipher`, `Replay Attack`, `SSRF`, `TOCTOU`, `Two-Time Pad`, `Vigenère Cipher`, `WAF Bypass` y `Web API Security`.

Son referencias previas de notas conservadas. Se enumeran como texto para no introducir nuevas referencias rotas. El JSON de auditoría contiene cada nota de origen. La integración nueva y todos los archivos modificados quedan sin wikilinks rotos ni ambiguos.

## Validación automática

| Comprobación | Resultado |
|---|---|
| Cantidad y rutas | Exactamente cinco write-ups de ronda 2, en la carpeta del evento |
| Duplicados | Ninguna colisión de nombres normalizados en el conjunto CTF |
| YAML | Parseo estricto y claves únicas; metadatos mínimos presentes en los Markdown creados/modificados |
| Wikilinks nuevos/modificados | Destinos existentes, resolución única y encabezados de enlaces internos comprobados |
| Primera ronda | Los nueve write-ups mantienen sus hashes SHA-256 anteriores |
| Código y tablas | 78 bloques originales y seis tablas conservados; delimitadores cerrados |
| Python | Cinco bloques con sintaxis analizada mediante AST; no se ejecutaron |
| Fragmentos reparados | Cuatro fragmentos deteriorados reconstruidos cambiando solo espacios/saltos de línea |
| Cobertura | 421 registros de correspondencia de párrafos, tablas y bloques; sin contenido técnico ausente en el cotejo |
| Flags | Cuatro flags de ronda 2 coinciden literalmente con el Word; Lives no contiene una flag inventada |
| Cálculos locales | Dos tokens SHA-256, longitud del secreto, XOR inicial, hexadecimal del Codex y resta de base libc coherentes |
| Adjuntos | DOCX idéntico al original; no había imágenes incrustadas ni enlaces externos a imágenes en el documento |
| Grafo CTF | Un componente conectado; 0 notas aisladas y 0 notas sin enlaces entrantes |
| Publicación | Mismo inventario, contenido, permisos y fechas de modificación, incluyendo `.git` |

El grafo se calculó a partir de los enlaces entre notas, no de la posición visual de los nodos. Inicialmente había un componente de 48 notas CTF; tras añadir write-ups, metodología, índice e informe hay un componente de 56. Las notas técnicas fuera de CTF añaden conexiones con el resto de la bóveda.

### Filtros de Obsidian

Se inspeccionaron `.obsidian/graph.json`, `workspace.json` y `workspaces.json`. El grafo guardado tiene búsqueda vacía, `showOrphans: true`, `hideUnresolved: false`, `showTags: false` y `showAttachments: false`. No hay filtro guardado que excluya los nuevos enlaces entre notas. El DOCX y los tags no se muestran como nodos por esas opciones. No se modificó la configuración ni se afirmó una comprobación visual del renderizado en Obsidian.

## Contenido que requiere revisión

1. **Lives:** incorporar la flag final de la evidencia de la resolución. Las cuatro respuestas están completadas y aceptadas.
2. **SMBiablo:** recuperar el resto del exploit original. Faltan cálculo del leak/base/gadgets, construcción y envío del desbordamiento e interacción con la shell. La fuente enumera cuatro símbolos aunque dice «tres funciones»; se conserva esa observación sin alterar sus evidencias.
3. **Data:** recuperar el preámbulo del script final. Se restauró formato, pero faltan imports y asignaciones iniciales. El extractor conserva sus offsets y `raw[2:]`; no se verificaron contra el PE ausente del Word.
4. **Nozama:** la salida final usa algunos rótulos distintos de los `print` del script. Se conservan ambos registros y no se simula una correspondencia exacta.
5. **Evidencia externa:** `evidence.tar.xz`, `codex_acquisition.MEM`, `pid.392.dmp`, `smbiablo.zip`, `smbiablo`, `libc.so.6` y `DataMasAlla.exe` se mencionan en la fuente, pero no están adjuntos dentro del Word. No se presentan como archivos incorporados a la bóveda.
6. **Deuda histórica:** los 27 destinos antiguos sin nota permanecen documentados arriba; no afectan a la resolución de enlaces de las notas nuevas ni crean componentes CTF aislados.

## Respaldo y reversión

Directorio de respaldo: `/home/je7remy/Documentos/Respaldos-Obsidian/pentraze-ronda2-20261018-110032/`.

- `linuxknowledge-antes.tar.gz`: copia completa de los 1,752 archivos originales, cotejada archivo a archivo mediante SHA-256 antes de integrar.
- `trabajo-antes.json` y `publicacion-antes.json`: inventarios iniciales, hashes, permisos y fechas de modificación.
- `ctf.docx`: copia adicional de la fuente original.
- `validacion-final.json`, `cambios.json` y `wikilinks-nuevos.tsv`: resultados y alcance exacto de la integración.
- `cobertura-fuente.json`: correspondencia del Word con los contenidos convertidos.
- `auditar.py` y `verificar.py`: verificadores locales; leen Markdown/XML y no ejecutan sus bloques de código.

Para revertir selectivamente, extraer el TAR en una ubicación separada y restaurar **solo** los archivos marcados como modificados en `cambios.json`; los creados se identifican en ese mismo manifiesto. Comparar antes sus hashes finales evita sobrescribir trabajo posterior. La copia de publicación no participa en la reversión.

## Navegación

- ⬆️ Carpeta: [[_PentraZE 2026]]
- ⬅️ Índice de ronda: [[PentraZE CTF 2026 - Ronda 2]]
- 🏠 Evento: [[PentraZE CTF 2026 - MOC]]

## Relacionadas

- [[log]] — registro cronológico.
- [[index]] — catálogo del segundo cerebro.
- [[assets/PentraZE-2026-ronda-2/ctf.docx|Fuente original]] — material conservado para revisión.
