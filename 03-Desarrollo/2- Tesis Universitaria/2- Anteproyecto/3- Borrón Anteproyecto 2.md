
**ANTEPROYECTO**

**TÍTULO:** Desarrollo e Implementación de un Sistema Web para la Gestión de Citas Médicas en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch

**ÍNDICE**

1. **Introducción**
    
    - Descripción del Contexto Hospitalario
        
    - Problemática de la Gestión Manual de Citas
        
    - Propuesta de Solución: Sistema Web de Gestión de Citas
        
2. **Planteamiento del Problema**
    
    - Identificación de Problemas Específicos
        
    - Impacto en la Operativa y Calidad del Servicio
        
    - Preguntas de Investigación (Opcional, más académico) / Formulación del Problema Central
        
3. **Justificación**
    
    - Necesidad Operativa del Hospital
        
    - Beneficios Esperados (Eficiencia, Reducción de Errores, Satisfacción)
        
    - Relevancia para la Calidad de Atención al Paciente
        
    - Alineación con la Modernización Institucional
        
4. **Objetivos**
    
    - Objetivo General
        
    - Objetivos Específicos
        
5. **Alcance y Límites**
    
    - Alcances del Sistema
        
    - Límites del Sistema
        
6. **Marco Teórico y Conceptual**
    
    - Antecedentes (Sistemas Similares, Digitalización en Salud)
        
    - Bases Conceptuales (Gestión de Citas, Sistema Web, Intranet, Base de Datos - SQLite, Interfaz de Usuario)
        
    - Bases Teóricas (Teorías de Usabilidad, Gestión de Procesos - Opcional)
        
    - Bases Legales (Confidencialidad de Datos del Paciente - Leyes Dominicanas relevantes)
        
7. **Marco Metodológico**
    
    - Enfoque de Desarrollo (Metodología Ágil - Scrum)
        
    - Fases del Desarrollo (Planificación, Diseño, Implementación, Pruebas, Despliegue)
        
    - Población Objetivo (Usuarios del Sistema: Secretarias y Médicos)
        
    - Técnicas de Recolección de Requerimientos (Entrevistas, Observación)
        
    - Herramientas Tecnológicas (SQLite, Lenguajes/Frameworks a definir)
        
8. **Presupuesto Estimado**
    
    - Desglose de Costos (Desarrollo, Equipos, Capacitación, Otros)
        
    - Costo Total Estimado
        
9. **Cronograma de Trabajo**
    
    - Distribución de Tareas por Fases/Meses
        
    - Hitos Principales
        
10. **Estructura Tentativa del Trabajo Final (Tesis/Informe)**
    
    - Capítulo 1: Introducción
        
    - Capítulo 2: Marco Teórico y Conceptual
        
    - Capítulo 3: Metodología de Desarrollo
        
    - Capítulo 4: Diseño y Desarrollo del Sistema
        
    - Capítulo 5: Implementación y Pruebas
        
    - Capítulo 6: Resultados y Discusión
        
    - Capítulo 7: Conclusiones y Recomendaciones
        
    - Referencias Bibliográficas
        
    - Anexos (Manuales, Prototipos, etc.)
        

---

**1. Introducción**

El Hospital Traumatológico y Quirúrgico Prof. Juan Bosch se erige como un pilar fundamental en la prestación de servicios de salud especializados en la región, atendiendo un volumen significativo de pacientes que requieren atención traumatológica y procedimientos quirúrgicos. La eficiencia en la gestión de sus procesos internos es crucial para garantizar una atención oportuna y de calidad.

Actualmente, la gestión de citas médicas dentro del hospital se basa en gran medida en procesos manuales (registros en papel, llamadas telefónicas, coordinación verbal), lo cual genera una serie de ineficiencias operativas significativas. Estas incluyen largas demoras para los pacientes, posibilidad de errores en la asignación de turnos, duplicación de esfuerzos y dificultades en la coordinación entre el personal administrativo (secretarias) y el personal médico.

Frente a esta problemática, se propone el desarrollo e implementación de un **Sistema Web de Gestión de Citas**. Esta herramienta tecnológica estará diseñada específicamente para el entorno del hospital y será utilizada internamente por el personal autorizado (secretarias y médicos). El sistema funcionará a través de la intranet del hospital, proporcionando una plataforma centralizada y segura para programar, consultar, modificar y cancelar citas médicas, optimizando así las agendas y mejorando el flujo de pacientes.

**2. Planteamiento del Problema**

La dependencia de métodos manuales para la gestión de citas en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch ha derivado en una serie de problemas concretos que afectan la operatividad diaria y la experiencia del paciente:

- **Ineficiencia en la Programación:** Dificultad para visualizar la disponibilidad real y actualizada de los médicos, llevando a tiempos de espera prolongados para asignar citas.
    
- **Errores Administrativos:** Alta probabilidad de errores humanos como duplicación de citas para un mismo horario, asignación incorrecta de especialista, o pérdida de solicitudes de citas.
    
- **Falta de Coordinación:** Comunicación ineficaz entre secretarias de diferentes áreas o turnos y los médicos, resultando en agendas desactualizadas o con conflictos.
    
- **Sobrecarga del Personal:** El personal administrativo invierte una cantidad considerable de tiempo en tareas manuales de agendamiento y confirmación, tiempo que podría dedicarse a otras labores de atención.
    
- **Experiencia Negativa del Paciente:** Largas esperas telefónicas o presenciales para conseguir una cita, incertidumbre sobre la confirmación y posibles reprogramaciones de último minuto.
    

**Formulación del Problema Central:** ¿De qué manera el desarrollo e implementación de un sistema web interno para la gestión de citas puede optimizar los procesos de programación, reducir los errores administrativos y mejorar la coordinación entre secretarias y médicos en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch?

**3. Justificación**

La implementación de un Sistema Web de Gestión de Citas en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch se justifica por múltiples razones de carácter operativo, estratégico y de calidad:

1. **Necesidad Operativa Urgente:** Los procesos manuales actuales son insostenibles ante el volumen de pacientes y la complejidad de las agendas médicas, generando cuellos de botella y frustración tanto en el personal como en los pacientes.
    
2. **Optimización de Recursos:** Un sistema automatizado permitirá una asignación más eficiente de los horarios médicos y los consultorios, maximizando la capacidad de atención del hospital.
    
3. **Reducción de Errores y Mejora de la Seguridad:** Minimizar los errores humanos en la programación reduce el riesgo de citas duplicadas o perdidas, contribuyendo a una atención más segura y confiable.
    
4. **Mejora en la Calidad del Servicio:** Agilizar el proceso de obtención de citas y reducir los tiempos de espera impacta directamente en la satisfacción del paciente y en la percepción de calidad del hospital.
    
5. **Facilitación del Trabajo del Personal:** Liberar a secretarias y médicos de tareas manuales repetitivas les permite enfocarse en actividades de mayor valor añadido, mejorando su eficiencia y satisfacción laboral.
    
6. **Modernización Institucional:** La adopción de herramientas tecnológicas posiciona al hospital a la vanguardia, mejorando su imagen y eficiencia administrativa, alineándose con las tendencias de digitalización en el sector salud.
    

**4. Objetivos**

### **Objetivo General**

Desarrollar un sistema web de gestión de citas médicas para el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch, dirigido exclusivamente a secretarias y médicos. Este sistema permitirá a las secretarias programar, editar y cancelar citas de manera eficiente a través de una interfaz centralizada, y a los médicos consultar y gestionar sus agendas en tiempo real, optimizando la organización operativa del hospital y reduciendo los tiempos de espera de los pacientes.

---

### **Objetivos Específicos**

1. **Proveer a las secretarias** una herramienta para agendar citas con mayor facilidad, asignando turnos según la disponibilidad de los médicos y vinculando la información del paciente de manera rápida y precisa.

2. **Facilitar a los médicos** una interfaz que les permita consultar sus agendas actualizadas en tiempo real, con la capacidad de buscar citas específicas y recibir notificaciones rápidas sobre cambios o cancelaciones.

3. **Optimizar para las secretarias** la búsqueda y consulta de datos de pacientes y citas, reduciendo errores administrativos y agilizando el proceso de atención mediante un acceso inmediato a la información relevante.

4. **Generar reportes automáticos** para las secretarias, con información diaria y semanal sobre citas programadas, canceladas y atendidas, permitiendo un mejor seguimiento y apoyo en la planificación administrativa.


**5. Alcance y Límites**

## Alcances del Sistema de Gestión de Citas

El sistema abarcará la creación de una plataforma web que permita a las secretarias programar, editar y cancelar citas según la disponibilidad de los médicos, así como consultar el historial de citas de los pacientes. Los médicos podrán visualizar y gestionar sus agendas de citas de manera eficiente. Además, el sistema generará reportes básicos para apoyar la planificación y el seguimiento de la actividad médica.

---

## Límites del Sistema

- No gestionará la facturación ni los pagos de los pacientes.
- No incluirá funcionalidades de telemedicina ni consultas virtuales.
- No se integrará con sistemas de historias clínicas electrónicas externas.
- No proporcionará soporte para múltiples idiomas en esta fase inicial.
- No incluirá funcionalidades avanzadas de análisis de datos ni inteligencia artificial.
    

**6. Marco Teórico y Conceptual**

**A) Antecedentes:**  
La digitalización de los procesos hospitalarios es una tendencia global. Numerosos centros de salud han implementado sistemas de gestión de citas (comerciales o desarrollados a medida) para superar las limitaciones de los métodos manuales. Estudios previos (citar ejemplos si se conocen) demuestran mejoras significativas en eficiencia, reducción de tasas de no asistencia y satisfacción del paciente tras la implementación de dichos sistemas. La experiencia de otros hospitales, tanto a nivel nacional como internacional, servirá como referencia para identificar buenas prácticas y posibles desafíos.

**B) Bases Conceptuales:**

- **Gestión de Citas Médicas:** Proceso administrativo y logístico de asignar y administrar horarios para consultas o procedimientos médicos, buscando equilibrar la demanda de los pacientes con la disponibilidad de los profesionales y recursos del hospital.
    
- **Sistema Web:** Aplicación informática que se ejecuta en un servidor web y es accesible a través de un navegador web estándar (como Chrome, Firefox, Edge) mediante una red (en este caso, la intranet del hospital).
    
- **Intranet:** Red informática privada y segura, utilizada internamente por una organización (el hospital) para compartir información y recursos entre sus miembros. Garantiza que el acceso al sistema esté restringido al personal autorizado.
    
- **Base de Datos:** Colección estructurada de datos almacenados electrónicamente. En este proyecto se utilizará **SQLite**, un sistema de gestión de bases de datos relacional ligero, basado en archivos, adecuado para aplicaciones embebidas o con concurrencia moderada, como se espera en la intranet del hospital para esta función específica. Almacenará información de pacientes (básica), médicos, horarios y citas.
    
- **Interfaz de Usuario (UI):** Medio visual a través del cual los usuarios (secretarias, médicos) interactúan con el sistema web. Debe ser intuitiva, clara y eficiente para facilitar la realización de tareas.
    

**C) Bases Teóricas (Opcional, si se quiere profundizar):**

- **Teoría de Aceptación Tecnológica (TAM):** Explica cómo los usuarios llegan a aceptar y usar una tecnología. Factores como la utilidad percibida y la facilidad de uso percibida serán clave para la adopción del sistema por parte del personal.
    
- **Principios de Usabilidad (Nielsen):** Guías para diseñar interfaces fáciles de usar, aprender y recordar, minimizando errores y aumentando la satisfacción del usuario.
    
- **Gestión de Procesos de Negocio (BPM):** Enfoque para analizar, diseñar, implementar y mejorar los procesos (en este caso, el de gestión de citas) para alcanzar los objetivos organizacionales.
    

**D) Bases Legales:**  
El sistema deberá cumplir con la legislación vigente en la República Dominicana referente a la protección de datos personales y la confidencialidad de la información médica. Se debe asegurar que el almacenamiento, acceso y tratamiento de los datos de los pacientes dentro del sistema respeten la privacidad y seguridad exigidas por ley (Investigar y citar leyes específicas dominicanas si es posible, como la Ley No. 172-13 sobre Protección de Datos de Carácter Personal). El acceso estará restringido por roles (secretaria, médico) para garantizar que cada usuario solo acceda a la información necesaria para su función.

**7. Marco Metodológico**

- **Enfoque de Desarrollo:** Se adoptará la metodología ágil **Scrum**. Este enfoque iterativo e incremental permite flexibilidad para adaptarse a cambios, entregas tempranas de valor (funcionalidades) y una colaboración estrecha con los usuarios finales (secretarias y médicos) a lo largo del proyecto.
    
- **Fases del Desarrollo (basado en Scrum):**
    
    - **Planificación Inicial (Sprint 0):** Definición detallada del backlog del producto (lista de funcionalidades), arquitectura inicial, configuración del entorno.
        
    - **Sprints de Desarrollo (Ciclos de 2-4 semanas):** En cada sprint se seleccionarán funcionalidades del backlog, se diseñarán, desarrollarán, probarán y se presentará un incremento funcional del producto.
        
    - **Revisión del Sprint:** Demostración del incremento funcional a los stakeholders (dirección del hospital, representantes de usuarios) para obtener feedback.
        
    - **Retrospectiva del Sprint:** Reunión interna del equipo de desarrollo para mejorar el proceso de trabajo.
        
    - **Pruebas Continuas:** Pruebas unitarias, de integración y funcionales a lo largo de los sprints. Pruebas de aceptación del usuario (UAT) con secretarias y médicos antes del despliegue final.
        
    - **Despliegue:** Instalación del sistema en el servidor de la intranet del hospital.
        
    - **Post-Implementación:** Soporte inicial y recolección de feedback para futuras mejoras.
        
- **Población Objetivo (Usuarios):** El personal de secretaría encargado de la gestión de citas y los médicos del Hospital Traumatológico y Quirúrgico Prof. Juan Bosch que utilizarán el sistema para consultar sus agendas.
    
- **Técnicas de Recolección de Requerimientos:**
    
    - **Entrevistas:** Con secretarias, médicos y personal administrativo relevante para comprender a fondo el proceso actual, los puntos débiles y las necesidades específicas para el nuevo sistema.
        
    - **Observación:** Observar directamente cómo se gestionan las citas actualmente para identificar flujos de trabajo y posibles mejoras.
        
    - **Análisis Documental:** Revisar agendas, formularios o registros existentes.
        
- **Herramientas Tecnológicas:**
    
    - **Base de Datos:** SQLite.
        
    - **Lenguajes/Frameworks:** A definir según la experiencia del equipo y los requerimientos técnicos (Ej. Backend: Python con Flask, Frontend: HTML, CSS, JavaScript con Boostrap).
        
    - **Control de Versiones:** Git.
        
    - **Gestión de Proyecto (Scrum):** Herramientas como Trello, Jira o similares (opcional).
        

**8. Presupuesto Estimado**

El presupuesto estimado para el desarrollo e implementación del sistema es el siguiente (basado en tu información, se puede detallar más si es necesario):

- **Desarrollo del Sistema:** $10,000
    
    - Análisis y Diseño
        
    - Programación (Backend y Frontend)
        
    - Pruebas (Testing)
        
    - Documentación Técnica
        
- **Equipos y Licencias:** $5,000
    
    - Servidor para Alojamiento en Intranet (si no existe uno adecuado)
        
    - Posibles licencias de software (si aplica, aunque se priorizará open source)
        
    - Adecuación de estaciones de trabajo (si se requieren computadoras adicionales/actualizadas para secretarías)
        
- **Otros Gastos:** $2,000
    
    - Capacitación del Personal (Secretarias y Médicos)
        
    - Manuales de Usuario
        
    - Gestión del Proyecto y Contingencias (aprox. 10-15%)
        

**Costo Total Estimado: $17,000**

(Nota: Este presupuesto es una estimación preliminar y debe ser refinado con un análisis más detallado de horas/hombre, tarifas y costos específicos de hardware/software en el contexto local).

**9. Cronograma de Trabajo (5 Meses)**

- **Mes 1: Análisis y Diseño**
    
    - Semana 1-2: Levantamiento detallado de requerimientos (entrevistas, observación).
        
    - Semana 3: Definición de la arquitectura del sistema y diseño de la base de datos (SQLite).
        
    - Semana 4: Diseño de prototipos de las interfaces de usuario (mockups/wireframes) y validación inicial con usuarios clave.
        
- **Mes 2: Desarrollo - Módulo Central de Citas y Usuarios**
    
    - Sprint 1: Desarrollo del módulo de gestión de médicos y disponibilidad.
        
    - Sprint 2: Desarrollo del módulo de gestión básica de pacientes y funcionalidades de creación/búsqueda de citas.
        
- **Mes 3: Desarrollo - Funcionalidades Avanzadas y Consultas**
    
    - Sprint 3: Desarrollo de funcionalidades de edición y cancelación de citas, validaciones de reglas de negocio (ej. no solapamiento).
        
    - Sprint 4: Desarrollo del módulo de consulta de agenda para médicos y generación de reportes básicos.
        
- **Mes 4: Integración, Pruebas y Ajustes**
    
    - Semana 1-2: Integración completa de todos los módulos. Pruebas internas (unitarias, integración, funcionales).
        
    - Semana 3-4: Pruebas de Aceptación de Usuario (UAT) con secretarias y médicos seleccionados. Ajustes basados en el feedback. Preparación de documentación final (manuales).
        
- **Mes 5: Despliegue, Capacitación y Soporte Inicial**
    
    - Semana 1: Despliegue del sistema en el servidor de la intranet del hospital. Configuración final.
        
    - Semana 2-3: Sesiones de capacitación para todo el personal usuario (secretarias y médicos).
        
    - Semana 4: Puesta en marcha oficial. Soporte inicial intensivo y monitoreo del sistema. Entrega final del proyecto.
        

**10. Estructura Tentativa del Trabajo Final (Tesis/Informe)**

1. **Introducción**
    
    - Contextualización del Hospital y el Problema de la Gestión de Citas.
        
    - Justificación y Relevancia del Proyecto.
        
    - Objetivos (General y Específicos).
        
    - Alcance y Límites del Sistema Desarrollado.
        
    - Estructura del Documento.
        
2. **Marco Teórico y Conceptual**
    
    - Antecedentes de Sistemas de Gestión de Citas en Salud.
        
    - Bases Conceptuales (Definiciones Clave: Sistema Web, Intranet, SQLite, etc.).
        
    - Bases Teóricas Relevantes (Usabilidad, TAM, etc. - si aplica).
        
    - Marco Legal (Leyes de Protección de Datos en RD).
        
3. **Metodología de Desarrollo**
    
    - Descripción de la Metodología Scrum Aplicada.
        
    - Fases del Proyecto Detalladas.
        
    - Técnicas de Recolección de Requerimientos Utilizadas.
        
    - Herramientas y Tecnologías Empleadas.
        
4. **Diseño y Desarrollo del Sistema**
    
    - Arquitectura del Sistema (Componentes, Capas).
        
    - Diseño de la Base de Datos (Modelo Entidad-Relación, Esquema SQLite).
        
    - Diseño de las Interfaces de Usuario (Presentación de Pantallas Clave).
        
    - Descripción de los Módulos Desarrollados y sus Funcionalidades.
        
5. **Implementación y Pruebas**
    
    - Proceso de Despliegue en la Intranet.
        
    - Estrategia de Pruebas (Tipos de Pruebas Realizadas).
        
    - Resultados de las Pruebas (Resumen de Hallazgos y Correcciones).
        
    - Proceso de Capacitación del Personal.
        
6. **Resultados y Discusión**
    
    - Evaluación del Funcionamiento del Sistema en el Entorno Real (si es posible, con datos iniciales de uso).
        
    - Análisis del Cumplimiento de los Objetivos.
        
    - Feedback de los Usuarios (Resultados de encuestas de satisfacción o entrevistas post-implementación).
        
    - Comparación con la Situación Anterior (Beneficios Observados).
        
    - Discusión de las Limitaciones Encontradas durante el Desarrollo o Implementación.
        
7. **Conclusiones y Recomendaciones**
    
    - Conclusiones Principales del Proyecto (Logros, Dificultades).
        
    - Recomendaciones para el Uso y Mantenimiento del Sistema.
        
    - Propuestas de Mejoras Futuras o Próximas Fases (Ej. Integración con HCE, portal paciente, etc.).
        

- **Referencias Bibliográficas**
    
- **Anexos** (Ej. Manual de Usuario, Manual Técnico (si aplica), Código Fuente (referencia), Diagramas, Resultados de Encuestas).
    
