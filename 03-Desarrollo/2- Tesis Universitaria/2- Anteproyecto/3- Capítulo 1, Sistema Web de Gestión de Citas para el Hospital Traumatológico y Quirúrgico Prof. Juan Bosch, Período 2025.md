
#### 1.1 Introducción

El Hospital Traumatológico y Quirúrgico Prof. Juan Bosch, ubicado en El Pino, La Vega, República Dominicana, es un pilar esencial en la región para la atención de pacientes con necesidades traumatológicas y quirúrgicas. Este centro enfrenta una alta demanda de servicios especializados, lo que requiere una gestión eficiente para garantizar atención médica oportuna y de calidad. Sin embargo, el proceso actual de gestión de citas depende de métodos manuales, como registros en papel, llamadas telefónicas y coordinación verbal entre el personal. Esta práctica genera ineficiencias operativas significativas, incluyendo demoras prolongadas para los pacientes, errores en la asignación de turnos y duplicación de esfuerzos administrativos. Además, la falta de un sistema centralizado dificulta la coordinación entre secretarias y médicos, afectando la planificación diaria y la experiencia del paciente. Para resolver estas problemáticas, se propone el desarrollo de un Sistema Web de Gestión de Citas, diseñado para optimizar la programación médica mediante una plataforma accesible a través de la intranet del hospital. Este sistema será utilizado exclusivamente por personal autorizado, como secretarias y médicos, permitiendo agendar, consultar, modificar y cancelar citas en tiempo real. Su implementación busca mejorar la organización de las agendas, reducir errores y optimizar el flujo de atención, elevando así la calidad del servicio ofrecido a la comunidad.


#### 1.2 Descripción de la Propuesta

El proyecto propone el desarrollo de un Sistema Web de Gestión de Citas para el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch, con el objetivo de modernizar y optimizar la programación de consultas médicas. Esta plataforma, accesible únicamente a través de la intranet del hospital, será utilizada por secretarias y médicos para gestionar citas de manera eficiente. Las secretarias podrán registrar, modificar y cancelar citas en tiempo real, asignando turnos según la disponibilidad médica actualizada, mientras que los médicos consultarán sus agendas y registrarán notas de las consultas atendidas. El sistema incluirá tres módulos principales: uno de citas, para la gestión de turnos; otro de consulta, para el seguimiento médico; y un módulo transversal, con herramientas como reportes y una interfaz intuitiva. Además, contará con un sistema de autenticación basado en roles para garantizar la seguridad de los datos. Esta solución busca eliminar las ineficiencias de los métodos manuales, reducir errores administrativos y mejorar la coordinación entre el personal. Al centralizar la información y agilizar las tareas, el sistema optimizará los recursos hospitalarios, disminuirá los tiempos de espera y elevará la calidad de la atención, beneficiando tanto al personal como a los pacientes en un contexto de alta demanda de servicios especializados.

#### 1.3 Justificación

La implementación de un Sistema Web de Gestión de Citas en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch se justifica por la necesidad de superar las limitaciones de los procesos manuales actuales. Este proyecto mejorará la eficiencia operativa al reducir significativamente los tiempos de espera y los errores administrativos, como duplicaciones o asignaciones incorrectas de citas. Al ofrecer una plataforma centralizada, facilitará la coordinación entre secretarias y médicos, asegurando agendas actualizadas y accesibles en tiempo real. Esto permitirá una planificación más efectiva de los recursos del hospital, optimizando el tiempo del personal médico y administrativo. Además, el sistema garantizará un servicio más ágil y seguro, ya que los médicos podrán registrar información de las consultas digitalmente, y la autenticación por roles protegerá la confidencialidad de los datos sensibles. La modernización de este proceso no solo incrementará la productividad interna, sino que también mejorará la experiencia del paciente, al ofrecer un acceso más rápido y confiable a las citas. En un entorno donde la tecnología es esencial para la gestión sanitaria, este proyecto representa una inversión estratégica que fortalecerá la capacidad del hospital para cumplir con su misión de brindar atención de calidad a la comunidad de La Vega y sus alrededores.

#### 1.4 Motivación

El desarrollo de este Sistema Web de Gestión de Citas está motivado por la necesidad de modernizar los procesos del Hospital Traumatológico y Quirúrgico Prof. Juan Bosch, aprovechando los avances tecnológicos que han transformado el sector salud a nivel global. Actualmente, la gestión manual de citas genera demoras, errores administrativos y una carga operativa excesiva para el personal, lo que compromete la eficiencia y la calidad del servicio. Esta situación inspiró la creación de una solución digital que optimice la programación de consultas, mejore la coordinación entre secretarias y médicos, y agilice la atención al paciente. La motivación principal radica en ofrecer una herramienta que reduzca los tiempos de espera, elimine ineficiencias y brinde un mejor servicio a los pacientes y al personal médico. Este proyecto no solo busca resolver problemas operativos inmediatos, sino también establecer un precedente para la adopción de tecnologías en el hospital, alineándose con las tendencias de salud digital. Al implementar esta plataforma, se espera elevar la satisfacción de los usuarios y demostrar cómo la innovación puede impactar positivamente en la atención sanitaria, contribuyendo al bienestar de la comunidad atendida por este centro especializado.

#### 1.5 Marco Teórico

##### 1.5.1 Antecedentes

La digitalización de procesos hospitalarios es una tendencia global. Centros de salud han implementado sistemas de gestión de citas, como Epic o soluciones personalizadas, logrando mejoras en eficiencia y satisfacción del paciente. Estos antecedentes servirán como referencia para adaptar buenas prácticas al contexto del hospital.

##### 1.5.2 Conceptos Clave

El proyecto se basa en 10 términos clave: 

1.5.3) Gestión de citas médicas: 
	
	Asignación y administración de horarios.
	
1.5.4) Sistema web: 
	
	Aplicación en navegador.
	
1.5.5) Intranet: 
	
	Red privada segura.
	
1.5.6) Salud digital: 
	
	Tecnología en servicios sanitarios.
	
1.5.7) Base de datos: 
	
	Almacenamiento estructurado (SQLite).
	 
1.5.8) Interfaz de usuario: 
	
	Diseño visual intuitivo.
	
1.5.9) Autenticación por roles: 
	
	Seguridad por permisos.
	
1.5.10) Reportes automáticos: 
	
	Estadísticas operativas.
	
1.5.11) Disponibilidad médica: 
	
	Horarios actualizados.
	 
1.5.12) Optimización de procesos: 
	
	Mejora operativa.

#### 1.6 Glosario de Términos

1.6.1 **Agenda**  

  Horario de trabajo de un médico que incluye las citas programadas con los pacientes, accesible y gestionable a través del sistema web para optimizar la planificación.

1.6.2 **Base de Datos**  

  Colección estructurada de datos almacenados electrónicamente. En este proyecto, se utiliza *SQLite*, un sistema de gestión de bases de datos relacional ligero y embebido, para almacenar información de citas, pacientes y médicos.

1.6.3 **Cita Médica**  

  Acuerdo entre un paciente y un médico para reunirse en un momento específico para una consulta o procedimiento, gestionado de manera centralizada por el sistema web.

1.6.4 **Despliegue**  

  Proceso de instalación y configuración del sistema web en el entorno de producción, específicamente en la intranet del Hospital Traumatológico y Quirúrgico Prof. Juan Bosch.

1.6.5 **Gestión de Citas**  

  Proceso administrativo y logístico que incluye programar, modificar, cancelar y consultar citas médicas, con el objetivo de optimizar la atención y reducir errores operativos.

1.6.6 **Interfaz de Usuario (UI)**  

  Medio visual a través del cual los usuarios (secretarias y médicos) interactúan con el sistema web. Diseñada para ser intuitiva, clara y eficiente, facilitando tareas como la programación y consulta de citas.

1.6.7 **Intranet**  

  Red informática privada y segura del hospital, utilizada para alojar el sistema web y restringir el acceso exclusivamente al personal autorizado (secretarias y médicos).

1.6.8 **Metodología Ágil**  

  Enfoque de desarrollo de software basado en flexibilidad, colaboración y entregas iterativas. En este proyecto, se utiliza *Scrum* para organizar el trabajo en ciclos cortos y adaptarse a los requerimientos cambiantes.

1.6.9 **Módulo**  

  Componente del sistema web que encapsula una funcionalidad específica, como la gestión de citas, la consulta de agendas o la generación de reportes.

1.6.10 **Paciente**  

  Persona que recibe atención médica en el hospital y cuya información se registra en el sistema para programar citas y dar seguimiento a su atención.

1.6.11 **Reporte**  

  Documento generado automáticamente por el sistema que presenta información resumida sobre citas programadas, canceladas o atendidas, útil para la planificación y toma de decisiones administrativas.

1.6.12 **Rol**  

  Función asignada a un usuario dentro del sistema (por ejemplo, secretaria o médico), que determina sus permisos y el nivel de acceso a las funcionalidades y datos.

1.6.13 **Scrum**  

  Framework de metodología ágil utilizado en el desarrollo del sistema, basado en ciclos de trabajo cortos (*sprints*), con reuniones regulares para planificación, revisión y mejora continua.

1.6.14 **Secretaria**  

  Personal administrativo encargado de programar, modificar y cancelar citas médicas a través del sistema web, así como de gestionar la información de pacientes y generar reportes.

1.6.15 **Sistema Web**  

  Aplicación informática accesible mediante un navegador web, diseñada para la gestión de citas y operativa exclusivamente dentro de la intranet del hospital.

1.6.16 **Sprint**  

  Ciclo de trabajo en la metodología *Scrum*, con una duración de 2 a 4 semanas, durante el cual se desarrolla y entrega un conjunto específico de funcionalidades del sistema.

1.6.17 **SQLite**  

  Sistema de gestión de bases de datos relacional ligero y embebido, seleccionado para este proyecto por su simplicidad y adecuación a una aplicación con concurrencia moderada.

1.6.18 **Stakeholder**  

  Persona o grupo con interés en el proyecto, como la dirección del hospital, secretarias, médicos o el equipo de desarrollo, cuyos aportes y necesidades guían la implementación.

1.6.19 **Usabilidad**  

  Medida de la facilidad con la que los usuarios pueden interactuar con el sistema para realizar sus tareas de manera eficiente, minimizando errores y maximizando la satisfacción.

#### 1.7 Objetivos

##### 1.7.1 Objetivo General

**Desarrollar** un sistema web de gestión de citas médicas para el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch, dirigido exclusivamente a secretarias y médicos, que incluya tres módulos principales: citas, consulta y transversal. El módulo de citas permitirá a las secretarias programar, editar y cancelar citas de manera eficiente, asignando turnos según la disponibilidad de los médicos y vinculando la información del paciente. El módulo de consulta facilitará a los médicos consultar y gestionar sus agendas en tiempo real, con funciones de búsqueda de citas y recepción de notificaciones. El módulo transversal proporcionará una interfaz centralizada y generará reportes automáticos, optimizando la organización operativa del hospital y reduciendo los tiempos de espera de los pacientes.

#### 1.7.2 Objetivos Específicos

1. **Proveer** a las secretarias un módulo de citas que permita agendar turnos con mayor facilidad, asignando horarios según la disponibilidad actualizada de los médicos y vinculando la información del paciente de manera rápida y precisa, con validaciones para evitar conflictos de horarios.
2. **Facilitar** a los médicos un módulo de consulta con una interfaz intuitiva que permita consultar sus agendas actualizadas en tiempo real, buscar citas por fecha o paciente, revisar historiales básicos y recibir notificaciones rápidas sobre cambios o cancelaciones.
3. **Optimizar** para las secretarias la búsqueda y consulta de datos de pacientes y citas a través del módulo transversal, proporcionando acceso inmediato a la información relevante, reduciendo errores administrativos y agilizando el proceso de atención.
4. **Generar**, mediante el módulo transversal, reportes automáticos diarios y semanales para las secretarias, con información sobre citas programadas, canceladas y atendidas, facilitando el seguimiento y la planificación administrativa.


#### 1.8 Importancia del Problema

La gestión manual de citas en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch genera problemas críticos que afectan a pacientes, personal y la institución. Este sistema, basado en papel y coordinación verbal, provoca **ineficiencias operativas** como largas esperas, errores en la asignación de turnos y falta de coordinación entre el personal. Para los pacientes, esto se traduce en **frustración y desconfianza** debido a retrasos y desorganización. El personal, por su parte, enfrenta una **sobrecarga administrativa**, lo que aumenta los errores humanos y reduce el tiempo para la atención directa. A nivel institucional, la ausencia de un sistema centralizado **limita la optimización de recursos**, afectando la capacidad de atender más pacientes y dañando la reputación del hospital.

La modernización con un **Sistema Web de Gestión de Citas** es esencial para resolver estas fallas. Esta solución reduciría errores, mejoraría la coordinación, disminuiría los tiempos de espera y optimizaría los recursos disponibles. En resumen, la gestión manual compromete la **calidad del servicio**, la **eficiencia operativa** y la **imagen del hospital**, haciendo urgente una transformación tecnológica que garantice una atención médica oportuna y efectiva para todos los involucrados.

#### 1.9 Planteamiento del Problema

La gestión de citas en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch enfrenta serios desafíos debido a su dependencia de procesos manuales. La ausencia de un sistema digitalizado impide visualizar la disponibilidad actualizada de los médicos, lo que resulta en asignaciones ineficientes de turnos y tiempos de espera prolongados para los pacientes. Los errores administrativos, como la duplicación de citas, la asignación incorrecta de especialistas o la pérdida de solicitudes, son comunes y generan inconvenientes tanto para el personal como para los usuarios. Asimismo, la comunicación deficiente entre secretarias de diferentes áreas y turnos, así como con los médicos, produce agendas desactualizadas o conflictos de horarios, disminuyendo la eficiencia operativa del hospital. Esta situación sobrecarga al personal administrativo, quienes dedican excesivo tiempo a tareas repetitivas como la confirmación telefónica de citas, en lugar de enfocarse en mejorar la atención al paciente. Para los pacientes, el proceso manual se traduce en largas esperas para obtener una cita, incertidumbre sobre confirmaciones y reprogramaciones inesperadas, afectando negativamente su percepción del servicio. El problema central se plantea como: ¿Cómo puede un sistema web interno optimizar la programación de citas, reducir errores administrativos y mejorar la coordinación entre secretarias y médicos, contribuyendo a una atención más eficiente en el hospital?


#### 2.1 Alcances y Límites

##### 2.1.1 Alcances

El sistema abarcará la creación de una plataforma web con tres módulos principales. El módulo de citas permitirá a las secretarias registrar citas con información del paciente y médico, gestionar horarios según disponibilidad actualizada, y editar o cancelar turnos con validaciones. El módulo de consulta posibilitará a los médicos visualizar agendas en tiempo real, consultar historiales básicos de citas previas y añadir notas de las consultas realizadas. El módulo transversal incluirá una interfaz de usuario intuitiva para ambos roles, reportes automáticos sobre citas programadas, canceladas y atendidas, y notificaciones en tiempo real sobre cambios. La plataforma funcionará exclusivamente en la intranet, garantizando seguridad y accesibilidad para el personal autorizado.

##### 2.1.2 Límites

El sistema no gestionará facturación ni pagos de pacientes, ni controlará inventarios de insumos médicos. No incluirá funcionalidades de telemedicina, como consultas virtuales, ni se integrará con sistemas externos de historias clínicas electrónicas. En esta fase inicial, no ofrecerá soporte multilingüe ni herramientas avanzadas de análisis de datos o inteligencia artificial, limitándose a funciones básicas de gestión y reporte.

#### 2.2 Formulación del Problema

En la actualidad, el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch enfrenta serias dificultades en la gestión de citas médicas debido a su dependencia de métodos manuales, como registros en papel, llamadas telefónicas y coordinación verbal. Estos procesos obsoletos generan múltiples ineficiencias operativas, incluyendo largas demoras para los pacientes, errores en la asignación de turnos, duplicación de esfuerzos y una notable falta de coordinación entre el personal administrativo y médico. Además, el personal dedica un tiempo excesivo a tareas administrativas que podrían automatizarse, lo que limita su capacidad para enfocarse en la atención directa al paciente. Todo esto contribuye a una experiencia negativa para los pacientes, quienes sufren largos tiempos de espera y una gestión poco clara de sus citas.

Ante esta problemática, surgen las siguientes preguntas de investigación:

1. ¿Cómo puede un sistema web de gestión de citas optimizar los procesos de programación y mejorar la coordinación entre secretarias y médicos en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch?  
2. ¿Cuáles son las principales dificultades que enfrenta el hospital en la administración manual de citas y cómo puede la digitalización mitigar estos problemas?  
3. ¿De qué manera la automatización de la asignación y consulta de citas puede reducir los errores administrativos y los tiempos de espera para los pacientes?  
4. ¿Qué tecnologías y metodologías son más adecuadas para desarrollar un sistema web eficiente y seguro que se integre con la intranet del hospital y garantice la protección de los datos médicos?  
5. ¿Cómo impactará la implementación de este sistema en la eficiencia operativa del hospital y en la experiencia general del paciente?

#### 2.3 Marco Metodológico

Para desarrollar tu Sistema Web de Gestión de Citas, se empleará una combinación de métodos de recolección de datos y una metodología ágil que garantizará que el sistema sea funcional, eficiente y responda a tus necesidades específicas. Este marco está diseñado para optimizar la gestión de citas y mejorar la experiencia de los usuarios involucrados, como secretarias, médicos o cualquier otro personal relevante en tu contexto.

#### 2.3.1 Métodos de Recolección de Datos

Para entender cómo funciona tu sistema actual y definir lo que necesitas, usaremos estos métodos:

- **Observación directa**: Analizaremos cómo gestionas las citas actualmente. Observaremos cómo se programan, cambian o cancelan, identificando problemas como retrasos, errores manuales o cuellos de botella en el proceso.
- **Entrevistas y encuestas**: Hablaremos contigo y con las personas que usarán el sistema (por ejemplo, secretarias o médicos) para conocer tus expectativas y los desafíos que enfrentas. También aplicaremos encuestas breves si hay más usuarios involucrados, para captar sus opiniones y necesidades.
- **Revisión documental**: Si tienes documentos como agendas, formularios o reportes relacionados con las citas, los estudiaremos para entender la estructura de la información que manejas. Además, investigaremos tendencias en sistemas de citas para asegurarnos de que tu sistema esté actualizado.

---

#### 2.3.2 Metodología de Desarrollo

Usaremos la metodología ágil **Scrum**, que nos permitirá trabajar de forma flexible y entregarte versiones funcionales del sistema rápidamente. El desarrollo se dividirá en **sprints de 2 a 4 semanas**, con estas etapas:

1. **Definición de requerimientos**: Con base en lo que nos cuentes y lo que observemos, definiremos qué debe hacer el sistema. Por ejemplo, programar citas, consultar agendas o generar reportes. También estableceremos aspectos como seguridad o facilidad de uso.
2. **Diseño del sistema**: Crearemos diagramas claros (como flujos de datos o casos de uso) para planificar cómo funcionará todo y cómo se conectarán las partes del sistema.
3. **Desarrollo paso a paso**: Construiremos las funciones más importantes primero (como el módulo para programar citas) y te las mostraremos para que nos des tu opinión y hagamos ajustes.
4. **Pruebas continuas**: Probaremos cada parte del sistema a medida que lo desarrollamos, y al final haremos pruebas contigo para asegurarnos de que sea fácil de usar y cumpla con lo que necesitas.
5. **Documentación**: Te daremos un manual sencillo para que sepas cómo usar el sistema, además de una guía técnica por si necesitas hacerle cambios en el futuro.

---

#### 2.3.3 Herramientas y Tecnologías

- **Base de datos**: **SQLite**, porque es ligero y funciona bien para sistemas con un número moderado de usuarios.
- **Backend**: **Python con Flask**, para hacer el sistema rápido y fácil de mantener, y SQLAlchemy como ORM para gestionar una base de datos SQLite.
- **Frontend**: **HTML, CSS y JavaScript** con **Bootstrap**, para que la interfaz sea clara, responsive, amigable y se vea bien en cualquier dispositivo.
- **Entorno de operación:** El sistema estará alojado en un servidor local (intranet) del hospital, accesible únicamente desde la red interna para garantizar la seguridad y confidencialidad de los datos.
- **Control de versiones**: **Git**, para organizar el código y trabajar en equipo si es necesario.
- **Diseño**: Usaremos herramientas como **Draw.io** para planificar el sistema visualmente.


#### 2.4 Presupuesto Estimado

|**Elemento**|**Costo Estimado (RD$)**|**Descripción**|**Horas Trabajadas**|**Precio por Hora (RD$)**|
|---|--:|---|--:|--:|
|Desarrollo del sitio web|350 000|Diseño, programación e integración de módulos (citas, consulta, reportes)|300|1 167|
|Pruebas de funcionamiento|60 000|Pruebas unitarias, de integración y aceptación, corrección de errores|60|1 000|
|Servidor y hosting|50 000|Configuración y mantenimiento en intranet (Flask, SQLite)|—|—|
|Seguridad|70 000|Autenticación por roles, cifrado de datos y buenas prácticas de seguridad|80|875|
|Capacitación y soporte técnico|40 000|Formación a secretarias y médicos; soporte post-lanzamiento|25|1 600|
|Formación en tecnologías|30 000|Cursos de Flask, SQLAlchemy, SQLite, HTML/CSS/JS, Bootstrap, Draw.io|—|—|
|Gastos generales|40 000|Luz, internet, consumibles y otros servicios durante el proyecto|—|—|
|Contingencia (20%)|160 000|Reserva para imprevistos y ajustes de alcance|—|—|
|**Total General**|**800 000**||—|—|

#### 2.5 Cronograma

**Sistema Web de Gestión de Citas Médicas**

|**Actividad**|**Duración**|**Fecha de Inicio**|**Fecha de Finalización**|
|:--|:--|:--|:--|
|**1. Levantamiento de Requisitos y Análisis**|1 semana|15-abr-2025|21-abr-2025|
|**2. Diseño del Sistema y Prototipos**|2 semanas|22-abr-2025|05-may-2025|
|**3. Desarrollo del Sitio Web**|6 semanas|06-may-2025|16-jun-2025|
|**4. Implementación de Seguridad y Autenticación**|2 semanas|17-jun-2025|30-jun-2025|
|**5. Pruebas de Funcionamiento**|2 semanas|01-jul-2025|14-jul-2025|
|**6. Configuración de Servidor y Hosting (Intranet)**|1 semana|15-jul-2025|21-jul-2025|
|**7. Capacitación de Personal y Soporte Inicial**|2 semanas|22-jul-2025|04-ago-2025|
|**8. Publicación y Entrega Oficial**|1 semana|05-ago-2025|11-ago-2025|
|**9. Contingencias y Ajustes Finales**|2 semanas|12-ago-2025|25-ago-2025|

## 📌 **Resumen por Fases**

|**Fase**|**Duración**|
|:--|:--|
|Análisis y Diseño|3 semanas|
|Desarrollo e Implementación|8 semanas|
|Pruebas y Configuración|3 semanas|
|Capacitación y Soporte|2 semanas|
|Entrega y Contingencias|3 semanas|
|**Total del Proyecto**|**19 semanas**|

#### 2.6 Índice Tentativo

1. **Capítulo 1: Introducción al Proyecto**  
    1.1. Introducción  
    1.2. Descripción de la Propuesta  
    1.3. Justificación  
    1.4. Motivación  
    1.5. Marco Teórico  
     1.5.1. Antecedentes  
     1.5.2. Conceptos Clave  
    1.6. Glosario de Términos  
    1.7. Objetivos  
     1.7.1. Objetivo General  
     1.7.2. Objetivos Específicos  
    1.8. Importancia del Problema  
    1.9. Planteamiento del Problema
    
2. **Capítulo 2: Marco Metodológico y Planificación**  
    2.1. Alcances y Límites  
     2.1.1. Alcances  
     2.1.2. Límites  
    2.2. Formulación del Problema  
    2.3. Marco Metodológico  
     2.3.1. Métodos de Recolección de Datos  
      – Observación Directa  
      – Entrevistas y Encuestas  
      – Revisión Documental  
     2.3.2. Metodología de Desarrollo (Scrum)  
     2.3.3. Herramientas y Tecnologías  
    2.4. Presupuesto Estimado  
    2.5. Cronograma  
    2.6. Índice Tentativo
    
3. **Capítulo 3: Análisis y Diseño del Sistema**  
    3.1. Modelado de Requisitos  
     3.1.1. Casos de Uso  
     3.1.2. Diagramas de Actividad  
    3.2. Diseño de Arquitectura  
     3.2.1. Diagrama de Componentes  
     3.2.2. Diagrama de Despliegue  
    3.3. Diseño de la Base de Datos  
     3.3.1. Modelo Entidad–Relación  
     3.3.2. Esquema Relacional  
    3.4. Diseño de la Interfaz de Usuario  
     3.4.1. Wireframes y Mockups  
     3.4.2. Prototipo de Alta Fidelidad
    
4. **Capítulo 4: Implementación**  
    4.1. Configuración del Entorno de Desarrollo  
    4.2. Desarrollo del Backend  
     4.2.1. Estructura de la API en Flask  
     4.2.2. Modelos y Persistencia (SQLAlchemy + SQLite)  
    4.3. Desarrollo del Frontend  
     4.3.1. Maquetación con Bootstrap  
     4.3.2. Lógica de Cliente (JavaScript)  
    4.4. Integración de Módulos  
     4.4.1. Módulo de Citas  
     4.4.2. Módulo de Consulta  
     4.4.3. Módulo Transversal (Reportes)
    
5. **Capítulo 5: Seguridad y Autenticación**  
    5.1. Gestión de Usuarios y Roles  
    5.2. Autenticación y Autorización  
    5.3. Cifrado y Protección de Datos  
    5.4. Buenas Prácticas y Políticas de Seguridad
    
6. **Capítulo 6: Pruebas y Calidad**  
    6.1. Plan de Pruebas  
     6.1.1. Pruebas Unitarias  
     6.1.2. Pruebas de Integración  
     6.1.3. Pruebas de Aceptación de Usuario  
    6.2. Resultados de las Pruebas  
    6.3. Corrección de Errores y Ajustes
    
7. **Capítulo 7: Despliegue y Operación**  
    7.1. Configuración del Servidor Intranet  
    7.2. Despliegue de la Aplicación  
    7.3. Plan de Mantenimiento  
    7.4. Respaldo y Recuperación de Datos
    
8. **Capítulo 8: Capacitación y Soporte**  
    8.1. Manual de Usuario  
    8.2. Manual Técnico  
    8.3. Plan de Capacitación  
    8.4. Soporte Post‑Lanzamiento
    
9. **Capítulo 9: Conclusiones y Recomendaciones**  
    9.1. Conclusiones del Proyecto  
    9.2. Lecciones Aprendidas  
    9.3. Recomendaciones para Futuras Mejoras
    
10. **Anexos**  
    A. Glosario de Términos  
    B. Diagramas Completos  
    C. Códigos Fuente Relevantes  
    D. Formularios de Encuesta y Entrevista  
    E. Plan de Gestión de Riesgos
    

#### 2.7 Referencias

1. Beck, K., Beedle, M., van Bennekum, A., Cockburn, A., Cunningham, W., Fowler, M., … Thomas, D. (2001). _Manifesto for Agile Software Development_. Recuperado de [https://agilemanifesto.org/](https://agilemanifesto.org/)
    
2. Schwaber, K., & Sutherland, J. (2020). _The Scrum Guide™_. Scrum.org. Recuperado de [https://scrumguides.org/scrum-guide.html](https://scrumguides.org/scrum-guide.html)
    
3. Grinberg, M. (2018). _Flask Web Development: Developing Web Applications with Python_. O’Reilly Media.
    
4. Bayer, S. (2013). _Mastering SQLAlchemy_. Packt Publishing.
    
5. Hipp, D. R. (2024). _SQLite Documentation_. SQLite Consortium. Recuperado de [https://www.sqlite.org/docs.html](https://www.sqlite.org/docs.html)
    
6. Otto, M., & Thornton, J. (2018). _Bootstrap 4 Quick Start: A Beginner’s Guide to Building Responsive Layouts with Bootstrap 4_. Leanpub.
    
7. OASIS Open. (2023). _The Open Document Format for Office Applications (OpenDocument) v1.3_. Recuperado de [https://www.oasis-open.org/standards#opendocument](https://www.oasis-open.org/standards#opendocument)
    
8. Draw.io (diagrams.net). (2024). _diagrams.net User Manual_. Recuperado de [https://www.diagrams.net/](https://www.diagrams.net/)
    
9. ISO. (2011). _ISO/IEC 27001:2013 – Information technology — Security techniques — Information security management systems — Requirements_. International Organization for Standardization.
    
10. World Health Organization. (2016). _Global strategy on digital health 2020–2025_. Geneva: WHO Press.
    
11. Khosrow-Pour, M. (Ed.). (2021). _Encyclopedia of Information Science and Technology_ (5th ed.). IGI Global. (Capítulo “Digital Health” y “Healthcare Information Systems”)
    
12. Ministry of Public Health of the Dominican Republic. (2019). _Normativas de confidencialidad y protección de datos de salud_. Santo Domingo.
    
13. Pressman, R. S., & Maxim, B. R. (2020). _Software Engineering: A Practitioner’s Approach_ (9th ed.). McGraw-Hill Education.
    
14. Sommerville, I. (2016). _Software Engineering_ (10th ed.). Pearson.
    
15. Nielsen, J. (1994). _Usability Engineering_. Morgan Kaufmann.
    
16. ISO. (2019). _ISO 9241-11:2018 – Ergonomics of human-system interaction — Usability: Definitions and concepts_. International Organization for Standardization.
    
17. Hospital Traumatológico y Quirúrgico Prof. Juan Bosch. (2024). _Manual de procedimientos administrativos y gestión de citas_. El Pino, La Vega, República Dominicana. (Documento interno)
    
18. República Dominicana. (2008). _Ley No. 172-13 sobre protección de datos personales_. Gaceta Oficial.
    
