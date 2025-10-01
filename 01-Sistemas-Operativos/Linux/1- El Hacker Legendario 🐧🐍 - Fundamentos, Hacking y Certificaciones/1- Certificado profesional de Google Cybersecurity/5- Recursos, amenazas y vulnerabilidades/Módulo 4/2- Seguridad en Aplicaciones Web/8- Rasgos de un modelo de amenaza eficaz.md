
El **Modelado de amenazas** es el proceso de identificación de los recursos, sus vulnerabilidades y el modo en que cada uno de ellos está expuesto a las amenazas. Es un enfoque estratégico que combina varias actividades de Seguridad, como la gestión de vulnerabilidades, el análisis de amenazas y la Respuesta ante incidentes. Los Equipos de Seguridad suelen realizar estos ejercicios para asegurarse de que sus sistemas están adecuadamente protegidos. Otro uso del modelado de amenazas es encontrar proactivamente formas de reducir los riesgos de cualquier sistema o proceso empresarial.

Tradicionalmente, el Modelado de amenazas se asocia al Campo del desarrollo de aplicaciones. En esta lectura, aprenderá sobre los marcos comunes de Modelado de amenazas que se utilizan para diseñar software que pueda resistir ataques. También aprenderá sobre la creciente necesidad de Seguridad de las aplicaciones y las formas en las que puede participar.

## Por qué es importante la Seguridad de las aplicaciones

Las aplicaciones se han convertido en una parte esencial del éxito de muchas organizaciones. Por ejemplo, las aplicaciones basadas en la web permiten a los clientes de cualquier parte del mundo conectar con las empresas, sus socios y otros clientes.

Las aplicaciones móviles también han cambiado la forma en que las personas acceden al mundo digital. Los teléfonos inteligentes son a menudo la principal vía de intercambio de Datos entre los usuarios y una empresa. El volumen de datos que procesan las aplicaciones hace que su seguridad sea clave para reducir el riesgo para todos los que están conectados.

Por ejemplo, supongamos que una aplicación utiliza bibliotecas de registro basadas en Java con la vulnerabilidad Log4Shell[(CVE-2021-44228](https://nvd.nist.gov/vuln/detail/CVE-2021-44228)). Si no se parchea, esta vulnerabilidad puede permitir la ejecución remota de código que un atacante puede utilizar para obtener acceso completo a su sistema desde cualquier parte del mundo. Si se explota, una vulnerabilidad crítica como ésta puede afectar a millones de dispositivos.

## Defensa de la capa de aplicación

La defensa de la capa de aplicación requiere pruebas adecuadas para descubrir los puntos débiles que pueden provocar riesgos. El Modelado de amenazas es una de las principales formas de garantizar que una aplicación cumple los requisitos de Seguridad. Un Equipo DevSecOps, siglas de desarrollo, seguridad y operaciones, suele realizar estos análisis.

Un proceso típico de Modelado de amenazas se realiza en un ciclo:

- Definir el Alcance
    
- Identificar las amenazas
    
- Caracterizar el entorno
    
- Analizar las amenazas
    
- Mitigar riesgos
    
- Evaluar los resultados
    

![Los seis pasos de un ejercicio de Modelado de amenazas mostrados como un ciclo.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/jcxiyXGsSgiFzXVKEA2MlA_e5fb4921773047658ae29b53532617f1_IkNCZRnA8vFZL9bPa3yahdiNcz5YvwZzxcn1GyvaYWkF00CzvIWq3MkCyR_IgzOSs5bKO7iIiROjznDNMHk60Cun_ZP-OriA0rGw7gQqWHj-jiTAFPzddosn0AJ9zQxySZuHVXi856Oqf1ZWNZBt34U?expiry=1759363200000&hmac=JUl9ZNRQ_YnYagee3t8SBBuxgqG55rl_AU9UYSaAMek)

Idealmente, el Modelado de amenazas debería realizarse antes, durante y después del desarrollo de una aplicación. Sin embargo, llevar a cabo un análisis exhaustivo del software requiere tiempo y Recursos. Debe evaluarse todo, desde la arquitectura de la aplicación hasta sus fines empresariales. Por ello, a lo largo de los años se han desarrollado varios marcos de Modelado de amenazas para facilitar el proceso.

**Nota:** El Modelado de amenazas debe incorporarse en cada etapa del ciclo de vida de desarrollo del software, o SDLC.

## Marcos comunes

A la hora de realizar el Modelado de amenazas, existen múltiples métodos que se pueden utilizar, como:

- STRIDE
    
- PASTA
    
- Trike
    
- VAST
    

Las organizaciones pueden utilizar cualquiera de ellos para recopilar información y tomar decisiones para mejorar su postura de Seguridad. En última instancia, el Modelo "correcto" depende de la situación y de los tipos de riesgos a los que pueda enfrentarse una aplicación.

### **STRIDE**

STRIDE es un framework de Modelado de amenazas desarrollado por Microsoft. Se utiliza habitualmente para identificar vulnerabilidades en seis vectores de ataque específicos. El acrónimo representa cada uno de estos vectores: suplantación de identidad, manipulación, repudio, revelación de información, denegación de servicio y elevación de privilegios.

### **PASTA**

El **Proceso de Simulación de Ataques y Análisis de Amenazas** (PASTA) es un proceso de Modelado de Amenazas centrado en el Riesgo desarrollado por dos líderes de OWASP y apoyado por una empresa de ciberseguridad llamada VerSprite. Su principal objetivo es descubrir pruebas de amenazas viables y representar esta información como un Modelo. El diseño basado en pruebas de PASTA puede aplicarse al modelado de amenazas de una aplicación o del entorno que soporta dicha aplicación. Su proceso de siete etapas consta de varias actividades que incorporan artefactos de seguridad relevantes del entorno, como los informes de evaluación de vulnerabilidades.

### **Trike**

Trike es una metodología y una herramienta de código abierto que adopta un enfoque centrado en la Seguridad para el modelado de amenazas. Se suele utilizar para centrarse en los permisos de seguridad, los casos de uso de las aplicaciones, los modelos de privilegios y otros elementos que sustentan un entorno seguro.

### **VAST**

El framework de Modelado de Amenazas Visual, Ágil y Sencillo (VAST) forma parte de una plataforma automatizada de modelado de amenazas llamada ThreatModeler®. Muchos equipos de Seguridad optan por utilizar VAST como forma de automatizar y agilizar sus evaluaciones de modelado de amenazas.

## Participar en el Modelado de amenazas

El Modelado de amenazas suele ser realizado por profesionales de la Seguridad experimentados, pero casi nunca se hace en solitario. Esto es especialmente cierto cuando se trata de la seguridad de las aplicaciones. Los Programas son sistemas complejos responsables de manejar muchos Datos y procesar una gran variedad de órdenes de usuarios y otros sistemas.

Una de las claves del Modelado de amenazas es formular las preguntas adecuadas:

- ¿En qué estamos trabajando?
    
- ¿Qué tipo de cosas pueden salir mal?
    
- ¿Qué estamos haciendo al respecto?
    
- ¿Lo hemos abordado todo?
    
- ¿Hemos hecho un buen trabajo?
    

Lleva tiempo y práctica aprender a trabajar con cosas como diagramas de flujo de datos y árboles de ataque. Sin embargo, cualquiera puede aprender a ser un modelador de amenazas eficaz. Independientemente de su nivel de experiencia, participar en uno de estos ejercicios siempre empieza simplemente por hacerse las preguntas adecuadas.

## Puntos clave

Muchas personas dependen de aplicaciones de software en su día a día. Asegurar las aplicaciones que la gente utiliza nunca ha sido tan importante. El Modelado de amenazas es una de las principales formas de determinar si existen Controles de seguridad para proteger la privacidad de los datos. Adquirir las habilidades necesarias para liderar una actividad de Modelado de amenazas es cuestión de práctica. Sin embargo, incluso un analista de Seguridad con poca experiencia puede ser un valioso colaborador en el proceso. Todo empieza por aplicar una mentalidad de atacante y pensar de forma crítica sobre cómo se manejan los Datos.