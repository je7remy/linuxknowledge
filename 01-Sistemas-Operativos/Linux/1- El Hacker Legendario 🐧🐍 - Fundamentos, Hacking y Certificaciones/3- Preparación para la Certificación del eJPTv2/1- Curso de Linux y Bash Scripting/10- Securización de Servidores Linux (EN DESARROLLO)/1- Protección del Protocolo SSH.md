---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, linux, bash]
actualizado: 2026-05-28
---

# Protección del Protocolo SSH

---

#CyberSecurity #HackingÉtico #Linux #KaliLinux #Ubuntu #SSH #Fail2Ban #Pentesting #EthicalHacking #InfoSec #CTF #RedTeam #BlueTeam #SeguridadInformática #ForenseDigital #SysAdmin #DevSecOps #Redes #Nmap #Hydra #Hardening

----
# **🔹 Laboratorio: Ataque y Defensa de SSH con Kali Linux y Ubuntu Server**

Este laboratorio muestra cómo realizar un **ataque de fuerza bruta** a un servidor **Ubuntu** con **Hydra** desde Kali Linux y luego cómo **protegerlo** con Fail2Ban.

---

## **1️⃣ Configurar la red en VirtualBox o VMware**

1. **Inicia ambas máquinas virtuales**:
    - **Ubuntu Server** (objetivo).
    - **Kali Linux** (atacante).
2. **Configura el adaptador de red en modo puente** para que ambas estén en la misma red.
3. **Verifica que tienen direcciones IP en la misma subred:**
    
    ```bash
    ip a
    ```
    

---

## **2️⃣ Configurar el servidor SSH en Ubuntu**

### **1. Cambiar contraseña de usuario**

```bash
sudo passwd jeremyserver
```

- Usamos una contraseña débil para pruebas: **password1**.

### **2. Instalar y activar el servicio SSH**

```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl start ssh
sudo systemctl enable ssh
sudo systemctl status ssh
```

- **Verificamos que SSH está corriendo.**

### **3. Obtener la IP del servidor Ubuntu**

```bash
hostname -I
```

- Supongamos que la IP del servidor es **192.168.0.108**.

---

## **3️⃣ Ataque de fuerza bruta con Hydra desde Kali Linux**

```bash
hydra -l jeremyserver -P /usr/share/wordlists/rockyou.txt ssh://192.168.0.108
```

### **Explicación de los argumentos:**

- **`-l jeremyserver`** → Usuario objetivo.
- **`-P /usr/share/wordlists/rockyou.txt`** → Lista de contraseñas.
- **`ssh://192.168.0.108`** → Protocolo y dirección IP del objetivo.

### **Resultado exitoso:**

```
[22][ssh] host: 192.168.0.108   login: jeremyserver   password: password1
```

🔴 **SSH es vulnerable a ataques de fuerza bruta.**

---

## **4️⃣ Escaneo con Nmap para detectar puertos abiertos**

```bash
nmap -p- -sS -sC -sV --min-rate=5000 -n -vvv -Pn 192.168.0.108
```

### **Explicación de los argumentos:**

- **`-p-`** → Escanea **todos los puertos** (0-65535).
- **`-sS`** → Escaneo **SYN stealth** (rápido y sigiloso).
- **`-sC`** → Usa scripts básicos de reconocimiento.
- **`-sV`** → Detecta versiones de los servicios activos.
- **`--min-rate=5000`** → Acelera el escaneo.
- **`-n`** → No resuelve nombres de dominio (más rápido).
- **`-vvv`** → Muestra salida **detallada**.
- **`-Pn`** → No hace ping, **asume que el host está activo**.

### **Salida relevante:**

```
PORT   STATE SERVICE  VERSION
21/tcp open  ftp      vsftpd 3.0.5
22/tcp open  ssh      OpenSSH 9.6p1 Ubuntu 3ubuntu13.5 (Ubuntu Linux; protocol 2.0)
```

🔴 **SSH está visible y expuesto en el puerto 22**.

---

## **5️⃣ Mejorar la seguridad: Cambiar el puerto de SSH**

### **1. Editar configuración de SSH**

```bash
sudo nano /etc/ssh/sshd_config
```

- Cambiar:
    
    ```
    Port 22
    ```
    
    Por:
    
    ```
    Port 111
    ```
    
- Guardar (`CTRL+X`, `Y`, `ENTER`).

### **2. Reiniciar el servicio SSH**

```bash
sudo systemctl restart ssh
```

### **3. Verificar que SSH está corriendo en el nuevo puerto**

```bash
sudo systemctl status ssh
```

### **4. Volver a escanear con Nmap**

```bnmap -p- -sS -sC -sV --min-rate=5000 -n -vvv -Pn 192.168.0.108
```

- SSH **ya no estará en el puerto 22**, sino en **111**.

---

## **6️⃣ Atacar el nuevo puerto con Hydra**

```bash
hydra -l jeremyserver -P /usr/share/wordlists/rockyou.txt.gz ssh://192.168.0.108 -s 111
```

### **Explicación adicional:**

- **`-s 111`** → Especifica el **nuevo puerto SSH (111)**.

✔️ **Hydra sigue funcionando, pero ahora en el puerto 111.**

---

## **7️⃣ Instalar y configurar Fail2Ban para bloquear ataques**

### **1. Instalar Fail2Ban**

```bash
sudo apt install fail2ban -y
```

### **2. Configurar Fail2Ban para SSH**

```bash
sudo nano /etc/fail2ban/jail.local
```

- Agregar la configuración:
    
    ```
    [sshd]
    enable = true
    port = 111
    maxretry = 5
    bantime = 600
    findtime = 600
    ```
    
- Guardar (`CTRL+X`, `Y`, `ENTER`).

### **3. Reiniciar Fail2Ban**

```bash
sudo systemctl restart fail2ban
sudo systemctl status fail2ban
```

---

## **8️⃣ Probar Fail2Ban con Hydra**

4. **Volver a lanzar Hydra:**
    
    ```bash
    hydra -l jeremyserver -P /usr/share/wordlists/rockyou.txt.gz ssh://192.168.0.108 -s 111
    ```
    
5. **Después de 5 intentos fallidos, aparece el error:**
    
    ```
    [ERROR] could not connect to ssh://192.168.0.108:111 - Connection refused
    ```
    

✔️ **La IP de Kali ha sido bloqueada por Fail2Ban.**

---

## **9️⃣ Verificar y gestionar las IPs bloqueadas**

### **1. Revisar el estado de Fail2Ban**

```bash
sudo fail2ban-client status sshd
```

✔️ **Muestra cuántas IPs han sido baneadas.**

### **2. Desbloquear una IP manualmente**

```bash
sudo fail2ban-client set sshd unbanip 192.168.0.120
```

✔️ **Si devuelve `0`, significa que la IP ha sido desbloqueada.**

### **3. Listar todos los servicios protegidos por Fail2Ban**

```bash
sudo fail2ban-client status
```

---

## **🔹 Conclusión**

- **ANTES:**
    - SSH estaba en el puerto **22** y vulnerable a ataques de fuerza bruta.
    - Hydra pudo descubrir la contraseña fácilmente.
- **DESPUÉS:**  
    ✅ Se **cambió el puerto SSH a 111** para mayor seguridad.  
    ✅ Se **instaló Fail2Ban**, que **bloquea IPs maliciosas** tras 5 intentos fallidos.  
    ✅ Hydra ya **no puede hacer ataques**, y la seguridad del servidor ha mejorado significativamente.

---

🎯 **¡Servidor más seguro!** Ahora tienes un **entorno bien protegido** contra ataques básicos de fuerza bruta. 🚀🔐



**[[2- Gestión de Grupos]]**
[[2- Protección del Protocolo FTP]]
[[5- Cómo Crear un Servidor SSH con OPENSSH]]
**[[6- Gestión de Usuarios en Linux]]**
**[[11- Automatizar la Gestión de Usuarios en Linux]]**

---

## Navegación

- ⬆️ Carpeta: [[_10- Securización de Servidores Linux (EN DESARROLLO)|10- Securización de Servidores Linux (EN DESARROLLO)]]
- ➡️ Siguiente: [[2- Protección del Protocolo FTP]]
