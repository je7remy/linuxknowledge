
En los puntos anteriores del curso, aprendió cómo se utilizan el sniffing de paquetes y la Suplantación de IP en los ataques a las redes. Dado que estos ataques interceptan paquetes de datos mientras viajan por la red, se denominan ataques de interceptación.

Esta lectura le presentará algunos ataques específicos que utilizan el sniffing de paquetes y la Suplantación de IP. Aprenderá cómo los hackers utilizan estas tácticas y cómo los analistas de Seguridad pueden contrarrestar la amenaza de los ataques de interceptación.

## Una revisión más detallada del sniffing de paquetes

Como aprendió en un vídeo anterior, el **sniffing** de paquetes es la práctica de capturar e inspeccionar paquetes de datos a través de una red. En una red privada, los paquetes de datos se dirigen al dispositivo de destino correspondiente de la red.

La tarjeta de interfaz de red (NIC) del dispositivo es una pieza de hardware que conecta el dispositivo a una red. La NIC lee la transmisión de datos y, si contiene la dirección MAC del dispositivo, acepta el paquete y lo envía al dispositivo para que procese la información basándose en el protocolo. Esto ocurre en todas las operaciones de red estándar. Sin embargo, una NIC puede configurarse en modo promiscuo, lo que significa que acepta todo el tráfico de la red, incluso los paquetes que no están dirigidos al dispositivo de la NIC. Más adelante en el Programa aprenderá más sobre las NIC. Los actores maliciosos podrían utilizar software como Wireshark para capturar los datos de una red privada y almacenarlos para su uso posterior. A continuación, pueden utilizar la información personal en su propio beneficio. Otra posibilidad es que utilicen las direcciones IP y MAC de los usuarios autorizados de la red privada para realizar la suplantación de IP.

## Un examen más detallado de la Suplantación de IP

Después de que un actor malicioso haya olfateado paquetes en la red, puede suplantar las direcciones IP y MAC de dispositivos autorizados para realizar un ataque de suplantación de IP. Los cortafuegos pueden evitar los ataques de suplantación de IP configurándolos para que rechacen los paquetes IP no autorizados y el tráfico sospechoso. A continuación, examinará algunos ataques comunes de suplantación de IP con los que es importante familiarizarse como analista de Seguridad.

### **Ataque en ruta**

Un **ataque en** ruta se produce cuando un hacker intercepta la comunicación entre dos dispositivos o servidores que tienen una relación de confianza. La transmisión entre estos dos dispositivos de red de confianza podría contener información valiosa como nombres de usuario y contraseñas que el actor malicioso puede recopilar. Un ataque en ruta se denomina a veces **ataque de intermediario** porque el hacker se esconde en medio de las comunicaciones entre dos partes de confianza.

También puede ocurrir que la transmisión interceptada contenga una búsqueda en el sistema DNS. Recordará de un vídeo anterior que un servidor DNS traduce los nombres de dominio de los sitios web en direcciones IP. Si un agente malicioso intercepta una transmisión que contiene una búsqueda DNS, podría falsificar la respuesta DNS del servidor y redirigir un nombre de dominio a una dirección IP diferente, quizás una que contenga código malicioso u otras amenazas. La forma más importante de protegerse contra un ataque en ruta es la encriptación de sus Datos en tránsito, por ejemplo utilizando TLS.

### **Ataque Smurf**

Un **Ataque Smurf** es un ataque a la red que se realiza cuando un atacante olfatea la dirección IP de un usuario autorizado y lo inunda de paquetes. Una vez que el paquete falsificado alcanza la dirección de broadcast, se envía a todos los dispositivos y servidores de la red.

En un ataque Smurf, la suplantación de IP se combina con otra técnica de denegación de servicio (DoS) para inundar la red con tráfico no deseado. Por ejemplo, el Paquete falsificado podría incluir un ping del Protocolo de mensajes de control de Internet (ICMP). Como ya ha aprendido, el ICMP se utiliza para solucionar problemas en una red. Pero si se transmiten demasiados mensajes ICMP, las respuestas de eco ICMP abruman a los servidores de la red y éstos se apagan. Esto crea una denegación de servicio y puede paralizar las operaciones de una organización.

Una forma importante de protegerse contra un ataque smurf es utilizar un firewall avanzado que pueda supervisar cualquier tráfico inusual en la red. La mayoría de los firewalls de nueva generación (NGFW) incluyen características que detectan anomalías en la red para garantizar que se detectan las broadcast de tamaño excesivo antes de que tengan la oportunidad de hacer caer la red.

### **Ataque DoS**

Como ya ha aprendido, una vez que el actor malicioso ha olfateado el tráfico de red, puede hacerse pasar por un usuario autorizado. Un **ataque de denegación de** servicio es una clase de ataques en los que el atacante impide que el sistema comprometido realice una actividad legítima o responda al tráfico legítimo. Sin embargo, a diferencia de la suplantación de IP, el atacante no recibirá respuesta del host atacado. Todo en el paquete de datos está autorizado, incluida la dirección IP en el Encabezado del paquete. En los ataques de suplantación de IP, el actor malicioso utiliza paquetes IP que contienen direcciones IP falsas. Los atacantes siguen enviando paquetes IP que contienen direcciones IP falsas hasta que el servidor de red se bloquea.

**Consejo profesional**: Recuerde el principio de defensa en profundidad. No existe una estrategia perfecta para detener cada tipo de ataque. Puede estratificar su defensa utilizando múltiples estrategias. En este caso, el uso de la encriptación estándar del sector reforzará su Seguridad y le ayudará a defenderse de los ataques DoS en más de un nivel.

## Puntos clave

Esta lectura cubrió varios tipos de ataques comunes de Suplantación de IP. Ha aprendido cómo se realiza el sniffing de paquetes y cómo la recopilación de información a partir de la interceptación de transmisiones de datos puede dar a los actores maliciosos oportunidades para la suplantación de IP. Tanto si se trata de un ataque en ruta, un ataque de suplantación de IP o un ataque Smurf, los analistas deben asegurarse de que existen estrategias de mitigación para limitar la amenaza y prevenir las brechas de Seguridad.