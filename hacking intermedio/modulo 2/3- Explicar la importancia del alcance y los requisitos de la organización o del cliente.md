### **Descripción general**

Como sabes, la ciberseguridad es un tema importante en los negocios y la sociedad. Las regulaciones y los marcos de cumplimiento han evolucionado para guiar a las organizaciones en las medidas necesarias para minimizar el riesgo de pérdidas debido a los ataques cibernéticos. Algunas medidas son solo pautas, pero otras son legalmente obligatorias. En algunos casos, se requieren evaluaciones de seguridad independientes para que las organizaciones puedan ser aprobadas para manejar información protegida o transacciones financieras.

Gran parte del trabajo que hacemos de Un **Especialista en Cumplimiento en Ciberseguridad** consiste en realizar auditorías de seguridad, pruebas de penetración y otras actividades que se requieren para certificar que las organizaciones cumplen con diferentes regulaciones. Es importante que esté familiarizado con los diferentes marcos de cumplimiento que son relevantes para nuestros diferentes clientes y que comprenda los tipos de actividades que se nos pueden pedir que realicemos para ayudar a nuestros clientes a mantener sus certificaciones de cumplimiento.

En el Módulo 1, "Introducción al Hacking Ético y las Pruebas de Penetración", aprendiste sobre la importancia de un permiso escrito para atacar y los diferentes estándares y metodologías de pruebas de penetración, como el Estándar de Ejecución de Pruebas de Penetración (PTES), el Manual de Metodología de Pruebas de Seguridad de Código Abierto (OSSTMM), el Marco de Evaluación de Seguridad de Sistemas de Información (ISSAF) y diferentes documentos de orientación del Instituto Nacional de Estándares y Tecnología (NIST) y el Open Proyecto de Seguridad de Aplicaciones Web (OWASP). También aprendió sobre las diferentes consideraciones del entorno (para entornos de red, aplicaciones y nube). En esta sección, aprenderá sobre las reglas de interacción, la lista de destino/activos dentro del alcance y cómo validar el alcance de una interacción.

### **Reglas de enfrentamiento**

El **documento de reglas de enfrentamiento** especifica las condiciones bajo las cuales se llevará a cabo el compromiso de pruebas de penetración de seguridad. Es necesario documentar y acordar estas condiciones de la regla de compromiso con el cliente o con una parte interesada adecuada. En la Tabla 2-3 se enumeran algunos ejemplos de los elementos que normalmente se incluyen en un documento de reglas de enfrentamiento.

**_Tabla 2-3_** _-_ _Ejemplos de elementos de un documento de reglas de enfrentamiento_

![[3.1- Tabla 2-3.png]]

Los diagramas de Gantt y las estructuras de desglose del trabajo (WBS) se pueden utilizar como herramientas para demostrar y documentar la línea de tiempo. La Figura 2-1 muestra un ejemplo de un diagrama de Gantt básico.

**_Figura 2-1_** _- Ejemplo de un diagrama de Gantt_

![[3.2- Figura 2-1.png]]

**PROPINA** En el Módulo 1, aprendió que otro documento que se usa a menudo y que es importante para cualquier participación en pruebas de penetración es el documento de permiso para probar (o permiso para atacar). Puede ser un documento independiente o puede estar agrupado con otros documentos, como el contrato principal.

### **Lista de objetivos y activos dentro del ámbito**

El alcance es uno de los elementos más importantes de las tareas previas a la participación en cualquier participación en pruebas de penetración. No solo tiene que identificar y documentar cuidadosamente todos los sistemas, aplicaciones y redes que se probarán, sino también determinar los requisitos específicos y las calificaciones necesarias para realizar la prueba. Cuanto más amplio sea el alcance de la participación en las pruebas de penetración, más habilidades y requisitos se necesitarán.

El alcance y la documentación relacionada deben incluir información sobre los tipos de redes que se probarán. En la Tabla 2-3, vio algunos ejemplos de los rangos de direcciones IP de los dispositivos y activos que el probador de penetración puede evaluar. Además de los rangos de IP, debe documentar las redes inalámbricas o los identificadores de conjuntos de servicios (SSID) que pueda o no probar.

También se le puede contratar para realizar una evaluación de aplicaciones modernas utilizando diferentes interfaces de programación de aplicaciones (API). Seleccione cada una de las siguientes opciones para obtener más información sobre los tipos de documentación de API que su cliente puede tener disponible.

***SOAP***

Archivos de proyecto Simple Object Access Protocol (SOAP): SOAP es un estándar de API que se basa en XML y esquemas relacionados. Las especificaciones basadas en XML se rigen por documentos de definición de esquema XML (XSD). Tener una buena referencia de lo que soporta una API específica puede ser muy beneficioso para un probador de penetración y acelerará las pruebas. Se puede acceder a la especificación SOAP en [_https://www.w3.org/TR/soap_](https://www.w3.org/TR/soap).

**Swagger***

La documentación de Swagger (OpenAPI) es un marco moderno de documentación y desarrollo de API que ahora es la base de la especificación OpenAPI (OAS). Estos documentos se utilizan en las API de transferencia de estado representacional (REST). REST es un estilo de arquitectura de software diseñado para guiar el desarrollo de la arquitectura de los servicios web (incluidas las API). Las API REST, o "RESTful", son los tipos más comunes de API que se utilizan en la actualidad. Los documentos de Swagger pueden ser extremadamente beneficiosos al probar las API. Se puede obtener información adicional sobre Swagger en [_https://swagger.io_](https://swagger.io/). La OEA está disponible en [_https://github.com/OAI/OpenAPI-Specification_](https://github.com/OAI/OpenAPI-Specification).

***WSDL***

El lenguaje de descripción de servicios web (WSDL) es un lenguaje basado en XML que se utiliza para documentar la funcionalidad de un servicio web. Se puede acceder a la especificación WSDL en [_https://www.w3.org/TR/wsdl20-primer_](https://www.w3.org/TR/wsdl20-primer).

***GraphQL***

GraphQL es un lenguaje de consulta para APIs. También es un tiempo de ejecución del lado del servidor para ejecutar consultas mediante un sistema de tipos definido para los datos. Se puede acceder a información técnica adicional sobre GraphQL en [_https://graphql.org/learn_](https://graphql.org/learn).

***WADL***

Web Application Description Language (WADL) es un lenguaje basado en XML para describir aplicaciones web. La especificación WADL se puede obtener de [_https://www.w3.org/Submission/wadl_](https://www.w3.org/Submission/wadl).


***

Los siguientes son algunos recursos de soporte adicionales que puede obtener de la organización para realizar la prueba de penetración.

***


***Kit de desarrollo de software (SDK) para aplicaciones específicas***

Un SDK, o devkit, es una colección de herramientas de desarrollo de software que se pueden usar para interactuar e implementar un marco de software, un sistema operativo o una plataforma de hardware. Los SDK también pueden ayudar a los probadores de penetración a comprender ciertas aplicaciones especializadas y plataformas de hardware dentro de la organización que se está probando.

***Acceso al código fuente***

Algunas organizaciones pueden permitirle obtener acceso al código fuente de las aplicaciones que se van a probar.

***Ejemplos de solicitudes de aplicación***

En la mayoría de los casos, podrá revelar el contexto mediante el uso de herramientas de prueba de aplicaciones web, como proxies como Burp Suite y OWASP Zed Attack Proxy (ZAP). Aprenderá más sobre estas herramientas en el Módulo 6, "Explotación de vulnerabilidades basadas en aplicaciones" y en el Módulo 10, "Herramientas y análisis de código".

***Diagramas arquitectónicos de sistemas y redes***

Estos documentos pueden ser muy beneficiosos para los probadores de penetración, y se pueden utilizar para documentar y definir qué sistemas están dentro del alcance durante las pruebas.


***


Es muy importante documentar la ubicación física donde se realizarán las pruebas de penetración, así como los nombres de dominio completos (FQDN) del Sistema de nombres de dominio (DNS) de las aplicaciones y activos permitidos (incluidos los subdominios). También debe estar de acuerdo y comprender si se le permitirá demostrar cómo un atacante externo podría poner en peligro sus sistemas o cómo una persona interna podría poner en peligro los activos internos. Esta identificación y alcance de objetivos externos e internos debe estar claramente documentada.

En el Módulo 1, aprendió que hay varias consideraciones ambientales, como las aplicaciones alojadas en una nube pública. Es muy importante comprender el concepto de aplicaciones alojadas de origen frente a las de terceros. Hoy en día, las aplicaciones no solo se pueden alojar en una nube pública (como AWS, GCP o Azure), sino también en nubes privadas e híbridas. Como probador de penetración, debe familiarizarse con las restricciones y limitaciones dictadas por cualquier proveedor de alojamiento o nube de terceros.

_El scope creep_ es un término de gestión de proyectos que se refiere al crecimiento descontrolado del alcance de un proyecto. También se le conoce a menudo como _síndrome del fregadero de la cocina_, _arrastre de requisitos_ y _deslizamiento de funciones_. La corrupción del alcance puede dejarlo fuera del negocio. Muchas empresas de seguridad sufren de corrupción del alcance y no tienen éxito porque no tienen idea de cómo identificar cuándo comienza el problema o cómo reaccionar ante él.

Cuando hay una mala gestión del cambio en el compromiso de las pruebas de penetración.  

Cuando exista una identificación ineficaz de los elementos técnicos y no técnicos que se requerirán para la prueba de penetración.  

Cuando hay una mala comunicación entre las partes interesadas, incluido su cliente y su propio equipo.

La corrupción del alcance no siempre comienza como una mala situación. Por ejemplo, un cliente que está satisfecho con el trabajo que está realizando en su compromiso podría pedirle que realice pruebas adicionales o trabajo técnico. La gestión del cambio y la comunicación clara son cruciales para evitar una situación muy incómoda y mala.

Si inicialmente se comprometió con su cliente después de una solicitud de propuesta (RFP) y se necesita trabajo adicional que no formaba parte de la RFP o de su SOW inicial, debe solicitar que se firme y acuerde una nueva SOW.