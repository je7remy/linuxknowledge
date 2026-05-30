---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-1]
actualizado: 2026-05-28
---

# Desafío del módulo 1

### 🧠 Pregunta 1

Rellene el espacio en blanco: Si utiliza código Python para reducir el esfuerzo manual necesario para gestionar una Lista de control de acceso, éste es un ejemplo de _____.

- análisis de datos
    
- automatización
    
- reasignación
    
- depuración
    

✅ Respuesta correcta:

automatización

📘 Explicación:

La automatización es, por definición, el uso de la tecnología (como un script de Python) para reducir el esfuerzo humano y manual en la realización de tareas comunes y repetitivas.

---

### 🧠 Pregunta 2

¿Qué ocurre con el siguiente Código?

Python

```
for username in failed_login:
print(username)
```

- La primera línea debe dividirse en dos, y `in failed_login:` debe sangrarse en la nueva línea.
    
- Ambas líneas no tienen sangría.
    
- La línea con `print(username)` no tiene sangría.
    
- La línea con `for username in failed_login:` no tiene sangría.
    

✅ Respuesta correcta:

La línea con print(username) no tiene sangría.

📘 Explicación:

Python utiliza la sangría (indentación) para definir bloques de código. El código que pertenece al cuerpo de un bucle for (la acción a repetir) debe estar indentado (generalmente con 4 espacios) para indicar que está dentro del bucle.

---

### 🧠 Pregunta 3

¿Cuáles de estos son Datos de cadena? Seleccione todas las que correspondan.

- `"100"`
    
- `100`
    
- `"user1"`
    
- `[100, 200, 300]`
    

✅ Respuesta correcta:

"100" y "user1"

📘 Explicación:

Los Datos de cadena (strings) se identifican porque son secuencias de caracteres encerradas entre comillas (ya sean dobles " o simples ').

- `100` es un **entero** (integer).
    
- `[100, 200, 300]` es una **lista** (list).
    

---

### 🧠 Pregunta 4

¿Cuáles son los valores posibles para el tipo de datos booleanos? Seleccione todos los que correspondan.

- `True`
    
- `!=`
    
- `>`
    
- `False`
    

✅ Respuesta correcta:

True y False

📘 Explicación:

El tipo de dato booleano (boolean) solo puede tener dos valores posibles: True (verdadero) o False (falso). Los símbolos != (no igual a) y > (mayor que) son operadores de comparación que evalúan a un valor booleano, pero no son valores booleanos en sí mismos.

---

### 🧠 Pregunta 5

¿Cuáles son las variables del siguiente código? Seleccione todas las que correspondan.

Python

```
username = "kcarter"
attempts = 5
print(username)
print(attempts)
print("locked")
```

- `username`
    
- `attempts`
    
- `"locked"`
    
- `"kcarter"`
    

✅ Respuesta correcta:

username y attempts

📘 Explicación:

Las variables son los nombres (identificadores) que se utilizan para almacenar valores. Están a la izquierda del operador de asignación (=). Los valores "kcarter" y "locked" son datos de tipo cadena (string) que están almacenados en una variable o se pasan directamente a una función, pero no son variables.

---

### 🧠 Pregunta 6

¿Qué código puede utilizar para devolver el tipo de datos del valor almacenado en la variable `input`?

- `type("string")`
    
- `print("type")`
    
- `print(input)`
    
- `type(input)`
    

✅ Respuesta correcta:

type(input)

📘 Explicación:

La función type() es la herramienta de Python diseñada para devolver el tipo de dato de cualquier objeto o variable que se le pase como argumento. type(input) devolverá el tipo de dato del valor que contiene la variable input.

---

### 🧠 Pregunta 7

...esta sentencia condicional no es correcta. ¿Cuáles son los problemas de esta sentencia condicional? Seleccione todo lo que corresponda.

Python

```
if update_status != "incomplete"
    print("schedule update")
```

- Faltan dos puntos (`:`) al final del encabezado condicional.
    
- Debe haber comillas alrededor de la variable `update_status`.
    
- La línea con `print("schedule update")` no debe tener sangría.
    
- El Operador no debe ser `!=`. Debe ser `==`.
    

✅ **Respuesta correcta:**

- Faltan dos puntos (`:`) al final del encabezado condicional.
    
- El Operador no debe ser `!=`. Debe ser `==`.
    

📘 Explicación:

Este código tiene dos errores:

1. **Error de Sintaxis:** Todas las sentencias `if`, `elif` y `else` en Python deben terminar con dos puntos (`:`).
    
2. **Error de Lógica:** El objetivo es imprimir el mensaje cuando el valor _es_ `"incomplete"`. El operador `!=` significa "no igual a". El operador correcto para "es igual a" es `==`.
    

---

### 🧠 Pregunta 8

Usted escribió el siguiente código:

Python

```
if attempts >= 5:
    print("locked")
else:
    print("try again")
```

Si el valor de la variable `attempts` es 3, ¿qué hará Python?

- Primero emita el mensaje "locked" y después emita el mensaje "try again"
    
- Emita el mensaje "try again"
    
- Emita el mensaje "locked"
    
- Primero emita el mensaje "try again" y después emita el mensaje "locked"
    

✅ Respuesta correcta:

Emita el mensaje "try again"

📘 **Explicación:**

1. Python evalúa la condición `if attempts >= 5`.
    
2. Sustituye el valor: `if 3 >= 5`.
    
3. Esta comparación es `False` (3 no es mayor ni igual que 5).
    
4. Dado que la condición `if` es `False`, Python ignora ese bloque y ejecuta el bloque `else`.
    
5. El resultado es que se imprime `"try again"`.
    

---

### 🧠 Pregunta 9

¿Qué Sentencia iterativa puede utilizar si desea imprimir "Security alert" cinco veces?

- `for i in range(5): print("Security alert")`
    
- `for i in range(6): print("Security alert")`
    
- `for i in [0, 5]: print("Security alert")`
    
- `for i in range(1,5): print("Security alert")`
    

✅ **Respuesta correcta:**

Python

```
for i in range(5):
    print("Security alert")
```

📘 Explicación:

La función range(5) genera una secuencia de 5 números: 0, 1, 2, 3, 4. El bucle for itera una vez por cada número en esa secuencia, ejecutando el comando print 5 veces.

- `range(6)` se ejecutaría 6 veces.
    
- `[0, 5]` se ejecutaría 2 veces.
    
- `range(1, 5)` se ejecutaría 4 veces (para 1, 2, 3, 4).
    

---

### 🧠 Pregunta 10

Desea imprimir todos los números pares entre 0 y 10 (en otras palabras, 0, 2, 4, 6, 8 y 10). ¿Cuál debería ser su siguiente línea de programación?

Python

```
count = 0
while count <= 10:
    print(count)
    # ¿Qué va aquí?
```

- `count = 1`
    
- `count = count + 2`
    
- `count = count + 1`
    
- `if count < 10:`
    

✅ Respuesta correcta:

count = count + 2

📘 Explicación:

El bucle comienza imprimiendo 0 (que es par). Para obtener el siguiente número par, debes sumar 2.

- Iteración 1: Imprime `0`. `count` se vuelve `0 + 2 = 2`.
    
- Iteración 2: Imprime `2`. `count` se vuelve `2 + 2 = 4`.
    
- ...así hasta imprimir `10`. `count` se vuelve `10 + 2 = 12`.
    
- En la siguiente comprobación, `12 <= 10` es `False` y el bucle termina.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[3- Términos del glosario del Módulo 1]]
