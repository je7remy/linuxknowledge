
# Anteproyecto: Desarrollo de un Sistema Web de Gestión de Citas para el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch

## 1. Introducción

El Hospital Traumatológico y Quirúrgico Prof. Juan Bosch es una institución de salud esencial en la región, dedicada a la atención de emergencias y procedimientos quirúrgicos. Sin embargo, enfrenta problemas críticos en la gestión de citas médicas debido a procesos manuales que generan ineficiencias operativas y afectan la calidad del servicio ofrecido a los pacientes. Entre las principales dificultades se encuentran las largas demoras en la atención, la duplicación de registros médicos, los conflictos en la asignación de turnos y la pérdida de citas por errores administrativos. Estos inconvenientes no solo incrementan la carga laboral del personal, sino que también comprometen la experiencia y seguridad de los pacientes.

El propósito de este proyecto es desarrollar un **Sistema Web de Gestión de Citas** que modernice y optimice la programación de turnos en el hospital. Dirigido exclusivamente a secretarias y médicos, el sistema ofrecerá una plataforma centralizada para programar, editar, cancelar y consultar citas, permitiendo a las secretarias gestionar los turnos de manera eficiente y a los médicos consultar y administrar sus agendas en tiempo real. Esta solución busca reducir los tiempos de espera, minimizar errores y mejorar la coordinación interdepartamental, contribuyendo a una atención médica más eficiente y segura.

## 2. Justificación del Problema

La gestión actual de citas en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch depende de procesos manuales que generan múltiples inconvenientes. Las secretarias enfrentan dificultades para coordinar las agendas de los médicos, lo que resulta en superposiciones de turnos y cancelaciones frecuentes. Los médicos, por su parte, carecen de una herramienta que les permita visualizar sus horarios actualizados de manera rápida y confiable. Estos problemas se traducen en largas esperas para los pacientes, errores administrativos y una atención fragmentada, afectando tanto la eficiencia operativa como la satisfacción de los usuarios.

La implementación de un sistema web de gestión de citas es una solución necesaria para abordar estas deficiencias. Al automatizar la programación y centralizar la información, se reducirán los errores humanos, se optimizará el uso de los recursos disponibles y se facilitará la comunicación entre departamentos. Dado el rol crítico del hospital en la región, esta modernización no solo mejorará los procesos internos, sino que también elevará los estándares de calidad en la atención médica, justificando plenamente la relevancia de este proyecto.

## 3. Planteamiento del Problema

El Hospital Traumatológico y Quirúrgico Prof. Juan Bosch enfrenta desafíos significativos en la administración de citas médicas, derivados de la falta de un sistema automatizado. Los principales problemas identificados son:

- **Largas demoras en la atención:** La programación ineficiente de citas genera esperas prolongadas para los pacientes.
- **Duplicación de registros médicos:** La gestión manual provoca registros múltiples para un mismo paciente, causando confusión y errores.
- **Conflictos en la asignación de turnos:** La ausencia de una plataforma centralizada lleva a superposiciones en las agendas de los médicos.
- **Pérdidas de citas por errores administrativos:** Los procesos manuales incrementan el riesgo de omisiones o asignaciones incorrectas.
- **Dificultad en la coordinación interdepartamental:** Sin una herramienta compartida, la comunicación entre secretarias y médicos es limitada, afectando la planificación.

Estos problemas sobrecargan al personal y comprometen la calidad del servicio. La implementación de un sistema web es esencial para optimizar la gestión de citas, reducir los tiempos de espera y garantizar una atención más segura y eficiente.

## 4. Marco Teórico

### 4.1 Marco Conceptual

- **Gestión de Citas:** Proceso de programar, editar, cancelar y dar seguimiento a turnos médicos, con el objetivo de optimizar la atención y los recursos hospitalarios.
- **Sistema Web:** Aplicación accesible mediante un navegador, diseñada para interactuar con una base de datos y facilitar operaciones específicas desde dispositivos conectados.
- **Intranet:** Red privada dentro del hospital que asegura el acceso seguro a la información y aplicaciones internas.
- **Base de Datos:** Conjunto organizado de datos almacenados electrónicamente, gestionado en este caso con SQLite para registrar pacientes, médicos y citas.
- **Interfaz de Usuario:** Componente del sistema diseñado para ser intuitivo, permitiendo a secretarias y médicos realizar sus tareas de manera eficiente.

### 4.2 Marco Metodológico

El desarrollo del sistema se realizará bajo la metodología ágil **Scrum**, que favorece la flexibilidad y la entrega incremental de funcionalidades. Este enfoque incluye:

- **Sprints:** Ciclos de dos semanas para implementar características específicas, priorizando las más críticas.
- **Reuniones Diarias:** Encuentros breves para coordinar avances y resolver obstáculos.
- **Revisión y Retrospectiva:** Evaluación al final de cada sprint para ajustar el plan según retroalimentación.

Esta metodología garantiza la colaboración con los usuarios finales (secretarias y médicos), integrando sus necesidades a lo largo del desarrollo y asegurando un sistema funcional y adaptado a sus requerimientos.

## 5. Presupuesto del Proyecto

El presupuesto estimado para el desarrollo e implementación del sistema es el siguiente:

- **Desarrollo del Sistema:** $10,000  
  - Diseño, programación, pruebas y despliegue.
- **Equipos:** $5,000  
  - Servidor local para alojar la aplicación y base de datos.  
  - Computadoras adicionales (si se requieren).
- **Otros Gastos:** $2,000  
  - Capacitación del personal.  
  - Documentación y materiales de soporte.

**Total Estimado:** $17,000

Este presupuesto asegura los recursos necesarios para una implementación exitosa, cubriendo costos técnicos y operativos.

## 6. Cronograma de Desarrollo

El proyecto se desarrollará en 5 meses, con las siguientes etapas:

- **Mes 1: Diseño de la Arquitectura del Sistema**  
  - Levantamiento de requerimientos.  
  - Diseño de la base de datos y arquitectura.  
  - Prototipos de la interfaz.
- **Mes 2: Desarrollo del Módulo de Citas**  
  - Funcionalidades de programación, edición, cancelación y consulta de citas.  
  - Integración con agendas médicas.
- **Mes 3: Desarrollo del Módulo de Consultas y Reportes**  
  - Registro de consultas médicas.  
  - Generación de reportes básicos.
- **Mes 4: Integración y Pruebas del Sistema**  
  - Unificación de módulos.  
  - Pruebas funcionales y de usabilidad.  
  - Ajustes finales.
- **Mes 5: Implementación y Capacitación del Personal**  
  - Despliegue en la intranet del hospital.  
  - Capacitación de usuarios.  
  - Soporte inicial.

Este cronograma asegura una ejecución ordenada y la entrega de un sistema probado y funcional.

## 7. Índice Tentativo de la Tesis

1. **Introducción**  
   - Contexto y relevancia del proyecto.  
   - Objetivos generales y específicos.
2. **Marco Teórico**  
   - Fundamentos de gestión de citas y sistemas web.  
   - Tecnologías empleadas.
3. **Metodología**  
   - Enfoque Scrum y herramientas utilizadas.
4. **Desarrollo del Sistema**  
   - Diseño de arquitectura y base de datos.  
   - Implementación de módulos.  
   - Pruebas e integración.
5. **Resultados y Discusión**  
   - Evaluación del sistema con usuarios.  
   - Impacto en la gestión de citas.
6. **Conclusiones y Recomendaciones**  
   - Logros y beneficios.  
   - Propuestas de mejoras futuras.

