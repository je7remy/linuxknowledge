
Un **analizador de protocolos de red**, a veces denominado sniffer de paquetes o analizador de paquetes, es una herramienta diseñada para capturar y analizar el tráfico de datos dentro de una red. Suelen utilizarse como herramientas de investigación para monitorizar redes e identificar actividades sospechosas. Existe una gran variedad de analizadores de protocolos de red, pero algunos de los más comunes son:

- Analizador de Tráfico NetFlow de SolarWinds
    
- ManageEngine OpManager
    
- Observador de redes Azure
    
- Wireshark
    
- tcpdump
    

Esta lectura se centrará exclusivamente en tcpdump, aunque puede aplicar lo que aprenda aquí a muchos de los otros analizadores de protocolos de red que utilizará como analista de ciberseguridad para defenderse de cualquier intrusión en la red. En una próxima actividad, revisará un registro de Tráfico de Datos de tcpdump e identificará un ataque DoS para practicar estas habilidades.

## tcpdump

**tcpdump** es un analizador de protocolos de red de línea de comandos. Es popular, ligero -lo que significa que utiliza poca memoria y tiene un bajo uso de CPU- y utiliza la biblioteca de código abierto libpcap. tcpdump está basado en texto, lo que significa que todos los comandos de tcpdump se ejecutan en el terminal. También puede instalarse en otros sistemas operativos basados en Unix, como macOS®. Está preinstalado en muchas distribuciones de Linux.

tcpdump proporciona un breve análisis de paquetes y convierte la información clave sobre el tráfico de red en formatos fácilmente legibles por humanos. Imprime información sobre cada paquete directamente en su terminal. tcpdump también muestra la dirección IP de origen, las direcciones IP de destino y los números de puerto que se están utilizando en las comunicaciones.

## Interpretar la salida

tcpdump imprime la salida del comando como los paquetes olfateados en la línea de comandos, y opcionalmente en un archivo de registro, después de ejecutar un comando. La salida de una captura de paquetes contiene muchas piezas de información importante sobre el tráfico de la red.

![tipos de información presentados en una captura de paquetes tcpdump.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/B-PaECh0ToSFgBWpFczYZg_4896abe8c06443f08eec4dc003dcf8f1_image.png?expiry=1751068800000&hmac=rVHykQQbFjIzp2NHYrwARbwDDhYMAFCTK10ppZK1t0s)

Alguna de la información que recibe de una captura de paquetes incluye:

- **Marca** de tiempo: La salida comienza con la marca de tiempo, formateada como horas, minutos, segundos y fracciones de segundo.
    
- **IP** de origen: El origen del paquete lo proporciona su dirección IP de origen.
    
- **Puerto** de origen: Este número de puerto es donde se originó el paquete.
    
- **IP** de destino: La dirección IP de destino es hacia dónde se está transmitiendo el paquete.
    
- **Puerto de** destino: Este número de puerto es hacia donde se está transmitiendo el paquete.
    

**Nota:** Por defecto, tcpdump intentará resolver las direcciones de host a nombres de host. También sustituirá los números de puerto por servicios comúnmente asociados que utilicen estos puertos.

## Usos comunes

tcpdump y otros analizadores de protocolos de red se utilizan habitualmente para capturar y visualizar las comunicaciones de red y para recopilar estadísticas sobre la red, como la solución de problemas de rendimiento de la red. También pueden utilizarse para:

- Establecer una línea de base para los patrones de tráfico de red y las métricas de utilización de la red.
    
- Detectar e identificar el tráfico malicioso
    
- Crear alertas personalizadas para enviar las notificaciones adecuadas cuando surjan problemas en la red o amenazas a la seguridad.
    
- Localizar la mensajería instantánea (MI), el tráfico o los puntos de acceso inalámbricos no autorizados.
    

Sin embargo, los atacantes también pueden utilizar los analizadores de protocolos de red de forma maliciosa para obtener información sobre una red específica. Por ejemplo, los atacantes pueden capturar paquetes de datos que contengan información confidencial, como nombres de usuario de cuentas y contraseñas. Como analista de ciberseguridad, es importante comprender la finalidad y los usos de los analizadores de protocolos de red.

## Puntos clave

Los analizadores de protocolos de red, como tcpdump, son herramientas comunes que pueden utilizarse para supervisar los patrones de tráfico de red e investigar actividades sospechosas. tcpdump es un analizador de protocolos de red de línea de comandos compatible con Linux/Unix y macOS®. Cuando ejecute un comando tcpdump, la herramienta mostrará información sobre el enrutamiento de paquetes, como la marca de tiempo, la dirección IP de origen y el número de puerto, y la dirección IP de destino y el número de puerto. Por desgracia, los atacantes también pueden utilizar analizadores de protocolos de red para capturar paquetes de datos que contengan información confidencial, como nombres de usuario y contraseñas de cuentas.