
---

#Linux #chmod #PermisosLinux #ComandosLinux #SeguridadLinux #AdministraciónDeSistemas #LinuxTips #SistemasUnix #AdministraciónDeArchivos #SeguridadInformática #ComandosBash #LinuxCommands #TerminalLinux #LinuxSysAdmin #PermisosDeArchivos #PermisosDeCarpetas #LinuxSecurity #GestiónDePermisos

---
`chmod` es un comando en sistemas Unix/Linux que sirve para cambiar los **permisos** de archivos o carpetas. Define quién puede **leer (r)**, **escribir (w)** o **ejecutar (x)**.

---

### 1. **`sudo chmod -r documento.txt`**

- **Acción:** Este comando intenta remover el permiso de lectura (`r`) del archivo `documento.txt` para todos los usuarios (propietario, grupo y otros).
- **Resultado:** Ahora el archivo no puede ser leído por ningún usuario.

### 2. **`ls -l`**

- **Acción:** Muestra los permisos actuales del archivo. Los permisos habrán cambiado y ya no incluirán el permiso de lectura (`r`).

### 3. **`cat documento.txt`**

- **Acción:** Intenta mostrar el contenido de `documento.txt`.
- **Resultado:** Falla porque no tienes permiso de lectura sobre el archivo.

---

### 4. **`sudo chmod +r documento.txt`**

- **Acción:** Añade el permiso de lectura (`r`) al archivo para todos los usuarios.
- **Resultado:** Ahora cualquier usuario puede leer el archivo.

### 5. **`ls -l`**

- **Acción:** Vuelve a mostrar los permisos. Ahora los permisos de lectura (`r`) se habrán restaurado.

### 6. **`cat documento.txt`**

- **Acción:** Intenta mostrar el contenido del archivo nuevamente.
- **Resultado:** Esta vez funciona porque el archivo tiene permiso de lectura.

---

### 7. **`sudo chmod -w documento.txt`**

- **Acción:** Remueve el permiso de escritura (`w`) del archivo para todos los usuarios.
- **Resultado:** El archivo no se puede modificar.

### 8. **`ls -l`**

- **Acción:** Muestra los permisos. El permiso de escritura (`w`) estará ausente.

### 9. **`nano documento.txt`**

- **Acción:** Intenta abrir el archivo con el editor `nano`.
- **Resultado:** Puedes abrirlo, pero no podrás guardar cambios porque no tienes permiso de escritura.

---

### 10. **`sudo chmod +w documento.txt`**

- **Acción:** Añade el permiso de escritura (`w`) al archivo para todos los usuarios.
- **Resultado:** Ahora se puede modificar el archivo.

### 11. **`ls -l`**

- **Acción:** Muestra los permisos. El permiso de escritura (`w`) estará presente nuevamente.

### 12. **`nano documento.txt`**

- **Acción:** Abres el archivo con `nano` otra vez.
- **Resultado:** Ahora puedes modificar y guardar cambios porque tienes permiso de escritura.

---

### 13. **`sudo chmod +x documento.sh`**

- **Acción:** Añade el permiso de ejecución (`x`) al archivo `documento.sh`.
- **Resultado:** Ahora puedes ejecutar el archivo como un script.

### 14. **`./documento.sh`**

- **Acción:** Intenta ejecutar el script directamente.
- **Resultado:** Se ejecuta correctamente porque tiene permiso de ejecución.

---

### 15. **`sudo chmod -x documento.sh`**

- **Acción:** Remueve el permiso de ejecución (`x`) del archivo `documento.sh`.
- **Resultado:** Ahora el archivo ya no se puede ejecutar directamente.

### 16. **`bash documento.sh`**

- **Acción:** Intenta ejecutar el archivo usando el intérprete `bash`.
- **Resultado:** Funciona porque no depende del permiso de ejecución (`x`), ya que `bash` se encarga de leer y ejecutar el contenido.

### 17. **`./documento.sh`**

- **Acción:** Intenta ejecutar el script nuevamente directamente.
- **Resultado:** Falla porque el archivo no tiene el permiso de ejecución (`x`).

---

### 18. **`ls -l`**

- **Acción:** Muestra los permisos finales del archivo. Los permisos reflejarán los cambios realizados a lo largo del proceso.

---

En resumen, los comandos `chmod` permiten modificar los permisos de lectura (`r`), escritura (`w`) y ejecución (`x`) de archivos o directorios. A través de estos pasos, se cambió dinámicamente la capacidad de leer, escribir y ejecutar el archivo, lo que afecta cómo puedes interactuar con él.


# Gestión Detallada de Permisos – Comando chmod

### Asignación de Permisos en Linux

1. **`ls -l`**: Lista el contenido del directorio actual con detalles, incluyendo los permisos de los archivos o carpetas.
    
2. **`sudo chmod g-r carpeta`**: Revoca el permiso de lectura para el grupo sobre la carpeta `carpeta`.
    
3. **`sudo chmod g+r carpeta`**: Concede el permiso de lectura para el grupo sobre la carpeta `carpeta`.
    
4. **`sudo chmod g-w carpeta`**: Revoca el permiso de escritura para el grupo sobre la carpeta `carpeta`.
    
5. **`sudo chmod g+w carpeta`**: Concede el permiso de escritura para el grupo sobre la carpeta `carpeta`.
    
6. **`sudo chmod u-r carpeta`**: Revoca el permiso de lectura para el propietario (usuario) sobre la carpeta `carpeta`.
    
7. **`sudo chmod u-wx carpeta`**: Revoca los permisos de escritura y ejecución para el propietario (usuario) sobre la carpeta `carpeta`.
    
8. **`sudo chmod o-x carpeta`**: Revoca el permiso de ejecución para otros usuarios sobre la carpeta `carpeta`.
    
9. **`sudo chmod o-r carpeta`**: Revoca el permiso de lectura para otros usuarios sobre la carpeta `carpeta`.
    

En cada paso, puedes observar cómo cambian los permisos de la carpeta ejecutando nuevamente `ls -l`. Los permisos se muestran en una forma como esta:  
`drwxr-xr--`, donde:

- **d**: Es un directorio.
- **r**: Permiso de lectura.
- **w**: Permiso de escritura.
- **x**: Permiso de ejecución.
- Los 9 caracteres se dividen en 3 bloques:
    - Usuario (dueño): Primeros 3 caracteres.
    - Grupo: Siguientes 3 caracteres.
    - Otros: Últimos 3 caracteres.

### Verificación de permisos:

- **Comando:** `ls -l`
- **Descripción:** Muestra los permisos de archivos y directorios en formato largo.

### Cambiar permisos de un archivo:

- **Comando:** `chmod`
- **Ejemplo:** `chmod u+rwx archivo.txt`
- **Descripción:** Concede permisos de lectura, escritura y ejecución al propietario del archivo «archivo.txt».

### Cambiar permisos para diferentes usuarios/grupos:

- **Comando:** `chmod`
- **Ejemplo:** `chmod g-w archivo.txt`
- **Descripción:** Revoca los permisos de escritura del grupo para el archivo «archivo.txt».

### Cambiar el propietario de un archivo:

- **Comando:** `chown`
- **Ejemplo:** `chown usuario archivo.txt`
- **Descripción:** Cambia el propietario del archivo «archivo.txt» al usuario especificado.

### Cambiar el grupo de un archivo:

- **Comando:** `chown`
- **Ejemplo:** `chown :grupo archivo.txt`
- **Descripción:** Cambia el grupo del archivo «archivo.txt» al grupo especificado.

### Cambiar recursivamente permisos en un directorio:

- **Comando:** `chmod -R`
- **Ejemplo:** `chmod -R u+rwx directorio`
- **Descripción:** Concede permisos de lectura y escritura al propietario y permite la ejecución a directorios dentro de «directorio».

### Cambiar permisos utilizando notación octal:

- **Comando:** `chmod`
- **Ejemplo:** `chmod 755 archivo.sh`
- **Descripción:** Establece permisos específicos utilizando la notación octal (en este caso, 755). Otorga permisos completos (lectura, escritura y ejecución) al propietario del archivo(7), mientras que al grupo(5) y a otros usuarios(5) solo se les otorga permiso de lectura y ejecución, sin permiso de escritura.

### Cambiar el propietario y el grupo simultáneamente:

- **Comando:** `chown`
- **Ejemplo:** `chown usuario:grupo archivo.txt`
- **Descripción:** Cambia el propietario y el grupo del archivo «archivo.txt» al usuario y grupo especificados.


# Gestión de Permisos con números – Comando chmod
### Gestión de Permisos Linux con Números


-----------

#bash

-------------

- 4 Representa todos los permisos de lectura (r)
- 2 Representa todos los permisos de escritura (w)
- 1 Representa todos los permisos de ejecucion (x)

---------------------

- Ahora ya podemos dar permisos sumando los numeros de los permisos que queramos dar es decir si tenemos permisos 400 estariamos dando permisos de escritura 600 serian de lectura  y 700 serian todos los permisos para el usuario. 

- Todo esto se hace sumando los numeros que hemos puesto al principio

- Si queremos ir dando permisos a los grupos y a otros simplemente tendríamos que ir donde hemos puesto un 0 modificarlo por el numero de permisos que queremos para ese apartado. 

---

### **1. `sudo chmod 777 carpeta`**

- **Significado:**
    - `777` otorga **todos los permisos** a **propietario**, **grupo** y **otros**.
    - Permisos: **rwxrwxrwx**.
- **Efecto:**
    - La carpeta será **completamente accesible** por cualquier usuario del sistema.
- **`ls -l`:**
    
    ```bash
    drwxrwxrwx  2 user group 4096 Jan 12 10:00 carpeta
    ```
    

---

### **2. `sudo chmod 000 carpeta`**

- **Significado:**
    - `000` quita **todos los permisos** a **propietario**, **grupo** y **otros**.
    - Permisos: **---------**.
- **Efecto:**
    - Nadie puede leer, escribir ni acceder a la carpeta (ni siquiera el propietario sin usar `sudo`).
- **`ls -l`:**
    
    ```bash
    d---------  2 user group 4096 Jan 12 10:00 carpeta
    ```
    

---

### **3. `sudo chmod 400 carpeta`**

- **Significado:**
    - `400` otorga solo **permiso de lectura** al **propietario**.
    - Permisos: **r--------**.
- **Efecto:**
    - Solo el propietario puede leer la carpeta; no puede escribir ni acceder a su contenido.
- **`ls -l`:**
    
    ```bash
    dr--------  2 user group 4096 Jan 12 10:00 carpeta
    ```
    

---

### **4. `sudo chmod 600 carpeta`**

- **Significado:**
    - `600` otorga **lectura y escritura** al **propietario**, pero ningún permiso a **grupo** u **otros**.
    - Permisos: **rw-------**.
- **Efecto:**
    - El propietario puede leer y escribir, pero otros no tienen acceso.
- **`ls -l`:**
    
    ```bash
    drw-------  2 user group 4096 Jan 12 10:00 carpeta
    ```
    

---

### **5. `sudo chmod 700 carpeta`**

- **Significado:**
    - `700` otorga **todos los permisos** (lectura, escritura y ejecución) al **propietario**, pero ningún permiso a **grupo** u **otros**.
    - Permisos: **rwx------**.
- **Efecto:**
    - Solo el propietario puede acceder, modificar y navegar la carpeta.
- **`ls -l`:**
    
    ```bash
    drwx------  2 user group 4096 Jan 12 10:00 carpeta
    ```
    

---

### **6. `sudo chmod 720 carpeta`**

- **Significado:**
    - `720` otorga:
        - **rwx** al **propietario**.
        - **w--** al **grupo**.
        - Sin permisos para **otros**.
    - Permisos: **rwx-w----**.
- **Efecto:**
    - El propietario tiene control total, el grupo puede escribir (pero no leer ni ejecutar), y otros no tienen acceso.
- **`ls -l`:**
    
    ```bash
    drwx-w----  2 user group 4096 Jan 12 10:00 carpeta
    ```
    

---

### **7. `sudo chmod 730 carpeta`**

- **Significado:**
    - `730` otorga:
        - **rwx** al **propietario**.
        - **rwx** al **grupo**.
        - Sin permisos para **otros**.
    - Permisos: **rwxrwx---**.
- **Efecto:**
    - El propietario y el grupo tienen control total, pero otros no tienen acceso.
- **`ls -l`:**
    
    ```bash
    drwxrwx---  2 user group 4096 Jan 12 10:00 carpeta
    ```
    

---

### **8. `sudo chmod 732 carpeta`**

- **Significado:**
    - `732` otorga:
        - **rwx** al **propietario**.
        - **rwx** al **grupo**.
        - **-w-** a **otros**.
    - Permisos: **rwxrwx-w-**.
- **Efecto:**
    - El propietario y el grupo tienen control total, mientras que otros solo pueden escribir (pero no leer ni ejecutar).
- **`ls -l`:**
    
    ```bash
    drwxrwx-w-  2 user group 4096 Jan 12 10:00 carpeta
    ```



[[8- Permisos Especiales – Sticky Bit]]
[[9- Permisos Especiales – BIt SUID]] 
