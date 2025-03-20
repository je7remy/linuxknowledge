
## Título del Proyecto

**Desarrollo de un Sistema de Gestión de Citas para el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch**

## Problemática

El Hospital Traumatológico y Quirúrgico Prof. Juan Bosch enfrenta desafíos significativos en la organización y administración de las citas médicas. Se identifican problemas como largas demoras en la atención, duplicación de registros médicos, conflictos en la asignación de turnos y pérdidas de citas derivadas de errores administrativos. Estas deficiencias no solo afectan la eficiencia operativa del hospital, sino que también repercuten negativamente en la calidad del servicio brindado a los pacientes y en la optimización de los recursos disponibles. La ausencia de un sistema automatizado impide una coordinación efectiva entre departamentos, lo que puede derivar en un incremento de la sobrecarga laboral y en una atención fragmentada.

## Objetivo General

Desarrollar e implementar un sistema de gestión de citas médicas que optimice la programación y administración de turnos en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch, elevando la eficiencia operativa y la calidad de la atención al paciente.

## Objetivos Específicos

1. **Diseñar** la arquitectura del sistema de gestión de citas, incluyendo la definición de módulos y la integración con la base de datos, para garantizar una estructura robusta y escalable. 
2. **Integrar** el módulo de agendas médicas por departamento, permitiendo la organización y visualización integral de los turnos. 
3. **Aplicar** mecanismos de validación para evitar la duplicación de registros, asegurando la integridad y confiabilidad de la información.
4. **Evaluar** la efectividad del sistema a través de pruebas de usuario y retroalimentación, para asegurar que cumple con los requerimientos y mejora la eficiencia operativa. 

## Descripción del Proyecto

El proyecto se orienta a la creación de un **Sistema de Gestión de Citas** que permita modernizar y optimizar el proceso de programación de turnos en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch. A través de este sistema, se busca establecer un proceso unificado y eficiente para la organización de citas médicas, facilitando la consulta y actualización del historial de citas, así como asegurando un control riguroso de acceso a la información. La automatización de este proceso contribuirá a la reducción de tiempos de espera, minimización de errores administrativos y mejora en la coordinación interdepartamental, aspectos fundamentales para elevar la calidad y seguridad en la atención médica.

## Características del Sistema

- **Programación de citas por especialidad:** Permite asignar y gestionar las citas de acuerdo a la especialidad y departamento, ofreciendo una visión integral y ordenada de la agenda.  
- **Registro de historial de citas:** Facilita el acceso a la información histórica de cada paciente, lo cual es esencial para el seguimiento y continuidad de la atención.  
- **Control de acceso por usuario:** Garantiza que únicamente el personal autorizado tenga acceso al sistema, protegiendo la confidencialidad e integridad de los datos.  

## Tecnología Utilizada

- **Backend:**  
  - Python con Flask  
  - SQLAlchemy (ORM para la base de datos)  
- **Base de datos:**  
  - SQLite  
- **Frontend:**  
  - HTML5, CSS3 y JavaScript  
  - Bootstrap (para diseño responsivo)  
  - Media queries (para adaptación a diferentes dispositivos)  
- **Seguridad:**  
  - Flask-Login (para la gestión de sesiones)  
- **Compatibilidad:**  
  - Diseño web adaptable (responsive design)  
  - Compatible con navegadores modernos (Chrome, Firefox, Safari, Edge)  

El sistema se desarrollará con la premisa de ser accesible desde cualquier dispositivo con conexión a internet, permitiendo su integración en el entorno hospitalario de manera ágil y eficiente.

## Módulos del Sistema de Gestión de Citas

El sistema permitirá el registro y la administración de citas médicas, abarcando los siguientes módulos:  

- **Módulo de Registro de Citas:** Facilita la asignación y programación de citas por departamento.  
- **Módulo de Gestión de Citas:** Permite la edición y cancelación de citas, adaptándose a cambios y contingencias.  
- **Módulo de Historial de Citas:** Proporciona acceso y actualización del historial de citas de los pacientes.  
- **Módulo de Seguridad:** Gestiona la autenticación de usuarios y el control de acceso para garantizar la seguridad y confidencialidad de la información.  
- **Módulo de Reportes:** Genera listados diarios y semanales que facilitan el seguimiento de la actividad médica.  

## Límites del Proyecto

Para delimitar los módulos del proyecto, se establecen los siguientes límites:  

- El sistema no gestionará la facturación ni los pagos de los pacientes.  
- No incluirá funcionalidades de telemedicina o consultas virtuales.  
- No se integrará con sistemas de historias clínicas electrónicas externas.  
- No proporcionará soporte para múltiples idiomas en esta fase inicial.  
- No incluirá funcionalidades avanzadas de análisis de datos o inteligencia artificial.
