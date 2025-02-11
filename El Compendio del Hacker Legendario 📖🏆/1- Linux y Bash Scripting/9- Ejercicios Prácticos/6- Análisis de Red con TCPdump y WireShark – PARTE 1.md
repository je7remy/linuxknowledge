
---

#Pentesting #CyberSecurity #HackingÉtico #Linux #KaliLinux #Tcpdump #Wireshark #Sniffing #EthicalHacking #InfoSec #CTF #RedTeam #BlueTeam #SeguridadInformática #ForenseDigital #SysAdmin #DevSecOps #CapturaDeTráfico #AnálisisDeRed #FTP #ProtocolosInseguros

---
### **1. `tcpdump -I eth0`**

Este comando intenta habilitar **modo monitor** en la interfaz de red `eth0`. El modo monitor permite capturar paquetes en redes inalámbricas sin necesidad de estar conectado a ellas.

#### **Error observado:**

```
tcpdump: eth0: That device doesn't support monitor mode
```

- **Razón:** La interfaz `eth0` es una interfaz Ethernet (cableada), no inalámbrica. El modo monitor solo es soportado por interfaces Wi-Fi.

#### **Solución:**

Este comando no es válido para interfaces cableadas. En su lugar, puedes usar el siguiente comando para capturar tráfico estándar:

```bash
tcpdump -i eth0
```

---

### **2. `tcpdump -i eth0`**

Este comando captura tráfico en la interfaz `eth0` en tiempo real y lo muestra en pantalla.

#### **Opciones explicadas:**

- `-i eth0`: Selecciona la interfaz de red `eth0` para capturar tráfico.

#### **Uso:**

Ejecutar este comando capturará todos los paquetes entrantes y salientes de la interfaz `eth0`. Es útil para monitorear actividad general en la red.

---

### **3. `tcpdump -i eth0 icmp`**

Este comando filtra y captura únicamente los paquetes del protocolo ICMP (Internet Control Message Protocol) en la interfaz `eth0`.

#### **Detalles:**

- **ICMP:** Se utiliza para diagnóstico y control de red, como el comando `ping`.
- **Ejemplo práctico:**
    1. En una terminal de Windows, envía un ping a una IP (por ejemplo: la dirección de ip privada de la maquina virtual, `192.168.0.107`):
        
        ```cmd
        ping 192.168.0.107
        ```
        
    2. Captura los paquetes ICMP en Kali Linux con el comando:
        
        ```bash
        tcpdump -i eth0 icmp
        ```
        

#### **Resultado esperado:**

Capturarás paquetes tipo `echo request` y `echo reply` correspondientes al comando `ping`. Ejemplo:

```
14:52:11.123456 IP 192.168.0.1 > 192.168.0.107: ICMP echo request, id 1, seq 1, length 64
14:52:11.123567 IP 192.168.0.107 > 192.168.0.1: ICMP echo reply, id 1, seq 1, length 64
```

---

### **4. `tcpdump -i eth0 -w trafico.pcap`**

Este comando captura tráfico en la interfaz `eth0` y guarda los datos en un archivo llamado `trafico.pcap`.

#### **Opciones explicadas:**

- `-w trafico.pcap`: Especifica el archivo de salida donde se almacenará la captura.
- **Importante:** El archivo `trafico.pcap` puede ser analizado posteriormente con herramientas como Wireshark.

---

### **5. Proceso de conexión al servidor Ubuntu mediante FTP:**

1. **Configuración en el servidor Ubuntu:**
    
    - Crear un usuario llamado `invitado` para permitir el acceso FTP:
        
        ```bash
        sudo adduser invitado
        ```
        
2. **Conexión desde Kali Linux al servidor:**
    
    - Usar el cliente FTP para iniciar sesión:
        
        ```bash
        ftp 192.168.0.114
        ```
        
    - Ingresar el usuario `invitado` y su contraseña.
3. **Generar tráfico de red:**
    
    - Ejecutar comandos básicos como `ls` o subir/descargar archivos:
        
        ```bash
        ftp> ls
        ftp> put archivo.txt
        ftp> get archivo_remoto.txt
        ```
        
4. **Capturar este tráfico mientras se realiza la sesión FTP:**
    
    - Asegúrate de que el comando `tcpdump -i eth0 -w trafico.pcap` esté activo para registrar toda la sesión.

---

### **6. Analizar la captura en Wireshark:**

1. **Abrir el archivo `trafico.pcap`:**
    
    - Lanza Wireshark y selecciona `File > Open`, luego carga el archivo `trafico.pcap`.
    - o usa el comando `wireshark trafico.pcap` 
    
1. **Filtrar el tráfico FTP:**
    
    - Usa el filtro:
        
        ```wireshark
        ftp
        ```
        
    - Esto muestra solo los paquetes relacionados con el protocolo FTP.
3. **Buscar credenciales:**
    
    - Examina los paquetes para encontrar comandos `USER` y `PASS`, que contienen el usuario y la contraseña enviados en texto claro. Ejemplo:
        
        ```
        USER invitado
        PASS contraseña123
        ```
        
4. **Explorar más detalles:**
    
    - Revisa transferencias de archivos (`STOR`, `RETR`) y comandos como `ls` para entender toda la interacción.

---

### **Resumen de lo que aprendiste:**

- Capturaste tráfico en la red usando `tcpdump`.
- Registraste el tráfico en un archivo `.pcap` para análisis posterior.
- Filtraste y analizaste tráfico FTP en Wireshark para ver credenciales y detalles de sesión.

### Repetimos el proceso para afianzar el conocimiento:

1. **Preparar el entorno:**
    
    - Asegúrate de que tienes acceso a las máquinas:
        - Máquina **Kali Linux** con `tcpdump` instalado.
        - Servidor **Ubuntu** donde configuraste un usuario llamado `invitado`.
2. **Verificar la conectividad de red:**
    
    - Desde Windows, ejecuta un comando `ping` para confirmar que puedes comunicarte con el servidor Ubuntu:
        
        ```bash
        ping 192.168.0.107
        ```
        
    - Esto garantiza que la red está activa y funcional.
3. **Capturar tráfico con `tcpdump`:**
    
    - Inicia sesión en tu máquina Kali Linux.
    - Abre una terminal y ejecuta el siguiente comando para capturar tráfico de la interfaz `eth0` y guardarlo en un archivo:
        
        ```bash
        sudo tcpdump -i eth0 -w trafico.pcap
        ```
        
        - `-i eth0`: Captura en la interfaz de red `eth0`.
        - `-w trafico.pcap`: Guarda el tráfico en un archivo llamado `trafico.pcap`.
4. **Iniciar sesión en el servidor Ubuntu:**
    
    - Desde tu máquina Kali Linux, utiliza el cliente FTP para conectarte al servidor Ubuntu:
        
        ```bash
        ftp 192.168.0.114
        ```
        
        - Ingresa el usuario `invitado` y la contraseña correspondiente.
5. **Interactuar con el servidor FTP:**
    
    - Realiza algunas acciones básicas, como listar directorios (`ls`) o transferir archivos, para generar tráfico FTP que será capturado por `tcpdump`.
6. **Finalizar la captura:**
    
    - Cuando termines de interactuar con el servidor FTP, detén el proceso de captura en Kali Linux presionando `Ctrl + C` en la terminal donde ejecutaste `tcpdump`.
7. **Abrir el archivo de captura en Wireshark:**
    
    - Inicia Wireshark en tu máquina Kali Linux.
    - Abre el archivo `trafico.pcap`:
        
        ```bash
        wireshark trafico.pcap
        ```
        
    - Aplica un filtro para tráfico FTP:
        
        ```bash
        ftp
        ```
        
        Esto limitará la visualización a los paquetes relacionados con el protocolo FTP.
8. **Analizar la información capturada:**
    
    - Busca los paquetes FTP que contienen la autenticación (usuario y contraseña). Normalmente, esta información se encuentra en el paquete `USER` (usuario) y `PASS` (contraseña), ya que FTP no cifra las credenciales.
9. **Observaciones importantes:**
    
    - **Seguridad:** FTP transmite datos en texto claro, lo que permite capturar credenciales fácilmente. Considera usar FTP seguro (FTPS/SFTP) en entornos reales.
    - **Ética:** Asegúrate de tener permiso para realizar estas pruebas, ya que capturar tráfico sin autorización es ilegal.

### Resultado esperado:

En Wireshark, al filtrar por `ftp`, deberías ver paquetes como:

- `USER invitado`
- `PASS <contraseña>`

Este tráfico confirma que `tcpdump` capturó correctamente la sesión FTP. Puedes analizar más detalles sobre archivos transferidos o comandos ejecutados durante la sesión.


[[3- Análisis De La Red Desde Linux – Comandos Básicos Parte 1]]
[[4- Análisis de la Red con Bash – PARTE 2]]
[[5- Análisis de la Red con Bash – PARTE 3]]
**[[Hoja de trucos NMAP]]**
**[[nmap firewall evasion]]**
**[[nmap output]]**

