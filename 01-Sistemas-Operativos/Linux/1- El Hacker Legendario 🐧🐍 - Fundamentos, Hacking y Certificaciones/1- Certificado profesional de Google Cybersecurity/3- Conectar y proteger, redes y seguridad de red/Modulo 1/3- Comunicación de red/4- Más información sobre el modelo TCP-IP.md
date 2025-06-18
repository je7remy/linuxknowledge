
En esta lectura, se basará en lo que ha aprendido sobre el modelo de Protocolo de control de transmisión/Protocolo de Internet (TCP/IP), considerará las diferencias entre el modelo de interconexión de sistemas abiertos (OSI) y el modelo TCP/IP, y aprenderá cómo se relacionan. A continuación, revisará cada capa del modelo TCP/IP y repasará los protocolos comunes que se usan en cada capa.

Como profesional de la seguridad, es importante que comprenda el modelo TCP/IP porque describe las funciones de varios protocolos de red. El modelo TCP/IP se basa en el conjunto de protocolos TCP/IP que incluye todos los protocolos de red que admiten el protocolo TCP/IP principal. Para reiterar las lecciones anteriores, un protocolo de red, también conocido como protocolo de Internet, es un conjunto de estándares utilizados para enrutar y direccionar paquetes de datos a medida que viajan entre dispositivos en una red. En esta lectura, aprenderá qué protocolos de red operan en qué capas de comunicación del modelo TCP/IP. Los dos modelos más comunes disponibles son el TCP/IP y el modelo OSI. Estos modelos son una guía representativa de cómo los hosts se comunican a través de una red. Los ejemplos proporcionados en este curso seguirán el modelo TCP/IP.

## El modelo TCP/IP

El **modelo TCP/IP** es un marco utilizado para visualizar cómo se organizan y transmiten los datos a través de una red. Este modelo ayuda a los ingenieros de redes y a los analistas de seguridad de redes a conceptualizar los procesos de la red y a comunicar dónde se producen interrupciones o amenazas de seguridad.

El modelo TCP/IP tiene cuatro capas: la capa de acceso a la red, la capa de Internet, la capa de transporte y la capa de aplicación. Al solucionar problemas en la red, los profesionales de seguridad pueden analizar qué capas se vieron afectadas por un ataque en función de los procesos involucrados en un incidente.

![Las cuatro capas del modelo TCP/IP etiquetadas como capa de aplicación, capa de transporte, capa de Internet y capa de acceso a la red](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/H9jj1YSsSDKlU8c8qzOgsQ_89f77799b50040b08911a8de1012e2f1_CS_R-210_S33G011-edited.png?expiry=1750377600000&hmac=HUcsCQX7qo-Zq98Hs9gciKUrbI3DIBQSrnkk-INBdzg)

## Capa de acceso a la red

La capa de acceso a la red, a veces llamada capa de enlace de datos, se ocupa de la creación de paquetes de datos y su transmisión a través de una red. Esta capa corresponde al hardware físico involucrado en la transmisión de la red. Los concentradores, los módems, los cables y el cableado se consideran parte de esta capa. El protocolo de resolución de direcciones (ARP) forma parte de la capa de acceso a la red. Dado que las direcciones MAC se utilizan para identificar hosts en la misma red física, se necesita ARP para asignar direcciones IP a direcciones MAC para la comunicación de red local.

## Capa de Internet

La capa de Internet, a veces denominada capa de red, es responsable de garantizar la entrega al host de destino, que potencialmente reside en una red diferente. Garantiza que las direcciones IP se adjunten a los paquetes de datos para indicar la ubicación del remitente y el receptor. La capa de Internet también determina qué protocolo es responsable de entregar los paquetes de datos y garantiza la entrega al host de destino. Estos son algunos de los protocolos comunes que operan en la capa de Internet:

- **Protocolo de Internet (IP).** IP envía los paquetes de datos al destino correcto y se basa en el Protocolo de control de transmisión/Protocolo de datagramas de usuario (TCP/UDP) para entregarlos al servicio correspondiente. Los paquetes IP permiten la comunicación entre dos redes. Se enrutan desde la red de envío a la red de recepción. TCP, en particular, retransmite cualquier dato que se haya perdido o dañado.
    
- **Protocolo de mensajes de control de Internet (ICMP).** El ICMP comparte información de error y actualizaciones de estado de los paquetes de datos. Esto es útil para detectar y solucionar errores de red. El ICMP informa sobre los paquetes que se descartaron o que desaparecieron en tránsito, los problemas con la conectividad de red y los paquetes redirigidos a otros enrutadores.
    

## Capa de transporte

La capa de transporte es responsable de entregar datos entre dos sistemas o redes e incluye protocolos para controlar el flujo de tráfico a través de una red. TCP y UDP son los dos protocolos de transporte que se producen en esta capa.

### Protocolo de control de transmisión

El **Protocolo de control de transmisión (TCP)** es un protocolo de comunicación por Internet que permite que dos dispositivos formen una conexión y transmitan datos. Garantiza que los datos se transmitan de forma fiable al servicio de destino. TCP contiene el número de puerto del servicio de destino previsto, que reside en el encabezado TCP de un paquete TCP/IP.

### Protocolo de datagramas de usuario

El **protocolo de datagramas de usuario (UDP)** es un protocolo sin conexión que no establece una conexión entre dispositivos antes de las transmisiones. Es utilizado por aplicaciones que no se preocupan por la confiabilidad de la transmisión. Los datos enviados a través de UDP no se rastrean tan extensamente como los datos enviados mediante TCP. Debido a que UDP no establece conexiones de red, se usa principalmente para aplicaciones sensibles al rendimiento que operan en tiempo real, como la transmisión de video.

## Capa de aplicación

La capa de aplicación en el modelo TCP/IP es similar a las capas de aplicación, presentación y sesión del modelo OSI. La capa de aplicación es responsable de realizar solicitudes de red o responder a las solicitudes. Esta capa define a qué servicios y aplicaciones de Internet puede acceder cualquier usuario. Los protocolos de la capa de aplicación determinan cómo interactuarán los paquetes de datos con los dispositivos receptores. Algunos protocolos comunes utilizados en esta capa son:

- Protocolo de transferencia de hipertexto (HTTP)
    
- Protocolo simple de transferencia de correo (SMTP)
    
- Shell seguro (SSH)
    
- Protocolo de transferencia de archivos (FTP)
    
- Sistema de nombres de dominio (DNS)
    

Los protocolos de la capa de aplicación se basan en las capas subyacentes para transferir los datos a través de la red.

## Modelo TCP/IP frente a modelo OSI

![El modelo TCP/IP junto al modelo OSI](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/RbNt47PDRTGJZ6q_QtaNMg_9b9098ac04e84c2d8ad04b220c5456f1_CS_R-210_TCP-vs-OSI.png?expiry=1750377600000&hmac=tyZmdh204yVmcZYF2ma1AKqIAk3MBnyACdTnBYJwxDQ)

El **OSI** organiza visualmente los protocolos de red en diferentes capas. Los profesionales de redes a menudo utilizan este modelo para comunicarse entre sí sobre posibles fuentes de problemas o amenazas de seguridad cuando ocurren.

El modelo TCP/IP combina varias capas del modelo OSI. Hay muchas similitudes entre los dos modelos. Ambos modelos definen estándares para las redes y dividen el proceso de comunicación en red en diferentes capas. El modelo TCP/IP es una versión simplificada del modelo OSI.

## Conclusiones clave

Tanto el modelo TCP/IP como el OSI son modelos conceptuales que ayudan a los profesionales de redes a visualizar los procesos y protocolos de red en lo que respecta a la transmisión de datos entre dos o más sistemas. El modelo TCP/IP contiene cuatro capas y el modelo OSI contiene siete capas.