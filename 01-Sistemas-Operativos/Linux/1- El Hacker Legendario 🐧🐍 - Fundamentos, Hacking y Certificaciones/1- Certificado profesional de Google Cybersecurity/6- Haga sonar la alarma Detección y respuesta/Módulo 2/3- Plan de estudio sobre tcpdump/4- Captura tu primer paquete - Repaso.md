---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Captura tu primer paquete - Repaso

### Tarea 1: Identificar Interfaces de Red

Para comenzar a capturar tráfico, primero debes saber qué interfaces de red están disponibles en tu sistema.

- **Comandos clave**: Puedes usar dos comandos principales para listar las interfaces:
    
    - `sudo ifconfig`: Muestra detalles completos de las interfaces, como **`eth0`** (la conexión principal de Ethernet) y **`lo`** (la interfaz de loopback).
        
    - `sudo tcpdump -D`: Es una forma rápida y directa de listar todas las interfaces en las que `tcpdump` puede escuchar.
        

---

### Tarea 2: Inspeccionar Tráfico de Red en Vivo

Esta tarea se enfoca en capturar y mostrar paquetes de red directamente en tu terminal en tiempo real.

- **Comando de ejemplo**: Para capturar 5 paquetes de la interfaz `eth0` y mostrar información detallada sobre ellos, usa el siguiente comando:
    
    Bash
    
    ```
    sudo tcpdump -i eth0 -v -c5 
    ```
    
    - **`-i eth0`**: Especifica la **interfaz** de red que se va a monitorear.
        
    - **`-v`**: Activa el modo **_verbose_**, que muestra información detallada del paquete (como TTL, banderas TCP, etc.).
        
    - **`-c5`**: Indica a `tcpdump` que se detenga después de **contar** y capturar 5 paquetes.
        

---

### Tarea 3: Capturar Tráfico de Red a un Archivo

Es muy común guardar los paquetes capturados en un archivo `.pcap` para un análisis más profundo y posterior.

- **Comando para guardar en archivo**: Este comando captura 9 paquetes del **puerto 80** (tráfico web HTTP) y los guarda en un archivo llamado `capture.pcap`.
    
    Bash
    
    ```
    sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
    ```
    
    - **`-nn`**: Evita que `tcpdump` resuelva las direcciones IP y los puertos a nombres, lo que es más rápido y seguro.
        
    - **`port 80`**: Es un **filtro** para capturar solo el tráfico que va hacia o desde el puerto 80.
        
    - **`-w capture.pcap`**: Le dice a `tcpdump` que **escriba** (_write_) los paquetes en el archivo especificado.
        
    - **`&`**: Ejecuta el comando en **segundo plano** para que puedas seguir usando la terminal.
        

---

### Tarea 4: Filtrar y Analizar Datos de un Archivo Capturado

Una vez que tienes el archivo `.pcap`, puedes usar `tcpdump` para leerlo y examinar su contenido de diferentes maneras.

- **Leer el archivo con detalles**: Para leer el archivo `capture.pcap` y mostrar la información detallada de los paquetes, usa:
    
    Bash
    
    ```
    sudo tcpdump -nn -r capture.pcap -v
    ```
    
    - **`-r capture.pcap`**: Indica a `tcpdump` que **lea** (_read_) desde un archivo en lugar de una interfaz en vivo.
        
- **Ver el contenido en Hexadecimal y ASCII**: Para un análisis más profundo, como en la investigación de malware, puedes ver los datos crudos del paquete.
    
    Bash
    
    ```
    sudo tcpdump -nn -r capture.pcap -X
    ```
    
    - **`-X`**: Muestra el contenido del paquete en formato **hexadecimal** y **ASCII**.
        

---

### Pon a Prueba Tus Conocimientos 🧠

- **¿Qué comando usarías para capturar 3 paquetes en cualquier interfaz con la opción detallada?**
    
    - ✅ `sudo tcpdump -c3 -i any -v`
        
- **¿Qué indica la opción `-i`?**
    
    - ✅ La interfaz de red para monitorear
        
- **¿Qué tipo de información incluye la opción `-v`?**
    
    - ✅ Información detallada
        
- **¿Qué comando `tcpdump` puedes usar para identificar las interfaces disponibles?**
    
    - ✅ `sudo tcpdump -D`

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[3- Actividad - Captura tu primer paquete]]
- ➡️ Siguiente: [[5- Ejemplar - Capture su primer Paquete]]
