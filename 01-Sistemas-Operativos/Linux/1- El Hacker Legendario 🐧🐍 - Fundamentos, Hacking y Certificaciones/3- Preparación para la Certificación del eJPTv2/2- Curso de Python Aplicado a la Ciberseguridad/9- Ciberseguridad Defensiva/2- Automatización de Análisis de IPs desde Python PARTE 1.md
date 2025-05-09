
### 1. Contexto y Objetivo

- **Contexto en Ciberseguridad:**  
    Se trata de automatizar el análisis de vulnerabilidades en el ámbito de la ciberseguridad, centrándonos esta vez en el escaneo de direcciones IP para determinar si son maliciosas o inocuas. Esto es especialmente útil en ambientes como un SOC (Centro de Operaciones de Seguridad), donde se requiere evaluar rápidamente múltiples IPs.
    
- **Objetivo del Ejemplo:**  
    Utilizar Python para automatizar consultas a un servicio web – en este caso, **Abuse-IP** – el cual dispone de una extensa base de datos con reportes de actividad sospechosa asociados a direcciones IP. La idea es, mediante el uso de la API de Abuse-IP, obtener información que permita identificar si una IP ha sido reportada por actividades maliciosas (por ejemplo, spam o ataques).
    

---

### 2. Exploración y Análisis de la Herramienta Abuse-IP

En este paso se profundiza en el funcionamiento y la utilidad práctica de Abuse-IP, antes de pasar a la automatización:

- **Interfaz y Usabilidad:**  
    Abuse-IP ofrece una interfaz web intuitiva donde se puede ingresar manualmente cualquier dirección IP para obtener un reporte completo. La herramienta muestra información como el número total de reportes, las categorías de incidentes (por ejemplo, spam, ataques, etc.) y otros detalles relevantes, lo que permite a un analista tener una primera impresión sobre la reputación de la IP.
    
- **Comprensión del Reporte:**  
    Analizar manualmente un reporte ayuda a identificar qué datos son significativos para determinar si una IP es maliciosa o no. Por ejemplo, se puede observar el porcentaje de confianza en los reportes, la frecuencia de las incidencias y la naturaleza de los incidentes reportados. Esta información es crucial para definir criterios y umbrales en un análisis automatizado.
    
- **Importancia en un Entorno Real:**  
    En un SOC o durante una investigación de seguridad, comenzar con un análisis manual permite familiarizarse con el formato y la calidad de los datos que Abuse-IP proporciona. Esta experiencia práctica es esencial para diseñar y ajustar scripts automatizados que puedan interpretar correctamente la información y tomar decisiones basadas en ella.


---

### 3. Integración de la API con Python

- **Motivación de la Automatización:**
    
    - La idea es que, en vez de realizar consultas manuales, se automatice el proceso usando Python.
        
    - Con la API de Abuse-IP, se puede enviar una dirección IP (o incluso un lote de direcciones) y recibir un informe detallado en formato JSON. Esto permite filtrar y analizar automáticamente la información relevante.
        
- **Proceso de Obtención del API Key:**
    
    - Primero se debe crear una cuenta en Abuse-IP (en este caso se opta por la modalidad gratuita).
        
    - Luego, dentro de la configuración de la cuenta, se accede a la sección **API** donde se puede generar una clave.
        
    - En el ejemplo se muestra cómo generar la clave, asignarle un nombre (por ejemplo, "Python course") y copiarla para su uso posterior en el script.
        
- **Límites y Uso Gratuito:**
    
    - Se destaca que, en la modalidad gratuita, Abuse-IP permite realizar un número considerable de consultas diarias. En el ejemplo, el uso de dos consultas apenas consume el 0.2% de la cuota diaria.
        

---

### 4. Desglose del Código en Python

Se utiliza la librería **`requests`** de Python para realizar peticiones HTTP a la API de Abuse-IP. A continuación, se explica cada parte del código:

1. **Importación de la Librería:**
    
    ```python
    import requests
    ```
    
    - Se importa la librería `requests` que permite hacer peticiones HTTP de manera sencilla.
        
2. **Definición de la URL Base de la API:**
    
    ```python
    url = 'https://api.abuseipdb.com/api/v2/check/'
    ```
    
    - Se define la variable `url` con la dirección de la API que se utilizará para hacer el chequeo de la IP.
        
    - La URL es fija y siempre se debe usar esta misma dirección para acceder al endpoint de verificación.
        
3. **Asignación del API Key:**
    
    ```python
    api_key = '523f2f2a30ac7df2daa6da8c6022737033addd66345f081896614d638969047ce9a6746ae888d9de'
    ```
    
    - Se guarda el API key (obtenido previamente en la web de Abuse-IP) en la variable `api_key`.
        
4. **Construcción del Diccionario de Parámetros (Payload):**
    
    ```python
    informacion = {
        "ipAddress": "209.38.16.157",
        "maxAgeInDays": "90"
    }
    ```
    
    - Se crea un diccionario llamado `informacion` que contiene:
        
        - **`ipAddress`**: La dirección IP que se desea analizar. En el ejemplo se usa la IP "209.38.16.157", aunque podría ser cualquier otra.
            
        - **`maxAgeInDays`**: Se establece el parámetro para limitar los reportes a aquellos realizados en un máximo de 90 días. Esto permite obtener datos recientes y relevantes.
            
5. **Configuración de los Headers para la Petición:**
    
    ```python
    api = {
        "key": api_key,
        "Accept": "application/json"
    }
    ```
    
    - Se crea otro diccionario llamado `api` que contendrá:
        
        - **`key`**: La clave API que autentica la petición.
            
        - **`Accept`**: Se especifica que la respuesta se espera en formato JSON, lo cual es importante para poder trabajar fácilmente con los datos.
            
6. **Realización de la Petición GET:**
    
    ```python
    respuesta = requests.get(url, headers=api, params=informacion)
    ```
    
    - Se realiza una petición GET a la URL de la API.
        
    - Se pasan dos parámetros clave:
        
        - **`headers`**: Con el diccionario `api` que contiene la clave de autenticación y el formato de respuesta.
            
        - **`params`**: Con el diccionario `informacion` que contiene la IP a analizar y el límite de antigüedad de los reportes.
            
7. **Procesamiento y Visualización de la Respuesta:**
    
    ```python
    respuesta_json = respuesta.json()
    print(respuesta_json)
    ```
    
    - Se convierte la respuesta obtenida a formato JSON y se guarda en la variable `respuesta_json`.
        
    - Finalmente, se imprime el contenido JSON, que incluirá detalles como:
        
        - Si la IP es parte de una red inalámbrica o no.
            
        - El porcentaje de reportes o “confianza” de la información.
            
        - Número total de reportes y las razones asociadas a cada reporte (por ejemplo, spam, ataques, etc.).
            

---

### 5. Ejecución y Resultados

- **Proceso de Ejecución:**
    
    - Se guarda el script en un archivo (por ejemplo, `script.py`) dentro de Visual Studio Code.
        
    - Se abre la terminal (usando la opción integrada en VS Code) y se ejecuta el script con el comando `python script.py` (o `python3 script.py` según el sistema operativo).
        
- **Interpretación del Resultado:**
    
    - Al ejecutar el script, se realiza la consulta a la API y se muestra en la terminal el reporte completo en formato JSON.
        
    - La información mostrada permite identificar si la IP tiene actividad maliciosa (por ejemplo, porcentaje de reportes elevado, número de reportes) y la naturaleza de los incidentes reportados.
        
    - Con base en estos datos, se podrían implementar condicionales en el código para automatizar acciones (por ejemplo, marcar una IP como maliciosa si supera cierto umbral de reportes).
        

---

### 6. Posibles Extensiones Futuras

- **Filtrado Automático:**  
    Se pueden agregar condicionales para automatizar la clasificación de las IPs. Por ejemplo:
    
    - Si el porcentaje de reportes es mayor al 10% o si la cantidad de reportes supera un valor específico, la IP podría ser etiquetada automáticamente como maliciosa.
        
- **Manejo de Múltiples IPs:**  
    Se puede ampliar el script para iterar sobre una lista de IPs, analizando cada una de ellas y generando reportes automáticos para cada caso.
    
- **Integración en Sistemas de Monitoreo:**  
    En un entorno corporativo o en un SOC, este tipo de automatización puede integrarse en herramientas de monitoreo para alertar a tiempo sobre posibles amenazas.
    

---

### Conclusión

El proceso descrito muestra cómo se puede utilizar Python y la librería `requests` para interactuar con la API de Abuse-IP, obteniendo información valiosa sobre la reputación de una dirección IP. Desde la obtención y configuración del API key, hasta el envío de parámetros específicos y la interpretación del resultado, cada paso está diseñado para facilitar la automatización en entornos de ciberseguridad, permitiendo respuestas rápidas y precisas ante posibles amenazas.

Esta metodología, al integrarse en un flujo de trabajo automatizado, resulta extremadamente útil para equipos de seguridad que necesitan evaluar de forma eficiente múltiples direcciones IP y responder ante actividades maliciosas.


### Código Completo:

````python
import requests

  

url = 'https://api.abuseipdb.com/api/v2/check/'

api_key = '523f2f2a30ac7df2daa6da8c6022737033addd66345f081896614d638969047ce9a6746ae888d9de'

  

informacion = {

  

    "ipAddress": "209.38.16.157",

    "maxAgeInDays":"90"

}

  

api = {

  

    "key":api_key,

    "Accept": "application/json"

}

  

respuesta = requests.get(url, headers=api, params=informacion)

  

respuesta_json = respuesta.json()

print(respuesta_json)
`````

