
---

#FTP #Python #ftplib #ConexiónFTP #SubirArchivo #AutenticaciónFTP #ManejoDeExcepciones #CierreDeConexión

---

### **Primera Sección: Verificación de Conexión Básica**

```python
from ftplib import FTP

try:
    ftp = FTP('192.168.0.116')
    ftp.login(user='kali', passwd='kali')
    print("Bien, conexion exitosa")
except:
    print("Hubo un error de conexion")
```

#### **Paso a Paso:**
1. **Importación de la biblioteca:**
   - `from ftplib import FTP`: Importa la clase `FTP` de la biblioteca `ftplib`, que permite interactuar con servidores FTP.
   
2. **Establecimiento de la conexión:**
   - `ftp = FTP('192.168.0.116')`: Crea una instancia de la clase `FTP` y trata de conectarse al servidor FTP ubicado en la dirección IP `'192.168.0.116'`.
   
3. **Inicio de sesión:**
   - `ftp.login(user='kali', passwd='kali')`: Intenta autenticarse en el servidor FTP con el nombre de usuario `'kali'` y la contraseña `'kali'`.
   
4. **Manejo de excepciones:**
   - `try`/`except`: Si la conexión o el inicio de sesión fallan (por ejemplo, debido a una IP incorrecta, servidor no disponible o credenciales inválidas), se captura cualquier excepción y se imprime `"Hubo un error de conexion"`.
   - Si no hay errores, se imprime `"Bien, conexion exitosa"`.

#### **Propósito:**
Esta sección prueba si es posible establecer una conexión y autenticarse en el servidor FTP en `'192.168.0.116'` con las credenciales dadas.

---

### **Segunda Sección: Conexión y Subida de Archivo**

```python
from ftplib import FTP

try:
    ftp = FTP('192.168.129.25')
    ftp.login(user='kali', passwd='kali')
    # print("Bien, conexion exitosa")

    with open('subir.txt', 'rb') as file:
        ftp.storbinary('STOR subir.txt', file)
        print("Archivo subido")

except:
    print("Hubo un error de conexion")
finally:
    ftp.quit()
```

#### **Paso a Paso:**
1. **Importación y conexión:**
   - `from ftplib import FTP`: Igual que en la primera sección.
   - `ftp = FTP('192.168.129.25')`: Intenta conectarse a un servidor FTP diferente, en la IP `'192.168.129.25'`.
   
2. **Inicio de sesión:**
   - `ftp.login(user='kali', passwd='kali')`: Autentica al usuario con las mismas credenciales que en la primera sección.
   
3. **Subida de archivo:**
   - `with open('subir.txt', 'rb') as file`: Abre el archivo local `'subir.txt'` en modo binario de lectura (`'rb'`). El modo binario es necesario para FTP, ya que asegura que los datos se transfieran sin alteraciones.
   - `ftp.storbinary('STOR subir.txt', file)`: Usa el método `storbinary` para subir el archivo al servidor FTP. El comando `'STOR subir.txt'` indica que el archivo se almacenará en el servidor con el nombre `'subir.txt'`.
   - `print("Archivo subido")`: Si la subida es exitosa, imprime este mensaje.
   
4. **Manejo de excepciones:**
   - `try`/`except`: Si hay un error en la conexión, autenticación o subida del archivo, se imprime `"Hubo un error de conexion"`.
   
5. **Cierre de la conexión:**
   - `finally: ftp.quit()`: Independientemente de si hubo un error o no, se ejecuta `ftp.quit()` para cerrar la conexión FTP de manera ordenada, liberando recursos.

#### **Propósito:**
Además de verificar la conexión y autenticación, esta sección sube un archivo (`'subir.txt'`) al servidor FTP en `'192.168.129.25'`.

---

### **Tercera Sección: Conexión y Subida con Credenciales Personalizadas**

```python
from ftplib import FTP

usuario = input('Introduce tu usuario FTP:')
contraseña = input('Introduce la contraseña')

try:
    ftp = FTP('192.168.129.25')
    ftp.login(user=usuario, passwd=contraseña)
    # print("Bien, conexion exitosa")

    with open('subir.txt', 'rb') as file:
        ftp.storbinary('STOR subir.txt', file)
        print("Archivo subido")

except:
    print("Hubo un error de conexion")
finally:
    ftp.quit()
```

#### **Paso a Paso:**
1. **Solicitud de credenciales:**
   - `usuario = input('Introduce tu usuario FTP:')`: Pide al usuario que ingrese su nombre de usuario FTP.
   - `contraseña = input('Introduce la contraseña')`: Pide la contraseña correspondiente.
   
2. **Conexión:**
   - `ftp = FTP('192.168.129.25')`: Intenta conectarse al mismo servidor FTP que en la segunda sección.
   
3. **Inicio de sesión:**
   - `ftp.login(user=usuario, passwd=contraseña)`: Autentica al usuario con las credenciales ingresadas manualmente, en lugar de usar valores fijos como en las secciones anteriores.
   
4. **Subida de archivo:**
   - Igual que en la segunda sección: abre `'subir.txt'` en modo binario y lo sube al servidor con `ftp.storbinary`, imprimiendo `"Archivo subido"` si tiene éxito.
   
5. **Manejo de excepciones y cierre:**
   - `try`/`except`: Captura errores e imprime `"Hubo un error de conexion"` si algo falla.
   - `finally: ftp.quit()`: Cierra la conexión FTP al final, haya o no errores.

#### **Propósito:**
Esta sección es una versión más flexible de la segunda, ya que permite al usuario ingresar sus propias credenciales, en lugar de tenerlas codificadas.

---

### **Código Completo**
La tercera sección es la más completa y versátil, ya que combina la funcionalidad de conexión y subida de archivos con la flexibilidad de credenciales personalizadas. Aquí está el código completo:

```python
from ftplib import FTP

usuario = input('Introduce tu usuario FTP: ')
contraseña = input('Introduce la contraseña: ')

try:
    ftp = FTP('192.168.129.25')
    ftp.login(user=usuario, passwd=contraseña)
    # print("Bien, conexion exitosa")

    with open('subir.txt', 'rb') as file:
        ftp.storbinary('STOR subir.txt', file)
        print("Archivo subido")

except:
    print("Hubo un error de conexion")
finally:
    ftp.quit()
```

---
