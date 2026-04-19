# UNIVERSIDAD NACIONAL PEDRO HENRÍQUEZ UREÑA

**(UNPHU)**

Recinto La Vega

Facultad de Ciencias y Tecnología

Escuela de Informática

---

## Sistema Web de Gestión de Citas Médicas para el Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch

---

Trabajo de Grado para optar por el título de:

**Licenciatura en Informática**

**Sustentantes:**

Cristopher Rafael Marcial — 21-1969

Jeremy José de la Cruz Pérez — 21-0266

**Asesor:**

Lic. David D'Oleo

La Vega, República Dominicana

Agosto, 2026

---

## Resumen

El presente trabajo de grado tiene como objetivo diseñar, desarrollar e implementar un sistema web de gestión de citas médicas para el Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch (HTQPJB), institución pública de tercer nivel ubicada en la Autopista Duarte KM 101, Comunidad El Pino, La Vega, República Dominicana. El hospital gestiona actualmente sus citas mediante procesos manuales que generan duplicaciones de turnos, tiempos de espera prolongados y descoordinación entre el personal administrativo y médico.

El sistema propuesto automatiza este proceso mediante tres módulos principales: registro de pacientes, gestión de citas con calendario interactivo y consulta de agenda médica. Se adoptó un enfoque de desarrollo iterativo incremental con ciclos de dos semanas, inspirado en los principios del Manifiesto Ágil. El stack tecnológico comprende Python con FastAPI y SQLModel en el backend, PostgreSQL como sistema gestor de base de datos, HTML, JavaScript con FullCalendar.js y Tailwind CSS en el frontend, WeasyPrint para la generación de reportes en PDF, Alembic para el control de versiones del esquema de la base de datos, pytest para las pruebas automatizadas, y Docker con Nginx para el despliegue seguro en la intranet del hospital.

El sistema implementa control de acceso basado en roles (RBAC) mediante tokens JWT, hashing de contraseñas con bcrypt, auditoría transaccional de todas las operaciones críticas, y cumplimiento de la Ley 172-13 sobre protección de datos personales. La integración continua se garantiza mediante GitHub Actions, que ejecuta automáticamente las pruebas y validaciones de lint en cada cambio del código fuente. Los resultados esperados incluyen la reducción de errores administrativos, la optimización del tiempo de agendamiento y la mejora en la experiencia del personal y los pacientes.

**Palabras clave:** sistema web, gestión de citas médicas, FastAPI, PostgreSQL, RBAC, auditoría transaccional, integración continua, salud digital, República Dominicana.

---

## Agradecimientos

### Cristopher Rafael Marcial

A Dios: agradezco al Señor Todopoderoso por concederme la sabiduría y la fortaleza necesarias para culminar este proyecto, y por ser guía en cada etapa de mi formación profesional.

A la Universidad Nacional Pedro Henríquez Ureña (UNPHU): por brindarnos la formación académica y el entorno institucional necesarios para el desarrollo de este trabajo de grado.

Al Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch: por abrirnos las puertas de su institución y permitirnos implementar este sistema. Se agradece especialmente la colaboración del personal administrativo y médico durante las fases de análisis y validación del sistema.

Al asesor, Lic. David D'Oleo: por su orientación metodológica, su paciencia y sus valiosos aportes que enriquecieron este trabajo en cada etapa de su desarrollo.

*Cristopher Rafael Marcial*

### Jeremy José de la Cruz Pérez

A Dios: al Todopoderoso, por acompañarme en cada etapa de este proceso y darme la fortaleza para culminar esta meta con éxito.

A mis padres: por su amor, dedicación y esfuerzo constante para brindarme las mejores condiciones para mi formación académica.

Al asesor, Lic. David D'Oleo: por su disponibilidad, sus orientaciones precisas y sus aportaciones técnicas, que fueron fundamentales para el desarrollo de este proyecto.

*Jeremy José de la Cruz Pérez*

---

## Dedicatorias

### Cristopher Rafael Marcial

A Dios, por ser el guía y el motor de mi vida. A mis padres, por su dedicación y esfuerzo para brindarme la mejor educación posible. A mi compañero de tesis Jeremy, por su compromiso y trabajo constante a lo largo de este proyecto.

*Cristopher Rafael Marcial*

### Jeremy José de la Cruz Pérez

A Dios, por acompañarme en cada etapa de este camino. A mis padres, cuyo amor, dedicación y esfuerzo hacen posible este logro. A mis hermanos, por su apoyo incondicional.

*Jeremy José de la Cruz Pérez*

---

# CAPÍTULO I: ASPECTOS INTRODUCTORIOS

## 1.1. Introducción

Desde los orígenes de la humanidad, la comunicación y la organización han constituido factores determinantes para el desarrollo de las instituciones. Hoy en día, gracias al avance de las tecnologías de la información, las instituciones de salud disponen de herramientas capaces de transformar radicalmente la eficiencia de sus procesos administrativos.

Los sistemas de información constituyen un activo estratégico para las instituciones, independientemente de su tamaño, pues contribuyen a la optimización de sus procesos, la centralización de datos y la generación de información en tiempo real para la toma de decisiones.

El Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch (HTQPJB), ubicado en la Autopista Duarte KM 101, Comunidad El Pino, provincia La Vega, República Dominicana, es una institución pública de tercer nivel especializada en traumatología y cirugía, que constituye el primer hospital de la región del Cibao dedicado exclusivamente a la atención de usuarios traumatizados y con patologías ortopédicas y quirúrgicas (HTQPJB, 2022).

Sin embargo, el proceso actual de gestión de citas depende de métodos manuales que generan ineficiencias operativas significativas, entre las que destacan demoras en el agendamiento, errores en la asignación de turnos y duplicación de esfuerzos administrativos. La ausencia de un sistema centralizado dificulta la coordinación entre secretarias y médicos, afectando la planificación diaria y la experiencia del paciente.

Por esta razón, resulta indispensable el desarrollo de un sistema web de gestión de citas médicas para automatizar y centralizar la programación médica mediante una plataforma digital accesible desde la intranet institucional.

## 1.2. Antecedentes

### 1.2.1. Antecedentes internacionales

Martínez y Rodríguez (2019) desarrollaron una investigación orientada al diseño e implementación de un sistema digital de agendamiento médico en el Hospital Universitario de Navarra, España. Los autores concluyeron que la digitalización redujo en un 42 % los tiempos de espera y en un 78 % los errores de duplicación, destacando la implementación de un sistema de control de acceso basado en roles como elemento clave para la confidencialidad de los datos médicos.

García y Pérez (2020) propusieron la digitalización del proceso de agendamiento médico para la red hospitalaria del Instituto Mexicano del Seguro Social. El sistema implementado gestionó más de cinco millones de citas mensuales y logró una reducción del 35 % en las ausencias de pacientes gracias a un módulo de gestión de disponibilidad médica en tiempo real.

Ramírez et al. (2021) implementaron un sistema web de gestión hospitalaria en el Hospital Clínico de la Universidad de Chile. Los autores concluyeron que la ausencia de una plataforma centralizada generaba pérdidas de información y descoordinación entre departamentos. El sistema implementado integró la gestión de citas con el expediente médico electrónico, logrando una mejora del 60 % en la satisfacción del personal administrativo.

### 1.2.2. Antecedentes nacionales

Méndez y Santos (2022) desarrollaron un sistema de información para la gestión de citas del Centro de Diagnóstico de Imágenes de Santo Domingo, orientado a automatizar el proceso de agendamiento y la generación automática de reportes de atención, bajo un enfoque iterativo de desarrollo.

Comprés y Familia (2020) implementaron un módulo de gestión de citas integrado al sistema de información hospitalaria del Hospital General Plaza de la Salud, en el Distrito Nacional. Los resultados indicaron que el módulo eliminó el 60 % de los procesos manuales de agendamiento y redujo los tiempos de espera en consulta externa.

## 1.3. Planteamiento del problema

El Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch gestiona actualmente sus citas médicas mediante procesos completamente manuales, apoyados en registros físicos, llamadas telefónicas y comunicación verbal entre el personal administrativo y médico. La ausencia de mecanismos tecnológicos para el registro y control de las citas genera múltiples problemas operativos que comprometen la calidad del servicio.

Las principales dificultades identificadas son: duplicación de citas por carencia de un registro centralizado; tiempos de espera prolongados causados por la desorganización en la asignación de turnos; errores administrativos frecuentes como asignaciones incorrectas o cancelaciones no procesadas; sobrecarga de trabajo para el personal administrativo; y falta de visibilidad en tiempo real sobre la disponibilidad médica.

Ante esta realidad, surge la siguiente pregunta central de investigación: ¿cómo puede un sistema web de gestión de citas médicas optimizar los procesos administrativos y mejorar la calidad del servicio en el Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch?

## 1.4. Objetivos

### 1.4.1. Objetivo general

Diseñar, desarrollar e implementar un sistema web para la automatización del proceso de gestión de citas médicas en el Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch, mediante módulos especializados de registro de pacientes, agendamiento de citas y consulta de agenda médica, garantizando la seguridad de los datos y la optimización del tiempo de atención.

### 1.4.2. Objetivos específicos

- Implementar un módulo de registro de pacientes que permita crear, consultar, modificar y eliminar datos de forma centralizada y segura, con validación de cédula dominicana.
- Desarrollar un módulo de gestión de citas con calendario interactivo mediante FullCalendar.js que permita agendar, consultar, reprogramar y cancelar citas según la disponibilidad de los médicos.
- Crear un módulo de consulta médica que permita a los médicos visualizar su agenda diaria y registrar observaciones básicas de cada consulta.
- Implementar control de acceso basado en roles mediante tokens JWT para garantizar que cada usuario acceda solo a las funcionalidades de su perfil.
- Diseñar una interfaz adaptativa que oculte dinámicamente los controles y vistas no autorizados según el rol del usuario autenticado, mejorando la experiencia de uso y reforzando la seguridad en la capa de presentación.
- Generar reportes exportables en formato PDF mediante WeasyPrint, filtrados por período y por médico, que faciliten la toma de decisiones administrativas.
- Implementar un registro de auditoría transaccional que capture todas las operaciones críticas del sistema, garantizando trazabilidad completa y cumplimiento de la Ley 172-13 sobre protección de datos personales.
- Establecer un proceso de integración continua mediante GitHub Actions que ejecute automáticamente las pruebas y los controles de calidad del código ante cada modificación.

## 1.5. Justificación

La implementación del Sistema Web de Gestión de Citas en el HTQPJB se justifica desde las perspectivas operativa, tecnológica y social. Operativamente, el sistema eliminará las ineficiencias derivadas de los procesos manuales, reduciendo tiempos de agendamiento y errores administrativos. Tecnológicamente, incorpora herramientas modernas de código abierto que garantizan un sistema robusto y de bajo costo de mantenimiento. Socialmente, impacta positivamente la experiencia del paciente al ofrecer un servicio más ágil y confiable a la comunidad de La Vega.

## 1.6. Motivación

Durante la fase de observación preliminar, los investigadores constataron directamente las dificultades del personal: agendas físicas saturadas, llamadas continuas para confirmar citas y errores frecuentes. Esta realidad generó la motivación de desarrollar una solución tecnológica que aliviara las cargas operativas y demostrara cómo la informática puede contribuir al bienestar comunitario.

## 1.7. Alcance y límites

### 1.7.1. Alcances

| Módulo | Funcionalidades incluidas |
|---|---|
| Autenticación y seguridad | Inicio y cierre de sesión con tokens JWT, validación de credenciales, control de roles y auditoría automática de accesos. |
| Registro de pacientes | Registro con validación de cédula dominicana, actualización de datos, búsqueda incremental y exportación mediante reportes PDF. |
| Gestión de citas | Registro con FullCalendar.js, reprogramación, cancelación validada y vistas de disponibilidad por día, semana y mes. |
| Consulta médica | Agenda diaria en tiempo real, registro de observaciones básicas y búsqueda por paciente, fecha o estado. |
| Gestión de médicos | Alta, edición, desactivación y configuración de bloques de disponibilidad horaria. |
| Reportes | Generación de documentos PDF filtrados por período y por médico mediante WeasyPrint. |
| Administración | Gestión de usuarios, asignación de roles, desactivación de cuentas y consulta de registros de auditoría. |

### 1.7.2. Limitaciones

- No enviará recordatorios por mensaje de texto o correo electrónico, dado que el sistema opera en una intranet sin servicios externos.
- No gestionará citas de emergencia ni atenciones espontáneas.
- No integrará historial clínico completo ni expediente médico electrónico.
- No validará datos con bases gubernamentales o aseguradoras en tiempo real.

## 1.8. Formulación

- ¿De qué manera la implementación del sistema web optimizará los procesos de agendamiento y reducirá los errores administrativos en el HTQPJB?
- ¿Cómo puede la digitalización mejorar la coordinación entre secretarias y médicos y reducir los tiempos de espera?
- ¿Qué tecnologías son más adecuadas para garantizar la seguridad de los datos médicos conforme a la Ley 172-13?

---

# CAPÍTULO II: MARCO TEÓRICO

## 2.1. Gestión de citas médicas

La gestión de citas médicas es el proceso administrativo mediante el cual un centro de salud organiza, asigna y controla las consultas entre pacientes y personal médico. Cuando se realiza de forma manual, es frecuente que se presenten errores como citas duplicadas y falta de coordinación (Organización Mundial de la Salud, 2021). Un sistema digital garantiza la disponibilidad de la información en tiempo real y elimina estructuralmente las duplicaciones mediante validaciones a nivel de base de datos.

## 2.2. Sistema web

Un sistema web es una aplicación informática que se ejecuta a través de un navegador web, sin requerir instalación en el equipo del usuario (Pressman y Maxim, 2020). Esta característica es ideal para entornos hospitalarios donde múltiples usuarios necesitan acceder desde diferentes equipos.

## 2.3. Intranet

Una intranet es una red privada de comunicación interna de una organización, accesible exclusivamente para su personal autorizado (Sommerville, 2016). Su naturaleza cerrada la convierte en una opción segura para el manejo de información sensible como los datos médicos de los pacientes.

## 2.4. Base de datos relacional

Una base de datos es un conjunto de datos almacenados de forma sistemática y estructurada para su posterior consulta (Gómez, 2007). Para este proyecto se utiliza PostgreSQL, sistema de gestión de bases de datos relacional de código abierto que garantiza integridad mediante transacciones ACID (PostgreSQL Global Development Group, 2023). PostgreSQL ofrece funcionalidades avanzadas como los índices únicos parciales, que permiten aplicar restricciones de unicidad condicionadas al valor de una columna, característica empleada en el presente proyecto para la gestión de citas.

## 2.5. Control de acceso basado en roles

El control de acceso basado en roles, conocido por sus siglas en inglés como RBAC (*Role-Based Access Control*), es el mecanismo de seguridad que determina los permisos de cada usuario según su función dentro de la organización (ISO/IEC 27001, 2022). En este proyecto se aplica con tres perfiles: secretaria, médico y administrador. El control se implementa en dos capas complementarias: una capa de autorización en el backend, que valida cada petición HTTP mediante dependencias de FastAPI, y una capa de presentación en el frontend, que adapta dinámicamente la interfaz mostrando únicamente los controles autorizados para el rol activo.

## 2.6. Python con FastAPI y SQLModel

Python es un lenguaje de programación de alto nivel, interpretado, orientado a objetos y de propósito general, reconocido por su legibilidad y su ecosistema de bibliotecas (Van Rossum y Drake, 2023). FastAPI es el framework web para la construcción de la API REST, destacado por su alto rendimiento y documentación automática mediante OpenAPI (Ramírez, 2023a). SQLModel combina SQLAlchemy y Pydantic en una sola capa, facilitando la definición de modelos de base de datos y esquemas de validación (Ramírez, 2023b).

## 2.7. Alembic, WeasyPrint y pytest

Alembic es la herramienta estándar de control de versiones para esquemas de bases de datos en proyectos SQLAlchemy y SQLModel (Bayer, 2023). WeasyPrint convierte documentos HTML y CSS en archivos PDF de alta calidad, permitiendo generar reportes a partir de los mismos templates HTML del frontend (WeasyPrint Team, 2023). Pytest es el framework de pruebas automatizadas estándar para Python, que en combinación con httpx permite verificar el comportamiento correcto de los endpoints de la API (Krekel et al., 2023).

## 2.8. FullCalendar.js

FullCalendar.js es una biblioteca de JavaScript de código abierto que implementa un calendario interactivo con soporte para vistas de día, semana y mes, gestión de eventos y bloques de tiempo. Su integración con APIs REST mediante *fetch* permite mostrar los horarios disponibles de cada médico en tiempo real (FullCalendar LLC, 2023).

## 2.9. Docker y Nginx

Docker es una plataforma de virtualización a nivel de sistema operativo que empaqueta aplicaciones y dependencias en contenedores portátiles (Docker Inc., 2023). Nginx es el servidor web y proxy inverso que gestiona las solicitudes HTTP y habilita HTTPS dentro de la intranet mediante un certificado SSL generado con mkcert (Nginx Inc., 2023). La combinación de Docker Compose con Nginx permite orquestar los servicios de base de datos, backend y frontend como unidades independientes pero coordinadas.

## 2.10. Integración continua

La integración continua es la práctica de desarrollo que consiste en incorporar los cambios del código fuente a un repositorio compartido de forma frecuente, ejecutando automáticamente verificaciones de calidad ante cada modificación (Duvall et al., 2007). En el presente proyecto se emplea GitHub Actions, plataforma de automatización incorporada en el servicio GitHub, que ejecuta en cada envío de código un flujo de trabajo que comprende la instalación del entorno, el análisis estático mediante *linters*, la ejecución de la suite completa de pruebas pytest y la verificación de la construcción de la imagen Docker del sistema.

## 2.11. Marco legal: Ley 172-13

La Ley 172-13 sobre Protección de Datos de Carácter Personal de la República Dominicana establece los principios que deben cumplir las instituciones en el tratamiento de datos personales (República Dominicana, 2013): licitud, finalidad, proporcionalidad, seguridad y confidencialidad. El SGCM implementa estas obligaciones mediante el control de acceso basado en roles, el hashing con bcrypt, la comunicación cifrada HTTPS a través de Nginx y el registro completo de auditoría transaccional.

---

# CAPÍTULO III: INVESTIGACIÓN PRELIMINAR

## 3.1. Datos generales de la institución

### 3.1.1. Descripción de la institución

El Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch es una institución de salud pública de tercer nivel, especializada y descentralizada, perteneciente a la red pública del Servicio Nacional de Salud, dependiente del Ministerio de Estado de Salud Pública y Asistencia Social. Se encuentra ubicado en la Autopista Duarte KM 101, Carretera Bonao–La Vega, Comunidad El Pino, provincia La Vega, República Dominicana (HTQPJB, 2022).

Constituye el primer hospital de la región del Cibao dedicado exclusivamente a la atención de usuarios traumatizados y aquellos con patologías ortopédicas y quirúrgicas. Cuenta con 145 camas instaladas y ocho salas de cirugía, con una nómina que superaba los 749 empleados al año 2016, siendo una de las instituciones que más empleo aporta a la ciudad de La Vega. Es uno de los hospitales traumatológicos más importantes del país y el más relevante en la región norcentral.

Sus datos de contacto oficiales son: teléfono (809) 725-8262, fax (809) 725-8472, correo electrónico info@hospitaljuanbosch.gob.do, y página web www.hospitaljuanbosch.gob.do.

### 3.1.2. Historia

El Hospital Traumatológico y Quirúrgico Prof. Juan Bosch fue inaugurado el 5 de septiembre del año 2006 por el entonces presidente Dr. Leonel Fernández Reina, bajo la visión de un hospital modelo denominado *Hospital del Futuro en el Presente*. La primera emergencia se realizó el 25 de septiembre de 2006 a las 8:30 de la noche, con el usuario José Aníbal Díaz (HTQPJB, 2022).

En el año 2008, se convirtió en el único centro de salud de la región del Cibao en recibir el Premio Nacional a la Calidad y Prácticas Promisorias con Medalla de Bronce. En 2016, fue el primer hospital del Servicio Nacional de Salud en obtener el Gran Premio Nacional a la Calidad y Prácticas Promisorias, habiendo acumulado seis medallas de oro consecutivas en ese certamen.

En octubre de 2022, el Dr. Eligio Joel Ortega asumió la Dirección General. Bajo su gestión, en el año 2025 el hospital obtuvo el tercer lugar en el renglón *Hospital Autogestión* y logró un 98 % de cumplimiento en la Carta Compromiso al Ciudadano, consolidando su posición como referente en calidad y excelencia (HTQPJB, 2022).

### 3.1.3. Misión institucional

Somos una institución de servicios de salud especializada, que brinda atenciones, con calidad y humanizadas, con énfasis en traumatología y cirugía, utilizando procesos asistenciales estandarizados e integrales, apoyados en la utilización eficiente de los recursos y el uso racional de tecnologías, promoviendo el constante desarrollo del conocimiento científico a través de la docencia e investigación (HTQPJB, 2022).

### 3.1.4. Visión institucional

Alcanzar la excelencia en la prestación de los servicios traumatológicos y quirúrgicos basados en la autogestión y la oferta de servicios de salud oportunos, accesibles y de calidad, garantizando la sostenibilidad y el desarrollo de nuestros recursos humanos (HTQPJB, 2022).

### 3.1.5. Valores institucionales

Los valores que rigen la cultura organizacional del HTQPJB, conforme a su página institucional oficial, son los siguientes (HTQPJB, 2022):

| Valor | Descripción oficial del HTQPJB |
|---|---|
| Excelencia | Brindando servicios por encima de las expectativas esperadas. |
| Calidad | Trabajando para satisfacer las necesidades y expectativas de los usuarios dentro de un proceso de mejora continua, garantizando la equidad en la atención y el uso de tecnología y conocimientos actualizados en salud. |
| Humanidad | Promoviendo en el personal la sensibilidad y devoción ante sus semejantes, para garantizar un trato digno y de respeto a los usuarios. |
| Educación | Promoviendo las actividades educativas para facilitar la formación especializada, actualización, información e investigación de los recursos humanos. |
| Responsabilidad social | Promoviendo la excelencia en la entrega de servicios, con especial atención en las personas, para cumplir con el compromiso social, económico y ambiental. |
| Trabajo en equipo | Implementando estrategias, procedimientos y metodologías interrelacionadas para lograr la satisfacción y seguridad en la atención de los usuarios. |
| Lealtad | Firme compromiso de cumplir y defender el derecho de la institución y de los usuarios a brindar y recibir atenciones de calidad. |
| Honestidad | Actuando con verdad, transparencia, justicia, ética y coherencia, tomando las decisiones con base en el análisis de datos. |
| Integridad | Compromiso con el cumplimiento de los ejes transversales de la institución. |

*Nota.* Valores transcritos textualmente de la página oficial del HTQPJB (www.hospitaljuanbosch.gob.do/quienes-somos-2/).

### 3.1.6. Servicios que ofrece la institución

El HTQPJB ofrece los siguientes servicios especializados, según su página web oficial (HTQPJB, 2022):

- Ortopedia y Traumatología, servicio principal y especialidad de referencia regional.
- Cirugía General, Cirugía Vascular, Cirugía Torácica, Cirugía Plástica, Cirugía Pediátrica y Cirugía Ginecológica.
- Neurocirugía y Cirugía Maxilofacial.
- Anestesiología, Analgesia y Reanimación.
- Medicina Interna y Especialidades, incluyendo evaluaciones prequirúrgicas, electrocardiogramas y punción lumbar.
- Urgencias y Emergencias, con atención las veinticuatro horas los siete días de la semana.
- Urología, Oftalmología y Otorrinolaringología.
- Medicina Física y Rehabilitación.
- Laboratorio Clínico, Radiología y Diagnóstico por Imágenes.
- Residencias médicas en Ortopedia y Traumatología, Emergenciología y Desastres, Cirugía General, y Anestesiología.

### 3.1.7. Organización de la institución

La estructura organizativa del HTQPJB está encabezada por la Dirección General, actualmente a cargo del Dr. Eligio Joel Ortega. Coordina las subdirecciones Médica y Administrativa, junto a las áreas de Docencia e Investigación. La Subdirección Médica supervisa los departamentos clínicos: Ortopedia y Traumatología, Cirugía General, Emergencias, Anestesiología y Consulta Externa, entre otros. La Subdirección Administrativa gestiona Finanzas, Recursos Humanos, Estadísticas, Farmacia y Mantenimiento. El área de Consulta Externa es la principal beneficiaria del sistema propuesto en este proyecto.

## 3.2. Datos generales del sistema

### 3.2.1. Descripción del sistema

El Sistema Web de Gestión de Citas Médicas automatizará los procesos de agendamiento de consultas, registro de pacientes y consulta de agenda médica en el HTQPJB. Su propósito es centralizar la información en una base de datos relacional, permitiendo al personal autorizado acceder, registrar y gestionar los datos de forma ágil y segura desde la intranet del hospital. El sistema no reemplazará al personal, sino que liberará al personal de tareas repetitivas para concentrarse en la atención directa al usuario, en consonancia con la misión institucional del HTQPJB de brindar atenciones con calidad y humanizadas.

### 3.2.2. Metodología de investigación

La metodología de investigación es el conjunto de procedimientos sistemáticos mediante los cuales se recopila, analiza e interpreta la información necesaria para fundamentar el desarrollo del sistema (Creswell, 2014). Los métodos empleados fueron los siguientes.

#### 3.2.2.1. Entrevistas

Se realizaron entrevistas semiestructuradas a la coordinadora de secretarias, dos secretarias en activo y tres médicos especialistas del área de Consulta Externa. Los hallazgos revelaron que el proceso actual de agendamiento demora entre diez y veinte minutos por cita, que se registran en promedio tres duplicaciones diarias, y que el personal dedica aproximadamente el 40 % de su jornada a tareas administrativas manuales (Fontana y Frey, 2018).

#### 3.2.2.2. Cuestionarios

Se aplicó un cuestionario estructurado a quince miembros del personal. Los resultados indicaron que el 87 % de los participantes calificó el proceso actual como ineficiente o muy ineficiente, y el 93 % consideró que un sistema digital mejoraría su desempeño laboral (Babbie, 2016).

#### 3.2.2.3. Observaciones

Se realizaron tres sesiones de observación directa en el área de Consulta Externa. Las observaciones confirmaron fricciones especialmente en los horarios de mayor demanda, los lunes y miércoles en la mañana, cuando la afluencia de pacientes supera la capacidad del sistema manual (Fraenkel y Wallen, 2014).

#### 3.2.2.4. Recopilación de documentos

Se analizaron formularios físicos de registro de pacientes, libretas de agendas de los médicos y reportes mensuales elaborados manualmente, que sirvieron de base para la definición de los campos y estructuras de datos del sistema (Creswell, 2014).

#### 3.2.2.5. Análisis del Diagrama de Flujo de Datos

Se elaboró un Diagrama de Flujo de Datos del proceso actual de gestión de citas para identificar los puntos críticos susceptibles de digitalización. El análisis reveló que la información fluye de forma fragmentada entre los actores: los pacientes proporcionan datos verbalmente a las secretarias, quienes los registran en libretas físicas; los médicos consultan sus agendas al inicio de cada turno; y los reportes se elaboran manualmente a fin de mes.

---

# CAPÍTULO IV: ANÁLISIS DEL SISTEMA

## 4.1. Estudio de factibilidad

### 4.1.1. Factibilidad operacional

El sistema cuenta con el respaldo de la administración y el personal del HTQPJB. El 80 % de los participantes encuestados tiene conocimientos básicos o intermedios en el uso de aplicaciones web. Se planifica un programa de capacitación de tres días antes de la puesta en marcha, garantizando que el personal pueda operarlo con confianza desde el primer día.

### 4.1.2. Factibilidad técnica

El hospital cuenta con computadoras en el área de Consulta Externa que cumplen los requisitos mínimos de hardware para ejecutar el sistema como cliente web. La conectividad interna es adecuada para soportar múltiples usuarios concurrentes. En caso de que el departamento de informática no permita Docker, se dispone de un plan de despliegue alternativo mediante instalación directa de Python y PostgreSQL sobre Ubuntu Server.

### 4.1.3. Factibilidad económica

Dado que todas las tecnologías son de código abierto y gratuitas, el presupuesto se concentra en gastos operativos, equipos y materiales. En comparación con sistemas comerciales equivalentes, cuyos costos de licenciamiento pueden superar los USD 50,000 anuales (Epic Systems Corporation, 2023; Cerner Corporation, 2022), el sistema propuesto representa una inversión significativamente más accesible para una institución pública.

## 4.2. Evaluación de costos y beneficios

### 4.2.1. Costos

| Concepto | Descripción | Total (RD$) |
|---|---|---|
| Transporte integrante 1 | Gasto semanal en transporte durante el proyecto (RD$400 × 52 semanas) | 20,800 |
| Transporte integrante 2 | Gasto semanal en transporte durante el proyecto (RD$400 × 52 semanas) | 20,800 |
| Conectividad integrante 1 | Internet y electricidad mensual (RD$3,000 × 12 meses) | 36,000 |
| Conectividad integrante 2 | Internet y electricidad mensual (RD$2,500 × 12 meses) | 30,000 |
| Impresión de tesis | Tres copias impresas y empastadas del documento final | 2,000 |
| Papelería y materiales | Hojas, bolígrafos, carpetas e insumos varios | 3,500 |
| Capacitación técnica | Cursos de FastAPI, PostgreSQL y seguridad informática | 5,000 |
| Vestimenta formal | Indumentaria formal por integrante (× 2) | 9,000 |
| Laptop integrante 1 | Core i5 / 8 GB RAM / 240 GB SSD | 17,000 |
| Laptop integrante 2 | Core i7 / 16 GB RAM / 512 GB SSD | 23,000 |
| **Total** | | **167,100** |

*Nota.* Elaboración propia (2026). Todo el software del sistema es de código abierto y gratuito.

### 4.2.2. Beneficios

- Reducción del tiempo de agendamiento de entre diez y veinte minutos a menos de cinco minutos por cita.
- Eliminación física de citas duplicadas mediante el índice único parcial sobre la combinación de médico, fecha y hora en PostgreSQL.
- Visibilidad en tiempo real de la disponibilidad médica a través de FullCalendar.js.
- Generación automática de reportes PDF en segundos, eliminando el proceso manual mensual.
- Mejora en la experiencia del paciente al reducir tiempos de espera y desorganización.
- Trazabilidad completa de operaciones mediante el registro de auditoría transaccional, en cumplimiento de la Ley 172-13.
- Reducción del riesgo de fallos regresivos gracias al proceso automatizado de integración continua, que valida cada cambio del código fuente antes de su incorporación a la rama principal.

## 4.3. Requerimientos del sistema

### 4.3.1. Requerimientos de información

- Datos de pacientes: cédula, nombre, apellidos, fecha de nacimiento, teléfono y dirección.
- Datos de médicos: nombre, especialidad y bloques de disponibilidad horaria.
- Datos de citas: paciente, médico, fecha, hora, estado y motivo de consulta.
- Datos de usuarios: nombre, correo electrónico, rol y hash de contraseña.
- Datos de consultas: cita asociada, observaciones del médico y fecha de registro.
- Datos de auditoría: usuario que ejecuta la acción, tipo de acción, tabla afectada, identificador del registro, detalle textual, dirección IP de origen y marca temporal.

### 4.3.2. Requerimientos de proceso

- Operaciones de creación, lectura, actualización y eliminación sobre todas las entidades del sistema, con los permisos correspondientes a cada rol.
- Autenticación con tokens JWT con expiración configurable y autorización mediante RBAC en cada endpoint protegido.
- Consulta de disponibilidad médica en tiempo real mediante FullCalendar.js, alimentada por un feed JSON expuesto por el backend.
- Generación de reportes en PDF mediante WeasyPrint con filtros por período y por médico.
- Registro automático y transaccional de auditoría de todas las operaciones críticas, donde el registro del log comparte transacción con la operación principal.
- Adaptación dinámica de la interfaz según el rol del usuario autenticado, ocultando enlaces, formularios y controles no autorizados.
- Ejecución automática de la suite de pruebas pytest y del análisis estático del código en cada envío al repositorio, mediante GitHub Actions.
- Respaldo automático diario de la base de datos mediante pg_dump y tareas programadas.

## 4.4. Diagramas de flujo de datos

### 4.4.1. Diagrama de Contexto (DFD Nivel 0)

El Diagrama de Contexto representa el sistema en su nivel más alto de abstracción, identificando las entidades externas que interactúan con él y los flujos de información principales. Las entidades externas son tres: Secretaria, Médico y Administrador.

*Figura 1.* Diagrama de contexto del Sistema Web de Gestión de Citas Médicas.

- **Secretaria** → Datos del paciente, solicitud de cita, modificación, cancelación → **SGCM**
- **SGCM** → Confirmación de cita, reporte PDF, disponibilidad médica → **Secretaria**
- **Médico** → Consulta de agenda, registro de observaciones → **SGCM**
- **SGCM** → Agenda actualizada, confirmación de observaciones → **Médico**
- **Administrador** → Gestión de usuarios, solicitud de reportes globales, consulta de auditoría → **SGCM**
- **SGCM** → Reportes globales, registro de auditoría, confirmación de cambios → **Administrador**

Descripción de los flujos del diagrama de contexto:

| Flujo | Origen | Destino | Descripción |
|---|---|---|---|
| Datos del paciente | Secretaria | SGCM | Nombre, cédula, teléfono, dirección y datos de contacto para registro. |
| Solicitud de cita | Secretaria | SGCM | Identificador del paciente, identificador del médico, fecha, hora y motivo de consulta. |
| Modificación de cita | Secretaria | SGCM | Identificador de cita existente, nueva fecha y nueva hora seleccionada. |
| Cancelación de cita | Secretaria | SGCM | Identificador de la cita a cancelar y confirmación del usuario. |
| Confirmación de cita | SGCM | Secretaria | Identificador de cita asignado, datos del médico, fecha, hora y estado. |
| Reporte PDF | SGCM | Secretaria / Administrador | Archivo PDF con listado de citas del período seleccionado. |
| Disponibilidad médica | SGCM | Secretaria | Horarios disponibles del médico visualizados en FullCalendar.js. |
| Consulta de agenda | Médico | SGCM | Período de consulta solicitado (día o semana). |
| Agenda actualizada | SGCM | Médico | Lista de citas ordenadas cronológicamente con datos del paciente. |
| Registro de observaciones | Médico | SGCM | Identificador de cita y texto de observaciones clínicas básicas. |
| Gestión de usuarios | Administrador | SGCM | Crear, editar, activar o desactivar usuarios y asignar roles. |
| Consulta de auditoría | Administrador | SGCM | Filtros por usuario, tipo de acción, fecha y tabla afectada. |
| Registro de auditoría | SGCM | Administrador | Log completo de operaciones con usuario, acción, tabla y marca temporal. |

*Nota.* Elaboración propia (2026).

### 4.4.2. Diagrama General (DFD Nivel 1)

El DFD de Nivel 1 descompone el sistema en sus cuatro procesos principales, mostrando los flujos de datos entre ellos y los almacenes de datos. Los procesos son P1 Autenticación y Seguridad, P2 Gestión de Citas y Pacientes, P3 Gestión de Médicos y Disponibilidad, y P4 Generación de Reportes PDF.

*Figura 2.* Diagrama general de flujo de datos del SGCM.

- **Entidades externas**: Secretaria, Médico, Administrador.
- **P1. Autenticación y Seguridad**: valida credenciales, emite token JWT, aplica RBAC.
- **P2. Gestión de Citas y Pacientes**: registro, consulta, modificación y cancelación de citas. Operaciones sobre pacientes.
- **P3. Gestión de Médicos y Disponibilidad**: administra horarios de médicos y retorna disponibilidad en tiempo real.
- **P4. Generación de Reportes PDF**: filtra datos, renderiza HTML y convierte a PDF con WeasyPrint.

Almacenes de datos del sistema:

| Almacén | Tabla PostgreSQL | Descripción del contenido |
|---|---|---|
| A1 — Usuarios | usuarios | Credenciales, roles y estado de acceso de todos los usuarios del sistema. |
| A2 — Pacientes | pacientes | Datos personales: cédula, nombre, apellidos, fecha de nacimiento, teléfono, dirección. |
| A3 — Médicos y horarios | medicos, horarios | Datos del médico (nombre, especialidad) y bloques de disponibilidad por día y hora. |
| A4 — Citas | citas | Registro completo: paciente, médico, fecha, hora, estado y motivo de consulta. |
| A5 — Consultas | consultas | Observaciones clínicas básicas registradas por el médico al atender cada cita. |
| A6 — Auditoría | auditoria | Registro automático de todas las operaciones: usuario, acción, tabla, marca temporal e IP. |

*Nota.* Elaboración propia (2026).

### 4.4.3. Diagrama de Nivel 1: detalle del proceso P2

Este diagrama descompone el proceso P2 en sus cinco subprocesos constitutivos, que representan el núcleo funcional del sistema.

*Figura 3.* Subprocesos del proceso P2 de gestión de citas y pacientes.

- **P2.1 Buscar o Registrar Paciente**: busca en A2 y, si no existe, registra con validación de cédula única.
- **P2.2 Consultar Disponibilidad Médica**: envía solicitud a P3 y recibe los horarios libres para FullCalendar.js.
- **P2.3 Registrar Nueva Cita**: valida unicidad de la combinación médico, fecha y hora, e inserta el registro en A4.
- **P2.4 Modificar o Cancelar Cita**: actualiza fecha y hora o cambia el estado a cancelada, liberando el horario correspondiente.
- **P2.5 Consultar Citas**: filtra A4 por paciente, médico, fecha o estado y retorna el listado solicitado.

*Nota.* Elaboración propia (2026). El subproceso P2.3 se apoya en el índice único parcial sobre (id_medico, fecha, hora) con la condición de estado distinto de cancelada para prevenir duplicaciones.

## 4.5. Diagrama de Casos de Uso

El diagrama de casos de uso describe las interacciones entre los actores del sistema y las funcionalidades disponibles según su rol. Los tres actores son Secretaria, Médico y Administrador. El Administrador es una generalización que hereda todas las capacidades de la Secretaria y añade las funciones de gestión de usuarios, médicos y auditoría.

*Figura 4.* Diagrama de casos de uso del SGCM.

| Actor | ID | Caso de uso | Descripción del flujo normal |
|---|---|---|---|
| Todos | CU-01 | Iniciar sesión | El usuario ingresa correo y contraseña, el sistema valida las credenciales, emite un token JWT y redirige al panel correspondiente a su rol. |
| Todos | CU-02 | Cerrar sesión | El usuario finaliza la sesión; el sistema invalida el token JWT activo. |
| Secretaria | CU-03 | Registrar paciente | La secretaria completa el formulario; el sistema valida la cédula y guarda el registro. |
| Secretaria | CU-04 | Buscar paciente | La secretaria ingresa nombre o cédula y el sistema filtra los resultados en tiempo real. |
| Secretaria | CU-05 | Editar paciente | La secretaria selecciona un registro, edita los campos y el sistema valida y actualiza. |
| Secretaria | CU-06 | Agendar cita | La secretaria selecciona paciente y médico; el calendario muestra la disponibilidad; selecciona el horario y confirma. |
| Secretaria | CU-07 | Reprogramar cita | La secretaria busca la cita, selecciona un nuevo horario disponible y el sistema libera el anterior y reserva el nuevo. |
| Secretaria | CU-08 | Cancelar cita | La secretaria selecciona la cita y confirma la cancelación; el estado se actualiza y el horario queda libre para reutilización. |
| Secretaria | CU-09 | Consultar citas | La secretaria aplica filtros por paciente, médico, fecha o estado y el sistema retorna el listado. |
| Secretaria | CU-10 | Generar reporte PDF | La secretaria selecciona tipo y período; el sistema genera el PDF mediante WeasyPrint y lo descarga automáticamente. |
| Médico | CU-11 | Ver agenda diaria | El médico accede al panel y el sistema muestra sus citas del día ordenadas por hora. |
| Médico | CU-12 | Registrar observaciones | El médico selecciona una cita, ingresa las observaciones y el estado cambia a atendida. |
| Administrador | CU-13 | Gestionar usuarios | El administrador crea, edita, activa o desactiva usuarios y asigna roles. |
| Administrador | CU-14 | Registrar médico | El administrador registra datos del médico y configura sus bloques de disponibilidad. |
| Administrador | CU-15 | Consultar auditoría | El administrador aplica filtros y visualiza el log completo de operaciones del sistema. |

*Nota.* Elaboración propia (2026).

---

# CAPÍTULO V: DISEÑO DEL SISTEMA

## 5.1. Diagrama Entidad-Relación

El Modelo Entidad-Relación es una representación gráfica de las entidades que conforman la base de datos, sus atributos y las relaciones semánticas entre ellas (Chen, 1976). A continuación se describe la estructura del modelo.

*Figura 5.* Diagrama Entidad-Relación del SGCM.

- **Usuarios**: id (PK), nombre, email (único), password_hash, rol, activo, fecha_creacion.
- **Médicos**: id (PK), id_usuario (FK → usuarios), nombre, especialidad, telefono, activo.
- **Horarios**: id (PK), id_medico (FK → medicos), dia_semana, hora_inicio, hora_fin, activo.
- **Pacientes**: id (PK), cedula (único), nombre, apellidos, fecha_nacimiento, telefono, direccion, fecha_registro.
- **Citas**: id (PK), id_paciente (FK), id_medico (FK), fecha, hora, estado, motivo, id_secretaria (FK), fecha_registro.
- **Consultas**: id (PK), id_cita (FK → citas, único), observaciones, fecha_registro.
- **Auditoría**: id (PK), id_usuario (FK → usuarios), accion, tabla_afectada, id_registro, detalle, fecha_hora, ip_origen.

*Nota.* Elaboración propia (2026). Las claves foráneas implementan la integridad referencial. La restricción de unicidad sobre la tabla citas es la pieza técnica central que previene el problema de duplicación de citas identificado en el diagnóstico.

### 5.1.1. Descripción de cardinalidades

| Entidad A | Cardinalidad | Entidad B | Descripción de la relación |
|---|---|---|---|
| Usuario | 1 : 1 (opcional) | Médico | Un usuario del sistema puede estar asociado a un perfil de médico. |
| Médico | 1 : N | Horario | Un médico puede tener múltiples bloques de disponibilidad registrados. |
| Médico | 1 : N | Cita | Un médico puede recibir múltiples citas asignadas. |
| Paciente | 1 : N | Cita | Un paciente puede tener múltiples citas registradas en el tiempo. |
| Usuario (secretaria) | 1 : N | Cita | Una secretaria puede crear múltiples citas. |
| Cita | 1 : 1 (opcional) | Consulta | Una cita atendida puede tener como máximo una nota de consulta. |
| Usuario | 1 : N | Auditoría | Un usuario puede generar múltiples registros de auditoría. |

*Nota.* Elaboración propia (2026).

## 5.2. Diseño de la base de datos

A continuación se presenta el diseño de las siete tablas que conforman la base de datos del SGCM, con sus columnas, tipos de datos y restricciones.

### Tabla: usuarios

Descripción: almacena los datos de acceso al sistema de todos los usuarios registrados. Clave primaria: id.

| Columna | Descripción | Tipo y tamaño | Nulo | Default |
|---|---|---|---|---|
| id | Identificador único autogenerado del usuario | serial | No | Auto |
| nombre | Nombre completo del usuario | varchar(100) | No | — |
| email | Correo electrónico utilizado como nombre de usuario (único) | varchar(100) | No | — |
| password_hash | Hash de la contraseña generado con bcrypt | varchar(255) | No | — |
| rol | Rol del usuario: secretaria, medico o admin | varchar(20) | No | — |
| activo | Indica si el usuario tiene acceso habilitado | boolean | No | true |
| fecha_creacion | Fecha y hora de creación del registro | timestamp | No | NOW() |

*Nota.* Elaboración propia (2026).

### Tabla: pacientes

Descripción: almacena los datos básicos de los pacientes registrados en el hospital. Clave primaria: id.

| Columna | Descripción | Tipo y tamaño | Nulo | Default |
|---|---|---|---|---|
| id | Identificador único autogenerado del paciente | serial | No | Auto |
| cedula | Número de cédula de identidad (único en el sistema) | varchar(13) | No | — |
| nombre | Nombre del paciente | varchar(100) | No | — |
| apellidos | Apellidos del paciente | varchar(100) | No | — |
| fecha_nacimiento | Fecha de nacimiento del paciente | date | Sí | NULL |
| telefono | Número de teléfono de contacto | varchar(15) | No | — |
| direccion | Dirección de residencia | text | Sí | NULL |
| fecha_registro | Fecha y hora de registro en el sistema | timestamp | No | NOW() |

*Nota.* Elaboración propia (2026).

### Tabla: medicos

Descripción: almacena los datos del personal médico del hospital. Clave primaria: id.

| Columna | Descripción | Tipo y tamaño | Nulo | Default |
|---|---|---|---|---|
| id | Identificador único autogenerado del médico | serial | No | Auto |
| id_usuario | Referencia al registro de usuario asociado | integer (FK) | No | — |
| nombre | Nombre completo del médico | varchar(100) | No | — |
| especialidad | Especialidad médica del doctor | varchar(50) | No | — |
| telefono | Teléfono de contacto del médico | varchar(15) | Sí | NULL |
| activo | Indica si el médico está activo en el sistema | boolean | No | true |

*Nota.* Elaboración propia (2026).

### Tabla: horarios

Descripción: bloques de disponibilidad horaria de cada médico para asignación de citas. Clave primaria: id.

| Columna | Descripción | Tipo y tamaño | Nulo | Default |
|---|---|---|---|---|
| id | Identificador único autogenerado | serial | No | Auto |
| id_medico | Referencia al médico al que pertenece el horario | integer (FK) | No | — |
| dia_semana | Día de la semana: 1 lunes, 7 domingo | smallint | No | — |
| hora_inicio | Hora de inicio del bloque de disponibilidad | time | No | — |
| hora_fin | Hora de fin del bloque de disponibilidad | time | No | — |
| activo | Indica si este bloque está habilitado actualmente | boolean | No | true |

*Nota.* Elaboración propia (2026).

### Tabla: citas

Descripción: registros de todas las citas médicas agendadas en el sistema. Clave primaria: id.

| Columna | Descripción | Tipo y tamaño | Nulo | Default |
|---|---|---|---|---|
| id | Identificador único autogenerado de la cita | serial | No | Auto |
| id_paciente | Referencia al registro del paciente | integer (FK) | No | — |
| id_medico | Referencia al médico asignado a la cita | integer (FK) | No | — |
| fecha | Fecha de la cita médica | date | No | — |
| hora | Hora de inicio de la cita | time | No | — |
| estado | Estado: pendiente, atendida o cancelada | varchar(20) | No | 'pendiente' |
| motivo | Motivo de la consulta ingresado por la secretaria | text | Sí | NULL |
| id_secretaria | Referencia al usuario que registró la cita | integer (FK) | No | — |
| fecha_registro | Fecha y hora de creación del registro | timestamp | No | NOW() |

Restricción clave: se aplica un índice único parcial sobre la combinación (id_medico, fecha, hora) con la condición de que el estado sea distinto de cancelada. Esta decisión de diseño resuelve la tensión entre dos requisitos: por una parte, garantizar que no existan dos citas activas para el mismo médico en el mismo horario; por otra, permitir que un horario cancelado pueda ser reutilizado por una nueva cita, dando soporte a los casos de uso CU-07 (Reprogramar cita) y CU-08 (Cancelar cita). La implementación emplea la cláusula WHERE del DDL de PostgreSQL, de modo que la restricción no considera los registros con estado cancelada al evaluar la unicidad.

*Nota.* Elaboración propia (2026).

### Tabla: consultas

Descripción: observaciones registradas por los médicos al atender cada consulta. Clave primaria: id.

| Columna | Descripción | Tipo y tamaño | Nulo | Default |
|---|---|---|---|---|
| id | Identificador único autogenerado | serial | No | Auto |
| id_cita | Referencia a la cita médica correspondiente (único) | integer (FK) | No | — |
| observaciones | Notas clínicas básicas del médico durante la consulta | text | No | — |
| fecha_registro | Fecha y hora de registro de las observaciones | timestamp | No | NOW() |

*Nota.* Elaboración propia (2026).

### Tabla: auditoria

Descripción: registro automático de cada operación realizada en el sistema. Clave primaria: id.

| Columna | Descripción | Tipo y tamaño | Nulo | Default |
|---|---|---|---|---|
| id | Identificador único autogenerado | serial | No | Auto |
| id_usuario | Referencia al usuario que realizó la operación | integer (FK) | No | — |
| accion | Tipo de acción: CREATE, UPDATE, DELETE o LOGIN | varchar(20) | No | — |
| tabla_afectada | Nombre de la tabla sobre la que se realizó la operación | varchar(50) | No | — |
| id_registro | Identificador del registro afectado por la operación | integer | Sí | NULL |
| detalle | Información adicional sobre la operación | text | Sí | NULL |
| fecha_hora | Fecha y hora exacta de la operación | timestamp | No | NOW() |
| ip_origen | Dirección IP del cliente desde donde se realizó la operación | varchar(45) | Sí | NULL |

*Nota.* Elaboración propia (2026).

## 5.3. Índice único parcial sobre la tabla de citas

El diseño del sistema incorpora un índice único parcial como pieza central de la integridad del proceso de agendamiento. Este índice se define sobre las columnas id_medico, fecha y hora de la tabla citas, condicionado a que el estado sea distinto de cancelada. Esta característica, soportada de manera nativa por PostgreSQL, permite resolver simultáneamente dos requisitos aparentemente contradictorios: evitar que existan dos citas activas simultáneas para el mismo médico, y permitir que un horario previamente ocupado por una cita cancelada pueda volver a utilizarse para agendar una nueva cita.

La lógica de negocio del sistema aprovecha esta restricción delegando en la base de datos la validación final de unicidad, de manera que incluso en condiciones de concurrencia el sistema responde de forma determinista. Cuando una petición intenta registrar una cita sobre un horario ya ocupado por otra cita activa, PostgreSQL devuelve un error de violación de unicidad que el backend traduce en una respuesta HTTP con el código de error E-005 del sistema. Esta estrategia elimina la necesidad de bloqueos explícitos y garantiza la consistencia del almacenamiento aun cuando múltiples secretarias operen simultáneamente.

## 5.4. VTOC: estructura modular del sistema

La estructura modular del sistema se organiza en los siguientes componentes funcionales:

- Módulo de autenticación y seguridad: inicio de sesión, emisión y validación de tokens JWT, cierre de sesión y aplicación de RBAC.
- Módulo de pacientes: registro, búsqueda, edición y eliminación de pacientes, con validación de cédula dominicana.
- Módulo de médicos: registro y gestión de médicos y administración de bloques de disponibilidad.
- Módulo de citas: registro de nueva cita con FullCalendar.js, reprogramación, cancelación y visualización en calendario.
- Módulo de consulta médica: agenda diaria del médico y registro de observaciones de cada cita atendida.
- Módulo de reportes: generación de reportes diarios, semanales y por médico en formato PDF.
- Módulo de administración: gestión de usuarios, asignación de roles y consulta de auditoría.
- Módulo de auditoría transaccional: registro automático de todas las operaciones críticas en la tabla de auditoría, con ejecución dentro de la misma transacción que la operación que las origina.

## 5.5. Arquitectura de control de acceso en dos capas

El sistema implementa el control de acceso basado en roles en dos capas complementarias.

En la capa de backend, cada endpoint protegido de la API declara mediante dependencias de FastAPI los roles autorizados para ejecutarlo. Las peticiones recibidas son validadas extrayendo el token JWT del encabezado de autorización, verificando su firma y vigencia, y contrastando el rol incluido en el *payload* contra los roles permitidos para la ruta invocada. Las peticiones con credenciales ausentes, inválidas o con un rol no autorizado son rechazadas con los códigos HTTP 401 o 403, según corresponda, y la denegación queda registrada en la tabla de auditoría cuando aplica.

En la capa de frontend, la interfaz adapta dinámicamente los elementos visibles al rol del usuario autenticado. Los elementos HTML susceptibles de mostrar u ocultar declaran un atributo *data-role* con el perfil requerido para su visualización, y una función JavaScript central recorre estos elementos tras autenticar al usuario, ajustando su visibilidad. Este mecanismo garantiza, por ejemplo, que el enlace de navegación hacia la pantalla de auditoría solo sea visible al administrador, que el formulario de alta de médicos permanezca oculto para los perfiles de secretaria y médico, y que los botones de edición y eliminación de la tabla de pacientes se muestren únicamente al personal administrativo.

Es importante enfatizar que la capa de frontend no constituye una barrera de seguridad, sino una mejora de la experiencia de uso. La verdadera autorización reside en el backend, que valida cada petición independientemente del estado visual del cliente. El propósito del control de acceso en el frontend es evitar confusión al usuario y eliminar controles que, aunque bloqueados por el servidor, generarían una mala experiencia si estuvieran visibles.

## 5.6. Auditoría transaccional

La auditoría del sistema se implementa bajo un esquema transaccional: cada operación crítica (creación, modificación o eliminación de registros en las tablas de dominio, así como los inicios de sesión) genera un registro en la tabla de auditoría que se inserta en la misma transacción de base de datos que la operación principal. De este modo, si la operación principal falla y se revierte mediante *rollback*, el registro de auditoría correspondiente también se descarta, evitando que queden registros huérfanos que describan acciones que no ocurrieron realmente.

Esta estrategia se complementa con la captura automática de información contextual relevante: el identificador del usuario autenticado, la dirección IP de origen extraída del encabezado HTTP, la marca temporal exacta y una descripción textual de la operación. Las pruebas automatizadas del sistema verifican tanto la creación correcta de los registros de auditoría en flujos exitosos, como la ausencia de registros cuando la operación principal falla.

## 5.7. Descripción de errores del sistema

| Código | Mensaje al usuario | Causa técnica |
|---|---|---|
| E-001 | Usuario o contraseña incorrectos. Verifique sus credenciales. | Credenciales inválidas; mensaje genérico ante posible enumeración. |
| E-002 | Su sesión ha expirado. Por favor, inicie sesión nuevamente. | Token JWT caducado. |
| E-003 | No tiene permisos para realizar esta acción. | El rol del usuario no autoriza la operación (HTTP 403). |
| E-004 | El paciente solicitado no existe en el sistema. | Búsqueda por identificador inexistente (HTTP 404). |
| E-005 | Horario ocupado. Seleccione otro horario disponible. | Violación del índice único parcial sobre (id_medico, fecha, hora). |
| E-006 | Complete todos los campos obligatorios correctamente. | Validación de esquema Pydantic fallida (HTTP 422). |
| E-007 | La cédula ingresada ya está registrada en el sistema. | Violación de unicidad en cedula (tabla pacientes). |
| E-008 | No se puede eliminar: registro referenciado por otros datos. | Violación de integridad referencial (clave foránea activa). |
| E-010 | Error inesperado. Contacte al administrador del sistema. | Error interno del servidor (HTTP 500, registrado en logs). |

*Nota.* Todos los errores HTTP 500 son registrados automáticamente en los logs del sistema. Elaboración propia (2026).

---

# CAPÍTULO VI: METODOLOGÍA DE DESARROLLO

## 6.1. Tipo de investigación

Este proyecto se clasifica como investigación aplicada de enfoque mixto. La investigación aplicada tiene como objetivo resolver un problema concreto mediante la aplicación de conocimientos existentes (Hernández et al., 2014). El enfoque mixto combina técnicas cualitativas (entrevistas, observaciones) y cuantitativas (cuestionarios, análisis de datos).

## 6.2. Metodología de desarrollo

Para el desarrollo del sistema se adoptó un enfoque de desarrollo iterativo incremental con ciclos de dos semanas, inspirado en los principios del Manifiesto Ágil (Beck et al., 2001). Cada iteración entrega un incremento funcional del sistema, permite la retroalimentación temprana del personal del hospital y se adapta a cambios en los requisitos sin comprometer la calidad del producto final. Este enfoque es más apropiado que Scrum puro para un equipo de dos personas, dado que Scrum está diseñado para equipos de tres a nueve integrantes (Schwaber y Sutherland, 2020).

## 6.3. Herramientas y tecnologías

| Componente | Tecnología | Versión | Función en el sistema |
|---|---|---|---|
| Backend | Python | 3.11+ | Lenguaje de programación principal. |
| Backend | FastAPI | 0.110+ | Framework para la API REST con documentación automática. |
| Backend | SQLModel | 0.0.16+ | ORM que integra SQLAlchemy y Pydantic. |
| Backend | Alembic | 1.13+ | Control de versiones del esquema de base de datos. |
| Backend | python-jose | 3.3+ | Generación y validación de tokens JWT. |
| Backend | passlib (bcrypt) | 1.7+ | Hashing seguro de contraseñas con bcrypt. |
| Backend | WeasyPrint | 61+ | Conversión de HTML a PDF para reportes. |
| Backend | pytest + httpx | 7.4+ | Pruebas unitarias y de integración de la API. |
| Base de datos | PostgreSQL | 15+ | Sistema gestor de base de datos relacional. |
| Frontend | HTML5 + JavaScript ES6 | — | Estructura e interactividad de la interfaz. |
| Frontend | Tailwind CSS (CDN) | 3.4+ | Estilos visuales de la interfaz de usuario. |
| Frontend | FullCalendar.js | 6.1+ | Calendario interactivo de disponibilidad médica. |
| Infraestructura | Docker Engine | 24+ | Contenedorización de la aplicación. |
| Infraestructura | Docker Compose | 2.20+ | Orquestación de los contenedores del sistema. |
| Infraestructura | Nginx | 1.25+ | Proxy inverso y terminación HTTPS con SSL. |
| Infraestructura | mkcert | 1.4+ | Generación de certificado SSL para intranet. |
| Infraestructura | Git | 2.30+ | Control de versiones del código fuente. |
| Integración continua | GitHub Actions | — | Ejecución automática de pruebas, análisis estático y verificación de construcción Docker en cada envío de código. |

*Nota.* Elaboración propia (2026). Todo el software listado es de código abierto y gratuito.

## 6.4. Estrategia de pruebas automatizadas

El sistema incorpora una suite de pruebas automatizadas construida con pytest que cubre los quince casos de uso definidos. La estrategia de pruebas se apoya en dos mecanismos técnicos principales. En primer lugar, se emplea una base de datos SQLite en memoria, configurada mediante la clase StaticPool de SQLAlchemy, que permite ejecutar cada prueba contra un esquema limpio sin dependencia de infraestructura externa y con tiempos de ejecución inferiores a los que ofrecería PostgreSQL en cada prueba. En segundo lugar, se utilizan *fixtures* de pytest que preparan el contexto necesario para cada prueba: un cliente HTTP de pruebas, sesiones de base de datos y funciones auxiliares que simulan el inicio de sesión con cada uno de los roles del sistema.

Las pruebas abarcan los flujos normales y alternos de cada caso de uso, las validaciones de cédula dominicana, las restricciones de unicidad, la correcta generación de registros de auditoría, el comportamiento transaccional (verificando que un error en la operación principal impide que quede un registro de auditoría huérfano) y la generación de reportes PDF. La totalidad de la suite se ejecuta de manera automatizada en cada envío al repositorio a través del flujo de integración continua descrito en la sección siguiente.

## 6.5. Integración continua con GitHub Actions

El proyecto cuenta con un flujo de integración continua configurado en el archivo de *workflow* de GitHub Actions, que se dispara ante cada envío de código a las ramas principales del repositorio y ante cada solicitud de incorporación de cambios. El flujo está compuesto por dos trabajos que se ejecutan en paralelo sobre runners con sistema operativo Ubuntu.

El primer trabajo, denominado *Tests + Lint*, instala el intérprete de Python, las dependencias de sistema requeridas por WeasyPrint, las dependencias del proyecto declaradas en el archivo requirements.txt y, finalmente, ejecuta el análisis estático del código mediante el linter ruff y la suite completa de pruebas pytest. Para garantizar un entorno realista, este trabajo arranca un servicio PostgreSQL como contenedor auxiliar. Para asegurar la reproducibilidad de las pruebas de generación de PDF se fijan explícitamente las versiones de las dependencias críticas WeasyPrint y pydyf, evitando incompatibilidades derivadas de actualizaciones automáticas.

El segundo trabajo, denominado *Verifica que la imagen Docker compila*, construye la imagen Docker completa del sistema utilizando el mismo Dockerfile empleado en producción, validando que cualquier modificación del código o de las dependencias mantiene un artefacto desplegable.

La disciplina de integración continua se complementa con una convención de mensajes de *commit* basada en el estándar *Conventional Commits*, que clasifica los cambios en categorías como *feat* para nuevas funcionalidades, *fix* para correcciones, *docs* para documentación, *refactor* para reestructuración interna y *test* para modificaciones exclusivas de la suite de pruebas. Esta convención permite generar automáticamente notas de versión y facilita la trazabilidad histórica del proyecto.

## 6.6. Cronograma de actividades

| Fase | Descripción | Inicio | Fin | Días |
|---|---|---|---|---|
| 1 | Análisis y levantamiento de requisitos | 15/04/2026 | 21/04/2026 | 5 |
| 2 | Diseño: MER, DFD, casos de uso y prototipos de UI | 22/04/2026 | 05/05/2026 | 10 |
| 3 | Iteración 1: módulo de pacientes y autenticación con JWT/RBAC | 06/05/2026 | 19/05/2026 | 10 |
| 4 | Iteración 2: módulo de citas con FullCalendar.js | 20/05/2026 | 02/06/2026 | 10 |
| 5 | Iteración 3: módulo médico y reportes PDF con WeasyPrint | 03/06/2026 | 16/06/2026 | 10 |
| 6 | Seguridad: Nginx con HTTPS, Alembic, auditoría y respaldos | 17/06/2026 | 26/06/2026 | 8 |
| 7 | Pruebas automatizadas (pytest) y pruebas de usuario | 01/07/2026 | 10/07/2026 | 8 |
| 8 | Despliegue en intranet del hospital (Docker) | 15/07/2026 | 21/07/2026 | 5 |
| 9 | Capacitación del personal y ajustes posteriores a la implementación | 22/07/2026 | 11/08/2026 | 15 |
| 10 | Cierre del proyecto y entrega del documento final | 11/08/2026 | 15/08/2026 | 5 |
| 11 | Contingencias y correcciones finales | 18/08/2026 | 27/08/2026 | 8 |
| **Total** | | 15/04/2026 | 27/08/2026 | **97 días hábiles** |

*Nota.* Todas las fechas corresponden al año 2026, en coherencia con la fecha de presentación indicada en la portada. Elaboración propia (2026).

## 6.7. Requerimientos de hardware

Servidor de la intranet del hospital:

| Componente | Mínimo | Recomendado |
|---|---|---|
| Procesador | Intel Core i5 8.ª generación / AMD Ryzen 5 | Intel Core i7 / AMD Ryzen 7 |
| Memoria RAM | 8 GB DDR4 | 16 GB DDR4 |
| Almacenamiento | 256 GB SSD | 512 GB SSD |
| Sistema operativo | Ubuntu Server 20.04 LTS | Ubuntu Server 22.04 LTS |
| Red | Ethernet 100 Mbps | Ethernet 1 Gbps |

*Nota.* El servidor debe permanecer encendido durante todo el horario laboral del hospital. Elaboración propia (2026).

---

## Conclusión

El desarrollo e implementación del Sistema Web de Gestión de Citas Médicas para el Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch representa una solución tecnológica concreta y fundamentada a una problemática real que afecta la eficiencia operativa de la institución y la calidad del servicio brindado a los pacientes de La Vega y sus alrededores.

El sistema centraliza el proceso de agendamiento mediante una interfaz intuitiva que reduce el tiempo de registro de citas de entre diez y veinte minutos a menos de cinco minutos. El índice único parcial implementado en la base de datos PostgreSQL elimina físicamente la posibilidad de citas duplicadas en horarios activos, que constituía el principal problema operativo identificado en el diagnóstico, y al mismo tiempo permite la reutilización de horarios liberados por cancelación, soportando los flujos completos de reprogramación. El calendario interactivo FullCalendar.js permite a las secretarias visualizar la disponibilidad de los médicos en tiempo real, sin necesidad de comunicación telefónica.

Desde la perspectiva de la seguridad, el sistema implementa control de acceso basado en roles en dos capas complementarias (backend y frontend), hashing de contraseñas con bcrypt, comunicación cifrada HTTPS a través de Nginx, y auditoría transaccional de todas las operaciones críticas, en plena conformidad con la Ley 172-13. El módulo de generación de reportes PDF mediante WeasyPrint elimina el proceso de elaboración manual mensual, proporcionando datos actualizados para la toma de decisiones administrativas.

La adopción de una suite de pruebas automatizadas y de un flujo de integración continua con GitHub Actions asegura que cada cambio del código fuente sea validado antes de su incorporación al repositorio principal, reduciendo el riesgo de regresiones y elevando la calidad del software a estándares profesionales.

El proyecto demuestra que es posible desarrollar una solución digital robusta para el sector salud público dominicano utilizando exclusivamente tecnologías de código abierto, alineada con la misión del HTQPJB de brindar servicios con calidad y humanizados, y con su visión de alcanzar la excelencia en la prestación de servicios traumatológicos y quirúrgicos.

---

## Recomendaciones

- Mantener actualizados el software y sus componentes de forma periódica, dado que las actualizaciones incorporan correcciones de seguridad y mejoras de rendimiento.
- Verificar mensualmente que el proceso de respaldo automático (pg_dump más tareas programadas) esté funcionando correctamente, revisando los registros correspondientes.
- Revisar periódicamente los roles asignados a cada usuario desde el módulo de administración, garantizando el principio de mínimo privilegio.
- Realizar sesiones de capacitación con el personal cada vez que se incorporen nuevos empleados al área de Consulta Externa, y mantener material de apoyo actualizado.
- Evaluar en el mediano plazo la integración del sistema con un módulo de expediente clínico electrónico, eliminando progresivamente el expediente físico del paciente.
- Implementar en una versión futura un módulo de notificaciones automáticas por mensaje de texto o correo electrónico para reducir las ausencias y cancelaciones tardías.
- Realizar una auditoría de seguridad del sistema a los seis meses de su implementación, incluyendo pruebas de penetración y revisión de los registros de auditoría.
- Establecer un canal formal de soporte técnico durante los primeros seis meses de operación para atender dudas, incidencias y sugerencias del personal usuario.
- Documentar los procedimientos operativos estándar derivados del uso del sistema para formalizar los flujos de trabajo del área de Consulta Externa.
- Considerar la implementación de un *dashboard* de métricas e indicadores de gestión (citas por día, tasa de ausentismo, tiempo promedio de atención) para apoyar la toma de decisiones directivas.

---

## Bibliografía

American Psychological Association. (2020). *Publication manual of the American Psychological Association* (7.ª ed.). https://doi.org/10.1037/0000165-000

Babbie, E. (2016). *The practice of social research* (14.ª ed.). Cengage Learning.

Bayer, M. (2023). *Alembic documentation*. https://alembic.sqlalchemy.org

Beck, K., Beedle, M., van Bennekum, A., Cockburn, A., Cunningham, W., Fowler, M., Grenning, J., Highsmith, J., Hunt, A., Jeffries, R., Kern, J., Marick, B., Martin, R. C., Mellor, S., Schwaber, K., Sutherland, J., y Thomas, D. (2001). *Manifesto for agile software development*. https://agilemanifesto.org

Cerner Corporation. (2022). *Cerner health information technology*. https://www.cerner.com

Chen, P. P.-S. (1976). The entity-relationship model: Toward a unified view of data. *ACM Transactions on Database Systems, 1*(1), 9–36. https://doi.org/10.1145/320434.320440

Comprés, R., y Familia, M. (2020). *Módulo de gestión de citas del Hospital General Plaza de la Salud* [Informe técnico]. Hospital General Plaza de la Salud.

Creswell, J. W. (2014). *Research design: Qualitative, quantitative, and mixed methods approaches* (4.ª ed.). SAGE Publications.

Docker Inc. (2023). *Docker documentation*. https://docs.docker.com

Duvall, P., Matyas, S., y Glover, A. (2007). *Continuous integration: Improving software quality and reducing risk*. Addison-Wesley.

Epic Systems Corporation. (2023). *Epic: Healthcare software*. https://www.epic.com

Fontana, A., y Frey, J. H. (2018). The interview: From structured questions to negotiated text. En N. K. Denzin y Y. S. Lincoln (Eds.), *Collecting and interpreting qualitative materials* (5.ª ed., pp. 113–167). SAGE Publications.

Fraenkel, J. R., y Wallen, N. E. (2014). *How to design and evaluate research in education* (8.ª ed.). McGraw-Hill.

FullCalendar LLC. (2023). *FullCalendar documentation*. https://fullcalendar.io/docs

García, M., y Pérez, R. (2020). *Sistema de agendamiento médico en línea para la red hospitalaria del IMSS* [Informe técnico]. Instituto Mexicano del Seguro Social.

GitHub Inc. (2024). *GitHub Actions documentation*. https://docs.github.com/actions

Gómez, L. (2007). *Bases de datos relacionales: Teoría y práctica*. McGraw-Hill.

Hernández, R., Fernández, C., y Baptista, P. (2014). *Metodología de la investigación* (6.ª ed.). McGraw-Hill.

Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch. (2022). *¿Quiénes somos?* https://hospitaljuanbosch.gob.do/quienes-somos-2/

Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch. (2022). *Historia*. https://hospitaljuanbosch.gob.do/historia/

ISO/IEC 27001. (2022). *Information security, cybersecurity and privacy protection: Information security management systems — Requirements*. International Organization for Standardization.

Krekel, H., Oliveira, B., y Pfannschmidt, R. (2023). *Pytest documentation*. https://docs.pytest.org

Martínez, A., y Rodríguez, P. (2019). *Diseño e implementación de un sistema de gestión de citas para el Hospital Universitario de Navarra* [Informe técnico]. Ministerio de Sanidad de España.

Méndez, C., y Santos, R. (2022). *Sistema de información para la gestión de citas del Centro de Diagnóstico de Imágenes* [Trabajo de grado, Universidad APEC]. Repositorio institucional UNAPEC.

Nginx Inc. (2023). *Nginx documentation*. https://nginx.org/en/docs/

Organización Mundial de la Salud. (2021). *Global strategy on digital health 2020-2025*. https://www.who.int/docs/default-source/documents/gs4dhdaa2a9f352b0445bafbc79ca799dce4d.pdf

PostgreSQL Global Development Group. (2023). *PostgreSQL 15 documentation*. https://www.postgresql.org/docs/15/

Pressman, R. S., y Maxim, B. R. (2020). *Software engineering: A practitioner's approach* (9.ª ed.). McGraw-Hill.

Ramírez, C., Fuentes, P., y Lagos, M. (2021). *Implementación de un sistema web de gestión hospitalaria en el Hospital Clínico de Chile* [Informe técnico]. Universidad de Chile.

Ramírez, S. (2023a). *FastAPI documentation*. https://fastapi.tiangolo.com

Ramírez, S. (2023b). *SQLModel documentation*. https://sqlmodel.tiangolo.com

República Dominicana. (2013). *Ley 172-13 sobre Protección de Datos de Carácter Personal*. Congreso Nacional.

Schwaber, K., y Sutherland, J. (2020). *The Scrum guide: The definitive guide to Scrum*. https://www.scrumguides.org/scrum-guide.html

Sommerville, I. (2016). *Software engineering* (10.ª ed.). Pearson.

Van Rossum, G., y Drake, F. L. (2023). *Python 3.11 reference manual*. Python Software Foundation. https://docs.python.org/3.11/

Wathan, A. (2023). *Tailwind CSS documentation*. https://tailwindcss.com/docs

WeasyPrint Team. (2023). *WeasyPrint documentation*. https://doc.courtbouillon.org/weasyprint/stable/

---

## Glosario de términos

| Término | Definición |
|---|---|
| Alembic | Herramienta de control de versiones para esquemas de bases de datos SQLAlchemy/SQLModel. Genera scripts de migración versionados. |
| API REST | Interfaz de programación que sigue los principios REST (*Representational State Transfer*), usando HTTP para la comunicación cliente-servidor. |
| Auditoría transaccional | Registro de operaciones que comparte la misma transacción de base de datos con la operación que las origina, garantizando que logs y cambios de datos sean consistentes. |
| Bcrypt | Algoritmo de hashing unidireccional para almacenamiento seguro de contraseñas. Incorpora un factor de costo configurable para resistir ataques de fuerza bruta. |
| CRUD | *Create, Read, Update, Delete*: las cuatro operaciones básicas de gestión de datos en un sistema de información. |
| DFD | Diagrama de Flujo de Datos. Representación gráfica del flujo de información entre procesos, almacenes de datos y entidades externas. |
| Docker | Plataforma de virtualización a nivel de sistema operativo que empaqueta aplicaciones y dependencias en contenedores portátiles. |
| FastAPI | Framework web moderno de Python para APIs REST, con validación automática de datos y documentación Swagger interactiva. |
| FullCalendar.js | Biblioteca JavaScript de código abierto para calendarios interactivos con soporte de vistas de día, semana y mes. |
| GitHub Actions | Plataforma de integración y entrega continua integrada en GitHub que automatiza flujos de trabajo en respuesta a eventos del repositorio. |
| Hashing | Proceso computacional unidireccional que transforma un dato en una cadena de longitud fija. Diferente al cifrado: el hash no puede revertirse. |
| HTTPS | Protocolo HTTP con cifrado TLS/SSL que garantiza confidencialidad e integridad en la transmisión de datos. |
| Índice único parcial | Característica de PostgreSQL que aplica una restricción de unicidad únicamente a los registros que cumplen una condición, definida mediante una cláusula WHERE en la declaración del índice. |
| Integración continua | Práctica de desarrollo que automatiza la verificación del código mediante la ejecución de pruebas y análisis estático ante cada modificación del repositorio. |
| Intranet | Red privada de comunicación interna de una organización, accesible exclusivamente para su personal autorizado. |
| JWT | *JSON Web Token* (RFC 7519). Estándar para transmisión segura de información entre partes, usado para gestión de sesiones de usuario. |
| MER | Modelo Entidad-Relación. Representación gráfica de entidades, atributos y relaciones de una base de datos (Chen, 1976). |
| mkcert | Herramienta de código abierto para generar certificados SSL confiables en entornos locales e intranet. |
| Nginx | Servidor web y proxy inverso de alto rendimiento, utilizado para gestionar solicitudes HTTP y habilitar HTTPS. |
| PostgreSQL | Sistema de gestión de bases de datos relacional de código abierto con soporte para transacciones ACID. |
| Pytest | Framework de pruebas automatizadas para Python, empleado en este proyecto para verificar los casos de uso del sistema. |
| RBAC | *Role-Based Access Control*. Mecanismo de seguridad que determina los permisos según el rol del usuario en la organización. |
| SQLModel | Biblioteca Python que combina SQLAlchemy y Pydantic en una sola capa para modelos de base de datos y validación. |
| Tailwind CSS | Framework de CSS de tipo *utility-first* donde la interfaz se construye componiendo clases de utilidad predefinidas. |
| WeasyPrint | Biblioteca Python que convierte documentos HTML/CSS en archivos PDF de alta calidad para generación de reportes. |

---

## Anexos

### Anexo A. Instrumento de entrevista al personal administrativo

Universidad Nacional Pedro Henríquez Ureña (UNPHU), Recinto La Vega.

Objetivo: recopilar información sobre el proceso actual de gestión de citas en el HTQPJB.

Datos del entrevistado:

- Cargo o función: ____________________
- Área: ____________________
- Años de experiencia en el cargo: ____________________

Preguntas:

- ¿De qué manera se realiza actualmente el proceso de registro de una nueva cita médica?
- ¿Cuánto tiempo aproximado tarda el agendamiento desde que el paciente solicita la cita?
- ¿Con qué frecuencia se producen errores de duplicación de citas? ¿Cómo se identifican?
- ¿Cómo se coordina la disponibilidad de los médicos para asignar los turnos?
- ¿Qué reportes o informes se generan actualmente sobre las citas atendidas?
- ¿Qué funcionalidades considera más importantes en un sistema digital de gestión de citas?
- ¿Tiene experiencia previa en el uso de sistemas de información hospitalaria o aplicaciones web?
- ¿Qué dificultades anticipa en la transición del proceso manual al sistema digital?

### Anexo B. Cuestionario de satisfacción y expectativas

Instrucciones: marque con una X la opción que mejor refleje su opinión.

- ¿Cómo califica la eficiencia del proceso actual de gestión de citas?
  ( ) Muy eficiente ( ) Eficiente ( ) Regular ( ) Ineficiente ( ) Muy ineficiente

- ¿Con qué frecuencia se producen errores en la asignación de citas?
  ( ) Nunca ( ) Raramente ( ) A veces ( ) Frecuentemente ( ) Siempre

- ¿Considera que un sistema digital mejoraría su desempeño laboral?
  ( ) Definitivamente sí ( ) Probablemente sí ( ) No sé ( ) Probablemente no ( ) Definitivamente no

- ¿Cuánto tiempo promedio tarda en registrar una cita manualmente?
  ( ) Menos de 5 min ( ) 5 a 10 min ( ) 10 a 20 min ( ) Más de 20 min

### Anexo C. Análisis de resultados de la encuesta

| Pregunta | Respuesta más frecuente | % de participantes |
|---|---|---|
| Eficiencia del proceso actual | Ineficiente o muy ineficiente | 87 % |
| Frecuencia de errores en asignación | Frecuentemente | 73 % |
| Sistema digital mejoraría el desempeño | Definitivamente sí | 93 % |
| Nivel de comodidad con aplicaciones web | Medio o alto | 80 % |
| Tiempo promedio por cita manual | 10 a 20 minutos | 67 % |

*Nota.* Encuesta aplicada a 15 miembros del personal del área de Consulta Externa del HTQPJB. Elaboración propia (2026).

### Anexo D. Script DDL completo de la base de datos

```sql
-- Base de datos: sgcm_db — PostgreSQL 15

CREATE TABLE usuarios (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    rol VARCHAR(20) NOT NULL
        CHECK (rol IN ('secretaria', 'medico', 'admin')),
    activo BOOLEAN DEFAULT TRUE,
    fecha_creacion TIMESTAMP DEFAULT NOW()
);

CREATE TABLE pacientes (
    id SERIAL PRIMARY KEY,
    cedula VARCHAR(13) UNIQUE NOT NULL,
    nombre VARCHAR(100) NOT NULL,
    apellidos VARCHAR(100) NOT NULL,
    fecha_nacimiento DATE,
    telefono VARCHAR(15) NOT NULL,
    direccion TEXT,
    fecha_registro TIMESTAMP DEFAULT NOW()
);

CREATE TABLE medicos (
    id SERIAL PRIMARY KEY,
    id_usuario INTEGER REFERENCES usuarios(id) ON DELETE SET NULL,
    nombre VARCHAR(100) NOT NULL,
    especialidad VARCHAR(50) NOT NULL,
    telefono VARCHAR(15),
    activo BOOLEAN DEFAULT TRUE
);

CREATE TABLE horarios (
    id SERIAL PRIMARY KEY,
    id_medico INTEGER REFERENCES medicos(id) ON DELETE CASCADE,
    dia_semana SMALLINT NOT NULL
        CHECK (dia_semana BETWEEN 1 AND 7),
    hora_inicio TIME NOT NULL,
    hora_fin TIME NOT NULL,
    activo BOOLEAN DEFAULT TRUE
);

CREATE TABLE citas (
    id SERIAL PRIMARY KEY,
    id_paciente INTEGER REFERENCES pacientes(id) NOT NULL,
    id_medico INTEGER REFERENCES medicos(id) NOT NULL,
    fecha DATE NOT NULL,
    hora TIME NOT NULL,
    estado VARCHAR(20) DEFAULT 'pendiente'
        CHECK (estado IN ('pendiente', 'atendida', 'cancelada')),
    motivo TEXT,
    id_secretaria INTEGER REFERENCES usuarios(id) NOT NULL,
    fecha_registro TIMESTAMP DEFAULT NOW()
);

-- Índice único parcial: permite reutilizar horarios liberados por cancelación
CREATE UNIQUE INDEX uq_citas_medico_fecha_hora
    ON citas (id_medico, fecha, hora)
    WHERE estado <> 'cancelada';

CREATE TABLE consultas (
    id SERIAL PRIMARY KEY,
    id_cita INTEGER REFERENCES citas(id) UNIQUE NOT NULL,
    observaciones TEXT NOT NULL,
    fecha_registro TIMESTAMP DEFAULT NOW()
);

CREATE TABLE auditoria (
    id SERIAL PRIMARY KEY,
    id_usuario INTEGER REFERENCES usuarios(id),
    accion VARCHAR(20) NOT NULL,
    tabla_afectada VARCHAR(50) NOT NULL,
    id_registro INTEGER,
    detalle TEXT,
    fecha_hora TIMESTAMP DEFAULT NOW(),
    ip_origen VARCHAR(45)
);
```
