
---

#SeguridadWeb #ProtecciónDeDatos #Apache #ArchivoEnv #Ciberseguridad #ApacheSecurity #ProtecciónDeCredenciales #SeguridadServidor #SistemasSeguros #AdministraciónDeServidores #SeguridadLinux #ConfiguraciónApache #BuenasPrácticas #AuditoríaDeSeguridad #Hardening #ProtecciónDeArchivos

---
# **Reporte de Seguridad: Protección del Archivo `.env`**

## **Pasos Realizados**

### 1. **Elevación de Privilegios**

- Se ejecutó el comando `sudo su` para obtener privilegios de superusuario.

### 2. **Navegación al Directorio Web**

- Se usó `cd /var/www/html/public` para cambiar al directorio donde se encuentran los archivos públicos del servidor web.

### 3. **Listar Archivos**

- Se usaron los comandos `ls` y `ls -a` para listar los archivos en el directorio, incluyendo los ocultos.

### 4. **Edición del Archivo `.env`**

- Se abrió el archivo `.env` con `nano .env`.
    
- Se configuraron las variables de entorno:

    
    **DATABASE_URL=mysql://kali:11262372@localhost:3306/my_database
    API_KEY=123123123**
    
- Se guardaron los cambios con `CTRL+O` y se salió del editor con `CTRL+X`.

### 5. **Verificación del Archivo `.env`**

- Se utilizó `cat .env` para verificar el contenido del archivo.

### 6. **Acceso al Archivo desde un Navegador**

- Se mencionó que el archivo es accesible vía `http://localhost/.env`, lo cual representa un riesgo de seguridad porque expone credenciales sensibles.

### 7. **Configuración de Seguridad en Apache**

- Se navegó al directorio de configuración de Apache con:
    
    ```sh
    cd /etc/apache2/sites-available/
    ```
    
- Se editó el archivo `000-default.conf` con `nano 000-default.conf` y se agregó la siguiente regla para bloquear el acceso al archivo `.env`:
    
    ```apache
    <Files ".env">
        Require all denied
    </Files>
    ```
    

### 8. **Habilitación del Sitio y Reinicio de Apache**

- Se ejecutó el siguiente comando para activar la nueva configuración:
    
    ```sh
    a2ensite 000-default.conf
    ```
    
- Finalmente, se reinició Apache para aplicar los cambios:
    
    ```sh
    systemctl restart apache2
    ```
    

---

## **Conclusión y Consideraciones de Seguridad**

### **Problema Identificado**

- La exposición del archivo `.env` en `http://localhost/.env` es un riesgo crítico porque contiene credenciales de base de datos y claves API.

### **Solución Implementada**

- Se bloqueó el acceso al archivo `.env` en la configuración de Apache, protegiendo las credenciales.

### **Recomendaciones Adicionales**

1. **Usar Permisos Adecuados:**  
    Asegurar que `.env` solo sea accesible por el usuario del servidor web:
    
    ```sh
    chmod 600 .env
    ```
    
2. **No Exponer Claves Sensibles en el Código:**  
    Utilizar mecanismos de cifrado o variables de entorno a nivel de sistema.
    
3. **Auditar Seguridad Regularmente:**  
    Usar herramientas como `Lynis` o `Nikto` para escanear vulnerabilidades en el servidor.
    

---

**✅ Implementar estas medidas mejora significativamente la seguridad del servidor y protege la información sensible.**







[[3- Securización de Servidores Web Apache – PARTE 1]]
[[4- Securización de Servidores Web Apache – PARTE 2]]
[[6- Securización de Servidores Web Apache – Evitar Ataques de Fuzzing Web – PARTE 4]]