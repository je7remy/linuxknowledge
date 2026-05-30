---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Crear otro algoritmo

### 🧠 Tarea 1

...Muestre las variables `import_file` y `remove_list`...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the file
import_file = "allow_list.txt"

# Assign `remove_list` to a list of IP addresses that are no longer allowed to access restricted information.
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# Display `import_file`
print(import_file)

# Display `remove_list`
print(remove_list)
```

---

### 🧠 Pregunta 1

¿Qué observa sobre la salida anterior?

✅ Respuesta correcta:

La salida muestra el nombre del archivo de texto ("allow_list.txt") en la primera línea y la lista de direcciones IP a eliminar (['192.168.97.225', '192.168.158.170', '192.168.201.40', '192.168.58.57']) en la segunda línea.

---

### 🧠 Tarea 2

...empiece abriendo el archivo de texto usando `import_file`, la palabra clave `with`, y la función `open()` con el parámetro `"r"`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the file
import_file = "allow_list.txt"

# Assign `remove_list` to a list of IP addresses that are no longer allowed to access restricted information.
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# First line of `with` statement
with open(import_file, "r") as file:
    pass # Placeholder for the body
```

---

### 🧠 Tarea 3

...use el método `.read()` para leer el archivo importado y almacénelo en `ip_addresses`. ...muestre `ip_addresses`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the file
import_file = "allow_list.txt"

# Assign `remove_list` to a list of IP addresses that are no longer allowed to access restricted information.
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# Build `with` statement to read in the initial contents of the file
with open(import_file, "r") as file:

  # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`
  ip_addresses = file.read()

# Display `ip_addresses`
print(ip_addresses)
```

---

### 🧠 Pregunta 2

¿Nota alguna dirección IP en la lista de permitidos que también esté en `remove_list`?

✅ Respuesta correcta:

Sí. Al inspeccionar la salida de la cadena ip_addresses (el contenido del archivo) y compararla con remove_list, se puede observar que "192.168.97.225" está presente en ambas. (Nota: Las otras IPs de remove_list pueden o no estar en el archivo inicial, dependiendo de su contenido exacto).

---

### 🧠 Tarea 4

...reasigne `ip_addresses` para actualizar su tipo de dato de cadena a lista. Use el método `.split()`. ...muestre `ip_addresses`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the file
import_file = "allow_list.txt"

# Assign `remove_list` to a list of IP addresses that are no longer allowed to access restricted information.
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# Build `with` statement to read in the initial contents of the file
with open(import_file, "r") as file:

  # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`
  ip_addresses = file.read()

# Use `.split()` to convert `ip_addresses` from a string to a list
ip_addresses = ip_addresses.split()

# Display `ip_addresses`
print(ip_addresses)
```

---

### 🧠 Tarea 5

...construya la sentencia iterativa. Nombre la variable del bucle `element`, recorra `ip_addresses` y muestre cada `element`.

✅ **Respuesta correcta (Código):**

Python

```
# (Código anterior omitido por brevedad) ...
with open(import_file, "r") as file:
  ip_addresses = file.read()
ip_addresses = ip_addresses.split()

# Build iterative statement
# Name loop variable `element`
# Loop through `ip_addresses`
for element in ip_addresses:

    # Display `element` in every iteration
    print(element)
```

---

### 🧠 Tarea 6

...construya una sentencia condicional para eliminar los elementos de `remove_list` de `ip_addresses`. ...si el elemento actual... está en `remove_list`, use el método `remove()`. ...muestre `ip_addresses` actualizada.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `import_file` to the name of the file
import_file = "allow_list.txt"

# Assign `remove_list` to a list of IP addresses that are no longer allowed to access restricted information.
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# Build `with` statement to read in the initial contents of the file
with open(import_file, "r") as file:
  ip_addresses = file.read()
ip_addresses = ip_addresses.split()

# Build iterative statement
# Name loop variable `element`
# Loop through `ip_addresses`
# Es importante iterar sobre una COPIA de la lista si la modificas dentro del bucle
for element in ip_addresses[:]: # Iterar sobre una copia [:]

  # Build conditional statement
  # If current element is in `remove_list`,
    if element in remove_list:

        # then current element should be removed from `ip_addresses`
        ip_addresses.remove(element)

# Display `ip_addresses`
print(ip_addresses)
```

_(Nota: Se añadió `[:]` al bucle `for` para iterar sobre una copia. Modificar una lista mientras se itera directamente sobre ella puede causar comportamientos inesperados)_.

---

### 🧠 Tarea 7

...construya la sentencia `with` que reescribe el archivo original. Use el parámetro `"w"`...

✅ **Respuesta correcta (Código):**

Python

```
# (Código anterior omitido por brevedad) ...
with open(import_file, "r") as file:
    ip_addresses = file.read()
ip_addresses = ip_addresses.split()
for element in ip_addresses[:]:
    if element in remove_list:
        ip_addresses.remove(element)

# Convert `ip_addresses` back to a string so that it can be written into the text file
ip_addresses_string = " ".join(ip_addresses) # Se cambió el nombre de la variable

# Build `with` statement to rewrite the original file
with open(import_file, "w") as file:

  # Rewrite the file, replacing its contents with `ip_addresses_string`
  file.write(ip_addresses_string)
```

_(Nota: Cambié el nombre de la variable a `ip_addresses_string` para mayor claridad después del `.join()`)_.

---

### 🧠 Tarea 8

...escriba otra sentencia `with`, esta vez para leer el archivo actualizado. ...almacene su contenido en `text`. ...muestre `text`.

✅ **Respuesta correcta (Código):**

Python

```
# (Código completo de las tareas anteriores omitido por brevedad) ...
# ... (leer, split, bucle for con remove, join, with open("w")...)

# Build `with` statement to read in the updated file
with open(import_file, "r") as file:

    # Read in the updated file and store the contents in `text`
    text = file.read()

# Display the contents of `text`
print(text)
```

---

### 🧠 Tarea 9

...defina una función llamada `update_file()` que tome dos parámetros: `import_file` y `remove_list`.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `update_file` that takes in two parameters: `import_file` and `remove_list`
# and combines the steps you've written in this lab leading up to this
def update_file(import_file, remove_list):

    # Build `with` statement to read in the initial contents of the file
    with open(import_file, "r") as file:
        # Use `.read()` to read the imported file and store it in a variable named `ip_addresses`
        ip_addresses = file.read()

    # Use `.split()` to convert `ip_addresses` from a string to a list
    ip_addresses = ip_addresses.split()

    # Build iterative statement
    # Name loop variable `element`
    # Loop through `ip_addresses` (iterating over a copy)
    for element in ip_addresses[:]:
        # Build conditional statement
        # If current element is in `remove_list`,
        if element in remove_list:
            # then current element should be removed from `ip_addresses`
            ip_addresses.remove(element)

    # Convert `ip_addresses` back to a string so that it can be written into the text file
    ip_addresses_string = " ".join(ip_addresses)

    # Build `with` statement to rewrite the original file
    with open(import_file, "w") as file:
        # Rewrite the file, replacing its contents with `ip_addresses_string`
        file.write(ip_addresses_string)
```

---

### 🧠 Pregunta 3

¿Cuáles son los beneficios de incorporar el algoritmo en una sola función?

✅ **Respuesta correcta:**

- **Reutilización:** Puedes llamar a la función `update_file()` fácilmente con diferentes nombres de archivo y diferentes listas de IPs a eliminar, sin tener que copiar y pegar todo el código cada vez.
    
- **Organización:** Agrupa toda la lógica relacionada en un solo bloque, haciendo el código más limpio y fácil de entender.
    
- **Mantenibilidad:** Si necesitas corregir o mejorar el algoritmo, solo tienes que hacerlo en un lugar (dentro de la definición de la función).
    
- **Abstracción:** Puedes usar la función sin necesidad de conocer los detalles internos de cómo funciona exactamente, solo necesitas saber qué parámetros acepta y qué hace.
    

---

### 🧠 Tarea 10

...llame a `update_file()`... Aplique la función a `"allow_list.txt"` y pase una lista... como segundo argumento. ...use una sentencia `with` para leer... muestre el contenido...

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `update_file` ...
def update_file(import_file, remove_list):
    # (Definición de la función de la Tarea 9) ...
    with open(import_file, "r") as file:
        ip_addresses = file.read()
    ip_addresses = ip_addresses.split()
    for element in ip_addresses[:]:
        if element in remove_list:
            ip_addresses.remove(element)
    ip_addresses_string = " ".join(ip_addresses)
    with open(import_file, "w") as file:
        file.write(ip_addresses_string)

# Call `update_file()` and pass in "allow_list.txt" and a list of IP addresses to be removed
update_file("allow_list.txt", ["192.168.25.60", "192.168.140.81", "192.168.203.198"])

# Build `with` statement to read in the updated file
with open("allow_list.txt", "r") as file:

  # Read in the updated file and store the contents in `text`
  text = file.read()

# Display the contents of `text`
print(text)
```

---

### 🧠 Conclusión

¿Cuáles son sus principales conclusiones de este laboratorio?

✅ **Conclusiones clave:**

- **Proceso Completo de Archivos:** Has practicado el ciclo completo de manipulación de archivos: leer (`"r"` y `.read()`), procesar los datos (convertir a lista con `.split()`, iterar con `for`, modificar con `if` y `.remove()`), y escribir los resultados de nuevo en el archivo (convertir a cadena con `.join()`, abrir en modo escritura `"w"` y usar `.write()`).
    
- **Algoritmos y Archivos:** Los algoritmos a menudo implican leer datos de una fuente (como un archivo), aplicar lógica para transformar o filtrar esos datos y, a veces, escribir el resultado de nuevo.
    
- **Mutabilidad de Listas:** La capacidad de modificar listas (usando `.remove()` en este caso) es esencial para tareas como actualizar listas de acceso.
    
- **Importancia de la Conversión de Tipos:** Fue necesario convertir la cadena leída del archivo a una lista (`.split()`) para poder iterar y eliminar elementos fácilmente, y luego volver a convertirla en una cadena (`.join()`) para poder escribirla de nuevo en el archivo.
    
- **Funciones para Reutilización:** Encapsular todo el algoritmo en una función (`update_file`) lo hace mucho más práctico y reutilizable para diferentes archivos o listas de eliminación.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[6- Desarrollar un algoritmo de análisis sintáctico en Python]]
- ➡️ Siguiente: [[8- Actividad de Portfolio - Actualizar un archivo mediante un algoritmo Python]]
