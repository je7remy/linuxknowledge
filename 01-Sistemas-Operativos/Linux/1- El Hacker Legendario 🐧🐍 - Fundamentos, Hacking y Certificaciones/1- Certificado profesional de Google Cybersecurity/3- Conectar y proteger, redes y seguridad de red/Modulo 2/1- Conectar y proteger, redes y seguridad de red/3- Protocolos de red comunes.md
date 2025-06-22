
En esta sección del curso, aprendió sobre los protocolos de red y cómo organizan la comunicación a través de una red. En esta lectura se analizarán los protocolos de red con más profundidad y se revisarán algunos protocolos básicos que ha aprendido anteriormente. También aprenderá nuevos protocolos y discutirá algunas de las formas en que los protocolos están involucrados en la seguridad de la red.

## Descripción general de los protocolos de red

Un **protocolo de red** es un conjunto de reglas utilizadas por dos o más dispositivos en una red para describir el orden de entrega y la estructura de los datos. Los protocolos de red sirven como instrucciones que vienen con la información en el paquete de datos. Estas instrucciones le dicen al dispositivo receptor qué hacer con los datos. Los protocolos son como un lenguaje común que permite que los dispositivos de todo el mundo se comuniquen y se entiendan entre sí.

A pesar de que los protocolos de red realizan una función esencial en la comunicación de red, los analistas de seguridad deben comprender sus implicaciones de seguridad asociadas. Algunos protocolos tienen vulnerabilidades que los actores maliciosos explotan. Por ejemplo, un actor malintencionado podría utilizar el protocolo del Sistema de Nombres de Dominio (DNS), que resuelve las direcciones web en direcciones IP, para desviar el tráfico de un sitio web legítimo a un sitio web malicioso que contenga malware. Aprenderá más sobre este tema en los próximos materiales del curso.

## Tres categorías de protocolos de red

Los protocolos de red se pueden dividir en tres categorías principales: protocolos de comunicación, protocolos de gestión y protocolos de seguridad. Hay docenas de protocolos de red diferentes, pero no es necesario memorizarlos todos para un puesto de analista de seguridad de nivel básico. Sin embargo, es importante que conozcas los que se enumeran en esta lectura.

### **Protocolos de comunicación**

Los protocolos de comunicación rigen el intercambio de información en la transmisión de red. Dictan cómo se transmiten los datos entre dispositivos y el momento de la comunicación. También incluyen métodos para recuperar datos perdidos en tránsito. Estos son algunos de ellos.

- **El protocolo de control de transmisión (TCP)** es un protocolo de comunicación por Internet que permite que dos dispositivos formen una conexión y transmitan datos. TCP utiliza un proceso de protocolo de enlace de tres vías. En primer lugar, el dispositivo envía una solicitud de sincronización (SYN) a un servidor. A continuación, el servidor responde con un paquete SYN/ACK para acusar recibo de la solicitud del dispositivo. Una vez que el servidor recibe el paquete ACK final del dispositivo, se establece una conexión TCP. En el modelo TCP/IP, TCP se produce en la capa de transporte.
    
- **El protocolo de datagramas de usuario (UDP)** es un protocolo sin conexión que no establece una conexión entre dispositivos antes de una transmisión. Esto lo hace menos confiable que TCP. Pero también significa que funciona bien para las transmisiones que necesitan llegar a su destino rápidamente. Por ejemplo, un uso de UDP es para enviar solicitudes DNS a servidores DNS locales. En el modelo TCP/IP, UDP se produce en la capa de transporte.
    
- **El protocolo de transferencia de hipertexto (HTTP)** es un protocolo de capa de aplicación que proporciona un método de comunicación entre los clientes y los servidores de sitios web. HTTP utiliza el puerto 80. HTTP se considera inseguro, por lo que está siendo reemplazado en la mayoría de los sitios web por una versión segura, llamada HTTPS, que utiliza el cifrado de SSL/TLS para la comunicación. Sin embargo, todavía hay muchos sitios web que utilizan el protocolo HTTP inseguro. En el modelo TCP/IP, HTTP se produce en la capa de aplicación.
    
- **El sistema de nombres de dominio (DNS)** es un protocolo que traduce los nombres de dominio de Internet en direcciones IP. Cuando un equipo cliente desea acceder al dominio de un sitio web utilizando su navegador de Internet, se envía una consulta a un servidor DNS dedicado. A continuación, el servidor DNS busca la dirección IP que corresponde al dominio del sitio web. DNS normalmente usa UDP en el puerto 53. Sin embargo, si la respuesta DNS a una solicitud es grande, cambiará al uso del protocolo TCP. En el modelo TCP/IP, DNS se produce en la capa de aplicación.
    

### **Protocolos de gestión**

La siguiente categoría de protocolos de red son los protocolos de gestión. Los protocolos de gestión se utilizan para supervisar y gestionar la actividad en una red. Incluyen protocolos para informar de errores y optimizar el rendimiento en la red.

- **El protocolo simple de administración de red (SNMP)** es un protocolo de red que se utiliza para monitorear y administrar dispositivos en una red. SNMP puede restablecer una contraseña en un dispositivo de red o cambiar su configuración de referencia. También puede enviar solicitudes a los dispositivos de red para obtener un informe sobre la cantidad de ancho de banda de la red que se está utilizando. En el modelo TCP/IP, SNMP se produce en la capa de aplicación.
    
- **El Protocolo de mensajes de control de Internet (ICMP)** es un protocolo de Internet utilizado por los dispositivos para informarse entre sí sobre errores de transmisión de datos a través de la red. ICMP es utilizado por un dispositivo receptor para enviar un informe al dispositivo emisor sobre la transmisión de datos. ICMP se usa comúnmente como una forma rápida de solucionar problemas de conectividad de red y latencia mediante la emisión del comando "ping" en un sistema operativo Linux. En el modelo TCP/IP, ICMP se produce en la capa de Internet.
    

### **Protocolos de seguridad**

Los protocolos de seguridad son protocolos de red que garantizan que los datos se envíen y reciban de forma segura a través de una red. Los protocolos de seguridad utilizan algoritmos de cifrado para proteger los datos en tránsito. A continuación se muestran algunos protocolos de seguridad comunes.

- **El protocolo de transferencia de hipertexto seguro (HTTPS)** es un protocolo de red que proporciona un método seguro de comunicación entre los clientes y los servidores del sitio web. HTTPS es una versión segura de HTTP que utiliza el cifrado de seguridad de la capa de sockets seguros/capa de transporte (SSL/TLS) en todas las transmisiones para que los actores maliciosos no puedan leer la información contenida. HTTPS utiliza el puerto 443. En el modelo TCP/IP, HTTPS se produce en la capa de aplicación.
    
- **El Protocolo seguro de transferencia de archivos (SFTP)** es un protocolo seguro que se utiliza para transferir archivos de un dispositivo a otro a través de una red. SFTP utiliza Secure Shell (SSH), normalmente a través del puerto TCP 22. SSH utiliza el estándar de cifrado avanzado (AES) y otros tipos de cifrado para garantizar que los destinatarios no deseados no puedan interceptar las transmisiones. En el modelo TCP/IP, SFTP se produce en la capa de aplicación. SFTP se usa a menudo con el almacenamiento en la nube. Cada vez que un usuario carga o descarga un archivo desde el almacenamiento en la nube, el archivo se transfiere utilizando el protocolo SFTP.
    

**Nota:** Los protocolos de cifrado mencionados no ocultan la dirección IP de origen o destino del tráfico de red. Esto significa que un actor malintencionado aún puede aprender información básica sobre el tráfico de la red si lo intercepta.

## Conclusiones clave

Los protocolos que aprendió en esta lectura son protocolos de red básicos que los analistas de ciberseguridad de nivel básico deben conocer. Comprender cómo funcionan los protocolos en una red es esencial. Los analistas de ciberseguridad pueden aprovechar su conocimiento de los protocolos para mitigar con éxito las vulnerabilidades de una red y, potencialmente, prevenir futuros ataques.