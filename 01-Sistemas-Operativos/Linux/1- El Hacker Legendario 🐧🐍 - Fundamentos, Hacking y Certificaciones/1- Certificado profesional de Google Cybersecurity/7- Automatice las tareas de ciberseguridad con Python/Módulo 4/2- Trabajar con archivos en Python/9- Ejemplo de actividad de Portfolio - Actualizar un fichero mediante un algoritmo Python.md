
## 📄 Algoritmo para Actualización de Archivos en Python

### **Descripción del proyecto** 📝

En mi organización, el acceso a contenido restringido se controla con una lista de permitidos de direcciones IP. El archivo **"allow_list.txt"** identifica estas direcciones IP. Una lista de eliminación separada identifica las direcciones IP que ya no deberían tener acceso a este contenido. Creé un algoritmo para automatizar la actualización del archivo "allow_list.txt" y eliminar estas direcciones IP que ya no deberían tener acceso.

---

### **Abrir el archivo que contiene la lista de permitidos** 📂

Para la primera parte del algoritmo, abrí el archivo "allow_list.txt". Primero, asigné este nombre de archivo como una cadena a la variable `import_file`:

Python

```
import_file = "allow_list.txt"
```

Luego, usé una declaración **`with`** para abrir el archivo:

Python

```
with open(import_file, "r") as file:
    # El código para leer sigue
    pass
```

En mi algoritmo, la declaración **`with`** se usa con la función **`open()`** en modo lectura (**`"r"`**) para abrir el archivo de la lista de permitidos con el propósito de leerlo. El propósito de abrir el archivo es permitirme acceder a las direcciones IP almacenadas en el archivo de la lista de permitidos. La palabra clave **`with`** ayudará a administrar los recursos cerrando el archivo después de salir de la declaración `with`. En el código `with open(import_file, "r") as file:`, la función `open()` tiene dos parámetros. El primero identifica el archivo a importar, y el segundo indica qué quiero hacer con el archivo. En este caso, **`"r"`** indica que quiero leerlo. El código también usa la palabra clave **`as`** para asignar una variable llamada `file`; `file` almacena la salida de la función `open()` mientras trabajo dentro de la declaración `with`.

---

### **Leer el contenido del archivo** 📖

Para leer el contenido del archivo, usé el método **`.read()`** para convertirlo en una cadena.

Python

```
# Dentro del bloque 'with open(...) as file:'
ip_addresses = file.read()
```

Al usar una función `open()` que incluye el argumento **`"r"`** para “leer”, puedo llamar a la función **`.read()`** en el cuerpo de la declaración `with`. El método `.read()` convierte el archivo en una cadena y me permite leerlo. Apliqué el método `.read()` a la variable `file` identificada en la declaración `with`. Luego, asigné la salida de cadena de este método a la variable `ip_addresses`.

En resumen, este código lee el contenido del archivo "allow_list.txt" en un formato de cadena que me permite usar posteriormente la cadena para organizar y extraer datos en mi programa Python.

---

### **Convertir la cadena en una lista** 🔄

Para eliminar direcciones IP individuales de la lista de permitidos, necesitaba que estuviera en formato de lista. Por lo tanto, a continuación usé el método **`.split()`** para convertir la cadena `ip_addresses` en una lista:

Python

```
# Después de leer el contenido del archivo en la cadena ip_addresses
ip_addresses = ip_addresses.split()
```

La función **`.split()`** se llama añadiéndola a una variable de cadena. Funciona convirtiendo el contenido de una cadena en una lista. El propósito de dividir `ip_addresses` en una lista es facilitar la eliminación de direcciones IP de la lista de permitidos. Por defecto, la función `.split()` divide el texto por espacios en blanco en elementos de lista. En este algoritmo, la función `.split()` toma los datos almacenados en la variable `ip_addresses`, que es una cadena de direcciones IP separadas cada una por un espacio en blanco, y convierte esta cadena en una lista de direcciones IP. Para almacenar esta lista, la reasigné de nuevo a la variable `ip_addresses`.

---

### **Iterar a través de la lista de eliminación** 🚶‍♀️

Una parte clave de mi algoritmo implica iterar a través de las direcciones IP que son elementos en `remove_list`. Para hacer esto, incorporé un bucle **`for`**:

Python

```
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"] # Ejemplo
ip_addresses = [...] # ip_addresses es ahora una lista

for element in remove_list:
    # El código para verificar y eliminar sigue
    pass
```

El bucle **`for`** en Python repite código para una secuencia especificada. El propósito general del bucle `for` en un algoritmo Python como este es aplicar declaraciones de código específicas a todos los elementos en una secuencia. La palabra clave **`for`** inicia el bucle `for`. Es seguida por la variable de bucle `element` y la palabra clave **`in`**. La palabra clave `in` indica iterar a través de la secuencia `remove_list` y asignar cada valor a la variable de bucle `element`.

---

### **Eliminar direcciones IP que están en la lista de eliminación** ❌

Mi algoritmo requiere eliminar cualquier dirección IP de la lista de permitidos, `ip_addresses`, que también esté contenida en `remove_list`. Como no había duplicados en `ip_addresses`, pude usar el siguiente código para hacer esto:

Python

```
# Dentro del bucle 'for element in remove_list:'
if element in ip_addresses:
    ip_addresses.remove(element)
```

Primero, dentro de mi bucle `for`, creé una condición (**`if`**) que evaluaba si la variable de bucle `element` se encontraba **`in`** la lista `ip_addresses`. Hice esto porque aplicar `.remove()` a elementos que no se encontraban en `ip_addresses` resultaría en un error.

Luego, dentro de esa condición, apliqué **`.remove()`** a `ip_addresses`. Pasé la variable de bucle `element` como argumento para que cada dirección IP que estuviera en `remove_list` fuera eliminada de `ip_addresses`.

---

### **Actualizar el archivo con la lista revisada de direcciones IP** 💾

Como paso final en mi algoritmo, necesitaba actualizar el archivo de la lista de permitidos con la lista revisada de direcciones IP. Para hacerlo, primero necesitaba convertir la lista de nuevo en una cadena. Usé el método **`.join()`** para esto:

Python

```
# ip_addresses es la lista modificada
ip_addresses_string = "\n".join(ip_addresses)
```

El método **`.join()`** combina todos los elementos en un iterable en una cadena. El método `.join()` se aplica a una cadena que contiene caracteres que separarán los elementos en el iterable una vez unidos en una cadena. En este algoritmo, usé el método `.join()` para crear una cadena a partir de la lista `ip_addresses` para poder pasarla como argumento al método `.write()` al escribir en el archivo "allow_list.txt". Usé la cadena (**`"\n"`**) como separador para instruir a Python a colocar cada elemento en una nueva línea.

Luego, usé otra declaración **`with`** y el método **`.write()`** para actualizar el archivo:

Python

```
with open(import_file, "w") as file:
    file.write(ip_addresses_string)
```

Esta vez, usé un segundo argumento de **`"w"`** con la función `open()` en mi declaración `with`. Este argumento indica que quiero abrir un archivo para **escribir** sobre su contenido. Al usar este argumento `"w"`, puedo llamar a la función **`.write()`** en el cuerpo de la declaración `with`. La función `.write()` escribe datos de cadena en un archivo especificado y reemplaza cualquier contenido de archivo existente.

En este caso, quería escribir la lista de permitidos actualizada como una cadena en el archivo "allow_list.txt". De esta manera, el contenido restringido ya no será accesible para ninguna dirección IP que se eliminó de la lista de permitidos. Para reescribir el archivo, añadí la función `.write()` al objeto `file` que identifiqué en la declaración `with`. Pasé la variable `ip_addresses_string` como argumento para especificar que el contenido del archivo especificado en la declaración `with` debería ser reemplazado con los datos en esta variable.

---

### **Resumen** ✨

Creé un algoritmo que elimina direcciones IP identificadas en una variable `remove_list` del archivo **"allow_list.txt"** de direcciones IP aprobadas. Este algoritmo implicó abrir el archivo (**`with open("r")`**), convertirlo en una cadena para ser leído (**`.read()`**), y luego convertir esta cadena en una lista almacenada en la variable `ip_addresses` (**`.split()`**). Luego iteré a través de las direcciones IP en `remove_list` (bucle **`for`**). Con cada iteración, evalué si el elemento era parte de la lista `ip_addresses` (**`if element in ip_addresses:`**). Si lo era, apliqué el método **`.remove()`** para eliminar el elemento de `ip_addresses`. Después de esto, usé el método **`.join()`** para convertir `ip_addresses` de nuevo en una cadena (separada por nuevas líneas `"\n"`) para poder escribir sobre el contenido del archivo "allow_list.txt" (**`with open("w")`**, **`.write()`**) con la lista revisada de direcciones IP.