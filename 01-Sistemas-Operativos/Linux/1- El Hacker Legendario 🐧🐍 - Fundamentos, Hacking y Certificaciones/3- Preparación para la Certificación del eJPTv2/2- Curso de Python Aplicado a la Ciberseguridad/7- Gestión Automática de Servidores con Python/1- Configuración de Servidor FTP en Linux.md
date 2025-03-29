
---

#KaliLinux #vsftpd #FTP #Pentesting #SeguridadInformática #EthicalHacking #AdministraciónDeSistemas

---

1. Instalas vsftpd usando `sudo apt install vsftpd`.
2. Reinicias el servicio vsftpd con `sudo systemctl restart vsftpd`.
3. Desde otra máquina virtual (llamada "víctima"), te conectas al servidor FTP usando `ftp (ip de la máquina víctima)`.
4. Inicias sesión con los credenciales `kali` como usuario y contraseña (en mi caso).
5. Aunque te conectas con éxito, notas que no tienes permisos de escritura.
6. En la máquina víctima, abres el archivo de configuración de vsftpd usando `sudo nano /etc/vsftpd.conf`.
7. Buscas la línea `write` dentro del archivo.
8. Descomentas esta línea cambiándola a `write_enable=yes`.
9. Guardas los cambios en el archivo y sales del editor.
10. Reinicias el servicio vsftpd nuevamente con `sudo systemctl restart vsftpd`.

¡Ahora deberías tener permisos de escritura en tu servidor FTP!

# Enviar y recibir algo

### **1. Conectarse al servidor FTP**

Desde la máquina cliente (Kali Linux), ejecuta:

```bash
ftp [IP_DEL_SERVIDOR]
```

Ejemplo:

```bash
ftp 192.168.1.100
```

Luego, ingresa las credenciales cuando se te soliciten.

---

### **2. Listar archivos en el servidor**

Una vez dentro de la sesión FTP, usa:

```bash
ls
```

Esto mostrará los archivos disponibles en el servidor.

---

### **3. Descargar (Obtener) un archivo desde el servidor FTP**

Para descargar un archivo del servidor a la máquina cliente, usa:

```bash
get [nombre_del_archivo]
```

Ejemplo:

```bash
get documento.txt
```

Esto descargará el archivo `documento.txt` a tu máquina local en el directorio donde ejecutaste `ftp`.

---

### **4. Subir (Enviar) un archivo desde la máquina cliente al servidor**

Para enviar un archivo al servidor FTP, usa:

```bash
put [nombre_del_archivo]
```

Ejemplo:

```bash
put imagen.jpg
```

Esto subirá `imagen.jpg` desde la máquina cliente al servidor.

---

### **5. Salir de la sesión FTP**

Cuando hayas terminado, cierra la conexión con:

```bash
bye
```






[[1- Instalación de Ubuntu Server – Laboratorio donde Automatizaremos su Uso]]
[[2- Cómo Crear un Servidor FTP con VSFTPD]]
[[2- Puertos Principales]]
[[2- Protección del Protocolo FTP]]