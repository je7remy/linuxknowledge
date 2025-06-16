
Anteriormente, se le presentaron las herramientas de administración de eventos e información de seguridad (SIEM) y algunos paneles de SIEM. También aprendió sobre las diferentes amenazas, riesgos y vulnerabilidades que puede experimentar una organización. En esta lectura, aprenderá más sobre los datos del panel SIEM y cómo los profesionales de la ciberseguridad utilizan esos datos para identificar una posible amenaza, riesgo o vulnerabilidad.

## Splunk

Splunk ofrece diferentes opciones de herramientas SIEM: Splunk® Enterprise y Splunk® Cloud. Ambos le permiten revisar los datos de una organización en paneles. Esto ayuda a los profesionales de la seguridad a gestionar la infraestructura interna de una organización mediante la recopilación, la búsqueda, la supervisión y el análisis de datos de registro de múltiples fuentes para obtener una visibilidad completa de las operaciones diarias de una organización.

Revise los siguientes paneles de Splunk y sus propósitos:

### **Panel de control de la posición de seguridad**

El panel de control de la posición de seguridad está diseñado para los centros de operaciones de seguridad (SOC). Muestra las últimas 24 horas de los eventos y tendencias notables relacionados con la seguridad de una organización y permite a los profesionales de la seguridad determinar si la infraestructura y las políticas de seguridad están funcionando según lo diseñado. Los analistas de seguridad pueden usar este panel para monitorear e investigar posibles amenazas en tiempo real, como la actividad sospechosa de la red que se origina en una dirección IP específica.

### **Panel de resumen ejecutivo**

El panel de resumen ejecutivo analiza y supervisa el estado general de la organización a lo largo del tiempo. Esto ayuda a los equipos de seguridad a mejorar las medidas de seguridad que reducen el riesgo. Los analistas de seguridad pueden usar este panel para proporcionar información de alto nivel a las partes interesadas, como generar un resumen de los incidentes y tendencias de seguridad durante un período de tiempo específico.

### **Panel de revisión de incidentes**

El panel de revisión de incidentes permite a los analistas identificar patrones sospechosos que pueden ocurrir en caso de un incidente. Ayuda al resaltar los elementos de mayor riesgo que necesitan una revisión inmediata por parte de un analista. Este panel puede ser muy útil porque proporciona una línea de tiempo visual de los eventos que conducen a un incidente.

### **Panel de análisis de riesgos**

El panel de análisis de riesgos ayuda a los analistas a identificar el riesgo para cada objeto de riesgo (por ejemplo, un usuario específico, una computadora o una dirección IP). Muestra cambios en la actividad o el comportamiento relacionados con el riesgo, como un usuario que inicia sesión fuera del horario laboral normal o un tráfico de red inusualmente alto desde una computadora específica. Un analista de seguridad puede usar este panel para analizar el impacto potencial de las vulnerabilidades en activos críticos, lo que ayuda a los analistas a priorizar sus esfuerzos de mitigación de riesgos.

## Crónica

Chronicle es una herramienta SIEM nativa de la nube de Google que retiene, analiza y busca datos de registro para identificar posibles amenazas de seguridad, riesgos y vulnerabilidades. Chronicle le permite recopilar y analizar datos de registro de acuerdo con:

- Un activo específico
    
- Un nombre de dominio
    
- Un usuario
    
- Una dirección IP
    

Chronicle proporciona varios paneles que ayudan a los analistas a monitorear los registros de una organización, crear filtros y alertas, y rastrear nombres de dominio sospechosos.

Revise los siguientes paneles de Chronicle y sus propósitos:

### **Panel de información empresarial**

El panel de información empresarial destaca las alertas recientes. Identifica nombres de dominio sospechosos en los registros, conocidos como indicadores de compromiso (IOC). Cada resultado se etiqueta con una puntuación de confianza para indicar la probabilidad de una amenaza. También proporciona un nivel de gravedad que indica la importancia de cada amenaza para la organización. Un analista de seguridad puede usar este panel para monitorear los intentos de inicio de sesión o acceso a datos relacionados con un activo crítico, como una aplicación o un sistema, desde ubicaciones o dispositivos inusuales.

### **Panel** **de ingesta de datos y estado**

El panel de control de estado e ingesta de datos muestra el número de registros de eventos, las fuentes de registro y las tasas de éxito de los datos que se procesan en Chronicle. Un analista de seguridad puede utilizar este panel para asegurarse de que los orígenes de registro estén configurados correctamente y de que los registros se reciban sin errores. Esto ayuda a garantizar que se resuelvan los problemas relacionados con los registros para que el equipo de seguridad tenga acceso a los datos de registro que necesita.

### **Panel** de **partidos** del **COI**

El panel de coincidencias de IOC indica las principales amenazas, riesgos y vulnerabilidades para la organización. Los profesionales de la seguridad utilizan este panel para observar los nombres de dominio, las direcciones IP y los IOC de los dispositivos a lo largo del tiempo con el fin de identificar tendencias. Esta información se utiliza para dirigir el enfoque del equipo de seguridad a las amenazas de mayor prioridad. Por ejemplo, los analistas de seguridad pueden usar este panel para buscar actividad adicional asociada con una alerta, como un inicio de sesión de usuario sospechoso desde una ubicación geográfica inusual.

### **Cuadro de mandos** **principal**

El panel principal muestra un resumen de alto nivel de la información relacionada con la ingesta de datos, las alertas y la actividad de eventos de la organización a lo largo del tiempo. Los profesionales de la seguridad pueden usar este panel para acceder a una línea de tiempo de eventos de seguridad, como un aumento en los intentos de inicio de sesión fallidos, para identificar tendencias de amenazas en orígenes de registro, dispositivos, direcciones IP y ubicaciones físicas.

### **Panel de detecciones de reglas**

El panel de detecciones de reglas proporciona estadísticas relacionadas con los incidentes con las ocurrencias, gravedades y detecciones más altas a lo largo del tiempo. Los analistas de seguridad pueden usar este panel para acceder a una lista de todas las alertas activadas por una regla de detección específica, como una regla diseñada para alertar cada vez que un usuario abre un archivo adjunto malintencionado conocido desde un correo electrónico. Luego, los analistas usan esas estadísticas para ayudar a administrar incidentes recurrentes y establecer tácticas de mitigación para reducir el nivel de riesgo de una organización.

### **Panel** **de información general** sobre el inicio de sesión del usuario

El panel de información general sobre el inicio de sesión del usuario proporciona información sobre el comportamiento de acceso de los usuarios en toda la organización. Los analistas de seguridad pueden usar este panel para acceder a una lista de todos los eventos de inicio de sesión de usuario para identificar la actividad inusual del usuario, como un usuario que inicia sesión desde varias ubicaciones al mismo tiempo. Esta información se usa para ayudar a mitigar las amenazas, los riesgos y las vulnerabilidades de las cuentas de usuario y las aplicaciones de la organización.

## Conclusiones clave

Las herramientas SIEM proporcionan paneles que ayudan a los profesionales de la seguridad a organizar y centrar sus esfuerzos de seguridad. Esto es importante porque permite a los analistas reducir el riesgo identificando, analizando y remediando los elementos de mayor prioridad de manera oportuna. Más adelante en el programa, tendrá la oportunidad de practicar el uso de varias funciones y comandos de la herramienta SIEM para consultas de búsqueda.