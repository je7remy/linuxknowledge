
###  Detección y Análisis: La Primera Línea de Defensa

Como analista de seguridad, tu trabajo en la fase de **Detección y Análisis** es ser el primer filtro para verificar si una actividad sospechosa es realmente una amenaza. Se trata de descubrir rápidamente posibles incidentes y luego investigarlos a fondo para confirmar si son reales.

---

### ## Detección: Separando el Ruido de las Señales

La **detección** se enfoca en identificar actividades inusuales. Para esto, se usan herramientas como los **Sistemas de Detección de Intrusiones (IDS)** y las plataformas **SIEM**, que centralizan y analizan datos de toda la red.

Es crucial entender la diferencia:

- **Eventos:** Son sucesos normales y cotidianos en una red, como iniciar sesión o visitar una página web.
    
- **Incidentes:** Son eventos que violan una política de seguridad, como un acceso no autorizado a una cuenta.
    

> **En resumen:** Todos los incidentes son eventos, pero no todos los eventos son incidentes. El objetivo es encontrar los eventos que son verdaderos incidentes.

---

### ## Análisis: La Labor de Investigación 🕵️‍♀️

Una vez que una herramienta genera una **alerta**, comienza la fase de **análisis**. Aquí es donde aplicas tu pensamiento crítico para investigar y validar esa alerta. Tu misión es examinar los **Indicadores de Compromiso (IoC)**, que son las pistas o evidencias que sugieren que un ataque ha ocurrido (o está ocurriendo).

---

### ## Desafíos Comunes

En esta fase, te enfrentarás a dos grandes retos:

1. **Es Imposible Detectarlo Todo:** Ninguna herramienta es perfecta. Siempre habrá limitaciones y algunos incidentes pasarán desapercibidos. Por eso es vital tener un plan de respuesta a incidentes bien definido.
    
2. **Alto Volumen de Alertas:** Los analistas a menudo reciben miles de alertas por turno. Esto puede deberse a:
    
    - **Falsos Positivos:** Reglas de alerta mal configuradas o demasiado amplias que generan alertas por actividades benignas.
        
    - **Alertas Legítimas Masivas:** Un atacante que explota una nueva vulnerabilidad puede generar una avalancha de alertas reales.
        

Tu habilidad para analizar estas alertas de manera eficiente es clave para el éxito.
### **Pregunta de Autoevaluación**

**¿Qué acciones realizan los analistas de Seguridad durante la fase de Detección y Análisis del Ciclo de vida de respuesta ante incidentes del NIST?** Seleccione dos respuestas.

---

### **Respuestas Correctas**

- **✅ Investigar las alertas de Seguridad**
    
- **✅ Validar las alertas de Seguridad**
    

Explicación:

Durante la fase de Detección y Análisis, el rol principal del analista es actuar como un investigador. Su trabajo consiste en tomar las alertas generadas por las herramientas de seguridad, investigarlas para entender su contexto y, finalmente, validarlas para confirmar si representan una amenaza real o si son falsos positivos.

---

### **Opciones Incorrectas**

- **❌ Configurar los ajustes de alerta**
    
- **❌ Creación de planes de respuesta ante incidentes**
    

Explicación:

Estas acciones son proactivas y se realizan antes de que ocurra un incidente. Pertenecen a la fase de Preparación, donde se establecen los cimientos y se afinan las herramientas para estar listos ante futuras amenazas.