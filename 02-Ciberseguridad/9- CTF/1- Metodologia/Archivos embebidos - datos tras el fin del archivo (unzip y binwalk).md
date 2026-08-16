---
tipo: cheatsheet
tags: [ctf, forensics, metodologia, esteganografia, zip, binwalk, png]
actualizado: 2026-08-15
---

# Archivos embebidos - datos tras el fin del archivo (unzip y binwalk)

Muchos formatos de archivo definen su propio marcador de fin (`IEND` en
PNG, por ejemplo). Ese marcador le dice al programa que lo abre "hasta
aquí llega la imagen" — pero no impide que, físicamente, haya más bytes
después. Nada obliga a que el fin del formato coincida con el fin del
archivo, y ese hueco es justo donde se esconden datos anexados: un
archivo completo, empaquetado, pegado detrás de otro.

## Por qué funciona

- El visor/parser del formato original (un lector de PNG, por ejemplo)
  deja de leer en cuanto encuentra su propio marcador de fin. Todo lo
  que venga después es invisible para él, pero sigue estando en el
  archivo.
- Muchos formatos de contenedor (como ZIP) guardan su índice —el
  *central directory*— al **final** del archivo, no al principio. Un
  lector de ZIP como `unzip` busca esa estructura desde el final hacia
  atrás, así que le da igual cuántos bytes ajenos haya delante: encuentra
  su índice igual y extrae el contenido.

## Detectar la anomalía

```bash
file archivo      # confirma el tipo real, primer paso siempre
strings archivo   # busca texto legible
```

La señal es texto que **no pertenece al formato original**, apareciendo
después de donde ese formato ya debería haber terminado: rutas de
carpetas (`secret/`, algo `.zip`), cabeceras de otro formato, cadenas que
no tienen sentido en una imagen o un documento. Ver
[[Triaje de archivos - file, strings y exiftool]] para el triaje completo
que precede a este paso.

## Extraer lo anexado

**Si lo anexado es un ZIP** (el caso más común en retos fáciles):

```bash
unzip archivo
```

Funciona directamente sobre el archivo combinado, sin necesidad de
recortar ni separar manualmente los bytes: `unzip` localiza el *central
directory* al final y extrae desde ahí.

**Opción general**, cuando no se sabe (o no es ZIP) qué tipo de archivo
está anexado:

```bash
binwalk -e archivo
```

`binwalk` escanea el archivo completo buscando firmas (magic bytes) de
cualquier formato conocido, esté donde esté dentro del archivo, y
extrae (`-e`) cada uno a una carpeta de salida.

## Si lo extraído no es texto

Una vez extraído el archivo anexado, seguir aplicando triaje: si el
contenido es otra imagen y la flag está **dibujada como píxeles**, ni
`strings` ni `grep` la van a encontrar — hay que abrir la imagen y
leerla a simple vista (o pasarla por OCR).

## Caso que la motivó

[[hideme]] — un PNG con un ZIP anexado tras el `IEND`, que a su vez
contenía otra imagen con la flag renderizada como píxeles.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Triaje de archivos - file, strings y exiftool]]
- ➡️ Siguiente: [[SSTI - de la detección al RCE en Jinja2]]

## Relacionadas

- [[Triaje de archivos - file, strings y exiftool]] — el triaje base (`file` → `strings`) que da la primera señal de que hay algo anexado.
- [[hideme]] — el writeup que estrena esta metodología.
- [[Identificar codificaciones, cifrados y hashes]] — el siguiente paso cuando lo anexado no es un archivo reconocible sino una cadena codificada.
