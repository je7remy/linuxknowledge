
### 🧠 Tarea 1

...escriba la primera línea de la sentencia `with`... Use `open()`, estableciendo el segundo parámetro en `"r"`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the text file that contains the security log file
import_file = "login.txt"

# First line of the `with` statement
# Use `open()` to import security log file and store it as a string
with open(import_file, "r") as file:
    # El cuerpo de la sentencia 'with' irá aquí en la siguiente tarea
    pass # 'pass' es un marcador de posición para evitar un error de indentación
```

---

### 🧠 Tarea 2

...use el método `.read()` para leer el archivo importado y almacene el resultado en `text`. ...muestre `text`...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the text file that contains the security log file
import_file = "login.txt"

# The `with` statement
# Use `open()` to import security log file and store it as a string
with open(import_file, "r") as file:

  # Use `.read()` to read the imported file and store the result in a variable named `text`
  text = file.read()

# Display the contents of `text`
print(text)
```

---

### 🧠 Tarea 3

...explore cómo puede dividir la cadena... en una lista de cadenas, una por línea. Use el método `.split()`...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the text file that contains the security log file
import_file = "login.txt"

# The `with` statement
# Use `open()` to import security log file and store it as a string
with open(import_file, "r") as file:

  # Use `.read()` to read the imported file and store the result in a variable named `text`
  text = file.read()

# Display the contents of `text` split into separate lines
print(text.split())
```

_(Nota: `.split()` sin argumentos divide por cualquier espacio en blanco, incluidos los saltos de línea, lo que efectivamente separa las líneas si no hay espacios dentro de ellas, aunque técnicamente divide por palabra si hay espacios. Para dividir estrictamente por líneas, se usaría `text.splitlines()` o `text.split('\n')`)_.

---

### 🧠 Pregunta 1

¿Qué nota sobre la salida antes y después de usar el método `.split()`?

✅ **Respuesta correcta:**

- **Antes** de `.split()` (Tarea 2), la salida es una **única cadena de texto larga** que contiene todo el contenido del archivo, incluyendo los caracteres de nueva línea (`\n`) que separan visualmente las líneas.
    
- **Después** de `.split()` (Tarea 3), la salida es una **lista** de Python. Cada elemento de la lista es una cadena que representa una porción del texto original, separada por los espacios en blanco (en este caso, principalmente los saltos de línea).
    

---

### 🧠 Tarea 4

...Use el método `.write()` y el parámetro `"a"` en `open()`... para añadir `missing_entry`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the text file that contains the security log file
import_file = "login.txt"

# Assign `missing entry` to a log that was not recorded in the log file
missing_entry = "\njrafael,192.168.243.140,4:56:27,2022-05-09" # Añadido \n al inicio

# Use `open()` to import security log file and store it as a string
# Pass in "a" as the second parameter to indicate that the file is being opened for appending purposes
with open(import_file, "a") as file:

    # Use `.write()` to append `missing_entry` to the log file
    file.write(missing_entry)

# Use `open()` with the parameter "r" to open the security log file for reading purposes
with open(import_file, "r") as file:

    # Use `.read()` to read in the contents of the log file and store in a variable named `text`
    text = file.read()

# Display the contents of `text`
print(text)
```

_(Nota: Añadí `\n` al inicio de `missing_entry` para asegurar que se añada en una nueva línea)._

---

### 🧠 Pregunta 2

¿Qué nota sobre la posición de la entrada que se añadió al archivo de registro?

✅ Respuesta correcta:

La nueva entrada (jrafael...) aparece al final del contenido del archivo.

📘 Explicación:

El modo "a" (append) abre el archivo para escribir, pero posiciona el cursor al final del archivo existente. Cualquier operación de escritura (.write()) añadirá el nuevo contenido después del contenido original, sin borrarlo.

---

### 🧠 Tarea 5

...cree una variable llamada `import_file` que almacene el nombre del archivo `"allow_list.txt"`. ...muestre las dos variables...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the text file that you want to create
import_file = "allow_list.txt"

# Assign `ip_addresses` to a list of IP addresses that are allowed to access the restricted information
ip_addresses = "192.168.218.160 192.168.97.225 192.168.145.158 192.168.108.13 192.168.60.153 192.168.96.200 192.168.247.153 192.168.3.252 192.168.116.187 192.168.15.110 192.168.39.246"

# Display `import_file`
print(import_file)

# Display `ip_addresses`
print(ip_addresses)
```

---

### 🧠 Tarea 6

...cree una sentencia `with` para escribir `ip_addresses` en el archivo de texto... ábralo usando el parámetro `"w"`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the text file that you want to create
import_file = "allow_list.txt"

# Assign `ip_addresses` to a list of IP addresses that are allowed to access the restricted information
ip_addresses = "192.168.218.160 192.168.97.225 192.168.145.158 192.168.108.13 192.168.60.153 192.168.96.200 192.168.247.153 192.168.3.252 192.168.116.187 192.168.15.110 192.168.39.246"

# Create a `with` statement to write to the text file
with open(import_file, "w") as file:

  # Write `ip_addresses` to the text file
  file.write(ip_addresses)
```

---

### 🧠 Tarea 7

...añada código para leer el archivo que contiene las direcciones IP. Complete una sentencia `with` que lea el archivo de texto y lo almacene en `text`. ...muestre `text`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the text file that you want to create
import_file = "allow_list.txt"

# Assign `ip_addresses` to a list of IP addresses that are allowed to access the restricted information
ip_addresses = "192.168.218.160 192.168.97.225 192.168.145.158 192.168.108.13 192.168.60.153 192.168.96.200 192.168.247.153 192.168.3.252 192.168.116.187 192.168.15.110 192.168.39.246"

# Create a `with` statement to write to the text file
with open(import_file, "w") as file:

    # Write `ip_addresses` to the text file
    file.write(ip_addresses)

# Create a `with` statement to read in the text file
with open(import_file, "r") as file:

    # Read the file and store the result in a variable named `text`
    text = file.read()

# Display the contents of `text`
print(text)
```

---

### 🧠 Conclusión

¿Cuáles son sus principales conclusiones de este laboratorio?

✅ **Conclusiones clave:**

- **`with open()` es Esencial:** Es la forma estándar y segura de trabajar con archivos en Python, ya que garantiza que los archivos se cierren automáticamente.
    
- **Modos de Apertura:** Los modos `"r"` (leer), `"w"` (escribir, sobrescribe) y `"a"` (añadir al final) determinan cómo interactúas con el archivo.
    
- **Leer Contenido:** El método `.read()` carga todo el contenido de un archivo como una sola cadena.
    
- **Dividir Contenido:** El método `.split()` es fundamental para convertir una cadena (leída de un archivo) en una lista, generalmente separando por líneas (espacios en blanco por defecto) para facilitar el análisis.
    
- **Escribir Contenido:** El método `.write()` permite escribir una cadena en un archivo (abierto en modo `"w"` o `"a"`).
    
- **Combinación de Operaciones:** Puedes combinar estas operaciones: leer un archivo, modificar los datos (quizás como una lista) y luego escribir los datos actualizados de nuevo en un archivo (después de volver a unirlos si es necesario).