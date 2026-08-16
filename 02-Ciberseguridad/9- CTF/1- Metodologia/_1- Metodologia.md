---
tipo: indice
seccion: 02-Ciberseguridad/9- CTF/1- Metodologia
actualizado: 2026-08-16
---

# 1 — Metodología

🏠 [[🔒🐧Hub|Hub Principal del vault]]

Marcos mentales y cheatsheets reutilizables para abordar retos de CTF web,
independientes de un reto concreto. Se leen antes de entrar a un writeup
en [[_2- Writeups|2- Writeups]] y se consultan durante la resolución.

## Contenido

- [[Marco de ataque web - tres movimientos]] — los tres movimientos para abordar cualquier reto web desde cero.
- [[Archivos y rutas ocultas en retos web]] — rutas conocidas a probar manualmente (`robots.txt`, `.git/`, `.env`, etc.).
- [[Identificar codificaciones, cifrados y hashes]] — distinguir codificación reversible, cifrado y hash irreversible.
- [[Barrer un parámetro - bucle, Burp Intruder y Caido]] — comparar bucle/script, Burp Intruder y Caido Automate para barrer un rango de valores.
- [[Triaje de archivos - file, strings y exiftool]] — primer barrido sobre un archivo de forense: tipo real, texto embebido y metadatos.
- [[Archivos embebidos - datos tras el fin del archivo (unzip y binwalk)]] — detectar y extraer datos anexados tras el marcador de fin de un archivo (`unzip`, `binwalk -e`).
- [[SSTI - de la detección al RCE en Jinja2]] — de la detección de una plantilla evaluada al escape del sandbox y RCE en Jinja2/Flask.
- [[Leer el código fuente - view-source, desminificado y señuelos]] — código fuente vs. página renderizada, desminificado/beautify y patrón de descarte de señuelos casi idénticos.

## Navegación

- ⬆️ Carpeta padre: [[_9- CTF|9- CTF]]

## Relacionadas

- [[_2- Writeups|2- Writeups]] — donde se aplica esta metodología caso por caso.
- [[MOC - Web Pentesting OWASP]] — marco profesional de pentesting web, más amplio que el enfoque CTF.
- [[_1- Cracking|1- Cracking]] — cracking de hashes con Hashcat, complementa la identificación de hashes.
