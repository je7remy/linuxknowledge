
---

#Python #MySQL #BaseDeDatos #SQL #ConexiónMySQL #Programación

---

### Explicación paso a paso del código

1. **Importación de la librería**
    
    ```python
    import mysql.connector
    ```
    
    Se importa `mysql.connector`, que es un módulo de Python que permite la conexión con bases de datos MySQL.
    
2. **Definición de la función `crear_tabla`**
    
    ```python
    def crear_tabla():
    ```
    
    Se define la función `crear_tabla()`, que maneja la conexión y consulta a la base de datos.
    
3. **Intento de conexión con MySQL**
    
    ```python
    conexion = mysql.connector.connect(
        host="localhost",
        database="pruebas",
        user="kali",
        password="kali",  
        auth_plugin="mysql_native_password"
    )
    ```
    
    Se establece una conexión con el servidor MySQL en `localhost`, utilizando la base de datos `pruebas` con el usuario y contraseña `kali`.
    
4. **Verificación de conexión**
    
    ```python
    if conexion.is_connected():
    ```
    
    Se verifica si la conexión fue exitosa. Si lo es, se imprime un mensaje indicando que la conexión se realizó correctamente.
    
5. **Creación de un cursor**
    
    ```python
    cursor = conexion.cursor()
    ```
    
    Se crea un cursor, que permite ejecutar consultas SQL en la base de datos.
    
6. **Solicitud de entrada al usuario**
    
    ```python
    decision = input("Quieres obtener los nombres, contraseñas o todo de la base de datos? nombre|contraseña|todo: ")
    ```
    
    Se solicita al usuario que elija si quiere ver solo los nombres, las contraseñas o toda la información de la tabla `usuarios`.
    
7. **Consulta según la opción del usuario**
    
    - **Si el usuario elige "nombre"**
        
        ```python
        if decision =='nombre':
            cursor.execute('SELECT nombre FROM usuarios')
            resultados = cursor.fetchall()
            for fila in resultados:
                print(f'Nombre: {fila[0]}')
        ```
        
        Se ejecuta la consulta `SELECT nombre FROM usuarios`, obteniendo solo los nombres. Luego, se recorren los resultados e imprimen.
        
    - **Si el usuario elige "contraseña"**
        
        ```python
        elif decision == 'contraseña':
            cursor.execute('SELECT contraseña FROM usuarios')
            resultados = cursor.fetchall()
            for fila in resultados:
                print(f'Contraseña: {fila[0]}')
        ```
        
        Se ejecuta `SELECT contraseña FROM usuarios`, obteniendo solo las contraseñas y mostrándolas.
        
    - **Si el usuario elige "todo"**
        
        ```python
        elif decision == 'todo':
            cursor.execute('SELECT * FROM usuarios')
            resultados = cursor.fetchall()
            for fila in resultados:
                print(f'Toda la informacion: {fila[1]}, {fila[2]}')
        ```
        
        Se ejecuta `SELECT * FROM usuarios`, obteniendo toda la información de la tabla.
        
8. **Cierre de la conexión**
    
    ```python
    cursor.close()
    conexion.close()
    print("Conexión cerrada")
    ```
    
    Después de ejecutar la consulta y mostrar los resultados, se cierran el cursor y la conexión.
    
9. **Manejo de errores**
    
    ```python
    except mysql.connector.Error as error: 
        print("Hubo un problema al conectarse a la base de datos:", error)
    ```
    
    Si ocurre algún error al conectarse o ejecutar la consulta, se imprime un mensaje de error.

### Código completo

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
            decision = input("Quieres obtener los nombres, contraseñas o todo de la base de datos? nombre|contraseña|todo: ")
            
            if decision =='nombre':

                cursor.execute(f'''
                SELECT nombre FROM usuarios
                ''')

                resultados = cursor.fetchall()

                for fila in resultados:
                    print(f'Nombre: {fila[0]}')
            
            elif decision == 'contraseña':

                cursor.execute(f'''
                SELECT contraseña FROM usuarios
                ''')

                resultados = cursor.fetchall()

                for fila in resultados:
                    print(f'Contraseña: {fila[0]}')

            elif decision == 'todo':

                 cursor.execute(f'''
                 SELECT * FROM usuarios
                 ''')

                 resultados = cursor.fetchall()

                 for fila in resultados:
                    print(f'Toda la informacion: {fila[1]}, {fila[2]}')

            cursor.close()
            conexion.close()
            print("Conexión cerrada")

        else:
         print("Dato no valido, escribe: nombre|contraseña|todo")

    except mysql.connector.Error as error: 
        print("Hubo un problema al conectarse a la base de datos:", error)
     

crear_tabla()
```





 **[[5- MySQL]]**