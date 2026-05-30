---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Índices y cortes de cadena

### 🧠 Índices y Cortes de Cadena

### 📘 Introducción: Buscar en Cadenas

En Seguridad, hay varias razones por las que podríamos necesitar buscar en una cadena. Por ejemplo, es posible que necesitemos localizar un nombre de usuario en un registro de Seguridad. O bien, si descubrimos que una dirección IP determinada está asociada a un software malicioso, es posible que busquemos esta dirección en un registro de red.

Y el primer paso para poder usar Python de esta manera es aprender sobre el **índice** de caracteres de una cadena.

### ⚙️ El Índice de Caracteres

El **índice** es un número asignado a cada elemento de una secuencia que indica su posición. Por lo tanto, el índice es la posición de cada carácter en una cadena.

Empecemos con la cadena «HOLA». A cada carácter de la cadena se le asigna un índice.

> **Regla Clave:** En Python, empezamos a contar los índices desde **0**.

|**Carácter**|**H**|**O**|**L**|**A**|
|---|---|---|---|---|
|**Índice**|**0**|**1**|**2**|**3**|

#### Sintaxis de Indexación

Al colocar un índice entre corchetes `[]` después de una cadena, se devuelve el carácter de ese índice.

Python

```
# Coloquemos el índice 1 entre corchetes después de «HOLA»
print("HOLA"[1])
```

📤 **Salida:**

```
O
```

Esto devolvió el carácter «O». Recuerde que los índices comienzan en 0, por lo que un índice de 1 no es el primer carácter de la palabra.

---

### ⚙️ Rebanadas (Slicing)

Pero, ¿y si queremos que devuelva más de un carácter? Podemos extraer una mayor parte de una cadena especificando un conjunto de índices. Esto se denomina **rebanada (slice)**.

Al tomar un sector de una cadena, especificamos dónde comienza el sector (`inicio`) y dónde termina (`fin`).

- El primer índice (`inicio`) **se incluye** en la salida.
    
- El segundo índice (`fin`) **no se incluye** en el resultado final. (Python detiene el segmento en el elemento _anterior_ al segundo índice).
    

#### Sintaxis de Rebanada

Por ejemplo, si quisiéramos tomar las letras O-L de «HOLA», comenzaríamos el intervalo desde el índice 1, pero terminaríamos antes del índice 3.

Python

```
# Comienza en el índice 1 (O)
# Termina ANTES del índice 3 (A)
print("HOLA"[1:3])
```

📤 **Salida:**

```
OL
```

Ahí está la porción que queríamos.

---

### ⚙️ Búsqueda con el Método `.index()`

Ahora que sabemos cómo describir la ubicación de un carácter, aprendamos cómo buscar en una cadena. Para hacer esto, necesitamos usar el método `index()`.

El método `index()` busca la **primera aparición** de la entrada en una cadena y devuelve su ubicación (índice).

Ejemplo 1:

Supongamos que queremos usar el método index() para encontrar el carácter «E» en la cadena «HELLO».

Python

```
# Usamos el carácter que queremos encontrar como argumento del método
# Recuerde: Python distingue entre mayúsculas y minúsculas
print("HELLO".index("E"))
```

📤 **Salida:**

```
1
```

Esto devolvió el número 1. Esto se debe a que «E» tiene un valor de índice de 1.

Ejemplo 2 (Caracteres Repetidos):

Ahora, exploremos un ejemplo en el que un carácter se repite varias veces. Intentemos buscar el carácter «L».

Python

```
print("HELLO".index("L"))
```

📤 **Salida:**

```
2
```

El resultado es el índice 2. Esto nos indica que el método solo identificó la **primera aparición** del carácter «L» (en el índice 2) y no la segunda (en el índice 3). Este es un detalle importante a tener en cuenta.

Como analista de Seguridad, aprender a trabajar con índices te permite encontrar ciertas partes de una cadena. Por ejemplo, si necesitas encontrar la ubicación del símbolo `@` en un correo electrónico, puedes usar el método `index()` para encontrar lo que buscas con una línea de código.

---

### ⚠️ Propiedad Clave: Las Cadenas son Inmutables

Ahora vamos a centrar nuestra atención en una propiedad importante de las cadenas. ¿Alguna vez has escuchado la expresión «algunas cosas nunca cambian»? Bueno, en Python, también podemos decir esto acerca de las cadenas.

**Las cadenas son inmutables.**

En Python, «inmutable» significa que **no se puede cambiar** una vez creado y asignado un valor.

Ejemplo de Error (Desglose):

Vamos a asignar la cadena «HELLO» a la variable my_string. Ahora, si queremos cambiar el carácter «E» por una «A» (para que my_string tenga el valor «HALLO»), podríamos optar por usar la notación de índice:

Python

```
my_string = "HELLO"

# Intentar reasignar el carácter en el índice 1
my_string[1] = "A"
```

📤 **Salida (Error):**

```
TypeError: 'str' object does not support item assignment
```

`my_string` es inmutable, por lo que no podemos hacer cambios como este.

---

### 💡 Resumen y Próximos Pasos

¡Y ahí lo tienes! Acabas de aprender a indexar (`[1]`) y dividir (`[1:4]`) cadenas. También has visto que las cadenas son inmutables. No puede reasignar caracteres después de que se haya definido una cadena.


### 🧠 Pregunta

¿Qué salida tiene el siguiente código?

Python

```
print("HELLO"[2:4])
```

- `"LLO"`
    
- `"EL"`
    
- `"LL"`
    
- `"E"`
    

---

### ✅ Respuesta correcta:

`"LL"`

### 📘 Explicación:

El código `print("HELLO"[2:4])` da como salida `"LL"`. Esto se debe a cómo funciona el **corte (slicing)** en Python:

1. El primer índice de la rebanada (`2`) es **inclusivo** (la rebanada comienza _en_ este índice).
    
2. El segundo índice de la rebanada (`4`) es **exclusivo** (la rebanada se detiene _antes_ de este índice).
    

Veamos los índices de la cadena "HELLO":

|**Carácter**|**H**|**E**|**L**|**L**|**O**|
|---|---|---|---|---|---|
|Índice|0|1|**2**|**3**|4|

- La rebanada **comienza** en el índice 2 (el carácter "L").
    
- La rebanada **termina** _antes_ del índice 4 (es decir, en el índice 3, que es el segundo "L").
    

Por lo tanto, la rebanada `[2:4]` extrae los caracteres en los índices 2 y 3, lo que da como resultado `"LL"`.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[2- Operaciones de cadena]]
- ➡️ Siguiente: [[4- Cadenas y el analista de Seguridad]]
