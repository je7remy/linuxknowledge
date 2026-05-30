---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, python, pentesting]
actualizado: 2026-05-28
---

# Instalación de Módulos Externos

---

#Python #pip #pip3 #Python3 #DesarrolloPython #Programación #PaquetesPython #PyPI #GestorDeDependencias #DevOps #Software #Código

---
# **Guía de Comandos Básicos de `pip3`**

`pip3` es una herramienta de línea de comandos utilizada para instalar y gestionar paquetes de software escritos en Python 3. Es la versión específica para Python 3 del instalador de paquetes `pip`.

A continuación, se presentan algunos de los comandos básicos más útiles:

## **1. Instalar un paquete**

```bash
pip3 install nombre_paquete
```

Instala el paquete especificado desde el Índice de Paquetes de Python (PyPI).

## **2. Desinstalar un paquete**

```bash
pip3 uninstall nombre_paquete
```

Desinstala el paquete especificado.

## **3. Actualizar un paquete**

```bash
pip3 install --upgrade nombre_paquete
```

Actualiza el paquete a la última versión disponible.

## **4. Listar paquetes instalados**

```bash
pip3 list
```

Muestra una lista de todos los paquetes instalados en el entorno actual.

## **5. Mostrar información sobre un paquete**

```bash
pip3 show nombre_paquete
```

Muestra detalles del paquete, incluyendo su versión, autor y dependencias.

## **6. Guardar los paquetes instalados en un archivo de requisitos**

```bash
pip3 freeze > requirements.txt
```

Genera un archivo `requirements.txt` con una lista de todos los paquetes y sus versiones actuales en el entorno.

## **7. Instalar paquetes desde un archivo de requisitos**

```bash
pip3 install -r requirements.txt
```

Instala todos los paquetes listados en `requirements.txt`.

## **8. Buscar un paquete**

```bash
pip3 search nombre_paquete
```

Busca paquetes en PyPI que coincidan con el nombre especificado.

---

`pip3` es una herramienta poderosa y esencial para gestionar dependencias en proyectos de Python, especialmente cuando se trabaja con Python 3.


---

# **Guía para Ejecutar un Archivo Python en la Terminal**

### **1. Asegúrate de tener Python instalado**

Para verificar si Python está instalado en tu sistema, abre una terminal y ejecuta uno de los siguientes comandos:

```bash
python3 --version
```

o

```bash
python --version
```

Dependiendo de la configuración de tu sistema, uno de estos comandos mostrará la versión de Python instalada.

---

### **2. Navega al directorio donde está el archivo**

Usa el comando `cd` para cambiar de directorio en la terminal hasta llegar a la ubicación donde se encuentra el archivo Python que deseas ejecutar.

```bash
cd ruta/al/directorio
```

---

### **3. Ejecuta el archivo Python**

Una vez dentro del directorio correcto, puedes ejecutar el archivo con uno de los siguientes comandos:

```bash
python3 nombre_del_archivo.py
```

o

```bash
python nombre_del_archivo.py
```

Asegúrate de reemplazar `nombre_del_archivo.py` con el nombre real de tu archivo.

---

## **📌 Ejemplo Completo**

Supongamos que tienes un archivo llamado `mi_script.py` dentro de un directorio llamado `proyecto`.

1. **Abre una terminal.**
2. **Navega al directorio `proyecto`:**
    
    ```bash
    cd ruta/al/directorio/proyecto
    ```
    
3. **Ejecuta el archivo `mi_script.py`:**
    
    ```bash
    python3 mi_script.py
    ```
    
    o
    
    ```bash
    python mi_script.py
    ```
    

---

### **⚠️ Nota Adicional**

Si el archivo Python que deseas ejecutar requiere ciertos paquetes que aún no has instalado, puedes instalarlos con `pip3` antes de ejecutarlo.

```bash
pip3 install nombre_del_paquete
```

Reemplaza `nombre_del_paquete` con el nombre real del paquete necesario.

---

💡 **Consejo:** Si usas entornos virtuales (`venv`), asegúrate de activarlo antes de ejecutar el script. 🚀

### **Código en Python:**

```python
import requests

url = "https://www.google.com"  # Definimos la URL de Google

response = requests.get(url)  # Realizamos una petición HTTP GET a la URL

if response.status_code == 200:
    # Si la respuesta es exitosa (código 200), imprimimos el estado de la respuesta
    print(f"Estado de la respuesta: {response.status_code}")
else:
    # Si la solicitud falla, imprimimos un mensaje de error junto con el código de estado
    print("Error en la solicitud", response.status_code)
```

---

### **Explicación paso a paso:**

4. **Importamos la biblioteca `requests`**
    
    ```python
    import requests
    ```
    
    - La librería `requests` nos permite realizar peticiones HTTP de manera sencilla en Python.
    - Si no la tienes instalada, puedes hacerlo con:
        
        ```bash
        pip install requests
        ```
        
5. **Definimos la URL a la que queremos hacer la petición**
    
    ```python
    url = "https://www.google.com"
    ```
    
    - En este caso, usamos la URL de Google.
6. **Hacemos la solicitud GET**
    
    ```python
    response = requests.get(url)
    ```
    
    - `requests.get(url)`: Envía una solicitud HTTP GET a la URL especificada.
    - La respuesta de la solicitud se almacena en la variable `response`.
7. **Verificamos si la solicitud fue exitosa**
    
    ```python
    if response.status_code == 200:
    ```
    
    - `response.status_code`: Devuelve el código de estado HTTP de la respuesta.
    - `200` indica que la solicitud fue exitosa.
8. **Si la solicitud fue exitosa (`200`), imprimimos el código de estado**
    
    ```python
    print(f"Estado de la respuesta: {response.status_code}")
    ```
    
    - Se usa una f-string (`f""`) para mostrar el código de estado en un mensaje claro.
9. **Si la solicitud falla, mostramos un mensaje de error con el código de estado**
    
    ```python
    else:
        print("Error en la solicitud", response.status_code)
    ```
    
    - Si el código de estado no es `200`, indicamos que hubo un error y mostramos el código recibido.
    - Por ejemplo, un código `404` significa que la página no se encontró, y un `500` indica un error interno del servidor.

---

### **Ejemplo de salida esperada:**

Si todo está correcto y la solicitud se realiza con éxito, el programa imprimirá:

```
Estado de la respuesta: 200
```

Si hay un error (por ejemplo, la URL no está disponible), podría mostrar:

```
Error en la solicitud 404
```

💡 _Nota:_

- Este código requiere conexión a Internet para ejecutarse correctamente.
- Algunos sitios pueden bloquear solicitudes automáticas o requerir encabezados específicos.

---

## Navegación

- ⬆️ Carpeta: [[_2- Introducción a los Módulos y uso de PIP|2- Introducción a los Módulos y uso de PIP]]
- ⬅️ Anterior: [[1- Introducción a los Módulos]]
- ➡️ Siguiente: [[3- Creación y Gestión de Entornos Virtuales]]
