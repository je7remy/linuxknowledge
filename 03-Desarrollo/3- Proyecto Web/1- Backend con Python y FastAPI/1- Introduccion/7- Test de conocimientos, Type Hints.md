
### 1- ¿Qué permite hacer la función type() en Python?

_Seleccione solamente LA MEJOR respuesta_

- A. Verifica si una variable está vacía
    
- B. Convierte una variable a tipo string
    
- **C. Devuelve el tipo actual de una variable** (Seleccionada)
    

---

> Esta respuesta es correcta.
> 
> La función type() devuelve el tipo actual de una variable en tiempo de ejecución.

### 2- ¿Para qué sirven los type hints en Python?

_Seleccione solamente LA MEJOR respuesta_

- A. Obligan al intérprete a usar tipos estrictos
    
- B. Permiten declarar el tipo de una variable para mejorar soporte y validación
    
- C. Evitan errores de sintaxis en tiempo de ejecución
    

---

Nota del tutor:

Recuerda que Python ignora los tipos al ejecutarse (por lo que la A es falsa), pero los Type Hints son vitales para que los editores nos ayuden (autocompletado) y para que librerías como FastAPI/Pydantic puedan validar los datos.


### 3- ¿Qué tipo de tipado tiene Python?

_Seleccione solamente LA MEJOR respuesta_

- A. Estático y seguro
    
- B. Fuerte y estático
    
- **C. Débil y dinámico** (Seleccionada)
    

---

> Esta respuesta es correcta.
> 
> Python tiene tipado débil y dinámico.

---

Nota del Tutor (Importante):

Hay una imprecisión técnica en esta pregunta del examen.

En la industria y la teoría de lenguajes, Python se considera de tipado FUERTE y DINÁMICO.

- **Dinámico:** Porque no necesitas declarar tipos y pueden cambiar (correcto).
    
- **Fuerte:** Porque el lenguaje **no** convierte tipos automáticamente sin tu permiso (por ejemplo, `1 + "1"` da error en Python, mientras que en lenguajes "débiles" como JavaScript daría `"11"`).
    

### 4- ¿Cuál es el comportamiento de Python si se cambia el valor de una variable string a un número?

_Seleccione solamente LA MEJOR respuesta_

- A. El editor bloquea el cambio
    
- B. Python lanza una excepción
    
- **C. Python acepta el cambio sin errores** (Respuesta Correcta)
    

---

> Explicación:
> 
> Como vimos en el ejemplo de código anterior (my_string_variable = 5), debido al tipado dinámico, Python permite cambiar el tipo de dato que contiene una variable en cualquier momento sin generar errores de ejecución.


### 5- ¿Qué ocurre si se especifica que un parámetro debe ser int y se envía un string en FastAPI?

_Seleccione solamente LA MEJOR respuesta_

- A. El parámetro se convierte automáticamente
    
- **B. FastAPI rechazará la petición por no cumplir el tipo esperado** (Respuesta Correcta)
    
- C. El servidor ignora el tipo y acepta el dato
    

---

> **Explicación del Experto:**
> 
> Esta es una de las características más potentes de FastAPI (gracias a Pydantic): la **Validación de Datos**.
> 
> 1. **Intento de Conversión:** Si envías el string `"5"` (un número entre comillas), FastAPI es lo suficientemente inteligente para **convertirlo** a un entero `5` y procesarlo (aquí la opción A sería parcialmente cierta).
>     
> 2. **Validación Estricta:** Sin embargo, la pregunta implica el envío de un string que **no** es un número (por ejemplo, `"hola"`). En este caso, FastAPI detecta que el dato no coincide con el tipo `int` y **rechaza la petición** automáticamente, devolviendo un error HTTP 422 (Unprocessable Entity) con un mensaje detallando exactamente qué campo falló.


### 6- ¿Qué ventaja tiene usar type hints en variables complejas?

_Seleccione solamente LA MEJOR respuesta_

- **A. El editor puede sugerir operaciones específicas y detectar errores** (Respuesta Correcta)
    
- B. Evita que se usen listas
    
- C. Convierte automáticamente los tipos
    

---

> Explicación:
> 
> Cuando trabajas con estructuras complejas (como diccionarios dentro de listas), el editor normalmente "se pierde" y no sabe qué sugerirte.
> 
> Al usar _Type Hints_ (por ejemplo: `users: List[Dict[str, int]]`), le das un mapa al editor. Así, cuando escribas código, el editor sabrá autocompletar los métodos de la lista y detectar si intentas meter un dato incorrecto dentro del diccionario, ahorrándote horas de depuración.


### 7- ¿Qué significa que Python sea de tipado dinámico?

_Seleccione solamente LA MEJOR respuesta_

- **A. El tipo de una variable puede cambiar en tiempo de ejecución** (Seleccionada)
    
- B. Las variables deben tener un tipo fijo
    
- C. El tipo de variable se define al compilar
    

---

> Esta respuesta es correcta.
> 
> Que un lenguaje de programación sea de tipado dinámico, significa que el tipo de una variable puede cambiar en tiempo de ejecución.


### 8- ¿Qué ventaja ofrece usar type hints en FastAPI?

_Seleccione solamente LA MEJOR respuesta_

- A. Permite ejecutar código más rápido
    
- B. Evita que se usen funciones en el backend
    
- **C. FastAPI puede validar automáticamente los datos según el tipo especificado** (Seleccionada)
    

---

> Esta respuesta es correcta.
> 
> Al usar type hints, FastAPI puede validar automáticamente los datos que llegan a la API.

---

Aclaración importante:

Es común confundirse con la opción A. Recuerda que en Python, los Type Hints no hacen que el programa se ejecute más rápido (la máquina los ignora). La magia está en que FastAPI los usa para validar los datos antes de que entren a tu función, ahorrándote escribir cientos de líneas de código de validación manual (if type(x) == int...).

### 9- ¿Por qué es útil especificar el tipo de datos en una API?

_Seleccione solamente LA MEJOR respuesta_

- **A. Ayuda a validar los datos y mejora la comunicación entre cliente y servidor** (Seleccionada)
    
- B. Evita que se usen strings en el backend
    
- C. Permite usar cualquier tipo sin restricciones
    

---

> Esta respuesta es correcta.
> 
> Facilita la validación y comprensión de los datos que se reciben.


### 10- ¿Qué significa que FastAPI aproveche los type hints?

_Seleccione solamente LA MEJOR respuesta_

- **A. Valida datos entrantes y genera documentación automáticamente** (Seleccionada)
    
- B. Evita el uso de variables globales
    
- C. Permite usar funciones sin definir tipos
    

---

> Esta respuesta es correcta.
> 
> Utiliza los tipos para validar datos y generar documentación.

