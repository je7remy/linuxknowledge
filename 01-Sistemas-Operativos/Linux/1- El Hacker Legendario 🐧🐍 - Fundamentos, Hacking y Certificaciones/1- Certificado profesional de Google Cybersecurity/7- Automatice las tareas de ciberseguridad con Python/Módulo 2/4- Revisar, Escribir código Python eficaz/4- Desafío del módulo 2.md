---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Desafío del módulo 2


### 🧠 Pregunta 1

Rellene el espacio en blanco: Para definir una función, debe colocar la palabra clave _____ antes del nombre de la función.

✅ Respuesta Correcta:

def

📘 Justificación:

En Python, la palabra clave (keyword) def es la abreviatura de "define" (definir). Se usa siempre al inicio de la declaración de una función para indicarle al intérprete que estás a punto de crear una nueva función.

---

### 🧠 Pregunta 2

¿Cuál de las siguientes llamadas a la función `type()` utiliza la sintaxis correcta?

✅ Respuesta Correcta:

type([55, 81, 17])

📘 Justificación:

type() es una función integrada de Python. Como todas las funciones, para "llamarla" o "ejecutarla", debes pasarle los argumentos (en este caso, la lista [55, 81, 17]) entre paréntesis (). Las otras opciones usan corchetes [] o dos puntos :, que son sintácticamente incorrectos para llamar a una función.

---

### 🧠 Pregunta 3

¿Qué es un parámetro?

✅ Respuesta Correcta:

Objeto que se incluye en la definición de una función para su uso en dicha función.

📘 Justificación:

Un parámetro es la variable que se lista dentro de los paréntesis en la definición de la función (por ejemplo, num en def mi_funcion(num):). Actúa como un marcador de posición. No debe confundirse con un argumento, que es el valor real (como 10) que se pasa a la función cuando se la llama (mi_funcion(10)).

---

### 🧠 Pregunta 4

Rellene el espacio en blanco: Una colección de módulos a los que los usuarios pueden acceder en sus programaciones es un _____.

✅ Respuesta Correcta:

biblioteca

📘 Justificación:

Una biblioteca (library) es un término general para una colección de módulos y paquetes relacionados que proporcionan funcionalidades adicionales. Ejemplos famosos son pandas, numpy o requests.

---

### 🧠 Pregunta 5

¿Qué devuelve esta línea de código?

print(type("h32rb17"))

✅ Respuesta Correcta:

str

📘 Justificación:

La función type() no devuelve el valor que se le pasa, sino el tipo de dato de ese valor. El valor "h32rb17" está entre comillas, lo que lo convierte en una cadena de texto (string). El nombre del tipo "string" en Python es str.

---

### 🧠 Pregunta 6

¿Qué devuelve la siguiente Función definida por el usuario si se le pasa el argumento 9?

Python

```
def subtract(num):
    total = 100 - num
    return total
subtract(9)
```

✅ Respuesta Correcta:

91

📘 **Justificación:**

1. Se llama a la función `subtract` con el **argumento** `9`.
    
2. Dentro de la función, el **parámetro** `num` toma el valor `9`.
    
3. Se calcula `total = 100 - num`, es decir, `total = 100 - 9`, lo que da `91`.
    
4. La línea `return total` devuelve el valor de la variable `total`, que es `91`.
    

---

### 🧠 Pregunta 7

¿En qué puede ayudarle una Guía de estilo cuando trabaja con Python? (Seleccione dos)

✅ **Respuestas Correctas:**

- Facilitar a otros programadores la comprensión de su código.
    
- Cómo hacer que su código sea más coherente.
    

📘 Justificación:

Una guía de estilo (como PEP 8 en Python) establece convenciones sobre cómo formatear el código (nombres de variables, espacios, etc.). Su objetivo principal es la legibilidad y la coherencia. Cuando todos en un equipo siguen la misma guía, el código se ve uniforme y es mucho más fácil de leer y mantener para todos.

---

### 🧠 Pregunta 8

¿Por qué son útiles los Comentarios? (Seleccione tres)

✅ **Respuestas Correctas:**

- Facilitan la depuración posterior.
    
- Explican el código a otros programadores.
    
- Proporcionan estadísticas sobre lo que hace el Código. _(Nota: Como mencionaste, esto es probablemente una mala traducción de "proporcionar contexto" o "documentar el propósito del código".)_
    

📘 Justificación:

Los comentarios (líneas que empiezan con #) son ignorados por el intérprete de Python; son notas para humanos:

1. **Explican:** Aclaran la lógica compleja ("por qué" se hizo algo) a otros programadores o a tu "yo" del futuro.
    
2. **Depuración:** Puedes "comentar" líneas de código para desactivarlas temporalmente y encontrar errores.
    
3. **Contexto:** Los comentarios a menudo incluyen metadatos como el autor, la fecha o el propósito general del script.
    

---

### 🧠 Pregunta 9

¿Qué es una función?

✅ Respuesta Correcta:

Una sección de código reutilizable.

📘 Justificación:

Esta es la definición principal de una función. En lugar de escribir el mismo bloque de código varias veces, lo "empaquetas" en una función con un nombre. Luego, puedes "llamar" a esa función por su nombre cada vez que necesites ejecutar ese bloque de código.

---

### 🧠 Pregunta 10

Rellene el espacio en blanco: Un archivo Python que contiene funciones adicionales, variables, clases y cualquier tipo de código ejecutable se denomina _____.

✅ Respuesta Correcta:

módulo

📘 Justificación:

En Python, un módulo es simplemente un archivo con la extensión .py que contiene código (funciones, variables, clases, etc.). Puedes importar ese módulo en otro script para usar el código que contiene. Una biblioteca (pregunta 4) es una colección de estos módulos.

---

# Segundo Intento:


### 🧠 Pregunta 1

¿Cuál de las siguientes opciones es un Encabezado válido en la definición de una Función?

- `def (remove_user(username))`
    
- `def remove_user(username):`
    
- `remove_user(username):`
    
- `def remove_user(username)`
    

✅ Respuesta correcta:

def remove_user(username):

📘 Justificación:

La sintaxis para un encabezado de función en Python requiere tres elementos clave:

1. La palabra clave `def` al inicio.
    
2. El nombre de la función seguido de paréntesis `()` (que contienen los parámetros, si los hay).
    
3. Dos puntos (`:`) al final de la línea.
    

---

### 🧠 Pregunta 2

¿Cuál de las siguientes llamadas a la función `type()` utiliza la sintaxis correcta?

- `type[(81, 17)]`
    
- `type([17, 81]):`
    
- `type[81, 55, 17]`
    
- `type([55, 81, 17])`
    

✅ Respuesta correcta:

type([55, 81, 17])

📘 Justificación:

type() es una función. Para "llamar" o ejecutar una función en Python, los argumentos (en este caso, la lista [55, 81, 17]) deben pasarse entre paréntesis (). El uso de corchetes [] o dos puntos : es sintácticamente incorrecto para una llamada de función.

---

### 🧠 Pregunta 3

¿Qué es un parámetro?

- El nombre de una función que se está definiendo
    
- Una variable devuelta por una función
    
- Los datos que se introducen en una función cuando se la llama
    
- Objeto que se incluye en la definición de una función para su uso en dicha función
    

✅ Respuesta correcta:

Objeto que se incluye en la definición de una función para su uso en dicha función.

📘 Justificación:

Un parámetro es la variable "marcador de posición" que se usa en la definición de la función (ej. def mi_funcion(parametro):). No debe confundirse con un argumento, que son los datos reales que se introducen cuando la función es llamada (ej. mi_funcion(argumento)).

---

### 🧠 Pregunta 4

Cuando se trabaja en Python, ¿qué es una biblioteca?

- Una colección de pautas de estilo para trabajar con Python
    
- Módulo que le permite trabajar con un tipo concreto de archivo
    
- Una colección de módulos que proporcionan código al que los usuarios pueden acceder en sus programas
    
- Un archivo Python que contiene funciones adicionales, variables, clases y cualquier tipo de código ejecutable
    

✅ Respuesta correcta:

Una colección de módulos que proporcionan código al que los usuarios pueden acceder en sus programas.

📘 Justificación:

La jerarquía es:

- **Módulo:** Un solo archivo Python (`.py`).
    
- **Biblioteca (o Paquete):** Una colección de módulos relacionados.
    

---

### 🧠 Pregunta 5

¿Qué devuelve esta línea de código?

print(sorted(["h32rb17", "p52jb81", "k11ry83"]))

- `["h32rb17"]`
    
- `["p52jb81"]`
    
- `["h32rb17", "k11ry83", "p52jb81"]`
    
- `["p52jb81", "k11ry83", "h32rb17"]`
    

✅ Respuesta correcta:

["h32rb17", "k11ry83", "p52jb81"]

📘 Justificación:

La función sorted() ordena los elementos de una lista en orden ascendente. Para las cadenas de texto (strings), esto significa orden alfabético. En orden alfabético: "h" viene antes de "k", y "k" viene antes de "p".

---

### 🧠 Pregunta 6

¿Qué devuelve la siguiente Función definida por el usuario si se le pasa el argumento de 2?

Python

```
def multiples(num):
    multiple = num * 3
    return multiple
multiples(2)
```

- `2`
    
- `num`
    
- `6`
    
- `multiples`
    

✅ Respuesta correcta:

6

📘 **Justificación:**

1. Se llama a la función `multiples` con el argumento `2`.
    
2. El parámetro `num` dentro de la función toma el valor `2`.
    
3. Se calcula `multiple = num * 3` (es decir, `multiple = 2 * 3`), lo que da `6`.
    
4. La sentencia `return multiple` devuelve el valor `6`.
    

---

### 🧠 Pregunta 7

¿Cuál de las siguientes opciones es un recurso que proporciona directrices estilísticas para los programadores que trabajan en Python?

- `re`
    
- `glob`
    
- `Biblioteca estándar de Python`
    
- `PEP 8`
    

✅ Respuesta correcta:

PEP 8

📘 Justificación:

PEP 8 (Python Enhancement Proposal 8) es la guía de estilo oficial para el código Python. Proporciona convenciones sobre cómo formatear el código, usar comentarios y nombrar variables para garantizar la legibilidad y coherencia.

---

### 🧠 Pregunta 8

¿Cuál es la ventaja de incluir este Comentario en el siguiente Código? (Seleccione todo lo que corresponda).

Python

```
# For loop iterates to print an alert message 5 times
for i in range(5):
    print("alert")
```

- Puede ayudar a otros programadores a entender el propósito de este Bucle.
    
- Puede ayudarle a entender el código si vuelve a consultarlo en el futuro.
    
- Aparece en la salida cuando se ejecuta el código en Python.
    
- Garantiza que el Bucle funcionará cuando se ejecute el código en Python.
    

✅ **Respuestas correctas:**

- Puede ayudar a otros programadores a entender el propósito de este Bucle.
    
- Puede ayudarle a entender el código si vuelve a consultarlo en el futuro.
    

📘 Justificación:

Los comentarios (líneas que comienzan con #) son ignorados por el intérprete de Python. Su único propósito es explicar el código a lectores humanos (ya sean otros programadores o usted mismo en el futuro). No afectan la ejecución ni la salida del código.

---

### 🧠 Pregunta 9

¿Cuál de las siguientes afirmaciones describe con precisión las funciones? (Seleccione todas las que correspondan).

- Las funciones son útiles para la Automatización.
    
- Cuando se actualizan las funciones, los cambios se aplican en todos los lugares en los que se utilizan.
    
- Las funciones pueden reutilizarse a lo largo de un programa.
    
- Las funciones no pueden utilizarse más de 10 veces desde un mismo programa.
    

✅ **Respuestas correctas:**

- Las funciones son útiles para la Automatización.
    
- Cuando se actualizan las funciones, los cambios se aplican en todos los lugares en los que se utilizan.
    
- Las funciones pueden reutilizarse a lo largo de un programa.
    

📘 Justificación:

Las funciones son la base de la reutilización de código (principio DRY: "Don't Repeat Yourself") y la automatización. Si actualizas la lógica dentro de la definición (def), todas las llamadas a esa función usarán la nueva lógica. No existe un límite de 10 usos; pueden ser llamadas tantas veces como sea necesario.

---

### 🧠 Pregunta 10

Ha importado un Módulo de Python, ¿a qué tiene ahora accesibilidad en Python?

- Una Función que existe dentro de Python y puede ser llamada directamente
    
- Funciones adicionales, variables, clases y otros tipos de código ejecutable
    
- Lista de comentarios que ha incluido en la programación anterior
    
- Un manual que informa sobre la redacción, el formato y el diseño de los documentos
    

✅ Respuesta correcta:

Funciones adicionales, variables, clases y otros tipos de código ejecutable.

📘 Justificación:

Un módulo es un archivo .py que contiene código. Al importar un módulo, obtienes acceso a todo ese código (funciones, variables, etc.) para usarlo en tu programa actual.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[3- Términos del glosario del Módulo 2]]
