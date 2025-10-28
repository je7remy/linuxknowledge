
## 🧠 Guía de Referencia: Conceptos de Python (Módulo 4)

Certificado de Ciberseguridad de Google

### Secciones

- Operaciones con Archivos
    
- Análisis Sintáctico (Parsing)
    

---

### 📂 Operaciones con Archivos

Las siguientes funciones, métodos y palabras clave se utilizan con operaciones que involucran archivos.

|**Palabra Clave / Función / Método**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`with`**|Maneja errores y gestiona recursos externos.|`with open("logs.txt", "r") as file:` _(Se usa para manejar errores y gestionar recursos al abrir un archivo; la variable `file` almacena la información del archivo mientras se está dentro de la sentencia `with`; gestiona recursos cerrando el archivo después de salir de la sentencia `with`)_|
|**`open()`**|Abre un archivo en Python.|`with open("login_attempts.txt", "r") as file:` _(Abre el archivo "login_attempts.txt" para leerlo (`"r"`))_ `with open("update_log.txt", "w") as file:` _(Abre el archivo "update_log.txt" en la variable `file` para escribir sobre su contenido (`"w"`))_ `with open(import_file, "a") as file:` _(Abre el archivo asignado a la variable `import_file` en la variable `file` para añadir (`"a"`) información al final)_|
|**`as`**|Asigna una variable que hace referencia a otro objeto.|`with open("logs.txt", "r") as file:` _(Asigna la variable `file` para referenciar la salida de la función `open()`)_|
|**`.read()`**|Convierte archivos en cadenas; devuelve el contenido de un archivo abierto como una cadena por defecto.|`with open("login_attempts.txt", "r") as file:` `file_text = file.read()` _(Convierte el objeto archivo referenciado en la variable `file` en una cadena y luego almacena esta cadena en la variable `file_text`)_|
|**`.write()`**|Escribe datos de cadena en un archivo especificado.|`with open("access_log.txt", "a") as file:` `file.write("jrafael")` _(Escribe la cadena `"jrafael"` en el archivo `"access_log.txt"`; como el segundo argumento en la llamada a `open()` es `"a"`, esta cadena se añade al final del archivo)_|

---

### 📄 Análisis Sintáctico (Parsing)

Los siguientes métodos son útiles al analizar datos.

|**Método**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`.split()`**|Convierte una cadena en una lista; separa la cadena basándose en el carácter que se pasa como argumento; si no se pasa un argumento, separará la cadena cada vez que encuentre caracteres de espacio en blanco (como espacio o retorno de línea).|`approved_users = "elarson,bmoreno,tshah".split(",")` _(Convierte la cadena `"elarson,bmoreno,tshah"` en la lista `["elarson", "bmoreno", "tshah"]` dividiendo en cada coma)_ `removed_users = "wjaffrey jsoto abernard".split()` _(Convierte la cadena `"wjaffrey jsoto abernard"` en la lista `["wjaffrey", "jsoto", "abernard"]` dividiendo en cada espacio)_|
|**`.join()`**|Concatena los elementos de un iterable (como una lista) en una cadena; toma el iterable a concatenar como argumento; se añade a un carácter (o cadena) que separará cada elemento una vez unidos en una cadena. **Sintaxis:** `"separador".join(iterable)`|`approved_users = ",".join(["elarson", "bmoreno", "tshah"])` _(Concatena los elementos de la lista en la cadena `"elarson,bmoreno,tshah"`, separando cada elemento con una coma)_|