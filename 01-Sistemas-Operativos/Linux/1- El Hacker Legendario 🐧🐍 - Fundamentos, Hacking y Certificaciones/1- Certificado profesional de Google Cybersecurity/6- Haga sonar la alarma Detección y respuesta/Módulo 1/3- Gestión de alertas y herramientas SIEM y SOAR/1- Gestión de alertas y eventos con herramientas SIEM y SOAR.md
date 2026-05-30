---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-1]
actualizado: 2026-05-28
---

# Gestión de alertas y eventos con herramientas SIEM y SOAR

# 🧭 Herramientas de Gestión de Eventos e Información de Seguridad (SIEM) y Orquestación y Respuesta (SOAR)

---

## 🔎 Introducción

Cuando un analista de seguridad recibe alertas desde herramientas de detección (IDS, IPS, firewalls, etc.), necesita un lugar donde **centralizar, analizar y visualizar** toda esa información.  
Aquí es donde entran en juego las herramientas **SIEM** y **SOAR**.

---

## ⚙️ ¿Qué es un SIEM?

**SIEM (Security Information and Event Management)**  
Es una herramienta que:

- **Recopila, analiza y correlaciona** grandes volúmenes de registros (logs).
    
- **Monitoriza** la actividad crítica de una organización.
    
- Proporciona una **vista unificada** del estado de seguridad de toda la red.
    

### 🧩 Analogía: el salpicadero de un coche

- En un vehículo, el salpicadero te avisa si hay un problema (presión de neumáticos, batería, combustible…).
    
- En una red, el SIEM **muestra alertas y métricas** sobre el estado de los sistemas y posibles amenazas.  
    ➡️ Ambas funciones ofrecen **una visión centralizada y en tiempo real** para tomar decisiones rápidamente.
    

---

## 🧱 Proceso de funcionamiento del SIEM

1. ### **Recopilación de datos (Logs)**
    
    - Reúne información desde múltiples fuentes:
        
        - IDS/IPS
            
        - Firewalls
            
        - Bases de datos
            
        - Servidores y aplicaciones
            
        - Equipos de usuario
            
2. ### **Agregación**
    
    - Centraliza todos los registros en un **único repositorio** para su análisis.
        
    - Puede manejar grandes volúmenes de datos provenientes de miles de dispositivos.
        
3. ### **Normalización**
    
    - “Limpia” los datos, eliminando atributos innecesarios.
        
    - Estandariza los formatos para que sean coherentes y comparables.
        
    - Facilita búsquedas y análisis posteriores.
        
4. ### **Análisis y correlación**
    
    - Aplica **reglas predefinidas** para identificar patrones sospechosos.
        
    - Detecta eventos anómalos y los **clasifica como alertas** para revisión.
        

---

## 🤖 ¿Qué es un SOAR?

**SOAR (Security Orchestration, Automation and Response)**  
Es un conjunto de herramientas, flujos de trabajo y aplicaciones que permiten **automatizar la respuesta** ante incidentes de seguridad.

### 🔧 Funciones principales:

- **Automatiza tareas repetitivas**, como cerrar tickets o aislar un equipo afectado.
    
- **Orquesta** varias herramientas de seguridad (SIEM, antivirus, firewalls, etc.) para actuar de forma coordinada.
    
- **Gestiona casos**, agrupando múltiples incidentes relacionados en un mismo panel.
    
- Reduce el **tiempo de respuesta (MTTR)** y libera al analista de tareas manuales.
    

---

## 🧠 Diferencias clave entre SIEM y SOAR

|Característica|**SIEM**|**SOAR**|
|---|---|---|
|**Función principal**|Recopila, analiza y genera alertas|Automatiza la respuesta y gestión de incidentes|
|**Nivel de acción**|Detecta y notifica|Responde y ejecuta acciones|
|**Objetivo**|Visibilidad y monitoreo|Automatización y eficiencia|
|**Ejemplo de acción**|Identifica tráfico sospechoso|Bloquea automáticamente la IP del atacante|

---

## ✅ Conclusión

- **SIEM** = “El tablero de control” que **detecta y alerta**.
    
- **SOAR** = “El piloto automático” que **actúa y responde**.  
    Ambas herramientas son esenciales en la **caja de herramientas del analista de seguridad**, ya que trabajan juntas para **detectar, analizar y responder rápidamente** ante incidentes cibernéticos.
    

---

## Pregunta

¿Cuáles son los pasos del proceso SIEM general en el orden correcto?

Recoger y agregar Datos, analizar Datos, normalizar Datos

Normalización de datos, automatización de datos y análisis de datos

Recopilación y agregación de Datos, Normalización de Datos y Automatización de Datos

Recopilación y agregación de datos, normalización de datos y análisis de datos

✅ **Respuesta correcta:**  
**Recopilación y agregación de datos, normalización de datos y análisis de datos.**

---

📘 **Explicación:**  
El proceso general de un **SIEM (Security Information and Event Management)** sigue tres pasos principales:

1. **Recopilación y agregación de datos**
    
    - El SIEM reúne registros (_logs_) desde múltiples fuentes (firewalls, IDS/IPS, servidores, aplicaciones, etc.) y los centraliza en un solo lugar.
        
2. **Normalización de datos**
    
    - Limpia y estandariza la información eliminando atributos irrelevantes para que los registros sean coherentes y fáciles de analizar.
        
3. **Análisis de datos**
    
    - Aplica reglas de correlación y detección para identificar comportamientos anómalos y generar alertas sobre posibles incidentes de seguridad.
        

---

🧠 **En resumen:**  
**SIEM = Recopilar → Normalizar → Analizar → Alertar.**

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ➡️ Siguiente: [[2- Visión general de la tecnología SIEM]]
