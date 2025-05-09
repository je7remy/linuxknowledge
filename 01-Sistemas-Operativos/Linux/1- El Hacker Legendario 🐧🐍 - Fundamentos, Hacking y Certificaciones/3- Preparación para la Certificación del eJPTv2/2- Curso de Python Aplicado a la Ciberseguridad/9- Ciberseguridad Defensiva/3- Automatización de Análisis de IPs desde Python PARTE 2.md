
## 1. Introducción y Objetivo

El objetivo del script es:

- Utilizar la API de AbuseIPDB para consultar información sobre direcciones IP.
    
- Analizar varias IPs de forma automática, recorriéndolas mediante un bucle `for`.
    
- Filtrar y mostrar únicamente el dato del número total de reportes (totalReports) que tiene cada IP.
    
- Además, se muestra cómo condicionar la salida para que se impriman solo aquellas IPs que superen un umbral de reportes (por ejemplo, más de 50).
    

---

## 2. Preparación del Entorno

Antes de comenzar, es necesario tener instalado el módulo `requests` de Python, ya que este se usará para realizar las peticiones HTTP a la API de AbuseIPDB.

```bash
pip install requests
```

Además, se debe contar con una clave API válida proporcionada por AbuseIPDB.

---

## 3. Estructura Básica del Código

### a) Importar la librería necesaria

Primero se importa el módulo `requests` para poder realizar las peticiones a la API.

```python
import requests
```

### b) Definir la URL de la API y la clave API

Se establece la URL de la API de AbuseIPDB y se define la variable `api_key` con la clave proporcionada:

```python
url = 'https://api.abuseipdb.com/api/v2/check/'
api_key = '523f2f2a30ac7df2daa6da8c6022737033addd66345f081896614d638969047ce9a6746ae888d9de'
```

---

## 4. Creación de la Lista de IPs

Se define una lista llamada `lista_ips` que contiene múltiples direcciones IP.  
Esta lista es la base sobre la que se realizará la iteración para consultar cada IP en la API.

```python
lista_ips = [
    "178.217.72.50", "175.100.33.246", "91.196.152.124", "161.35.230.46",
    "31.173.4.198", "60.37.152.45", "83.198.11.205", "85.72.53.103",
    "165.232.141.44", "180.104.103.146", "66.175.44.39", "220.134.92.45",
    "114.30.180.58", "92.63.197.210", "177.182.181.8", "42.63.224.248",
    "118.123.116.93"
]
```

---

## 5. Procesamiento de Cada IP con un Bucle for

### a) Inicio del bucle

Se utiliza un bucle `for` para iterar sobre cada dirección IP en la lista:

```python
for cada_ip in lista_ips:
```

Dentro de este bucle se realizan todos los pasos necesarios para procesar cada IP.

### b) Configuración de los Parámetros de la Consulta

#### i. Crear el diccionario `informacion`

Este diccionario contiene los parámetros que se enviarán a la API.

- `"ipAddress"`: Se asigna la IP actual del bucle.
    
- `"maxAgeInDays"`: Se establece el rango de tiempo (en días) sobre el cual se desean obtener los reportes (en este caso, 90 días).
    

```python
    informacion = {
        "ipAddress": cada_ip,
        "maxAgeInDays": "90"
    }
```

#### ii. Crear el diccionario `api`

Aquí se define el encabezado (headers) de la petición:

- `"key"`: Se incluye la clave API.
    
- `"Accept": "application/json"`: Se indica que se espera recibir la respuesta en formato JSON.
    

```python
    api = {
        "key": api_key,
        "Accept": "application/json"
    }
```

### c) Realizar la Petición a la API

Se utiliza `requests.get` para enviar una solicitud GET a la URL de la API, pasando tanto los encabezados como los parámetros definidos.

```python
    respuesta = requests.get(url, headers=api, params=informacion)
```

### d) Procesar la Respuesta

1. **Convertir la respuesta a JSON:**  
    Se utiliza el método `.json()` para transformar la respuesta en un diccionario de Python.
    
    ```python
     respuesta_json = respuesta.json()
    ```
    
2. **Extraer los datos de interés:**  
    Se extrae el campo `"ipAddress"` para identificar la IP y el campo `"totalReports"` para saber el número de reportes asociados a esa IP.
    
    ```python
     ip = respuesta_json['data']['ipAddress']
     reportes = respuesta_json['data']['totalReports']
    ```
    

---

## 6. Imprimir y Filtrar la Información

### a) Impresión Simple de Resultados

En un primer momento, se puede imprimir la IP y el número de reportes sin aplicar ningún filtro:

```python
    print(f"En la IP {ip} tenemos {reportes} reportes")
```

Al ejecutar el script, se obtiene un listado completo con la información de todas las IPs.

### b) Filtrado por Umbral de Reportes

Para hacerlo más útil, se decide imprimir únicamente aquellas IPs que tienen un número de reportes mayor a un valor específico (por ejemplo, más de 50).

Se utiliza una estructura condicional `if` para comprobar si el número de reportes es mayor a 50. Si se cumple, se imprime un mensaje personalizado:

```python
    if reportes > 50:
        print(f"La IP {ip} tiene mas de 50 reportes, tiene {reportes}")
```

Este filtrado permite enfocarse solo en aquellas IPs que presentan un comportamiento potencialmente malicioso, ya que cuentan con muchos reportes.

---

## 7. Ejecución del Script y Resultados

Al ejecutar el script (por ejemplo, con el comando `python abuseip.py` en la terminal), se observa lo siguiente:

- Se realizan las peticiones a la API para cada una de las IPs en la lista.
    
- Se muestran únicamente las IPs que cumplen la condición (más de 50 reportes).  
    Por ejemplo, se obtiene algo como:
    

```
La IP 178.217.72.50 tiene mas de 50 reportes, tiene 5734
La IP 91.196.152.124 tiene mas de 50 reportes, tiene 1833
La IP 161.35.230.46 tiene mas de 50 reportes, tiene 578
La IP 180.104.103.146 tiene mas de 50 reportes, tiene 1585
La IP 220.134.92.45 tiene mas de 50 reportes, tiene 1056
La IP 114.30.180.58 tiene mas de 50 reportes, tiene 1603
La IP 92.63.197.210 tiene mas de 50 reportes, tiene 15970
La IP 177.182.181.8 tiene mas de 50 reportes, tiene 9320
La IP 118.123.116.93 tiene mas de 50 reportes, tiene 1045
```

Las IPs con reportes inferiores al umbral no se muestran, lo cual facilita la identificación de aquellas que presentan un mayor riesgo.

---

## 8. Ideas de Mejora para el Futuro

El tutorial menciona algunas mejoras y posibles ampliaciones para este código:

- **Lectura desde un archivo:**  
    En lugar de definir las IPs directamente en el código, se podría leer cada línea de un archivo `.txt` donde se tengan listadas las IPs.
    
- **Volcado de información en un archivo:**  
    En lugar de imprimir la salida en la terminal, se podría escribir la información filtrada en un archivo de texto, lo que facilita el análisis posterior o la integración con otros sistemas.
    

---

## 9. Conclusión

Este ejemplo demuestra cómo se puede:

- Utilizar Python para interactuar con una API (en este caso, AbuseIPDB).
    
- Procesar y filtrar datos de forma dinámica utilizando bucles y condiciones.
    
- Adaptar y mejorar el código de forma progresiva (primero mostrando toda la información, luego filtrándola según criterios de interés).
    

Cada paso del proceso se ha realizado de forma secuencial:

1. Configuración inicial (importación y definición de variables).
    
2. Creación de una lista de IPs.
    
3. Iteración sobre cada IP y realización de la petición a la API.
    
4. Conversión y filtrado de la respuesta.
    
5. Impresión o volcado de la información según las condiciones deseadas.
    

Este enfoque modular y progresivo es muy útil en la ciberseguridad, ya que permite analizar grandes volúmenes de datos de forma automática, identificar posibles amenazas y, posteriormente, escalar la solución integrándola con otros sistemas o procesos de análisis.

---
## Código Completo:

````python
import requests

  

url = 'https://api.abuseipdb.com/api/v2/check/'

api_key = '523f2f2a30ac7df2daa6da8c6022737033addd66345f081896614d638969047ce9a6746ae888d9de'

  

lista_ips = [

    "178.217.72.50", "175.100.33.246", "91.196.152.124", "161.35.230.46",

    "31.173.4.198", "60.37.152.45", "83.198.11.205", "85.72.53.103",

    "165.232.141.44", "180.104.103.146", "66.175.44.39", "220.134.92.45",

    "114.30.180.58", "92.63.197.210", "177.182.181.8", "42.63.224.248",

    "118.123.116.93"

]

  

for cada_ip in lista_ips:

    informacion = {

  

    "ipAddress": cada_ip,

    "maxAgeInDays":"90"

    }

  

    api = {

  

    "key":api_key,

    "Accept": "application/json"

    }

  

    respuesta = requests.get(url, headers=api, params=informacion)

  

    respuesta_json = respuesta.json()

    #print(respuesta_json)

  

    ip = respuesta_json['data']['ipAddress']

    reportes = respuesta_json['data']['totalReports']

  

    #print(f"En la IP {ip} tenemos {reportes} reportes")

    if reportes > 5:

        print(f"La IP {ip} tiene mas de 5 reportes, tiene {reportes}")
`````

