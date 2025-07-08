
Esta sección del curso trata el tema del endurecimiento de la red y su supervisión. Cada dispositivo, herramienta o estrategia de seguridad puesta en marcha por los analistas de seguridad protege -o endurece- aún más la red hasta que el propietario de la red está satisfecho con el nivel de seguridad. Este enfoque de añadir capas de seguridad a una red se conoce como defensa en profundidad.

En esta lectura, va a conocer la Función de cuatro dispositivos utilizados para proteger una red: cortafuegos, sistemas de detección de intrusiones, sistemas de prevención de intrusiones y herramientas de gestión de incidentes y eventos de seguridad. Los profesionales de la Seguridad de red tienen la opción de utilizar cualquiera de estos dispositivos y herramientas, o todos ellos, en función del nivel de seguridad que esperen alcanzar.

En esta lectura se analizarán los beneficios de la Seguridad por capas. Cada herramienta mencionada es una capa adicional de defensa que puede endurecer una red de forma incremental, empezando por el nivel mínimo de seguridad (proporcionado sólo por un cortafuegos), hasta el nivel más alto de seguridad (proporcionado por la combinación de un cortafuegos, un dispositivo de detección y prevención de intrusiones y el monitoreo de eventos de seguridad).

![Imagen que muestra las diferencias entre un cortafuegos, un IPS y un IDS.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/4ENRXSswQSOsOrKt9KyG6A_06fe04a8d10846ba811fe89a969642f1_CS_R-055_Firewall-IDS-and-IPS.png?expiry=1752105600000&hmac=wOv6PIgUl2Jlm9xYfosClAv85Ix7_9fdxRE_0n0Gl0w)

Tome nota de dónde se encuentra cada herramienta en la red. Cada herramienta tiene su propio lugar en la arquitectura de la red. Los analistas de seguridad deben comprender las topologías de red que se muestran en los diagramas a lo largo de esta lectura.

## Firewall

Hasta ahora en este curso, ha aprendido sobre los firewalls sin estado, los firewalls con estado y los firewalls de nueva generación (NGFW), así como las ventajas de seguridad de cada uno de ellos.

La mayoría de los firewalls son similares en sus funciones básicas. Los firewalls permiten o bloquean el tráfico basándose en un conjunto de reglas. Cuando los paquetes de datos entran en una red, se inspecciona el encabezado del paquete y se permite o deniega en función de su número de puerto. Los NGFW también pueden inspeccionar la carga útil de los paquetes. Cada sistema debe tener su propio firewall, independientemente del cortafuegos de la red.

![Un cortafuegos rodeado de guiones que protege la red interna del tráfico de Internet que entra por el modo.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/dSLcIcXBSw-kw-9kzEwhAw_284c8540dab14a9e911296471c71d2f1_CS_R-055_Firewall.png?expiry=1752105600000&hmac=mvdwBZB_w0Sn5fK6zF8dL_o0qhfHB5U-sObey_QjZO8)

## Sistema de detección de intrusiones

Un **Sistema de detección de intrusiones** (IDS) es una aplicación que monitoriza la actividad del sistema y alerta sobre posibles intrusiones. Un IDS alerta a los administradores basándose en la firma del tráfico malicioso.

El IDS está configurado para detectar ataques conocidos. Los sistemas IDS suelen olfatear los paquetes de datos mientras se desplazan por la red y los analizan en busca de las características de ataques conocidos. Algunos sistemas IDS revisan no sólo en busca de firmas de ataques conocidos, sino también de anomalías que podrían ser el signo de una actividad maliciosa. Cuando el IDS descubre una anomalía, envía una alerta al administrador de la red, que puede investigar más a fondo.

Las limitaciones de los sistemas IDS son que sólo pueden buscar ataques conocidos o anomalías evidentes. Los ataques nuevos y sofisticados podrían no ser detectados. La otra limitación es que el IDS no detiene realmente el tráfico entrante si detecta algo raro. Depende del administrador de la red detectar la actividad maliciosa antes de que cause algún daño a la red.

![Un IDS rodea con un círculo la imagen de un conmutador, que se sitúa entre un cortafuegos y la red.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/5hPelJ74TwaKusUY4ZEkkQ_bcd56306ce904397a352cfe37e28b6f1_CS_R-055_IDS.png?expiry=1752105600000&hmac=xmR36bdg6h7U40F8R30JmQ2lp_lNmRn7dmeRcakBeL0)

Cuando se combina con un firewall, un IDS añade otra capa de defensa. El IDS se coloca detrás del firewall y antes de entrar en la LAN, lo que permite al IDS analizar los flujos de Datos después de que el Tráfico de red no permitido por el firewall haya sido filtrado. Esto se hace para reducir el ruido en las alertas del IDS, también denominadas falsos positivos.

## Sistema de prevención de intrusiones

Un **Sistema de prevención de intrusiones (IPS** ) es una aplicación que monitoriza la actividad del sistema en busca de actividades intrusivas y toma medidas para detenerlas. Ofrece incluso más protección que un IDS porque detiene activamente las anomalías cuando las detecta, a diferencia del IDS que simplemente informa de la anomalía a un administrador de red.

Un IPS busca firmas de ataques conocidos y anomalías en los Datos. Un IPS informa de la anomalía a los analistas de seguridad y bloquea un remitente específico o elimina los paquetes de red que parecen sospechosos.

![Un IPS se sitúa entre un cortafuegos y la red interna.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/sp1NiS2HR3KoLCBP36lq3g_f612a9b5e6cc47b2a9341208200b3ff1_CS_R-055_IPS.png?expiry=1752105600000&hmac=oHHQkAH-knUqnUUC9aN5xAvJ5Ym-0L2vaUpR3WThYR0)

El IPS (como un IDS) se sitúa detrás del firewall en la arquitectura de red. Esto ofrece un alto nivel de seguridad porque los flujos de datos arriesgados se interrumpen incluso antes de que lleguen a las partes sensibles de la red. Sin embargo, una limitación potencial es que está en línea: Si se rompe, se interrumpe la conexión entre la red privada e Internet. Otra limitación de los IPS es la posibilidad de que se produzcan falsos positivos, lo que puede hacer que se interrumpa el tráfico legítimo.

## Dispositivos de captura de paquetes completos

Los dispositivos de captura de paquetes completos pueden ser increíblemente útiles para los administradores de redes y los profesionales de la Seguridad. Estos dispositivos le permiten registrar y analizar todos los Datos que se transmiten a través de su red. También ayudan a investigar las alertas creadas por un IDS.

## Administración de información y eventos de seguridad

Un **sistema de administración de información y eventos de seguridad (SIEM** ) es una aplicación que recopila y analiza los datos de registro para supervisar las actividades críticas de una organización. Las herramientas SIEM trabajan en tiempo real para informar de las actividades sospechosas en un panel centralizado. Las herramientas SIEM analizan además los datos de registro de red procedentes de IDS, IPS, cortafuegos, VPN, proxies y registros DNS. Las herramientas SIEM son una forma de agregar los datos de los eventos de seguridad para que aparezcan todos en un mismo lugar y puedan ser analizados por los analistas de seguridad. Esto se conoce como un panel único de cristal.

A continuación, puede revisar un ejemplo de un panel de control de la herramienta SIEM de Google Nube, Chronicle. **Chronicle** es una herramienta nativa de la nube diseñada para retener, analizar y buscar datos.

![Imagen del cuadro de mandos de la Crónica](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/sTtz1jL8QzCTVyhfvICu1A_ee623d56206843d6823598a8f0e70ef1_eyi2ksdTfw4mJcwZ6NvBKQBg-7CVFr-2tq8qNBLlVbloMUlJsvGdPwkSGEk-5VnBU3eXxe9dF7mGPjvyN2T3nWNKtXtu19K2Ycnbt_rEE5FAE4rbNvixbF_oeU82PyiZWpEVVoTqMf6eQJWl7uRMQyvIWA94vNp88ew46W52Kh7QkFeihWUfB8cQkB5dI5c?expiry=1752105600000&hmac=56lBrNM1ndGxkhjJz35hjNQ5z1womVsbzN2U41twoBc)

**Splunk** es otra herramienta SIEM común. Splunk ofrece diferentes opciones de herramientas SIEM: Splunk Enterprise y Splunk Cloud. Ambas opciones incluyen cuadros de mando detallados que ayudan a los profesionales de la Seguridad a revisar y analizar los datos de una organización. También hay otras herramientas SIEM similares disponibles, y es importante que los profesionales de la Seguridad investiguen las diferentes herramientas para determinar cuál es la más beneficiosa para la organización.

Una herramienta SIEM no sustituye a los conocimientos de los analistas de seguridad ni a las actividades de refuerzo de redes y sistemas que se tratan en este curso, pero se utilizan en combinación con otros métodos de seguridad. Los analistas de seguridad suelen trabajar en un Centro de Operaciones de Seguridad (SOC) donde pueden supervisar la actividad en toda la red. A continuación, pueden utilizar sus conocimientos y experiencia para determinar cómo responder a la información del cuadro de mandos y decidir cuándo los eventos cumplen los criterios para ser escalados a supervisión.

## Puntos clave

|**Dispositivos / Herramientas**|**Ventajas**|**Desventajas**|
|---|---|---|
|Firewall|Un firewall permite o bloquea el tráfico basándose en un conjunto de reglas.|Un firewall sólo es capaz de filtrar paquetes basándose en la Información proporcionada en la cabecera de los paquetes.|
|Sistema de detección de intrusiones (IDS)|Un IDS detecta y alerta a los administradores sobre posibles intrusiones, ataques y otro tipo de tráfico malicioso.|Un IDS sólo puede escanear en busca de ataques conocidos o anomalías obvias; los ataques nuevos y sofisticados podrían no ser detectados. En realidad, no detiene el Tráfico entrante.|
|Sistema de prevención de intrusiones (IPS)|Un IPS monitorea la actividad del sistema en busca de intrusiones y anomalías y toma medidas para detenerlas.|Un IPS es un dispositivo en línea. Si falla, se interrumpe la conexión entre la red privada e Internet. Puede detectar falsos positivos y bloquear el tráfico legítimo.|
|Administración de información y eventos de seguridad (SIEM)|Una herramienta SIEM recopila y analiza los datos de registro de varios equipos de red. Agrega los eventos de Seguridad para su Monitoreo en un tablero central.|Una herramienta SIEM sólo informa sobre posibles Problemas de Seguridad. No lleva a cabo ninguna acción para detener o prevenir eventos sospechosos.|

La compra, instalación y mantenimiento de cada uno de estos dispositivos o herramientas cuesta dinero. Es posible que una organización necesite contratar personal adicional para monitorizar las herramientas de Seguridad, como en el caso de un SIEM. Los responsables de la toma de decisiones tienen la tarea de seleccionar el nivel apropiado de Seguridad basándose en el coste y el Riesgo para la organización. Más adelante aprenderá más sobre la elección de los niveles de Seguridad.