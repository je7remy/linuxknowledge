
¡La Comunicación en Red puede ser ruidosa! Eventos como el envío de un correo electrónico, la transmisión de un vídeo o la visita a una página web producen comunicaciones de red en forma de Tráfico de red y Datos de red. Como recordatorio, el **Tráfico de** red es la cantidad de datos que se mueven a través de una red. También puede incluir el tipo de datos que se transfieren, como HTTP. **Datos de** **red** son los datos que se transmiten entre los dispositivos de una red.

Monitoreo de red es esencial para mantener el conocimiento de la situación de cualquier actividad en una red. Mediante la recopilación y el análisis del tráfico de red, las organizaciones pueden detectar actividades sospechosas en la red. Pero antes de poder supervisar las redes, debe saber exactamente qué supervisar. En esta lectura, aprenderá más sobre la importancia del monitoreo de redes, las formas de monitorear su red y las herramientas de monitoreo de redes.

## Conozca su red

Como ya ha aprendido, las redes conectan dispositivos y éstos se comunican e intercambian datos mediante protocolos de red. Las comunicaciones de red proporcionan información sobre las conexiones, como las direcciones IP de origen y destino, la cantidad de datos transferidos, la fecha y la hora, etc. Esta información puede ser valiosa para los profesionales de la Seguridad a la hora de desarrollar una línea de **base** del comportamiento normal o esperado.

![Gráfico de líneas que muestra una línea de base que atraviesa el centro de los picos de datos.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/R-C-xmdWTRe8XfbJ4V9BMg_01d033967efe41ba898db5755db1f4f1_i-QtA3HA4BNT_yYXJ-qbty4-R8tuDG73XRllvRqnBMgcopHG7JmrlZYtjv-Jeorch1-w-rQhfh9u1ObkqF6KNsslNqhqyacRusAj38ehIjgImRN2lSB6DQ49MsFJCYgPdG2iBrOt-HEU99JuvC-070uPrh1M9UxFjb-Hvmfaa4yaGyn5kno71tlvVr_xgg?expiry=1759881600000&hmac=V0stTUQgTVTpk38uKfKdFubrNcbl7os0tqb2IVl1src)

Una línea de base es un punto de referencia que se utiliza para comparar. Probablemente se haya encontrado o haya utilizado líneas de base en algún momento. Por ejemplo, el importe de una compra para un presupuesto personal es un ejemplo de línea de base que puede utilizarse para ayudar a identificar cualquier patrón o cambio en los hábitos de gasto. En seguridad, las líneas de base ayudan a establecer un estándar de comportamiento esperado o normal para sistemas, dispositivos y redes. Esencialmente, al conocer la línea de base del comportamiento _normal_ de la red, podrá identificar mejor el comportamiento _anormal_ de la red.

## Monitoree su red

Una vez que haya determinado una línea de base, puede Monitorear una red para identificar cualquier desviación de esa línea de base. Monitorear implica examinar los componentes de la red para detectar actividades inusuales, como transferencias de datos grandes e inusuales. He aquí algunos ejemplos de componentes de red que pueden ser monitorizados para detectar actividades maliciosas:

### **Análisis de flujo**

Fluir se refiere al movimiento de las comunicaciones de red e incluye información relacionada con paquetes, protocolos y puertos. Los paquetes pueden viajar a puertos, que reciben y transmiten comunicaciones. Los puertos suelen estar asociados, aunque no siempre, a protocolos de redes. Por ejemplo, el puerto 443 es utilizado habitualmente por HTTPS, que es un protocolo que proporciona encriptación del tráfico de sitios web.

Sin embargo, los actores maliciosos pueden utilizar protocolos y puertos que no están comúnmente asociados para mantener comunicaciones entre el sistema comprometido y su propia máquina. Estas comunicaciones son lo que se conoce como **comando y control (C2)**, que son las técnicas utilizadas por los actores maliciosos para mantener las comunicaciones con los sistemas comprometidos.

Por ejemplo, los actores maliciosos pueden utilizar el protocolo HTTPS a través del puerto 8088 en lugar de su puerto comúnmente asociado 443 para comunicarse con los sistemas comprometidos. Las organizaciones deben saber qué puertos deben estar abiertos y aprobados para las conexiones, y vigilar cualquier desajuste entre los puertos y sus protocolos asociados.

### **Información sobre la carga útil de los paquetes**

Los paquetes de red contienen componentes relacionados con la transmisión del paquete. Esto incluye detalles como la dirección IP de origen y destino, y la información de la carga útil del paquete, que son los datos reales que se transmiten. A menudo, estos Datos están encriptados y requieren desencriptación para que sean legibles. Las organizaciones pueden monitorizar la información de la carga útil de los paquetes para descubrir actividades inusuales, como datos sensibles que se transmiten fuera de la red, lo que podría indicar un posible ataque de exfiltración de datos.

### **Patrones temporales**

Los paquetes de red contienen información relativa al tiempo. Esta Información es útil para comprender los patrones temporales. Por ejemplo, una empresa que opera en Norteamérica experimenta grandes flujos de tráfico entre las 9 de la mañana y las 5 de la tarde, que es la línea de base de la actividad normal de la red. Si de repente aparecen grandes volúmenes de tráfico fuera de las horas normales de actividad de la red, se considera que está _fuera_ de la línea de base y debe investigarse.

Mediante el Monitoreo de red, las organizaciones pueden detectar con prontitud las intrusiones en la red y trabajar para evitar que ocurran asegurando los componentes de la red.

## Proteja su red

En este Programa, ha aprendido sobre los centros de **operaciones de seguridad** (**SOC**) y su función en la supervisión de los sistemas contra las amenazas y ataques a la Seguridad. Las organizaciones pueden implementar un centro de operaciones de **red** (**NOC**), que es una unidad organizativa que supervisa el rendimiento de una red y responde a cualquier interrupción de la red, como un corte de red. Mientras que un SOC se centra en mantener la seguridad de una organización mediante la detección y la respuesta, un NOC es responsable de mantener el rendimiento, la disponibilidad y el tiempo de actividad de la red.

![Un analista supervisa la actividad del sistema en varias pantallas de ordenador.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/JC9h-84YTn-cwOHf6MXVMg_b307457feef74f0e88f8664100b395f1_JqtN_UgxVYbwkx1IjuMN31PoUM5XlHpZ0M-Z2hBqScuHUv62R7AvZcqAGJGuoDUpYu6MnQiCL0FPB8tspDaKzNRvL6CxZv3oMo5cZfNfql0to1vR8Qt9Zam2ETRZLp_2w66Ah-JzQAF70EQdzN10PqSMOHbomP8LWvk5cigov8vPptnVpNVkzZAcaB_V7Q?expiry=1759881600000&hmac=DeDbl_yum7Yg24xdmf900N5wSq3btUOyDzwLJycdXk0)

Los analistas de seguridad monitorizan las redes para identificar cualquier signo de posibles incidentes de seguridad conocidos como **Indicadores de compromiso** **(IoC**) y protegen las redes de amenazas o ataques. Para ello, deben comprender el entorno por el que viajan las comunicaciones de red para poder identificar desviaciones en el Tráfico de red.

### **Herramientas de Monitoreo de red**

El Monitoreo de red puede automatizarse o realizarse manualmente. Algunas herramientas comunes de Monitoreo de red pueden incluir:

- **Sistemas de detección de intrusiones** **(IDS**) Monitorean la actividad del sistema y alertan sobre posibles intrusiones. Un IDS detectará y alertará sobre las desviaciones que usted le haya configurado para detectar. Lo más habitual es que las herramientas IDS monitoricen el contenido de la carga útil de los paquetes para detectar patrones asociados a amenazas como el software malicioso o los intentos de phishing.
    
- **Los analizadores de protocolos de red**, también conocidos como rastreadores de paquetes, son herramientas diseñadas para capturar y analizar el tráfico de datos dentro de una red. Pueden utilizarse para analizar manualmente las comunicaciones de red en detalle. Algunos ejemplos son herramientas como tcpdump y Wireshark, que pueden utilizar los profesionales de la Seguridad para registrar las comunicaciones de red mediante capturas de paquetes. Las capturas de paquetes pueden investigarse después para identificar actividades potencialmente maliciosas.
    

## Puntos clave

Monitorear y proteger las redes de intrusiones y ataques son responsabilidades clave de los profesionales de la Seguridad. No se puede proteger lo que no se conoce. Como analista de seguridad, necesitará conocer los componentes de una red y las comunicaciones que se producen en ella, para poder protegerla mejor. Las líneas de base proporcionan una forma de entender el tráfico de la red descubriendo patrones comunes que ayudan a identificar cualquier desviación de los patrones de tráfico esperados. Herramientas como los sistemas de detección de intrusiones y los analizadores de protocolos de red apoyan los esfuerzos de supervisión de las actividades de la red.

## Recursos

- Si desea obtener más información sobre los componentes de red que pueden supervisar las organizaciones, consulte [Tráfico de red - MITRE ATT&CK®](https://attack.mitre.org/datasources/DS0029/)
    
- Los atacantes pueden aprovechar diferentes técnicas para exfiltrar datos, si desea saber más, consulte [técnicas de exfiltración de datos - MITRE ATT&CK®](https://attack.mitre.org/tactics/TA0010/)