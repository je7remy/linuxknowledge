
### 🧠 Listas y el Analista de Seguridad

Anteriormente, examinó cómo utilizar la notación entre corchetes para acceder a los elementos de una lista y cambiarlos, así como algunos métodos fundamentales para trabajar con listas. Esta lectura repasará estos conceptos con nuevos ejemplos, introducirá el método `.index()` tal y como se aplica a las listas y destacará cómo se utilizan las listas en un contexto de ciberseguridad.

#### Datos de lista en un entorno de seguridad

Como analista de Seguridad, trabajará frecuentemente con listas en Python. **Datos de lista** es una estructura de datos que consiste en una colección de datos en forma secuencial. Puede utilizar listas para almacenar múltiples elementos en una única variable. Una sola lista puede contener múltiples tipos de datos.

En un contexto de ciberseguridad, las listas pueden utilizarse para almacenar nombres de usuario, direcciones IP, URL, ID de dispositivos y datos.

Colocar datos dentro de una lista le permite trabajar con ellos de diversas maneras. Por ejemplo, podría iterar a través de una lista de ID de dispositivos utilizando un bucle `for` para realizar las mismas acciones para todos los elementos de la lista. Podría incorporar una sentencia condicional para realizar estas acciones sólo si los ID de dispositivo cumplen determinadas condiciones.

---

### 📘 Trabajar con índices en listas

#### Índices

Al igual que las cadenas, puede trabajar con listas a través de sus índices, y los índices comienzan en 0. En una lista, se asigna un índice a cada elemento de la lista.

Esta tabla contiene el índice de cada elemento de la lista `["elarson", "fgarcia", "tshah", "sgilmore"]`:

|**elemento**|**índice**|
|---|---|
|"elarson"|0|
|"fgarcia"|1|
|"tshah"|2|
|"sgilmore"|3|

#### Notación entre corchetes

De forma similar a las cadenas, puede utilizar la **notación entre corchetes** para extraer elementos o trozos de una lista. Para extraer un elemento de una lista, después de la lista o de la variable que la contiene, añada corchetes que contengan el índice del elemento. El siguiente ejemplo extrae el elemento con índice 2 de la variable `username_list` y lo imprime. Puede ejecutar este código para examinar su resultado:

Python

```
username_list = ["elarson", "fgarcia", "tshah", "sgilmore"]
print(username_list[2])
```

📤 **Salida:**

```
tshah
```

Este ejemplo extrae el elemento con índice 2 directamente de la lista:

Python

```
print(["elarson", "fgarcia", "tshah", "sgilmore"][2])
```

📤 **Salida:**

```
tshah
```

#### Extracción de un trozo de una lista

Al igual que con las cadenas, también es posible utilizar la notación entre corchetes para extraer un **trozo (slice)** de una lista. Con las listas, esto significa extraer más de un elemento de la lista.

Cuando se extrae un trozo de una lista, el resultado es otra lista. Esta lista extraída se denomina **sublista** porque forma parte de la lista original, más grande.

Para extraer una sublista utilizando la notación entre corchetes, debe incluir dos índices. Puede ejecutar el siguiente código que toma un trozo de una lista y explorar la sublista que devuelve:

Python

```
username_list = ["elarson", "fgarcia", "tshah", "sgilmore"]
print(username_list[0:2])
```

📤 **Salida:**

```
['elarson', 'fgarcia']
```

El código devuelve una sublista de `["elarson", "fgarcia"]`. Esto se debe a que el elemento en el índice 0, `"elarson"`, está incluido en la rebanada, pero el elemento en el índice 2, `"tshah"`, está excluido. La rebanada termina un elemento antes de este índice.

#### Cambio de los elementos de una lista

A diferencia de las cadenas, también puede utilizar la notación entre corchetes para cambiar los elementos de una lista. Esto se debe a que una cadena es inmutable y no puede cambiarse después de crearla y asignarle un valor, pero las listas no son inmutables (son **mutables**).

Para cambiar un elemento de la lista, utilice una sintaxis similar a la que utilizaría al reasignar una variable, pero coloque el elemento específico que desea cambiar entre corchetes después del nombre de la variable. Por ejemplo, el siguiente Código cambia el elemento en el índice 1 de la variable `username_list` a `"bmoreno"`.

Python

```
username_list = ["elarson", "fgarcia", "tshah", "sgilmore"]
print("Original:", username_list)
username_list[1] = "bmoreno"
print("Modificada:", username_list)
```

📤 **Salida:**

```
Original: ['elarson', 'fgarcia', 'tshah', 'sgilmore']
Modificada: ['elarson', 'bmoreno', 'tshah', 'sgilmore']
```

Este código ha actualizado el elemento en el índice 1 de `"fgarcia"` a `"bmoreno"`.

---

### 📘 Métodos de Lista

Los **métodos de lista** son funciones específicas del tipo de datos de lista. Entre ellos se incluyen `.insert()`, `.remove()`, `.append()` y `.index()`.

#### `.insert()`

El método `.insert()` añade un elemento en una posición específica dentro de una lista. Tiene dos parámetros. El primero es el índice donde insertará el nuevo elemento, y el segundo es el elemento que desea insertar.

Puede ejecutar el siguiente código para explorar cómo se puede utilizar este método para insertar un nuevo nombre de usuario en una lista de nombres de usuario:

Python

```
username_list = ["elarson", "fgarcia", "tshah", "sgilmore"]
print("Original:", username_list)
username_list.insert(2, "wjaffrey")
print("Modificada:", username_list)
```

📤 **Salida:**

```
Original: ['elarson', 'fgarcia', 'tshah', 'sgilmore']
Modificada: ['elarson', 'fgarcia', 'wjaffrey', 'tshah', 'sgilmore']
```

Como el primer parámetro es 2 y el segundo es `"wjaffrey"`, `"wjaffrey"` se inserta en el índice 2, que es la tercera posición. Los demás elementos de la lista se desplazan una posición en la lista. Por ejemplo, `"tshah"` se encontraba originalmente en el índice 2 y ahora se encuentra en el índice 3.

#### `.remove()`

El método `.remove()` elimina la **primera aparición** de un elemento específico en una lista. Sólo tiene un parámetro, el elemento que desea eliminar.

El siguiente código elimina `"elarson"` de la lista `username_list`:

Python

```
username_list = ["elarson", "fgarcia", "tshah", "sgilmore"]
print("Original:", username_list)
username_list.remove("elarson")
print("Modificada:", username_list)
```

📤 **Salida:**

```
Original: ['elarson', 'fgarcia', 'tshah', 'sgilmore']
Modificada: ['fgarcia', 'tshah', 'sgilmore']
```

Este código elimina `"elarson"` de la lista. Los elementos que siguen a `"elarson"` se desplazan todos una posición más cerca del principio de la lista.

**Nota:** Si hay dos del mismo elemento en una lista, el método `.remove()` sólo elimina la primera instancia de ese elemento y no todas las apariciones.

#### `.append()`

El método `.append()` añade un elemento **al final** de una lista. Su único parámetro es el elemento que desea añadir al final de la lista.

Por ejemplo, podría utilizar `.append()` para añadir `"btang"` al final de `username_list`:

Python

```
username_list = ["elarson", "fgarcia", "tshah", "sgilmore"]
print("Original:", username_list)
username_list.append("btang")
print("Modificada:", username_list)
```

📤 **Salida:**

```
Original: ['elarson', 'fgarcia', 'tshah', 'sgilmore']
Modificada: ['elarson', 'fgarcia', 'tshah', 'sgilmore', 'btang']
```

Este código coloca `"btang"` al final de `username_list`, y todos los demás elementos permanecen en sus posiciones originales.

El Método `.append()` se utiliza a menudo con los bucles `for` para rellenar una lista vacía con elementos. Puede explorar cómo funciona esto con el siguiente código:

Python

```
numbers_list = []
print("Antes del bucle:", numbers_list)
for i in range(5):
    numbers_list.append(i)
print("Después del bucle:", numbers_list)
```

📤 **Salida:**

```
Antes del bucle: []
Después del bucle: [0, 1, 2, 3, 4]
```

Antes del bucle `for`, la variable `numbers_list` no contiene ningún elemento. Cuando se imprime, aparece la lista vacía. A continuación, el bucle `for` itera a través de una secuencia de números y utiliza el método `.append()` para añadir cada uno de estos números a `numbers_list`. Después del bucle, cuando se imprime la variable `numbers_list`, muestra estos números.

#### `.index()`

Similar al método `.index()` utilizado para cadenas, el método `.index()` utilizado para listas encuentra la **primera aparición** de un elemento en una lista y devuelve su índice. Toma como entrada el elemento buscado.

**Nota:** Aunque tiene el mismo nombre y uso que el método `.index()` utilizado para cadenas, el método `.index()` utilizado para listas no es el mismo método. Los métodos se definen al definir un tipo de datos, y como las cadenas y las listas se definen de forma diferente, los métodos también son diferentes.

Utilizando la variable `username_list`, puede utilizar el método `.index()` para encontrar el índice del nombre de usuario `"tshah"`:

Python

```
username_list = ["elarson", "fgarcia", "tshah", "sgilmore"]
print(username_list.index("tshah"))
```

📤 **Salida:**

```
2
```

Como el índice de `"tshah"` es 2, se obtiene este número.

Al igual que el método `.index()` utilizado para las cadenas, sólo devuelve el índice de la primera aparición de un elemento de lista. Así, si el nombre de usuario `"tshah"` se repitiera dos veces, devolvería el índice de la primera instancia, y no el de la segunda.

---

### 💡 Puntos Clave

Python ofrece muchas formas de trabajar con listas. La **Notación entre corchetes** le permite extraer elementos y trozos de las listas y también alterarlos. Los **métodos de lista** le permiten alterar las listas de diversas maneras. Los métodos `.insert()` y `.append()` añaden elementos a las listas, mientras que el método `.remove()` le permite eliminarlos. El método `.index()` le permite encontrar el índice de un elemento en una lista.