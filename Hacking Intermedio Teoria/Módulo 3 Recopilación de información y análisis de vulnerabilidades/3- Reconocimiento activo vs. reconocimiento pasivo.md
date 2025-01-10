**_El reconocimiento activo_** es un método de recopilación de información en el que las herramientas utilizadas envían sondas a la red o sistemas objetivo con el fin de obtener respuestas que luego se utilizan para determinar la posición de la red o sistema. Estas sondas pueden utilizar varios protocolos y múltiples niveles de agresividad, normalmente en función de lo que se está analizando y cuándo. Por ejemplo, es posible que esté escaneando un dispositivo, como una impresora, que no tiene una pila TCP/IP muy robusta o hardware de red. Al enviar sondeos activos, es posible que se bloquee un dispositivo de este tipo. La mayoría de los dispositivos modernos no tienen este problema; Sin embargo, es posible, por lo que al realizar un escaneo activo, debe ser consciente de esto y ajustar la configuración de su escáner en consecuencia.

**_El reconocimiento pasivo_** es un método de recopilación de información en el que las herramientas no interactúan directamente con el dispositivo o la red objetivo. Existen múltiples métodos de reconocimiento pasivo. Algunos implican el uso de bases de datos de terceros para recopilar información. Otros también utilizan las herramientas de tal manera que no serán detectados por el objetivo. Estas herramientas, en particular, funcionan simplemente escuchando el tráfico en la red y utilizando la inteligencia para deducir información sobre la comunicación del dispositivo en la red. Este enfoque es mucho menos invasivo en una red, y es muy poco probable que este tipo de reconocimiento bloquee un sistema como una impresora. Debido a que no produce ningún tráfico, también es poco probable que sea detectado y no genera ninguna bandera en la red que está inspeccionando. Otro escenario en el que un escáner pasivo sería útil sería para un probador de penetración que necesita realizar análisis en una red de producción que no se puede interrumpir. La técnica de reconocimiento pasivo que utilice depende del tipo de información que desee obtener. Uno de los aspectos más importantes de aprender sobre las pruebas de penetración es desarrollar una buena metodología que te ayude a seleccionar las herramientas y tecnologías adecuadas para usar durante el compromiso.

Entre las herramientas y métodos comunes de reconocimiento activo se incluyen los siguientes:

- Enumeración de hosts
- Enumeración de red
- Enumeración de usuarios
- Enumeración de grupos
- Enumeración de recursos compartidos de red
- Enumeración de páginas web
- Enumeración de aplicaciones
- Enumeración de servicios
- Elaboración de paquetes

Entre las herramientas y métodos comunes de reconocimiento pasivo se incluyen los siguientes:

- Enumeración de dominios
- Inspección de paquetes
- Inteligencia de código abierto (OSINT)
- Reconocimiento
- Escuchando