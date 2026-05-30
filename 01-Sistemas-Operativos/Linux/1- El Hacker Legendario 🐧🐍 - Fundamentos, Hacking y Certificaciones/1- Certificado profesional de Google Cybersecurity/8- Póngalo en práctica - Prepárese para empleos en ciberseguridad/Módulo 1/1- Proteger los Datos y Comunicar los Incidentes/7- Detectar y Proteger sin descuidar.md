---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-1]
actualizado: 2026-05-28
---

# Detectar y Proteger sin descuidar

**La Continuidad del Negocio (BC)** es la estrategia general para asegurar que las funciones críticas de una empresa sigan operando durante y después de un desastre. La **Recuperación en Caso de Catástrofe (DR)** es un subconjunto de la BC, enfocado específicamente en restaurar la infraestructura tecnológica (IT) y los datos.

En el contexto B2B (Business-to-Business), estos planes son vitales porque la interrupción de tu servicio afecta directamente la operación de tus clientes empresariales.

---

### 📈 Continuidad del Negocio (Business Continuity - BC)

La Continuidad del Negocio (BC) es un plan proactivo y holístico diseñado para mantener las operaciones esenciales de la empresa ante cualquier interrupción (desastres naturales, ciberataques, pandemias, etc.).

- **Objetivo:** Mantener la resiliencia operativa.
    
- **Enfoque:** Holístico. Se preocupa por:
    
    - **Personal:** ¿Dónde trabajarán los empleados (ubicaciones alternativas)? ¿Cómo se comunicarán?
        
    - **Procesos:** ¿Existen procedimientos manuales temporales si falla la tecnología?
        
    - **Activos:** ¿Cómo se protegen las instalaciones, la cadena de suministro y la infraestructura (no solo TI)?
        
- **Pregunta Clave:** "¿Cómo seguimos vendiendo, prestando servicio y operando (aunque sea mínimamente) _durante_ el desastre?"
    

---

### 💻 Recuperación en Caso de Catástrofe (Disaster Recovery - DR)

La Recuperación en Caso de Catástrofe (DR) es un componente **técnico** dentro del plan de Continuidad del Negocio. Se activa _después_ de que ocurre el incidente y se enfoca en la infraestructura tecnológica.

- **Objetivo:** Restaurar los sistemas de TI y los datos.
    
- **Enfoque:** Técnico. Se preocupa por:
    
    - **Datos:** Copias de seguridad (backups) y replicación.
        
    - **Sistemas:** Servidores, bases de datos, aplicaciones y redes.
        
    - **Infraestructura:** Sitios de respaldo (centros de datos alternos, nube).
        
- **Pregunta Clave:** "¿Cómo recuperamos nuestros servidores y datos lo más rápido posible _después_ del desastre?"
    

**Analogía:** Si tu empresa fuera un hospital, la **BC** es el plan completo para seguir atendiendo pacientes (usando generadores, moviendo personal, gestionando suministros). La **DR** es el equipo de cirugía de emergencia que trabaja para salvar al paciente (tus datos y servidores).

---

### 🤝 La Importancia en el Contexto B2B

El término "Business-to-Business" (B2B) hace que los planes de BC/DR sean exponencialmente más importantes debido a la **interdependencia** entre empresas.

#### 1. Como Proveedor de Servicios B2B

Si tu empresa le vende servicios a otra empresa (ej. eres un proveedor de software en la nube, una plataforma de pagos, o un servicio de logística), tu cliente depende de ti para su propia operación.

- **Obligación Contractual:** Tus planes de BC/DR no son solo internos; son un compromiso con tus clientes.
    
- **Acuerdos de Nivel de Servicio (SLAs):** Los clientes B2B exigirán SLAs que especifiquen tu **Tiempo Objetivo de Recuperación (RTO)** (cuánto tiempo tardarás en volver a estar en línea) y tu **Punto Objetivo de Recuperación (RPO)** (cuánta pérdida de datos es aceptable, ej. "datos de los últimos 5 minutos").
    
- **Riesgo Reputacional:** Un fallo en tu servicio que detenga el negocio de tu cliente es devastador para la confianza y la relación comercial.
    

#### 2. Como Consumidor de Servicios B2B

Tu propia empresa también depende de otros proveedores B2B (proveedores de internet, servicios en la nube como AWS o Google Cloud, proveedores de materias primas, etc.).

- **Riesgo de la Cadena de Suministro:** Tu plan de Continuidad del Negocio (BC) debe identificar los riesgos asociados al fallo de tus proveedores críticos.
    
- **Debida Diligencia:** Debes evaluar los planes de BC/DR de tus proveedores B2B antes de contratarlos. ¿Qué pasa si ellos fallan?
    
- **Redundancia:** Tu plan puede incluir tener proveedores B2B redundantes (ej. dos proveedores de internet) para mitigar el riesgo de que uno de ellos falle.
    

### Resumen: BC vs. DR

|**Característica**|**Continuidad del Negocio (BC)**|**Recuperación en Caso de Catástrofe (DR)**|
|---|---|---|
|**Enfoque**|Estratégico y holístico (Procesos, Personas, TI)|Táctico y técnico (Datos, Servidores, Redes)|
|**Objetivo**|Mantener el negocio operativo|Restaurar la infraestructura de TI|
|**Pregunta**|"¿Cómo seguimos operando?"|"¿Cómo recuperamos los sistemas?"|
|**Relación**|DR es un **componente** de BC.|Es un **subconjunto** de BC.|**

---

## Navegación

- ⬆️ Carpeta: [[_8- Póngalo en práctica - Prepárese para empleos en ciberseguridad|8- Póngalo en práctica - Prepárese para empleos en ciberseguridad]]
- ⬅️ Anterior: [[6- Ponga a prueba sus Conocimientos -Detección de Eventos e Incidentes]]
- ➡️ Siguiente: [[8- Historia de Juliana - Protección de los recursos]]
