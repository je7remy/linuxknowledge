### **¿Qué aprendí en este módulo?**

### **Comparación y contraste de los conceptos de gobernanza, riesgo y cumplimiento**

La fase de planificación y preparación es crucial en cualquier participación en las pruebas de penetración e implica determinar el alcance del proyecto correctamente. Esto incluye comprender el público objetivo, las reglas de participación, los canales de comunicación, los recursos disponibles, el presupuesto, las limitaciones técnicas y cualquier descargo de responsabilidad. Además, es esencial estar familiarizado con varias consideraciones de cumplimiento normativo, incluidas PCI DSS, HIPAA, FedRAMP y GDPR. La mayoría de estas regulaciones requieren pruebas de penetración de terceros para verificar el cumplimiento y evaluar la postura de seguridad de la organización. Es importante estar familiarizado con estas regulaciones y sus listas de verificación para una evaluación exitosa basada en el cumplimiento.

**Regulaciones en el Sector Financiero**

El sector financiero es responsable de salvaguardar la información de los clientes y mantener la infraestructura crítica de los servicios financieros. Las regulaciones aplicables al sector financiero incluyen la Ley Gramm-Leach-Bliley (GLBA), el Consejo Federal de Examen de Instituciones Financieras (FFIEC), la Ley de Salvaguardias de la Corporación Federal de Seguros de Depósitos (FDIC) y el Reglamento de Ciberseguridad del Departamento de Servicios Financieros de Nueva York (Reglamento de Ciberseguridad del NY DFS). La GLBA se aplica a todas las organizaciones de servicios financieros, incluidas las instituciones financieras no tradicionales, como las empresas de cambio de cheques, los prestamistas de día de pago y los proveedores de tecnología que otorgan préstamos a los clientes. El cumplimiento de algunas regulaciones, como GLBA y el Reglamento de Ciberseguridad DFS de Nueva York, es obligatorio. La normativa obliga a las instituciones financieras a someterse periódicamente a pruebas de penetración y evaluaciones de vulnerabilidad en su infraestructura. La Comisión Federal de Comercio (FTC, por sus siglas en inglés) es responsable de hacer cumplir la GLBA en lo que respecta a las empresas financieras que no están cubiertas por las agencias bancarias federales, la Comisión de Bolsa y Valores (SEC), la Comisión de Comercio de Futuros de Productos Básicos (CFTC) y las autoridades estatales de seguros.

**Regulaciones en el Sector Salud**

La Regla de Seguridad de HIPAA, publicada en 2003, requiere salvaguardas técnicas y no técnicas para proteger la información de salud electrónica. Desde entonces, varias legislaciones han modificado y ampliado el alcance y los requisitos de la Regla de Seguridad, incluida la Ley HITECH, la Regla de Notificación de Infracciones y la Regla Ómnibus. La Regla de Seguridad se aplica a las entidades cubiertas y a los socios comerciales, incluidos los proveedores de atención médica, los planes de salud, las cámaras de compensación de atención médica y ciertos socios comerciales. El Departamento de Salud y Servicios Humanos (HHS, por sus siglas en inglés) ha publicado una guía adicional de ciberseguridad para ayudar a los profesionales de la salud a defenderse contra las vulnerabilidades de seguridad, el ransomware y las amenazas de ciberseguridad modernas. El HHS también ha proporcionado material de orientación para la Regla de Seguridad de HIPAA en su sitio web.

**Estándar de seguridad de datos de la industria de tarjetas de pago (PCI DSS)**

El Consejo de Estándares de Seguridad de la Industria de Tarjetas de Pago (PCI SSC) fue formado por las principales marcas de tarjetas de pago (Visa, MasterCard, Discover y American Express) para desarrollar el Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI DSS) con el fin de proteger a los titulares de tarjetas contra el uso indebido de su información personal y minimizar las pérdidas de canales de tarjetas de pago. PCI DSS debe ser adoptado por cualquier organización que transmita, procese o almacene datos de tarjetas de pago o que afecte directa o indirectamente la seguridad de los datos del titular de la tarjeta. Cualquier organización que recurra a un tercero para administrar los datos del titular de la tarjeta tiene la responsabilidad total de garantizar que este tercero cumpla con PCI DSS. El algoritmo de Luhn se utiliza para validar números de tarjetas de crédito y otros números de identificación. El sitio web de PCI SSC proporciona orientación sobre los requisitos para las pruebas de penetración.

**Elementos técnicos clave en las regulaciones que debe tener en cuenta**

La mayoría de las regulaciones exigen varios elementos técnicos clave, incluido el aislamiento de datos, la administración de contraseñas y la administración de claves. El aislamiento de datos implica la creación de una red separada para los sistemas involucrados en el procesamiento de tarjetas de pago para garantizar que estén completamente aislados. Las estrategias de administración de contraseñas deben cumplir con estándares de implementación específicos y deben incluir el uso de contraseñas seguras y autenticación multifactor. La gestión de claves también es crítica e implica la adecuada gestión y protección de las claves criptográficas para garantizar la seguridad de la información protegida por la criptografía. Las políticas y estándares para la administración de claves deben incluir las responsabilidades asignadas, la naturaleza de la información que se va a proteger, las clases de amenazas y los mecanismos de protección criptográfica que se van a utilizar.

**Consideraciones legales**

Los conceptos legales importantes que son relevantes para realizar una prueba de penetración incluyen acuerdos de nivel de servicio (SLA), acuerdos de confidencialidad, declaraciones de trabajo (SOW), acuerdos maestros de servicio (MSA) y acuerdos de confidencialidad (NDA). La sección también enfatiza la importancia de los contratos en un trabajo de pruebas de penetración y la necesidad de claridad, especificidad y asesoramiento legal. Por último, sugiere añadir exenciones de responsabilidad a la documentación previa al compromiso y a los informes finales para abordar las limitaciones de las pruebas de penetración y evitar posibles responsabilidades legales.

### **Explicar la importancia del alcance y los requisitos de la organización o del cliente**

El documento de reglas de participación describe las condiciones en las que se realizarán las pruebas e incluye detalles como el cronograma de pruebas, la ubicación de las pruebas, la ventana de tiempo de las pruebas, el método preferido de comunicación, los controles de seguridad que podrían impedir las pruebas, las direcciones IP o las redes desde las que se originarán las pruebas y los tipos de pruebas permitidas o no permitidas. Los diagramas de Gantt y las estructuras de desglose del trabajo se pueden utilizar para documentar el cronograma de las pruebas.

El alcance es uno de los elementos más importantes de las tareas previas al compromiso e incluye la documentación de los sistemas, redes y aplicaciones que se van a probar, así como cualquier requisito específico necesario para la prueba. Hay diferentes tipos de documentación de API y recursos de soporte adicionales que pueden estar disponibles para el probador de penetración. El alcance de la interacción debe incluir la ubicación física, los nombres de dominio completos de DNS y la identificación de objetivos externos frente a internos.

Es importante validar el alcance de un compromiso de prueba de penetración y comprender el público objetivo del informe. El tema proporciona una lista de preguntas que pueden ayudar a descubrir diferentes características del público objetivo, como su necesidad del informe, su posición dentro de la organización y su responsabilidad y autoridad para tomar decisiones basadas en los hallazgos. También es importante mantener abiertas las líneas de comunicación con los clientes y las partes interesadas. El tema proporciona una lista de preguntas que se deben tener en cuenta al comunicarse con las partes interesadas. Además, puede haber preguntas sobre el presupuesto y el retorno de la inversión que pueden surgir tanto del lado del cliente como del probador en las pruebas de penetración. Asegúrese de que el cliente entienda que las pruebas de penetración son una evaluación puntual y que las estrategias de mitigación, el análisis de impacto y los plazos de corrección claros y alcanzables deben discutirse con todas las partes interesadas.

Las pruebas de entorno desconocido implican proporcionar al evaluador solo información limitada, como nombres de dominio y direcciones IP, para simular la perspectiva de un atacante externo. El evaluador no tiene conocimiento previo de la organización y la infraestructura del objetivo, y es posible que el personal de soporte de red del objetivo no esté informado sobre la prueba. Esto permite una evaluación realista de la postura de seguridad.

Las pruebas de entorno conocido, por otro lado, proporcionan al evaluador una cantidad significativa de información sobre la organización y su infraestructura, incluidos diagramas de red, direcciones IP, configuraciones y credenciales de usuario. En algunos casos, el evaluador también puede recibir el código fuente de la aplicación de destino. El objetivo de este tipo de pruebas es identificar tantos agujeros de seguridad como sea posible.

El alcance de la prueba y la cantidad de tiempo y dinero invertidos en ella dependen de varios factores, como las preocupaciones específicas de la empresa y el nivel de sofisticación y capacidades de los posibles atacantes. Si bien las pruebas de entorno conocido pueden ser útiles para identificar vulnerabilidades específicas, las pruebas de entorno desconocido suelen ser una buena opción porque proporcionan una evaluación más realista de la posición de seguridad de la red.

### **Demostrar una mentalidad ética de hacking manteniendo la profesionalidad y la integridad**

En este tema se analizan varias consideraciones clave para que los hackers éticos o los probadores de penetración demuestren profesionalismo e integridad. Estos incluyen someterse a verificaciones de antecedentes, adherirse al alcance específico de la participación, identificar actividades delictivas y denunciarlas de inmediato, limitar el uso de herramientas, respetar la invasividad basada en el alcance, mantener la confidencialidad de los datos y la información, y comprender los riesgos involucrados. Además, el tema enfatiza la importancia de la gestión de riesgos y la tolerancia al riesgo en los programas de gobernanza de ciberseguridad. Todas las partes involucradas deben tomar decisiones informadas y gestionar el riesgo teniendo en cuenta los objetivos de la organización.

### **Preguntas de reflexión**

En este módulo se explican los trámites necesarios para establecer una relación contractual entre una empresa de servicios de ensayos de penetración y sus clientes. También se discutió el profesionalismo y la ética de un pentester.

¿Por qué se dedica tanto tiempo y esfuerzo a establecer la relación cliente-cliente antes de que se firme un contrato y se reciba el pago? ¿Por qué las empresas de pruebas de penetración deben tener tanto cuidado con los antecedentes y la ética de sus empleados?

### **Cuestionario - Planificación y alcance de una evaluación de pruebas de penetración**


---

**Pregunta 1**  
Se contrata a un contratista para revisar y realizar evaluaciones de vulnerabilidad de ciberseguridad para una clínica de salud local. ¿Qué regulación del gobierno de los EE. UU. debe comprender el contratista antes de que pueda comenzar?

- **Respuesta**: **HIPAA**

---

**Pregunta 2**  
Una oficina del Servicio de Impuestos Internos (IRS) en Nueva York está considerando trasladar algunos servicios a una plataforma de computación en la nube. ¿Qué regulación del gobierno de los EE. UU. debe seguir la oficina en el proceso?

- **Respuesta**: **FedRAMP**

---

**Pregunta 3**  
Una universidad estadounidense en California planea ofrecer cursos en línea a estudiantes de universidades asociadas en Francia y Alemania. ¿Qué normativa debe seguir la universidad cuando se ofrecen esos cursos?

- **Respuesta**: **RGPD**

---

**Pregunta 4**  
¿Qué agencia gubernamental de los EE. UU. es responsable de hacer cumplir la Regla de Privacidad de la Información Financiera del Consumidor de la Ley Gramm-Leach-Bliley (GLB Act)?

- **Respuesta**: **Federal Trade Commission (FTC)**

---

**Pregunta 5**  
En el sector de la salud, ¿qué término define a una entidad que procesa información de salud no estándar que recibe de otra entidad y la convierte en un formato estándar?

- **Respuesta**: **Healthcare clearinghouse**

---

**Pregunta 6**  
En el sector de la salud, ¿qué término se utiliza para definir a una entidad que proporciona el pago de servicios médicos?

- **Respuesta**: **Health plan**

---

**Pregunta 7**  
En el comercio electrónico, ¿qué determina la aplicación de los requisitos del Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI DSS)?

- **Respuesta**: **Primary Account Number (PAN)** - Los requisitos de PCI DSS se aplican si el PAN se almacena, procesa o transmite.

---

**Pregunta 8**  
¿Cuáles son dos ejemplos de datos de autenticación sensibles asociados con una tarjeta de pago que requieren el cumplimiento del Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI DSS)? *(Elige dos)*

- **Respuestas**:
  - **CAV2/CVC2/CVV2/CID**
  - **Datos completos de la banda magnética o datos equivalentes en un chip**

---

**Pregunta 9**  
Empareja las partes de la Recomendación para la administración de claves en el NIST SP 800-57 con la descripción.

- **Parte 1: Generalidades**  
  - Proporciona orientación general y prácticas recomendadas para la administración de material de clave criptográfica.

- **Parte 2: Mejores Prácticas para la Organización de Gestión Clave**  
  - Proporciona orientación sobre los requisitos de planificación de políticas y seguridad para las agencias gubernamentales de EE. UU.

- **Parte 3: Guía de administración de claves específicas de la aplicación**  
  - Proporciona orientación al utilizar las características criptográficas de los sistemas actuales.

---

**Pregunta 10**  
Un empleado de una empresa de consultoría de ciberseguridad en los EE. UU. es asignado para ayudar a evaluar las vulnerabilidades del sistema y el funcionamiento de varias instituciones financieras en Europa. La tarea incluye pruebas de penetración para el cumplimiento. ¿Cuál es un elemento clave que debe tener el empleado antes de comenzar el encargo?

- **Respuesta**: **Documentación de permiso para la realización de las pruebas por parte de las instituciones clientes**

---

**Pregunta 11**  
Una empresa contrata a un profesional de la ciberseguridad para que realice pruebas de penetración con el fin de evaluar el cumplimiento de la normativa gubernamental. ¿Qué documento legal se debe proporcionar al profesional de la ciberseguridad que especifique las expectativas y limitaciones, incluida la calidad del trabajo, los plazos y el costo?

- **Respuesta**: **Acuerdo de nivel de servicio (SLA)** - Es un documento detallado que define las expectativas mínimas y máximas de rendimiento, como calidad, plazos y costos de los servicios de pruebas de penetración.

---

**Pregunta 12**  
Una empresa contrata a un profesional de ciberseguridad para realizar pruebas de penetración para evaluar el cumplimiento de la normativa gubernamental. ¿Qué documento se le proporcionará al profesional de ciberseguridad que especifique una lista detallada y descriptiva de todos los entregables, incluido el alcance del proyecto, el cronograma y el calendario de entrega de informes, la ubicación del trabajo y el calendario de pagos?

- **Respuesta**: **Declaración de trabajo (SOW)**

---

**Pregunta 13**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración para evaluar el cumplimiento de la normativa gubernamental. La empresa desea que el consultor divulgue información solo a ellos y a nadie más. ¿Qué tipo de acuerdo de confidencialidad (NDA) debe presentar al consultor?

- **Respuesta**: **NDA unilateral**

---

**Pregunta 14**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración para cumplir con la normativa gubernamental. ¿Qué documento debe recibir el consultor que especifique el acuerdo entre el consultor y la empresa para las pruebas de penetración?

- **Respuesta**: **Contrato** - Es uno de los documentos más importantes en un compromiso de pruebas de penetración. Especifica los términos del acuerdo, la forma de pago y proporciona una documentación clara de los servicios que se realizarán.

---

**Pregunta 15**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración. El consultor está preparando el informe final después de completar las pruebas. ¿En qué sección del informe debe el consultor cubrir las limitaciones del trabajo realizado, como las fechas específicas en las que se realizaron las pruebas y que los hallazgos no garantizan la cobertura de todas las vulnerabilidades?

- **Respuesta**: **Disclaimers**

---

**Pregunta 16**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración y revisar los documentos de reglas de compromiso. ¿Cuáles son tres ejemplos típicos de elementos que se encuentran en el documento de reglas de compromiso? *(Selecciona tres)*

- **Respuestas**:
  - **Cronograma de pruebas**
  - **Ubicación de las pruebas**
  - **Método de comunicación preferido**

---

**Pregunta 17**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración y revisar los documentos de reglas de compromiso. El consultor nota que un elemento especifica que las pruebas deben realizarse solo en aplicaciones web en los sitios www1.company.com y www2.company.com, sin ataques de ingeniería social y sin ataques de scripts entre sitios. ¿Qué elemento del documento se utiliza para esta especificación?

- **Respuesta**: **Tipos de pruebas permitidas o no permitidas**

---

**Pregunta 18**  
Una empresa contrata a un consultor de ciberseguridad para evaluar aplicaciones utilizando diferentes API. ¿Qué documento debe proporcionar la empresa al consultor sobre un lenguaje basado en XML utilizado para documentar la funcionalidad de un servicio web?

- **Respuesta**: **Documento WSDL (Web Services Description Language)**

---

**Pregunta 19**  
Una empresa contrata a un consultor de ciberseguridad para evaluar aplicaciones utilizando diferentes API. ¿Qué documento debe proporcionar la empresa al consultor sobre un lenguaje de consulta para API y un lenguaje para ejecutar consultas en tiempo real?

- **Respuesta**: **Documentación de GraphQL**

---

**Pregunta 20**  
Una empresa contrata a un consultor de ciberseguridad para evaluar la vulnerabilidad en dispositivos críticos de aplicaciones web, como servidores web y de bases de datos. ¿Qué documento debe proporcionar la empresa para ayudar al consultor a documentar y definir qué sistemas están en la prueba?

- **Respuesta**: **Diagrama arquitectónico del sistema y red**

---

**Pregunta 21**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración. ¿Qué puede causar un alcance no definido (scope creep) del compromiso?

- **Respuesta**: **Identificación ineficaz de los elementos técnicos y no técnicos requeridos para la prueba de penetración**

---

**Pregunta 22**  
¿Qué paso debe tomar primero el consultor de ciberseguridad para validar el alcance del compromiso de pruebas de penetración?

- **Respuesta**: **Cuestionar al cliente y revisar los contratos** - El consultor debe entender la audiencia objetivo del informe de pruebas de penetración, así como las áreas, unidades de negocio u otras entidades que el compromiso evaluará.

---

**Pregunta 23**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración. El consultor está trabajando con la empresa para establecer procedimientos de comunicación. ¿Qué dos protocolos deberían considerarse para intercambiar correos electrónicos de forma segura? *(Elige dos)*

- **Respuestas**:
  - **PGP**
  - **S/MIME**

---

**Pregunta 24**  
Una empresa contrata a un consultor de ciberseguridad para realizar pruebas de penetración. El consultor está discutiendo con la empresa sobre la estrategia de pruebas de penetración. ¿Qué afirmación describe el término "pruebas de entorno desconocido"?

- **Respuesta**: **Este tipo de pruebas se realiza cuando se le proporciona al consultor información muy limitada sobre los sistemas y redes objetivo.**

---

**Pregunta 25**

  
Una empresa está colaborando con un consultor de ciberseguridad para realizar pruebas de penetración. El consultor de seguridad utiliza inteligencia de código abierto para investigar los sistemas de la empresa. ¿Qué término se utiliza para describir la recopilación de información de inteligencia de código abierto?

- **Respuesta**: **OSINT (Open Source Intelligence)**

--- 
