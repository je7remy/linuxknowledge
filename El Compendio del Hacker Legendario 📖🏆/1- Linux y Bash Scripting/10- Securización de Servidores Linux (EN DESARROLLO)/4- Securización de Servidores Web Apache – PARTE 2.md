
---

#Apache #SeguridadWeb #Linux #ServidorWeb #ConfiguraciónApache #Ciberseguridad #SecurizaciónDeServidores #DocumentRoot #ConfiguraciónDeApache #SeguridadDeArchivos #ApacheSecurity #LinuxCommands #ServidorSeguro #ProtecciónWeb #ConfiguraciónServidor #Apache2 #AdministraciónDeServidores

---
#### **1. Configuración Inicial**

Primero, accedí al servidor web y realicé algunos cambios en la estructura de archivos:

```bash
sudo su
cd /var/www/html/
mkdir public
mv index.html public/
```

✔️ Creé el directorio `public/` y moví `index.html` dentro.

#### **2. Verificación en el Navegador**

Abrí `http://localhost` en el navegador y me di cuenta de que **`password.txt` seguía expuesto**, a pesar de haber movido `index.html` a `public/`.

#### **3. Edición del Archivo de Configuración de Apache**

Sabía que Apache seguía sirviendo el contenido de `/var/www/html/`, así que entré a la configuración y edité `000-default.conf`:

```bash
cd /etc/apache2/sites-available/
nano 000-default.conf
```

Modifiqué `DocumentRoot` para que solo sirviera el contenido de `public/`:

```apache
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html/public

    <Directory /var/www/html/public>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

✔️ Con esto, Apache ya no debería exponer archivos fuera de `public/`.

#### **4. Activación del Sitio y Reinicio de Apache**

Después, habilité la configuración y ajusté permisos:

```bash
a2ensite 000-default.conf
chown -R www-data:www-data public/
chmod -R 755 public/
sudo systemctl restart apache2
```

✔️ Apache quedó configurado para servir solo desde `public/`... **pero `password.txt` seguía visible**.

#### **5. Solución del Problema: `password.txt` Seguía Expuesto**

Sabía que algo no estaba bien, así que revisé las posibles causas y solucioné lo siguiente:

1. **El archivo `password.txt` seguía en `/var/www/html/`**  
    Como Apache aún podía acceder a él, lo eliminé:
    
    ```bash
    rm /var/www/html/password.txt
    ```
    
2. **El navegador tenía la página en caché**  
    Probé en una ventana de incógnito y recargué con `Ctrl + Shift + R`.
    
3. **Verifiqué que la configuración de Apache estuviera bien aplicada**
    
    ```bash
    apachectl configtest
    ```
    
    ✔️ No había errores.
    
4. **Deshabilité el listado de archivos (`Indexes`) en `/var/www/html/`**  
    Para evitar que Apache mostrara archivos si `index.html` no estaba presente:
    
    ```apache
    <Directory /var/www/html>
        Options -Indexes
        AllowOverride None
    </Directory>
    ```
    
5. **Reinicié Apache para aplicar los cambios**
    
    ```bash
    sudo systemctl restart apache2
    ```
    

#### **6. Verificación Final**

Volví a abrir `http://localhost` en el navegador y esta vez **solo se mostraba `index.html` dentro de `public/`**.

### ✅ **Conclusión**

El problema era que Apache seguía accediendo a `password.txt` en su `DocumentRoot` original. Eliminé el archivo, deshabilité `Indexes` y reinicié el servicio para asegurarme de que solo sirviera el contenido de `public/`. Ahora todo funciona correctamente.







[[3- Securización de Servidores Web Apache – PARTE 1]]
[[5- Securización de Servidores Web Apache – Restricción de Acceso a Archivos – PARTE 3]]
[[6- Securización de Servidores Web Apache – Evitar Ataques de Fuzzing Web – PARTE 4]]