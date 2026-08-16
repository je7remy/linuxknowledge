---
tipo: laboratorio
tags: [ctf, picoctf, reverse-engineering, java, writeup]
actualizado: 2026-08-16
dificultad: fácil
fecha: 2026-08-16
---

# vault-door-training

Reto de **picoCTF / picoGym**, categoría **Reverse Engineering**, dificultad
**fácil** (50 puntos — el más bajo de la categoría, diseñado como rampa de
entrada). Resuelto el **16 de agosto de 2026**.

Estrena la categoría en el vault: primer reto de Reverse Engineering
resuelto, tras cerrar la capa fácil de [[_Web Exploitation|Web Exploitation]]
y avanzar en [[_Forensics|Forensics]].

## El cambio de mentalidad

En forense la pregunta era "¿qué *es* este archivo?" (ver
[[Triaje de archivos - file, strings y exiftool]]). En reversing la
pregunta cambia: **"¿qué *hace* este programa y qué espera de mí?"**. Ya
no se trata de identificar un tipo de archivo o extraer metadatos
estáticos, sino de entender el comportamiento — el flujo de ejecución —
de un programa.

## Qué te dan

El reto entrega el **código fuente** en Java (`VaultDoorTraining.java`),
no un binario compilado. Por eso no hace falta un desensamblador ni leer
ensamblador: basta con abrir el archivo en un editor de texto y leerlo
como código.

## El reflejo central

Buscar en el programa la parte que **decide si la flag introducida es
correcta** — la función o bloque de comprobación/comparación — y leer
**contra qué** compara la entrada del usuario. Cuando se dispone del
código fuente, la lógica de validación delata la respuesta directamente:
no hace falta ejecutar nada ni razonar sobre estados intermedios.

## Nota honesta de nivel

Este reto es "reversing con rueditas". La flag estaba escrita
literalmente dentro de la comparación del código — bastaba con copiarla
y pegarla. Es correcto que sea así en un reto de 50 puntos: enseña el
reflejo "busca la validación" en su forma más amable, **no** representa
el reversing real.

## Marco de progresión

Ver [[Reversing - de leer código fuente a desensamblar binarios]] para la
escalera completa. Resumen: código fuente legible (este reto) → lógica
ligeramente ofuscada → binario del que se puede sacar texto con
`strings` (la misma herramienta que aparece en
[[Triaje de archivos - file, strings y exiftool]], reutilizada aquí) →
binario donde `strings` no basta y toca un desensamblador como Ghidra.

<!-- No se incluye la flag: esta nota sirve para repetir el ejercicio, no para saltárselo. -->

---

## Navegación

- ⬆️ Carpeta padre: [[_Reverse Engineering|Reverse Engineering]]

## Relacionadas

- [[_Reverse Engineering|Reverse Engineering]] — índice de la categoría que estrena este writeup.
- [[Reversing - de leer código fuente a desensamblar binarios]] — metodología completa, con este reto como primer peldaño.
- [[Triaje de archivos - file, strings y exiftool]] — `strings` reaparece en el siguiente peldaño del reversing, ya usado en forense.
