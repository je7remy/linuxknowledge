
---

#Python #SSH #SCP #Automatización #SeguridadInformática

---


## **Paso 1: Importar las bibliotecas necesarias**

```python
import paramiko
from scp import SCPClient, SCPException
```

### **Explicación**

- `paramiko`: Es una biblioteca de Python que permite la conexión SSH a servidores remotos.
- `scp`: Proporciona una forma de transferir archivos a través de SSH utilizando `SCPClient`.
    - `SCPClient`: Se usa para enviar y recibir archivos con SCP (Secure Copy Protocol).
    - `SCPException`: Captura errores relacionados con SCP.

---

## **Paso 2: Definir las credenciales y archivos**

```python
host = '192.168.0.113'   # Dirección IP del servidor remoto
user = 'kali'            # Usuario SSH
password = 'kali'        # Contraseña SSH

archivo_local = 'subir.txt'   # Archivo en la máquina local
archivo_remoto = 'subir.txt'  # Ruta donde se guardará en el servidor
```

### **Explicación**

- `host`: Dirección IP del dispositivo remoto (servidor SSH).
- `user`: Nombre de usuario en el servidor SSH.
- `password`: Clave de acceso para autenticarse.
- `archivo_local`: Nombre del archivo que queremos subir desde la máquina local.
- `archivo_remoto`: Nombre con el que se guardará en el servidor (puede ser una ruta absoluta o relativa).

---

## **Paso 3: Crear un bloque `try-except-finally`**

```python
try:
```

### **Explicación**

- Se usa `try` para ejecutar el código principal y capturar cualquier error que pueda ocurrir durante la ejecución.

---

## **Paso 4: Crear un cliente SSH**

```python
    cliente = paramiko.SSHClient()
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy())
```

### **Explicación**

- `paramiko.SSHClient()`: Se crea un objeto para gestionar la conexión SSH.
- `set_missing_host_key_policy(paramiko.AutoAddPolicy())`: Permite aceptar automáticamente la clave del host remoto si no está en la lista de hosts conocidos.

---

## **Paso 5: Conectar al servidor SSH**

```python
    cliente.connect(host, username=user, password=password)
```

### **Explicación**

- `connect()`: Establece la conexión con el servidor remoto usando las credenciales proporcionadas.

---

## **Paso 6: Subir el archivo con SCP**

```python
    with SCPClient(cliente.get_transport()) as scp_enviar:
        scp_enviar.put(archivo_local, archivo_remoto)
        print(f"Archivo {archivo_local} subido correctamente")
```

### **Explicación**

- `cliente.get_transport()`: Obtiene el canal de comunicación SSH.
- `SCPClient()`: Crea un cliente SCP para transferencias de archivos.
- `put(archivo_local, archivo_remoto)`: Sube el archivo especificado desde la máquina local al servidor.
- `print()`: Muestra un mensaje de éxito si el archivo se subió correctamente.

---

## **Paso 7: Capturar errores con `except`**

```python
except SCPException as e:
    print(f"Error SCP: {e}")
except Exception as e:
    print(f"Error: {e}")
```

### **Explicación**

- `except SCPException as e`: Captura errores específicos relacionados con SCP.
- `except Exception as e`: Captura cualquier otro error inesperado.

---

## **Paso 8: Cerrar la conexión SSH**

```python
finally:
    cliente.close()
```

### **Explicación**

- `finally`: Se ejecuta siempre, haya ocurrido un error o no.
- `cliente.close()`: Cierra la conexión SSH para liberar recursos.

---

## **Código completo**

```python
import paramiko
from scp import SCPClient, SCPException

# Datos de conexión SSH
host = '192.168.0.113'
user = 'kali'
password = 'kali'

# Archivos locales y remotos
archivo_local = 'subir.txt'
archivo_remoto = 'subir.txt'

try:
    # Inicializar el cliente SSH
    cliente = paramiko.SSHClient()
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    # Conectar al host remoto
    cliente.connect(host, username=user, password=password)
    
    # Subir archivo usando SCP
    with SCPClient(cliente.get_transport()) as scp_enviar:
        scp_enviar.put(archivo_local, archivo_remoto)
        print(f"Archivo {archivo_local} subido correctamente")
        
except SCPException as e:
    print(f"Error SCP: {e}")
except Exception as e:
    print(f"Error: {e}")
finally:
    # Cerrar conexión SSH
    cliente.close()
```

---

### **Resumen**

Este código permite subir un archivo de una máquina local a un servidor remoto usando SCP sobre SSH. Se divide en:

1. **Importar librerías** (`paramiko` y `scp`).
2. **Definir credenciales y nombres de archivos**.
3. **Crear un cliente SSH** y **conectar al servidor**.
4. **Subir el archivo con SCP**.
5. **Manejar errores** y **cerrar la conexión**.
