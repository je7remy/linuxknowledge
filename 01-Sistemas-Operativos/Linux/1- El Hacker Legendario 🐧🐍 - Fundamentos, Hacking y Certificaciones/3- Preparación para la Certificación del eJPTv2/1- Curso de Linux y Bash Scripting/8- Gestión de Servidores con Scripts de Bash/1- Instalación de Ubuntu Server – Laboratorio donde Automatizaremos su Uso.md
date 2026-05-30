---
tipo: laboratorio
tags: [ejptv2, el-hacker-legendario, linux, bash, laboratorio]
actualizado: 2026-05-28
---

# Instalación de Ubuntu Server – Laboratorio donde Automatizaremos su Uso
Para instalar **Ubuntu Server 24.04.1 LTS** en una máquina virtual utilizando VirtualBox, sigue estos pasos detallados:

---

### **1. Descarga de Ubuntu Server**

- Ve al sitio oficial de [Ubuntu Server](https://ubuntu.com/download/server) y descarga la imagen ISO para la versión 24.04.1 LTS.
- Verifica la integridad del archivo utilizando el checksum SHA256 proporcionado en la página.

---

### **2. Instalación de VirtualBox**

- Descarga e instala VirtualBox desde su [sitio oficial](https://www.virtualbox.org/).
- Instala también las **Guest Additions** para un mejor rendimiento de la VM más adelante.

---

### **3. Configuración de la Máquina Virtual**

1. **Crea una nueva VM**:
    
    - Abre VirtualBox y haz clic en **"Nueva"**.
    - Asigna un nombre (por ejemplo, `Ubuntu Server 24.04`).
    - **Tipo**: Linux.
    - **Versión**: Ubuntu (64-bit).
    - Haz clic en **"Siguiente"**.
2. **Configura la memoria RAM**:
    
    - Asigna al menos 2 GB (2048 MB) de RAM para un entorno básico (recomendado 4 GB o más para tareas avanzadas).
3. **Crea un disco duro virtual**:
    
    - Selecciona **"Crear un disco duro virtual ahora"**.
    - Formato: **VDI (VirtualBox Disk Image)**.
    - Asignación: **Dinamicamente asignado**.
    - Tamaño: Al menos **20 GB** (más si planeas instalar paquetes adicionales).
4. **Configuración de Red**:
    
    - Por defecto, la red estará configurada como NAT. Si necesitas acceso directo a la red local, cambia el adaptador de red a **"Bridged"** en la configuración de la VM después de crearla.

---

### **4. Monta la ISO de Ubuntu Server**

1. Selecciona la máquina virtual creada y haz clic en **"Configuración"**.
2. Ve a **"Almacenamiento"**.
3. En el controlador **IDE**, haz clic en el icono de disco y selecciona **"Elegir un archivo de disco"**.
4. Selecciona la imagen ISO de Ubuntu Server que descargaste.
5. Haz clic en **"Aceptar"**.

---

### **5. Inicio e Instalación de Ubuntu Server**

1. Selecciona la VM y haz clic en **"Iniciar"**.
2. Sigue las instrucciones en pantalla:
    - Selecciona el idioma y la distribución del teclado.
    - Configura la red automáticamente con DHCP o de forma manual si es necesario.
    - Configura el particionado:
        - Opción recomendada: **"Usar disco entero"** (o configurar manualmente).
    - Configura tu usuario:
        - Crea un nombre de usuario y contraseña.
        - Opcionalmente, configura SSH si lo necesitas para accesos remotos.
3. Revisa las configuraciones y comienza la instalación.

---

### **6. Post-Instalación**

1. **Expulsa la ISO**:
    - Ve a la configuración de la VM, selecciona **"Almacenamiento"**, y elimina la ISO montada.
2. Reinicia la VM.
3. Inicia sesión con el usuario y contraseña que configuraste durante la instalación.

---

### **7. Configuración Adicional**

1. **Actualiza el sistema**:
    
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```
    
2. **Instala herramientas opcionales** (como OpenSSH si no lo configuraste durante la instalación):
    
    ```bash
    sudo apt install openssh-server
    ```
    
3. **Configura el cortafuegos**:
    - Habilita el acceso SSH:
        
        ```bash
        sudo ufw allow OpenSSH
        sudo ufw enable
        ```
        
4. **Instala las Guest Additions** (para mejorar el rendimiento y funcionalidad):
    - Inserta la imagen de Guest Additions desde el menú de VirtualBox (**"Dispositivos > Insertar Imagen de CD de Guest Additions"**).
    - Sigue las instrucciones en pantalla para instalarlas.

---

Con estos pasos, tendrás **Ubuntu Server 24.04.1 LTS** instalado y funcionando dentro de VirtualBox. Este entorno es ideal para pruebas, desarrollo, y configuración de servidores. 🚀

---

## Navegación

- ⬆️ Carpeta: [[_8- Gestión de Servidores con Scripts de Bash|8- Gestión de Servidores con Scripts de Bash]]
- ➡️ Siguiente: [[2- Cómo Crear un Servidor FTP con VSFTPD]]
