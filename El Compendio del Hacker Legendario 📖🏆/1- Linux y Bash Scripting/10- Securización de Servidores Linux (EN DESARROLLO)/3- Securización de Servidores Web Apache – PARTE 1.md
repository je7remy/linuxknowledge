
---

#Linux #Apache #ServidorWeb #SeguridadInformática #SysAdmin #WebSecurity #EthicalHacking #Pentesting #Ciberseguridad #DevOps

---

### 1️⃣ Instalación y ejecución de Apache

```bash
sudo apt install apache2
sudo systemctl start apache2
sudo systemctl status apache2
```

- Se instaló **Apache2**, un servidor web popular.
- Se inició el servicio con `systemctl start apache2`.
- Se verificó su estado con `systemctl status apache2`, asegurándose de que estaba funcionando correctamente.

---

### 2️⃣ Acceso al directorio web y edición de archivos

```bash
cd /var/www/html/
ls
```

- Se cambió al directorio `/var/www/html/`, que es la raíz de Apache.
- `ls` mostró los archivos disponibles, donde se encuentra **index.html**, la página por defecto del servidor.

Después de esto, edite el **index.html**, cambiando su contenido para que refleje la personalización.

---

### 3️⃣ Acceder a la página editada desde el navegador

- Al abrir `http://localhost/`, se vio la página editada, confirmando que Apache está sirviendo el contenido correctamente.

---

### 4️⃣ Creación de archivos y posible vulnerabilidad

```bash
touch password.txt
nano password.txt
```

- Se creó un archivo **password.txt**.
- En el archivo, se escribió un **token** sensible:
    
    ```
    TOKEN=8284838343983983
    ```
    
- Se guardó (`CTRL+O`) y se salió (`CTRL+X`).

---

### 5️⃣ Acceder al archivo desde el navegador

Al abrir `http://localhost/password.txt` en el navegador, el contenido del archivo se mostró directamente.

📌 **Vulnerabilidad detectada**:  
Cualquier usuario con acceso a la URL podría ver el archivo **password.txt**. Esto representa un riesgo si se almacena información confidencial en directorios accesibles públicamente en un servidor web.

---

### 6️⃣ Conclusión y prevención

#### 🔴 **Qué pasó**:

- Apache, por defecto, **sirve cualquier archivo en `/var/www/html/`** si no se restringe el acceso.
- **Se expuso información sensible** porque `password.txt` estaba en un directorio público.

#### ✅ **Cómo prevenirlo**:

1. **No almacenar credenciales en archivos accesibles por Apache.**
2. **Usar permisos adecuados**:
    
    ```bash
    chmod 600 password.txt  # Solo el dueño puede leer y escribir
    ```
    
3. **Restringir acceso en Apache** con `.htaccess`:
    - Crear `/var/www/html/.htaccess` y añadir:
        
        ```
        <Files "password.txt">
        Order allow,deny
        Deny from all
        </Files>
        ```
        
4. **Mover archivos sensibles fuera del directorio web**:
    - Guardar `password.txt` en `/home/user/` en lugar de `/var/www/html/`.

---

📢 **En la próxima lección** podemos cubrir técnicas para proteger servidores web en Kali Linux, como:

- Configurar permisos adecuados.
- Evitar la exposición de archivos sensibles.
- Implementar reglas en Apache para reforzar la seguridad.




**[[3- Transferencia de Archivos por la Red]]** 
**[[4- Cómo Utilizar CURL con HTTP]]**
**[[5- Cómo Utilizar WGET]]**
**[[Protocolo http]]**
[[4- Securización de Servidores Web Apache – PARTE 2]]
[[5- Securización de Servidores Web Apache – Restricción de Acceso a Archivos – PARTE 3]]
**[[6- Securización de Servidores Web Apache – Evitar Ataques de Fuzzing Web – PARTE 4]]**