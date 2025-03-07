
---

#SCP #TransferenciaDeArchivos #Automatización #BashScript #Ciberseguridad #SSH #AdministraciónDeSistemas #Linux #BackupAutomatizado #ScriptDeBash #GestiónDeArchivos #ComandosLinux #CopiasDeSeguridad #AutomatizaciónLinux #ComandosDeSistemas

---
### **Comando SCP**

`scp script.sh jeremyserver@192.168.43.106:/home/jeremyserver/Desktop`

1. **scp**: Es un comando para copiar archivos entre computadoras a través de SSH.
2. **`script.sh`**: Es el archivo que deseas transferir.
3. **`jeremyserver@192.168.43.106`**: Es el usuario y la dirección IP del servidor remoto.
4. **`/home/jeremyserver/Desktop`**: Es la ruta de destino donde se copiará el archivo en el servidor.

---

### **Script Bash**

El script realiza las siguientes acciones:

1. **Define variables clave:**
    
    - `zip_file="escritorio.zip"`: El nombre del archivo comprimido.
    - `ssh_user="jeremyserver"`: El usuario del servidor SSH.
    - `ssh_server="192.168.43.106"`: La dirección IP del servidor SSH.
    - `remote_path="/home/jeremyserver/Desktop"`: La ruta de destino en el servidor remoto.
2. **Comprime todos los archivos y directorios en un archivo ZIP llamado `escritorio.zip`:**
    
    ```bash
    zip -r "$zip_file" .
    ```
    
    - `-r`: Comprime de manera recursiva todos los archivos y subdirectorios.
    - `"."`: Indica que se comprimirá el contenido del directorio actual.
3. **Transfiere el archivo ZIP al servidor remoto:**
    
    ```bash
    scp "$zip_file" "$ssh_user@$ssh_server:$remote_path"
    ```
    
    - Utiliza el comando `scp` para enviar `escritorio.zip` al directorio especificado en el servidor remoto.
4. **Verifica si la transferencia fue exitosa:**
    
    ```bash
    if [ $? -eq 0 ]; then
        echo "La operacion fue un exito"
    else
        echo "Fatal, hubo un error"
    fi
    ```
    
    - `$?`: Devuelve el código de salida del último comando ejecutado (en este caso, `scp`).
    - `-eq 0`: Indica que la operación fue exitosa (código de salida 0).
5. **Elimina el archivo ZIP local:**
    
    ```bash
    rm "$zip_file"
    ```
    
    - Borra el archivo comprimido del sistema local para liberar espacio o evitar duplicados.

---

### **Resumen**

1. **Comprime el contenido actual en un archivo llamado `escritorio.zip`.**
2. **Envía el archivo al servidor remoto utilizando `scp`.**
3. **Muestra un mensaje de éxito o error según el resultado de la transferencia.**
4. **Elimina el archivo ZIP local para limpiar el entorno.**

Este flujo asegura que los archivos se transfieran de manera eficiente y limpia.

### Codigos Completos

```bash
scp script.sh jeremyserver@192.168.43.106:/home/jeremyserver/Desktop
````

```bash
#!/bin/bash

zip_file="escritorio.zip"

ssh_user="jeremyserver"
ssh_server="192.168.43.106"

remote_path="/home/jeremyserver/Desktop"

zip -r "$zip_file" .

scp "$zip_file" "$ssh_user@$ssh_server:$remote_path"

if [ $? -eq 0 ]; then
       echo "La operacion fue un exito"
else
       echo "Fatal, hubo un error"
fi

rm "$zip_file"
````








[[6- Acceso Automatizado SSH Importando Clave Pública]]
[[5- Automatizar conexión SSH y Ejecución de Comandos con Python]]
[[11- Automatizar la Gestión de Usuarios en Linux]]
