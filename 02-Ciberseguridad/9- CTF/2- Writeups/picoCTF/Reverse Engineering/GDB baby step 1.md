---
tipo: laboratorio
tags: [ctf, picoctf, reverse-engineering, gdb, ensamblador, x86-64, writeup]
dificultad: medio
fecha: 2026-08-22
actualizado: 2026-08-22
---

# GDB baby step 1

Reto de **picoCTF / picoGym**, categoría **Reverse Engineering**, etiquetado
por la plataforma como **dificultad Medium** — no fácil, aunque el nombre
("baby step") suene a introductorio. Resuelto el **22 de agosto de 2026**.
Segundo reto de la categoría en el vault, tras [[vault-door-training]], y
el primero que exige leer ensamblador de verdad en lugar de código fuente.

## Qué te dan

Un **binario compilado**, no código fuente. El objetivo: hallar el valor
que queda en el registro `eax` al final de la función `main`, expresarlo
en decimal y envolverlo como `picoCTF{n}`. La propia descripción del reto
da el ejemplo de formato: si `eax` valiera `0x11`, la flag sería
`picoCTF{17}`.

Esto ya marca el salto respecto a [[vault-door-training]]: ahí la
validación estaba escrita en claro en código fuente Java; aquí no hay
código fuente ni cadena de texto que buscar con `strings` — el valor vive
como un inmediato dentro de una instrucción de ensamblador.

## El primer atajo, y por qué falla

Antes de abrir un desensamblador, hay un atajo tentador: ejecutar el
binario y leer su código de salida.

```
./gdb-baby-step1
echo $?
```

No es una idea disparatada — tiene lógica real detrás. Por la **ABI de
System V** (la convención de llamada estándar en Linux x86-64), el valor
de retorno de `main` queda en `eax`/`rax`, y el kernel toma ese valor como
*exit status* del proceso cuando termina.

El problema es que el **exit status en Linux está truncado a 8 bits**:
solo puede representar el rango 0–255, porque el kernel se queda con
`eax & 0xFF` — el byte bajo del registro, descartando todo lo demás. Si el
valor real de `eax` es mayor que 255, `$?` devuelve un número que
**parece** una respuesta válida pero que en realidad es solo un
fragmento truncado. No hay forma de reconstruir el valor original a
partir de ese número: infinitos valores de 32 bits comparten el mismo
byte bajo.

Este atajo, en este reto concreto, **no es fiable** — y esa es
precisamente la lección conceptual que el ejercicio quiere dejar: no
todo dato "observable" del comportamiento de un programa es el dato
completo.

## El enfoque correcto: análisis estático con gdb

`disassemble` en gdb es **análisis estático**: lee lo que el binario
*va a hacer* sin necesidad de ejecutarlo. Esto contrasta con el atajo
anterior, que era un intento de análisis dinámico (ejecutar y observar)
que se topó con un dato degradado por el propio sistema operativo.

Pasos:

```
gdb ./gdb-baby-step1
```

Al arrancar aparece el aviso `No debugging symbols found` — el binario no
se compiló con `-g`, así que gdb no tiene información de tipos, variables
locales ni líneas de código fuente. Pero **`main` sigue siendo un símbolo
reconocible**: la tabla de símbolos de un ejecutable normal conserva los
nombres de las funciones exportadas aunque falte la información de
depuración completa. Por eso se puede seguir refiriendo a la función por
su nombre en lugar de por dirección.

```
(gdb) disassemble main
```

Esto vuelca el ensamblador completo de la función:

```
Dump of assembler code for function main:
   0x0000000000401136 <+0>:	endbr64
   0x000000000040113a <+4>:	push   %rbp
   0x000000000040113b <+5>:	mov    %rsp,%rbp
   0x000000000040113e <+8>:	mov    $0x<REDACTADO>,%eax
   0x0000000000401143 <+13>:	pop    %rbp
   0x0000000000401144 <+14>:	ret
End of assembler dump.
```

(El inmediato real está redactado a propósito — ver nota sobre la flag
más abajo.)

**El patrón clave**, y el reflejo que vale la pena memorizar: cerca del
final de la función, justo antes de `pop %rbp` / `ret`, hay una
instrucción `mov $0x<valor>,%eax`. Esa es la última escritura sobre
`eax` antes del retorno, así que es literalmente el valor que la función
devuelve — completo, en 32 bits, sin el truncamiento que sufre `$?`. En
este binario el valor está *hardcodeado* directamente ahí: no hay
cálculo, ni entrada del usuario, ni rama condicional que lo module. Eso
significa que **ni siquiera hace falta ejecutar el programa**: el valor
se lee directamente del ensamblador estático.

El último paso es convertir ese inmediato hexadecimal a decimal. gdb
sirve de calculadora integrada:

```
(gdb) print 0x<REDACTADO>
$1 = <REDACTADO>
```

Ese decimal es la `n` de `picoCTF{n}`.

## La confirmación de la trampa

Vale la pena cerrar el círculo con el atajo del principio. Al comparar
el `$?` obtenido al ejecutar el binario contra el valor real hallado con
`disassemble`, se confirma la trampa: `$?` mostraba un número pequeño,
mientras que el valor real en `eax` era considerablemente mayor — y su
**byte bajo coincidía exactamente** con lo que mostraba `$?`.

Un ejemplo hipotético para ilustrar el mecanismo sin usar el valor real
del reto: si `eax` valiera `0x1F042`, el kernel calcularía
`0x1F042 & 0xFF = 0x42 = 66`, así que `echo $?` mostraría `66` —
ocultando por completo los bytes altos `0x1F0`. Cualquier otro valor que
termine en `0x42` (`0x0042`, `0x9942`, `0xABC42`, …) produciría el mismo
`$? = 66`. Desde el exit status es **imposible** distinguir cuál de esos
valores es el real; solo `disassemble` lo revela sin ambigüedad.

## Técnicas transversales (para reutilizar en otros retos)

- **`disassemble <función>` = análisis estático**: leer qué hace un
  binario sin ejecutarlo, a diferencia de observar su comportamiento en
  tiempo de ejecución.
- **Reflejo de localización**: buscar, cerca del `ret` de una función, la
  última instrucción que escribe sobre el registro de retorno
  (`eax`/`rax`) — esa es la que fija el valor devuelto.
- **`print 0x...` en gdb** funciona como conversor rápido hexadecimal →
  decimal, sin salir de la sesión de depuración.
- **Notación AT&T** (la que usa gdb por defecto): `mov origen, destino`
  — el destino va a la **derecha**, al revés que en notación Intel.
  `%` prefija registros (`%eax`, `%rbp`), `$` prefija valores inmediatos
  (`$0x11`).
- **ABI de System V**: el valor de retorno de una función va en
  `eax`/`rax`; el kernel toma el valor de retorno de `main` como *exit
  status* del proceso — y lo trunca a 8 bits. De ahí nace la trampa de
  este reto.
- **Principio general**: desconfiar de atajos que truncan o resumen un
  dato (`$?` aquí es el ejemplo perfecto) cuando lo que se necesita es el
  valor completo y exacto.

## Nota honesta de nivel

A pesar del nombre "baby step", picoCTF etiqueta este reto como
**Medium**, no como introductorio. Tiene sentido: a diferencia de
[[vault-door-training]] (código fuente en claro, copiar y pegar), aquí
hace falta reconocer una convención de la ABI, saber leer notación AT&T,
usar un desensamblador y — el punto que de verdad separa este reto de uno
fácil — **darse cuenta de que el atajo obvio (`$?`) es una trampa** y
entender *por qué* falla, no solo evitarlo por instinto.

<!-- No se incluye la flag ni el inmediato hexadecimal real: esta nota documenta la técnica para poder repetir el ejercicio, no para saltárselo. -->

---

## Navegación

- ⬆️ Carpeta padre: [[_Reverse Engineering|Reverse Engineering]]
- ⬅️ Anterior: [[vault-door-training]]

## Relacionadas

- [[_Reverse Engineering|Reverse Engineering]] — índice de la categoría, ahora con dos retos.
- [[Reversing - de leer código fuente a desensamblar binarios]] — metodología ampliada con el peldaño de análisis estático con gdb que aplica este writeup.
- [[vault-door-training]] — reto anterior de la categoría; ahí la validación estaba en código fuente legible, aquí hay que leerla en ensamblador.
