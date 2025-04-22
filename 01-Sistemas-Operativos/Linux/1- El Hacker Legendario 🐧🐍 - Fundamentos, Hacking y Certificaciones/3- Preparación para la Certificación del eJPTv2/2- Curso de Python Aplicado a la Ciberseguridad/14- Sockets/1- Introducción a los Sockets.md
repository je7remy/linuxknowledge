
### Paso a Paso:

#### Configuración del Servidor (`servidor.py`):

1. **Creación del Socket del Servidor:**
    
    ```python
    import socket
    
    servidor = socket.socket()
    ```
    
    Aquí creamos un objeto de socket para el servidor utilizando `socket.socket()`.
    
2. **Asociación y Escucha del Socket:**
    
    ```python
    servidor.bind(('192.168.1.110', 5000))
    ```
    
    El servidor se enlaza a la dirección IP y puerto especificados. Esto significa que el servidor estará escuchando en la dirección IP `192.168.1.110` en el puerto `5000`.
    
3. **Espera de Conexiones Entrantes:**
    
    ```python
    servidor.listen(1)
    ```
    
    El servidor está configurado para escuchar hasta 1 conexión entrante en la cola de conexiones pendientes.
    
4. **Aceptación de la Conexión del Cliente:**
    
    ```python
    cliente_socket, cliente_address = servidor.accept()
    ```
    
    Cuando un cliente se conecta, `servidor.accept()` acepta la conexión y devuelve un nuevo socket `cliente_socket` para la comunicación con ese cliente, junto con la dirección del cliente `cliente_address`.
    
5. **Recepción de Datos del Cliente:**
    
    ```python
    mensaje_recibido = cliente_socket.recv(1024)
    ```
    
    El servidor espera recibir datos del cliente a través del socket `cliente_socket`. En este caso, lee hasta 1024 bytes de datos enviados por el cliente.
    
6. **Procesamiento y Respuesta:**
    
    ```python
    print(mensaje_recibido.decode())
    ```
    
    El mensaje recibido se decodifica (asumiendo que es texto) y se imprime en la consola del servidor.
    
7. **Cierre de la Conexión del Cliente:**
    
    ```python
    cliente_socket.close()
    ```
    
    Una vez que se ha completado la comunicación con el cliente, se cierra el socket `cliente_socket`.
    
8. **Cierre del Socket del Servidor:**
    
    ```python
    servidor.close()
    ```
    
    Finalmente, el socket del servidor se cierra, liberando el puerto y los recursos asociados.
    

#### Configuración del Cliente (`cliente.py`):

1. **Creación del Socket del Cliente:**
    
    ```python
    import socket
    
    cliente = socket.socket()
    ```
    
    Se crea un socket cliente para establecer la conexión con el servidor.
    
2. **Conexión al Servidor:**
    
    ```python
    cliente.connect(("192.168.1.110", 5000))
    ```
    
    El cliente se conecta al servidor especificado por la dirección IP `192.168.1.110` y el puerto `5000`.
    
3. **Envío de Datos al Servidor:**
    
    ```python
    mensaje = 'hola, esto es un mensaje enviado desde el cliente'
    cliente.send(mensaje.encode())
    ```
    
    El cliente envía el mensaje codificado en bytes al servidor a través del socket `cliente`.
    
4. **Cierre de la Conexión del Cliente:**
    
    ```python
    cliente.close()
    ```
    
    Después de enviar el mensaje, el cliente cierra su conexión con el servidor.
    

### Importancia y Ejemplos:

- **Comunicación en Red:** Este ejemplo ilustra cómo los programas pueden comunicarse a través de una red utilizando sockets, lo cual es fundamental para aplicaciones cliente-servidor en internet.
    
- **Transmisión de Datos:** Permite el intercambio de datos estructurados (en este caso, texto) entre dispositivos conectados en red, esencial para aplicaciones como chats, transferencia de archivos, etc.
    
- **Gestión de Conexiones:** El manejo correcto de sockets incluye la creación, conexión, envío de datos y cierre ordenado de conexiones, lo cual garantiza una comunicación eficiente y segura.
    

En resumen, este ejemplo demuestra cómo implementar una comunicación básica cliente-servidor utilizando sockets en Python, proporcionando una base fundamental para el desarrollo de aplicaciones distribuidas y servicios en red.

### 🔍 ¿Qué acabamos de ver?

Se ha simulado una **comunicación en red** entre dos máquinas (por ejemplo, tu sistema anfitrión y una máquina virtual) usando **sockets** en Python. Esta comunicación es del tipo **cliente-servidor**, donde:

- El **servidor** espera conexiones.
    
- El **cliente** inicia la conexión y envía un mensaje.
    
- El **servidor** recibe el mensaje y lo muestra por pantalla.
    

Este modelo es la base de TODO: desde servicios web, mensajería instantánea, videollamadas, juegos online, hasta sistemas distribuidos.

---

### ✅ Código completo final:

#### 📡 `servidor.py` (ejecutar primero en la máquina virtual o servidor)

```python
import socket

# Crear el socket del servidor
servidor = socket.socket()

# Asociar el socket a una dirección IP y puerto
servidor.bind(('192.168.1.110', 5000))

# Escuchar conexiones entrantes
servidor.listen(1)
print("Servidor escuchando en 192.168.1.110:5000...")

# Aceptar la conexión del cliente
cliente_socket, cliente_address = servidor.accept()
print(f"Conexión establecida desde: {cliente_address}")

# Recibir mensaje del cliente
mensaje_recibido = cliente_socket.recv(1024)
print("Mensaje recibido:", mensaje_recibido.decode())

# Cerrar conexiones
cliente_socket.close()
servidor.close()
```

---

#### 🧑‍💻 `cliente.py` (ejecutar después en otra máquina)

```python
import socket

# Crear el socket del cliente
cliente = socket.socket()

# Conectar al servidor
cliente.connect(("192.168.1.110", 5000))

# Pedir mensaje al usuario
mensaje = input('Escribe lo que quieres enviar al servidor: ')

# Enviar el mensaje
cliente.send(mensaje.encode())

# Cerrar la conexión
cliente.close()
```

---

### 💡 Bonus: Cosas importantes para que funcione

1. Ambas máquinas deben estar en la misma red local (LAN).
    
2. La IP del servidor (`192.168.1.110`) debe ser accesible desde el cliente.
    
3. Asegúrate de que ningún firewall esté bloqueando el puerto `5000`.
    
4. Corre primero el **servidor** y luego el **cliente**.
    

---

