---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Cadenas y el analista de Seguridad

### 🧠 Cadenas y el Analista de Seguridad

La capacidad de trabajar con cadenas es importante en la profesión de la ciberseguridad. Anteriormente, se le presentaron varias formas de trabajar con cadenas, incluyendo funciones y métodos. También aprendió a extraer elementos en cadenas utilizando la notación entre corchetes y los índices. Esta lectura repasa estos conceptos y le explica más sobre el uso del método `.index()`. También destaca ejemplos de datos de cadenas que podría encontrar en un entorno de seguridad.

#### Datos de cadena en un entorno de seguridad

Como analista, los datos de cadena son uno de los tipos de datos más comunes que encontrará en Python. **Datos de cadena** son datos que consisten en una secuencia ordenada de caracteres. Se utiliza para almacenar cualquier tipo de información que no necesite manipular matemáticamente (como mediante una división o una resta). En un contexto de ciberseguridad, esto incluye direcciones IP, nombres de usuario, URL e identificaciones de empleados.

Tendrá que trabajar con estas cadenas de varias maneras. Por ejemplo, podría extraer ciertas partes de una dirección IP, o podría verificar si los nombres de usuario cumplen los criterios requeridos.

---

### 📘 Trabajar con índices en cadenas

#### Índices

Un **índice** es un número asignado a cada elemento de una secuencia que indica su posición. En el caso de las cadenas, esto significa que cada carácter de la cadena tiene su propio índice.

Los índices comienzan en 0. Por ejemplo, podría estar trabajando con esta cadena que contiene un identificador de dispositivo: `"h32rb17"`. La siguiente tabla indica el índice de cada carácter de esta cadena:

|**carácter**|**índice**|
|---|---|
|h|0|
|3|1|
|2|2|
|r|3|
|b|4|
|1|5|
|7|6|

También puede utilizar números negativos como índices. Esto se basa en su posición relativa al último carácter de la cadena:

|**carácter**|**índice**|
|---|---|
|h|-7|
|3|-6|
|2|-5|
|r|-4|
|b|-3|
|1|-2|
|7|-1|

#### Notación entre corchetes

La **notación entre corchetes** se refiere a los índices colocados entre corchetes. Puede utilizar la notación entre corchetes para extraer una parte de una cadena. Por ejemplo, el primer carácter del ID del dispositivo puede representar una determinada característica del mismo. Si desea extraerla, puede utilizar la notación entre corchetes para ello:

`"h32rb17"[0]`

Este ID de dispositivo también podría estar almacenado dentro de una variable llamada `device_id`. Puede aplicar la misma notación entre corchetes a la variable:

device_id = "h32rb17"

device_id[0]

En ambos casos, la notación entre corchetes da como resultado el carácter `h` cuando esta notación entre corchetes se coloca dentro de una función `print()`. Puede observar esto ejecutando el siguiente código:

Python

```
device_id = "h32rb17"
print(device_id[0])
```

📤 **Salida:**

```
h
```

También puede tomar una **rebanada (slice)** de una cadena. Cuando toma un slice de una cadena, extrae más de un carácter de ella. Suele hacerse en contextos de ciberseguridad cuando sólo le interesa una parte específica de una cadena. Por ejemplo, podrían ser ciertos números de una dirección IP o ciertas partes de una URL.

En el ejemplo de la identificación del dispositivo, podría necesitar los tres primeros caracteres para determinar una calidad concreta del dispositivo. Para ello, puede tomar un trozo de la cadena utilizando la notación entre corchetes. Puede ejecutar esta línea de código para observar que da salida a `"h32"`:

Python

```
print("h32rb17"[0:3])
```

📤 **Salida:**

```
h32
```

**Nota:** La rebanada comienza en el índice 0, pero se excluye el segundo índice especificado después de los dos puntos (3). Esto significa que la rebanada termina una posición antes del índice 3, que está en el índice 2.

---

### 📘 Funciones y Métodos de Cadena

Las funciones `str()` y `len()` son útiles para trabajar con cadenas. También puede aplicar métodos a las cadenas, como los métodos `.upper()`, `.lower()` y `.index()`. Un **método** es una función que pertenece a un tipo de datos específico.

#### `str()` y `len()`

La función `str()` convierte su objeto de entrada en una cadena. Como analista, podría utilizarla en los registros de Seguridad cuando trabaje con IDs numéricos que no vayan a ser utilizados con procesos matemáticos. Convertir un número entero en una cadena le da la posibilidad de buscar en ella y extraer trozos de la misma.

Considere el ejemplo de un ID de empleado `19329302` que necesita convertir en una cadena. Puede utilizar la siguiente línea de programación para convertirlo en una cadena y almacenarlo en una variable:

`string_id = str(19329302)`

La segunda función que aprendió para cadenas es la función `len()`, que devuelve el número de elementos de un objeto.

Por ejemplo, si desea verificar que el ID de un determinado dispositivo cumple la norma de contener siete caracteres, puede utilizar la función `len()` y un condicional. Cuando ejecute el código siguiente, imprimirá un mensaje si `"h32rb17"` tiene siete caracteres:

Python

```
device_id = "h32rb17"
if len(device_id) == 7:
    print("El ID del dispositivo tiene siete caracteres.")
```

📤 **Salida:**

```
El ID del dispositivo tiene siete caracteres.
```

#### `.upper()` y `.lower()`

El método `.upper()` devuelve una copia de la cadena con todos sus caracteres en mayúsculas. Por ejemplo, puede cambiar el nombre de este departamento a todo en mayúsculas ejecutando el código `"Information Technology".upper()`. Devolvería la cadena `"INFORMATION TECHNOLOGY"`.

Mientras tanto, el método `.lower()` devuelve una copia de la cadena con todos sus caracteres en minúsculas. `"Information Technology".lower()` devolvería la cadena `"information technology"`.

#### `.index()`

El método `.index()` encuentra la primera aparición de la entrada en una cadena y devuelve su ubicación. Por ejemplo, este Código utiliza el método `.index()` para encontrar la primera aparición del carácter `"r"` en el ID del dispositivo `"h32rb17"`:

Python

```
print("h32rb17".index("r"))
```

📤 **Salida:**

```
3
```

El método `.index()` devuelve `3` porque la primera aparición del carácter `"r"` se encuentra en el índice 3.

En otros casos, es posible que no se encuentre la entrada. Cuando esto ocurre, Python devuelve un error. Por ejemplo, el Código `print("h32rb17".index("a"))` devuelve un `ValueError` porque `"a"` no se encuentra en la cadena `"h32rb17"`.

Tenga en cuenta también que si una cadena contiene más de una instancia de un carácter, sólo se devolverá la primera. Por ejemplo, el identificador de dispositivo `"r45rt46"` contiene dos instancias de `"r"`. Puede ejecutar el siguiente código para explorar su resultado:

Python

```
print("r45rt46".index("r"))
```

📤 **Salida:**

```
0
```

La salida es `0` porque `.index()` devuelve sólo la primera instancia de `"r"`, que se encuentra en el índice 0. La instancia de `"r"` en el índice 3 no se devuelve.

#### Encontrar subcadenas con `.index()`

Una **Subcadena** es una secuencia continua de caracteres dentro de una Cadena. Por ejemplo, `"llo"` es una subcadena de `"hello"`.

El método `.index()` también puede utilizarse para encontrar el índice de la primera aparición de una subcadena. Devuelve el índice del primer carácter de esa subcadena. Considere este ejemplo que encuentra la primera instancia del usuario `"tshah"` en una cadena:

Python

```
log_in_string = "tsnow, tshah, bmoreno, elarson"
print(log_in_string.index("tshah"))
```

📤 **Salida:**

```
7
```

El método `.index()` devuelve el índice `7`, que es donde empieza la subcadena `"tshah"`.

**Nota:** Cuando utilice el método `.index()` para buscar subcadenas, debe tener cuidado. En el ejemplo anterior, quiere localizar la instancia de `"tshah"`. Si busca sólo `"ts"`, Python le devolverá `0` en lugar de `7` porque `"ts"` también es una subcadena de `"tsnow"`.

---

### 💡 Puntos Clave

Como analista de Seguridad, trabajará con cadenas de varias maneras. En primer lugar, es posible que necesite utilizar la notación entre corchetes para trabajar con índices de cadenas. Dos funciones que probablemente utilizará son `str()`, que convierte una entrada en una cadena, y `len()`, que halla la longitud de una cadena. También puede utilizar métodos de cadenas, funciones que sólo trabajan con cadenas. Entre ellas están `.upper()`, que convierte todas las letras de una cadena en mayúsculas, `.lower()`, que convierte todas las letras de una cadena en minúsculas, y `.index()`, que devuelve el índice de la primera aparición de su entrada dentro de una cadena.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[3- Índices y cortes de cadena]]
- ➡️ Siguiente: [[5- Actividad - Trabajar con cadenas en Python]]
