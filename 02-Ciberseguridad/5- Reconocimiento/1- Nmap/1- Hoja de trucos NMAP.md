
---

#Nmap #Pentesting #CyberSecurity #HackingÉtico #EthicalHacking #InfoSec #RedTeam #BlueTeam #SeguridadInformática #EscaneoDeRedes #OSINT #Networking #SysAdmin #DevSecOps #PortScanning #NetworkSecurity #CTF #Redes #Ciberseguridad

---
### Escaneo de IPs y Redes

| Opción    | Ejemplo                       | Descripción                         |
| --------- | ----------------------------- | ----------------------------------- |
|           | nmap 192.168.50.1             | Escanear una IP única               |
|           | nmap 192.168.50.1 192.168.2.1 | Escanear IPs específicas            |
|           | nmap 192.168.50.1-254         | Escanear un rango                   |
|           | nmap scanme.nmap.org          | Escanear un dominio                 |
|           | nmap 192.168.50.0/24          | Escanear usando notación CIDR       |
| -iL       | nmap -iL targets.txt          | Escanear objetivos desde un archivo |
| --exclude | nmap --exclude 192.168.50.1   | Excluir hosts listados              |

### Tipos de Escaneo

|Opción|Ejemplo|Descripción|
|---|---|---|
|-sS|nmap 192.168.50.1 -sS|Escaneo de puertos TCP SYN (Predeterminado)|
|-sT|nmap 192.168.50.1 -sT|Escaneo de puertos TCP connect (Predeterminado sin privilegios de root)|
|-sU|nmap 192.168.50.1 -sU|Escaneo de puertos UDP|
|-sA|nmap 192.168.50.1 -sA|Escaneo de puertos TCP ACK|
|-sW|nmap 192.168.50.1 -sW|Escaneo de puertos TCP Window|

### Detección del Sistema Operativo

|Opción|Ejemplo|Descripción|
|---|---|---|
|-O|nmap 192.168.50.1 -O|Detección remota de OS usando huella digital de TCP/IP|
|-O --osscan-limit|nmap 192.168.50.1 -O --osscan-limit|No intentará detectar OS si no se encuentra al menos un puerto TCP abierto y uno cerrado|
|-O --osscan-guess|nmap 192.168.50.1 -O --osscan-guess|Hace que Nmap adivine más agresivamente|
|-O --max-os-tries|nmap 192.168.50.1 -O --max-os-tries 1|Establece el número máximo de intentos de detección de OS contra un objetivo|
|-A|nmap 192.168.50.1 -A|Habilita detección de OS, detección de versión, escaneo de scripts y traceroute|

### Descubrimiento de Hosts

|Opción|Ejemplo|Descripción|
|---|---|---|
|-sL|nmap 192.168.50.1-3 -sL|Sin escaneo. Solo listar objetivos|
|-sn|nmap 192.168.50.1/24 -sn|Desactivar escaneo de puertos. Solo descubrimiento de hosts|
|-Pn|nmap 192.168.50.1-5 -Pn|Desactivar descubrimiento de hosts. Solo escaneo de puertos|
|-PS|nmap 192.168.50.1-5 -PS22-25,80|Descubrimiento TCP SYN en puerto x. Puerto 80 por defecto|
|-PA|nmap 192.168.50.1-5 -PA22-25,80|Descubrimiento TCP ACK en puerto x. Puerto 80 por defecto|
|-PU|nmap 192.168.50.1-5 -PU53|Descubrimiento UDP en puerto x. Puerto 40125 por defecto|
|-PR|nmap 192.168.50.1-1/24 -PR|Descubrimiento ARP en red local|
|-n|nmap 192.168.50.1 -n|Nunca hacer resolución DNS|

### Escaneo de Puertos

|Opción|Ejemplo|Descripción|
|---|---|---|
|-p|nmap 192.168.50.1 -p 21|Escaneo de puerto específico|
|-p|nmap 192.168.50.1 -p 21-100|Rango de puertos|
|-p|nmap 192.168.50.1 -p U:53,T:21-25,80|Escaneo de múltiples puertos TCP y UDP|
|-p-|nmap 192.168.50.1 -p-|Escaneo de todos los puertos|
|-p|nmap 192.168.50.1 -p http,https|Escaneo de puerto por nombre de servicio|
|-F|nmap 192.168.50.1 -F|Escaneo rápido de puertos (100 puertos)|
|--top-ports|nmap 192.168.50.1 --top-ports 2000|Escaneo de los mejores x puertos|
|-p-65535|nmap 192.168.50.1 -p-65535|Dejando fuera el puerto inicial en el rango hace que el escaneo comience en el puerto 1|
|-p0-|nmap 192.168.50.1 -p0-|Dejando fuera el puerto final en el rango hace que el escaneo vaya hasta el puerto 65535|

### Detección de Versión

|Opción|Ejemplo|Descripción|
|---|---|---|
|-sV|nmap 192.168.50.1 -sV|Intenta determinar la versión del servicio corriendo en el puerto|
|-sV --version-intensity|nmap 192.168.50.1 -sV --version-intensity 8|Nivel de intensidad de 0 a 9. Mayor número aumenta la posibilidad de precisión|
|-sV --version-light|nmap 192.168.50.1 -sV --version-light|Habilita modo ligero. Menor posibilidad de precisión. Más rápido|
|-sV --version-all|nmap 192.168.50.1 -sV --version-all|Habilita nivel de intensidad 9. Mayor posibilidad de precisión. Más lento|
|-A|nmap 192.168.50.1 -A|Habilita detección de OS, detección de versión, escaneo de scripts y traceroute|

### Tiempo y Rendimiento

| Opción | Ejemplo               | Descripción                                                                                       |
| ------ | --------------------- | ------------------------------------------------------------------------------------------------- |
| -T0    | nmap 192.168.50.1 -T0 | Paranoico (0) Evasión de Sistemas de Detección de Intrusos                                        |
| -T1    | nmap 192.168.50.1 -T1 | Sigiloso (1) Evasión de Sistemas de Detección de Intrusos                                         |
| -T2    | nmap 192.168.50.1 -T2 | Cortés (2) reduce la velocidad del escaneo para usar menos ancho de banda y recursos del objetivo |
| -T3    | nmap 192.168.50.1 -T3 | Normal (3) que es la velocidad predeterminada                                                     |
| -T4    | nmap 192.168.50.1 -T4 | Agresivo (4) acelera los escaneos; asume que estás en una red razonablemente rápida y confiable   |
| -T5    | nmap 192.168.50.1 -T5 | Insano (5) acelera los escaneos; asume que estás en una red extraordinariamente rápida            |



[[1- Comandos Basicos - Intermedio]]
**[[3- Análisis De La Red Desde Linux – Comandos Básicos Parte 1]]**
**[[4- Análisis de la Red con Bash – PARTE 2]]** 
**[[6- Análisis de Red con TCPdump y WireShark – PARTE 1]]**
**[[3- nmap firewall evasion]]**
**[[4- nmap output]]**
[[2- nmap comands]]
[[5- nmap scripts]]
