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