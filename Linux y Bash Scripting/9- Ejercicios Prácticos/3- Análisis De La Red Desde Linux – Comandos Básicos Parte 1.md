[[1- Comandos Basicos - Intermedio]]
1. **`hostname -I`**:
    
    - **Descripción**: Este comando muestra todas las direcciones IP asignadas a las interfaces de red del dispositivo, excluyendo las direcciones de loopback (127.0.0.1).
    - **Resultado**: Obtendrás una lista de IPs (ejemplo: `192.168.1.100 10.0.0.1`), lo que te permite saber cómo está configurada la red en tu máquina.
2. **`ip a`**:
    
    - **Descripción**: Este comando muestra información detallada sobre todas las interfaces de red (como sus nombres, estados, y direcciones IP).
    - **Resultado**: Se desplegará un listado de todas las interfaces de red (por ejemplo, `eth0`, `wlan0`) y sus detalles asociados.
3. **`ifconfig`**:
    
    - **Descripción**: Similar a `ip a`, este comando muestra las configuraciones de red de las interfaces (aunque está algo desactualizado frente a `ip`).
    - **Resultado**: Lista las interfaces de red activas y sus configuraciones, como direcciones IP, máscaras de subred y estados.
4. **`arp-scan`**:
    
    - **Descripción**: Escanea la red para identificar todos los dispositivos conectados dentro del rango de red configurado. Esto se basa en el protocolo ARP.
    - **Resultado**: Te proporciona una lista de dispositivos, mostrando direcciones IP y MAC, útil para identificar quién está conectado a tu red.
5. **`sudo arp-scan -I eth0 --localnet`**:
    
    - **Descripción**: Ejecuta un escaneo ARP más específico en la interfaz `eth0` sobre toda la red local.
    - **Resultado**: Muestra todos los dispositivos activos en la red local, asociando IPs con sus direcciones MAC. Esto es muy útil para identificar dispositivos desconocidos en una red.
6. **`nmap 192.168.118.205`**:
    
    - **Descripción**: Escanea el host `192.168.118.205` para identificar puertos abiertos y servicios en ejecución.
    - **Resultado**: Muestra qué puertos comunes están abiertos, junto con los servicios asociados. Esto es una primera aproximación para evaluar vulnerabilidades en un host.
7. **`nmap -p- 192.168.118.205`**:
    
    - **Descripción**: Realiza un escaneo completo de todos los puertos (del 1 al 65535) en el host `192.168.118.205`.
    - **Resultado**: Detecta todos los puertos abiertos y servicios en ejecución en el dispositivo objetivo. Esto lleva más tiempo pero ofrece información exhaustiva.

### Desarrollo

Cada paso implica una fase del reconocimiento o análisis de una red o dispositivo, una práctica común en auditorías de seguridad. En este caso, comenzamos por identificar la IP del dispositivo (con `hostname -I` o `ip a`), luego obtenemos información de dispositivos conectados (con `arp-scan`) y pasamos a identificar servicios y puertos abiertos en un objetivo específico (`nmap`). Esto forma parte de las fases de reconocimiento y escaneo, fundamentales en un análisis ético de vulnerabilidades【7†source】【9†source】.

