
### 🧠 Funciones Integradas (Explicación)

Anteriormente, usted exploró las funciones incorporadas en Python, incluyendo `print()`, `type()`, `max()`, y `sorted()`. Funciones integradas son funciones que existen dentro de Python y pueden ser llamadas directamente. En esta lectura, las explorará más a fondo y también aprenderá sobre la función `min()`. Además, revisará cómo pasar la salida de una función a otra función.

#### `print()`

La función print() da salida a un objeto especificado en la pantalla. La función print() es una de las más utilizadas en Python porque le permite dar salida a cualquier detalle de su código.

Para utilizar la función print(), debe pasar el objeto que desea imprimir como argumento a la función. La función print() acepta cualquier número de argumentos, separados por una coma, e imprime todos ellos. Por ejemplo, puede ejecutar el siguiente código que imprime una cadena, una variable, otra cadena y un número entero juntos:

Python

```
username = "jrafael"
print("El usuario", username, "intentó iniciar sesión", 3, "veces.")
```

📤 **Salida:**

```
El usuario jrafael intentó iniciar sesión 3 veces.
```

#### `type()`

La función type() devuelve el tipo de datos de su argumento. La función type() le ayuda a realizar un seguimiento de los tipos de datos de las variables para evitar errores a lo largo de su código.

Para utilizarla, se pasa el objeto como argumento, y devuelve su tipo de datos. Sólo acepta un argumento. Por ejemplo, puede especificar type("security") o type(7).

#### Pasar una función a otra

Cuando trabaje con funciones, a menudo necesitará pasarlas a través de `print()` si desea que el tipo de datos aparezca en pantalla. Este es el caso cuando se utiliza una función como `type()`. Considere el siguiente código:

Python

```
print(type("security"))
```

📤 **Salida:**

```
<class 'str'>
```

Muestra `<class 'str'>`, lo que significa que el argumento pasado a la función `type()` es una cadena. Esto sucede porque la función `type()` se procesa primero y su salida se pasa como argumento a la función `print()`.

#### `max()` y `min()`

La función max() devuelve la entrada numérica más grande que se le haya pasado. La función min() devuelve la entrada numérica más pequeña que se le haya pasado.

Las funciones max() y min() aceptan argumentos de múltiples valores numéricos o de un iterable como una lista, y devuelven el mayor o el menor valor respectivamente.

En un contexto de ciberseguridad, podría utilizar estas funciones para identificar la Sesión más larga o más corta en la que se registró un usuario. Si un usuario concreto se conectó siete veces durante una semana, y usted almacenó sus tiempos de acceso en minutos en una lista, puede utilizar las funciones `max()` y `min()` para encontrar e imprimir sus sesiones más larga y más corta:

Python

```
time_list = [15, 42, 8, 67, 21, 10, 3]
print("Sesión más larga (min):", max(time_list))
print("Sesión más corta (min):", min(time_list))
```

📤 **Salida:**

```
Sesión más larga (min): 67
Sesión más corta (min): 3
```

#### `sorted()`

La función `sorted()` ordena los componentes de una lista. La función `sorted()` también funciona sobre cualquier iterable, como una cadena, y devuelve los elementos ordenados en una lista. Por defecto, los ordena en orden ascendente. Cuando se le da un iterable que contiene números, los ordena de menor a mayor; esto incluye iterables que contienen datos numéricos, así como iterables que contienen Datos de cadena que comienzan con números. Un iterable que contenga cadenas que empiecen por caracteres alfabéticos se ordenará alfabéticamente.

La función `sorted()` toma como entrada un iterable, como una lista o una cadena. Así, por ejemplo, puede utilizar el siguiente código para ordenar la lista de sesiones de inicio de sesión de la más corta a la más larga:

Python

```
time_list = [15, 42, 8, 67, 21, 10, 3]
print(sorted(time_list))
```

📤 **Salida:**

```
[3, 8, 10, 15, 21, 42, 67]
```

Esto muestra la lista ordenada.

La función sorted() no cambia el iterable que ordena. El código siguiente lo ilustra:

Python

```
time_list = [15, 42, 8, 67, 21, 10, 3]
print("Lista ordenada:", sorted(time_list))
print("Lista original (sin cambios):", time_list)
```

📤 **Salida:**

```
Lista ordenada: [3, 8, 10, 15, 21, 42, 67]
Lista original (sin cambios): [15, 42, 8, 67, 21, 10, 3]
```

La primera función `print()` muestra la lista ordenada. Sin embargo, la segunda función `print()`, que no incluye la función `sorted()`, muestra la lista tal y como se asignó a `time_list` en la primera línea de código.

Otro detalle importante sobre la función `sorted()` es que no puede tomar listas o cadenas que tengan elementos de más de un tipo de datos. Por ejemplo, no puede utilizar la lista `[1, 2, "hello"]`.

---

### 💡 Puntos Clave

Las Funciones integradas son poderosas herramientas en Python que le permiten realizar tareas con un simple comando. La función `print()` imprime sus argumentos en la pantalla, la función `type()` devuelve el tipo de datos de su argumento, las funciones `min()` y `max()` devuelven los valores más pequeño y más grande de un iterable respectivamente, y `sorted()` organiza su argumento.

---

### 🔗 Recursos para obtener más Información

Estas son sólo algunas de las funciones integradas de Python. Puede seguir aprendiendo sobre otras por su cuenta:

- **Documentación de la Biblioteca estándar de Python**: Lista de las funciones integradas de Python e Información sobre cómo utilizarlas.