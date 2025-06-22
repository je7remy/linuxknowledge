
En lecturas y videos anteriores, aprendió cómo los protocolos de red organizan el envío y la recepción de datos a través de una red. También aprendió que los protocolos se pueden dividir en tres categorías: protocolos de comunicación, protocolos de administración y protocolos de seguridad.

Esta lectura le presentará algunos conceptos y protocolos adicionales que surgirán regularmente en su trabajo como analista de seguridad. A algunos protocolos se les asignan números de puerto por parte de la Autoridad de Números Asignados de Internet (IANA). Estos números de puerto se incluyen en la descripción de cada protocolo, si está asignado.

## Traducción de direcciones de red

Cada uno de los dispositivos de la red local de su hogar u oficina tiene una dirección IP privada que utilizan para comunicarse directamente entre sí. Sin embargo, para que los dispositivos con direcciones IP privadas se comuniquen con la red pública de Internet, deben tener una única dirección IP pública que represente todos los dispositivos de la LAN al público. Para los mensajes salientes, el router puede reemplazar una dirección IP de origen privada con su dirección IP pública y realizar la operación inversa para las respuestas. Este proceso se conoce como traducción de direcciones de red (NAT) y, por lo general, requiere que un enrutador o firewall esté configurado específicamente para realizar NAT. NAT es parte de la capa 2 (capa de Internet) y la capa 3 (capa de transporte) del modelo TCP/IP.

|**Direcciones IP privadas**|**Direcciones IP públicas**|
|---|---|
|- Asignado por el router<br>    <br>- Único solo dentro de la red privada<br>    <br>- Sin costo de uso<br>    <br>- Rangos de direcciones:<br>    <br>    - 10.0.0.0-10.255.255.255<br>        <br>    - 172.16.0.0-172.31.255.255<br>        <br>    - 192.168.0.0-192.168.255.255|- Asignado por ISP y IANA<br>    <br>- Dirección única en Internet global<br>    <br>- Costos de arrendamiento de una dirección IP pública<br>    <br>- Rangos de direcciones asignables:<br>    <br>    - 1.0.0.0-9.255.255.255<br>        <br>    - 11.0.0.0-126.255.255.255<br>        <br>    - 128.0.0.0-172.15.255.255<br>        <br>    - 172.32.0.0-192.167.255.255<br>        <br>    - 192.169.0.0-233.255.255.255|

## Protocolo de configuración dinámica de host

El protocolo de configuración dinámica de host (DHCP) pertenece a la familia de administración de protocolos de red. DHCP es un protocolo de capa de aplicación que se utiliza en una red para configurar dispositivos. Funciona con el router para asignar una dirección IP única a cada dispositivo y proporcionar las direcciones del servidor DNS adecuado y la puerta de enlace predeterminada para cada dispositivo. Los servidores DHCP funcionan en el puerto UDP 67, mientras que los clientes DHCP funcionan en el puerto UDP 68.

## Protocolo de resolución de direcciones

A estas alturas, ya está familiarizado con las direcciones IP y MAC. Ha aprendido que cada dispositivo de una red tiene una dirección IP pública, una dirección IP privada y una dirección MAC que lo identifican en la red. La dirección IP de un dispositivo puede cambiar con el tiempo, pero su dirección MAC es permanente porque es única para la tarjeta de interfaz de red de un dispositivo. La dirección MAC se utiliza para comunicarse con dispositivos dentro de la misma red, pero a veces, la dirección MAC es desconocida. Es por eso que se necesita el Protocolo de resolución de direcciones (ARP). ARP es principalmente un protocolo de capa de acceso a la red en el modelo TCP/IP que se utiliza para traducir las direcciones IP que se encuentran en los paquetes de datos a la dirección MAC del dispositivo de hardware.

Cada dispositivo de la red realiza ARP y realiza un seguimiento de las direcciones IP y MAC coincidentes en una caché ARP. ARP no tiene un número de puerto específico, ya que es un protocolo de capa 2 y los números de puerto están asociados con la capa de aplicación de capa 7.

## Telnet 

Telnet es un protocolo de capa de aplicación que se utiliza para conectarse con un sistema remoto. Telnet envía toda la información en texto claro. Utiliza indicaciones de línea de comandos para controlar otro dispositivo similar a Secure Shell (SSH), pero Telnet no es tan seguro como SSH. Telnet se puede utilizar para conectarse a dispositivos locales o remotos y utiliza el puerto TCP 23.

## Shell seguro

El protocolo de shell seguro (SSH) se utiliza para crear una conexión segura con un sistema remoto. Este protocolo de capa de aplicación proporciona una alternativa para la autenticación segura y la comunicación cifrada. SSH opera a través del puerto TCP 22 y es un reemplazo para protocolos menos seguros, como Telnet.

## Protocolo de Correos

El protocolo de oficina de correos (POP) es un protocolo de capa de aplicación (capa 4 del modelo TCP/IP) que se utiliza para administrar y recuperar correo electrónico de un servidor de correo. POP3 es la versión más utilizada de POP. Muchas organizaciones tienen un servidor de correo dedicado en la red que maneja el correo entrante y saliente para los usuarios de la red. Los dispositivos de usuario enviarán solicitudes al servidor de correo remoto y descargarán mensajes de correo electrónico localmente. Si alguna vez ha actualizado su aplicación de correo electrónico y ha aparecido nuevos correos electrónicos en su bandeja de entrada, está experimentando POP y el protocolo de acceso a mensajes de Internet (IMAP) en acción. La autenticación de texto sin formato sin cifrar utiliza el puerto TCP/UDP 110 y los correos electrónicos cifrados utilizan Secure Sockets Layer/Transport Layer Security (SSL/TLS) a través del puerto TCP/UDP 995. Cuando se usa POP, el correo debe terminar de descargarse en un dispositivo local antes de que se pueda leer. Después de la descarga, el correo puede o no eliminarse del servidor de correo, por lo que no garantiza que un usuario pueda sincronizar el mismo correo electrónico en varios dispositivos.

## Protocolo de acceso a mensajes de Internet (IMAP)

IMAP se utiliza para el correo electrónico entrante. Descarga los encabezados de los correos electrónicos y el contenido del mensaje. El contenido también permanece en el servidor de correo electrónico, lo que permite a los usuarios acceder a su correo electrónico desde varios dispositivos. IMAP utiliza el puerto TCP 143 para el correo electrónico sin cifrar y el puerto TCP 993 a través del protocolo TLS. El uso de IMAP permite a los usuarios leer parcialmente el correo electrónico antes de que termine de descargarse. Dado que el correo se mantiene en el servidor de correo, permite a un usuario sincronizar correos electrónicos en varios dispositivos.

## Protocolo simple de transferencia de correo

El Protocolo simple de transferencia de correo (SMTP) se utiliza para transmitir y enrutar el correo electrónico desde el remitente hasta la dirección del destinatario. SMTP funciona con el software Message Transfer Agent (MTA), que busca en los servidores DNS para resolver las direcciones de correo electrónico en direcciones IP, para garantizar que los correos electrónicos lleguen a su destino previsto. SMTP utiliza el puerto TCP/UDP 25 para los correos electrónicos no cifrados y el puerto TCP/UDP 587 utiliza TLS para los correos electrónicos cifrados. El puerto TCP 25 es utilizado a menudo por spam de gran volumen. SMTP ayuda a filtrar el spam regulando la cantidad de correos electrónicos que una fuente puede enviar a la vez.

## Protocolos y números de puerto

Recuerde que los números de puerto son utilizados por los dispositivos de red para determinar qué se debe hacer con la información contenida en cada paquete de datos una vez que llegan a su destino. Los firewalls pueden filtrar el tráfico no deseado en función de los números de puerto. Por ejemplo, una organización puede configurar un firewall para que solo permita el acceso al puerto TCP 995 (POP3) por parte de las direcciones IP que pertenecen a la organización.

Como analista de seguridad, deberá conocer muchos de los protocolos y números de puerto mencionados en este curso. Pueden usarse para determinar tus conocimientos técnicos en las entrevistas, por lo que es una buena idea memorizarlos. También aprenderá sobre nuevos protocolos en el trabajo en un puesto de seguridad.

## Conclusiones clave

Como analista de ciberseguridad, se encontrará con varios protocolos comunes en su trabajo diario. Los protocolos cubiertos en esta lectura incluyen NAT, DHCP, ARP, Telnet, SSH, POP3, IMAP y SMTP. Es igualmente importante comprender dónde está estructurado cada protocolo en el modelo TCP/IP y qué puertos ocupan.

|**Protocolo**|**Puerto**|
|---|---|
|DHCP|Puerto UDP 67 (servidores)<br><br>Puerto UDP 68 (clientes)|
|ARP|ninguno|
|Telnet|Puerto TCP 23|
|SSH|Puerto TCP 22|
|POP3|Puerto TCP/UDP 110 (sin cifrar)<br><br>Puerto TCP/UDP 995 (cifrado, SSL/TLS)|
|IMAP|Puerto TCP 143 (sin cifrar)<br><br>Puerto TCP 993 (cifrado, SSL/TLS)|
|SMTP|Puerto TCP/UDP 25 (sin cifrar)|
|SMTPS|Puerto TCP/UDP 587 (cifrado, TLS)|

