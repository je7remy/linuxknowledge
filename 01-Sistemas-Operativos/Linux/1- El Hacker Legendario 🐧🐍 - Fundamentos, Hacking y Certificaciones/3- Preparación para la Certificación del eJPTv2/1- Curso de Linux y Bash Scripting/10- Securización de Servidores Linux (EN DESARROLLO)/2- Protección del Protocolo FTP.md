
---

#Ciberseguridad #FTP #Hydra #Fail2Ban #KaliLinux #UbuntuServer #AtaquesDeFuerzaBruta #SeguridadDeRed #PenetrationTesting #EthicalHacking #Linux #Nmap #SeguridadEnRed #SSH #vsftpd #ProtecciónDeServidor #CiberseguridadPráctica #FuerzaBruta #SeguridadInformática #AtaqueYDefensa

---
# **🔹 Laboratorio: Ataque y Defensa de FTP con Kali Linux y Ubuntu Server**

### **1️⃣ Configuración del Servidor FTP en Ubuntu**

1. **Actualización de paquetes y instalación de vsftpd**
    
    ```bash
    sudo apt update
    sudo apt install vsftpd
    ```
    
2. **Iniciar y verificar el estado del servicio**
    
    ```bash
    sudo systemctl start vsftpd
    sudo systemctl status vsftpd
    ```
    
3. **Obtener la IP del servidor**
    
    ```bash
    hostname -I
    ```
    
    - La IP obtenida fue `192.168.0.118`.
4. **Conexión desde Kali Linux al servidor FTP**
    
    ```bash
    ftp 192.168.0.118
    ```
    
    - Esto confirma que el servicio FTP está corriendo en el puerto por defecto (`21`).

---

### **2️⃣ Escaneo con Nmap desde Kali**

1. **Ejecutamos un escaneo agresivo con Nmap para detectar servicios abiertos**
    
    ```bash
    nmap -p- -sS -sC -sV --min-rate=5000 -n -vvv -Pn 192.168.0.118
    ```
    
2. **Resultado del escaneo inicial:**
    - Puerto **21/tcp** (FTP) **abierto** → `vsftpd 3.0.5`
    - Puerto **111/tcp** (SSH) **abierto** → `OpenSSH 9.6p1 Ubuntu`

---

### **3️⃣ Cambio del Puerto del Servidor FTP**

1. **Editamos la configuración de vsftpd**
    
    ```bash
    sudo nano /etc/vsftpd.conf
    ```
    
    - Se cambia el puerto de `21` a `110`:
        
        Este código se pone debajo del todo en el archivo.
        
        *listen_port=110*
        
        
2. **Reiniciamos el servicio para aplicar cambios**
    
    ```bash
    sudo systemctl restart vsftpd
    ```
    
3. **Verificación con un nuevo escaneo de Nmap**
    
    ```bash
    nmap -p- -sS -sC -sV --min-rate=5000 -n -vvv -Pn 192.168.0.118
    ```
    
    - Ahora el puerto **21/tcp** ya no aparece abierto.
    - El servicio FTP ahora corre en **110/tcp**.
4. **Conexión desde Kali Linux usando el nuevo puerto**
    
    ```bash
    ftp 192.168.0.118 -P 110
    ```
    
    - Confirmamos que el cambio de puerto fue exitoso.

---

### **4️⃣ Prueba de Fuerza Bruta con Hydra**

1. **Ejecutamos Hydra para atacar el servicio FTP en el nuevo puerto 110**
    
    ```bash
    hydra -l jeremyserver -P /usr/share/wordlists/rockyou.txt.gz ftp://192.168.0.118 -s 110
    ```
    
2. **Resultado:**
    - Hydra encuentra credenciales válidas:
        - Usuario: `jeremyserver`
        - Contraseña: `password1`
    - **Esto confirma que el servidor FTP aún es vulnerable a ataques de fuerza bruta.**

---

### **5️⃣ Instalación y Configuración de Fail2Ban**

1. **Instalamos Fail2Ban en Ubuntu**
    
    ```bash
    sudo apt install fail2ban
    ```
    
2. **Creamos una regla específica para vsftpd**
    
    ```bash
    sudo nano /etc/fail2ban/jail.d/vsftpd.local
    ```
    
    - Configuración del archivo:
        
        
        [vsftpd]
        enabled = true
        port = 110
        filter = vsftpd
        logpath = /var/log/vsftpd.log
        maxretry = 5
        bantime = 600
        
        crtl+o para guardar
        ctrl+x para salir
        
3. **Reiniciamos y verificamos el estado de Fail2Ban**
    
    ```bash
    sudo systemctl restart fail2ban
    sudo systemctl status fail2ban
    sudo fail2ban-client status vsftpd
    ```
    

---

### **6️⃣ Comprobación de Bloqueo tras un Nuevo Ataque de Fuerza Bruta**

4. **Repetimos el ataque con Hydra**
    
    ```bash
    hydra -l jeremyserver -P /usr/share/wordlists/rockyou.txt.gz ftp://192.168.0.118 -s 110
    ```
    
5. **Resultado:**
    
    - Hydra falla y muestra un error:
        
        ```
        [ERROR] all children were disabled due to too many connection errors
        ```
        
    - **La IP atacante (`192.168.0.121`) ha sido bloqueada por Fail2Ban.**
6. **Verificamos en el servidor que la IP ha sido bloqueada**
    
    ```bash
    sudo fail2ban-client status vsftpd
    ```
    

---

### **7️⃣ Desbloqueo de la IP Bloqueada**

7. **Si queremos desbloquear la IP atacante, usamos:**
    
    ```bash
    sudo fail2ban-client set vsftpd unbanip 192.168.0.121
    ```
    
8. **Verificación de acceso al FTP tras el desbloqueo**
    
    ```bash
    ftp 192.168.0.118 -P 110
    ```
    
    - Ahora la máquina atacante puede conectarse nuevamente.
9. **Si repetimos un ataque de fuerza bruta con Hydra, la IP será bloqueada otra vez.**
    

---

### **📌 Repaso y mejoras**

**1. Configuración inicial del servidor FTP (Ubuntu):**
- Actualizaste paquetes: `sudo apt update`
- Instalaste vsftpd: `sudo apt install vsftpd`
- Iniciaste el servicio: `sudo systemctl start vsftpd`
- Verificaste la dirección IP: `hostname -I` (192.168.0.118)

**2. Conexión inicial desde Kali (prueba básica):**
- Usaste `ftp 192.168.0.118` (puerto 21 por defecto)
- Confirmaste que el servicio FTP respondía correctamente

**3. Escaneo inicial con Nmap:**
- Comando: `nmap -p- -sS -sC -sV...`
- Resultados:
  - Puerto 21 (FTP) abierto con vsftpd 3.0.5
  - Puerto 111 (SSH) abierto con OpenSSH 9.6p1

**4. Cambio de puerto del servicio FTP:**
- Modificaste `/etc/vsftpd.conf` agregando `listen_port=110`
- Reiniciaste el servicio: `sudo systemctl restart vsftpd`

**5. Verificación del cambio de puerto:**
- Nuevo escaneo Nmap mostró:
  - Puerto 110 abierto (FTP)
  - Puerto 111 (SSH) permaneció igual
- Conexión FTP exitosa con `ftp 192.168.0.118 -P 110`

**6. Ataque de fuerza bruta con Hydra:**
- Comando: `hydra -l jeremyserver... ftp://192.168.0.118 -s 110`
- Resultado exitoso: Contraseña encontrada (`password1`)
- **Vulnerabilidad expuesta:** No había protección contra intentos fallidos

**7. Implementación de Fail2Ban:**
- Instalación: `sudo apt install fail2ban`
- Creación de archivo de configuración personalizado:
  - Ruta: `/etc/fail2ban/jail.d/vsftpd.local`
  - Configuración:
    
    [vsftpd]
    enabled = true
    port = 110
    filter = vsftpd
    logpath = /var/log/vsftpd.log
    maxretry = 5
    bantime = 600
    

**8. Prueba de Fail2Ban:**
- Nuevo ataque con Hydra resultó en:
  - `[ERROR] all children were disabled due too many connection errors`
  - La IP atacante (192.168.0.121) fue bloqueada
- Verificación con `sudo fail2ban-client status vsftpd` mostró la IP en la lista de baneados

**9. Gestión de baneos:**
- Desbloqueo manual de IP: 
  ```bash
  sudo fail2ban-client set vsftpd unbanip 192.168.0.121
  ```
- Restauración de acceso FTP después del desbloqueo

**Análisis de seguridad:**
1. **Cambio de puerto:** Ofrece seguridad por ofuscación pero no es una medida real de protección
2. **vsftpd 3.0.5:** Versión actualizada (buena práctica)
3. **Fail2Ban:** Implementación efectiva para prevenir ataques de fuerza bruta
4. **Configuración de baneo:**
   - 5 intentos fallidos (maxretry)
   - Baneo de 10 minutos (600 segundos)
   - Monitoreo del archivo de log `/var/log/vsftpd.log`

**Posibles mejoras:**
1. Configurar autenticación con certificados SSL/TLS para FTP
2. Limitar usuarios permitidos para FTP
3. Usar listas de acceso (allow/deny) para IPs conocidas
4. Implementar contraseñas más fuertes
5. Actualizar el tiempo de baneo en Fail2Ban (`bantime`) a valores más altos
6. Habilitar logging detallado en vsftpd
7. Considerar el uso de SFTP (SSH) en lugar de FTP

**Lección clave:**
La combinación de:
- Actualización de servicios
- Cambio de puertos
- Herramientas de detección de intrusos (Fail2Ban)
- Monitoreo proactivo

Forma una estrategia de defensa en profundidad efectiva contra ataques comunes como fuerza bruta.


### **📌 Conclusión**

✔️ **Se cambió el puerto del servicio FTP** para evitar ataques dirigidos al puerto por defecto.  
✔️ **Se detectó una vulnerabilidad (fuerza bruta exitosa con Hydra)**.  
✔️ **Se implementó Fail2Ban** para mitigar ataques de fuerza bruta.  
✔️ **El sistema bloquea automáticamente IPs que intentan múltiples intentos de login fallidos**.

---

Este proceso mejora la seguridad del servidor FTP al ocultarlo en un puerto no estándar y al aplicar Fail2Ban como protección contra ataques automatizados. 🚀




[[1- Protección del Protocolo SSH]]
[[5- Cómo Crear un Servidor SSH con OPENSSH]]


