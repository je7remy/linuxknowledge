
---

#Python #SSH #Paramiko #ConexionRemota #SeguridadInformática

---

#### 1. **Importar la biblioteca necesaria**

```python
import paramiko
```

Esto importa `paramiko`, que se usa para manejar conexiones SSH en Python.

#### 2. **Definir las credenciales del servidor**

```python
host = '192.168.0.113'
user = 'kali'
password = 'kali'
```

Aquí definimos:

- `host`: dirección IP del servidor al que nos queremos conectar.
- `user`: el nombre de usuario para la autenticación.
- `password`: la contraseña del usuario para la conexión.

#### 3. **Manejo de la conexión con SSH**

```python
try:
    cliente = paramiko.SSHClient()
```

- `cliente = paramiko.SSHClient()`: Se crea una instancia de `SSHClient`, que es la base para la conexión SSH.

```python
    cliente.load_host_keys("C:/Users/Jeremy/.ssh/known_hosts")
```

- Intenta cargar las claves SSH almacenadas en `known_hosts`. Esto permite verificar la identidad del servidor antes de conectarse.

```python
    cliente.connect(host, username=user, password=password)
```

- Se establece la conexión con el servidor SSH utilizando las credenciales previamente definidas.

```python
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy())
```

- Si la clave del servidor no está en `known_hosts`, esta línea la agrega automáticamente en lugar de rechazar la conexión.

#### 4. **Ejecutar un comando en el servidor remoto**

```python
    stdin, stdout, stderr = cliente.exec_command('whoami')
```

- `exec_command('whoami')`: Envía el comando `whoami`, que devuelve el usuario con el que se ejecuta la sesión en el servidor.
- `stdin`, `stdout`, `stderr`: Tres flujos de datos:
    - `stdin`: Entrada estándar (para comandos interactivos).
    - `stdout`: Salida estándar (donde se almacena la respuesta del servidor).
    - `stderr`: Salida de errores (donde se almacena cualquier error).

```python
    resultado = stdout.read().decode()
    print(resultado)
```

- `stdout.read().decode()`: Lee la respuesta del servidor y la convierte en una cadena.
- `print(resultado)`: Muestra la respuesta en la consola.

#### 5. **Manejo de errores**

```python
except:
    print("A ocurrido un error de conexion")
```

- Si ocurre un error en cualquier punto, el programa muestra el mensaje `"A ocurrido un error de conexion"`.
- **Error:** "A ocurrido" debería ser "Ha ocurrido".

#### 6. **Cerrar la conexión**

```python
finally:
    cliente.close()
```

- Se cierra la conexión SSH para liberar los recursos.

---

### Código completo corregido y optimizado:

```python
import paramiko

host = '192.168.0.113'
user = 'kali'
password = 'kali'

try:
    cliente = paramiko.SSHClient()
    cliente.load_host_keys("C:/Users/Jeremy/.ssh/known_hosts")
    cliente.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    cliente.connect(host, username=user, password=password)

    stdin, stdout, stderr = cliente.exec_command('whoami')
    resultado = stdout.read().decode().strip()
    print(resultado)

except Exception as e:
    print("Ha ocurrido un error de conexión:", e)

finally:
    cliente.close()
```

---





[[6- Acceso Automatizado SSH Importando Clave Pública]]
[[7- Stdout, Stderr y Stdin]]
[[7- Automatización de Copias de Seguridad en Servidor SSH]]
[[11- Automatizar la Gestión de Usuarios en Linux]]