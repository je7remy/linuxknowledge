
Anteriormente, usted aprendió sobre el proceso SIEM. En esta lectura, explorará más sobre este proceso y por qué las herramientas SIEM son una parte importante de la detección y respuesta ante incidentes. A modo de repaso, una herramienta de **información de seguridad y gestión de eventos****(SIEM**) es una aplicación que recopila y analiza datos de registro para monitorizar actividades críticas en una organización. Quizá recuerde que las herramientas SIEM ayudan a los analistas de Seguridad a realizar el **análisis** de registros, que es el proceso de examinar los registros para identificar los eventos de interés.

## Ventajas de SIEM

Las herramientas SIEM recopilan y gestionan datos relevantes para la seguridad que pueden utilizarse durante las investigaciones. Esto es importante porque las herramientas SIEM permiten conocer la actividad que se produce entre los dispositivos de una red. La información que proporcionan las herramientas SIEM puede ayudar a los equipos de seguridad a investigar y responder rápidamente a los incidentes de seguridad. Las herramientas SIEM tienen muchas ventajas que pueden ayudar a los equipos de Seguridad a responder y gestionar eficazmente los incidentes. Algunas de estas ventajas son

- **Accesibilidad a los Datos de Eventos:** Las herramientas SIEM proporcionan acceso a los datos de eventos y actividades que se producen en una red, incluida la actividad en tiempo real. Las redes pueden estar conectadas a cientos de sistemas y dispositivos diferentes. Las herramientas SIEM tienen la capacidad de ingestar todos estos Datos para que se pueda acceder a ellos.
    
- **Monitorear, Detectar y Alertar:** Las herramientas SIEM supervisan continuamente los sistemas y las redes en tiempo real. A continuación, analizan los Datos recopilados utilizando reglas de Detección para detectar actividades maliciosas. Si una actividad coincide con la regla, se genera una alerta y se envía para que los equipos de Seguridad la evalúen.
    
- **Almacenamiento de registros:** Las herramientas SIEM pueden actuar como un sistema de retención de datos, que puede proporcionar accesibilidad a los datos históricos. Los Datos pueden conservarse o borrarse después de un periodo dependiendo de los Requisitos de una organización.
    

## El proceso SIEM

El proceso SIEM consta de tres pasos críticos:

1. **Recopilar y agregar Datos**
    
2. **Normalización de datos**
    
3. **Analizar los datos**
    

Al comprender estos pasos, las organizaciones pueden utilizar la potencia de las herramientas SIEM para recopilar, organizar y analizar los datos de los eventos de Seguridad procedentes de distintas fuentes. Posteriormente, las organizaciones pueden utilizar esta información para mejorar su capacidad de identificar y mitigar las amenazas potenciales.

### **Recopilar y agregar Datos**

Las herramientas SIEM requieren datos para que puedan utilizarse con eficacia. Durante el primer paso, el SIEM recopila Datos de Evento de varias fuentes como firewalls, servidores, routers y más. Estos datos, también conocidos como registros, contienen detalles de los eventos como marcas de tiempo, direcciones IP y más. Los **registros** A son un registro de los eventos que se producen en los sistemas de una organización. Una vez recopilados todos estos datos de registro, se agregan en un solo lugar. Agregación se refiere al proceso de consolidar los datos de registro en un lugar centralizado. Mediante la recopilación y agregación, las herramientas SIEM eliminan la necesidad de revisar y analizar manualmente los datos de eventos accediendo a fuentes de datos individuales. En su lugar, todos los Datos de Evento son accesibles en un solo lugar: el SIEM.

![Las piezas del puzzle que representan las fuentes de datos se introducen en un SIEM y se procesan como un puzzle completo.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/S4RVzsQNTH62x3KYJ85Uxg_95172ee75d1c4665927dcb44cc168ff1_S35G010.png?expiry=1759795200000&hmac=tQWHHkV-JSgF1-uz9v-GAlTNP8CQDIzRjxdW2N8wl6s)

El Análisis sintáctico puede producirse durante el primer paso del proceso SIEM, cuando se recopilan y agregan los Datos. _El Análisis sintáctico_ mapea los datos según sus campos y sus valores correspondientes. Por ejemplo, el siguiente ejemplo de registro contiene campos con valores. Al principio, puede resultar difícil interpretar la información de este registro basándose en su formato:

April 3 11:01:21 server sshd[1088]: Failed password for user nuhara from 218.124.14.105 port 5023

En un formato analizado, los campos y los valores se extraen y se vinculan, lo que facilita su lectura e interpretación:

- host = server
    
- proceso = sshd
    
- usuario_fuente = nuhara
    
- ip de origen = 218.124.14.105
    
- puerto_fuente = 5023
    

### **Normalización de datos**

Las herramientas SIEM recopilan datos de muchas fuentes diferentes. Estos datos deben transformarse en un formato único para que puedan ser procesados fácilmente por el SIEM. Sin embargo, cada fuente de datos es diferente y los datos pueden formatearse de muchas maneras distintas. Por ejemplo, un registro de firewall puede tener un formato diferente al de un registro de servidor.

![Una solución SIEM ingiere datos sin procesar y los normaliza en datos estructurados.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/sO_SKjBLQ624WVuvgg9p_w_22b55ac3196c4b508dd1df3572065ff1_S35G009.png?expiry=1759795200000&hmac=n0rtR69RHtRHIplq6CvUbS1vjgpq1hoAuPIFfzA9xI4)

Los Datos de Eventos recopilados deben pasar por el proceso de normalización. _La normalización_ convierte los datos en un formato estándar y estructurado que se puede buscar fácilmente.

### **Analizar los datos**

Una vez recopilados, agregados y normalizados los datos de registro, el SIEM debe hacer algo útil con todos ellos para que los equipos de seguridad puedan investigar las amenazas. Durante este último paso del proceso, las herramientas SIEM analizan los Datos. El Análisis puede realizarse con algún tipo de lógica de Detección, como un conjunto de reglas y condiciones. A continuación, las herramientas SIEM aplican estas reglas a los datos y, si alguna actividad del registro coincide con una regla, se envían alertas a los equipos de ciberseguridad.

**Nota**: Una parte del proceso de análisis incluye la correlación. La _correlación_ implica la comparación de varios eventos de registro para identificar patrones comunes que indiquen posibles amenazas a la Seguridad.

## Herramientas SIEM

Existen muchas herramientas SIEM. Las siguientes son algunas herramientas SIEM utilizadas habitualmente en el sector de la ciberseguridad:

- AlienVault® OSSIM™
    
- Chronicle
    
- Elastic
    
- Exabeam
    
- Plataforma de Inteligencia de Seguridad IBM QRadar
    
- LogRhythm
    
- Splunk
    

## Puntos clave

Las herramientas SIEM recopilan y organizan enormes cantidades de Datos para crear estadísticas significativas para los Equipos de Seguridad. Si comprende cómo funcionan las herramientas SIEM, qué incluye el proceso y cómo las aprovechan las organizaciones, podrá contribuir a los esfuerzos para detectar y responder a los incidentes de Seguridad con eficacia. Con estos Conocimientos, podrá ayudar a analizar los datos de registro, identificar las amenazas y contribuir a las actividades de respuesta ante incidentes para ayudar a mejorar la Postura de seguridad y Proteger los recursos valiosos de las amenazas.