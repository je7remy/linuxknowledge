### **Descripción general**

Una de las fases más importantes (si no la más importante) de cualquier participación en las pruebas de penetración es la fase de planificación y preparación. Durante esta fase, tendrá un alcance claro de su compromiso. Si no tienes el alcance correcto, definitivamente tendrás problemas con tu cliente (si trabajas como consultor) o con tu jefe (si eres parte de un red team corporativo), e incluso podrías encontrar problemas legales.

**NOTA** Un _red team es un grupo de expertos en ciberseguridad y probadores de penetración contratados por una organización para imitar a un actor de amenazas real al exponer vulnerabilidades y riesgos relacionados con la tecnología, las personas y la seguridad física. Un _blue team_ es un equipo de seguridad corporativo que defiende a la organización contra las amenazas de ciberseguridad (es decir, los analistas del centro de operaciones de seguridad, los equipos de respuesta a incidentes de seguridad informática [CSIRT], los equipos de seguridad de la información [InfoSec] y otros).

Los siguientes son algunos conceptos clave que debe abordar y comprender en la fase de planificación y preparación:

- El público objetivo
- Las reglas de enfrentamiento
- La ruta de escalamiento de la comunicación y los canales de comunicación
- Los recursos y requisitos disponibles
- El presupuesto total para el compromiso
- Cualquier descargo de responsabilidad específico
- Cualquier restricción técnica
- Los recursos disponibles para usted como probador de penetración

En las siguientes secciones se tratan estos conceptos clave en detalle.

### **Consideraciones de cumplimiento normativo**

Debe estar familiarizado con varias consideraciones de cumplimiento normativo para tener éxito en el hacking ético y las pruebas de penetración, no solo para completar evaluaciones basadas en el cumplimiento, sino también para comprender qué regulaciones pueden afectarle a usted y a su cliente.

Comencemos a revisar estas consideraciones asumiendo que está contratado para realizar una evaluación basada en el cumplimiento. En ese escenario, se le contrata a usted (el evaluador de penetración) para verificar y auditar la posición de seguridad de la organización y para asegurarse de que la organización cumple con las regulaciones específicas, como las siguientes. Seleccione cada regulación para obtener más información.

**PCI DSS**

El Reglamento del Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI DSS) tiene como objetivo asegurar el procesamiento de pagos con tarjeta de crédito y otros tipos de pagos digitales. Se puede acceder a las especificaciones, documentación y recursos de PCI DSS en [_https://www.pcisecuritystandards.org_](https://www.pcisecuritystandards.org/).

**HIPAA**

La intención original de la regulación de la Ley de Portabilidad y Responsabilidad del Seguro Médico de 1996 (HIPAA) era simplificar y estandarizar los procesos administrativos de atención médica. La simplificación administrativa exige la transición de los registros y transacciones en papel a los registros y transacciones electrónicos. Se instruyó al Departamento de Salud y Servicios Humanos de los Estados Unidos (HHS, por sus siglas en inglés) a desarrollar y publicar estándares para proteger la información de salud electrónica de una persona y, al mismo tiempo, permitir el acceso y el uso adecuados de esa información por parte de los proveedores de atención médica y otras entidades. La información sobre HIPAA se puede obtener de [_https://www.cdc.gov/phlp/publications/topic/hipaa.html_](https://www.cdc.gov/phlp/publications/topic/hipaa.html).

**FedRAMP**

El gobierno federal de EE. UU. utiliza el estándar del Programa Federal de Administración de Riesgos y Autorizaciones (FedRAMP) para autorizar el uso de ofertas de servicios en la nube. Puede obtener información sobre FedRAMP en [_https://www.fedramp.gov_](https://www.fedramp.gov/).

La mayoría de estas regulaciones y especificaciones requieren que la empresa regulada contrate a empresas de pruebas de penetración de terceros para asegurarse de que cumplen con las normas y de que su postura de seguridad es aceptable. Debe estar familiarizado con estas regulaciones si está contratado para realizar pruebas de penetración para verificar el cumplimiento y la postura de seguridad general de la organización. Muchos de estos estándares proporcionan listas de verificación de los elementos que deben evaluarse durante un compromiso de prueba de penetración.

También debe familiarizarse con diferentes normativas relacionadas con la privacidad, como el **_Reglamento General de Protección de Datos (RGPD)._** El GDPR incluye reglas estrictas sobre el procesamiento de datos y la privacidad. Uno de los principales objetivos del RGPD es reforzar y unificar la protección de datos de las personas dentro de la Unión Europea (UE), al tiempo que se aborda la exportación de datos personales fuera de la UE. En resumen, el objetivo principal del GDPR es dar a los ciudadanos el control de sus datos personales. Puede obtener información adicional sobre el RGPD en [_https://gdpr-info.eu_](https://gdpr-info.eu/).

**PROPINA** Debe estar al tanto de cualquier restricción de control de exportaciones que pueda estar presente en el país donde se realizará una prueba de penetración. Por ejemplo, puede haber herramientas, software y hardware que no se puedan exportar fuera del país (por ejemplo, cierto software criptográfico o tecnologías de cifrado). Durante varios años, más de 40 países han estado negociando controles de exportación en el marco del Acuerdo de Wassenaar. El Acuerdo de Wassenaar se estableció para el control de las exportaciones de armas convencionales y bienes y tecnologías de doble uso. Las herramientas de seguridad específicas (software y hardware) pueden considerarse "armas" y pueden ser controladas y restringidas por ciertas leyes nacionales en varios países.

Para familiarizarse con las reglas relacionadas con la realización de una evaluación basada en el cumplimiento, debe familiarizarse con algunas de las normativas subyacentes clave, como las que se describen en las secciones siguientes.

Aquí tienes la línea de esa forma:


---


**Regulaciones en el Sector Financiero**

Las instituciones de servicios financieros, como los bancos, las cooperativas de crédito y las instituciones crediticias, ofrecen una variedad de soluciones e instrumentos financieros. Se podría pensar que el dinero es su activo más valioso, pero en realidad, la información de los clientes y las transacciones es el corazón de su negocio. Los activos financieros son materiales y pueden ser reemplazados. La protección de la información de los clientes es necesaria para establecer y mantener la confianza entre una institución financiera y la comunidad a la que sirve. Más específicamente, las instituciones tienen la responsabilidad de salvaguardar la privacidad de los consumidores individuales y protegerlos de daños, incluidos el fraude y el robo de identidad. A una escala más amplia, la industria es responsable de mantener la infraestructura crítica de los servicios financieros de la nación.

Los siguientes son algunos ejemplos de regulaciones aplicables al sector financiero:

- Título V, Sección 501(b) de la Ley Gramm-Leach-Bliley (GLBA) y las pautas interinstitucionales correspondientes
- El Consejo Federal de Examen de Instituciones Financieras (FFIEC)
- La Ley de Salvaguardias de la Corporación Federal de Seguros de Depósitos (FDIC) y las Cartas de Instituciones Financieras (FIL)
- La Regulación de Ciberseguridad del Departamento de Servicios Financieros de Nueva York (Reglamento de Ciberseguridad DFS de Nueva York; 23 NYCRR Parte 500)

El cumplimiento de algunas regulaciones, como NYCRR y GLBA, es obligatorio.

La GLBA define una _institución financiera_ como "cualquier institución cuyo negocio se dedique significativamente a actividades financieras como se describe en _la Sección 4(k) de la Ley de Sociedades de Cartera Bancarias_ (12 U.S.C. § 1843(k))". La GLBA se aplica a todas las organizaciones de servicios financieros, independientemente de su tamaño. Es importante entender esta definición porque estas instituciones financieras incluyen muchas empresas que tradicionalmente no se consideran instituciones financieras, incluidas las siguientes:

- Negocios de cambio de cheques
- Prestamistas de día de pago
- Corredores hipotecarios
- Prestamistas no bancarios (por ejemplo, concesionarios de automóviles que prestan servicios financieros)
- Proveedores de tecnología que ofrecen préstamos a clientes
- Instituciones educativas que brindan ayuda financiera
- Cobradores de deudas
- Proveedores de servicios de liquidación de bienes raíces
- Tasadores de bienes muebles o bienes raíces
- Minoristas que emiten tarjetas de crédito de marca
- Preparadores de impuestos profesionales
- Servicios de mensajería

La ley también se aplica a las empresas que reciben información sobre clientes de otras instituciones financieras, incluidas las agencias de informes crediticios y los operadores de cajeros automáticos.

La Comisión Federal de Comercio (FTC, por sus siglas en inglés) es responsable de hacer cumplir la GLBA en lo que respecta a las empresas financieras que no están cubiertas por las agencias bancarias federales, la Comisión de Bolsa y Valores (SEC), la Comisión de Comercio de Futuros de Productos Básicos (CFTC) y las autoridades estatales de seguros, que incluyen preparadores de impuestos, cobradores de deudas, corredores de préstamos, tasadores de bienes raíces y prestamistas hipotecarios no bancarios. La GLBA exige que las organizaciones financieras se sometan a pruebas periódicas de penetración en su infraestructura. Se puede obtener información adicional sobre la GLBA en [_https://www.ftc.gov/tips-advice/business-center/privacy-and-security/gramm-leach-bliley-act_](https://www.ftc.gov/tips-advice/business-center/privacy-and-security/gramm-leach-bliley-act).

Otro ejemplo es el Reglamento de Ciberseguridad del DFS de Nueva York. La sección 500.05 de este reglamento requiere que la entidad cubierta realice pruebas de penetración de seguridad y evaluaciones de vulnerabilidad de manera continua. El programa de ciberseguridad debe incluir supervisión y pruebas, desarrolladas de acuerdo con la evaluación de riesgos de la entidad cubierta, que está diseñada para evaluar la eficacia del programa de ciberseguridad de la entidad cubierta. El reglamento dicta que "el monitoreo y las pruebas incluirán monitoreo continuo o pruebas periódicas de penetración y evaluaciones de vulnerabilidad". La organización debe realizar una prueba anual de penetración de seguridad y una evaluación de vulnerabilidad semestral. Se puede acceder al Reglamento de Ciberseguridad del DFS de Nueva York en [_https://www.dfs.ny.gov/industry_guidance/cyber_faqs_](https://www.dfs.ny.gov/industry_guidance/cyber_faqs).


---


**Normativa en el sector sanitario**

El 20 de febrero de 2003, se publicaron las Normas de Seguridad para la Protección de la Información Médica Electrónica Protegida, conocidas como la Regla de Seguridad HIPAA. La Regla de Seguridad requiere salvaguardas técnicas y no técnicas para proteger la información de salud electrónica. El 16 de febrero de 2006 se emitió la Regla Final de Aplicación de Seguridad de HIPAA correspondiente. Desde entonces, la siguiente legislación ha modificado y ampliado el alcance y los requisitos de la Regla de Seguridad:

- La Ley de Tecnología de la Información Sanitaria para la Salud Económica y Clínica de 2009 (conocida como Ley HITECH)
- La Regla de Notificación de Infracciones de 2009
- Las Modificaciones de 2013 a las Reglas de Privacidad, Seguridad, Aplicación y Notificación de Infracciones de HIPAA bajo la Ley HITECH y la Ley de No Discriminación por Información Genética; Otras modificaciones a las reglas de HIPAA (conocidas como la Regla Ómnibus)

El Departamento de Salud y Servicios Humanos (HHS, por sus siglas en inglés) ha publicado una guía adicional de ciberseguridad para ayudar a los profesionales de la salud a defenderse contra las vulnerabilidades de seguridad, el ransomware y las amenazas modernas de ciberseguridad. Véase [_https://www.hhs.gov/hipaa/for-professionals/security/guidance/ cybersecurity/index.html_](https://www.hhs.gov/hipaa/for-professionals/security/guidance/).

La regla de seguridad de HIPAA se enfoca en salvaguardar la información de salud electrónica protegida (ePHI), que se define como información de salud identificable individualmente (IIHI) que se almacena, procesa o transmite electrónicamente. La regla de seguridad de HIPAA se aplica a las entidades cubiertas y a los socios comerciales. Las entidades cubiertas incluyen proveedores de atención médica, planes de salud, centros de compensación de atención médica y ciertos socios comerciales. Seleccione cada entidad cubierta para obtener más información.

**Proveedor de atención médica**

Un _proveedor de atención médica_ es una persona u organización que brinda servicios médicos o a pacientes, como médicos, clínicas, hospitales y servicios ambulatorios; Asesoramiento; servicios de hogares de ancianos y hospicio; servicios de farmacia; servicios de diagnóstico médico e imagenología; y equipo médico duradero.

**Plan de salud**

Un _plan de salud_ es una entidad que proporciona el pago de servicios médicos, como compañías de seguros de salud, HMO, planes de salud del gobierno o programas gubernamentales que pagan por la atención médica, como Medicare, Medicaid, programas militares y de veteranos.

**Centro de Intercambio de Información sobre el Cuidado de la Salud**

Un _centro de intercambio de información de atención médica_ es una entidad que procesa la información de salud no estándar que recibe de otra entidad en un formato estándar.

**Socios comerciales**

_Los socios comerciales_ se definieron inicialmente como personas u organizaciones que realizan ciertas funciones o actividades que involucran el uso o la divulgación de información de salud personal (PHI) en nombre de una entidad cubierta o le brindan servicios. Los servicios de socios comerciales incluyen servicios legales, actuariales, contables, de consultoría, de agregación de datos, de gestión, administrativos, de acreditación y financieros. La legislación posterior amplió la definición de socio comercial a una persona o entidad que crea, recibe, mantiene, transmite, accede o tiene el potencial de acceder a la PHI para realizar ciertas funciones o actividades en nombre de una entidad cubierta.

El Departamento de Salud y Servicios Humanos (HHS, por sus siglas en [_inglés_](https://www.hhs.gov/hipaa/for-professionals/security/guidance/index.html)) ha publicado material de orientación sobre las reglas de seguridad de HIPAA en https://www.hhs.gov/hipaa/for-professionals/security/guidance/index.html.


---


**Estándar de seguridad de datos de la industria de tarjetas de pago (PCI DSS)**

Con el fin de proteger a los titulares de tarjetas contra el uso indebido de su información personal y minimizar las pérdidas del canal de tarjetas de pago, las principales marcas de tarjetas de pago (Visa, MasterCard, Discover y American Express) formaron el Consejo de Estándares de Seguridad de la Industria de Tarjetas de Pago (PCI SSC) y desarrollaron el Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI DSS). La última versión de la norma y la documentación colateral se pueden obtener en [_https://www.pcisecuritystandards.org_](https://www.pcisecuritystandards.org/).

PCI DSS debe ser adoptado por cualquier organización que transmita, procese o almacene datos de tarjetas de pago o que afecte directa o indirectamente la seguridad de los datos del titular de la tarjeta. Cualquier organización que recurra a un tercero para gestionar los datos del titular de la tarjeta tiene la plena responsabilidad de garantizar que este tercero cumpla con PCI DSS. Las marcas de tarjetas de pago pueden imponer multas y sanciones a las organizaciones que no cumplan con los requisitos y/o pueden revocar su autorización para aceptar tarjetas de pago.

Antes de continuar con los detalles sobre cómo proteger los datos de los titulares de tarjetas y la orientación sobre cómo realizar pruebas de penetración en entornos PCI, debemos definir varios términos clave que se utilizan en este módulo y que son definidos por el PCI SSC en [_https://www.pcisecuritystandards.org/documents/PCI_DSS_Glossary_v3-2.pdf_](https://www.pcisecuritystandards.org/documents/PCI_DSS_Glossary_v3-2.pdf). Seleccione cada uno de los siguientes términos para una definición.

**Adquirente**

También se le conoce como "banco adquirente" o "institución financiera adquirente", una entidad que inicia y mantiene relaciones con comerciantes para la aceptación de tarjetas de pago.

**ASV (proveedor de escaneo aprobado)**

Una organización aprobada por el PCI SSC para llevar a cabo servicios externos de análisis de vulnerabilidades.

**Comerciante**

A los efectos de PCI DSS, una entidad que acepta tarjetas de pago que lleven los logotipos de cualquiera de los miembros de PCI SSC (American Express, Discover, MasterCard o Visa) como pago de bienes y/o servicios. Tenga en cuenta que un comerciante que acepta tarjetas de pago como pago de bienes y/o servicios también puede ser un proveedor de servicios, si los servicios vendidos dan como resultado el almacenamiento, procesamiento o transmisión de datos del titular de la tarjeta en nombre de otros comerciantes o proveedores de servicios. Por ejemplo, un ISP es un comerciante que acepta tarjetas de pago para el servicio mensual.

**PAN (número de cuenta principal)**

Un número de tarjeta de pago de hasta 19 dígitos.

**Marca de pago**

Marcas como Visa, MasterCard, Amex o Discover.

**Investigador Forense PCI (PFI)**

Una persona capacitada y certificada para investigar y contener información sobre incidentes y violaciones de seguridad cibernética que involucran datos del titular de la tarjeta.

**Asesor de Seguridad Calificado (QSA)**

Una persona capacitada y certificada para llevar a cabo evaluaciones de cumplimiento de PCI DSS.

**Proveedor de servicios**

Una entidad comercial que no es una marca de pago y que está directamente involucrada en el procesamiento, almacenamiento o transmisión de datos del titular de la tarjeta. Esto incluye empresas que brindan servicios que controlan o podrían afectar la seguridad de los datos de los titulares de tarjetas, como proveedores de servicios administrados que proporcionan firewalls administrados, detección de intrusos y otros servicios, y proveedores de alojamiento y otras entidades. Se excluyen entidades como las empresas de telecomunicaciones que solo proporcionan enlaces de comunicación sin acceso a la capa de aplicación del enlace de comunicación.

Para contrarrestar la posibilidad de pérdidas asombrosas, las marcas de tarjetas de pago exigen contractualmente que todas las organizaciones que almacenan, procesan o transmiten datos del titular de la tarjeta y/o datos de autenticación confidenciales cumplan con PCI DSS. Los requisitos de PCI DSS se aplican a todos los componentes del sistema en los que se almacenan, procesan o transmiten _datos de cuenta_.

Como se muestra en la Tabla 2-2, los datos de la cuenta consisten en datos del titular de la tarjeta, así como datos confidenciales de autenticación. Un componente del sistema es cualquier componente de red, servidor o aplicación que esté incluido o conectado al entorno de datos del titular de la tarjeta. El _entorno de datos del titular_ de la tarjeta se define como las personas, los procesos y la tecnología que manejan los datos del titular de la tarjeta o los datos de autenticación confidenciales.

**_Tabla 2-2_** _-_ _Elementos de datos de la cuenta_

![[2.1- Tabla 2-2.png]]

El PAN es el factor definitorio en la aplicabilidad de los requisitos de PCI DSS. Los requisitos de PCI DSS se aplican si el PAN se almacena, procesa o transmite. Si el PAN no se almacena, procesa o transmite, los requisitos de PCI DSS no se aplican. Si el nombre del titular de la tarjeta, el código de servicio y/o la fecha de vencimiento se almacenan, procesan o transmiten con el PAN o están presentes de otro modo en el entorno de datos del titular de la tarjeta, también deben protegerse. Según los estándares, el PAN debe almacenarse en un formato ilegible (cifrado). Es posible que los datos de autenticación confidenciales nunca se almacenen después de la autorización, incluso si están cifrados.

El algoritmo de Luhn, o fórmula de Luhn, es un algoritmo de la industria que se utiliza para validar diferentes números de identificación, incluidos números de tarjetas de crédito, números de identidad internacional de equipo móvil (IMEI), números de identificación de proveedores nacionales en los Estados Unidos, números de seguro social canadienses y más. El algoritmo de Luhn, creado por Hans Peter Luhn en 1954, es ahora de dominio público.

La mayoría de las tarjetas de crédito y muchas organizaciones gubernamentales utilizan el algoritmo de Luhn para validar los números. El algoritmo de Luhn se basa en el principio de la aritmética de módulos y las raíces digitales. Utiliza matemáticas de módulo 10.

Los siguientes son los elementos típicos en el anverso de una tarjeta de crédito:

- Microchip integrado
- CACEROLA
- Fecha de caducidad
- Nombre del titular de la tarjeta

El microchip contiene la misma información que la banda magnética. La mayoría de las personas que no son de EE. UU. Las tarjetas tienen un microchip en lugar de una banda magnética. Algunas tarjetas de EE. UU. tienen ambos para aceptación internacional.

Los siguientes son los elementos típicos en el reverso de una tarjeta de crédito:

- **Banda magnética (banda magnética):** La banda magnética contiene datos codificados necesarios para autenticar, autorizar y procesar transacciones.
- **CAV2/CID/CVC2/CVV2:** Todas estas abreviaturas son nombres de códigos de seguridad de tarjetas para las diferentes marcas de pago.

El sitio web de PCI SSC proporciona una excelente orientación sobre los requisitos para las pruebas de penetración. Véase [_https://www.pcisecuritystandards.org_](https://www.pcisecuritystandards.org/).


---


**Elementos técnicos clave en las regulaciones que debe tener en cuenta**

La mayoría de las regulaciones dictan varios elementos clave, y un probador de penetración debe prestarles atención y verificarlos durante la evaluación para asegurarse de que la organización cumpla con la normativa. Seleccione cada elemento para obtener más información.

**Aislamiento de datos**  

Las organizaciones que necesitan cumplir con PCI DSS (y otras regulaciones, para el caso) deben tener una estrategia de aislamiento de datos. También conocido como aislamiento de red o segmentación de red, el objetivo es implementar una red completamente aislada que incluya todos los sistemas involucrados en el procesamiento de tarjetas de pago.

**Gestión de contraseñas**

La mayoría de las regulaciones exigen estrategias sólidas de administración de contraseñas. Por ejemplo, las organizaciones no deben usar valores predeterminados proporcionados por el proveedor para las contraseñas del sistema y los parámetros de seguridad. Este requisito también se extiende mucho más allá de su título y entra en el ámbito de la gestión de la configuración. Además, la mayoría de estas regulaciones exigen estándares de implementación específicos, incluida la longitud de la contraseña, la complejidad de la contraseña y el tiempo de espera de la sesión, así como el uso de la autenticación multifactor.

**Gestión de claves**

Este es otro elemento importante que también es evaluado y exigido por la mayoría de las regulaciones. Una _clave_ es un valor que especifica qué parte del algoritmo se va a aplicar y en qué orden, así como qué variables se van a introducir. Al igual que con las contraseñas de autenticación, es fundamental utilizar una clave segura que no se pueda detectar y proteger la clave del acceso no autorizado. La protección de la clave se conoce generalmente como _administración de claves_. NIST SP 800-57: Recomendaciones para la administración de claves, Parte 1: General (Revisión 4) proporciona orientación general y mejores prácticas para la administración de material de claves criptográficas. Parte 2: Mejores prácticas para la organización de administración de claves proporciona orientación sobre los requisitos de planificación de políticas y seguridad para las agencias gubernamentales de EE. UU. Parte 3: Guía de administración de claves específicas de la aplicación proporciona orientación cuando se utilizan las características criptográficas de los sistemas actuales. En la Introducción a la Parte 1, el NIST describe la importancia de la gestión de claves de la siguiente manera:

La gestión adecuada de las claves criptográficas es esencial para el uso eficaz de la criptografía para la seguridad. Las llaves son análogas a la combinación de una caja fuerte. Si un adversario conoce una combinación de cajas fuertes, la caja fuerte más fuerte no proporciona seguridad contra la penetración. Del mismo modo, una mala gestión de claves puede comprometer fácilmente los algoritmos sólidos. En última instancia, la seguridad de la información protegida por la criptografía depende directamente de la solidez de las claves, la eficacia de los mecanismos y protocolos asociados a las claves y la protección que se les brinda. Todas las claves deben protegerse contra modificaciones, y las claves secretas y privadas deben protegerse contra la divulgación no autorizada. La administración de claves proporciona la base para la generación, el almacenamiento, la distribución, el uso y la destrucción seguros de claves.

La política y los estándares de administración de claves deben incluir la responsabilidad asignada para la administración de claves, la naturaleza de la información que se va a proteger, las clases de amenazas, los mecanismos de protección criptográfica que se utilizarán y los requisitos de protección para la clave y los procesos asociados.

**NOTA** El siguiente sitio web incluye la guía general de administración de claves del NIST: [_https://csrc.nist.gov/projects/key-management/key-management-guidelines_](https://csrc.nist.gov/projects/key-management/key-management-guidelines).

### **Restricciones locales**

Debe tener en cuenta las restricciones locales cuando lo contraten para realizar pruebas de penetración. Por ejemplo, es posible que viaje al extranjero a un país diferente donde puede haber limitaciones específicas del país y leyes locales que pueden restringir si puede realizar algunas tareas como probador de penetración. Las leyes de las pruebas de penetración varían de un país a otro. Algunos probadores de penetración han sido acusados e incluso arrestados por presuntamente violar la Ley de Fraude y Abuso Informático de América Sección 1030 (a) (5) (B). Siempre debes tener documentación clara de tu cliente (la entidad que te contrató) que indique que tienes permiso para realizar las pruebas. Claramente, algunas de estas limitaciones y consideraciones pueden tener un impacto directo en su contrato y declaración de trabajo (SOW).

**NOTA** Aprenderá más sobre los SOW y otros conceptos legales más adelante en este módulo.

Durante las tareas previas a la interacción, debe identificar las restricciones de prueba, incluidas las restricciones de herramientas. A menudo, se verá limitado por ciertos aspectos del negocio y la tecnología de la organización que lo contrató (incluso describiendo las herramientas que puede usar o que no está autorizado a usar durante el compromiso de prueba de penetración).

Además, a continuación se muestran algunos ejemplos de restricciones a las que puede enfrentarse durante una interacción de pruebas de penetración:

- Ciertas áreas y tecnologías que no se pueden probar debido a limitaciones operativas (por ejemplo, es posible que no pueda lanzar ataques de inyección SQL específicos, ya que al hacerlo podría dañar una base de datos de producción).
- Tecnologías que pueden ser específicas para la organización que se está probando
- Limitación de los conjuntos de habilidades
- Limitación de exploits conocidos
- Sistemas que se clasifican como fuera de ámbito debido a la criticidad o a los problemas de rendimiento conocidos

Debe comunicar claramente cualquier restricción técnica a las partes interesadas correspondientes de la organización que lo contrató antes y durante las pruebas.

También es posible que te enfrentes a diferentes requisitos del gobierno local, como los requisitos de privacidad del RGPD y la Ley de Privacidad del Consumidor de California (CCPA), que es una ley estatal centrada en la privacidad. Puede obtener información sobre la CCPA en [_https://oag.ca.gov/privacy/ccpa_](https://oag.ca.gov/privacy/ccpa).

**PROPINA** Es posible que su cliente tenga políticas corporativas específicas que deben tenerse en cuenta al realizar una prueba de penetración. En la mayoría de los casos, el cliente revelará inicialmente en su política corporativa cualquier elemento que pueda tener un impacto directo en el compromiso de las pruebas de penetración, pero siempre debe preguntar y documentar claramente si hay alguno. Algunas empresas también pueden estar sujetas a regulaciones específicas que les exigen crear políticas de pruebas de vulnerabilidad y penetración. Estas regulaciones pueden especificar sistemas restringidos y no restringidos e información sobre cómo se debe realizar una prueba de penetración de acuerdo con un estándar regulatorio.

### **Conceptos jurídicos**

****Acuerdo de nivel de servicio (SLA)****

Un SLA es una expectativa o restricción bien documentada relacionada con una o más de las medidas de rendimiento mínimo y/o máximo (como la calidad, el cronograma/marco de tiempo y el costo) del servicio de pruebas de penetración. Debe familiarizarse con los SLA que la organización que lo contrató ha proporcionado a sus clientes.

****Confidencialidad****

Debe discutir y acordar el manejo de los datos confidenciales. Por ejemplo, si puede encontrar contraseñas u otros datos confidenciales, ¿necesita revelar todas esas contraseñas o todos esos datos confidenciales? ¿Quién tendrá acceso a los datos sensibles? ¿Cuál será la forma adecuada de comunicar y manejar dichos datos? Del mismo modo, debe proteger los datos confidenciales y eliminar todos los registros, según lo acordado con su cliente. Es posible que su cliente tenga políticas de retención de datos específicas que también deba tener en cuenta. Cada vez que finalice una participación de prueba de penetración, debe eliminar cualquier registro de sus sistemas. No desea que su próximo cliente encuentre información confidencial de otro cliente en ningún sistema o comunicación.

****Declaración de trabajo (SOW)****

Un SOW es un documento que especifica las actividades que se deben realizar durante un compromiso de pruebas de penetración. Se puede utilizar para definir algunos de los siguientes elementos:

- Cronogramas del proyecto (pruebas de penetración), incluido el cronograma de entrega de informes
- El alcance del trabajo a realizar
- La ubicación de la obra (ubicación geográfica o ubicación de red)
- Requisitos técnicos y no técnicos especiales
- Multivencimiento
- Elementos varios que pueden no formar parte de la negociación principal, pero que deben enumerarse y rastrearse porque podrían plantear problemas durante el compromiso general

El SOW puede ser un documento independiente o puede formar parte de un **_acuerdo marco de servicios (MSA)._**  
 

**NOTA** El uso de los términos maestro y esclavo SOLO está en asociación con la terminología oficial utilizada en las especificaciones y estándares de la industria y de ninguna manera disminuye el compromiso de Pearson de promover la diversidad, la equidad y la inclusión y de desafiar, contrarrestar y / o combatir los prejuicios y estereotipos en la población global de los estudiantes a los que servimos.

****Contrato marco de servicios (MSA)****

Los MSA, que son muy populares hoy en día, son contratos que se pueden utilizar para negociar rápidamente el trabajo a realizar. Cuando existe un acuerdo marco, no es necesario renegociar los mismos términos cada vez que realiza un trabajo para un cliente. Los MSA son especialmente beneficiosos cuando realizas una prueba de penetración y sabes que serás recontratado de forma recurrente para realizar pruebas adicionales en otras áreas de la empresa o para verificar que la postura de seguridad de la organización ha mejorado como resultado de pruebas y correcciones previas.

****Acuerdo de confidencialidad (NDA)****

Un acuerdo de confidencialidad es un documento legal y un contrato entre usted y una organización que lo ha contratado como probador de penetración. Un acuerdo de confidencialidad especifica y define el material, el conocimiento y la información confidenciales que no deben divulgarse y que deben ser mantenidos confidenciales por ambas partes. Los acuerdos de confidencialidad se pueden clasificar como cualquiera de los siguientes:

- **Unilateral: Con** un acuerdo de confidencialidad unilateral, solo una de las partes divulga cierta información a la otra parte, y la información debe mantenerse protegida y no divulgarse. Por ejemplo, una organización que lo contrata debe incluir en un acuerdo de confidencialidad cierta información que no debe divulgar. Por supuesto, todos sus hallazgos deben mantenerse en secreto y no deben divulgarse a ninguna otra organización o individuo.
- **Bilateral**: Un acuerdo de confidencialidad bilateral también se conoce como acuerdo de confidencialidad mutuo o bidireccional. En un acuerdo de confidencialidad bilateral, ambas partes comparten información confidencial entre sí, y esta información no debe divulgarse a ninguna otra entidad.
- **Multilateral**: Este tipo de NDA involucra a tres o más partes, y al menos una de las partes divulga información confidencial que no debe divulgarse a ninguna entidad fuera del acuerdo. Los acuerdos de confidencialidad multilaterales se utilizan en el caso de que una organización externa a su cliente (socio comercial, proveedor de servicios, etc.) también participe en el compromiso de pruebas de penetración.


### **Contratos**

El contrato es uno de los documentos más importantes en un compromiso de prueba de penetración. Especifica los términos del acuerdo y cómo se le pagará, y proporciona documentación clara de los servicios que se realizarán. Un contrato debe ser muy específico, fácil de entender y sin ambigüedades. Cualquier ambigüedad probablemente conducirá a la insatisfacción y la fricción del cliente. Siempre se recomienda el asesoramiento legal (de un abogado) para cualquier contrato.

Su cliente también puede contratar a su departamento legal o a una agencia externa para revisar el contrato. Un cliente puede especificar y exigir que cualquier información recopilada o analizada durante la participación de la prueba de penetración no pueda estar disponible fuera del país donde realizó la prueba. Además, el cliente puede especificar que usted (como probador de penetración) no puede eliminar información de identificación personal (PII) que pueda estar sujeta a leyes o regulaciones específicas sin antes comprometerse a estar sujeto a esas leyes y regulaciones o sin la autorización por escrito de la empresa. Su cliente también revisará el contrato o acuerdo de pruebas de penetración para asegurarse de que no permita más riesgos de los que se pretende resolver.

Otro elemento muy importante de su contrato y de las tareas previas al compromiso es que debe obtener la firma de una autoridad de firma adecuada para su contrato. Esto incluye la autorización por escrito para el trabajo que se va a realizar. Si es necesario, también debe tener una autorización por escrito de cualquier proveedor externo o socio comercial. Esto incluiría, por ejemplo, proveedores de servicios de Internet, proveedores de servicios en la nube o cualquier otra entidad externa que pueda considerarse afectada o relacionada con la prueba de penetración que se va a realizar.

### **Descargos de responsabilidad**

Es posible que desee agregar exenciones de responsabilidad a su documentación previa a la interacción, así como en el informe final. Por ejemplo, puede especificar que ha realizado pruebas de penetración en las aplicaciones y sistemas que existían a partir de una fecha claramente indicada. Las amenazas de ciberseguridad siempre están cambiando y a diario se descubren nuevas vulnerabilidades. Ningún software, hardware o tecnología es inmune a las vulnerabilidades de seguridad, independientemente de la cantidad de pruebas de seguridad que se realicen.

También debe especificar que el informe de pruebas de penetración está destinado únicamente a proporcionar documentación y que el cliente determinará la mejor manera de remediar cualquier vulnerabilidad. Además, debe incluir un descargo de responsabilidad que indique que su informe de pruebas de penetración no puede proteger y no protege contra pérdidas personales o comerciales como resultado del uso de las aplicaciones o sistemas descritos en él.

Otra exención de responsabilidad estándar es que usted (o sus organizaciones) no proporcionan garantías, representaciones o certificaciones legales con respecto a las aplicaciones o sistemas que fueron o serán probados. Un descargo de responsabilidad podría decir que su informe de pruebas de penetración no representa ni garantiza que la aplicación probada sea adecuada para la tarea y esté libre de otras vulnerabilidades o defectos funcionales distintos de los informados. Además, es estándar incluir un descargo de responsabilidad que indique que dichos sistemas cumplen plenamente con cualquier estándar de la industria o son totalmente compatibles con cualquier sistema operativo, hardware u otra aplicación.

Por supuesto, estas son ideas generales y mejores prácticas. También puede contratar a un abogado para que le ayude a crear y personalizar sus contratos, según sea necesario.

