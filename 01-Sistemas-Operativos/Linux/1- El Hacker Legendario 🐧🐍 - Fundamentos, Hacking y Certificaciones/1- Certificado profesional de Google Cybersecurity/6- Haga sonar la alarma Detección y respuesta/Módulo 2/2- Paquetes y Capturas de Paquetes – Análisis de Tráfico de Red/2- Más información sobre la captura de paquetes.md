
La función de los analistas de seguridad consiste en supervisar y analizar los flujos de tráfico de la red. Una forma de hacer esto es generando capturas de paquetes y luego analizando el tráfico capturado para identificar actividad inusual en una red.

Anteriormente, exploraste los fundamentos de las redes. A lo largo de esta sección, se referirá a sus fundamentos en redes para comprender mejor los flujos de tráfico de red. En esta lectura, aprenderá sobre los tres aspectos principales del análisis de redes: paquetes, analizadores de protocolos de red y capturas de paquetes.

## Paquetes

Anteriormente en el programa, aprendiste que un **paquete de datos** es una unidad básica de información que viaja de un dispositivo a otro dentro de una red. La detección de intrusiones en la red comienza a nivel de paquetes. Esto se debe a que los paquetes forman la base del intercambio de información a través de una red. Cada vez que usted realiza una actividad en Internet -como visitar un sitio web- se envían y reciben paquetes entre su ordenador y el servidor del sitio web. Estos paquetes son los que ayudan a transmitir información a través de una red. Por ejemplo, al subir una imagen a un sitio web, los datos se dividen en varios paquetes, que luego se envían al destino previsto y se vuelven a ensamblar en el momento de la entrega.

En ciberseguridad, los paquetes proporcionan información valiosa que ayuda a contextualizar los sucesos durante las investigaciones. Comprender la transferencia de información a través de paquetes no sólo le ayudará a comprender la actividad de la red, sino también a identificar anomalías y a defender mejor las redes de los ataques.

Los paquetes contienen tres componentes: la cabecera, la carga útil y el pie de página. He aquí una descripción de cada uno de estos componentes.

### **Cabecera**

Los paquetes comienzan con el componente más esencial: la cabecera . Los paquetes pueden tener varias cabeceras dependiendo de los protocolos utilizados, como una cabecera Ethernet, una cabecera IP, una cabecera TCP y más. Las cabeceras proporcionan información que se utiliza para encaminar los paquetes a su destino. Esto incluye información sobre las direcciones IP de origen y destino, la longitud del paquete, el protocolo, los números de identificación del paquete, etc.

A continuación se muestra una cabecera IPv4 con la información que proporciona:

![Una cabecera IPv4 con sus trece campos](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Mi_kryGkRiyYUOJDIwnPCw_ac942d1eec284467a5ca533cb99c4bf1_S20G003.png?expiry=1759968000000&hmac=HC3fHf8S_YvRbNX9Xh6LzSTsixEOfGKmI8abZ28iwWo)

### **Carga útil**

El componente de carga útil de sigue directamente a la cabecera y contiene los datos reales que se envían. Piensa en el ejemplo de subir una imagen a un sitio web; la carga útil de este paquete sería la propia imagen.

### **Pie de página**

El pie de página, también conocido como trailer, se encuentra al final del paquete. El protocolo Ethernet utiliza los pies de página para proporcionar información de comprobación de errores para determinar si los datos se han corrompido. Además, es posible que los paquetes de red Ethernet que se analizan no muestren información de pie de página debido a las configuraciones de red.

**Nota:** La mayoría de los protocolos, como el Protocolo de Internet (IP), _no_ utilizan pies de página.

## Analizadores de protocolos de red

**Los analizadores de protocolos** de**red** **(packet sniffers)** son herramientas diseñadas para capturar y analizar el tráfico de datos dentro de una red. Algunos ejemplos de analizadores de protocolos de red son tcpdump, Wireshark y TShark.

Más allá de su uso en seguridad como herramienta de investigación utilizada para supervisar redes e identificar actividades sospechosas, los analizadores de protocolos de red pueden utilizarse para recopilar estadísticas de red, como el ancho de banda o la velocidad, y solucionar problemas de rendimiento de la red, como ralentizaciones.

Los analizadores de protocolos de red también pueden utilizarse con fines maliciosos. Por ejemplo, agentes maliciosos pueden utilizar analizadores de protocolos de red para capturar paquetes que contengan datos confidenciales, como información de inicio de sesión de cuentas.

A continuación se muestra un diagrama de red que ilustra cómo se transmiten los paquetes de un emisor a un receptor. Un analizador de protocolos de red se coloca en medio de las comunicaciones para capturar los paquetes de datos que viajan por el cable.

![El ordenador A envía paquetes de datos al ordenador B. El analizador de protocolos de red se encuentra en medio de la ruta de la red.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/EjVePDcSRvmzvvtk8lQlXw_43c1eaf1c9f3444e99c62361ecd078f1_S29G004.png?expiry=1759968000000&hmac=qakSlZfPMnD8BB2MZ4TG5gyIgKzhPyIjUdxdqEE2kO0)

### **Cómo funcionan los analizadores de protocolos de red**

Los analizadores de protocolos de red utilizan capacidades tanto de software como de hardware para capturar el tráfico de red y mostrarlo para que los analistas de seguridad lo examinen y analicen. A continuación se explica cómo:

1. En primer lugar, los paquetes deben recogerse de la red a través de la **Tarjeta de interfaz de red (NIC)**, que es el hardware que conecta los ordenadores a una red, como un router. Las NIC reciben y transmiten tráfico de red, pero por defecto sólo escuchan el tráfico de red dirigido a ellas. Para capturar todo el tráfico de red que se envía a través de la red, una NIC debe conmutarse a un modo que tenga acceso a todos los paquetes de datos de red visibles. En las interfaces inalámbricas, esto suele denominarse modo monitor, y en otros sistemas puede llamarse modo promiscuo. Este modo permite que la NIC tenga acceso a todos los paquetes de datos de red visibles, pero no ayudará a los analistas a acceder a todos los paquetes de una red. Un analizador de protocolos de red debe colocarse en un segmento de red adecuado para acceder a todo el tráfico entre los distintos hosts.
    
2. El analizador de protocolos de red recopila el tráfico de red en formato binario sin procesar. El formato binario se compone de 0s y 1s y no es tan fácil de interpretar para los humanos. El analizador de protocolos de red toma el binario y lo convierte para que se muestre en un formato legible para el ser humano, de modo que los analistas puedan leer y comprender fácilmente la información.
    

**Nota:** Activar promiscuo puede exponer su dispositivo a posibles ataques porque permite capturar información sensible como contraseñas y otros datos confidenciales. Es importante utilizar las herramientas que funcionan en modo promiscuo con responsabilidad y precaución.

### **Captura de paquetes**

**El sniffing** de paquetes es la práctica de capturar e inspeccionar paquetes de datos a través de una red. Una **captura de paquetes (p-cap)** es un archivo que contiene paquetes de datos interceptados desde una interfaz o red. Las capturas de paquetes pueden visualizarse y analizarse posteriormente mediante analizadores de protocolos de red. Por ejemplo, puede filtrar las capturas de paquetes para mostrar sólo la información más relevante para su investigación, como los paquetes enviados desde una dirección IP específica.

**Nota**: El uso de analizadores de protocolos de red para interceptar y examinar comunicaciones de red privadas sin permiso se considera ilegal en muchos lugares.

Los archivos P-cap pueden venir en muchos formatos dependiendo de la librería de captura de paquetes que se utilice. Cada formato tiene diferentes usos y las herramientas de red pueden usar o soportar formatos específicos de archivos de captura de paquetes por defecto. Deberías estar familiarizado con las siguientes librerías y formatos:

1. **Libpcap** es una librería de captura de paquetes diseñada para ser utilizada por sistemas tipo Unix, como Linux y MacOS®. Herramientas como tcpdump utilizan Libpcap como formato de captura de paquetes por defecto.
    
2. **WinPcap** es una librería de captura de paquetes de código abierto diseñada para dispositivos con sistemas operativos Windows. Se considera un formato de archivo antiguo y no se usa predominantemente.
    
3. **Npcap** es una biblioteca diseñada por la herramienta de exploración de puertos Nmap que se utiliza habitualmente en sistemas operativos Windows.
    
4. **PCAPng** es un formato de archivo moderno que puede capturar paquetes y almacenar datos simultáneamente. Su capacidad para hacer ambas cosas explica la "ng", que significa "próxima generación"
    

**Consejo profesional:** Analizar tu red doméstica puede ser una buena forma de practicar el uso de estas herramientas.

## Puntos clave

Los analizadores de protocolos de red son útiles herramientas de investigación que permiten conocer la actividad que tiene lugar en una red. Como analista, utilizará las herramientas del analizador de protocolos de red para ver y analizar los archivos de captura de paquetes para comprender mejor las comunicaciones de red y defenderse contra las intrusiones.

## Recursos para obtener más información

Este artículo de Infosec describe los riesgos del [packet crafting](https://resources.infosecinstitute.com/topic/packet-crafting-a-serious-crime/), una técnica utilizada para comprobar la estructura de una red.