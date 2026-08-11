---
tipo: cheatsheet
tags: [ctf, forensics, metodologia, file, strings, exiftool, base64, pentraze]
actualizado: 2026-08-11
---

# Triaje de archivos — file, strings y exiftool

Primer barrido a aplicar sobre cualquier archivo entregado en un reto de
forense antes de asumir que hay que hacer algo más avanzado. Cuando el
archivo "se ve normal" a simple vista, la flag suele estar en una capa
que no es visual: el tipo real del archivo, el texto legible embebido, o
los metadatos.

## 1. `file` — confirmar el tipo real

```bash
file archivo
```

Comprueba la firma real del archivo (magic bytes), no la extensión. Un
`.jpg` puede ser en realidad otra cosa, o puede ser exactamente lo que
dice ser — confirmarlo primero evita perder tiempo con la herramienta
equivocada.

## 2. `strings` — buscar texto legible

```bash
strings archivo | grep -i pico
```

Extrae las cadenas de texto imprimible embebidas en un archivo binario.
Puede sacar a la luz un rastro parcial (un fragmento de nombre de reto, un
comentario suelto) que funciona como **señal**, no como flag: indica que
hay algo metido en el archivo, pero rara vez dice dónde ni cómo está
codificado. Si `strings` no da nada útil, el siguiente paso es mirar
metadatos.

## 3. `exiftool` — inspeccionar metadatos

```bash
exiftool archivo
```

Repasa todos los campos de metadatos del archivo (EXIF en imágenes, y
equivalentes en otros formatos). Prestar atención especial a los campos
con **nombre propio** — *License*, *Copyright*, *Comment*, *Artist* — porque
son los que se reutilizan para esconder algo sin que se note al abrir el
archivo con un visor normal. Ver también [[Extraer Metadatos]], la nota
existente del vault sobre esta misma herramienta.

## 4. Si el metadato aparece codificado

Cuando el campo encontrado no se lee en claro, identificar de qué tipo de
codificación se trata antes de intentar nada más — ver
[[Identificar codificaciones, cifrados y hashes]]. El caso más común en
retos fáciles es Base64, que se reconoce por terminar en `=`, `==` o
ninguno, y se decodifica con:

```bash
echo "cadena" | base64 -d
```

o con CyberChef si se prefiere una herramienta visual.

## Orden recomendado

1. `file` — ¿es realmente lo que dice ser?
2. `strings` — ¿hay alguna señal de texto suelta?
3. `exiftool` — ¿hay algo en los campos de metadatos, sobre todo en los de nombre propio?
4. Si aparece una cadena rara, identificar la codificación y decodificar.

## Caso que la motivó

[[Information]] — primer reto de forense resuelto en la sección, donde
`strings` dio solo una señal parcial y la flag real apareció con
`exiftool` en el campo *License*, codificada en Base64.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Barrer un parámetro - bucle, Burp Intruder y Caido]]

## Relacionadas

- [[Information]] — el writeup que estrena esta metodología.
- [[Identificar codificaciones, cifrados y hashes]] — paso de reconocimiento de Base64 dentro de este flujo.
- [[Extraer Metadatos]] — nota existente del vault sobre extracción de metadatos con `exiftool`.
- [[_6- Forense Digital|6- Forense Digital]] — dominio de forense más amplio donde encaja este triaje.
