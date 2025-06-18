
Hasta ahora, en esta sección del curso, aprendió sobre los componentes de una red, los dispositivos de red y cómo se produce la comunicación a través de una red. También ha estudiado el modelo TCP/IP para comprender cómo se organiza la comunicación de red en las diferentes capas de Internet.

Toda la comunicación en una red se organiza mediante protocolos de red. Anteriormente, aprendió sobre el Protocolo de control de transmisión (TCP), que establece conexiones entre dos dispositivos, y el Protocolo de Internet (IP), que se usa para enrutar y direccionar paquetes de datos a medida que viajan entre dispositivos en una red. Estos protocolos se utilizan en capas específicas de Internet en el modelo TCP/IP. El modelo TCP/IP de 4 capas es una forma condensada del modelo OSI (interconexión de sistemas abiertos), que se compone de 7 capas. El modelo OSI proporcionará una comprensión más profunda de los procesos que ocurren en cada capa. Trabajaremos hacia atrás desde la capa siete hasta la capa uno, pasando de los procesos que implican la interacción directa del usuario con la red a los que implican la conexión física a Internet a través de componentes de red como cables y conmutadores. En esta lectura también se revisarán las principales diferencias entre los modelos TCP/IP y OSI.

## El modelo TCP/IP frente al modelo OSI

El **modelo TCP/IP** es un marco utilizado para visualizar cómo se organizan y transmiten los datos a través de una red. Este modelo ayuda a los ingenieros de redes y analistas de seguridad a conceptualizar los procesos en la red y a comunicar dónde se producen interrupciones o amenazas de seguridad.

El modelo TCP/IP tiene cuatro capas: la capa de acceso a la red, la capa de Internet, la capa de transporte y la capa de aplicación. Al analizar los eventos de red, los profesionales de seguridad pueden determinar en qué capa o capas se produjo un ataque en función de los procesos involucrados en el incidente.

El **modelo OSI** es un concepto estandarizado que describe las siete capas que utilizan los ordenadores para comunicarse y enviar datos a través de la red. Los profesionales de redes y seguridad a menudo usan este modelo para comunicarse entre sí sobre posibles fuentes de problemas o amenazas de seguridad cuando ocurren.

![The seven layers of the OSI model labeled application, presentation, session, transport, network, data link, and physical](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/b5ghKGCVSp6e-fAUC8oo4w_4efb617fe17648559c4a8a0bc0b1abf1_CS_R-043_OSI-Model.png?expiry=1750377600000&hmac=D-277xZeIAcC-1loGNijllQTFnmAhbfgQfE6lx-8coc)

Algunas organizaciones dependen en gran medida del modelo TCP/IP, mientras que otras prefieren utilizar el modelo OSI. Como analista de seguridad, es importante estar familiarizado con ambos modelos. Tanto el modelo TCP/IP como el OSI son útiles para comprender cómo funcionan las redes.

## Capa 7: Capa de aplicación

La capa de aplicación incluye procesos que involucran directamente al usuario cotidiano. Esta capa incluye todos los protocolos de red que utilizan las aplicaciones de software para conectar a un usuario a Internet. Esta característica es el rasgo identificativo de la capa de aplicación: la conexión del usuario a Internet a través de aplicaciones y solicitudes.

Un ejemplo de un tipo de comunicación que se produce en la capa de aplicación es el uso de un navegador web. El navegador de Internet utiliza HTTP o HTTPS para enviar y recibir información del servidor del sitio web. La aplicación de correo electrónico utiliza el protocolo simple de transferencia de correo (SMTP) para enviar y recibir información de correo electrónico. Además, los navegadores web utilizan el protocolo del sistema de nombres de dominio (DNS) para traducir los nombres de dominio de los sitios web en direcciones IP que identifican al servidor web que aloja la información del sitio web.

## Capa 6: Capa de presentación

Las funciones de la capa de presentación implican la traducción de datos y el cifrado de la red. Esta capa añade y reemplaza datos con formatos que pueden ser entendidos por las aplicaciones (capa 7) tanto en los sistemas emisores como en los receptores. Los formatos en el extremo del usuario pueden ser diferentes de los del sistema receptor. Los procesos en la capa de presentación requieren el uso de un formato estandarizado.

Algunas funciones de formato que se producen en la capa 6 incluyen el cifrado, la compresión y la confirmación de que el conjunto de códigos de caracteres se puede interpretar en el sistema receptor. Un ejemplo de encriptación que tiene lugar en esta capa es SSL, que encripta los datos entre servidores web y navegadores como parte de sitios web con HTTPS.

## Capa 5: Capa de sesión

Una sesión describe cuando se establece una conexión entre dos dispositivos. Una sesión abierta permite que los dispositivos se comuniquen entre sí. Los protocolos de capa de sesión mantienen la sesión abierta mientras se transfieren los datos y finalizan la sesión una vez que se completa la transmisión.

La capa de sesión también es responsable de actividades como la autenticación, la reconexión y la configuración de puntos de control durante una transferencia de datos. Si se interrumpe una sesión, los puntos de control garantizan que la transmisión se reanude en el último punto de control de la sesión cuando se reanude la conexión. Las sesiones incluyen una solicitud y una respuesta entre aplicaciones. Las funciones de la capa de sesión responden a las solicitudes de servicio de los procesos de la capa de presentación (capa 6) y envían solicitudes de servicios a la capa de transporte (capa 4).

## Capa 4: Capa de transporte

La capa de transporte se encarga de entregar datos entre dispositivos. Esta capa también maneja la velocidad de transferencia de datos, el flujo de la transferencia y la división de datos en segmentos más pequeños para que sean más fáciles de transportar. La segmentación es el proceso de dividir una gran transmisión de datos en partes más pequeñas que pueden ser procesadas por el sistema receptor. Estos segmentos deben volver a ensamblarse en su destino para que puedan procesarse en la capa de sesión (capa 5). La velocidad y la tasa de transmisión también deben coincidir con la velocidad de conexión del sistema de destino. TCP y UDP son protocolos de capa de transporte.

## Capa 3: Capa de red

La capa de red supervisa la recepción de las tramas de la capa de enlace de datos (capa 2) y las entrega al destino previsto. El destino previsto se puede encontrar en función de la dirección que reside en la trama de los paquetes de datos. Los paquetes de datos permiten la comunicación entre dos redes. Estos paquetes incluyen direcciones IP que indican a los routers dónde enviarlos. Se enrutan desde la red de envío a la red de recepción.

## Capa 2: Capa de enlace de datos

La capa de enlace de datos organiza el envío y la recepción de paquetes de datos dentro de una sola red. La capa de enlace de datos alberga los conmutadores de la red local y las tarjetas de interfaz de red en los dispositivos locales.

En la capa de enlace de datos se utilizan protocolos como el protocolo de control de red (NCP), el control de enlace de datos de alto nivel (HDLC) y el protocolo de control de enlace de datos síncrono (SDLC).

## Capa 1: Capa física

Como su nombre indica, la capa física corresponde al hardware físico involucrado en la transmisión de la red. Los concentradores, los módems y los cables y el cableado que los conectan se consideran parte de la capa física. Para viajar a través de un cable Ethernet o coaxial, un paquete de datos debe traducirse a un flujo de 0 y 1. El flujo de 0 y 1 se envía a través del cableado y los cables físicos, se recibe y luego se pasa a los niveles superiores del modelo OSI.

## Conclusiones clave

Tanto el modelo TCP/IP como el OSI son modelos conceptuales que ayudan a los profesionales de redes a diseñar procesos y protocolos de red con respecto a la transmisión de datos entre dos o más sistemas. El modelo OSI contiene siete capas de comunicación. Los profesionales de redes y seguridad utilizan el modelo OSI para comunicarse entre sí sobre posibles fuentes de problemas o amenazas de seguridad cuando se producen. Los ingenieros de redes y los analistas de seguridad de redes utilizan los modelos TCP/IP y OSI para conceptualizar los procesos de red y comunicar la ubicación de interrupciones o amenazas.