
---

#paramiko #scp #ssh #python #seguridad #transferencia #automatización #programación

---

### **Paso 1: Importación de librerías**

```python
import paramiko
from scp import SCPClient, SCPException
```

- **`paramiko`**: Es una biblioteca de Python para manejar conexiones SSH de manera programática.
- **`scp`**: Proporciona una manera de transferir archivos a través de SSH utilizando el protocolo SCP (Secure Copy Protocol).
    - **`SCPClient`**: Permite copiar archivos de manera segura.
    - **`SCPException`**: Maneja errores específicos del protocolo SCP.

---

### **Paso 2: Definición de variables**

```python
host = '192.168.0.113'
user = 'kali'
password = 'kali'
archivo_local = 'descargar.txt'
archivo_remoto = 'descargar.txt'
```

- **`host`**: Dirección IP del servidor al que queremos conectarnos.
- **`user`** y **`password`**: Credenciales de acceso al servidor SSH.
- **`archivo_local`**: Nombre del archivo en nuestra máquina local.
- **`archivo_remoto`**: Nombre del archivo en el servidor remoto.

---

### **Paso 3: Establecer conexión SSH**

```python
try:
    cliente = paramiko.SSHClient()
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy)
    cliente.connect(host, username=user, password=password)
```

- Se crea una instancia de **`SSHClient`** para gestionar la conexión SSH.
- **`set_missing_host_key_policy(paramiko.AutoAddPolicy)`**: Acepta automáticamente la clave del servidor remoto si no está en la lista de hosts conocidos.
- **`connect(host, username=user, password=password)`**: Establece la conexión SSH con el servidor.

---

### **Paso 4: Transferencia del archivo usando SCP**

```python
    with SCPClient(cliente.get_transport()) as scp_recibir:
        scp_recibir.get(archivo_remoto, archivo_local)
        print(f"Archivo {archivo_remoto} descargado correctamente")
```

- **`SCPClient(cliente.get_transport())`**: Usa la conexión SSH para crear una sesión SCP.
- **`scp_recibir.get(archivo_remoto, archivo_local)`**: Descarga el archivo del servidor remoto a nuestra máquina.
- **`print(f"Archivo {archivo_remoto} descargado correctamente")`**: Mensaje de éxito.

---

### **Paso 5: Manejo de errores**

```python
except:
    print("Error al descargar el archivo por SCP")
```

- Si ocurre un error en la conexión SSH o en la transferencia del archivo, se captura la excepción y se imprime un mensaje de error.

---

### **Paso 6: Cerrar la conexión**

```python
finally:
    cliente.close()
```

- **`cliente.close()`**: Se cierra la conexión SSH para liberar recursos.

---

### **Código completo**

```python
import paramiko
from scp import SCPClient, SCPException

host = '192.168.0.113'
user = 'kali'
password = 'kali'
archivo_local = 'descargar.txt'
archivo_remoto = 'descargar.txt'

try:
    cliente = paramiko.SSHClient()
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy)
    cliente.connect(host, username=user, password=password)

    with SCPClient(cliente.get_transport()) as scp_recibir:
        scp_recibir.get(archivo_remoto, archivo_local)
        print(f"Archivo {archivo_remoto} descargado correctamente")

except:
    print("Error al descargar el archivo por SCP")

finally:
    cliente.close()
```

---
