¡Hola amigos! Bienvenidos una vez más a este curso de Python aplicado a la ciberseguridad. Hoy vamos a desarrollar paso a paso y de manera superdetallada cómo hemos trabajado con un código que consulta reportes de direcciones IP usando la API de AbuseIPDB. Veremos dos tareas principales: **guardar reportes de IPs en un archivo .txt** y **leer IPs desde un archivo .txt para analizarlas**. Explicaremos cada parte de forma coherente, enfatizando la evolución del código en cada etapa. ¡Vamos a ello!

---

## **Parte 1: Guardar reportes en un archivo .txt**

### **Objetivo**
Queremos tomar una lista de direcciones IP, consultar cuántos reportes tienen en la API de AbuseIPDB (limitando los datos a los últimos 90 días) y guardar en un archivo `reportes.txt` solo aquellas IPs que tengan más de 1000 reportes. Vamos a desglosar cómo llegamos al código final y cómo evolucionó.

### **Paso a paso inicial: Código base**
Supongamos que al inicio teníamos un código básico que solo imprimía los reportes en la consola. Este sería el punto de partida:

```python
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
        "maxAgeInDays": "90"
    }
    api = {
        "key": api_key,
        "Accept": "application/json"
    }
    respuesta = requests.get(url, headers=api, params=informacion)
    respuesta_json = respuesta.json()
    ip = respuesta_json['data']['ipAddress']
    reportes = respuesta_json['data']['totalReports']
    print(f"En la IP {ip} tenemos {reportes} reportes")
```

#### **Explicación del código base**
1. **Importamos `requests`**: Esta biblioteca nos permite hacer solicitudes HTTP a la API.
2. **Definimos la URL y la API Key**: La URL es el endpoint de AbuseIPDB para verificar IPs, y la clave es necesaria para autenticarnos.
3. **Lista de IPs**: Una lista estática (`lista_ips`) con las IPs que queremos analizar.
4. **Bucle `for`**: Recorre cada IP en la lista.
5. **Parámetros y headers**: 
   - `informacion` contiene la IP y el límite de 90 días para los reportes.
   - `api` incluye la clave y el formato de respuesta (JSON).
6. **Solicitud a la API**: Usamos `requests.get()` para obtener los datos.
7. **Procesamos la respuesta**: Extraemos la IP y el número de reportes del JSON.
8. **Imprimimos**: Mostramos los resultados en la consola con `print()`.

Este código funciona bien para ver los reportes en pantalla, pero ahora queremos guardarlos en un archivo. Aquí comienza la evolución.

---

### **Evolución 1: Guardar en un archivo en lugar de imprimir**
Para guardar los reportes en un archivo `reportes.txt`, necesitamos abrir un archivo en modo escritura y reemplazar el `print()` por un método que escriba en él. Vamos a adaptar el código:

```python
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

with open('reportes.txt', 'w') as archivo_reporte:
    for cada_ip in lista_ips:
        informacion = {
            "ipAddress": cada_ip,
            "maxAgeInDays": "90"
        }
        api = {
            "key": api_key,
            "Accept": "application/json"
        }
        respuesta = requests.get(url, headers=api, params=informacion)
        respuesta_json = respuesta.json()
        ip = respuesta_json['data']['ipAddress']
        reportes = respuesta_json['data']['totalReports']
        archivo_reporte.write(f"La IP {ip} tiene {reportes} reportes")
```

#### **Cambios realizados**
1. **Abrimos un archivo**: Usamos `with open('reportes.txt', 'w') as archivo_reporte` para crear (o sobrescribir) el archivo `reportes.txt` en modo escritura (`'w'`). El `with` asegura que el archivo se cierre automáticamente al terminar.
2. **Movemos el bucle**: Colocamos el bucle `for` dentro del bloque `with` para que todas las operaciones se realicen mientras el archivo está abierto.
3. **Reemplazamos `print`**: Cambiamos `print()` por `archivo_reporte.write()`, que escribe la cadena en el archivo.

#### **Problema detectado**
Si ejecutamos este código, los reportes se escriben en el archivo, pero todo aparece en una sola línea, algo como:

```
La IP 178.217.72.50 tiene 5739 reportesLa IP 175.100.33.246 tiene 12 reportes...
```

Esto es difícil de leer. Necesitamos agregar saltos de línea.

---

### **Evolución 2: Añadir saltos de línea**
Ajustamos el código para que cada reporte esté en una línea separada añadiendo `\n`:

```python
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

with open('reportes.txt', 'w') as archivo_reporte:
    for cada_ip in lista_ips:
        informacion = {
            "ipAddress": cada_ip,
            "maxAgeInDays": "90"
        }
        api = {
            "key": api_key,
            "Accept": "application/json"
        }
        respuesta = requests.get(url, headers=api, params=informacion)
        respuesta_json = respuesta.json()
        ip = respuesta_json['data']['ipAddress']
        reportes = respuesta_json['data']['totalReports']
        archivo_reporte.write(f"La IP {ip} tiene {reportes} reportes\n")
```

#### **Cambio realizado**
- Añadimos `\n` al final de la cadena en `write()`. Esto inserta un salto de línea después de cada reporte.

#### **Resultado**
Ahora, el archivo `reportes.txt` se ve así:

```
La IP 178.217.72.50 tiene 5739 reportes
La IP 175.100.33.246 tiene 12 reportes
La IP 91.196.152.124 tiene 1833 reportes
...
```

Mucho más legible, ¿verdad?

---

### **Evolución 3: Filtrar IPs con más de 1000 reportes**
El objetivo es guardar solo las IPs con más de 1000 reportes. Añadimos una condición `if`:

```python
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

with open('reportes.txt', 'w') as archivo_reporte:
    for cada_ip in lista_ips:
        informacion = {
            "ipAddress": cada_ip,
            "maxAgeInDays": "90"
        }
        api = {
            "key": api_key,
            "Accept": "application/json"
        }
        respuesta = requests.get(url, headers=api, params=informacion)
        respuesta_json = respuesta.json()
        ip = respuesta_json['data']['ipAddress']
        reportes = respuesta_json['data']['totalReports']
        if reportes > 1000:
            archivo_reporte.write(f"La IP {ip} tiene mas de 1000 reportes, tiene {reportes}\n")
```

#### **Cambio realizado**
- Añadimos `if reportes > 1000` antes de escribir en el archivo. Solo las IPs con más de 1000 reportes se guardan.
- Ajustamos el mensaje para que sea más claro: `"La IP {ip} tiene mas de 1000 reportes, tiene {reportes}\n"`.

#### **Resultado final**
El archivo `reportes.txt` ahora contiene solo las IPs que cumplen el criterio, por ejemplo:

```
La IP 178.217.72.50 tiene mas de 1000 reportes, tiene 5739
La IP 91.196.152.124 tiene mas de 1000 reportes, tiene 1833
La IP 180.104.103.146 tiene mas de 1000 reportes, tiene 1585
La IP 220.134.92.45 tiene mas de 1000 reportes, tiene 1056
La IP 114.30.180.58 tiene mas de 1000 reportes, tiene 1603
La IP 92.63.197.210 tiene mas de 1000 reportes, tiene 15972
La IP 177.182.181.8 tiene mas de 1000 reportes, tiene 9326
La IP 118.123.116.93 tiene mas de 1000 reportes, tiene 1045
```

#### **Resumen de la evolución**
1. **Base**: Imprimíamos todo en consola con `print()`.
2. **Escritura**: Cambiamos a `write()` y añadimos manejo de archivos con `with open`.
3. **Formato**: Añadimos `\n` para saltos de línea.
4. **Filtro**: Incorporamos `if reportes > 1000` para guardar solo lo relevante.

¡Primera parte lista! Ahora, a leer IPs desde un archivo.

---

## **Parte 2: Leer IPs desde un archivo .txt y analizarlas**

### **Objetivo**
Queremos leer una lista de IPs desde un archivo `listado_ip.txt`, consultar sus reportes en la API y mostrar en la consola las que tengan más de 1000 reportes. Vamos a construir este código desde cero y detallar su evolución.

### **Preparación: Crear el archivo de entrada**
Primero, creamos un archivo `listado_ip.txt` con algunas IPs (pueden ser las mismas de antes). Por ejemplo:

```
178.217.72.50
175.100.33.246
91.196.152.124
161.35.230.46
31.173.4.198
```

Cada IP está en una línea separada.

---

### **Paso a paso inicial: Leer el archivo**
Empezamos con un código que lee las IPs y las analiza, similar al de la Parte 1, pero adaptado para leer desde un archivo:

```python
import requests

url = 'https://api.abuseipdb.com/api/v2/check/'
api_key = '523f2f2a30ac7df2daa6da8c6022737033addd66345f081896614d638969047ce9a6746ae888d9de'

lista_ips = []

with open('listado_ip.txt', 'r') as archivo_ips:
    for cada_ip in archivo_ips:
        lista_ips.append(cada_ip)

for cada_ip_lista in lista_ips:
    informacion = {
        "ipAddress": cada_ip_lista,
        "maxAgeInDays": "90"
    }
    api = {
        "key": api_key,
        "Accept": "application/json"
    }
    respuesta = requests.get(url, headers=api, params=informacion)
    respuesta_json = respuesta.json()
    ip = respuesta_json['data']['ipAddress']
    reportes = respuesta_json['data']['totalReports']
    print(f"La IP {ip} tiene {reportes} reportes")
```

#### **Explicación**
1. **Lista vacía**: Creamos `lista_ips = []` para almacenar las IPs que leeremos.
2. **Abrimos el archivo**: Usamos `with open('listado_ip.txt', 'r') as archivo_ips` en modo lectura (`'r'`).
3. **Leemos las líneas**: Iteramos sobre `archivo_ips` (cada línea es una IP) y las añadimos a `lista_ips` con `append()`.
4. **Analizamos**: Usamos un segundo bucle para consultar la API como en la Parte 1.
5. **Imprimimos**: Mostramos los resultados en la consola.

#### **Problema detectado**
Si ejecutamos esto, las IPs incluyen un salto de línea (`\n`) al final porque así se leen del archivo. Por ejemplo, `178.217.72.50\n`. Esto puede causar errores en la API o resultados inesperados.

---

### **Evolución 1: Limpiar las IPs con `strip()`**
Ajustamos el código para eliminar espacios y saltos de línea:

```python
import requests

url = 'https://api.abuseipdb.com/api/v2/check/'
api_key = '523f2f2a30ac7df2daa6da8c6022737033addd66345f081896614d638969047ce9a6746ae888d9de'

lista_ips = []

with open('listado_ip.txt', 'r') as archivo_ips:
    for cada_ip in archivo_ips:
        lista_ips.append(cada_ip.strip())

for cada_ip_lista in lista_ips:
    informacion = {
        "ipAddress": cada_ip_lista,
        "maxAgeInDays": "90"
    }
    api = {
        "key": api_key,
        "Accept": "application/json"
    }
    respuesta = requests.get(url, headers=api, params=informacion)
    respuesta_json = respuesta.json()
    ip = respuesta_json['data']['ipAddress']
    reportes = respuesta_json['data']['totalReports']
    print(f"La IP {ip} tiene {reportes} reportes")
```

#### **Cambio realizado**
- Añadimos `.strip()` a `cada_ip` para eliminar espacios en blanco y saltos de línea antes de añadir la IP a la lista.

#### **Resultado**
Ahora las IPs se leen correctamente (ej. `178.217.72.50` sin `\n`) y la API las procesa sin problemas.

---

### **Evolución 2: Filtrar IPs con más de 1000 reportes**
Queremos mostrar solo las IPs con más de 1000 reportes:

```python
import requests

url = 'https://api.abuseipdb.com/api/v2/check/'
api_key = '523f2f2a30ac7df2daa6da8c6022737033addd66345f081896614d638969047ce9a6746ae888d9de'

lista_ips = []

with open('listado_ip.txt', 'r') as archivo_ips:
    for cada_ip in archivo_ips:
        lista_ips.append(cada_ip.strip())

for cada_ip_lista in lista_ips:
    informacion = {
        "ipAddress": cada_ip_lista,
        "maxAgeInDays": "90"
    }
    api = {
        "key": api_key,
        "Accept": "application/json"
    }
    respuesta = requests.get(url, headers=api, params=informacion)
    respuesta_json = respuesta.json()
    ip = respuesta_json['data']['ipAddress']
    reportes = respuesta_json['data']['totalReports']
    if reportes > 1000:
        print(f"La IP {ip} tiene mas de 1000 reportes, tiene {reportes}")
```

#### **Cambio realizado**
- Añadimos `if reportes > 1000` antes del `print()` para filtrar las IPs.
- Ajustamos el mensaje para reflejar el criterio.

#### **Resultado**
La salida en consola muestra solo las IPs relevantes, por ejemplo:

```
La IP 178.217.72.50 tiene mas de 1000 reportes, tiene 5739
La IP 91.196.152.124 tiene mas de 1000 reportes, tiene 1833
```

#### **Nota adicional**
No necesitamos `\n` al final del `print()` porque `print()` ya añade un salto de línea por defecto.

---

### **Resumen de la evolución**
1. **Base**: Leíamos IPs sin limpiar y mostrábamos todos los reportes.
2. **Limpieza**: Añadimos `strip()` para procesar las IPs correctamente.
3. **Filtro**: Incorporamos `if reportes > 1000` para mostrar solo lo relevante.

---

## **Conclusión**
Hemos visto dos procesos clave:
- **Guardar reportes**: Evolucionamos desde imprimir en consola hasta guardar en `reportes.txt` con formato y filtro.
- **Leer IPs**: Pasamos de una lista estática a leer desde `listado_ip.txt`, limpiando datos y filtrando resultados.

Estos ejemplos muestran cómo Python puede automatizar tareas de ciberseguridad, como analizar cientos de IPs de forma eficiente. 