
---

#Python #MySQL #BaseDeDatos #SQL #mysqlconnector #Seguridad #InyeccionSQL #Conexion #Commit #Cursor #Input #Workbench

---

### **Primer fragmento: Creación de la tabla**

#### **Código:**
```python
import mysql.connector

def crear_tabla():
    try:
        conexion = mysql.connector.connect(
            host="localhost",
            database="pruebas",
            user="kali",
            password="kali",   
            auth_plugin="mysql_native_password"
        )
        if conexion.is_connected():
            print("La conexión se completó correctamente")
            cursor = conexion.cursor()
            cursor.execute('''
                CREATE TABLE IF NOT EXISTS usuarios (   
                    id_usuarios INT AUTO_INCREMENT PRIMARY KEY,
                    nombre VARCHAR(50) NOT NULL,
                    contraseña VARCHAR(255) NOT NULL
                )
            ''')
            conexion.commit()
            print("Tabla creada correctamente")
            cursor.close()
            conexion.close()
            print("Conexión cerrada")
    
    except mysql.connector.Error as error:
        print("Hubo un problema al conectarse a la base de datos:", error)

crear_tabla()
```

#### **Análisis paso a paso:**

1. **Importación de la biblioteca:**
   - Se importa la biblioteca `mysql.connector` para permitir la conexión e interacción con una base de datos MySQL.

2. **Definición de la función:**
   - Se define una función llamada `crear_tabla()` que se encargará de crear una tabla en la base de datos.

3. **Conexión a la base de datos:**
   - Se intenta establecer una conexión a la base de datos MySQL utilizando los parámetros siguientes:
     - `host="localhost"`: el servidor está en la máquina local.
     - `database="pruebas"`: la base de datos a la que se conecta.
     - `user="kali"` y `password="kali"`: credenciales del usuario.
     - `auth_plugin="mysql_native_password"`: especifica el plugin de autenticación para el usuario.
   - Si la conexión es exitosa, se imprime el mensaje: "La conexión se completó correctamente".

4. **Creación del cursor:**
   - Se crea un objeto `cursor` utilizando `conexion.cursor()`. El cursor se usa para ejecutar comandos SQL.

5. **Ejecución del comando SQL:**
   - Se ejecuta un comando SQL para crear una tabla llamada `usuarios`, pero solo si no existe ya (`IF NOT EXISTS`).
   - La tabla tiene las siguientes columnas:
     - `id_usuarios`: tipo `INT`, clave primaria y auto-incremental.
     - `nombre`: tipo `VARCHAR(50)`, no puede ser nulo.
     - `contraseña`: tipo `VARCHAR(255)`, no puede ser nulo.

6. **Confirmación de la transacción:**
   - Se ejecuta `conexion.commit()` para confirmar los cambios y hacerlos permanentes en la base de datos.

7. **Cierre de recursos:**
   - Se cierra el cursor con `cursor.close()`.
   - Se cierra la conexión con `conexion.close()`.
   - Se imprime el mensaje: "Tabla creada correctamente" y "Conexión cerrada".

8. **Manejo de excepciones:**
   - Si ocurre un error durante el proceso (por ejemplo, problemas de conexión), se captura la excepción y se imprime el mensaje: "Hubo un problema al conectarse a la base de datos:" seguido del error específico.

---

### **Segundo fragmento: Inserción de datos estáticos**

#### **Código:**
```python
import mysql.connector

def crear_tabla():
    try:
        conexion = mysql.connector.connect(
            host="localhost",
            database="pruebas",
            user="kali",
            password="kali",   
            auth_plugin="mysql_native_password"
        )
        if conexion.is_connected():
            print("La conexión se completó correctamente")
            cursor = conexion.cursor()
            cursor.execute('''
           INSERT INTO usuarios (nombre, contraseña) VALUES ('Jeremy','1234')
            ''')
            conexion.commit()
            print("Datos insertados correctamente")
            cursor.close()
            conexion.close()
            print("Conexión cerrada")
    
    except mysql.connector.Error as error:
        print("Hubo un problema al conectarse a la base de datos:", error)

crear_tabla()
```

#### **Análisis paso a paso:**

1. **Importación de la biblioteca:**
   - Igual que en el primer fragmento, se importa `mysql.connector`.

2. **Definición de la función:**
   - Se define una función llamada `crear_tabla()`, aunque en este caso no crea una tabla, sino que inserta datos. Este nombre podría ser confuso y sería mejor renombrarlo a algo como `insertar_datos()`.

3. **Conexión a la base de datos:**
   - Similar al primer fragmento, se establece la conexión con los mismos parámetros.

4. **Creación del cursor:**
   - Similar al primer fragmento, se crea un cursor para ejecutar comandos SQL.

5. **Ejecución del comando SQL:**
   - Se ejecuta un comando SQL para insertar un registro estático en la tabla `usuarios`:
     - Nombre: 'Jeremy'
     - Contraseña: '1234'

6. **Confirmación de la transacción:**
   - Similar al primer fragmento, se ejecuta `conexion.commit()` para confirmar los cambios.

7. **Cierre de recursos:**
   - Similar al primer fragmento, se cierran el cursor y la conexión, con los respectivos mensajes.

8. **Manejo de excepciones:**
   - Similar al primer fragmento, se manejan posibles errores de conexión o ejecución.

#### **Verificación en MySQL Workbench:**
- Ejecutando la consulta `SELECT * FROM pruebas.usuarios;` en MySQL Workbench, se pueden visualizar los registros insertados, como el usuario 'Jeremy' con contraseña '1234'.

---

### **Tercer fragmento: Inserción de datos dinámicos**

#### **Código:**
```python
import mysql.connector

def crear_tabla():
    try:
        conexion = mysql.connector.connect(
            host="localhost",
            database="pruebas",
            user="kali",
            password="kali",   
            auth_plugin="mysql_native_password"
        )
        if conexion.is_connected():
            print("La conexión se completó correctamente")
            cursor = conexion.cursor()
            nombre = input("Cual es tu nombre, lo vamos añadir a la base de datos: ")
            contraseña = input("Cual es tu contraseña, lo vamos a añadir a la base de datos: ")
            cursor.execute(f'''
           INSERT INTO usuarios (nombre, contraseña) VALUES ('{nombre}','{contraseña}')
            ''')
            conexion.commit()
            print("Datos insertados correctamente")
            cursor.close()
            conexion.close()
            print("Conexión cerrada")
    
    except mysql.connector.Error as error:
        print("Hubo un problema al conectarse a la base de datos:", error)

crear_tabla()
```

#### **Análisis paso a paso:**

1. **Importación de la biblioteca:**
   - Igual que en los fragmentos anteriores, se importa `mysql.connector`.

2. **Definición de la función:**
   - Similar al segundo fragmento, la función se llama `crear_tabla()`, pero inserta datos dinámicos. El nombre debería ser más descriptivo, como `insertar_datos_dinamicos()`.

3. **Conexión a la base de datos:**
   - Similar a los fragmentos anteriores, se establece la conexión con los mismos parámetros.

4. **Creación del cursor:**
   - Similar a los fragmentos anteriores, se crea un cursor para ejecutar comandos SQL.

5. **Obtención de datos del usuario:**
   - Se utiliza la función `input()` para pedir al usuario:
     - Su nombre, con el mensaje: "Cual es tu nombre, lo vamos añadir a la base de datos: ".
     - Su contraseña, con el mensaje: "Cual es tu contraseña, lo vamos a añadir a la base de datos: ".
   - Los valores ingresados se almacenan en las variables `nombre` y `contraseña`.

6. **Ejecución del comando SQL:**
   - Se ejecuta un comando SQL para insertar los datos proporcionados por el usuario en la tabla `usuarios`.
   - Se utiliza una f-string para construir la consulta SQL: `f'INSERT INTO usuarios (nombre, contraseña) VALUES ('{nombre}','{contraseña}')'`.
   - **Nota de seguridad:** Este método es vulnerable a inyección SQL. Por ejemplo, si el usuario ingresa `nombre = "Robert'; DROP TABLE usuarios; --"`, podría eliminar la tabla. Es mejor usar consultas parametrizadas.

7. **Confirmación de la transacción:**
   - Similar a los fragmentos anteriores, se ejecuta `conexion.commit()`.

8. **Cierre de recursos:**
   - Similar a los fragmentos anteriores, se cierran el cursor y la conexión, con los respectivos mensajes.

9. **Manejo de excepciones:**
   - Similar a los fragmentos anteriores, se manejan posibles errores.

---

### **Comentarios adicionales y recomendaciones:**

1. **Nombres de funciones:**
   - En el segundo y tercer fragmento, la función se llama `crear_tabla()`, pero se usa para insertar datos. Esto puede ser confuso. Sería mejor renombrar estas funciones según su propósito real, como `insertar_datos_estaticos()` y `insertar_datos_dinamicos()`.

2. **Seguridad en el tercer fragmento:**
   - El uso de f-strings para construir consultas SQL es inseguro y puede llevar a vulnerabilidades de inyección SQL. En su lugar, se debería usar consultas parametrizadas, como:
     ```python
     cursor.execute('INSERT INTO usuarios (nombre, contraseña) VALUES (%s, %s)', (nombre, contraseña))
     ```
   - Esto evita que el contenido de las variables sea interpretado como comandos SQL.

3. **Verificación de la existencia de la tabla:**
   - En el segundo y tercer fragmento, no se verifica si la tabla `usuarios` existe antes de insertar datos. Si la tabla no existe, se generará un error. El primer fragmento crea la tabla, pero sería buena práctica verificar la existencia en los otros fragmentos.

4. **Almacenamiento de contraseñas:**
   - En todos los fragmentos, las contraseñas se almacenan en texto plano, lo cual no es seguro. Es recomendable usar bibliotecas como `bcrypt` o `hashlib` para almacenar un hash de la contraseña en lugar del texto plano.

5. **Uso del plugin de autenticación:**
   - El parámetro `auth_plugin="mysql_native_password"` es necesario si el usuario 'kali' está configurado para usar ese plugin de autenticación en MySQL. Esto debe coincidir con la configuración del servidor MySQL.
