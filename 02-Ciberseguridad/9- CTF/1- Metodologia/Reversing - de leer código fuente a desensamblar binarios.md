---
tipo: cheatsheet
tags: [ctf, picoctf, reverse-engineering, java, ghidra, strings, metodologia]
actualizado: 2026-08-16
---

# Reversing — de leer código fuente a desensamblar binarios

En forense la pregunta era "¿qué *es* este archivo?"
([[Triaje de archivos - file, strings y exiftool]]). En reversing la
pregunta es **"¿qué *hace* este programa y qué espera de mí?"**: hay que
entender el comportamiento, no solo clasificar un archivo estático.

## El reflejo transversal: buscar la validación

En casi cualquier reto de reversing hay un punto del programa que
**decide si la entrada del usuario es correcta** — una comparación, una
función `check`/`verify`, un bucle que transforma la entrada y la
compara byte a byte contra un valor esperado. Encontrar ese punto y leer
**contra qué compara** es el reflejo que se repite en todos los
peldaños de la escalera, cambiando solo la dificultad para localizarlo y
leerlo.

## La escalera de progresión

El reversing real casi nunca entrega el código fuente; entrega un
**binario compilado**. Los retos fáciles como [[vault-door-training]]
simulan el primer peldaño de una escalera que se vuelve
progresivamente más opaca:

1. **Código fuente legible** — el programa se entrega tal cual (Java,
   Python, C sin compilar). Se lee en un editor de texto normal y la
   validación es directamente legible. Caso aplicado:
   [[vault-door-training]].
2. **Lógica ligeramente ofuscada** — sigue habiendo código fuente, pero
   con nombres de variable sin sentido, indirecciones o transformaciones
   simples (XOR, desplazamientos) antes de la comparación. Hay que
   *seguir* el flujo, no solo leerlo.
3. **Binario del que `strings` saca texto** — ya no hay código fuente,
   pero la cadena de la flag (o un fragmento, o un mensaje de depuración)
   sigue estando en claro dentro del binario compilado y
   `strings archivo | grep -i pico` (la misma herramienta de
   [[Triaje de archivos - file, strings y exiftool]]) la saca a la luz
   sin desensamblar nada.
4. **Binario donde `strings` no basta** — la flag no está en texto plano
   (se construye en tiempo de ejecución, está cifrada, o la comparación
   es lógica y no un string fijo). Aquí hace falta un
   desensamblador/decompilador como **Ghidra** para leer el código
   máquina traducido a algo legible y localizar la lógica de validación
   al nivel de instrucciones.

Cada peldaño reutiliza el reflejo del anterior: siempre se trata de
encontrar la validación y leer contra qué compara; lo que cambia es
cuánto trabajo hace falta para que esa lógica sea legible.

## Caso aplicado

[[vault-door-training]] — primer reto de la categoría en el vault,
ejemplo del peldaño 1: la flag vivía directamente en la comparación del
código fuente, sin ofuscación ni compilación de por medio.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Leer el código fuente - view-source, desminificado y señuelos]]

## Relacionadas

- [[vault-door-training]] — el writeup que estrena esta metodología.
- [[Triaje de archivos - file, strings y exiftool]] — `strings` es la herramienta compartida entre el peldaño 3 de esta escalera y el triaje forense.
- [[_Reverse Engineering|Reverse Engineering]] — índice de la categoría de writeups donde se aplica esta metodología.
