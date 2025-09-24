
Anteriormente, usted aprendió acerca de una evaluación de **vulnerabilidad**, que es el proceso de revisión interna de los sistemas de Seguridad de una organización. Una organización realiza evaluaciones de vulnerabilidad para identificar debilidades y prevenir ataques. Las herramientas de exploración de vulnerabilidades se utilizan habitualmente para simular amenazas encontrando vulnerabilidades en una superficie de ataque. También ayudan a los Equipos de Seguridad a tomar medidas proactivas para implementar su estrategia de remediación.

Los escáneres de vulnerabilidades son herramientas importantes que probablemente utilizará sobre el terreno. En esta lectura, explorará cómo funcionan los escáneres de vulnerabilidades y los tipos de escaneos que pueden realizar.

## ¿Qué es un escáner de vulnerabilidades?

Un **escáner de vulnerabilidades** es un software que compara automáticamente las vulnerabilidades y exposiciones conocidas con las tecnologías de la red. En general, estas herramientas escanean los sistemas para encontrar errores de configuración o de programación.

Las herramientas de escaneado se utilizan para analizar cada una de las cinco superficies de ataque que conoció en [el vídeo sobre la estrategia de defensa en profundidad](https://www.coursera.org/learn/assets-threats-and-vulnerabilities/lecture/IdvXj/defense-in-depth-strategy):

1. Capa de**perímetro**, como los sistemas de autenticación que validan la accesibilidad de los usuarios
    
2. **Capa de** red, que se compone de tecnologías como firewalls de red y otras
    
3. Capa**de punto** final, que describe los dispositivos de una red, como ordenadores portátiles, de sobremesa o servidores
    
4. **Capa de** aplicación, que implica el software con el que interactúan los usuarios
    
5. Capa de**datos**, que incluye cualquier información almacenada, en tránsito o en uso
    

Cuando comienza un escaneado de cualquier capa, la herramienta de escaneado compara los hallazgos con las bases de datos de amenazas a la seguridad. Al final de la exploración, la herramienta marca cualquier vulnerabilidad que encuentre y la añade a su base de datos de referencia. Cada exploración añade más información a la base de datos, lo que ayuda a la herramienta a ser más precisa en su análisis.

**Nota:** Las bases de datos de vulnerabilidades también son actualizadas rutinariamente por la empresa que diseñó el software de exploración.

## Realización de exploraciones

Los escáneres de vulnerabilidades están pensados para no ser intrusivos. Es decir, no rompen ni se aprovechan de un sistema como lo haría un atacante. En su lugar, simplemente escanean una superficie y le alertan de cualquier puerta potencialmente desbloqueada en sus sistemas.

**Nota:** Aunque los escáneres de vulnerabilidades no son intrusivos, hay casos en los que un escáner puede causar problemas inadvertidamente, como bloquear un sistema.

Estas herramientas se utilizan de varias maneras para escanear una superficie. Cada enfoque corresponde a la vía que podría seguir un Agente de amenaza. A continuación, puede explorar cada tipo de escaneado para tener una idea más clara al respecto.

**Externo frente a interno**

Los escaneos externos e internos simulan el enfoque de un atacante.

Los escaneos_externos_ prueban la capa perimetral fuera de la red interna. Analizan sistemas orientados al exterior, como sitios web y firewalls. Este tipo de exploraciones pueden descubrir puntos vulnerables, como puertos de red o servidores vulnerables.

Los escaneos_internos_ parten del extremo opuesto, examinando los sistemas internos de una organización. Por ejemplo, este tipo de escaneado podría analizar el software de aplicación en busca de puntos débiles en la forma en que gestiona la entrada de datos de los usuarios.

### **Autenticación frente a no autenticación**

Los escaneos autenticados y no autenticados simulan si un usuario tiene o no acceso a un sistema.

Los escaneos_autenticados_ pueden probar un sistema registrándose con una cuenta de usuario real o incluso con una cuenta de administrador. Estas cuentas de servicio se utilizan para comprobar vulnerabilidades, como controles de acceso rotos.

Los escaneos_no_ autenticados simulan agentes de amenaza externos que no tienen acceso a los recursos de su empresa. Por ejemplo, un escaneado podría analizar los recursos compartidos de archivos dentro de la organización que se utilizan para albergar documentos exclusivamente internos. Los usuarios no autentificados deberían recibir resultados de "acceso denegado" si intentaran abrir estos archivos. Sin embargo, se identificaría una vulnerabilidad si pudieran acceder a un archivo.

### **Limitado frente a exhaustivo**

Los escaneos limitados y exhaustivos se centran en dispositivos concretos a los que acceden usuarios internos y externos.

Los escaneos_limitados_ analizan dispositivos concretos de una red, como la búsqueda de errores de configuración en un firewall.

Los escaneados_exhaustivos_ analizan todos los dispositivos conectados a una red. Esto incluye sistemas operativos, bases de datos de usuarios, etc.

**Consejo profesional:** La exploración de descubrimiento debe realizarse antes de las exploraciones limitadas o exhaustivas. La exploración de descubrimiento se utiliza para hacerse una idea de las computadoras, dispositivos y puertos abiertos que hay en una red.

## Puntos clave

Encontrar vulnerabilidades requiere pensar en todas las posibilidades. Los escaneos de vulnerabilidad varían en función de las superficies que una organización esté evaluando. Por lo general, los profesionales de seguridad experimentados lideran el esfuerzo de configurar y realizar este tipo de escaneos para crear un perfil de la postura de seguridad de una empresa. Sin embargo, los analistas también desempeñan una función importante en el proceso. Los resultados de un escaneado de vulnerabilidad a menudo conducen a la renovación de los esfuerzos de cumplimiento, a cambios en los procedimientos y a la aplicación de parches en el sistema. Comprender los objetivos de los tipos comunes de escáneres de vulnerabilidad le ayudará a participar en estos ejercicios proactivos de Seguridad siempre que sea posible.

**Consejo:** Para explorar el software escáner de vulnerabilidades utilizado habitualmente en el sector de la ciberseguridad, en su navegador preferido introduzca términos de búsqueda similares a "software escáner de vulnerabilidades popular" y/o "software escáner de vulnerabilidades de código abierto utilizado en ciberseguridad".