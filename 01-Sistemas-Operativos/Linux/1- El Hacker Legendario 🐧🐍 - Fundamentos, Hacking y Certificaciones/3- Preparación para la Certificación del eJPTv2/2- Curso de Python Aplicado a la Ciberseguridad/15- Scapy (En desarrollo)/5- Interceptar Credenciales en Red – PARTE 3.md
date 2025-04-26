
---

### **Contexto General**
El objetivo de los scripts es capturar (o "sniffear") paquetes de red que se transmiten a través del puerto 80, que es el puerto predeterminado para el protocolo HTTP. Estos paquetes suelen contener solicitudes y respuestas de servicios web que no están cifrados (es decir, no usan HTTPS). Scapy es una biblioteca poderosa para manipulación y análisis de paquetes de red, y aquí se usa para inspeccionar el contenido de los paquetes TCP que transportan datos HTTP.

Los scripts evolucionan desde una versión básica que captura datos crudos hasta una más específica que filtra solicitudes HTTP. 

---

## **Versión 1: Captura básica de datos crudos**

```python
from scapy.all import sniff, TCP, Raw
from scapy.layers.http import HTTPRequest

def procesar_paquetes(paquete):
    if paquete.haslayer(Raw):
        raw_data = paquete.getlayer(Raw)
        print(f"Datos: {raw_data}")

def empezar_sniffing(interfaz):
    print(f"Iniciando sniffing en la interfaz {interfaz}")
    sniff(iface=interfaz, filter="tcp port 80", prn=procesar_paquetes, store=False)

empezar_sniffing("docker0")
```

### **Explicación Detallada**

1. **Importaciones**:
   - `from scapy.all import sniff, TCP, Raw`: Importa las funciones y clases necesarias de Scapy.
     - `sniff`: Función principal para capturar paquetes de red.
     - `TCP`: Clase que representa la capa del protocolo TCP.
     - `Raw`: Clase que representa datos crudos (payload) en un paquete.
   - `from scapy.layers.http import HTTPRequest`: Importa la clase `HTTPRequest` para manejar solicitudes HTTP. **Nota**: En esta versión, aunque se importa `HTTPRequest`, no se usa, lo que indica que podría ser un residuo de una versión anterior o una preparación para futuras mejoras.

2. **Función `procesar_paquetes(paquete)`**:
   - Esta función se ejecuta para cada paquete capturado.
   - `if paquete.haslayer(Raw)`: Verifica si el paquete tiene una capa `Raw`, que contiene los datos crudos (payload) del paquete, como el contenido de una solicitud o respuesta HTTP.
   - `raw_data = paquete.getlayer(Raw)`: Obtiene la capa `Raw` del paquete.
   - `print(f"Datos: {raw_data}")`: Imprime los datos crudos. Sin embargo, aquí no se decodifican, por lo que `raw_data` es un objeto de Scapy que puede incluir bytes no legibles directamente (por ejemplo, datos binarios).

3. **Función `empezar_sniffing(interfaz)`**:
   - Imprime un mensaje indicando que el sniffing comienza en la interfaz especificada (en este caso, `"docker0"`).
   - `sniff(iface=interfaz, filter="tcp port 80", prn=procesar_paquetes, estore=False)`:
     - `iface=interfaz`: Especifica la interfaz de red donde se capturarán los paquetes (aquí, `"docker0"`, una interfaz común en entornos Docker).
     - `filter="tcp port 80"`: Aplica un filtro BPF (Berkeley Packet Filter) para capturar solo paquetes TCP que usen el puerto 80 (HTTP).
     - `prn=procesar_paquetes`: Indica que cada paquete capturado se pasará a la función `procesar_paquetes` para su procesamiento.
     - `estore=False`: Desactiva el almacenamiento de paquetes en memoria, lo que reduce el uso de recursos pero impide acceder a los paquetes capturados después.

4. **Ejecución**:
   - `empezar_sniffing("docker0")`: Inicia el sniffing en la interfaz `docker0`.

### **Limitaciones de esta versión**
- **Datos no decodificados**: Los datos en la capa `Raw` se imprimen como un objeto de Scapy, no como una cadena legible. Esto puede incluir bytes binarios o datos no interpretables directamente.
- **Falta de especificidad**: No filtra específicamente solicitudes HTTP, solo verifica si hay una capa `Raw`. Esto significa que captura cualquier paquete TCP en el puerto 80, incluyendo tráfico no HTTP (por ejemplo, WebSockets o protocolos personalizados).
- **Importación no utilizada**: `HTTPRequest` se importa pero no se usa, lo que sugiere que el código es un punto de partida o está incompleto.

### **Uso**
Esta versión es útil para inspeccionar tráfico TCP genérico en el puerto 80, pero no es práctica para analizar solicitudes HTTP específicas porque los datos no se decodifican y no se filtran por tipo de protocolo.

---

## **Versión 2: Decodificación de datos crudos**

```python
from scapy.all import sniff, TCP, Raw
from scapy.layers.http import HTTPRequest

def procesar_paquetes(paquete):
    if paquete.haslayer(Raw):
        raw_data = paquete.getlayer(Raw).load.decode()
        print(f"Datos: {raw_data}")

def empezar_sniffing(interfaz):
    print(f"Iniciando sniffing en la interfaz {interfaz}")
    sniff(iface=interfaz, filter="tcp port 80", prn=procesar_paquetes, store=False)

empezar_sniffing("docker0")
```

### **Evolución y Cambios**
La principal diferencia con la versión 1 está en la función `procesar_paquetes`, específicamente en cómo se manejan los datos crudos.

### **Explicación Detallada**

1. **Importaciones**: Identicas a la versión 1. Nuevamente, `HTTPRequest` no se usa, lo que indica que sigue siendo un código en transición.

2. **Función `procesar_paquetes(paquete)`**:
   - `if paquete.haslayer(Raw)`: Igual que antes, verifica si el paquete tiene una capa `Raw`.
   - `raw_data = paquete.getlayer(Raw).load.decode()`:
     - `paquete.getlayer(Raw).load`: Accede al contenido (payload) de la capa `Raw`, que es un objeto de bytes.
     - `.decode()`: Intenta convertir los bytes a una cadena de texto, asumiendo una codificación como UTF-8 (por defecto). Esto hace que los datos sean legibles si contienen texto, como una solicitud HTTP (por ejemplo, `GET /index.html HTTP/1.1`).
   - `print(f"Datos: {raw_data}")`: Imprime los datos decodificados, que ahora deberían ser más legibles si el payload contiene texto HTTP.

3. **Función `empezar_sniffing(interfaz)`**: Sin cambios respecto a la versión 1.

### **Mejoras**
- **Datos legibles**: Al decodificar los datos con `.decode()`, el script ahora puede mostrar el contenido de las solicitudes o respuestas HTTP en formato de texto, lo que es mucho más útil para inspeccionar tráfico web.
- **Mantenimiento de simplicidad**: Sigue siendo un script simple, pero ahora es más práctico para analizar tráfico HTTP.

### **Limitaciones**
- **Errores de decodificación**: Si los datos en la capa `Raw` no son texto (por ejemplo, datos binarios como imágenes), `.decode()` puede generar una excepción (`UnicodeDecodeError`). El código no maneja estos casos.
- **Falta de filtrado HTTP**: Todavía captura cualquier paquete TCP en el puerto 80, no solo solicitudes HTTP. Esto puede incluir ruido (tráfico no relacionado con HTTP).
- **Interfaz `docker0`**: La elección de la interfaz `docker0` limita el uso a entornos con Docker. En un sistema diferente, podría necesitarse otra interfaz (por ejemplo, `eth0` o `wlan0`).

### **Uso**
Esta versión es adecuada para inspeccionar tráfico HTTP en texto plano en el puerto 80, como solicitudes GET o POST. Sin embargo, sigue siendo genérica y no está optimizada para manejar solo solicitudes HTTP.

---

## **Versión 3: Filtrado específico de solicitudes HTTP**

```python
from scapy.all import sniff, TCP, Raw
from scapy.layers.http import HTTPRequest

def procesar_paquetes(paquete):
    if paquete.haslayer(HTTPRequest):
        if paquete.haslayer(Raw):
            raw_data = paquete.getlayer(Raw).load.decode()
            print(f"Datos: {raw_data}")

def empezar_sniffing(interfaz):
    print(f"Iniciando sniffing en la interfaz {interfaz}")
    sniff(iface=interfaz, filter="tcp port 80", prn=procesar_paquetes, store=False)

empezar_sniffing("docker0")
```

### **Evolución y Cambios**
Esta versión introduce un filtro adicional en la función `procesar_paquetes` para procesar solo paquetes que contengan una solicitud HTTP, haciendo uso de la clase `HTTPRequest` importada.

### **Explicación Detallada**

1. **Importaciones**: Sin cambios respecto a las versiones anteriores. Ahora se usa `HTTPRequest`, lo que justifica su importación.

2. **Función `procesar_paquetes(paquete)`**:
   - `if paquete.haslayer(HTTPRequest)`: Verifica si el paquete contiene una capa `HTTPRequest`, que representa una solicitud HTTP (por ejemplo, GET, POST, etc.). Esto asegura que solo se procesen paquetes que Scapy identifica como solicitudes HTTP válidas.
   - `if paquete.haslayer(Raw)`: Dentro del bloque `HTTPRequest`, verifica si hay una capa `Raw`. Esto es importante porque las solicitudes HTTP pueden incluir un cuerpo (por ejemplo, en un POST), que se almacena en la capa `Raw`.
   - `raw_data = paquete.getlayer(Raw).load.decode()`: Igual que en la versión 2, decodifica los datos crudos para hacerlos legibles.
   - `print(f"Datos: {raw_data}")`: Imprime los datos decodificados, que ahora deberían corresponder al cuerpo de una solicitud HTTP (si existe).

3. **Función `empezar_sniffing(interfaz)`**: Sin cambios.

### **Mejoras**
- **Filtrado específico**: Al usar `paquete.haslayer(HTTPRequest)`, el script ignora paquetes TCP en el puerto 80 que no sean solicitudes HTTP, como respuestas HTTP, tráfico no HTTP, o protocolos personalizados.
- **Uso de `HTTPRequest`**: Aprovecha la capacidad de Scapy para parsear solicitudes HTTP, lo que hace que el script sea más robusto y enfocado.
- **Eficiencia**: Al filtrar antes de procesar, reduce la cantidad de datos impresos, mostrando solo lo relevante.

### **Limitaciones**
- **Solo solicitudes HTTP**: El script solo captura solicitudes (`HTTPRequest`), no respuestas HTTP. Esto puede ser intencional, pero limita su capacidad para analizar el tráfico completo de un servicio web.
- **Errores de decodificación**: Como en la versión 2, no maneja excepciones si los datos en `Raw` no son texto.
- **Interfaz específica**: La interfaz `docker0` sigue siendo un punto de configuración que puede no ser adecuada para todos los entornos.
- **Falta de detalles HTTP**: Aunque filtra solicitudes HTTP, no extrae información específica como el método (GET, POST), la URL, o los encabezados, lo que podría ser útil para un análisis más profundo.

### **Uso**
Esta versión es ideal para monitorear solicitudes HTTP específicas en un servicio web que opera en el puerto 80. Por ejemplo, podría usarse para depurar una aplicación web en un entorno Docker, capturando solo las solicitudes enviadas por los clientes.

---

## **Evolución General**
La evolución de los scripts refleja un refinamiento progresivo:
1. **Versión 1**: Captura cualquier paquete TCP en el puerto 80 con datos crudos, pero los datos no son legibles.
2. **Versión 2**: Mejora la legibilidad decodificando los datos crudos, pero aún captura tráfico no específico.
3. **Versión 3**: Filtra solo solicitudes HTTP, haciendo el script más preciso y útil para analizar tráfico web.

Cada versión aborda una limitación de la anterior, mejorando la funcionalidad y especificidad.

---

## **Consideraciones Técnicas y Mejoras Potenciales**

1. **Manejo de excepciones**:
   - Agregar un bloque `try-except` alrededor de `.decode()` para manejar casos donde los datos no son texto:
     ```python
     try:
         raw_data = paquete.getlayer(Raw).load.decode()
         print(f"Datos: {raw_data}")
     except UnicodeDecodeError:
         print("Datos no decodificables (binarios)")
     ```

2. **Extracción de detalles HTTP**:
   - Usar atributos de la capa `HTTPRequest` para mostrar información específica:
     ```python
     if paquete.haslayer(HTTPRequest):
         http_layer = paquete.getlayer(HTTPRequest)
         print(f"Método: {http_layer.Method.decode()}")
         print(f"URL: {http_layer.Path.decode()}")
         print(f"Host: {http_layer.Host.decode()}")
     ```

3. **Captura de respuestas HTTP**:
   - Para capturar respuestas, se puede usar la clase `HTTPResponse` (disponible en Scapy):
     ```python
     from scapy.layers.http import HTTPResponse
     if paquete.haslayer(HTTPResponse):
         print("Respuesta HTTP detectada")
     ```

4. **Interfaz dinámica**:
   - Permitir que el usuario especifique la interfaz como argumento o detectar interfaces disponibles:
     ```python
     from scapy.all import get_if_list
     print("Interfaces disponibles:", get_if_list())
     ```

5. **Soporte para HTTPS**:
   - El script solo captura HTTP (puerto 80). Para HTTPS (puerto 443), se necesitaría descifrado (por ejemplo, con un proxy como `mitmproxy`), ya que los datos están cifrados.

6. **Almacenamiento de paquetes**:
   - Cambiar `estore=False` a `estore=True` o guardar paquetes en un archivo con `wrpcap` para análisis posterior:
     ```python
     sniff(..., store=True)
     wrpcap("captura.pcap", paquetes)
     ```

---

## **Ejemplo de Uso Práctico**
Supongamos que tienes un contenedor Docker ejecutando un servidor web en `docker0` que sirve una página en `http://localhost:80`. Este script puede capturar las solicitudes GET o POST enviadas al servidor. Por ejemplo, si un cliente envía:
```
GET /index.html HTTP/1.1
Host: localhost
```
El script (versión 3) imprimirá el cuerpo de la solicitud (si lo hay) y, con las mejoras sugeridas, podría mostrar el método (`GET`), la URL (`/index.html`), etc.

---

## **Conclusión**
Los tres scripts representan una progresión lógica hacia un sniffer más específico y útil para tráfico HTTP. La versión final es la más adecuada para monitorear solicitudes HTTP en un servicio web no cifrado. Sin embargo, para un uso en producción, se recomiendan mejoras como manejo de errores, extracción de detalles HTTP, y soporte para respuestas o interfaces dinámicas. La elección de `docker0` sugiere un entorno específico (Docker), pero el código es adaptable a otras interfaces con ajustes mínimos.
