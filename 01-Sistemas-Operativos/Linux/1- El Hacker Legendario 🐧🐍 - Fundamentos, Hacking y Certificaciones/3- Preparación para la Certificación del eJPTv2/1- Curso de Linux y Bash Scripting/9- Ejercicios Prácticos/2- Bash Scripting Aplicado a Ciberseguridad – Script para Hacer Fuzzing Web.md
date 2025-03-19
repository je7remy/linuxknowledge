### **Contexto**

Este script realiza pruebas de fuerza bruta en un servidor web utilizando un diccionario (lista de directorios comunes) para identificar directorios o rutas accesibles en el servidor.

### **1. Preparación del entorno**

1. **Ejecutar un servidor local**:
    
    ```bash
    python3 -m http.server 80
    ```
    
    Esto inicia un servidor web en el puerto 80 de tu máquina local. Este será el objetivo del script para realizar las pruebas.
    
2. **Comprobar el diccionario**: Se usa el diccionario proporcionado en `/usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt`, que contiene nombres comunes de directorios para descubrir rutas válidas en el servidor objetivo.
    
3. **Verificar líneas del diccionario**:
    
    ```bash
    wc -l /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt
    ```
    
    Este comando cuenta el número total de líneas del archivo (cada línea corresponde a un nombre de directorio o archivo). Esto es útil para rastrear el progreso del script.
    

### **2. Script `fuzzer.sh`**

Este script toma dos argumentos: el diccionario y la URL base del servidor.

#### **Código detallado**:

```bash
#!/bin/bash

# Verificación de los argumentos.
if [ $# -ne 2 ]; then
    echo "Uso: <Diccionario> <URL>"
    exit 1
fi

diccionario="$1"
url="$2"

# Contar líneas totales en el diccionario.
total_lines=$(wc -l $diccionario | awk '{print $1}')
current_line=0

# Leer el diccionario línea por línea.
while read -r linea; do
    current_line=$((current_line + 1))
    echo -ne "Progreso: $current_line / $total_lines\r"
    
    # Realizar una solicitud HTTP para cada ruta.
    respuesta=$(curl -s -o /dev/null -w "%{http_code}" "$url$linea/")

    # Si la respuesta es 200, la URL es válida.
    if [ "$respuesta" -eq 200 ]; then
        echo "URL accesible: $url$linea/"
    fi
done < "$diccionario"
```

### **3. Ejecución del script**

El comando para ejecutarlo sería:

```bash
./fuzzer.sh /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt http://localhost/
```

#### **Proceso paso a paso**:

1. **Entrada del usuario**:
    
    - `diccionario`: Archivo de texto con nombres de directorios comunes.
    - `URL`: Base del servidor objetivo, en este caso `http://localhost/`.
2. **Ciclo principal**:
    
    - El script recorre cada línea del diccionario, simulando una solicitud HTTP `GET` con `curl` a la combinación de la URL base más el nombre del directorio actual.
    - Ejemplo: Si la línea actual del diccionario es `admin`, realiza una solicitud a `http://localhost/admin/`.
3. **Verificación de la respuesta**:
    
    - Utiliza `curl` para obtener el código de estado HTTP de la solicitud.
    - Si el código es `200`, indica que el directorio es accesible y lo imprime en la salida.
4. **Progreso**:
    
    - El script imprime el progreso actual en tiempo real, mostrando cuántas líneas del diccionario se han procesado.
5. **Resultados**:
    
    - Para cada directorio encontrado (código 200), muestra un mensaje como:
        
        ```bash
        URL accesible: http://localhost/admin/
        ```
        

### **4. Análisis**

- Este método es útil para mapear rutas ocultas en un servidor web durante pruebas de penetración.
- Los resultados ayudan a identificar directorios no protegidos o expuestos.

### **Cosas Asumidas y Omisiones**

Al explicar el uso del script `fuzzer.sh`, algunas configuraciones y pasos previos necesarios para que las pruebas funcionen correctamente fueron omitidos. A continuación, se detalla lo que asumimos que pasa y las configuraciones necesarias que deben realizarse antes de ejecutar las pruebas:

---

### **1. Creación de la estructura web de prueba**

Antes de levantar el servidor local con `python3 -m http.server 80`, se asume que existe una estructura de directorios o archivos que sirva como base para las pruebas. Sin embargo, esto no se mencionó ni detalló.

#### **Pasos asumidos para crear la estructura web**:

1. **Crear un directorio base para el servidor**:
    
    ```bash
    mkdir webserver
    cd webserver
    ```
    
2. **Añadir contenido web simulado**: Crear directorios y archivos simulados para que el script pueda identificarlos como "URLs accesibles". Por ejemplo:
    
    ```bash
    mkdir admin
    mkdir users
    mkdir config
    echo "Página admin" > admin/index.html
    echo "Página de usuarios" > users/index.html
    echo "Configuración" > config/index.html
    ```
    
    Ahora la estructura del servidor sería:
    
    ```
    webserver/
    ├── admin/
    │   └── index.html
    ├── users/
    │   └── index.html
    └── config/
        └── index.html
    ```
    
3. **Levantar el servidor en este directorio**: Desde el directorio `webserver`, iniciar el servidor:
    
    ```bash
    python3 -m http.server 80
    ```
    
    Esto sirve al contenido local en `http://localhost/`.
    

---

### **2. Disponibilidad del diccionario**

Se asumió que el archivo `/usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt` ya existe en el sistema. Este archivo debe estar accesible y contener una lista de directorios comunes.

#### **Omisión de verificar el archivo**:

Si no existe el archivo en la ruta mencionada, es posible obtener uno desde el repositorio de DirBuster o crear uno manualmente:

- **Descargar un diccionario desde un repositorio público**:
    
    ```bash
    sudo apt update
    sudo apt install dirb
    ```
    
    Esto instalará DirBuster y sus listas de directorios.
    
- **Crear un diccionario básico**: Si no se desea usar un archivo grande, se puede crear uno mínimo para pruebas rápidas:
    
    ```bash
    echo -e "admin\nusers\nconfig\ntest\nbackup" > small-wordlist.txt
    ```
    
    Este archivo contiene nombres de directorios comunes para probar con el script.
    

---

### **3. Uso de permisos y dependencias**

Se asumió que el usuario tiene los permisos necesarios para ejecutar las herramientas involucradas (e.g., `curl`) y que las dependencias están instaladas correctamente.

#### **Omisión de verificar dependencias**:

1. **Verificar que `curl` esté instalado**:
    
    ```bash
    which curl
    ```
    
    Si no está instalado:
    
    ```bash
    sudo apt update
    sudo apt install curl
    ```
    
2. **Permisos para ejecutar el script**: El script debe tener permisos de ejecución:
    
    ```bash
    chmod +x fuzzer.sh
    ```
    

---

### **4. Prueba de conectividad al servidor**

Antes de ejecutar el script, se asumió que el servidor local está funcionando correctamente y que el puerto `80` está accesible.

#### **Omisión de prueba de conectividad**:

1. **Probar el acceso manualmente**: Antes de usar el script, es importante probar si el servidor responde correctamente. Esto se puede hacer accediendo desde un navegador:
    
    - Visitar `http://localhost/` en un navegador.
    - Asegurarse de que los directorios y archivos creados anteriormente son accesibles.
2. **Probar usando `curl`**: Realizar una solicitud manual para confirmar la accesibilidad:
    
    ```bash
    curl -I http://localhost/
    ```
    
    Si el servidor está activo, debería devolver un encabezado HTTP con código `200 OK`.
    

---

### **5. Errores potenciales y manejo de excepciones**

El script no incluye un manejo robusto de errores en caso de que:

- El diccionario no exista.
- El servidor no esté disponible.
- Se produzcan problemas de red.

#### **Omisión de manejo de errores básicos**:

Es buena práctica añadir verificaciones al script para manejar estos casos. Por ejemplo:

- **Verificar la existencia del diccionario**:
    
    ```bash
    if [ ! -f "$diccionario" ]; then
        echo "Error: El archivo $diccionario no existe."
        exit 1
    fi
    ```
    
- **Comprobar si el servidor está activo**:
    
    ```bash
    curl -s -o /dev/null -w "%{http_code}" "$url" | grep -q 200
    if [ $? -ne 0 ]; then
        echo "Error: No se puede acceder a $url. Asegúrate de que el servidor está activo."
        exit 1
    fi
    ```
    

---

### **6. Documentación y resultados esperados**

El uso del script también asumió que el usuario sabe interpretar los resultados generados. Cada vez que el script detecta un directorio accesible, imprime un mensaje en la salida estándar.

#### **Ejemplo de resultados esperados**:

Con la estructura web previamente creada, la ejecución del script debería mostrar:

```bash
URL accesible: http://localhost/admin/
URL accesible: http://localhost/users/
URL accesible: http://localhost/config/
```

Si el servidor no contiene otros directorios coincidentes con el diccionario, no se mostrarán más resultados.

---

### **Cosas a tener en cuenta para hacer el laboratorio**

1. **Creación de la estructura de archivos y directorios web**.
2. **Comprobación de la existencia y accesibilidad del diccionario**.
3. **Verificación de conectividad con el servidor antes de las pruebas**.
4. **Manejo de errores básicos en el script**.
5. **Documentación clara sobre cómo interpretar los resultados del script**.

