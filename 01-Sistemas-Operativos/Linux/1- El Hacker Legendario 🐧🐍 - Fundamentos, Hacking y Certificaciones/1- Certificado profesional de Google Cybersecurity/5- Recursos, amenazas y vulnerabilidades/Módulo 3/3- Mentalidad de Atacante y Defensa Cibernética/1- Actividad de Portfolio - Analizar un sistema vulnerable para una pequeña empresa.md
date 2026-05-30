---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Actividad de Portfolio - Analizar un sistema vulnerable para una pequeña empresa

# 📄 Informe de Evaluación de Vulnerabilidades

**Fecha:** 26 de septiembre de 2025

---

## Descripción del Sistema

El servidor de la empresa de comercio electrónico cuenta con un procesador de alto rendimiento y 128 GB de memoria. Ejecuta un sistema operativo Linux e implementa MySQL como gestor de base de datos. Está disponible en Internet mediante direcciones IPv4 y permite acceso remoto de empleados en todo el mundo. El servidor ha permanecido público desde el inicio de la empresa, lo que representa una vulnerabilidad grave que expone información sensible de clientes y operaciones.

---

## Alcance

El alcance de esta evaluación se limita a los riesgos de **confidencialidad, integridad y disponibilidad de los datos** almacenados en el servidor de base de datos. No se evaluará la seguridad física ni otros sistemas de infraestructura relacionados. El periodo de referencia será de tres meses y se seguirá la metodología de la guía **NIST SP 800-30 Rev. 1**.

---

## Propósito

El servidor de base de datos es el recurso principal para el almacenamiento y la consulta de información de clientes, lo cual lo hace crítico para las operaciones de la empresa. La protección de estos datos es fundamental para garantizar la confianza de los clientes y la continuidad del negocio. En caso de que el servidor sea desactivado o comprometido, la empresa sufriría interrupciones en sus operaciones, pérdidas económicas y un daño significativo a su reputación. El propósito de esta evaluación es identificar riesgos clave y recomendar controles que reduzcan la exposición a amenazas.

---

## Evaluación de Riesgos

|Fuente de amenaza|Evento de amenaza|Probabilidad (1-3)|Gravedad (1-3)|Riesgo (PxG)|
|---|---|---|---|---|
|Hacker externo|Exfiltración de información sensible|3 (Alta)|3 (Alta)|9 (Crítico)|
|Competidor|Alteración o eliminación de datos críticos|2 (Media)|3 (Alta)|6 (Alto)|
|Hacktivista|Ataque de Denegación de Servicio (DoS)|2 (Media)|2 (Media)|4 (Moderado)|

---

## Enfoque

Las amenazas seleccionadas fueron elegidas porque representan los riesgos más relevantes para un servidor expuesto al público. La **exfiltración de datos por hackers** se consideró crítica por la alta probabilidad e impacto financiero y reputacional. La **alteración de datos por competidores** se evaluó como un riesgo alto que puede afectar la integridad de la información y decisiones de negocio. Finalmente, los **ataques DoS de hacktivistas** se incluyeron como una amenaza real que puede afectar la disponibilidad del sistema y frenar operaciones comerciales. Estas amenazas reflejan los tres pilares de la seguridad de la información: confidencialidad, integridad y disponibilidad.

---

## Estrategia de Remediación

Se recomienda implementar un plan de defensa en profundidad con los siguientes controles:

1. **Autenticación multifactor (MFA)** para garantizar accesos seguros.
    
2. **Controles de acceso basados en roles (RBAC)** aplicando el principio de menor privilegio.
    
3. **Cifrado de datos en tránsito con TLS actualizado**, eliminando protocolos obsoletos como SSL.
    
4. **Firewall e IP allow-listing** para limitar conexiones solo a direcciones autorizadas.
    
5. **Monitoreo y auditoría continua**, con alertas en tiempo real para detectar actividades anómalas.
    

La implementación de estas medidas reducirá significativamente la probabilidad y el impacto de los riesgos identificados, fortaleciendo la seguridad global del sistema.

---

# ✅ Preguntas finales (actividad calificada)

**1. ¿Qué valor tiene el servidor de base de datos para la empresa?**  
El servidor es el corazón de las operaciones de la empresa, ya que almacena y permite consultar información crítica de clientes y prospectos, indispensable para las ventas y la toma de decisiones.

**2. ¿Por qué es importante para la empresa proteger los datos del servidor?**  
Porque una brecha de seguridad puede causar pérdida de confianza de los clientes, sanciones legales, pérdidas económicas y daño a la reputación.

**3. Identifique tres fuentes de amenaza y tres eventos de amenaza asociados.**

- **Fuente:** Hacker externo → **Evento:** Exfiltración de información sensible.
    
- **Fuente:** Competidor → **Evento:** Alteración o eliminación de datos críticos.
    
- **Fuente:** Hacktivista → **Evento:** Ataque de Denegación de Servicio (DoS).
    

**4. Calcule probabilidad, gravedad y riesgo para cada evento.**

- Exfiltración de datos → Probabilidad: 3, Gravedad: 3, Riesgo: 9.
    
- Alteración de datos → Probabilidad: 2, Gravedad: 3, Riesgo: 6.
    
- Ataque DoS → Probabilidad: 2, Gravedad: 2, Riesgo: 4.
    

**5. ¿Qué controles de seguridad recomienda implementar?**  
MFA, RBAC, principio del menor privilegio, cifrado TLS, firewall con IP allow-listing, y monitoreo/auditoría continua para mitigar riesgos y proteger la confidencialidad, integridad y disponibilidad del sistema.

---




### Redacción fiel




---

### **Informe de Evaluación de Vulnerabilidades**

**1 de enero de 20XX**

---

### **Descripción del Sistema**

El hardware del servidor consta de un potente procesador CPU y 128 GB de memoria. Ejecuta la última versión del sistema operativo Linux y aloja un sistema de gestión de bases de datos MySQL. Está configurado con una conexión de red estable utilizando direcciones IPv4 y se comunica con otros servidores en la red. Las medidas de seguridad incluyen conexiones cifradas mediante SSL/TLS.

---

### **Alcance**

El alcance de esta evaluación de vulnerabilidades se relaciona con los controles de acceso actuales del sistema. La evaluación cubrirá un período de tres meses, desde junio de 20XX hasta agosto de 20XX. Se utiliza la guía NIST SP 800-30 Rev. 1 para el análisis de riesgos del sistema de información.

---

### **Propósito**

El servidor de bases de datos es un sistema informático centralizado que almacena y gestiona grandes cantidades de datos. Se utiliza para almacenar datos de clientes, campañas y análisis que luego pueden ser examinados para rastrear el rendimiento y personalizar los esfuerzos de marketing. Es fundamental asegurar el sistema debido a su uso regular en operaciones de marketing.

---

### **Evaluación de Riesgos**

|Fuente de amenaza|Evento de amenaza|Probabilidad|Severidad|Riesgo|
|---|---|---|---|---|
|Hacker|Obtener información sensible mediante exfiltración|3|3|9|
|Empleado|Interrumpir operaciones críticas para la misión|2|3|6|
|Cliente|Alterar/Eliminar información crítica|1|3|3|

---

### **Enfoque**

Los riesgos evaluados consideraron los procedimientos de almacenamiento y gestión de datos del negocio. Se determinaron posibles fuentes y eventos de amenaza utilizando la probabilidad de un incidente de seguridad dado los permisos de acceso abiertos del sistema de información. La severidad de los posibles incidentes se ponderó en función del impacto en las necesidades operativas diarias.

---

### **Estrategia de Remediación**

Implementación de mecanismos de autenticación, autorización y auditoría para garantizar que solo los usuarios autorizados accedan al servidor de bases de datos. Esto incluye el uso de contraseñas seguras, controles de acceso basados en roles y autenticación multifactor para limitar los privilegios de los usuarios. Cifrado de datos en tránsito utilizando TLS en lugar de SSL. Lista blanca de direcciones IP para oficinas corporativas con el fin de evitar que usuarios aleatorios de Internet se conecten a la base de datos.

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ➡️ Siguiente: [[2- Proteger todos los puntos de entrada]]
