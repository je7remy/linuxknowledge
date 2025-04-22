
### Código Inicial del Cliente (`cliente.py`):

```python
import socket

ip = '192.168.1.110'
puerto = 5000
archivo = 'nota.txt'

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as conexion:
    conexion.connect((ip, puerto))
    with open(archivo, 'rb') as archivo_binario:
        conexion.sendall(archivo_binario)
        print("Archivo Enviado")
```

#### Problema:

En el código inicial del cliente, se intenta enviar el archivo `nota.txt` al servidor, pero se envía el objeto de archivo en sí mismo en lugar de los datos binarios del archivo.

#### Solución:

Modificar el cliente para leer los datos del archivo y luego enviarlos al servidor.

### Código Corregido del Cliente (`cliente.py`):

```python
import socket

ip = '192.168.1.110'
puerto = 5000
archivo = 'nota.txt'

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as conexion:
    conexion.connect((ip, puerto))
    with open(archivo, 'rb') as archivo_binario:
        data = archivo_binario.read(1024)  # Leer datos del archivo en bloques de 1024 bytes
        while data:
            conexion.sendall(data)  # Enviar los datos al servidor
            data = archivo_binario.read(1024)  # Leer el siguiente bloque de datos
        print("Archivo Enviado")
```

#### Cambios Realizados:

- Se lee el archivo en bloques de 1024 bytes (`data = archivo_binario.read(1024)`).
    
- Se envían los bloques de datos al servidor en un bucle hasta que se haya enviado todo el archivo.
    

### Código Inicial del Servidor (`servidor.py`):

```python
import socket

ip = '192.168.1.110'
puerto = 5000

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as conexion:
    conexion.bind((ip, puerto))
    conexion.listen()
    connect, address = conexion.accept()
    with connect:
        print("Conexion recibida: ", connect)
        with open('nota_recibida.txt', 'wb') as archivo_recibido:
            archivo_recibido.write()
        print("Archivo Recibido")
```

#### Problema:

En el código inicial del servidor:

- No se lee ni se escribe ningún dato del socket de conexión.
    
- La escritura del archivo no tiene datos para escribir.
    

#### Solución:

Modificar el servidor para recibir los datos del cliente y escribirlos en un archivo.

### Código Corregido del Servidor (`servidor.py`):

```python
import socket

ip = '192.168.1.110'
puerto = 5000

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as conexion:
    conexion.bind((ip, puerto))
    conexion.listen()
    connect, address = conexion.accept()
    with connect:
        print("Conexion recibida: ", connect)
        data = connect.recv(1024)  # Recibir datos del cliente en bloques de 1024 bytes
        with open('nota_recibida.txt', 'wb') as archivo_recibido:
            while data:
                archivo_recibido.write(data)  # Escribir los datos recibidos en el archivo
                data = connect.recv(1024)  # Recibir el siguiente bloque de datos
        print("Archivo Recibido")
```

#### Cambios Realizados:

- Se recibe los datos del cliente en bloques de 1024 bytes (`data = connect.recv(1024)`).
    
- Se escriben los datos recibidos en el archivo `nota_recibida.txt` en un bucle hasta que se han recibido todos los datos.
    

### Ejecución y Resultados:

1. **Cliente**: Ejecuta `cliente.py` y se conecta al servidor especificado (`192.168.1.110:5000`). Lee el archivo `nota.txt`, lo divide en bloques de 1024 bytes y los envía al servidor.
    
2. **Servidor**: Ejecuta `servidor.py` y espera conexiones entrantes en `192.168.1.110:5000`. Cuando se establece una conexión con el cliente, recibe los datos en bloques de 1024 bytes, los escribe en el archivo `nota_recibida.txt` y luego confirma que ha recibido el archivo.
    

### Resultados de la Ejecución:

- **Servidor**: Imprime `Conexion recibida` con detalles sobre la conexión establecida y luego `Archivo Recibido` una vez que ha completado la recepción y escritura del archivo.
    
- **Cliente**: Imprime `Archivo Enviado` una vez que ha completado el envío de todos los bloques de datos al servidor.
    

Este flujo muestra cómo se corrigen los errores iniciales para permitir una comunicación efectiva entre el cliente y el servidor para transferir archivos.