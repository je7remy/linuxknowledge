
---

#Linux #Curl #HTTP #Descargas #Automatización #Terminal #ComandosLinux #SysAdmin #Networking #DevOps

---

### **CURL: Información básica**

- **Siglas:**  
    `curl` significa **Client URL**.
    
- **Función:**  
    Es una herramienta de línea de comandos para transferir datos mediante diferentes protocolos como HTTP, HTTPS, FTP, entre otros.
    

---

### **1. Comprobar si una web existe con HTTP**

Para verificar si un sitio responde correctamente, utiliza:

curl -I http://ejemplo.com

- Esto devuelve los encabezados HTTP, incluyendo el código de estado (`200 OK`, `404 Not Found`, etc.).

---

### **2. Hacer una petición HTTP**

Una solicitud HTTP simple (GET) se hace así:

curl http://ejemplo.com

Esto muestra el contenido de la página en la terminal.

### **3. Descargar un archivo**

Para descargar un archivo desde una URL y guardarlo en tu equipo:

curl -O http://ejemplo.com/archivo.zip

El archivo se guardará con el mismo nombre que tiene en el servidor (`archivo.zip`), tambien podriamos experimentar otra cosas como:

curl http://ejemplo.com/archivodegithub.sh -o "buscador de imagenes.sh" 

para que quede con el nombre que quieras.

### **1. Comprobar si una web existe con HTTP (Avanzado)**

curl -s -o /dev/null -w "%{http_code}" http://ejemplo.com 
### Qué hace:

1. **`-s`**: Oculta mensajes de progreso o errores.
2. **`-o /dev/null`**: Ignora el contenido de la respuesta.
3. **`-w "%{http_code}"`**: Muestra solo el código de estado HTTP (e.g., 200, 404).
4. **`http://ejemplo.com`**: URL objetivo.

**Resultado:** Solo imprime el código HTTP, útil para comprobar el estado de un sitio.

### Veamos el siguiente método de instalación de un navegador con curl 

curl -fsS https://dl.brave.com/install.sh | sh

1. **`curl`**:
    
    - recordemos que curl es una herramienta de línea de comandos utilizada para transferir datos desde o hacia un servidor. En este caso, está siendo usada para descargar un archivo desde una URL.
2. **`-fsS`**:
    
    - Estas son opciones que se pasan a `curl` para modificar su comportamiento:
        - **`-f`**: Si hay un error en la transferencia (por ejemplo, si no se puede acceder a la URL), `curl` fallará sin mostrar mensajes de error innecesarios.
        - **`-s`**: "Silent" (silencioso), lo que significa que `curl` no mostrará ninguna información de progreso ni mensajes de error.
        - **`-S`**: Si ocurre un error, muestra el mensaje de error, incluso si se ha usado la opción `-s` (silencioso).
3. **`https://dl.brave.com/install.sh`**:
    
    - Es la URL de un script de instalación para Brave. Este script es descargado a tu máquina.
4. **`|` (pipe)**:
    
    - El símbolo de pipe se utiliza para redirigir la salida de un comando como entrada para otro. En este caso, la salida del comando `curl` (el contenido del archivo descargado) se pasa directamente al siguiente comando.
5. **`sh`**:
    
    - `sh` es el intérprete de comandos de shell que ejecuta el script descargado. En este caso, ejecutará el archivo `install.sh` que contiene los comandos necesarios para instalar el navegador Brave en tu sistema.

En resumen, este comando descarga un script de instalación de Brave y lo ejecuta directamente en tu terminal para instalar el navegador de manera automática.



**[[3- Transferencia de Archivos por la Red]]** 
**[[1- Protocolo HTTP]]**
**[[5- Cómo Utilizar WGET]]**
**[[3- Securización de Servidores Web Apache – PARTE 1]]**
**[[6- Securización de Servidores Web Apache – Evitar Ataques de Fuzzing Web – PARTE 4]]**