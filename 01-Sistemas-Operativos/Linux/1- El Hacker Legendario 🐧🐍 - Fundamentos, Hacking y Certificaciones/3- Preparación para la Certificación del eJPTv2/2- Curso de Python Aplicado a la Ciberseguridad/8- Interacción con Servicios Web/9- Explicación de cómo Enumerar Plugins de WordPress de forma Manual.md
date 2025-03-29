# Creación de un Script en Python para Enumerar Plugins de WordPress: Paso a Paso

En este tutorial, vamos a desarrollar paso a paso un script en Python diseñado para enumerar plugins instalados en un sitio WordPress, utilizando la máquina vulnerable "Azucar" de Docker Labs. Este proceso es útil en el ámbito de la ciberseguridad para identificar plugins que podrían ser vulnerables y, por ende, explotables. A continuación, detallaremos todo el proceso desde el inicio hasta el final, con explicaciones claras y formato Markdown para facilitar la comprensión.

---

## Introducción al Proyecto

El objetivo es crear una herramienta en Python que automatice la enumeración de plugins en un sitio WordPress. En el contexto de la ciberseguridad, esta técnica es valiosa porque muchos plugins obsoletos o con vulnerabilidades conocidas pueden ser puntos de entrada para ataques. Usaremos:

- **Kali Linux**: Como sistema operativo base.
- **Docker Labs**: Plataforma que proporciona máquinas vulnerables para prácticas de ciberseguridad.
- **Máquina "Azucar"**: Una máquina específica de Docker Labs con un WordPress que incluye un plugin vulnerable ("site-editor").
- **Python**: Con la librería `requests` para realizar peticiones HTTP.

---

## Paso 1: Descarga y Despliegue de la Máquina "Azucar"

### 1.1 Descarga de la Máquina
1. **Acceder a Docker Labs**:
   - Visita el sitio oficial de [Docker Labs](https://dockerlabs.es/).
   - Busca la máquina llamada "Azucar" y haz clic en "Descargar".
   - Esto abrirá un enlace en Mega (o similar). Elimina cualquier sufijo como ".LOAD" si aparece en el nombre del archivo.

2. **Tamaño del Archivo**:
   - La máquina ocupa aproximadamente 200 MB, por lo que es relativamente ligera.

3. **Descarga**:
   - Descarga el archivo ZIP al escritorio de tu Kali Linux.

### 1.2 Descompresión
1. **Abrir la Terminal**:
   - Abre una terminal en Kali Linux.

2. **Organizar el Escritorio**:
   - Para mantener el orden, elimina cualquier archivo innecesario del escritorio:
     ```bash
     sudo rm -r /home/user/Desktop/*
     ```
   - Nota: Asegúrate de que no haya archivos importantes antes de ejecutar este comando.

3. **Extraer el ZIP**:
   - Navega al directorio del escritorio:
     ```bash
     cd /home/user/Desktop
     ```
   - Extrae el archivo ZIP descargado:
     ```bash
     unzip azucar.zip
     ```
   - Esto generará una carpeta con los archivos necesarios, incluyendo `azucar.tar` y el script `autodeploy.sh`.

### 1.3 Desplegar la Máquina
1. **Ejecutar el Script de Despliegue**:
   - En la terminal, ejecuta:
     ```bash
     sudo bash autodeploy.sh azucar.tar
     ```
   - Este comando despliega la máquina vulnerable usando Docker.

2. **Obtener la IP**:
   - Una vez desplegada, la terminal mostrará la IP asignada a la máquina (por ejemplo, `172.17.0.2`). Anótala, ya que la usaremos para acceder al WordPress.

---

## Paso 2: Configuración Inicial del Entorno

### 2.1 Acceso al WordPress
1. **Probar la IP en el Navegador**:
   - Abre un navegador (como Firefox) y escribe:
     ```
     http://172.17.0.2/
     ```
   - Verás un sitio WordPress. Puede parecer mal configurado o "raro", pero esto no afecta nuestro propósito.

2. **Identificar el Dominio**:
   - Inspecciona la página (Ctrl+U para ver el código fuente).
   - Busca referencias a un dominio, como `azucar.dl`. Este dominio está asociado a la máquina y lo usaremos para evitar problemas con las peticiones HTTP.

### 2.2 Configurar el Archivo `/etc/hosts`
1. **Editar el Archivo**:
   - En la terminal, abre el archivo `/etc/hosts` con un editor como `nano`:
     ```bash
     sudo nano /etc/hosts
     ```

2. **Añadir el Dominio**:
   - Agrega una línea con la IP de la máquina y el dominio `azucar.dl`:
     ```
     172.17.0.2  azucar.dl
     ```
   - Guarda el archivo (Ctrl+O, Enter, Ctrl+X).

3. **Verificar la Configuración**:
   - Regresa al navegador y accede a:
     ```
     http://azucar.dl/
     ```
   - Ahora las imágenes y otros elementos deberían cargarse correctamente, confirmando que el dominio está bien asociado.

---

## Paso 3: Entendiendo la Enumeración de Plugins en WordPress

### 3.1 Ruta de los Plugins
- En WordPress, los plugins se alojan en la carpeta `wp-content/plugins/`.
- Accede a:
  ```
  http://azucar.dl/wp-content/plugins/
  ```
- Verás una página en blanco, lo cual es normal porque WordPress no lista los plugins directamente.

### 3.2 Archivos `readme.txt`
- Cada plugin suele incluir un archivo `readme.txt` en su directorio.
- Si el plugin existe, puedes acceder a este archivo con la ruta:
  ```
  http://azucar.dl/wp-content/plugins/<nombre-plugin>/readme.txt
  ```
- Ejemplos:
  - **Plugin inexistente**: `http://azucar.dl/wp-content/plugins/fdf/readme.txt` → Error 404.
  - **Plugin existente**: `http://azucar.dl/wp-content/plugins/site-editor/readme.txt` → Muestra el contenido del archivo, incluyendo la versión del plugin (por ejemplo, "Stable tag: 1.1").

### 3.3 Objetivo
- Automatizaremos este proceso con Python para probar una lista de plugins y determinar cuáles están instalados en el WordPress objetivo.

---

## Paso 4: Desarrollo del Script en Python

### 4.1 Preparación del Entorno de Desarrollo
1. **Abrir Visual Studio Code**:
   - En Kali Linux, abre Visual Studio Code (o tu editor preferido):
     ```bash
     code .
     ```

2. **Crear un Nuevo Archivo**:
   - Crea un archivo llamado `enum_plugins.py`.

### 4.2 Código Inicial
Comenzaremos con un script básico que prueba una lista de plugins.

#### Código:
```python
import requests

# Lista de plugins a comprobar
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
    "site-editor"
    # Puedes añadir más plugins aquí...
)

# URL base
base_url = "http://172.17.0.2/wp-content/plugins/"

def check_plugin(plugin):
    url = f"{base_url}{plugin}/readme.txt"
    response = requests.get(url)
    if response.status_code == 200:
        print(f"[+] Plugin encontrado: {plugin}")
    else:
        pass

# Iterar sobre cada plugin
for plugin in plugins:
    check_plugin(plugin)
```

#### Explicación:
- **Librería `requests`**: Permite hacer peticiones HTTP.
- **Tupla `plugins`**: Contiene nombres de plugins comunes. Para este ejemplo, usamos una lista corta, pero idealmente debería incluir cientos o miles de plugins (puedes obtener listas de internet o bases de datos como la de WPScan).
- **URL Base**: La ruta común donde se alojan los plugins.
- **Función `check_plugin`**: Construye la URL completa y verifica si el `readme.txt` existe (código 200).
- **Bucle**: Itera sobre cada plugin y ejecuta la función.

### 4.3 Ejecución Inicial
1. **Guardar el Archivo**:
   - Guarda el script como `enum_plugins.py`.

2. **Ejecutar**:
   - En la terminal:
     ```bash
     python3 enum_plugins.py
     ```
   - Resultado esperado (si "site-editor" está instalado):
     ```
     [+] Plugin encontrado: site-editor
     ```

### 4.4 Mejora del Script
El script inicial solo indica qué plugins existen, pero no proporciona la URL del `readme.txt` para inspeccionar manualmente. Vamos a mejorarlo.

#### Código Mejorado:
```python
import requests

# Lista de plugins a comprobar
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
    "site-editor"
    # Puedes añadir más plugins aquí...
)

# URL base
base_url = "http://172.17.0.2/wp-content/plugins/"

def check_plugin(plugin):
    url = f"{base_url}{plugin}/readme.txt"
    response = requests.get(url)
    if response.status_code == 200:
        print(f"[+] Plugin encontrado: {plugin}")
        print(f"Debes insertar esta url: {url}")
    else:
        pass

# Iterar sobre cada plugin
for plugin in plugins:
    check_plugin(plugin)
```

#### Cambios:
- **Mensaje Adicional**: Si se encuentra un plugin, se imprime la URL completa del `readme.txt`.

3. **Ejecutar de Nuevo**:
   - Corre el script:
     ```bash
     python3 enum_plugins.py
     ```
   - Resultado:
     ```
     [+] Plugin encontrado: site-editor
     Debes insertar esta url: http://172.17.0.2/wp-content/plugins/site-editor/readme.txt
     ```

---

## Paso 5: Verificación Manual
1. **Copiar la URL**:
   - Copia la URL proporcionada: `http://172.17.0.2/wp-content/plugins/site-editor/readme.txt`.

2. **Acceder en el Navegador**:
   - Pégala en el navegador y presiona Enter.
   - Verás el contenido del `readme.txt`, que incluye la versión del plugin (por ejemplo, "Stable tag: 1.1").

---

## Paso 6: Investigación de Vulnerabilidades
1. **Buscar Exploits**:
   - Con el nombre y versión del plugin ("site-editor 1.1"), busca en Google:
     ```
     site-editor 1.1 exploit
     ```
   - Encuentras que este plugin es vulnerable a un **Local File Inclusion (LFI)**.

2. **Explotación (Ejemplo)**:
   - Supongamos que el exploit requiere una URL como:
     ```
     http://172.17.0.2/wp-content/plugins/site-editor/editor.php?file=../../../../etc/passwd
     ```
   - Accede a esta URL en el navegador.
   - Si funciona, podrías ver el contenido del archivo `/etc/passwd` de la máquina, demostrando la vulnerabilidad.

**Nota**: La explotación está fuera del alcance de este tutorial y solo debe realizarse en entornos controlados con permiso explícito.

---

## Paso 7: Limpieza
1. **Detener la Máquina**:
   - En la terminal donde desplegaste "Azucar", presiona `Ctrl+C`.
   - Esto detiene y elimina la máquina de Docker, limpiando el entorno.

---

## Conclusión
Hemos creado un script en Python que:
- Enumera plugins instalados en un WordPress comprobando la existencia de archivos `readme.txt`.
- Proporciona las URLs para inspeccionar manualmente los plugins encontrados.
- Facilita la identificación de vulnerabilidades al revelar versiones de plugins.

Este proceso demuestra cómo técnicas simples de automatización con Python pueden ser poderosas en ciberseguridad. Recuerda practicar estas habilidades de manera ética y en entornos autorizados como Docker Labs.

---

## Código Final Completo
```python
import requests

# Lista de plugins a comprobar
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
    "site-editor"
    # Añade más plugins según necesites
)

# URL base (ajusta según la IP de tu máquina)
base_url = "http://172.17.0.2/wp-content/plugins/"

def check_plugin(plugin):
    url = f"{base_url}{plugin}/readme.txt"
    response = requests.get(url)
    if response.status_code == 200:
        print(f"[+] Plugin encontrado: {plugin}")
        print(f"Debes insertar esta url: {url}")
    else:
        pass

# Iterar sobre cada plugin
for plugin in plugins:
    check_plugin(plugin)
```

---

