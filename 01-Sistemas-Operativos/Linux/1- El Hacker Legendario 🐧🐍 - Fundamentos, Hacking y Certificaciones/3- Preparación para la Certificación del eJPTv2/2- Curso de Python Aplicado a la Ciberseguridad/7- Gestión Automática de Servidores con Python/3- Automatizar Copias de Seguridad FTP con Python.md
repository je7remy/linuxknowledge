
---

#FTP #Python #archivos #backup

---

1. **Importación de módulos necesarios:**
    
    ```python
    from ftplib import FTP  # Importa la clase FTP para la conexión FTP
    import zipfile  # Importa el módulo zipfile para manejar archivos zip
    import os  # Importa el módulo os para interactuar con el sistema operativo
    ```
    
2. **Solicitar credenciales de usuario FTP:**
    
    ```python
    usuario = input('Introduce tu usuario FTP:')
    contraseña = input('Introduce la contraseña:')
    ```
    
3. **Definición de variables:**
    
    ```python
    zip_name = 'scripts.zip'  # Nombre del archivo zip a crear
    extensiones_scripts = ('.sh', '.py')  # Extensiones de archivos a incluir en el zip
    ```
    
4. **Crear archivo zip con scripts:**
    
    ```python
    with zipfile.ZipFile(zip_name, 'w') as ziparchivo:
        for archivo in os.listdir():
            if archivo.endswith(extensiones_scripts):
                ziparchivo.write(archivo)
    ```
    
    - Este bloque crea un archivo zip llamado `scripts.zip` y añade todos los archivos con extensiones `.sh` y `.py` del directorio actual al zip.
5. **Establecer conexión FTP y subir archivo:**
    
    ```python
    try:
        ftp = FTP('192.168.129.25')  # Conectar al servidor FTP
        ftp.login(user=usuario, passwd=contraseña)  # Iniciar sesión con las credenciales proporcionadas
    
        with open(zip_name, 'rb') as file:
            ftp.storbinary(f'STOR {zip_name}', file)  # Subir el archivo zip al servidor FTP
            print("Copia de seguridad subida exitosamente")
    
    except Exception as e:
        print(f"Error: {e}")
    
    finally:
        ftp.quit()  # Cerrar la conexión FTP
    ```
    
    - Intenta conectar al servidor FTP con la IP `192.168.129.25` y las credenciales ingresadas.
    - Abre el archivo zip en modo lectura binaria y lo carga al servidor FTP.
    - Cierra la conexión FTP al finalizar.


```python
from ftplib import FTP
import zipfile
import os

usuario = input('Introduce tu usuario FTP:')
contraseña = input('Introduce la contraseña:')

zip_name = 'scripts.zip'
extensiones_scripts = ('.sh', '.py')

with zipfile.ZipFile(zip_name, 'w') as ziparchivo:
    for archivo in os.listdir():
        if archivo.endswith(extensiones_scripts):
            ziparchivo.write(archivo)

try:
    ftp = FTP('192.168.129.25')
    ftp.login(user=usuario, passwd=contraseña)
    
    with open(zip_name, 'rb') as file:
        ftp.storbinary(f'STOR {zip_name}', file)
        print("Copia de seguridad subida exitosamente")

except Exception as e:
    print(f"Error: {e}")

finally:
    ftp.quit()
```


----



[[3- Gestión y Automatización de Servidores FTP – PARTE 1]]
[[4- Gestión y Automatización de Servidores FTP – PARTE 2]]