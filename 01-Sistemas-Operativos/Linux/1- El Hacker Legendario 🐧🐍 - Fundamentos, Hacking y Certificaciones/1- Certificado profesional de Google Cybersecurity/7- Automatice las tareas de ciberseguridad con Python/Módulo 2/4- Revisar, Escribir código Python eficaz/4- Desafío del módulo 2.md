

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