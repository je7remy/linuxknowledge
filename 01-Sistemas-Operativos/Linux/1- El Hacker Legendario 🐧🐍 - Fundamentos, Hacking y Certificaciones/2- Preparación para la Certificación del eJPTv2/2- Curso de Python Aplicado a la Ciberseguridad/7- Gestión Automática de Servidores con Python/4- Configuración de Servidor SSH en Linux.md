
---

#Linux #SSH #OpenSSH #Sistema #Seguridad #Configuración #Servidor #Nano #ConexiónRemota

---


### **Paso 1: Instalar el servidor OpenSSH**

```bash
sudo apt install openssh-server
```

- `sudo` → Ejecuta el comando con permisos de superusuario.
- `apt install` → Instala paquetes desde el repositorio de Ubuntu/Debian.
- `openssh-server` → Es el paquete que permite conexiones SSH entrantes.

---

### **Paso 2: Verificar el estado del servicio SSH**

```bash
sudo systemctl status ssh
```

- `systemctl` → Controla los servicios en sistemas con `systemd`.
- `status ssh` → Muestra si el servicio SSH está en ejecución, detenido o con errores.

---

### **Paso 3: Iniciar el servicio SSH**

```bash
sudo systemctl start ssh
```

- `start ssh` → Inicia el servidor SSH si no está corriendo.

---

### **Paso 4: Habilitar SSH para que inicie automáticamente**

```bash
sudo systemctl enable ssh
```

- `enable ssh` → Configura SSH para iniciarse automáticamente en cada arranque del sistema.

---

### **Paso 5: Conectarse a una máquina remota vía SSH**

```bash
ssh kali@192.168.0.113
```

- `ssh` → Cliente SSH para conectarse a otro equipo.
- `kali@192.168.0.113` → Usuario y dirección IP del equipo remoto.

---

### **Paso 6: Listar archivos en la máquina remota**

```bash
ls
```

- `ls` → Lista los archivos y directorios en la carpeta actual.

---

### **Paso 7: Crear y editar un archivo de texto**

```bash
nano hola.txt
```

- `nano` → Editor de texto en terminal.
- `hola.txt` → Archivo de texto que se creará o editará.

---

### **Paso 8: Escribir en el archivo y guardarlo**

```plaintext
hola
```

- Se escribe el contenido del archivo (`hola`).

**Guardar y salir:**

- `Ctrl + O` → Guarda los cambios en el archivo.
- `Ctrl + X` → Sale del editor `nano`.

---




[[2- Puertos Principales]]
[[5- Cómo Crear un Servidor SSH con OPENSSH]]
[[1- Protección del Protocolo SSH]]
