
Anteriormente, se le presentaron los ataques de denegación de servicio (DoS). También aprendió que los ataques DoS distribuidos volumétricamente (DDoS) saturan una red enviando paquetes de datos no deseados en cantidades tan grandes que los servidores se vuelven incapaces de dar servicio a los usuarios normales. Esto puede ser perjudicial para una organización. Cuando los sistemas fallan, las organizaciones no pueden satisfacer las necesidades de sus clientes. A menudo pierden dinero y, en algunos casos, incurren en otras pérdidas. La Reputación de una organización también puede sufrir si las noticias de un ataque DDoS exitoso llegan a los consumidores, que entonces cuestionan la Seguridad de la organización.

En esta lectura aprenderá sobre un ataque DDoS de 2016 contra servidores DNS que causó importantes interrupciones en varias organizaciones que tienen millones de usuarios diarios.

## Un DDoS dirigido a un servidor DNS muy utilizado

En los vídeos anteriores, aprendió sobre la función de un servidor DNS. A modo de repaso, los servidores DNS traducen los nombres de dominio de los sitios web en la dirección IP del sistema que contiene la información del sitio web. Por ejemplo, si un usuario tecleara la URL de un sitio web, un servidor DNS la traduciría en una dirección IP numérica que dirige el tráfico de red a la ubicación del servidor del sitio web.

El día del ataque DDoS que estamos estudiando, muchas grandes empresas utilizaban un proveedor de servicios DNS. El proveedor de servicios alojaba el sistema DNS para estas empresas. Esto significaba que cuando los usuarios de Internet tecleaban la URL del sitio web al que querían acceder, sus dispositivos eran dirigidos al lugar correcto. El 21 de octubre de 2016, el proveedor de servicios fue víctima de un ataque DDoS.

## Antes del ataque

Antes del ataque al proveedor de servicios, un grupo de estudiantes universitarios creó una botnet con la intención de atacar varios servidores y redes de juegos. Una **botnet** es una colección de computadoras infectadas por software malicioso que están bajo el control de un único agente de amenaza, conocido como "bot-herder" Cada computadora de la botnet puede ser controlada a distancia para enviar un paquete de datos a un sistema objetivo. En un ataque de botnet, los ciberdelincuentes ordenan a todos los bots de la botnet que envíen paquetes de datos al sistema objetivo al mismo tiempo, lo que da lugar a un ataque DDoS.

El grupo de estudiantes universitarios publicó en línea el código de la botnet para que fuera accesible a miles de usuarios de Internet y las autoridades no pudieran rastrear la botnet hasta los estudiantes. Al hacerlo, hicieron posible que otros actores maliciosos aprendieran el código de la botnet y la controlaran a distancia. Esto incluyó a los ciberdelincuentes que atacaron al proveedor de servicios DNS.

## El día del ataque

A las 7 de la mañana del día del ataque, la botnet envió decenas de millones de peticiones DNS al proveedor de servicios. Esto desbordó el sistema y el servicio DNS se desconectó. Esto significaba que no se podía acceder a todos los sitios web que utilizaban el proveedor de servicios. Cuando los usuarios intentaban acceder a los distintos sitios web que utilizaban el proveedor de servicios, no eran dirigidos al sitio web que habían tecleado en su navegador. Las interrupciones de cada servicio web se produjeron en toda Norteamérica y Europa.

Los sistemas del proveedor de servicios se restablecieron tras sólo dos horas de inactividad. Aunque los ciberdelincuentes enviaron oleadas posteriores de ataques de botnet, la empresa de DNS estaba preparada y fue capaz de mitigar el impacto.

## Claves

Como se demuestra en el ejemplo anterior, los ataques DDoS pueden ser muy perjudiciales para una organización. Como analista de seguridad, es importante reconocer la gravedad de un ataque de este tipo para estar al tanto de las oportunidades de proteger la red frente a ellos. Si su red tiene operaciones importantes distribuidas entre hosts que pueden escalarse dinámicamente, entonces las operaciones pueden continuar si la infraestructura del host base se desconecta. Los ataques DDoS son dañinos, pero hay acciones concretas que los analistas de Seguridad pueden tomar para ayudar a proteger sus organizaciones. Siga avanzando en este curso y conocerá las estrategias de mitigación más comunes para protegerse de los ataques DDoS.