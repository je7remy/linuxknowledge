
### Resumen de Actividades

Como analista de seguridad, es importante saber cómo capturar y filtrar el tráfico de red en un entorno Linux. En esta actividad de laboratorio, realizarás tareas asociadas con el uso de **`tcpdump`** para capturar tráfico de red en un archivo de captura de paquetes (`.pcap`) y luego examinarás el contenido para concentrarte en tipos específicos de tráfico.

### Tarea 1: Identificar Interfaces de Red

En esta tarea, debes identificar las interfaces de red que se pueden utilizar para capturar datos.

1. Utiliza `ifconfig` para identificar las interfaces disponibles:
    
    Bash
    
    ```
    sudo ifconfig
    ```
    
    Este comando devuelve una salida similar a la siguiente:
    
    ```
    eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1460
            inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
            ether 02:42:ac:11:00:02  txqueuelen 0  (Ethernet)
            RX packets 784  bytes 9379957 (8.9 MiB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 683  bytes 56880 (55.5 KiB)
            TX errors 0  dropped 0 overruns 0  carrier 0 collisions 0
    
    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            loop  txqueuelen 1000  (Local Loopback)
            RX packets 400  bytes 42122 (41.1 KiB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 400  bytes 42122 (41.1 KiB)
            TX errors 0  dropped 0 overruns 0  carrier 0 collisions 0
    ```
    
    La interfaz de red Ethernet se identifica como **`eth0`**.
    
2. Utiliza `tcpdump` para identificar las opciones de interfaz disponibles:
    
    Bash
    
    ```
    sudo tcpdump -D
    ```
    
    Este comando también te permitirá identificar qué interfaces de red están disponibles, lo que puede ser útil en sistemas que no incluyen `ifconfig`.
    

---

### Tarea 2: Inspeccionar el Tráfico de Red con `tcpdump`

En esta tarea, debes utilizar `tcpdump` para filtrar el tráfico de paquetes de red en vivo en una interfaz.

1. Filtra datos de paquetes de red en vivo desde la interfaz **`eth0`**:
    
    Bash
    
    ```
    sudo tcpdump -i eth0 -v -c5
    ```
    
    - **`-i eth0`**: Capturar datos específicamente de la interfaz `eth0`.
        
    - **`-v`**: Mostrar datos detallados de paquetes.
        
    - **`-c5`**: Capturar 5 paquetes de datos.
        
    
    Algunos de sus datos de tráfico de paquetes serán similares a los siguientes:
    
    ```
    tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
    10:57:33.427749 IP (tos 0x0, ttl 64, id 35057, offset 0, flags [DF], proto TCP (6), length 134)
        7acb26dc1f44.5000 > some-remote-host.internal.59788: Flags [P.], cksum 0x5851 (incorrect > 0x30d3), seq 1:83, ack 1, win 501, options [nop,nop,TS val 1017464119 ecr 3001513453], length 82
    10:57:33.427954 IP (tos 0x0, ttl 64, id 21812, offset 0, flags [DF], proto TCP (6), length 52)
        some-remote-host.internal.59788 > 7acb26dc1f44.5000: Flags [.], cksum 0x9122 (correct), ack 83, win 510, options [nop,nop,TS val 3001513453 ecr 1017464119], length 0
    ...
    5 packets captured
    7 packets received by filter
    0 packets dropped by kernel
    ```
    
    **Explorar los detalles de los paquetes de red**
    
    1. `tcpdump` informó que estaba escuchando en la interfaz **`eth0`**:
        
        ```
        tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
        ```
        
    2. El primer campo es la marca de tiempo del paquete, seguido del tipo de protocolo, **IP**:
        
        ```
        10:57:33.427749 IP 
        ```
        
    3. La opción _verbose_, **`-v`**, ha proporcionado más detalles sobre los campos del paquete IP:
        
        ```
        (tos 0x0, ttl 64, id 35057, offset 0, flags [DF], proto TCP (6), length 134)
        ```
        
    4. Los datos muestran los sistemas que se están comunicando entre sí:
        
        ```
        7acb26dc1f44.5000 > some-remote-host.internal.59788:
        ```
        
    5. Los datos restantes son del encabezado para el paquete TCP interno:
        
        ```
        Flags [P.], cksum 0x5851 (incorrect > 0x30d3), seq 1:83, ack 1, win 501, options [nop,nop,TS val 1017464119 ecr 3001513453], length 82
        ```
        

---

### Tarea 3: Capturar el Tráfico de Red con `tcpdump`

En esta tarea, utilizarás `tcpdump` para guardar los datos de red capturados en un archivo.

1. Captura los datos de paquetes en un archivo llamado **`capture.pcap`**:
    
    Bash
    
    ```
    sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
    ```
    
    - **`-nn`**: No resolver direcciones IP o puertos a nombres.
        
    - **`-c9`**: Capturar 9 paquetes y salir.
        
    - **`port 80`**: Filtrar sólo el tráfico del puerto 80 (HTTP).
        
    - **`-w capture.pcap`**: Guardar los datos capturados en el archivo nombrado.
        
    - **`&`**: Ejecutar el comando en segundo plano.
        
2. Usa `curl` para generar algo de tráfico HTTP (puerto 80):
    
    Bash
    
    ```
    curl opensource.google.com
    ```
    
3. Comprueba que se han capturado los paquetes de datos:
    
    Bash
    
    ```
    ls -l capture.pcap
    ```
    

---

### Tarea 4: Filtrar los Datos de Paquetes Capturados

En esta tarea, utiliza `tcpdump` para filtrar los datos del archivo que guardaste anteriormente.

1. Utiliza `tcpdump` para filtrar los datos de cabecera del paquete del archivo `capture.pcap`:
    
    Bash
    
    ```
    sudo tcpdump -nn -r capture.pcap -v
    ```
    
    - **`-r`**: Leer los datos de captura del archivo nombrado.
        
    
    Esto devuelve datos de salida similares a los siguientes:
    
    ```
    reading from file capture.pcap, link-type EN10MB (Ethernet)
    20:53:27.669101 IP (tos 0x0, ttl 64, id 50874, offset 0, flags [DF], proto TCP (6), length 60)
        172.17.0.2.46498 > 146.75.38.132.80: Flags [S], cksum 0x5445 (incorrect), seq 4197622953, win 65320, options [mss 1420,sackOK,TS val 610940466 ecr 0, nop,wscale 7], length 0
    20:53:27.669422 IP (tos 0x0, ttl 62, id 0, offset 0, flags [DF], proto TCP (6), length 60)
        146.75.38.132.80 > 172.17.0.2.46498: Flags [S.], cksum 0xc272 (correct), seq 2026312556, ack 4197622953, win 65535, options [mss 1420,sackOK,TS val 155704241 ecr 610940466, nop,wscale 9], length 0
    ```
    
2. Utiliza `tcpdump` para filtrar los datos de paquetes extendidos del archivo `capture.pcap`:
    
    Bash
    
    ```
    sudo tcpdump -nn -r capture.pcap -X
    ```
    
    - **`-X`**: Mostrar los datos del paquete en formato de salida hexadecimal y ASCII.
        

---

### Comprueba Tus Conocimientos 🧠

- **¿Qué comando usarías para capturar 3 paquetes en cualquier interfaz con la opción detallada?**
    
    - **Respuesta**: `sudo tcpdump -c3 -i any -v`
        
- **¿Qué indica la opción `-i`?**
    
    - **Respuesta**: La opción `-i` indica la **interfaz de red** a monitorizar.
        
- **¿Qué tipo de información incluye la opción `-v`?**
    
    - **Respuesta**: La opción `-v` proporciona **información detallada**.
        
- **¿Qué comando `tcpdump` puede utilizar para identificar las interfaces que están disponibles?**
    
    - **Respuesta**: `sudo tcpdump -D`