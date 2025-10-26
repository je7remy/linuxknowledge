
### 🧠 Pregunta 1

¿Cuál es el resultado del siguiente código?

```python
print(len("125"))
```

  * 3
  * 5
  * 10
  * 8

✅ **Respuesta correcta:**
3

📘 **Justificación:**
La función `len()` devuelve el número de caracteres en una cadena. La cadena `"125"` tiene tres caracteres: `'1'`, `'2'` y `'5'`.

-----

### 🧠 Pregunta 2

¿Cuál es el resultado cuando se aplica `.upper()` a una cadena?

  * Se extrae de la cadena el carácter que aparece con más frecuencia en ella y se devuelve.
  * El valor de la cadena se reasigna para contener todas las letras mayúsculas.
  * El valor de la cadena se reasigna al valor de la cadena de la línea que la precede.
  * Se devuelve una copia de la cadena con todas las letras mayúsculas.

✅ **Respuesta correcta:**
Se devuelve una **copia** de la cadena con todas las letras mayúsculas.

📘 **Justificación:**
El método `.upper()` **no modifica** la cadena original (porque las cadenas son inmutables). En su lugar, **devuelve una nueva cadena** donde todos los caracteres alfabéticos están en mayúsculas.

-----

### 🧠 Pregunta 3

En la Cadena `"network"`, ¿qué carácter tiene un índice de 1?

  * `"e"`
  * `"n"`
  * `"k"`
  * `"t"`

✅ **Respuesta correcta:**
`"e"`

📘 **Justificación:**
La indexación en Python comienza en 0.

  * Índice 0: `"n"`
  * Índice **1**: `"e"`
  * Índice 2: `"t"`
  * ... y así sucesivamente.

-----

### 🧠 Pregunta 4

Necesita extraer un trozo de un identificador de empleado (`employee_id = "abc237x430def"`). Concretamente, debe extraer los caracteres con índices de 3, 4, 5 y 6. Complete el código Python...

```python
employee_id = "abc237x430def" # Asumiendo un ID de ejemplo
# COMPLETAR CÓDIGO AQUÍ
# slice_id = employee_id[?:?]
# print(slice_id)
slice_id = employee_id[3:7]
print(slice_id)
```

¿Qué cadena muestra el código?

  * `"x430"`
  * `"237x"`
  * `"37x4"`
  * `"7x43"`

✅ **Respuesta correcta:**
`"237x"`

📘 **Justificación:**
El corte `[3:7]` extrae caracteres desde el índice 3 (inclusive) hasta *antes* del índice 7 (exclusivo).

  * Índice 3: `"2"`
  * Índice 4: `"3"`
  * Índice 5: `"7"`
  * Índice 6: `"x"`
    El resultado es `"237x"`.

-----

### 🧠 Pregunta 5

¿Cuál es el resultado del siguiente código?

```python
list1  = [1, 2, 3]
list2 = ["a", "b", "c"]
print(list1 + list2)
```

  * `[6, "abc"]`
  * `[1, "a", 2, "b", 3, "c"]`
  * Un mensaje de error
  * `[1, 2, 3, "a", "b", "c"]`

✅ **Respuesta correcta:**
`[1, 2, 3, "a", "b", "c"]`

📘 **Justificación:**
El operador `+` se usa para la **concatenación** de listas. Simplemente une los elementos de la segunda lista al final de la primera lista, creando una nueva lista combinada.

-----

### 🧠 Pregunta 6

Una variable llamada `my_list` contiene la lista `[1, 2, 3, 4]`. ¿Qué línea de programación elimina el último elemento de la lista?

  * `remove(my_list, 4)`
  * `my_list.remove(3)`
  * `remove (my_list, 3)`
  * `my_list.remove(4)`

✅ **Respuesta correcta:**
`my_list.remove(4)`

📘 **Justificación:**
El método `.remove()` elimina la primera aparición del **valor** especificado. Para eliminar el último elemento, que tiene el valor `4`, se usa `my_list.remove(4)`. Las opciones con `remove(my_list, ...)` son sintácticamente incorrectas, y `my_list.remove(3)` eliminaría el valor `3`, no el último elemento.

-----

### 🧠 Pregunta 7

¿Qué es un algoritmo?

  * Un conjunto de reglas para resolver un problema
  * Una función que encuentra coincidencias con un Patrón
  * Una función que devuelve información
  * Un conjunto de directrices para mantener la coherencia del código

✅ **Respuesta correcta:**
Un conjunto de reglas para resolver un problema.

📘 **Justificación:**
Esta es la definición fundamental de un algoritmo: una serie de pasos o reglas definidas para lograr un objetivo específico o resolver un problema.

-----

### 🧠 Pregunta 8

¿Cuál de las siguientes cadenas devolvería Python como coincidencias con el patrón de expresión regular de `"\w"`? (Seleccione todas las que correspondan).

  * `"W"`
  * `"security"`
  * `"1B"`
  * `"2"`

✅ **Respuestas correctas:**

  * `"W"`
  * `"2"`

📘 **Justificación:**
El patrón `\w` coincide con **un solo** carácter alfanumérico (letra, número o guion bajo).

  * `"W"` es un solo carácter alfanumérico.
  * `"2"` es un solo carácter alfanumérico.
  * `"security"` y `"1B"` contienen *más de un* carácter.

-----

### 🧠 Pregunta 9

¿Qué Módulo necesita importar para utilizar expresiones regulares en Python?

  * `re`
  * `os`
  * `time`
  * `csv`

✅ **Respuesta correcta:**
`re`

📘 **Justificación:**
El módulo `re` es la biblioteca estándar de Python para trabajar con **r**egular **e**xpressions (expresiones regulares).

-----

### 🧠 Pregunta 10

¿Qué hace el Método del Código `username_list.append("bmoreno")`?

  * Devuelve todas las coincidencias con el patrón "bmoreno" en la lista username\_list
  * Añade "bmoreno" al final de la lista username\_list
  * Inserta "bmoreno" al principio de la lista username\_list
  * Actualiza a mayúsculas todas las instancias de "bmoreno" en la lista username\_list

✅ **Respuesta correcta:**
Añade `"bmoreno"` al final de la lista `username_list`.

📘 **Justificación:**
El método `.append()` se utiliza específicamente para añadir un elemento al **final** de una lista existente.


---
# Mas preguntas

---

### 🧠 Pregunta 1

¿Qué línea de código devuelve el número de caracteres de la cadena asignada a la variable `username`?

✅ **Respuesta correcta:**`print(len(username))`

📘 **Justificación:** La función integrada **`len()`** se utiliza para obtener la longitud (número de elementos o caracteres) de un objeto, como una cadena. `str()` convierte a cadena, y `.len()` o `.str()` no son métodos/funciones válidos para obtener la longitud.

---

### 🧠 Pregunta 2

¿Qué línea de código devuelve una copia de la cadena `"HG91AB2"` como `"hg91ab2"`?

✅ **Respuesta correcta:**`print("HG91AB2".lower())`

📘 **Justificación:** El método de cadena **`.lower()`** devuelve una copia de la cadena con todos los caracteres en minúsculas. Los métodos se aplican _después_ de la cadena usando un punto (`.`). Las otras sintaxis intentan usar `lower` como una función independiente o de forma incorrecta.

---

### 🧠 Pregunta 3

En la Cadena `"network"`, ¿qué carácter tiene un índice de 1?

✅ **Respuesta correcta:**`"e"`

📘 **Justificación:** La indexación en Python comienza en **0**.

- Índice 0: `"n"`
    
- Índice **1**: `"e"`
    

---

### 🧠 Pregunta 4

Necesita extraer un trozo de un identificador de empleado (`employee_id = "abc237x430def"`). Concretamente, debe extraer los caracteres con índices de 3, 4, 5 y 6. Complete el código Python...

Python

```
employee_id = "abc237x430def" # Asumiendo un ID de ejemplo
slice_id = employee_id[3:7] # Código completado
print(slice_id)
```

¿Qué cadena muestra el código?

✅ **Respuesta correcta:**`"237x"`

📘 **Justificación:** El corte `[3:7]` extrae caracteres desde el índice 3 (inclusive) hasta _antes_ del índice 7 (exclusivo), resultando en los caracteres en los índices 3, 4, 5 y 6.

---

### 🧠 Pregunta 5

¿Cuál es el resultado del siguiente código?

Python

```
list1  = [1, 2, 3]
list2 = ["a", "b", "c"]
print(list1 + list2)
```

✅ **Respuesta correcta:**`[1, 2, 3, "a", "b", "c"]`

📘 **Justificación:** El operador `+` realiza la **concatenación** de listas, uniendo los elementos de la segunda lista al final de la primera.

---

### 🧠 Pregunta 6

Una variable llamada `my_list` contiene la lista `[1, 2, 3, 4]`. ¿Qué línea de programación elimina el último elemento de la lista?

✅ **Respuesta correcta:**`my_list.remove(4)`

📘 **Justificación:** El método **`.remove()`** elimina la primera aparición del **valor** especificado. El último elemento tiene el valor `4`. Las sintaxis `remove(...)` son incorrectas porque `.remove()` es un método de lista.

---

### 🧠 Pregunta 7

¿Qué es un algoritmo?

✅ **Respuesta correcta:** Un conjunto de reglas para resolver un problema.

📘 **Justificación:** Un algoritmo es una secuencia de pasos definidos diseñados para realizar una tarea o resolver un problema específico.

---

### 🧠 Pregunta 8

¿A qué corresponde el símbolo `\w` en una expresión regular?

✅ **Respuesta correcta:** Cualquier carácter alfanumérico.

📘 **Justificación:**`\w` coincide con cualquier letra (mayúscula o minúscula), número o el guion bajo (`_`).

---

### 🧠 Pregunta 9

¿Qué Módulo necesita importar para utilizar expresiones regulares en Python?

✅ **Respuesta correcta:**`re`

📘 **Justificación:** El módulo **`re`** es la biblioteca estándar de Python para trabajar con **r**egular **e**xpressions (expresiones regulares).

---

### 🧠 Pregunta 10

¿Qué hace el código `device_ids.append("h32rb17")`?

✅ **Respuesta correcta:** Añade `"h32rb17"` al final de la lista `device_ids`.

📘 **Justificación:** El método **`.append()`** se usa específicamente para añadir un elemento al **final** de una lista existente.