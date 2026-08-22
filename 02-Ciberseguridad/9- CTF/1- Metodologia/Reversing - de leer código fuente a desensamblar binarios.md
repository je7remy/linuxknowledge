---
tipo: cheatsheet
tags: [ctf, picoctf, reverse-engineering, java, ghidra, gdb, strings, metodologia]
actualizado: 2026-08-22
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
   desensamblador/decompilador como **Ghidra**, o directamente **gdb**
   para binarios pequeños, para leer el código máquina traducido a algo
   legible y localizar la lógica de validación al nivel de
   instrucciones.

Cada peldaño reutiliza el reflejo del anterior: siempre se trata de
encontrar la validación y leer contra qué compara; lo que cambia es
cuánto trabajo hace falta para que esa lógica sea legible.

## Análisis estático con gdb (peldaño 4, versión ligera)

Cuando el binario es pequeño y no hace falta un decompilador con vista en
pseudocódigo (Ghidra), **gdb solo con `disassemble`** alcanza. Es
análisis **estático**: se lee lo que el binario va a hacer sin
ejecutarlo, al contrario que depurar paso a paso observando el
comportamiento en tiempo real. Caso aplicado: [[GDB baby step 1]].

Flujo:

1. `gdb ./binario` — aunque aparezca `No debugging symbols found`, los
   símbolos de funciones normales (`main`, etc.) suelen sobrevivir en la
   tabla de símbolos incluso sin información de depuración completa. Se
   puede seguir referenciando la función por nombre.
2. `disassemble main` (o la función que corresponda) vuelca el
   ensamblador. gdb usa **notación AT&T** por defecto: `mov origen,
   destino` (el destino va a la **derecha**, al revés que en notación
   Intel), `%` prefija registros (`%eax`, `%rbp`) y `$` prefija
   inmediatos (`$0x11`).
3. **Reflejo de localización del valor de retorno**: buscar, cerca del
   `pop %rbp` / `ret` final, la última instrucción que escribe sobre
   `eax`/`rax` — normalmente un `mov $0x<valor>,%eax`. Esa es la
   instrucción que fija lo que la función devuelve.
4. `print 0x<valor>` usa gdb como conversor rápido hexadecimal →
   decimal, sin salir de la sesión.

**Trampa a tener presente — el exit status truncado a 8 bits.** Por la
ABI de System V, el valor de retorno de `main` queda en `eax`, y el
kernel lo usa como *exit status* del proceso (`echo $?` tras ejecutar el
binario). Pero el exit status en Linux **solo tiene 8 bits** (rango
0–255): el kernel se queda con `eax & 0xFF`, el byte bajo, descartando
el resto. Si el valor real de `eax` supera 255, `$?` devuelve un número
que parece válido pero es solo un fragmento — infinitos valores de 32
bits comparten el mismo byte bajo, así que no hay forma de reconstruir
el original desde ahí. Ejecutar y mirar `$?` es un atajo tentador
(análisis dinámico rápido) pero **no fiable** cuando el valor buscado
puede exceder un byte; `disassemble` da el valor crudo y completo sin
ese riesgo. Principio general: desconfiar de atajos que truncan un dato
cuando hace falta el valor exacto.

## Caso aplicado

- [[vault-door-training]] — primer reto de la categoría en el vault,
  ejemplo del peldaño 1: la flag vivía directamente en la comparación del
  código fuente, sin ofuscación ni compilación de por medio.
- [[GDB baby step 1]] — ejemplo del peldaño 4 en su versión ligera: sin
  código fuente, valor de retorno hardcodeado localizado con
  `disassemble` y `print`, y la trampa del exit status truncado a 8 bits.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Leer el código fuente - view-source, desminificado y señuelos]]

## Relacionadas

- [[vault-door-training]] — el writeup que estrena esta metodología (peldaño 1).
- [[GDB baby step 1]] — writeup que aplica el peldaño 4: análisis estático con gdb y la trampa del exit status truncado.
- [[Triaje de archivos - file, strings y exiftool]] — `strings` es la herramienta compartida entre el peldaño 3 de esta escalera y el triaje forense.
- [[_Reverse Engineering|Reverse Engineering]] — índice de la categoría de writeups donde se aplica esta metodología.
