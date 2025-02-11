
---

#Bash #ShellScript #Automatización #Linux #FTP #SeguridadInformática #SysAdmin #Backup #Ciberseguridad #Curl

---

### Análisis del Script

```bash

#!/bin/bash

# Crear las carpetas si no existen

mkdir -p imagenes videos documentos

# Iterar sobre cada archivo en el directorio actual

for archivo in *

do

# Obtener el nombre base del archivo sin la ruta

nombre_base=$(basename "$archivo")

# Obtener la extencion del archivo utilizando awk

extension=$(echo "$nombre_base" | awk -F '.' '{print $NF}')

# Mover el archivo a la carpeta correspondiente segun su extension

case "$extension" in

jpg|png)

mv "$archivo" imagenes/

echo "Movido $archivo a la carpeta imagenes"

;;

mp4|mkv)

mv "$archivo" videos/

echo "Movido $archivo a la carpeta videos"

;;

pdf|docx)

mv "$archivo" documentos/

echo "Movido $archivo a la carpteta documentos"

;;

*)

echo "Archivo $archivo no se movio, extension desconocida: $extension"

esac

done

zip -r copia_seguridad.zip imagenes/ videos/ documentos/

servidor='192.168.1.106'

usuario='jeremyserver'

clave='11262372'

ruta_archivo_local=copia_seguridad.zip

archivo_remoto='/home/jeremyserver/copia_seguridad.zip'

curl -u "$usuario:$clave" -T "$ruta_archivo_local" ftp://$servidor/$archivo_remoto

```
#### 1. **Creación de Carpetas**

```bash
mkdir -p imagenes videos documentos
```

- Crea las carpetas `imagenes`, `videos` y `documentos` si no existen.

#### 2. **Iteración sobre Archivos**

```bash
for archivo in *
```

- Itera sobre todos los archivos en el directorio actual.

#### 3. **Obtención del Nombre y Extensión**

```bash
nombre_base=$(basename "$archivo")
extension=$(echo "$nombre_base" | awk -F '.' '{print $NF}')
```

- `basename` extrae el nombre del archivo sin la ruta.
- `awk` divide el nombre en partes usando `.` como separador y toma la última parte (la extensión).

#### 4. **Mover Archivos según su Extensión**

```bash
case "$extension" in
  jpg|png)
     mv "$archivo" imagenes/
     echo "Movido $archivo a la carpeta imagenes"
    ;;
  mp4|mkv)
     mv "$archivo" videos/
     echo "Movido $archivo a la carpeta videos"
    ;;
  pdf|docx)
     mv "$archivo" documentos/
     echo "Movido $archivo a la carpeta documentos"
    ;;
  *)
    echo "Archivo $archivo no se movió, extensión desconocida: $extension"
esac
```

- Clasifica los archivos según su extensión y los mueve a la carpeta correspondiente.
- Si la extensión no coincide con ningún caso, muestra un mensaje de error.

#### 5. **Creación de un Archivo de Respaldo**

```bash
zip -r copia_seguridad.zip imagenes/ videos/ documentos/
```

- Comprime las carpetas `imagenes`, `videos` y `documentos` en un archivo ZIP llamado `copia_seguridad.zip`.

#### 6. **Subida al Servidor FTP**

La configuración de FTP en el script utiliza el comando `curl`, que es una herramienta versátil para transferir datos a través de varios protocolos, incluido FTP.

```bash
servidor='192.168.1.106'
usuario='jeremyserver'
clave='11262372'

ruta_archivo_local=copia_seguridad.zip
archivo_remoto='/home/jeremyserver/copia_seguridad.zip'

curl -u "$usuario:$clave" -T "$ruta_archivo_local" ftp://$servidor/$archivo_remoto
```

- Define los datos del servidor FTP.
- Usa `curl` para subir el archivo `copia_seguridad.zip` al directorio especificado.

- **`servidor`**: Es la dirección IP o el nombre de dominio del servidor FTP.
    
    - Ejemplo: `192.168.1.106` o `ftp.miservidor.com`.
    
- **`usuario`**: El nombre de usuario para autenticarse en el servidor FTP.
    
- **`clave`**: La contraseña asociada con el usuario FTP.
    
- **`ruta_archivo_local`**: Especifica el archivo local que se desea subir.
    
- **`archivo_remoto`**: Define la ruta en el servidor donde se almacenará el archivo. Debe incluir el nombre del archivo.
    

---

#### **Comando curl para Subir Archivos**

```bash
curl -u "$usuario:$clave" -T "$ruta_archivo_local" ftp://$servidor/$archivo_remoto
```

1. **`-u "$usuario:$clave"`**:
    
    - Especifica las credenciales de autenticación.
    - Se proporciona en el formato `usuario:contraseña`.
    
1. **`-T "$ruta_archivo_local"`**:
    
    - Indica el archivo local que se subirá al servidor.
    
1. **`ftp://$servidor/$archivo_remoto`**:
    
    - Especifica el protocolo FTP y la ruta destino en el servidor.

---



**[[3- Transferencia de Archivos por la Red]]** 