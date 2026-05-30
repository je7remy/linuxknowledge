---

## 📝 Actividad de Portafolio: Actualizar un Archivo Mediante un Algoritmo Python

### **Resumen de la Actividad**

En esta actividad, crearás un nuevo documento de portafolio para demostrar tu experiencia usando Python para desarrollar algoritmos que involucran abrir archivos y analizar su contenido. Puedes agregar este documento a tu portafolio de ciberseguridad, el cual puedes compartir con posibles empleadores o reclutadores. Para revisar la importancia de crear un portafolio profesional y las opciones para crear tu portafolio, lee _Crear un portafolio de ciberseguridad_.

Para crear tu documento de portafolio, revisarás un escenario y seguirás una serie de pasos. Este escenario está relacionado con el laboratorio **Crea otro algoritmo** que acabas de completar. Explicarás el código que desarrollaste en ese laboratorio, y esto te ayudará a prepararte para futuras entrevistas de trabajo y otros pasos del proceso de contratación.

**Asegúrese de completar esta actividad antes de continuar.** El siguiente punto del curso le proporcionará un ejemplo completado para comparar con su propio trabajo.

---

### **🏥 Escenario**

Revise el siguiente escenario. A continuación, complete las instrucciones paso a paso.

Usted es un profesional de la seguridad que trabaja en una **empresa de atención sanitaria**. Como parte de su trabajo, se le pide que **actualice regularmente un archivo** que identifica a los empleados que pueden acceder a contenido restringido (basado en quién trabaja con registros personales de pacientes). El acceso está restringido por dirección IP.

- Existe una **lista de permitidos** (`allow_list.txt`) de direcciones IP autorizadas.
    
- También hay una **lista de eliminados** (`remove_list`) que identifica qué IPs deben eliminarse de la lista de permitidos.
    

**Tu tarea:** Crear un algoritmo en Python que:

1. Compruebe si la lista de permitidos contiene alguna IP de la lista de eliminados.
    
2. Si es así, elimine esas direcciones IP del archivo `allow_list.txt`.
    

**Nota:** Este escenario implica desarrollar el mismo algoritmo que en las **Tareas 2-7** del laboratorio _Crear otro algoritmo_. (No necesita consultar la Tarea 1 y las Tareas 8-10). Deberá volver a visitar el laboratorio para obtener **capturas de pantalla** para incluir en su documento.

---

### **📋 Instrucciones Paso a Paso**

Sigue las instrucciones para completar cada paso. A continuación, responda a las 9 preguntas al final antes de comparar su trabajo con el ejemplo.

#### **Paso 1: Acceder a la Plantilla**

- Para utilizar la plantilla, haga clic en el enlace y seleccione **Usar plantilla**.
    
    - **Enlace a la plantilla:** Algoritmo para actualización de archivos en Python
        
- O, si no tiene cuenta de Google, descargue la plantilla adjunta.
    

#### **Material de Apoyo (Instrucciones Código Python)**

- Este documento proporciona buenas prácticas para incluir código Python en su portafolio. Manténgalo abierto.
    
    - **Enlace al material:** Instrucciones para incluir código Python
        
- O descargue el material adjunto.
    

#### **Paso 2: Completar la Plantilla - Descripción del Proyecto**

- En la sección **Descripción del proyecto**, ofrece una visión general del escenario y de lo que has logrado en Python (3-5 frases).
    

#### **Paso 3: Completar la Plantilla - Abrir Archivo**

- **Tarea:** Abrir `allow_list.txt`. Asignar `"allow_list.txt"` a `import_file`. Usar `with open(...) as file:` en modo lectura (`"r"`).
    
- **En la plantilla:** Describe la sintaxis (`with`, `open`, `"r"`, `as file`) en la sección **Abrir el archivo que contiene la lista de permitidos**.
    
- **Incluir código:** Agrega una captura de pantalla de la Tarea 2 del lab o escribe el código.
    

#### **Paso 4: Completar la Plantilla - Leer Contenido**

- **Tarea:** Usar el método `.read()` para leer el contenido del archivo (`file`) y almacenarlo como cadena en la variable `ip_addresses`.
    
- **En la plantilla:** Describe la sintaxis (`file.read()`, asignación a `ip_addresses`) en la sección **Leer el contenido del archivo**.
    
- **Incluir código:** Agrega una captura de pantalla de la Tarea 3 del lab o escribe el código.
    

#### **Paso 5: Completar la Plantilla - Convertir a Lista**

- **Tarea:** Convertir la cadena `ip_addresses` en una lista usando el método `.split()`.
    
- **En la plantilla:** Describe la sintaxis (`ip_addresses.split()`, reasignación) en la sección **CONVERTIR la cadena en una lista**.
    
- **Incluir código:** Agrega una captura de pantalla de la Tarea 4 del lab o escribe el código.
    

#### **Paso 6: Completar la Plantilla - Iterar Lista Eliminados**

- **Tarea:** Establecer el encabezado de un bucle `for` que itere a través de `remove_list`. Usar `element` como variable de bucle.
    
- **En la plantilla:** Describe la sintaxis (`for element in remove_list:`) en la sección **Iterar a través de la lista de eliminados**.
    
- **Incluir código:** Agrega una captura de pantalla de la Tarea 5 del lab (solo la línea `for`) o escribe el código.
    

#### **Paso 7: Completar la Plantilla - Eliminar IPs**

- **Tarea:** Dentro del bucle `for`, añadir un condicional `if` que evalúe si `element` (la IP a eliminar) está `in ip_addresses` (la lista de permitidos). Si es `True`, aplicar el método `.remove(element)` a `ip_addresses`.
    
- **En la plantilla:** Describe la sintaxis (`if element in ip_addresses:`, `ip_addresses.remove(element)`) en la sección **Eliminar direcciones IP que están en la lista de eliminación**.
    
- **Incluir código:** Agrega una captura de pantalla de la Tarea 6 del lab o escribe el código.
    
- **Añadir explicación:** Incluye una frase indicando que `.remove()` funciona aquí porque no hay duplicados en `ip_addresses`.
    

#### **Paso 8: Completar la Plantilla - Actualizar Archivo**

- **Tarea:** Convertir la lista `ip_addresses` (ya modificada) de nuevo en una cadena usando `"\n".join(ip_addresses)`. Luego, usar otra sentencia `with open(import_file, "w") as file:` y el método `file.write()` para escribir la nueva cadena en el archivo (sobrescribiendo el original).
    
- **En la plantilla:** Describe la sintaxis (`"\n".join()`, `with open`, `"w"`, `file.write()`) en la sección **Actualizar el archivo con la lista revisada de direcciones IP**.
    
- **Incluir código:** Agrega una captura de pantalla de la Tarea 7 del lab o escribe el código.
    

#### **Paso 9: Completar la Plantilla - Resumen**

- En la sección **Resumen**, proporciona un breve resumen del algoritmo destacando sus componentes principales (4-6 frases).
    

---

### **⭐ Consejo Profesional: Guarda una Copia**

Por último, asegúrate de guardar una copia de tu actividad terminada. Puedes utilizarla en tu portafolio profesional para demostrar tus conocimientos y/o experiencia a posibles empleadores.

---

### **✔️ Qué Incluir en tu Respuesta**

Asegúrate de incluir lo siguiente en tu actividad completada:

- Capturas de pantalla de tu código Python o versiones escritas del código.
    
- Explicaciones de la sintaxis, funciones y palabras clave del código.
    
- Una descripción del proyecto al principio.
    
- Un resumen al final.
    
- Detalles sobre el uso de `with open()` en tu algoritmo.
    
- Detalles sobre el uso de los métodos `.read()` y `.write()`.
    
- Utilización del método `.split()`.
    
- Cómo utilizar un bucle `for`.
    
- Utilización del método `.remove()`.
    

---

### **💯 Paso 10: Evalúe su Actividad (Autoevaluación)**

Utiliza la siguiente autoevaluación para revisar tu trabajo. Hay **9 puntos** posibles (1 punto por afirmación).

1. Abre tu actividad completada.
    
2. Responde **Sí** o **No** a cada afirmación en la herramienta de autoevaluación del curso.
    

Recibirás una puntuación porcentual. La nota de aprobado recomendada es **≥ 80% (8/9 puntos)**. Si es necesario, revisa tu proyecto y vuelve a enviar tus respuestas. Intenta conseguir al menos 8 puntos antes de continuar.

---

## 📄 Algoritmo para Actualización de Archivos en Python

### **Project description**

Este proyecto demuestra cómo automatizar la actualización de una lista de control de acceso (ACL) basada en direcciones IP almacenada en un archivo de texto (`allow_list.txt`). Como profesional de seguridad en una empresa de atención médica, es crucial mantener esta lista actualizada para asegurar que solo el personal autorizado acceda a contenido restringido, como registros de pacientes. El algoritmo lee la lista de IPs permitidas actual, la compara con una lista de IPs que deben ser eliminadas (`remove_list`), realiza las eliminaciones necesarias y finalmente reescribe el archivo `allow_list.txt` con la información actualizada. Este proceso utiliza Python para leer, procesar y escribir archivos de texto.

---

### **Open the file that contains the allow list**

Para empezar, necesitamos acceder al archivo que contiene las direcciones IP permitidas. Utilizo la sentencia **`with open()`** de Python, que es la forma recomendada para manejar archivos, ya que asegura que el archivo se cierre correctamente al finalizar. La función **`open()`** recibe el nombre del archivo (guardado en `import_file`) y el modo de apertura, que es **`"r"`** (read) para leer su contenido inicial. El objeto archivo abierto se asigna a la variable `file` mediante **`as file`**.

Python

```
import_file = "allow_list.txt"
# remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"] # Definida previamente

with open(import_file, "r") as file:
    # Código para leer el archivo va aquí
    pass
```

---

### **Read the file contents**

Dentro del bloque `with`, una vez abierto el archivo, leo todo su contenido usando el método **`.read()`** aplicado al objeto `file`. Este método devuelve todo el contenido del archivo como una **única cadena de texto**. Almaceno esta cadena en la variable `ip_addresses` para su posterior procesamiento.

Python

```
# Dentro del bloque 'with open(import_file, "r") as file:'
ip_addresses = file.read()

# Ahora ip_addresses contiene todo el texto del archivo
# print(ip_addresses)
```

---

### **Convert the string into a list**

La cadena leída contiene múltiples direcciones IP, probablemente separadas por espacios o saltos de línea. Para poder trabajar con cada IP individualmente, convierto la cadena `ip_addresses` en una **lista** de Python. Utilizo el método de cadena **`.split()`** sin argumentos, lo que divide la cadena en cada espacio en blanco (incluidos saltos de línea), resultando en una lista donde cada elemento es una dirección IP. El resultado se reasigna a la variable `ip_addresses`.

Python

```
# ip_addresses es inicialmente la cadena leída del archivo
ip_addresses = ip_addresses.split()

# Ahora ip_addresses es una lista de cadenas
# print(ip_addresses)
```

---

### **Iterate through the remove list**

Para procesar las eliminaciones, necesito recorrer la lista que contiene las direcciones IP que ya no están permitidas. Utilizo un bucle **`for`** para iterar sobre cada elemento en `remove_list`. La variable `element` tomará el valor de cada IP a eliminar en cada pasada del bucle.

Python

```
# remove_list = [...] # Definida previamente
# ip_addresses = [...] # Es ahora una lista

for element in remove_list:
    # Código para verificar y eliminar va aquí
    pass
```

---

### **Remove IP addresses that are on the remove list**

Dentro del bucle `for`, para cada dirección IP (`element`) de la `remove_list`, compruebo si esa dirección existe actualmente en la lista `ip_addresses` (la lista de permitidos). Uso una sentencia **`if`** con el operador **`in`** para esta verificación (`if element in ip_addresses:`). Si la dirección IP a eliminar se encuentra en la lista de permitidos, utilizo el método de lista **`.remove()`** para quitarla. El método `ip_addresses.remove(element)` elimina la primera ocurrencia del valor `element` de la lista `ip_addresses`.

Aplicar el método `.remove()` de esta manera es posible porque no hay duplicados en la lista `ip_addresses`.

Python

```
# Dentro del bucle 'for element in remove_list:'
if element in ip_addresses:
    ip_addresses.remove(element)

# La lista ip_addresses se modifica directamente
# print(ip_addresses)
```

---

### **Update the file with the revised list of IP addresses**

Una vez que el bucle ha terminado y se han eliminado todas las IPs necesarias de la lista `ip_addresses`, debo guardar esta lista actualizada en el archivo original. Como el método `.write()` necesita una cadena, primero convierto la lista `ip_addresses` de nuevo en una cadena usando el método **`.join()`**. Lo aplico a la cadena **`"\n"`** (nueva línea) para que cada IP se escriba en una línea separada en el archivo. Luego, abro el archivo `import_file` de nuevo con **`with open()`**, pero esta vez en modo escritura **`"w"`** (write), que sobrescribe el contenido anterior. Finalmente, uso el método **`.write()`** para escribir la cadena recién creada en el archivo.

Python

```
# ip_addresses es la lista final después de las eliminaciones

# Convertir la lista a cadena con saltos de línea
ip_addresses_string = "\n".join(ip_addresses)

# Reescribir el archivo con el contenido actualizado
with open(import_file, "w") as file:
    file.write(ip_addresses_string)
```

---

### **Summary**

Este algoritmo automatiza eficazmente la tarea de mantener actualizada una lista de permitidos de IP almacenada en un archivo. Lee el archivo `allow_list.txt`, convierte su contenido en una lista manipulable usando `.read()` y `.split()`. Procesa una lista separada de IPs a eliminar (`remove_list`), iterando sobre ella y eliminando las coincidencias de la lista de permitidos mediante un bucle `for`, condicionales `if` y el método `.remove()`. Finalmente, reconstruye el contenido del archivo como una cadena con formato (usando `"\n".join()`) y sobrescribe el archivo original con la lista actualizada usando `with open()` en modo escritura y `.write()`. Este proceso asegura que la lista de acceso refleje con precisión los permisos actuales, combinando manejo de archivos, manipulación de listas y cadenas, y lógica de control.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[7- Crear otro algoritmo]]
- ➡️ Siguiente: [[9- Ejemplo de actividad de Portfolio - Actualizar un fichero mediante un algoritmo Python]]
