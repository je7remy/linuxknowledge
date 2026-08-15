---
tipo: laboratorio
tags: [ctf, picoctf, forensics, metadatos, exiftool, base64, writeup]
actualizado: 2026-08-11
dificultad: fácil
fecha: 2026-08-11
---

# Information

Reto de **picoCTF**, categoría **Forensics**, dificultad **fácil**.
Resuelto el **11 de agosto de 2026**. Primer reto de forense de la
sección — abre [[_Forensics|Forensics]] dentro de picoCTF.

Se entrega una única imagen JPEG (un gato). A simple vista es una foto
normal: nada en los píxeles ni en el cuerpo del archivo delata la flag.

## Técnica que abrió el reto

Inspección de **metadatos** de la imagen. La flag no estaba escondida en
el contenido visual ni en la estructura del archivo, sino en un campo de
metadatos con nombre propio — el campo *License* — y ese campo estaba
además codificado en Base64.

## Recorrido

1. `file` sobre el archivo entregado, para confirmar que efectivamente es
   un JPEG y no un archivo con extensión falseada.
2. `strings` sobre el archivo: aparece un rastro parcial de "picoCTF" en
   el volcado. Es una **señal**, no la flag — indica que hay algo del reto
   metido en el archivo, pero no dice dónde ni cómo está codificado.
3. `exiftool` sobre el archivo: revela el campo de metadatos con la
   cadena Base64. Este es el paso que realmente abre el reto — ver
   [[Triaje de archivos - file, strings y exiftool]] para el flujo
   completo aplicado aquí.
4. Reconocer la cadena como Base64 (ver
   [[Identificar codificaciones, cifrados y hashes]]) y decodificarla con
   `base64 -d` o con CyberChef.

## Lección extraída

`strings` da una pista de que "algo" hay, pero no basta: hace falta mirar
los metadatos con `exiftool` para encontrar dónde está exactamente. Y
dentro de los metadatos, los campos con nombre propio — *License*,
*Copyright*, *Comment*, *Artist* — son los primeros a revisar, porque son
los que un reto (o un adversario real) suele reutilizar para esconder
algo sin que salte a la vista en un visor de imágenes normal.

El conocimiento se encadena entre categorías: una flag escondida "a la
forense" (en metadatos) puede estar cerrada "a la web" (en Base64). Ya
había pasado lo inverso en [[WebDecode]] — ahí la cadena Base64 estaba en
una página secundaria, aquí está en un campo EXIF. Es la misma técnica de
identificación de codificación, aplicada sobre una superficie distinta.
También conecta con [[Extraer Metadatos]], la nota de la sección OSINT
sobre extracción de metadatos con `exiftool`.

<!-- No se incluye la flag ni el valor literal del campo de metadatos: esta nota sirve para repetir el ejercicio, no para saltárselo. -->

---

## Navegación

- ⬆️ Carpeta padre: [[_Forensics|Forensics]]
- ➡️ Siguiente: [[hideme]]

## Relacionadas

- [[Triaje de archivos - file, strings y exiftool]] — la metodología que resume este flujo (`file` → `strings` → `exiftool` → decodificar).
- [[Identificar codificaciones, cifrados y hashes]] — cómo reconocer que la cadena del metadato era Base64.
- [[Extraer Metadatos]] — nota existente del vault sobre extracción de metadatos con `exiftool`.
- [[WebDecode]] — otro reto donde el paso decisivo fue reconocer Base64, en este caso escondido en la web en vez de en metadatos.
