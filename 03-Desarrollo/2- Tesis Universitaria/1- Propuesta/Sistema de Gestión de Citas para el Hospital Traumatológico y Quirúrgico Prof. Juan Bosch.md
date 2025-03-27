
---

## Título del Proyecto

**Desarrollo de un Sistema Web de Gestión de Citas para el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch**

---

## Problemática

El Hospital Traumatológico y Quirúrgico Prof. Juan Bosch enfrenta desafíos significativos en la organización y administración de las citas médicas. Actualmente, se presentan problemas como largas demoras en la atención, duplicación de registros médicos, conflictos en la asignación de turnos y pérdidas de citas derivadas de errores administrativos. Estas deficiencias afectan la eficiencia operativa del hospital, repercuten negativamente en la calidad del servicio brindado a los pacientes y dificultan la optimización de los recursos disponibles. La ausencia de un sistema automatizado impide una coordinación efectiva entre departamentos, lo que incrementa la sobrecarga laboral y genera una atención fragmentada.

---

## Descripción del Proyecto

El proyecto tiene como propósito desarrollar un **Sistema Web de Gestión de Citas** que modernice y optimice el proceso de programación de turnos en el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch. Este sistema estará diseñado para ser utilizado principalmente por secretarias y médicos, ofreciendo una plataforma centralizada que facilite la programación, edición, cancelación y consulta de citas. La automatización de estos procesos busca reducir los tiempos de espera, minimizar errores administrativos y mejorar la coordinación interdepartamental, contribuyendo así a elevar la calidad y seguridad en la atención médica.

---

## Alcances del Sistema de Gestión de Citas

El sistema abarcará la creación de una plataforma web que permita a las secretarias programar, editar y cancelar citas según la disponibilidad de los médicos, así como consultar el historial de citas de los pacientes. Los médicos podrán visualizar y gestionar sus agendas de citas de manera eficiente. Además, el sistema generará reportes básicos para apoyar la planificación y el seguimiento de la actividad médica.

---

## Límites del Sistema

- No gestionará la facturación ni los pagos de los pacientes.
- No incluirá funcionalidades de telemedicina ni consultas virtuales.
- No se integrará con sistemas de historias clínicas electrónicas externas.
- No proporcionará soporte para múltiples idiomas en esta fase inicial.
- No incluirá funcionalidades avanzadas de análisis de datos ni inteligencia artificial.

---

### **Objetivo General**

Desarrollar un sistema web de gestión de citas médicas para el Hospital Traumatológico y Quirúrgico Prof. Juan Bosch, dirigido exclusivamente a secretarias y médicos. Este sistema permitirá a las secretarias programar, editar y cancelar citas de manera eficiente a través de una interfaz centralizada, y a los médicos consultar y gestionar sus agendas en tiempo real, optimizando la organización operativa del hospital y reduciendo los tiempos de espera de los pacientes.

---

### **Objetivos Específicos**

1. **Proveer a las secretarias** una herramienta para agendar citas con mayor facilidad, asignando turnos según la disponibilidad de los médicos y vinculando la información del paciente de manera rápida y precisa.

2. **Facilitar a los médicos** una interfaz que les permita consultar sus agendas actualizadas en tiempo real, con la capacidad de buscar citas específicas y recibir notificaciones rápidas sobre cambios o cancelaciones.

3. **Optimizar para las secretarias** la búsqueda y consulta de datos de pacientes y citas, reduciendo errores administrativos y agilizando el proceso de atención mediante un acceso inmediato a la información relevante.

4. **Generar reportes automáticos** para las secretarias, con información diaria y semanal sobre citas programadas, canceladas y atendidas, permitiendo un mejor seguimiento y apoyo en la planificación administrativa.

---

## Tecnología Utilizada

El sistema será una aplicación web accesible a través de navegadores modernos (Chrome, Firefox, Safari, Edge). Se desarrollará utilizando:
- **Backend:** Python con Flask como framework y SQLAlchemy como ORM para gestionar una base de datos SQLite.
- **Frontend:** HTML5, CSS3, JavaScript y Bootstrap para una interfaz responsive y amigable.
- **Entorno de operación:** El sistema estará alojado en un servidor local (intranet) del hospital, accesible únicamente desde la red interna para garantizar la seguridad y confidencialidad de los datos.

---

## Módulos del Sistema de Gestión de Citas

El sistema estará estructurado en los siguientes módulos principales:

1. **Módulo de Citas:**  
   - Programación, edición, cancelación y consulta de citas.  
   - Gestión de agendas médicas por médico y departamento.

2. **Módulo de Consultas:**  
   - Registro y gestión de las consultas médicas realizadas, vinculadas a las citas programadas.

3. **Módulo de Reportes:**  
   - Generación de listados y estadísticas básicas sobre citas y consultas.

**Nota:** La seguridad (autenticación de usuarios y control de acceso) y la configuración básica del sistema se consideran aspectos transversales e inherentes al desarrollo, por lo que no se listan como módulos independientes.

---

## Especificidad del Sistema

- **Usuarios finales:** Secretarias (gestión de citas) y médicos (consulta y gestión de agendas).
- **Entorno de operación:** Intranet del hospital, accesible solo desde computadoras dentro de la red interna.
- **Propósito:** Optimizar la programación y gestión de citas, mejorando la eficiencia operativa y la experiencia del paciente.

