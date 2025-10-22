
Hasta ahora, ha aprendido sobre las firmas de detección y se le presentó Suricata, un Sistema de detección de intrusiones (IDS).

En esta lectura, explorará más sobre Suricata. También aprenderá sobre el valor de escribir firmas y configuraciones personalizadas. Esta es una habilidad importante que debe desarrollar en su carrera de ciberseguridad porque es posible que se le encargue la implementación y el mantenimiento de herramientas IDS.

## Introducción a Suricata

[**Suricata**](https://suricata.io/) es un Sistema de detección de intrusiones, un Sistema de prevención de intrusiones y una herramienta de análisis de redes de código abierto.

### **Características de Suricata**

Existen tres formas principales de utilizar Suricata:

- **Sistema de detección de intrusiones****(IDS**): Como IDS basado en la red, Suricata puede monitorizar el Tráfico de red y alertar sobre actividades sospechosas e intrusiones. Suricata también puede configurarse como un IDS basado en host para supervisar las actividades del sistema y de la red de un único host, como una computadora.
    
- **Sistema de prevención de intrusiones****(IPS**): Suricata también puede funcionar como un sistema de prevención de intrusiones (IPS) para detectar y bloquear actividades y tráfico maliciosos. Ejecutar Suricata en modo IPS requiere una configuración adicional, como habilitar el modo IPS.
    
- **Monitoreo de Seguridad de** red**(NSM**): En este modo, Suricata ayuda a mantener las redes seguras produciendo y guardando registros de red relevantes. Suricata puede analizar el tráfico de red en directo, los archivos de captura de paquetes existentes y crear y guardar capturas de paquetes completas o condicionales. Esto puede ser útil para análisis forenses, respuesta ante incidentes y para probar firmas. Por ejemplo, puede activar una alerta y capturar el tráfico de red en directo para generar registros de tráfico, que luego podrá analizar para refinar las firmas de detección.
    

## Reglas

Las reglas o firmas se utilizan para identificar patrones, comportamientos y condiciones específicos del tráfico de red que podrían indicar una actividad maliciosa. Los términos regla y firma se utilizan a menudo indistintamente en Suricata. Los analistas de Seguridad utilizan **firmas**, o patrones asociados con actividad maliciosa, para detectar y alertar sobre actividad maliciosa específica. Las reglas también pueden utilizarse para proporcionar un contexto y una visibilidad adicionales de los sistemas y redes, ayudando a identificar posibles amenazas a la seguridad o vulnerabilidades.

Suricata utiliza el Análisis de **firmas**, que es un Método de Detección utilizado para encontrar Eventos de Interés. Las Firmas constan de tres componentes:

- **Acción**: El primer componente de una firma. Describe la acción a tomar si la actividad de la red o del sistema coincide con la firma. Algunos ejemplos son: alertar, pasar, descartar o rechazar.
    
- **Encabezado**: El Encabezado incluye información sobre el Tráfico de red como direcciones IP de origen y destino, puertos de origen y destino, protocolo y dirección del tráfico.
    
- **Opciones de regla:** Las opciones de regla le proporcionan diferentes opciones para personalizar las firmas.
    

He aquí un ejemplo de una firma Suricata:

![Una firma Suricata con una acción, una cabecera y opciones de regla.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/sUAYMHVdQ-2IJCnBysJmzg_c3deef0b2a6c454fbc39b674cc0bc9f1_CS_R-138_Suricata-signature.png?expiry=1761264000000&hmac=PaxCh0WolcjmEUfne_GbVeasM435aW_IfBBQJt1ZZeM)

Las opciones de regla tienen un orden específico y cambiar su orden cambiaría el significado de la regla.

**Nota**: Los términos regla y Firma son sinónimos.

Nota**:** El orden de las reglas se refiere al orden en que éstas son evaluadas por Suricata. Las reglas se procesan en el orden en que están definidas en el archivo de configuración. Sin embargo, Suricata procesa las reglas en un orden diferente por defecto: pasar, descartar, rechazar y alerta. El orden de las reglas afecta al veredicto final de un paquete, especialmente cuando se producen acciones contradictorias, como cuando una regla de abandono y una de alerta coinciden en el mismo paquete.

### **Reglas personalizadas**

Aunque Suricata viene con reglas preescritas, es muy recomendable que modifique o personalice las reglas existentes para satisfacer sus Requisitos de Seguridad específicos.

No existe un enfoque único para la creación y modificación de reglas. Esto se debe a que la infraestructura de TI de cada organización es diferente. Los Equipos de Seguridad deben probar y modificar exhaustivamente las firmas de Detección en función de sus necesidades.

La creación de reglas personalizadas ayuda a adaptar la Detección y el Monitoreo. Las reglas personalizadas ayudan a minimizar la cantidad de falsas alertas positivas que reciben los equipos de Seguridad. Es importante desarrollar la capacidad de escribir firmas eficaces y personalizadas para poder aprovechar al máximo la potencia de las tecnologías de Detección.

## Archivo de configuración

Antes de que las herramientas de detección se implementen y puedan empezar a monitorizar sistemas y redes, debe configurar adecuadamente sus ajustes para que sepan qué hacer. Un **archivo** de configuración es un archivo utilizado para configurar los ajustes de una aplicación. Los archivos de configuración le permiten personalizar exactamente cómo desea que su IDS interactúe con el resto de su entorno.

El archivo de configuración de Suricata es suricata.yaml, que utiliza el formato de archivo YAML para la sintaxis y la estructura.

## Archivos de registro

Hay dos archivos de registro que Suricata genera cuando se activan las alertas:

- eve.**json**: El archivo eve.json es el archivo de registro estándar de Suricata. Este archivo contiene información detallada y metadatos sobre los eventos y alertas generados por Suricata almacenados en formato JSON. Por ejemplo, los eventos de este archivo contienen un identificador único llamado flow_id que se utiliza para correlacionar los registros o alertas relacionados con un único flujo de red, lo que facilita el análisis del tráfico de red. El archivo eve.json se utiliza para análisis más detallados y se considera un formato de archivo mejor para el análisis sintáctico de registros y la ingestión de registros SIEM.
    
- fast**.**log: El archivo fast.log se utiliza para registrar información mínima sobre alertas, incluyendo detalles básicos sobre la dirección IP y el puerto del tráfico de red. El archivo fast.log se utiliza para el registro y las alertas básicas y se considera un formato de archivo heredado y no es adecuado para tareas de respuesta ante incidentes o de caza de amenazas.
    

La principal diferencia entre el archivo eve.json y el archivo fast.log es el nivel de detalle que se registra en cada uno. El archivo fast.log registra información básica, mientras que el archivo eve.json contiene información detallada adicional.

## Puntos clave

En esta lectura, ha explorado algunas de las características de Suricata, la sintaxis de las reglas y la importancia de la configuración. Comprender cómo configurar las tecnologías de Detección y escribir reglas eficaces le proporcionará una clara estadística de la actividad que tiene lugar en un entorno, de modo que pueda mejorar la capacidad de detección y la visibilidad de la red. ¡Anímese y empiece a practicar el uso de Suricata en la próxima actividad!

## Recursos para más Información

Si desea obtener más información sobre Suricata, incluida la gestión y el rendimiento de las reglas, consulte los siguientes Recursos:

- [Guía del usuario de Suricata](https://suricata.readthedocs.io/en/latest/index.html#)
    
- [Características de Suricata](https://suricata.io/features/)
    
- [Gestión de reglas](https://suricata.readthedocs.io/en/latest/rule-management/suricata-update.html)
    
- [Análisis del rendimiento de las reglas](https://suricata.readthedocs.io/en/latest/configuration/suricata-yaml.html#engine-analysis-and-profiling)
    
- [Webinar sobre la Caza de amenazas de Suricata](https://youtu.be/kaDGolhTu94)
    
- [Introducción a la redacción de reglas de Suricata](https://youtu.be/tvoqFBVSShA)
    
- [Ejemplos jq de Eve.json](https://suricata.readthedocs.io/en/latest/output/eve/eve-json-examplesjq.html)