
### 🧠 Pregunta 1

¿Cuáles son los tres tipos de errores que encontrará durante la depuración?

- Excepciones, errores lógicos, errores iterativos
    
- **Errores de sintaxis, errores lógicos y excepciones**
    
- Errores de sintaxis, excepciones y errores de comentario
    
- Errores lógicos, errores de comentario y errores iterativos
    

✅ Respuesta correcta:

Errores de sintaxis, errores lógicos y excepciones.

📘 Justificación:

Los principales tipos de errores en programación son: errores de sintaxis (incumplimiento de las reglas del lenguaje), errores lógicos (el código se ejecuta pero da resultados incorrectos) y excepciones (errores que ocurren durante la ejecución).

---

### 🧠 Pregunta 2

El propósito del siguiente código es imprimir los caracteres de un identificador de dispositivo. [...] ¿A qué se debe el error `SyntaxError: EOL while scanning string literal`?

Python

```
device_id = "p35rv47 # Falta comilla al final
print(device_id)
```

- Faltan dos puntos (`:`)
    
- Una variable mal escrita
    
- **Falta una comilla (`"`)**
    
- Falta un doble signo igual (`==`)
    

✅ Respuesta correcta:

Falta una comilla (").

📘 Justificación:

El error "EOL while scanning string literal" (Fin de Línea mientras se escaneaba literal de cadena) indica que Python llegó al final de la línea mientras esperaba que terminara una cadena de texto. Esto ocurre porque falta la comilla de cierre (") al final de "p35rv47.

---

### 🧠 Pregunta 3

El propósito de este código es imprimir `"user flagged"` si el nombre de usuario es `"jhill"`, y en caso contrario imprimir `"user okay"`. [...] ¿Cómo puede solucionar este error? _(Se asume que el código original tenía solo un `if` y luego el `print("user okay")` sin `else`)_

Python

```
# Código Asumido con Error Lógico:
# username = "other_user"
# if username == "jhill":
#     print("user flagged")
# print("user okay") # Siempre se imprime
```

- Elimine la indentación de la línea que imprime `"user okay"` para que no forme parte del condicional.
    
- Utilice el operador `!=` en lugar del operador `==` en la cabecera condicional.
    
- Llame a `check_user()` antes de la definición de la función.
    
- **Añada una sentencia `else` antes de la línea que imprime `"user okay"`.**
    

✅ Respuesta correcta:

Añada una sentencia else antes de la línea que imprime "user okay".

📘 Justificación:

El problema es un error lógico: el mensaje "user okay" se imprime siempre, independientemente del resultado del if. Para que solo se imprima cuando la condición del if es falsa, debe colocarse dentro de un bloque else asociado a ese if.

---

### 🧠 Pregunta 4

Le pide a su código que divida algo por 0, pero se produce un error. ¿De qué tipo de error se trata?

- Índice fuera de los límites
    
- **Excepción**
    
- Error de sintaxis
    
- Error lógico
    

✅ Respuesta correcta:

Excepción.

📘 Justificación:

Intentar dividir por cero es una operación matemáticamente indefinida que Python detecta durante la ejecución. Este tipo de error en tiempo de ejecución se llama excepción, específicamente ZeroDivisionError.

---

### 🧠 Pregunta 5

Al depurar código, ¿cuáles son las formas eficaces de determinar qué secciones del código funcionan correctamente? (Seleccione todas las que correspondan).

- Añadir Comentarios en el Código
    
- **Añadir sentencias `print`**
    
- **Utilizar un Depurador**
    
- Borrar líneas en blanco del código
    

✅ **Respuestas correctas:**

- Añadir sentencias `print`.
    
- Utilizar un Depurador.
    

📘 Justificación:

Tanto añadir sentencias print temporales para rastrear el flujo y los valores, como usar un depurador para ejecutar el código paso a paso y establecer puntos de interrupción, son estrategias efectivas para aislar dónde ocurren los errores lógicos o las excepciones. Los comentarios explican el código pero no ayudan a rastrear la ejecución, y borrar líneas en blanco no afecta la lógica.

---

### 🧠 Pregunta 6

¿Cuál de estas funciones o argumentos debe incluir en una sentencia `with` si desea que Python abra un archivo llamado `access.txt` para poder leerlo? (Seleccione tres).

- **`"access.txt"`**
    
- `read()`
    
- **`"r"`**
    
- **`open()`**
    

✅ **Respuestas correctas:**

- `"access.txt"`
    
- `"r"`
    
- `open()`
    

📘 Justificación:

La estructura básica es with open(nombre_archivo, modo) as ...:. Por lo tanto, necesitas la función open(), el nombre del archivo ("access.txt"), y el modo de lectura ("r"). El método .read() se usa dentro del bloque with, no en la línea with misma.

---

### 🧠 Pregunta 7

Ha leído un archivo de registro en `file_text` (una cadena). [...] ¿Cómo convertir esta cadena en una lista `usernames`?

- **`usernames = file_text.split()`**
    
- `usernames = split(usernames, file_text)`
    
- `file_text.split() as usernames`
    
- `usernames = usernames.split(file_text)`
    

✅ Respuesta correcta:

usernames = file_text.split()

📘 Justificación:

El método de cadena .split() se llama sobre la cadena que quieres dividir (file_text). Sin argumentos, divide por espacios en blanco y devuelve una lista. Esta lista se asigna a la variable usernames usando =.

---

### 🧠 Pregunta 8

¿Cuál es el proceso de conversión de Datos a un formato más legible?

- **Análisis sintáctico (Parsing)**
    
- Dividir (Split)
    
- Depuración (Debugging)
    
- Rebanar (Slicing)
    

✅ Respuesta correcta:

Análisis sintáctico (Parsing).

📘 Justificación:

Parsing es el término general para analizar una cadena de texto o datos y transformarlos en una estructura más organizada y utilizable (como convertir una cadena JSON en un diccionario Python, o una cadena de log en una lista de campos). Split y Slicing son técnicas que se pueden usar durante el parsing. Debugging es corregir errores.

---

### 🧠 Pregunta 9

¿Qué hace el siguiente Código? `read_text = text.read()` _(Asumiendo que `text` es un objeto archivo abierto)_

- **Lee la variable `text`, que contiene un archivo, y la almacena como una cadena en `read_text`**
    
- Divide la variable `text`, que contiene una cadena, y la almacena como una lista en `read_text`
    
- Lee la cadena `text` y la almacena el archivo `read_text`
    
- Sustituye el contenido del archivo `read_text` por el contenido del archivo `text`
    

✅ Respuesta correcta:

Lee la variable text, que contiene un archivo, y la almacena como una cadena en read_text.

📘 Justificación:

El método .read() se aplica a un objeto archivo (text) y devuelve su contenido completo como una cadena. Esta cadena se asigna luego a la variable read_text.

---

### 🧠 Pregunta 10

Quiere comprobar si hubo más de tres intentos fallidos de inicio de sesión en los últimos 10 minutos por parte del último usuario [...]. Si desea automatizar esto [...], ¿qué formaría parte de su código? (Seleccione tres).

- **Un bucle `for` que itera a través de la lista de conexiones**
    
- Una línea de programación que reasigna una variable de contador a 0 si hay un intento fallido de inicio de sesión
    
- **Una variable contador que se incrementa cuando se detecta un inicio de sesión fallido**
    
- **Una sentencia `if` que comprueba si hubo más de tres intentos fallidos de inicio de sesión**
    

✅ **Respuestas correctas:**

- Un bucle `for` que itera a través de la lista de conexiones (o intentos de inicio de sesión).
    
- Una variable contador que se incrementa cuando se detecta un inicio de sesión fallido (para el usuario relevante y dentro del intervalo de tiempo).
    
- Una sentencia `if` que comprueba si hubo más de tres intentos fallidos de inicio de sesión (al final, para decidir si se alerta).
    

📘 Justificación:

Para implementar esta lógica, necesitas:

1. Iterar sobre los registros de inicio de sesión relevantes (usando un **bucle `for`**).
    
2. Dentro del bucle, identificar los intentos fallidos del usuario específico dentro de los últimos 10 minutos.
    
3. Usar una **variable contador** para llevar la cuenta de esos intentos fallidos.
    
4. Después del bucle (o en cada iteración si se quiere alertar inmediatamente), usar una sentencia if para verificar si el contador ha superado el umbral (3).
    
    La opción de reasignar el contador a 0 si hay un intento fallido es incorrecta; el contador debe incrementarse.