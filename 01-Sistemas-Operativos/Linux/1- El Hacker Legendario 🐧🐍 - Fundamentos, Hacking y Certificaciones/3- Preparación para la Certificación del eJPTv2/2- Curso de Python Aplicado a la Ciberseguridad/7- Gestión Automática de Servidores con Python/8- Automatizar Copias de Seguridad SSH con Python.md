
---

#Python #SSH #SCP #paramiko #automatización #backup #zip #transferencia_archivos

---

### **1. Importación de librerías**

```python
import paramiko
from scp import SCPClient
import zipfile
import os
```

- `paramiko`: Permite establecer conexiones SSH para interactuar con servidores remotos.
- `SCPClient` de `scp`: Se usa para transferir archivos a través del protocolo SCP.
- `zipfile`: Facilita la creación y manipulación de archivos ZIP.
- `os`: Proporciona funciones para interactuar con el sistema de archivos, como listar archivos en un directorio.

---

### **2. Definición de variables**

```python
host = '192.168.1.107'
user = 'kali'
password = 'kali'
archivo_destino = 'documentos.zip'
```

- `host`: Dirección IP del servidor remoto.
- `user`: Nombre de usuario para la conexión SSH.
- `password`: Contraseña del usuario para la autenticación.
- `archivo_destino`: Nombre del archivo ZIP que se enviará al servidor.

---

### **3. Inicio del bloque `try-except-finally`**

```python
try:
```

- Se inicia un bloque `try` para manejar posibles errores durante la ejecución del código.

---

### **4. Establecimiento de la conexión SSH**

```python
    cliente = paramiko.SSHClient()
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    cliente.connect(host, username=user, password=password)
```

- `paramiko.SSHClient()`: Crea una instancia del cliente SSH.
- `set_missing_host_key_policy(paramiko.AutoAddPolicy())`: Permite conectarse a servidores sin necesidad de verificar manualmente su clave de host.
- `connect(host, username=user, password=password)`: Establece la conexión SSH con el servidor remoto.

---

### **5. Creación del archivo ZIP**

```python
    zip_archivo = 'documentos.zip'
    extensiones_documentos = ('.doc', '.pdf', '.txt')

    with zipfile.ZipFile(zip_archivo, 'w') as zip:
        for archivo in os.listdir():
            if archivo.endswith(extensiones_documentos):
                zip.write(archivo)
```

- Se define el nombre del archivo ZIP (`documentos.zip`).
- Se establece un filtro para archivos con extensiones `.doc`, `.pdf` y `.txt`.
- Se abre un archivo ZIP en modo escritura (`'w'`), agregando solo los archivos que cumplen con las extensiones indicadas.
- `os.listdir()` obtiene la lista de archivos en el directorio actual.
- `zip.write(archivo)`: Agrega los archivos seleccionados al ZIP.

---

### **6. Transferencia del archivo ZIP mediante SCP**

```python
    with SCPClient(cliente.get_transport()) as scp_subir:
        scp_subir.put(zip_archivo, archivo_destino)
        print(f"Archivo {zip_archivo} subido correctamente")
```

- `SCPClient(cliente.get_transport())`: Crea una conexión SCP utilizando la sesión SSH existente.
- `scp_subir.put(zip_archivo, archivo_destino)`: Transfiere el archivo ZIP al servidor remoto.
- Si la transferencia es exitosa, se muestra un mensaje de confirmación.

---

### **7. Manejo de errores**

```python
except Exception as e:
    print(f"Error al subir la copia de seguridad por SCP: {e}")
```

- Si ocurre un error en la conexión SSH, compresión de archivos o transferencia SCP, se captura la excepción y se muestra un mensaje de error con el detalle del problema.

---

### **8. Cierre de la conexión SSH**

```python
finally:
    cliente.close()
```

- La conexión SSH se cierra siempre, ya sea que la ejecución haya sido exitosa o haya ocurrido un error.

---

### **Resumen de funcionalidad**

1. Establece una conexión SSH con el servidor remoto.
2. Crea un archivo ZIP con documentos (`.doc`, `.pdf`, `.txt`).
3. Transfiere el archivo ZIP al servidor mediante SCP.
4. Muestra un mensaje de éxito o error según el resultado.
5. Cierra la conexión SSH.

---

````python

import paramiko
from scp import SCPClient, SCPException
import zipfile
import os

host = '192.168.1.107'
user = 'kali'
password = 'kali'
archivo_destino = 'documentos.zip'

try:
    cliente = paramiko.SSHClient()
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy)
    cliente.connect(host, username=user, password=password)

    zip_archivo = 'documentos.zip'
    extensiones_documentos = ('.doc', '.pdf', '.txt')

    with zipfile.ZipFile(zip_archivo, 'w') as zip:
        for archivo in os.listdir():
            if archivo.endswith(extensiones_documentos):
                zip.write(archivo)

    with SCPClient(cliente.get_transport()) as scp_subir:
        scp_subir.put(zip_archivo, archivo_destino)
        print(f"Archivo {zip_archivo} subido correctamente")
except:
    print("Error al subir la copia de seguridad por scp")
finally:
    cliente.close()
    
    ````




