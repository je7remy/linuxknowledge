
---

#Python #MySQL #Windows11 #Database #SQL #MySQLConnector #Programación #DesarrolloSoftware #ConexiónMySQL #VSCode #PipInstall #ErroresYSoluciones #Backend #AprendePython

---
## **Paso 1: Instalación y configuración de MySQL**

Antes de trabajar con MySQL en Python, necesitamos asegurarnos de que MySQL está instalado y funcionando correctamente.

1. **Descargar e instalar MySQL**
    
    - Descarga MySQL Server desde [MySQL Community Downloads](https://dev.mysql.com/downloads/installer/).
    - Durante la instalación, configura un usuario (`root` o `kali`) con su respectiva contraseña.
    - Recuerda activar el **plugin de autenticación** `mysql_native_password`, ya que Python puede no funcionar con `caching_sha2_password`.
2. **Iniciar MySQL Server**
    
    - Asegúrate de que el servicio de MySQL esté corriendo.
    - Puedes verificarlo con:
        
        ```sh
        net start MySQL80
        ```
        
    - O acceder al cliente de MySQL con:
        
        ```sh
        mysql -u kali -p
        ```
        

---

## **Paso 2: Creación de la base de datos**

1. Abre **MySQL Workbench** o usa la terminal de MySQL y ejecuta:
    
    ```sql
    CREATE DATABASE pruebas;
    USE pruebas;
    ```
    
2. Esto crea una base de datos llamada `pruebas`, que usaremos para conectarnos desde Python.

---

## **Paso 3: Instalación del conector de MySQL para Python**

Necesitamos instalar `mysql-connector-python` para que Python pueda interactuar con MySQL.

1. Abre una terminal en **Windows** (**cmd** o **PowerShell**) y ejecuta:
    
    ```sh
    pip install mysql-connector-python
    ```
    
2. Si por algún motivo **falla**, intenta con:
    
    ```sh
    pip install mysql.connector
    ```
    
3. Verifica que la instalación fue correcta ejecutando:
    
    ```sh
    python -c "import mysql.connector; print('Conector instalado correctamente')"
    ```
    

---

## **Paso 4: Creación del archivo Python en VS Code**

1. Abre **Visual Studio Code**.
2. Crea un nuevo archivo llamado `database.py`:
    - Puedes hacerlo desde el terminal de VS Code con:
        
        ```sh
        code database.py
        ```
        
    - O manualmente: `Archivo > Nuevo Archivo > Guardar como "database.py"`

---

## **Paso 5: Escribir y ejecutar el script de conexión en Python**

Copia y pega el siguiente código en `database.py`:

```python
import mysql.connector
from mysql.connector import Error

def check_mysql_connection():
    connection = None
    try:
        connection = mysql.connector.connect(
            host='localhost',  
            database='pruebas',
            user='kali',
            password='kali',
            auth_plugin='mysql_native_password'  # Asegurar que el plugin sea compatible
        )
        if connection.is_connected():
            print("Conexión exitosa a MySQL")
        else:
            print("Fallo en la conexión a MySQL")

    except Error as e:
        print("Error al conectar a MySQL:", e)

    finally:
        if connection and connection.is_connected():
            connection.close()
            print("Conexión cerrada")

check_mysql_connection()
```

---

## **Paso 6: Ejecutar el script**

1. En la terminal de VS Code o **cmd**, dirígete a la carpeta donde guardaste `database.py`:
    
    ```sh
    cd ruta/del/archivo
    ```
    
2. Ejecuta el script:
    
    ```sh
    python database.py
    ```
    

---

## **Posibles errores y soluciones**

1. **Error de autenticación** (`Authentication plugin 'caching_sha2_password' is not supported`)
    
    - Se debe a que MySQL usa `caching_sha2_password` por defecto.
    - Solución: Ejecuta en MySQL:
        
        ```sql
        ALTER USER 'kali'@'localhost' IDENTIFIED WITH mysql_native_password BY 'kali';
        FLUSH PRIVILEGES;
        ```
        
2. **MySQL no está corriendo** (`Can't connect to MySQL server on 'localhost'`)
    
    - Asegúrate de que MySQL está iniciado:
        
        ```sh
        net start MySQL80
        ```
        
    - O inicia el servicio manualmente desde **Servicios de Windows**.
3. **Falta el módulo `mysql.connector`**
    
    - Reinstala el paquete:
        
        ```sh
        pip install mysql-connector-python
        ```
        

---

## **Paso 7: Confirmar conexión exitosa**

Si todo está correcto, deberías ver:

```sh
Conexión exitosa a MySQL
Conexión cerrada
```

---

Con esto, habrás configurado y probado la conexión entre **Python y MySQL en Windows 11** correctamente. 🚀



 **[[5- MySQL]]**