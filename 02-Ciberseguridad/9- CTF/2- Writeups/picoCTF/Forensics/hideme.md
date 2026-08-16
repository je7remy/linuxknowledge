---
tipo: laboratorio
tags:
  - ctf
  - picoctf
  - forensics
  - archivos-embebidos
  - zip
  - binwalk
  - writeup
actualizado: 2026-08-15
dificultad: fácil
fecha: 2026-08-15
---

# hideme

Reto de **picoCTF**, categoría **Forensics**, dificultad **fácil**.
Resuelto el **15 de agosto de 2026**. Segundo reto de forense de la
sección — sigue a [[Information]] dentro de [[_Forensics|Forensics]].

Se entrega una única imagen PNG (`flag.png`). A simple vista es una
imagen normal: abrirla con un visor no muestra nada fuera de lo común.

## Técnica que abrió el reto

**Datos anexados después del fin del archivo.** Un PNG termina con el
marcador `IEND`, pero nada impide que, tras ese marcador, alguien pegue
otro archivo completo — en este caso, un ZIP. El visor de imágenes lee
hasta `IEND` y da la imagen por completa; el resto de bytes lo ignora
por completo, pero ahí siguen.

## Recorrido

1. `file flag.png` confirma que efectivamente es un PNG.
2. `strings flag.png` muestra, **después** de donde debería terminar la
   imagen, rutas de texto plano como `secret/` y `secret/flag.png` —
   nombres de ruta que no pertenecen al formato PNG y delatan que hay
   otro archivo empaquetado ahí dentro.
3. Extracción con `unzip flag.png`: funciona directamente, sin recortar
   ni separar nada a mano. Un ZIP guarda su índice central al final del
   archivo, así que `unzip` busca esa estructura desde el final hacia
   atrás e ignora los bytes del PNG que hay delante. Alternativa general
   para cualquier tipo de archivo anexado (no solo ZIP):
   `binwalk -e`. Ver
   [[Archivos embebidos - datos tras el fin del archivo (unzip y binwalk)]].
4. Dentro del ZIP aparece `secret/flag.png`, una segunda imagen. La flag
   está **dibujada como píxeles**, no como texto: `strings` o `grep`
   sobre ese archivo no encuentran nada. Hace falta abrir la imagen
   extraída y leerla a simple vista.

## Lección extraída

El fin de un archivo tal como lo define su formato (`IEND` en PNG) no es
necesariamente el fin de los bytes del archivo. Que `strings` muestre
contenido después de ese marcador es la señal de que hay algo anexado —
el mismo triaje de
[[Triaje de archivos - file, strings y exiftool]] aplicado a otra capa:
ahí la señal era un metadato con nombre propio, acá es texto que aparece
donde el formato ya debería haber terminado.

También queda claro que **el tipo de dato de la flag decide la
herramienta**: en [[Information]] la flag era una cadena Base64 y
`base64 -d` bastaba; aquí la flag está renderizada como imagen, y
ninguna herramienta de texto la va a encontrar — hay que abrir el
archivo y mirarlo.

<!-- No se incluye la flag ni el contenido de la imagen extraída: esta nota sirve para repetir el ejercicio, no para saltárselo. -->

---

## Navegación

- ⬆️ Carpeta padre: [[_Forensics|Forensics]]
- ⬅️ Anterior: [[Information]]

## Relacionadas

- [[Archivos embebidos - datos tras el fin del archivo (unzip y binwalk)]] — la metodología que resume este flujo (`strings` tras el fin del formato → `unzip`/`binwalk -e`).
- [[Triaje de archivos - file, strings y exiftool]] — el triaje base (`file` → `strings`) que dio la primera señal.
- [[Information]] — primer reto de forense de la sección, misma familia de triaje aplicada a metadatos en vez de a datos anexados.
