### **1. Preparación en el Servidor Ubuntu**

#### **1.1. Actualiza el sistema**

```bash
sudo apt update && sudo apt upgrade -y
```

#### **1.2. Instala `net-tools` (opcional)**

Para usar `ifconfig` si no está disponible:

```bash
sudo apt install net-tools
```

#### **1.3. Instala vsftpd**

```bash
sudo apt install vsftpd -y
```

---

### **2. Configuración Básica del Servidor FTP**

#### **2.1. Inicia el servicio vsftpd**

```bash
sudo systemctl start vsftpd
```

#### **2.2. Verifica el estado del servicio**

Asegúrate de que vsftpd está corriendo:

```bash
systemctl status vsftpd
```

El estado debería indicar que el servicio está activo.

#### **2.3. Configura vsftpd**

Abre el archivo de configuración:

```bash
sudo nano /etc/vsftpd.conf
```

- Busca y **descomenta** (elimina el `#`) las siguientes líneas para permitir la escritura:
    
    ```
    write_enable=YES
    ```
    
    Esto permite a los usuarios autenticados subir archivos al servidor.
    
- Opcionalmente, asegúrate de que las siguientes configuraciones también están habilitadas o ajustadas según tus necesidades:
    
    ```
    local_enable=YES      # Permite a los usuarios locales iniciar sesión.
    chroot_local_user=YES # Restringe a los usuarios a su directorio home.
    ```
    

Guarda y cierra el archivo con **CTRL+O** y luego **CTRL+X**.

#### **2.4. Reinicia vsftpd**

Aplica los cambios reiniciando el servicio:

```bash
sudo systemctl restart vsftpd
```

---

### **3. Configuración de Red y Conexión**

#### **3.1. Verifica la dirección IP del servidor**

Usa `ifconfig` o `ip` para obtener la IP del servidor Ubuntu:

```bash
ifconfig
```

Busca la dirección IP en la interfaz de red activa, como `eth0` o `ens33` (por ejemplo: `192.168.0.114`).

#### **3.2. Configura el firewall (opcional)**

Si tienes habilitado el firewall, permite el tráfico FTP (puerto 21):

```bash
sudo ufw allow 21
sudo ufw reload
```

---

### **4. Conexión desde Kali Linux**

#### **4.1. Verifica la conectividad**

Desde Kali, verifica que puedes llegar al servidor Ubuntu:

```bash
ping 192.168.0.114
```

#### **4.2. Conéctate al servidor FTP**

Utiliza el cliente FTP para conectarte:

```bash
ftp 192.168.0.114
```

- Ingresa un nombre de usuario válido en el servidor Ubuntu.
- Introduce la contraseña cuando se solicite.

#### **4.3. Sube un archivo al servidor**

1. Crea un archivo en Kali Linux para probar:
    
    ```bash
    echo "Hola desde Kali" > hola.txt
    ```
    
2. En la sesión FTP, sube el archivo:
    
    ```bash
    put hola.txt
    ```
    

#### **4.4. Verifica el archivo en el servidor**

En el servidor Ubuntu, navega al directorio del usuario donde se subió el archivo y verifica su presencia:

```bash
ls -l
cat hola.txt
```

---

### **5. Opcional: Verificar la Seguridad**

- **Asegura el acceso limitado a usuarios específicos**: Edita `/etc/vsftpd.user_list` para permitir solo a ciertos usuarios conectarse al servidor.
- **Habilita FTPS** (FTP con TLS): Configura certificados SSL/TLS para cifrar las conexiones.

Con estos pasos, tendrás un servidor FTP funcional utilizando **vsftpd** en Ubuntu, y podrás acceder y transferir archivos desde Kali Linux. 🚀


# **1. Instalación mas realista**

### **1. Instala `net-tools`**

```bash
sudo apt install net-tools
```

---

### **2. Instala el servidor FTP `vsftpd`**

```bash
sudo apt install vsftpd
```

---

### **3. Inicia el servicio `vsftpd`**

```bash
sudo systemctl start vsftpd
```

---

### **4. Verifica el estado del servicio**

```bash
systemctl status vsftpd
```

---

### **5. Conéctate al servidor FTP desde otra máquina (como Kali Linux)**

```bash
ftp 192.168.0.114
```

---

### **6. Edita la configuración de vsftpd**

Abre el archivo de configuración:

```bash
sudo nano /etc/vsftpd.conf
```

Busca y descomenta (elimina el `#`) la línea:

```plaintext
write_enable=YES
```

Guarda los cambios y sal del editor (CTRL+O, ENTER, CTRL+X).

---

### **7. Reinicia el servicio `vsftpd`**

```bash
sudo systemctl restart vsftpd
```

---

### **8. Sube un archivo al servidor FTP**

1. En el cliente FTP (por ejemplo, conectado desde Kali Linux), sube un archivo:
    
    ```bash
    put hola.txt
    ```
    
2. Lista los archivos en el servidor para verificar la subida:
    
    ```bash
    ls
    ```
    

---

Estos comandos configuran el servidor FTP, habilitan la escritura, y permiten la transferencia de archivos entre sistemas.