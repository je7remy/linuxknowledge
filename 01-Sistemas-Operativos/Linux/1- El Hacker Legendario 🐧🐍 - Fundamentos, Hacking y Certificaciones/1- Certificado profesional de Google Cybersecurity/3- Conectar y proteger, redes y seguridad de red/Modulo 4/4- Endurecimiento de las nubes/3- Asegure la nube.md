
A principios de este curso, se le presentó la [computación en la nube](https://www.coursera.org/learn/networks-and-network-security/lecture/BGlnq/cloud-networks). **La computación en la nube** es un modelo que permite un acceso cómodo y bajo demanda a un conjunto compartido de recursos informáticos configurables. Estos recursos pueden configurarse y liberarse con un mínimo esfuerzo de gestión o interacción con el proveedor de servicios.

Al igual que cualquier otra infraestructura de TI, una infraestructura de nube debe estar protegida. Esta lectura abordará algunas de las principales consideraciones de seguridad que son exclusivas de la nube y le presentará el modelo de responsabilidad compartida utilizado para la seguridad en la nube. Muchas organizaciones que utilizan recursos e infraestructuras en la nube expresan su preocupación por la privacidad de sus datos y recursos. Esta preocupación se aborda a través de la criptografía y otras medidas de seguridad adicionales, que se discutirán más adelante en este curso.

## Seguridad de la nube

Muchas organizaciones optan por utilizar servicios en la nube debido a la facilidad de implementación, la velocidad de despliegue, el ahorro de costes y la escalabilidad de estas opciones. La computación en la nube presenta retos de seguridad únicos que los analistas de ciberseguridad deben conocer.

### Gestión de identidad y acceso

La**gestión del acceso a la identidad (IAM)** es un conjunto de procesos y tecnologías que ayuda a las organizaciones a gestionar las identidades digitales en su entorno. Este servicio también autoriza cómo los usuarios pueden utilizar los diferentes recursos de la nube. Un problema común al que se enfrentan las organizaciones cuando utilizan la nube es la configuración poco precisa de los roles de usuario en la nube. Un rol de usuario mal configurado aumenta el riesgo al permitir que usuarios no autorizados tengan acceso a operaciones críticas en la nube.

### Configuración

La expansión del ecosistema de la nube introduce una complejidad significativa en la gestión de la red. Cada servicio en la nube requiere una configuración precisa para mantener los estándares de seguridad y cumplimiento. Este reto se intensifica durante las migraciones a la nube, donde es fundamental garantizar una configuración precisa para cada proceso migrado. Un descuido en este aspecto puede exponer la red a vulnerabilidades. Los servicios en la nube mal configurados son una fuente frecuente de brechas de seguridad, lo que subraya la importancia de que los administradores y arquitectos de redes presten una atención meticulosa a los detalles durante la migración y la gestión continua de los servicios en la nube.

### Superficie de ataque

Los proveedores de servicios en la nube (CSP) ofrecen a las organizaciones numerosas aplicaciones y servicios a bajo coste.

Cada servicio o aplicación en una red conlleva su propio conjunto de riesgos y vulnerabilidades y aumenta la superficie de ataque global de una organización. Una mayor superficie de ataque debe compensarse con mayores medidas de seguridad.

Las redes en la nube que utilizan muchos servicios introducen muchos puntos de entrada en la red de una organización. Sin embargo, si la red se diseña correctamente, la utilización de varios servicios no introduce más puntos de entrada en el diseño de la red de una organización. Estos puntos de entrada pueden utilizarse para introducir malware en la red y plantear otras vulnerabilidades de seguridad. Es importante señalar que los CSP a menudo se decantan por opciones más seguras y han sido sometidos a un mayor escrutinio que una red tradicional in situ.

### Ataques de día cero

Los ataques de día cero son una importante consideración de seguridad para las organizaciones que utilizan soluciones de red en nube o tradicionales en las instalaciones. Un ataque de **día** cero es un exploit desconocido hasta ahora. Es más probable que los CSP sepan de un ataque de día cero antes que una organización de TI tradicional. Los CSP disponen de métodos para parchear hipervisores y migrar cargas de trabajo a otras máquinas virtuales. Estos métodos garantizan que los clientes no se vean afectados por el ataque. También hay varias herramientas disponibles para parchear a nivel de sistema operativo que las organizaciones pueden utilizar.

### Visibilidad y seguimiento

Los administradores de red tienen acceso a todos los paquetes de datos que cruzan la red, tanto con redes locales como en la nube. Pueden husmear e inspeccionar los paquetes de datos para conocer el rendimiento de la red o comprobar posibles amenazas y ataques.

Este tipo de visibilidad también se ofrece en la nube a través de registros de flujo y herramientas, como la duplicación de paquetes. Los CSP asumen la responsabilidad de la seguridad en la nube, pero no permiten que las organizaciones que utilizan su infraestructura supervisen el tráfico en los servidores del CSP. Muchos CSP ofrecen fuertes medidas de seguridad para proteger su infraestructura. Aun así, esta situación puede preocupar a las organizaciones acostumbradas a tener pleno acceso a su red y sus operaciones. Los CSP pagan auditorías de terceros para verificar el grado de seguridad de una red en la nube e identificar posibles vulnerabilidades. Las auditorías pueden ayudar a las organizaciones a identificar si alguna vulnerabilidad se origina en la infraestructura local y si hay algún incumplimiento por parte de su CSP.

### Las cosas cambian rápido en la nube

Los CSP son grandes organizaciones que trabajan duro para mantenerse al día de los avances tecnológicos. Para las organizaciones que están acostumbradas a tener el control de cualquier ajuste realizado en su red, esto puede suponer un reto potencial. Las actualizaciones de los servicios en la nube pueden afectar a la seguridad de las organizaciones que los utilizan. Por ejemplo, puede ser necesario cambiar las configuraciones de conexión en función de las actualizaciones del CSP.

Las organizaciones que utilizan CSP suelen tener que actualizar sus procesos de TI. Es posible que las organizaciones continúen siguiendo las mejores prácticas establecidas para cambios, configuraciones y otras consideraciones de seguridad. Sin embargo, una organización podría tener que adoptar un enfoque diferente de forma que se alinee con los cambios realizados por el CSP.

La Red en la nube ofrece varias opciones que pueden parecer atractivas para una pequeña empresa, opciones que nunca podrían permitirse construir en sus propias instalaciones. Sin embargo, es importante tener en cuenta que cada servicio añade complejidad al perfil de seguridad de la organización, y que necesitarán personal de seguridad para supervisar todos los servicios en la nube.

## Modelo de Responsabilidad compartida

Un principio de seguridad de la nube comúnmente aceptado es el modelo de Responsabilidad compartida. El **modelo de responsabilidad compartida** establece que el CSP debe asumir la responsabilidad de la seguridad que afecta a la infraestructura de la nube, incluidos los centros de datos físicos, los hipervisores y los sistemas operativos del host. La empresa que utiliza el servicio en nube es responsable de los activos y procesos que almacena u opera en la nube.

El modelo de responsabilidad compartida garantiza que tanto el CSP como los usuarios están de acuerdo sobre dónde empieza y termina su responsabilidad en materia de seguridad. Se produce un problema cuando las organizaciones asumen que el CSP se ocupa de una seguridad de la que no se han responsabilizado. Un ejemplo de ello son las aplicaciones y configuraciones en la nube. El CSP asume la responsabilidad de proteger la nube, pero es responsabilidad de la organización asegurarse de que los servicios están configurados correctamente de acuerdo con los requisitos de seguridad de su organización.

## Puntos clave

Es esencial conocer las consideraciones de seguridad que son exclusivas de la nube y comprender el modelo de responsabilidad compartida para la seguridad de la nube. Las organizaciones son responsables de configurar correctamente y mantener las mejores prácticas de seguridad para sus servicios en la nube. El modelo de responsabilidad compartida garantiza que tanto el CSP como los usuarios estén de acuerdo sobre de qué es responsable la organización y de qué es responsable el CSP a la hora de proteger la infraestructura de la nube.