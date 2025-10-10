
En este laboratorio, aprenderás a usar la herramienta **`tcpdump`** en un entorno de Linux para capturar, filtrar y analizar tráfico de red, una habilidad fundamental para cualquier analista de seguridad.

---

### Tarea 1: Identificar Interfaces de Red

Antes de capturar tráfico, necesitas saber qué interfaces de red están disponibles. 🌐

1. **Usar `ifconfig`**: Este es el comando tradicional para ver la configuración de las interfaces de red.
    
    Bash
    
    ```
    sudo ifconfig
    ```
    
    Este comando te mostrará interfaces como **`eth0`** (la conexión principal de Ethernet) y **`lo`** (la interfaz de loopback local).
    
2. **Usar `tcpdump`**: `tcpdump` también puede listar las interfaces disponibles, lo cual es útil si `ifconfig` no está instalado.
    
    Bash
    
    ```
    sudo tcpdump -D
    ```
    

---

### Tarea 2: Inspeccionar Tráfico de Red en Vivo

Esta tarea se centra en capturar y ver paquetes de red en tiempo real directamente desde una interfaz.

- **Comando de captura en vivo**: Para capturar 5 paquetes de la interfaz `eth0` con información detallada, usa:
    
    Bash
    
    ```
    sudo tcpdump -i eth0 -v -c5
    ```
    
    - **`-i eth0`**: Especifica la **interfaz** de red (`eth0`).
        
    - **`-v`**: Activa el modo **_verbose_**, que muestra información detallada de cada paquete (como TTL, banderas TCP y puertos).
        
    - **`-c5`**: Establece un **conteo** para detener la captura después de 5 paquetes.
        

---

### Tarea 3: Capturar Tráfico de Red a un Archivo

A menudo, querrás guardar los paquetes capturados en un archivo (`.pcap`) para un análisis posterior.

1. **Iniciar la captura en segundo plano**: Este comando captura 9 paquetes del **puerto 80** (tráfico web HTTP), evita la resolución de nombres y guarda el resultado en `capture.pcap`.
    
    Bash
    
    ```
    sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
    ```
    
    - **`-nn`**: Evita que `tcpdump` convierta las direcciones IP y los puertos en nombres, lo cual es más rápido y seguro.
        
    - **`port 80`**: Es un **filtro** que solo captura tráfico en el puerto 80.
        
    - **`-w capture.pcap`**: **Escribe** (_write_) la salida en el archivo `capture.pcap`.
        
    - **`&`**: Ejecuta el comando en **segundo plano** para que puedas seguir usando la terminal.
        
2. **Generar tráfico**: Para tener algo que capturar, puedes usar `curl`.
    
    Bash
    
    ```
    curl opensource.google.com
    ```
    

---

### Tarea 4: Filtrar y Analizar Datos de un Archivo

Una vez que tienes tu archivo `.pcap`, puedes usar `tcpdump` para leerlo y analizarlo de diferentes maneras.

1. **Leer el archivo con vista detallada**:
    
    Bash
    
    ```
    sudo tcpdump -nn -r capture.pcap -v
    ```
    
    - **`-r capture.pcap`**: **Lee** (_read_) los paquetes desde el archivo especificado en lugar de una interfaz en vivo.
        
2. **Ver el contenido del paquete en Hex y ASCII**: Esta vista es muy útil para análisis forense o de malware, ya que te permite ver los datos crudos del paquete.
    
    Bash
    
    ```
    sudo tcpdump -nn -r capture.pcap -X
    ```
    
    - **`-X`**: Muestra el contenido de cada paquete tanto en formato **hexadecimal** como en **ASCII**.
        

---

### Pon a Prueba Tus Conocimientos 🧠

Aquí están las respuestas a las preguntas para verificar lo aprendido:

- **¿Qué comando usarías para capturar 3 paquetes en cualquier interfaz con la opción detallada?**
    
    - ✅ `sudo tcpdump -c3 -i any -v`
        
- **¿Qué indica la opción `-i`?**
    
    - ✅ La interfaz de red para monitorear
        
- **¿Qué tipo de información incluye la opción `-v`?**
    
    - ✅ Información detallada
        
- **¿Qué comando `tcpdump` puedes usar para identificar las interfaces disponibles?**
    
    - ✅ `sudo tcpdump -D`