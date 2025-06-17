
En esta lectura, revisará los dispositivos y conexiones de red e investigará un diagrama de red simple similar a los que usan todos los días los profesionales de la seguridad de redes.

Una comprensión básica de la arquitectura de red, a veces denominada diseño de red, lo ayudará a medida que aprenda sobre las vulnerabilidades de seguridad inherentes a todas las redes y cómo los actores maliciosos intentan explotarlas. ¡Empecemos!

## **Dispositivos de red**

Los dispositivos de red mantienen la información y los servicios para los usuarios de una red. Estos dispositivos se conectan a través de conexiones cableadas e inalámbricas. Después de establecer una conexión a la red, los dispositivos envían paquetes de datos. Los paquetes de datos proporcionan información sobre el origen y el destino de los datos. Así es como se envía y recibe la información a través de diferentes dispositivos en una red.

La red es la infraestructura general que permite que los dispositivos se comuniquen entre sí. Los dispositivos de red son vehículos especializados, como enrutadores y conmutadores, que administran lo que se envía y recibe a través de la red. Además, dispositivos como computadoras y teléfonos se conectan a la red a través de dispositivos de red.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/s-oBYPbLT42rx92K21cvxQ_611ef444b75147a5a6e61d82c34b0df1_9i07czTUt71fHdJt2WJV-5cS3YvI7Y1YQdOBF4c19c2wYkhrIu_6f5gYEgtzAKr8DArrVLx6QY6AQNHpMTmD410f6kyDVYNdP1x36o6lrmsv_CRG8iTBfcIZz4FA-g01ceMoYuXTJjCbvwf38YBSWVwB?expiry=1750291200000&hmac=xKyVIv8kKZ45B6m-Fb-f7yGLIROO6HhCdZjN9w9sq3M)

**Nota:** En este diagrama, un **router** se conecta a Internet a través de un **módem**, proporcionado por su proveedor de servicios de Internet (ISP). El firewall es un dispositivo de seguridad que monitorea el tráfico entrante y saliente en su red. Luego, el enrutador dirige el tráfico a los dispositivos de su red doméstica, que pueden incluir computadoras, computadoras portátiles, teléfonos inteligentes, tabletas, impresoras y otros dispositivos. Puedes imaginar aquí que el servidor es un servidor de archivos. Todos los dispositivos de esta red pueden acceder a los archivos de este **servidor**. Este diagrama también incluye un **conmutador**, que es un dispositivo opcional que se puede utilizar para conectar más dispositivos a la red proporcionando puertos adicionales y conexiones Ethernet. Además, aquí hay 2 enrutadores conectados al conmutador con fines de equilibrio de carga, lo que mejorará el rendimiento de la red.

### **Dispositivos y ordenadores de sobremesa**

La mayoría de los usuarios de Internet están familiarizados con los dispositivos cotidianos, como computadoras personales, computadoras portátiles, teléfonos móviles y tabletas. Cada dispositivo y computadora de escritorio tiene una dirección MAC y una dirección IP únicas, que lo identifican en la red. También tienen una interfaz de red que envía y recibe paquetes de datos. Estos dispositivos pueden conectarse a la red a través de un cable duro o una conexión inalámbrica.

### **Cortafuegos**

Un **firewall** es un dispositivo de seguridad de red que monitorea el tráfico hacia o desde su red. Es como tu primera línea de defensa. Los firewalls también pueden restringir el tráfico de red entrante y saliente específico. La organización configura las reglas de seguridad del firewall. Los firewalls a menudo residen entre la red interna segura y controlada y los recursos de red que no son de confianza fuera de la organización, como Internet. Sin embargo, recuerde que los firewalls son solo una línea de defensa en el panorama de la ciberseguridad.

### **Servidores**

**Los servidores** proporcionan información y servicios para dispositivos como computadoras, dispositivos domésticos inteligentes y teléfonos inteligentes en la red. Los dispositivos que se conectan a un servidor se denominan clientes. En el siguiente gráfico se describe este modelo, que se denomina modelo cliente-servidor. En este modelo, los clientes envían solicitudes al servidor para obtener información y servicios. El servidor realiza las solicitudes para los clientes. Algunos ejemplos comunes son los servidores DNS que realizan búsquedas de nombres de dominio para sitios de Internet, los servidores de archivos que almacenan y recuperan archivos de una base de datos y los servidores de correo corporativo que organizan el correo de una empresa.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/yEzpFYBkSWChuqHQuw5-SA_47876296b9c140229777d37bc916bff1_DVEYhkRb2cM57vspz3iQIbbBaOfDTWTukQLteY2SDv_MAofv-SbuGazdECwDkbJneVXdDvAW6-CuMSMbYLZJVdkUm5b9k0YJd7m9NVDbEZzLgBhO7_0eq30pRJkkUl-QHu97fSitfr2Lva1bPsTd431k?expiry=1750291200000&hmac=0-P_RPAC-WUvMPB2yITrIDT2ZpkthNJm7t_Vo-F3QCw)

### **Concentradores y conmutadores**

Tanto los concentradores como los conmutadores dirigen el tráfico en una red local. Un **hub** es un dispositivo que proporciona un punto de conexión común para todos los dispositivos conectados directamente a él. Además, los concentradores repiten toda la información en todos los puertos. Desde el punto de vista de la seguridad, esto hace que los concentradores sean vulnerables a las escuchas. Por esta razón, los concentradores no se usan con tanta frecuencia en las redes modernas; En su lugar, la mayoría de las organizaciones utilizan conmutadores. Los concentradores se usan más comúnmente para una configuración de red limitada, como una oficina en casa.

Los switches son la opción preferida para la mayoría de las redes. Un **switch** reenvía paquetes entre dispositivos conectados directamente a él. Analizan la dirección de destino de cada paquete de datos y lo envían al dispositivo previsto. Los switches mantienen una tabla de direcciones MAC que coincide con las direcciones MAC de los dispositivos de la red con los números de puerto del switch y reenvía los paquetes de datos entrantes de acuerdo con la dirección MAC de destino. Los switches forman parte de la capa de enlace de datos en el modelo TCP/IP. En general, los conmutadores mejoran el rendimiento y la seguridad.

### **Routers**

**Los routers conectan** redes y dirigen el tráfico, en función de la dirección IP de la red de destino. Los routers permiten que los dispositivos de diferentes redes se comuniquen entre sí. En el modelo TCP/IP, los routers forman parte de la capa de red. La dirección IP de la red de destino se encuentra en el encabezado IP. El router lee la información del encabezado IP y reenvía el paquete al siguiente router en la ruta hacia el destino. Esto continúa hasta que el paquete llega a la red de destino. Los routers también pueden incluir una función de firewall que permite o bloquea el tráfico entrante en función de la información de la transmisión. Esto evita que el tráfico malicioso ingrese a la red privada y dañe la red de área local.

### **Módems y puntos de acceso inalámbricos**

**Los módems** generalmente conectan su hogar u oficina con un proveedor de servicios de Internet (ISP). Los ISP proporcionan conectividad a Internet a través de líneas telefónicas, cables coaxiales o cables de fibra óptica. Los módems reciben transmisiones o señales digitales de Internet y las convierten a un formato digital compatible con la conexión física proporcionada por su ISP. Por lo general, los módems se conectan a un enrutador que toma las transmisiones decodificadas y las envía a la red local.

**Nota: Las** redes empresariales utilizadas por grandes organizaciones para conectar a sus usuarios y dispositivos a menudo utilizan otras tecnologías de banda ancha para manejar el tráfico de gran volumen, en lugar de usar un módem.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/6gFK3i1wRCyopAF5k1j0HQ_c8d352d18c8e4474941916da8fed74f1_GGmNcX8TiMojwILA_9er2cddFq573EvzkLIBJWj8Bpx5asAiGYLNe-aPI6ZluB_5ub9YgBHeHF5xMvQ52k5VknA8RtTVa033ZN5juPaHECodnA1W0ZhlbBJmWbgXrpomHeRypDrDT36bR8LFLRUN4Kxd?expiry=1750291200000&hmac=o10WIiglAiYLzMFNpV7EbV4MG-S5o6HQfFcpFGwAxcQ)

**Punto de acceso inalámbrico**

Un **punto de acceso inalámbrico** envía y recibe señales digitales a través de ondas de radio creando una red inalámbrica. Los dispositivos con adaptadores inalámbricos se conectan al punto de acceso mediante Wi-Fi. **Wi-Fi** se refiere a un conjunto de estándares que utilizan los dispositivos de red para comunicarse de forma inalámbrica. Los puntos de acceso inalámbricos y los dispositivos conectados a ellos utilizan protocolos Wi-Fi para enviar datos a través de ondas de radio, donde se envían a enrutadores y conmutadores y se dirigen a lo largo de la ruta hasta su destino final.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/8vl7L2RlSvGkk3LvXaMeKg_6a15bfb726f541d38671388c13b052f1_XU9XxDWBAwQu9gCYs4ZbRB4Do3xxXScibznS8UvafzSyYJoW9JpmUjL8VNbhYvmNmvmgP9x6AwGltYH7SnkcuyJjEGQNsFLvyeyun2-GdCqjHnXbExJgx67JoFd9KMohmA2xv462hh3O2xkvqhl1kX-z?expiry=1750291200000&hmac=yiFlLQky7dWtQKSwIOTzXiM_HM7EuLIwOFUwUfXyl-w)

## **Using network diagrams as a security analyst**

Los diagramas de red permiten a los administradores de red y al personal de seguridad imaginar la arquitectura y el diseño de la red privada de su organización.

**Los diagramas de red** son mapas que muestran los dispositivos de la red y cómo se conectan. Los diagramas de red utilizan pequeños gráficos representativos para representar cada dispositivo de red y líneas punteadas para mostrar cómo se conecta cada dispositivo con el otro. Al estudiar los diagramas de red, los analistas de seguridad desarrollan y refinan sus estrategias para proteger las arquitecturas de red.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/v540rACBSUepbsQcE4s3PQ_3b799a13034d42938c980d7c473725f1_2SOA6jNuKUowAynp64ms-agTTUcxt1xas4SFTTAcKU-JfqJHyG2vzmM7qgqMh4J_Euwmri_t3G_CUXydGZRlmV4EZABYDusKE7pBnNWi5gZ_fUbiAetmRiQWL3cMO2iRWDtjtAPMazNxnmT-i5pWmPAe?expiry=1750291200000&hmac=IRUxkAhGuUI14l0QPeTiU7mKBgrHaUejun0TAzZHvmQ)

## **Conclusiones clave**

En el modelo cliente-servidor, el cliente solicita información y servicios al servidor, y el servidor realiza las solicitudes para los clientes. Los dispositivos de red incluyen enrutadores, estaciones de trabajo, servidores, concentradores, conmutadores y módems. Los analistas de seguridad utilizan diagramas de red para visualizar la arquitectura de red.
