
---

## 1. Cliente inicial (`cliente.py`)

```python
import socket
import threading
```

- **¿Qué hace?** Importa el módulo `socket` para trabajar con comunicaciones TCP/IP y `threading` para manejar concurrencia.
    
- **¿Por qué?** Queremos enviar y recibir mensajes al mismo tiempo sin bloquear la interfaz de usuario.
    

```python
servidor = '192.168.1.110'
puerto_servidor = 5000
```

- **¿Qué hace?** Define la IP y el puerto donde escucha el servidor.
    
- **¿Por qué?** Necesitamos saber a dónde conectar el socket cliente.
    

```python
cliente_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
cliente_socket.connect((servidor, puerto_servidor))
```

- **¿Qué hace?**
    
    1. Crea un socket IPv4 (`AF_INET`) de tipo TCP (`SOCK_STREAM`).
        
    2. Establece la conexión con el servidor en la dirección indicada.
        
- **¿Por qué?** Sin un socket conectado, no podemos enviar ni recibir datos.
    

```python
def recibir_mensaje():
    while True:
        respuesta_servidor = cliente_socket.recv(1024)
        print(f"Respuesta del servidor: {respuesta_servidor.decode()}")
```

- **¿Qué hace?** En bucle infinito, llama a `recv(1024)` para leer hasta 1024 bytes y los imprime.
    
- **¿Por qué?** Queremos mostrar al usuario cualquier mensaje que el servidor envíe en cualquier momento.
    

```python
def enviar_mensaje():
    mensaje = input("Escribe lo que quieres enviar: ")
    cliente_socket.sendall(mensaje.encode())
```

- **¿Qué hace?** Pide al usuario un texto por consola y lo envía codificado al servidor.
    
- **¿Por qué?** Permite al usuario escribir un mensaje que viaja por la conexión TCP.
    

```python
hilo_recibir = threading.Thread(target=recibir_mensaje)
hilo_enviar = threading.Thread(target=enviar_mensaje)
hilo_recibir.start()
hilo_enviar.start()
hilo_recibir.join()
hilo_enviar.join()
cliente_socket.close()
```

- **¿Qué hace?**
    
    1. Crea dos hilos: uno para recibir y otro para enviar.
        
    2. Los arranca simultáneamente.
        
    3. Espera (`join`) a que ambos acaben antes de cerrar el socket.
        
- **¿Por qué?** Sin hilos, las llamadas a `recv` o `input` bloquearían todo el programa; con concurrencia, enviamos y recibimos en paralelo.
    

---

## 2. Servidor inicial (`servidor.py`)

```python
import socket
import threading
```

- **¿Qué hace?** Igual que en el cliente: importamos librerías para sockets y concurrencia.
    

```python
servidor = '192.168.1.110'
puerto_servidor = 5000

servidor_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
servidor_socket.bind((servidor, puerto_servidor))
servidor_socket.listen()
print(f"Servidor esperando conexion en {servidor} {puerto_servidor}")
```

- **¿Qué hace?**
    
    1. Define IP/puerto.
        
    2. Crea el socket, lo vincula (`bind`) y pasa a modo escucha (`listen`).
        
    3. Imprime un mensaje de log.
        
- **¿Por qué?** Prepara el servidor para aceptar conexiones entrantes.
    

```python
def recibir_mensaje(conexion, address):
    while True:
        try:
            data = conexion.recv(1024)
            print(f"Mensaje del {address}: {data.decode()}")
        except:
            print("Hubo un error, saliendo...")
            conexion.close()
            break
```

- **¿Qué hace?** Lee datos desde un socket de cliente y los imprime, hasta que falle (cliente desconectado o error).
    
- **¿Por qué?** Para procesar asincrónicamente lo que envíe cada cliente.
    

```python
def enviar_mensaje(conexion, address):
    while True:
        try:
            respuesta = input(f"Que Quieres enviar a: {address}")
            conexion.sendall(respuesta.encode())
        except:
            print("Hubo un error, saliendo...")
            conexion.close()
            break
```

- **¿Qué hace?** Permite al operador del servidor escribir mensajes para enviar al cliente conectado.
    
- **¿Por qué?** Facilita la comunicación bidireccional.
    

```python
def gestionar_la_conexion(conexion, address):
    print(f"Conexion establecida con {conexion}")
    hilo_recibir = threading.Thread(target=recibir_mensaje, args=(conexion,address))
    hilo_recibir.start()
    hilo_recibir.join()
    hilo_enviar = threading.Thread(target=enviar_mensaje, args=(conexion,address))
    hilo_enviar.start()
    hilo_enviar.join()
    print(f"Desconectado de {address}")
```

- **¿Qué hace?**
    
    1. Informa de la conexión entrante.
        
    2. Arranca un hilo de recepción y espera a que termine (lo cual ocurre al desconectar el cliente).
        
    3. Luego arranca un hilo de envío y espera su final.
        
    4. Informa cuando se cierra la conexión.
        
- **¿Por qué?** Para aislar la lógica de cada cliente en su propio hilo, garantizando que la recepción y envío no interfieran entre sí.
    

```python
while True:
    try:
        conexion,address = servidor_socket.accept()
        hilo_gestionar = threading.Thread(
            target=gestionar_la_conexion,
            args=(conexion,address)
        )
        hilo_gestionar.start()
        hilo_gestionar.join()
    except:
        print("Hubo un error de conecion")
```

- **¿Qué hace?**
    
    1. Bucle principal que acepta nuevas conexiones.
        
    2. Por cada conexión, lanza un hilo que gestiona la conversación.
        
    3. Espera a que ese hilo termine antes de aceptar la siguiente.
        
- **¿Por qué?** Para procesar clientes de forma secuencial (aunque cada uno use hilos internos).
    

---

## 3. Corrección del servidor

Se ajusta la concurrencia interna para que **recepción** y **envío** se ejecuten totalmente en paralelo, sin hacer `join()` intercalados.

```python
def gestionar_la_conexion(conexion, address):
    print(f"Servidor conectado con {address}")
    hilo_recibir = threading.Thread(target=recibir_mensaje, args=(conexion,address))
    hilo_enviar  = threading.Thread(target=enviar_mensaje, args=(conexion,address))
    hilo_recibir.start()
    hilo_enviar.start()
    hilo_recibir.join()
    hilo_enviar.join()
    print(f"Desconectado de {address}")
```

- **¿Qué cambia?**
    
    - Ambos hilos se crean **antes** de arrancar y luego se lanza `start()` en paralelo.
        
    - Finalmente se espera (`join()`) a ambos.
        
- **¿Por qué?** Evitar que la parte de envío espere a que termine la de recepción o viceversa, garantizando verdadera bidireccionalidad.
    

El resto del servidor (bind, listen, loop de `accept`) permanece igual.

---

## 4. Versión final (IP `192.168.0.65`)

### Cliente

```python
import socket
import threading

servidor = '192.168.0.65'
puerto_servidor = 5000

cliente_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
cliente_socket.connect((servidor, puerto_servidor))
```

- **¿Qué cambia?** Solo la IP de destino.
    

```python
def recibir_mensaje():
    while True:
        respuesta_servidor = cliente_socket.recv(1024)
        print(f"Respuesta del servidor: {respuesta_servidor.decode()}")

def enviar_mensaje():
    while True:
        mensaje = input("Introduce el mensaje: ")
        cliente_socket.sendall(mensaje.encode())
```

- **¿Qué cambia?** Ahora `enviar_mensaje` está dentro de un bucle `while True`, para poder mandar múltiples mensajes sin reiniciar el hilo.
    

```python
hilo_recibir = threading.Thread(target=recibir_mensaje)
hilo_enviar  = threading.Thread(target=enviar_mensaje)
hilo_recibir.start()
hilo_enviar.start()
hilo_recibir.join()
hilo_enviar.join()
cliente_socket.close()
```

- **¿Por qué?** Igual que antes: dos hilos en paralelo para recepción y envío continuo.
    

---

### Servidor

```python
import socket
import threading

servidor = '192.168.0.65'
puerto_servidor = 5000

servidor_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
servidor_socket.bind((servidor, puerto_servidor))
servidor_socket.listen()
print(f"Servidor escuchando en {servidor}:{puerto_servidor}")
```

- **¿Qué cambia?** IP de enlace.
    

```python
def recibir_mensaje(conexion, address):
    while True:
        try:
            data = conexion.recv(1024)
            print(f"Mensaje del {address}: {data.decode()}")
        except:
            print("Hubo un error, saliendo...")
            conexion.close()
            break
```

- **¿Qué hace?** Mismo bucle de lectura de cliente.
    

```python
def enviar_mensaje(conexion, address):
    while True:
        try:
            respuesta = input(f"Que quieres enviar a {address}: ")
            conexion.sendall(respuesta.encode())
        except:
            print("Hubo un error")
            conexion.close()
            break
```

- **¿Qué hace?** Bucle de escritura al cliente.
    

```python
def gestionar_conexion(conexion, address):
    print(f"Conexión establecida con {address}")
    hilo_recibir = threading.Thread(
        target=recibir_mensaje, args=(conexion,address)
    )
    hilo_enviar  = threading.Thread(
        target=enviar_mensaje,  args=(conexion,address)
    )
    hilo_recibir.start()
    hilo_enviar.start()
    hilo_recibir.join()
    hilo_enviar.join()
    print(f"Desconectado de {address}")
```

- **¿Por qué?** Igual que la versión corregida: dos hilos paralelos por cliente.
    

```python
while True:
    try:
        conexion, address = servidor_socket.accept()
        hilo_gestionar = threading.Thread(
            target=gestionar_conexion,
            args=(conexion,address)
        )
        hilo_gestionar.start()
    except:
        print("Hubo un error de conexión")
```

- **¿Qué cambia?** Ya no hay `join()` en el hilo gestor, de modo que el servidor acepta nuevas conexiones sin esperar a que termine la conversación previa.
    

---

