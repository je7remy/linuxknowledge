
---

#Python #MySQL #mysqlconnector #BasesDeDatos #SQL #Programacion #Tutorial #Conexion #Codigo #Desarrollo

---
## 1. Importación de la librería

```python
import mysql.connector
```

- **¿Qué hace?**  
    Se importa el módulo `mysql.connector`, que es el encargado de facilitar la conexión y la interacción con bases de datos MySQL.
- **Importancia:**  
    Sin esta librería, el script no podría establecer la conexión ni ejecutar comandos SQL sobre la base de datos.

---

## 2. Definición de la función

```python
def crear_tabla():
```

- **¿Qué hace?**  
    Se define la función `crear_tabla()`, que engloba todo el proceso de conexión, consulta, procesamiento y cierre de la base de datos.
- **Organización:**  
    Encapsular el código dentro de una función ayuda a modularizar y reutilizar el código.

---

## 3. Bloque Try-Except

```python
    try:
        # Bloque de código a ejecutar
    except mysql.connector.Error as error:
        print("Hubo un problema al conectarse a la base de datos:", error)
```

- **¿Qué hace?**
    - El bloque `try` contiene el código que podría generar errores (por ejemplo, problemas de conexión o de consulta).
    - El bloque `except` captura cualquier error relacionado con `mysql.connector` y muestra un mensaje descriptivo junto con el error.
- **Importancia:**  
    Permite manejar de forma controlada posibles excepciones sin que el programa se detenga abruptamente.

---

## 4. Conexión a la Base de Datos

```python
        conexion = mysql.connector.connect(
            host="localhost",
            database="pruebas",
            user="kali",
            password="kali",  
            auth_plugin="mysql_native_password"
        )
```

- **Parámetros utilizados:**
    - **host:** `"localhost"`  
        Indica que la base de datos se encuentra en el mismo equipo donde se ejecuta el script.
    - **database:** `"pruebas"`  
        Nombre de la base de datos a la que se desea acceder.
    - **user y password:** `"kali"`  
        Credenciales de acceso para autenticar al usuario en la base de datos.
    - **auth_plugin:** `"mysql_native_password"`  
        Especifica el método de autenticación a utilizar.
- **Funcionamiento:**  
    Se establece una conexión utilizando las credenciales y parámetros indicados. Si la conexión es exitosa, se asigna el objeto a la variable `conexion`.

---

## 5. Verificación de la Conexión

```python
        if conexion.is_connected():
            print("La conexión se completó correctamente")
```

- **¿Qué hace?**
    - El método `conexion.is_connected()` verifica que la conexión a la base de datos se haya establecido correctamente.
    - Si la conexión es exitosa, se imprime un mensaje confirmando la conexión.
- **Importancia:**  
    Es un paso crucial para asegurarse de que se pueda continuar con la ejecución de comandos SQL de forma segura.

---

## 6. Creación del Cursor

```python
            cursor = conexion.cursor()
```

- **¿Qué hace?**
    - Se crea un objeto cursor a partir de la conexión.
    - El cursor actúa como un intermediario para ejecutar consultas SQL y recuperar resultados.
- **Importancia:**  
    Permite enviar comandos SQL a la base de datos y gestionar los datos obtenidos de las consultas.

---

## 7. Ejecución de la Consulta SQL

```python
            cursor.execute(f'''
              SELECT * FROM usuarios
            ''')
```

- **¿Qué hace?**
    - Se ejecuta la consulta SQL `SELECT * FROM usuarios`, que solicita recuperar todas las filas y columnas de la tabla `usuarios`.
- **Detalles del código:**
    - Se utiliza una cadena multilínea (mediante comillas triples) para definir la consulta.
    - La consulta se pasa al método `execute()` del cursor, que la envía al servidor MySQL.

---

## 8. Obtención y Procesamiento de los Resultados

### Variante 1: Imprimir la lista completa

```python
            resultados = cursor.fetchall()
            print(resultados)
```

- **¿Qué hace?**
    - `cursor.fetchall()` recupera todas las filas resultantes de la consulta y las guarda en la variable `resultados` como una lista de tuplas.
    - Se imprime la lista completa, mostrando todos los datos obtenidos de una vez.

### Variante 2: Recorrer e imprimir un campo específico

```python
            resultados = cursor.fetchall()
  
            for fila in resultados:
                print(f'Nombre: {fila[1]}')
```

- **¿Qué hace?**
    - Se recorre la lista `resultados` utilizando un bucle `for`.
    - Para cada fila (cada tupla), se accede al elemento en la posición 1 (segundo valor) y se imprime.
- **Interpretación:**  
    Se asume que la columna con índice 1 corresponde, por ejemplo, al nombre del usuario.

### Variante 3: Imprimir otro campo específico

```python
            resultados = cursor.fetchall()
  
            for fila in resultados:
                print(f'Nombre: {fila[2]}')
```

- **¿Qué hace?**
    - Similar al caso anterior, pero ahora se imprime el valor ubicado en la posición 2 de cada tupla.
- **Consideración:**  
    Esto sugiere que la estructura de la tabla es conocida y que la columna de índice 2 puede representar otro dato, como podría ser la contraseña o algún otro campo.

### Variante 4: Imprimir dos campos formateados

```python
            resultados = cursor.fetchall()
  
            for fila in resultados:
                print(f'Nombre: {fila[1]} contraseña: {fila[2]}')
```

- **¿Qué hace?**
    - Se recorre la lista de resultados y para cada fila se imprimen dos campos:
        - El campo en la posición 1 (por ejemplo, el nombre).
        - El campo en la posición 2 (por ejemplo, la contraseña).
- **Formato:**  
    Se utiliza la interpolación de cadenas (f-strings) para dar formato a la salida.

---

## 9. Cierre del Cursor y la Conexión

```python
            cursor.close()
            conexion.close()
            print("Conexión cerrada")
```

- **¿Qué hace?**
    - `cursor.close()`: Cierra el objeto cursor liberando los recursos asociados.
    - `conexion.close()`: Finaliza la conexión con la base de datos para evitar conexiones abiertas innecesarias.
    - Se imprime un mensaje confirmando el cierre de la conexión.
- **Importancia:**  
    Es fundamental cerrar la conexión y el cursor para evitar problemas de rendimiento o límites en el número de conexiones abiertas.

---

## 10. Manejo de Errores

```python
    except mysql.connector.Error as error:
        print("Hubo un problema al conectarse a la base de datos:", error)
```

- **¿Qué hace?**
    - Si ocurre algún error durante la conexión o la ejecución de la consulta, el bloque `except` captura la excepción.
    - Se imprime un mensaje que incluye la descripción del error.
- **Importancia:**  
    Ayuda a depurar el código y a manejar situaciones inesperadas sin que el programa se detenga abruptamente.

---

## 11. Ejecución de la Función

```python
crear_tabla()
```

- **¿Qué hace?**
    - Se llama a la función `crear_tabla()`, lo que inicia todo el proceso explicado anteriormente.
- **Resultado:**  
    Se establece la conexión, se ejecuta la consulta, se procesan y muestran los resultados, y finalmente se cierra la conexión.

---

## Resumen de las Diferencias entre las Variantes

- **Primera Variante:**  
    Imprime directamente la lista completa de resultados obtenidos de la consulta.
    
- **Segunda Variante:**  
    Recorre cada fila e imprime únicamente el valor ubicado en la posición 1 de cada tupla (por ejemplo, el nombre).
    
- **Tercera Variante:**  
    Similar a la segunda, pero imprime el valor de la posición 2 de cada fila.
    
- **Cuarta Variante:**  
    Recorre cada fila e imprime dos campos: el valor de la posición 1 y el de la posición 2, mostrando ambos de forma formateada (por ejemplo, nombre y contraseña).
    

---




 **[[5- MySQL]]**