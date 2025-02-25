
---

#SSH #Seguridad #Redes #ConexiónSegura #AdministraciónRemota #OpenSSH #Linux #ComandosLinux #Ciberseguridad #SeguridadInformática #ConexiónRemota #ConfiguraciónSSH #Servidores #Ubuntu #RedesSeguras #Privacidad #Autenticación

---
**Definición y explicación de comandos:**

- **SSH (Secure Shell):**  
    Es un protocolo que permite la conexión remota segura entre sistemas mediante la encriptación de datos. SSH es comúnmente usado para administrar servidores, transferir archivos, y ejecutar comandos de forma remota.

**Comandos:**

1. **Instalación del servidor SSH:**
    
    ```bash
    sudo apt install openssh-server
    ```
    
    - Este comando instala el servicio OpenSSH en el sistema, habilitando conexiones SSH.
    - **`sudo`**: Permite ejecutar el comando con privilegios de administrador.
    - **`apt install`**: Comando para instalar paquetes en distribuciones basadas en Debian.
    - **`openssh-server`**: El paquete que contiene el servidor SSH.
    
2. **Iniciar el servicio SSH**: Asegúrate de que el servicio esté activo:
    
    ```bash
    sudo systemctl start ssh
    sudo systemctl enable ssh
    ```
    
3. **Verificar el estado del servicio SSH**: Comprueba que el servidor SSH está corriendo:
    
    ```bash
    sudo systemctl status ssh
    ```
    
    
4. **Conexión a un servidor SSH:**
    
    ```bash
    ssh jeremyserver@192.168.1.106
    ```
    
    - **`ssh`**: Comando para iniciar una conexión SSH.
    - **`jeremyserver`**: Nombre de usuario en el servidor al que te conectarás.
    - **`192.168.1.106`**: Dirección IP del servidor al que deseas conectarte.
    
    **Nota:** Se te pedirá una contraseña para autenticarte si no se han configurado claves públicas/privadas.



[[1- Protección del Protocolo SSH]]
[[2- Protección del Protocolo FTP]]
