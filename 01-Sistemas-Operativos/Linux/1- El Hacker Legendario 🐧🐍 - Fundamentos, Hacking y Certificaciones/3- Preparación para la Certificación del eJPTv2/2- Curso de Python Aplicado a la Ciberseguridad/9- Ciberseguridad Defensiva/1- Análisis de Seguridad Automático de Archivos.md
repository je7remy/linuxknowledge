
## 1. Contextualización y Objetivo

El contenido expuesto muestra cómo utilizar Python para interactuar con la API de VirusTotal, una herramienta online que permite analizar archivos, direcciones IP, hashes, etc. VirusTotal utiliza múltiples antivirus para determinar si un archivo es potencialmente malicioso o inofensivo. El proceso descrito permite automatizar el análisis de archivos utilizando Python, lo que es especialmente útil en entornos donde se necesita revisar gran cantidad de archivos, como en un SOC (Security Operation Center).

---

## 2. Preparación del Entorno y Registro en VirusTotal

### a. Registro y Obtención de la API Key

- **Registro en VirusTotal:** Para utilizar la API es necesario tener una cuenta en VirusTotal. Una vez registrado, se accede a una sección de la web donde se muestra la API key (clave privada) que se utilizará para autenticar las peticiones desde Python.
    
- **Limitaciones:** La versión gratuita de VirusTotal permite realizar hasta cuatro peticiones por minuto. En entornos empresariales o con mayor volumen de análisis, se puede contratar una versión premium para aumentar este límite.
    

### b. Instalación de Librerías Necesarias

Se requiere instalar dos librerías de Python que facilitan la interacción con la API de VirusTotal:

1. **VirusTotal-Python**  
    Se instala utilizando:
    
    ```bash
    pip install VirusTotal-Python
    ```
    
2. **VirusTotal-API**  
    Se instala utilizando:
    
    ```bash
    pip install VirusTotal-API
    ```
    

Una vez instaladas, se recomienda cerrar y volver a abrir Visual Studio Code (o el entorno de desarrollo que se esté usando) para asegurarse de que los cambios se carguen correctamente.

---

## 3. Creación del Archivo a Analizar

Para la demostración, se crea un archivo de texto (por ejemplo, `test.txt` o `favoritos.txt` o `text.txt`) que contiene un mensaje simple (por ejemplo, "hola" o cualquier otro contenido que se considere seguro). Este archivo servirá para realizar la prueba de análisis con la API.

---

## 4. Desarrollo del Script en Python

El código se compone de varias secciones, las cuales se detallan a continuación:

### a. Importación de Librerías

```python
from hashlib import md5
from virus_total_apis import PublicApi
```

- **`hashlib` y la función `md5`:**  
    Se importa la función `md5` que permite calcular el hash MD5 de un archivo. El hash es una representación única del contenido del archivo y es utilizado por VirusTotal para identificar el archivo.
    
- **`virus_total_apis`:**  
    Se importa la clase `PublicApi` que contiene los métodos necesarios para interactuar con la API de VirusTotal.
    

### b. Configuración de la API Key y Creación del Objeto API

```python
API_KEY = "48554f978574de487073d93235579fd37a2470a2e378afe1d4e5764ea716535b"
api = PublicApi(API_KEY)
```

- **Definición de `API_KEY`:**  
    Se asigna a la variable `API_KEY` la clave privada obtenida al registrarse en VirusTotal.
    
- **Inicialización del Objeto API:**  
    Se crea un objeto llamado `api` utilizando la clase `PublicApi` y pasando la API key. Este objeto se usará para realizar peticiones a la API, como obtener reportes sobre archivos.
    

### c. Apertura y Lectura del Archivo

El siguiente bloque de código abre un archivo en modo binario (lectura en binario `"rb"`) para asegurarse de que se pueda leer correctamente su contenido sin problemas de codificación:

```python
with open("favoritos.txt", "rb") as file:
    hash_archivo = md5(file.read()).hexdigest()
```

- **Explicación del código:**
    
    - Se usa la sentencia `with` para abrir el archivo llamado `"favoritos.txt"` de manera segura, lo que garantiza que el archivo se cerrará automáticamente una vez que se termine de usar.
        
    - Se lee el contenido completo del archivo con `file.read()`.
        
    - Se calcula el hash MD5 del contenido utilizando `md5(...)` y se convierte a formato hexadecimal con el método `.hexdigest()`.
        
    - El resultado se almacena en la variable `hash_archivo`, que contendrá una cadena de caracteres representando el hash único del archivo.
        

### d. Obtención del Reporte del Archivo con la API

```python
respuesta = api.get_file_report(hash_archivo)
```

- **Uso del método `get_file_report`:**  
    Se llama al método `get_file_report` del objeto `api` pasándole el hash del archivo (`hash_archivo`).
    
- **Resultado:**  
    La respuesta obtenida se guarda en la variable `respuesta`. Esta respuesta es un diccionario que contiene toda la información devuelta por VirusTotal, incluyendo datos sobre la cantidad de antivirus que han marcado el archivo como malicioso, el código de respuesta y otros detalles.
    

### e. Visualización del Resultado

Existen varias variantes en los ejemplos presentados, que muestran diferentes formas de trabajar con la respuesta:

1. **Imprimir el diccionario completo:**
    
    ```python
    print(respuesta)
    ```
    
    - Esto mostrará en la consola toda la información devuelta, organizada en un diccionario. Es útil para entender la estructura de la respuesta.
        
2. **Filtrar y mostrar únicamente el número de detecciones (positives):**
    
    ```python
    print(respuesta['results']['positives'])
    ```
    
    - En este ejemplo, se accede a la clave `results` del diccionario y, dentro de ella, se extrae el valor de la clave `positives`, que indica el número de antivirus que han detectado el archivo como malicioso.
        
3. **Almacenar el número de reportes en una variable y mostrarlo de forma formateada:**
    
    ```python
    reportes = respuesta['results']['positives']
    print("El número de antivirus que han detectado como malicioso el archivo es: ", reportes)
    ```
    
    - Aquí se guarda el valor de `positives` en la variable `reportes`.
        
    - Luego se imprime un mensaje informativo junto con el número obtenido.
        

---

## 5. Consideraciones Adicionales y Aplicaciones Prácticas

### Automatización del Análisis

- **Automatización:**  
    Con este enfoque es posible automatizar el análisis de múltiples archivos. Se podría, por ejemplo, utilizar el módulo `os` para recorrer un directorio completo, calcular el hash de cada archivo y enviar cada uno a VirusTotal para su análisis.
    
- **Uso en Entornos Empresariales:**  
    En empresas donde se maneja gran cantidad de datos, este proceso automatizado es muy útil para detectar archivos maliciosos sin tener que hacerlo manualmente, lo que mejora la capacidad de respuesta ante posibles amenazas.
    

### Limitaciones de la Versión Gratuita

- **Límite de Peticiones:**  
    La versión gratuita de VirusTotal impone un límite de cuatro peticiones por minuto. Si se necesita analizar muchos archivos en un corto periodo de tiempo, se debería considerar la versión premium o implementar una pausa en el código (por ejemplo, utilizando `time.sleep()`) para respetar el límite de peticiones.
    

---

## 6. Resumen del Flujo Completo del Código

1. **Preparación:**
    
    - Registrarse en VirusTotal y obtener la API key.
        
    - Instalar las librerías necesarias (`VirusTotal-Python` y `VirusTotal-API`).
        
2. **Configuración:**
    
    - Importar las librerías `hashlib` y la clase `PublicApi` desde `virus_total_apis`.
        
    - Definir la API key y crear el objeto API.
        
3. **Procesamiento del Archivo:**
    
    - Abrir el archivo en modo binario.
        
    - Calcular el hash MD5 del archivo.
        
4. **Interacción con la API:**
    
    - Enviar el hash del archivo a VirusTotal mediante el método `get_file_report`.
        
    - Recibir un diccionario con el reporte de VirusTotal.
        
5. **Visualización y Filtrado:**
    
    - Imprimir el reporte completo o extraer únicamente el número de antivirus que marcaron el archivo como malicioso.
        
6. **Aplicaciones Prácticas:**
    
    - Automatización del análisis de seguridad de múltiples archivos.
        
    - Implementación en entornos corporativos para mejorar la seguridad informática.
        

---

## Código Completo:

````python
from hashlib import md5

from virus_total_apis import PublicApi

  

API_KEY = "48554f978574de487073d93235579fd37a2470a2e378afe1d4e5764ea716535b"

api = PublicApi(API_KEY)

  

with open("text.txt", "rb") as file:

    hash_archivo = md5(file.read()).hexdigest()

  

respuesta = api.get_file_report(hash_archivo)

  

reportes = respuesta['results']['positives']

  

print("El numero de antivirus que han detectado como malicioso el archivo es: ", reportes)
`````

