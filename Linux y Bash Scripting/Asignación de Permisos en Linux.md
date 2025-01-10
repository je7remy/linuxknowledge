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