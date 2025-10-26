
### 🧠 Pregunta 1

Desea abrir el archivo `"logs.txt"` y almacenarlo en la variable `file` con el fin de leerlo. También quiere asegurarse de que se liberan todos los Recursos y se cierra el archivo después de leerlo. ¿Cuál es la línea de código correcta para hacer esto?

- `with open("logs.txt", "r") as file:`
    
- `file = open("logs.txt", "r"):`
    
- `with file.open("logs.txt", "r"):`
    
- `with open("r", "logs.txt") as file:`
    

✅ **Respuesta correcta:**`with open("logs.txt", "r") as file:`

📘 **Justificación:** La sintaxis `with open(...) as ...:` es la forma estándar en Python para abrir archivos. Garantiza que el archivo se cierre automáticamente. El primer argumento de `open()` es el nombre del archivo, el segundo es el modo (`"r"` para leer), y `as file` asigna el objeto archivo a la variable `file`.

---

### 🧠 Pregunta 2

Después de haber abierto un archivo de registro como `login_file`, ¿qué línea de código puede utilizar para leer el archivo y almacenarlo en una variable llamada `login_attempts`?

- `login_attempts = read(login_file)`
    
- `login_attempts = login_file.reader()`
    
- `login_attempts = login_file.read()`
    
- `login_file.read() as login_attempts`
    

✅ **Respuesta correcta:**`login_attempts = login_file.read()`

📘 **Justificación:** El método **`.read()`** se aplica al objeto archivo (`login_file` en este caso) y devuelve todo el contenido del archivo como una sola cadena. Luego, se asigna esta cadena a la variable `login_attempts` usando `=`.

---

### 🧠 Pregunta 3

Acaba de leer un archivo de registro en una variable llamada `file`. La variable `file` contiene una cadena de múltiples direcciones IP separadas cada una por un espacio en blanco. ¿Qué línea de código separa cada dirección IP individual y la almacena como una lista en una variable llamada `ip_addresses`?

- `ip_addresses.split(file)`
    
- `ip_addresses = file.split()`
    
- `ip_addresses = split(file)`
    
- `split(file, ip_addresses)`
    

✅ **Respuesta correcta:**`ip_addresses = file.split()`

📘 **Justificación:** El método **`.split()`** se aplica a una cadena (`file` en este caso). Sin argumentos, divide la cadena por espacios en blanco y devuelve una lista. Esta lista se asigna a la variable `ip_addresses` usando `=`.

---

### 🧠 Pregunta 4

Necesita comprobar si hay actividad inusual de inicio de sesión. En concreto, necesita comprobar una lista de marcas de tiempo de inicio de sesión para determinar si alguno de los inicios de sesión se produjo a horas inusuales. Si desea automatizar esto a través de Python, ¿qué formaría parte de su código? (Seleccione dos).

- Una sentencia `if` que comprueba si un usuario específico tiene varias marcas de tiempo de inicio de sesión durante horas inusuales
    
- Una sentencia `if` que comprueba si la marca de tiempo de inicio de sesión se produjo a horas inusuales
    
- Una variable contador que lleva la cuenta del número de intentos fallidos de inicio de sesión
    
- Un bucle `for` que itera a través de la lista de marcas de tiempo
    

✅ **Respuestas correctas:**

- Una sentencia `if` que comprueba si la marca de tiempo de inicio de sesión se produjo a horas inusuales.
    
- Un bucle `for` que itera a través de la lista de marcas de tiempo.
    

📘 **Justificación:** Para automatizar la verificación de cada marca de tiempo en una lista, necesitas:

1. Un **bucle `for`** para procesar cada `marca_de_tiempo` individualmente dentro de la lista.
    
2. Dentro del bucle, una **sentencia `if`** para evaluar si esa `marca_de_tiempo` específica cumple la condición de ser "inusual" (por ejemplo, si está fuera del horario laboral). Un contador de intentos fallidos o verificar múltiples marcas para un _usuario específico_ no son directamente relevantes para la tarea descrita.