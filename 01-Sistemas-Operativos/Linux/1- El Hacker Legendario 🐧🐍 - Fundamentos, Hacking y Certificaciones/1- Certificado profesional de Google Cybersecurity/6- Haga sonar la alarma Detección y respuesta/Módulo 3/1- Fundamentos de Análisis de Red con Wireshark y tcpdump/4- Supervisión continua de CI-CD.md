

# **Monitorización continua de CI/CD: encontrar amenazas automáticamente**

En nuestra última lectura sobre métodos de detección de incidentes de ciberseguridad, exploró formas de descubrir amenazas. Aprendió sobre herramientas como los sistemas de detección de intrusiones (IDS) y la administración de información y eventos de seguridad (SIEM). Esta lectura se centra en la supervisión continua específicamente para sus canalizaciones de integración continua y entrega/despliegue continuos (CI/CD). La supervisión de su canal de CI/CD ayuda a proteger su cadena de suministro de software, y existen herramientas especiales que pueden detectar automáticamente actividades inusuales y ayudarle a identificar Indicadores de compromiso (IoC).

## **Automatización para detectar amenazas**

Las canalizaciones de CI/CD le ayudan a publicar software más rápidamente, pero también pueden abrir nuevas vulnerabilidades para los atacantes. Si alguien irrumpe en su canalización, podría añadir código, robar información privada o impedir que su software funcione. Por lo tanto, la supervisión continua que detecta automáticamente la actividad inusual de la canalización es fundamental. La supervisión eficaz de CI/CD utiliza la automatización para hacer algo más que recopilar registros. Utiliza herramientas de supervisión para encontrar automáticamente cosas inusuales que ocurren en los procesos de construcción, código o pasos de despliegue que pueden indicar posibles amenazas a la seguridad. Cuando se detectan estas amenazas, los equipos de seguridad pueden responder rápidamente y limitar los daños. Esta detección automática de amenazas es uno de los principales objetivos de una seguridad CI/CD sólida.

## **Indicadores de compromiso (IoC) comunes en los conductos de CI/CD**

Comprender los IoC comunes de CI/CD le ayuda a supervisar de forma eficaz y a encontrar rápidamente incidentes de seguridad. He aquí algunos ejemplos:

- **Cambios de código no autorizados:**
    
    - Cambios de código de personas que no deberían estar haciendo cambios.
        
    - Cambios de código realizados en momentos inusuales o desde lugares inesperados.
        
    - Cambios de código que parecen sospechosos, como código confuso, eliminaciones muy grandes sin una buena razón, o código que no sigue las reglas de codificación.
        
- **Patrones de despliegue sospechosos:**
    
    - Despliegues en sistemas inusuales o no aprobados (por ejemplo, despliegues de producción iniciados directamente desde ramas de desarrollador).
        
    - Despliegues que se producen en momentos inesperados o con demasiada frecuencia (despliegues fuera de los plazos de lanzamiento previstos).
        
    - Despliegues iniciados por cuentas de usuario poco habituales o cuentas automatizadas que no deberían pasar a producción.
        
- **Dependencias comprometidas:**
    
    - Encontrar vulnerabilidades conocidas (CVEs) en dependencias durante comprobaciones automatizadas en el proceso CI/CD.
        
    - Adición repentina de dependencias nuevas e inesperadas a las configuraciones de compilación.
        
    - Intentos de descargar dependencias de fuentes no oficiales o no fiables.
        
- **Ejecución inusual de la canalización:**
    
    - Pasos del pipeline que normalmente funcionan bien y de repente fallan.
        
    - Los pipelines tardan mucho más en ejecutarse sin una razón clara.
        
    - Cambios en el orden o la forma en que se ejecutan los pasos del pipeline sin que se hayan realizado cambios aprobados.
        
- **Intentos de exposición de secretos:**
    
    - Registros que muestran intentos de acceder a secretos desde lugares no aprobados en el proceso.
        
    - Descubrimiento de secretos privados codificados en cambios de código (lo ideal sería evitarlo antes, pero la supervisión puede detectar errores).
        

## **Seguridad proactiva mediante la supervisión de IoC**

La monitorización continua de los procesos CI/CD, centrada en la detección automatizada de anomalías y en la búsqueda de IoC, hace que su seguridad sea más sólida y proactiva. Mediante el uso de herramientas de supervisión para comprobar continuamente la actividad de las canalizaciones en busca de estos indicadores antes de que se produzcan daños graves, puede:

- **Responder rápidamente a los incidentes:** Encontrar los IoC en una fase temprana ayuda a los equipos de seguridad a responder rápidamente a posibles ataques, deteniendo los problemas antes de que los atacantes alcancen sus objetivos.
    
- **LIMITAR LOS DAÑOS:** Responder rápidamente basándose en la detección de IoC reduce el posible impacto de un problema de seguridad al limitar el tiempo que los atacantes están en la tubería.
    
- **Mejorar el conocimiento de las amenazas:** Comprobar los IoC proporciona información valiosa sobre cómo los atacantes se dirigen a su CI/CD, lo que ayuda a mejorar la seguridad y la caza de amenazas en el futuro.
    

## **Uso de la automatización para encontrar anomalías e IoCs**

Para supervisar los procesos de CI/CD y detectar automáticamente las amenazas, puede utilizar estos métodos:

### **Registro y auditoría exhaustivos**

Los registros detallados son la base de la supervisión. Los registros proporcionan los datos en bruto que las herramientas de supervisión comprueban en busca de actividad inusual y posibles Indicadores de compromiso (IoC). Los registros más comunes para encontrar anomalías incluyen:

- **Registros de ejecución de canalizaciones:** Para aprovechar eficazmente los registros de ejecución de canalizaciones para la supervisión de la seguridad, las herramientas especializadas emplean técnicas automatizadas de línea de base. Estas herramientas analizan los registros de ejecuciones típicas y satisfactorias de canalizaciones de CI/CD para establecer un perfil de funcionamiento normal. Esta línea de base engloba indicadores clave de rendimiento, como la duración estándar de cada etapa del proceso y las tasas de éxito y fracaso esperadas. Al supervisar continuamente los registros de ejecución y compararlos con esta línea de base establecida, las herramientas pueden detectar automáticamente actividades anómalas. Las desviaciones de la norma, incluidos los pasos del proceso que superan los tiempos de ejecución típicos, los errores inesperados o las alteraciones en el orden habitual de los pasos, se marcan como posibles Indicadores de compromiso (IoC), lo que justifica un mayor escrutinio de seguridad.
    
- **Registros de confirmación de código:** Realiza un seguimiento de los cambios en el código de cada proceso. Los cambios de código inusuales, como los cambios realizados por personas que no deberían estar realizando cambios, los cambios realizados a altas horas de la noche o los cambios con contenido sospechoso (como eliminaciones muy grandes o código confuso), son IoC importantes de supervisar.
    
- **Registros de acceso:** Las herramientas de monitorización pueden saber quién accede habitualmente a CI/CD. Los inicios de sesión inusuales, como los que se producen desde distintos países, los intentos fallidos de inicio de sesión seguidos de un inicio de sesión con éxito, o los intentos de inicio de sesión para cambiar ajustes importantes de las canalizaciones, son indicadores claros de compromiso.
    
- **Registros de despliegue:** Las herramientas pueden saber con qué frecuencia se producen los despliegues y qué aspecto tienen. Los despliegues inusuales, como los que se producen en momentos extraños o en lugares inesperados, pueden ser IoC.
    

### **Integración de la administración de información y eventos de seguridad (SIEM)**

Conectar sus registros de CI/CD a una herramienta SIEM puede ayudar a encontrar automáticamente anomalías a gran escala. Las plataformas SIEM están hechas para:

- **Encontrar anomalías automáticamente:** Los SIEM utilizan el aprendizaje automático y el análisis para encontrar automáticamente patrones inusuales en los registros de CI/CD, que son posibles IoC para investigar.
    
- **Utilizar reglas para alertar sobre IoC conocidos:** Puede configurar reglas específicas en el SIEM para encontrar IoC de CI/CD conocidos. Por ejemplo, las reglas pueden enviar alertas cuando:
    
    - Se detectan hashes de archivos maliciosos específicos (relacionados con ataques de CI/CD conocidos) en los resultados de la compilación.
        
    - Los servidores de CI/CD se conectan a servidores de Comando y control (C2) maliciosos conocidos (utilizando datos de inteligencia sobre amenazas).
        
    - Alguien intenta descargar o acceder a secretos privados fuera de los pasos aprobados del pipeline.
        

### **Alertas y notificaciones en tiempo real**

Las alertas automatizadas garantizan que los equipos de seguridad reciban notificaciones inmediatas sobre actividades inusuales y posibles IoC, para que puedan responder con rapidez. Las alertas deben configurarse para:

- **Fallos de compilación inusuales:** Fallos repetidos en los pasos del pipeline, especialmente después de cambios de código que no deberían causar fallos.
    
- **Cambios de código sospechosos (basados en anomalías):** Alertas enviadas por herramientas de análisis de código que encuentran cambios de código muy inusuales basados en el tamaño, autor o contenido confuso.
    
- **Intentos de exponer secretos:** Alertas enviadas por herramientas de seguridad cuando alguien intenta acceder o robar secretos de partes no aprobadas de la canalización.
    
- **Tráfico de red inusual:** Alertas de tráfico de red inusual desde servidores de CI/CD, especialmente tráfico que sale a ubicaciones desconocidas o sospechosas.
    

### **Monitorización del rendimiento para encontrar IoAs y descubrir IoCs**

La monitorización del rendimiento, aunque se utiliza principalmente para asegurarse de que las cosas están funcionando sin problemas, también puede ayudar indirectamente a encontrar IoCs. Los problemas de rendimiento (Indicadores de ataque - IoAs) como ralentizaciones repentinas o servidores CI/CD que se quedan sin recursos pueden llevar a comprobaciones más profundas que pueden descubrir IoCs.

### **Exploración continua de vulnerabilidades**

La comprobación periódica de la infraestructura de CI/CD en busca de puntos débiles puede detectar de forma proactiva partes vulnerables. Esto incluye Vulnerabilidades y exposiciones comunes (CVEs) en herramientas CI/CD, plugins y contenedores. Estos puntos débiles son IoC potenciales. Destacan las áreas que necesitan ser parcheadas de inmediato para evitar ataques y un posible compromiso de la tubería.

## **Puntos clave**

Al utilizar la automatización para supervisar sus canalizaciones de CI/CD, puede encontrar actividad inusual e identificar importantes Indicadores de compromiso. Con esta información, puede proteger su canalización de software y responder rápidamente a las amenazas. Esto permite a los ingenieros desarrollar, probar y desplegar código con confianza y resistencia frente a las amenazas. Al incorporar la seguridad a su CI/CD, permite a su equipo publicar funciones, mejoras y actualizaciones de seguridad críticas de forma rápida y fiable. Esto garantiza que el software no sólo se entrega de forma eficiente, sino también con el máximo nivel de seguridad, protegiendo de forma proactiva a su organización y a sus clientes.

**Recursos:**

1. Optimización de los registros para una canalización de CI/CD más eficaz [Mejores prácticas]. https://coralogix. [com/blog/optimizing-logs-for-a-more-effective-ci-cd-pipeline/](https://coralogix.com/blog/optimizing-logs-for-a-more-effective-ci-cd-pipeline/)
    
2. Optimice su CI/CD: Detección de anomalías manual con IA. https://www. [latesttechinsights.com/2024/04/streamline-your-cicd-hands-on-anomaly.html](https://www.latesttechinsights.com/2024/04/streamline-your-cicd-hands-on-anomaly.html)
    
3. ¿Qué es CI/CD? - Integración, entrega y despliegue continuos. https://www. [threatintelligence.com/blog/continuous-integration-continuous-delivery](https://www.threatintelligence.com/blog/continuous-integration-continuous-delivery)
    
4. Tuberías de CI/CD y DevOps: Una introducción. https://www. [splunk.com/en_us/blog/learn/ci-cd-devops-pipeline.html](https://www.splunk.com/en_us/blog/learn/ci-cd-devops-pipeline.html)