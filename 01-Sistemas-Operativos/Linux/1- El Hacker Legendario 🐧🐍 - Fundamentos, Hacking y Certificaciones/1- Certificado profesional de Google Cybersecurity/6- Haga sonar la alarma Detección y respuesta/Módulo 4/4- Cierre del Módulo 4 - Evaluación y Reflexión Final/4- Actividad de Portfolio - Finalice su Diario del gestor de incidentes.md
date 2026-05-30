---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Actividad de Portfolio - Finalice su Diario del gestor de incidentes

# 🧾 Diario del Gestor de Incidentes

**Autor:** Jeremy José de la Cruz Pérez  
**Curso:** Google Cybersecurity Professional Certificate — Curso 6, Módulo 4  
**Fecha de finalización:** 23 de octubre de 2025

---

### **📘 Entrada #1 – Investigación de incidente: Tráfico sospechoso HTTP**

**Fecha:** 05/10/2025  
**Descripción:** Investigación de un incidente detectado por Suricata donde se generaron alertas relacionadas con tráfico HTTP no habitual.  
**Herramienta(s) utilizada(s):** Suricata, Terminal de Ubuntu

**Las 5 W’s:**

- **Quién:** Usuario interno con IP 192.168.1.45
    
- **Qué:** Peticiones HTTP GET inusuales detectadas hacia servidores externos
    
- **Cuándo:** 05 de octubre de 2025 a las 14:32
    
- **Dónde:** Red doméstica simulada dentro del laboratorio
    
- **Por qué:** Actividad generada por un intento de conexión automatizada no autorizada
    

**Fase del NIST:** _Detección y Análisis_  
**Notas adicionales:** Se confirmó que las alertas provenían de un script automatizado de prueba de penetración. No hubo compromiso real.

---

### **📗 Entrada #2 – Uso de herramienta: Wireshark**

**Fecha:** 07/10/2025  
**Descripción:** Análisis de paquetes capturados para identificar el comportamiento del tráfico HTTP y posibles patrones de ataque.  
**Herramienta(s) utilizada(s):** Wireshark

**Las 5 W’s:**

- **Quién:** Analista de seguridad (yo)
    
- **Qué:** Captura de tráfico HTTP y DNS
    
- **Cuándo:** Durante el laboratorio “Analiza tu primer paquete”
    
- **Dónde:** Máquina virtual Windows
    
- **Por qué:** Para comprender el flujo de paquetes en tiempo real y el proceso de filtrado
    

**Fase del NIST:** _Preparación / Detección y Análisis_  
**Notas adicionales:** Se aplicaron filtros “http” y “ip.src ==” para aislar tráfico de interés. Wireshark demostró ser esencial para análisis forense en red.

---

### **📙 Entrada #3 – Investigación de incidente: Intento de malware detectado**

**Fecha:** 12/10/2025  
**Descripción:** Investigación sobre un archivo sospechoso tras recibir alertas relacionadas con su hash.  
**Herramienta(s) utilizada(s):** VirusTotal, Chronicle

**Las 5 W’s:**

- **Quién:** Usuario con acceso administrativo
    
- **Qué:** Archivo descargado que coincidía con firmas de malware
    
- **Cuándo:** 12 de octubre de 2025 a las 09:15
    
- **Dónde:** Equipo simulado dentro del entorno de práctica
    
- **Por qué:** Usuario abrió un archivo proveniente de fuente desconocida
    

**Fase del NIST:** _Contención, Erradicación y Recuperación_  
**Notas adicionales:** Se verificó el hash con VirusTotal y Chronicle, confirmando falsos positivos. Se reforzaron las políticas de descarga segura.

---

### **📕 Entrada #4 – Uso de herramienta: Splunk y Chronicle**

**Fecha:** 18/10/2025  
**Descripción:** Consultas SIEM realizadas para buscar eventos específicos y correlacionar registros normalizados.  
**Herramienta(s) utilizada(s):** Splunk (SPL), Google Chronicle (UDM, YARA-L)

**Las 5 W’s:**

- **Quién:** Analista de SOC
    
- **Qué:** Análisis de registros en bruto y normalizados para correlación de eventos
    
- **Cuándo:** 18 de octubre de 2025 durante práctica guiada
    
- **Dónde:** Entorno simulado de Google Cybersecurity
    
- **Por qué:** Para comprender cómo se buscan indicadores de compromiso (IoC) en SIEM
    

**Fase del NIST:** _Actividad posterior al incidente_  
**Notas adicionales:** Se usaron consultas personalizadas con comodines (*) para mejorar velocidad y relevancia.

---

## 🧠 Reflexiones / Notas Finales

**¿Hubo alguna actividad específica que supusiera un reto para ti?**  
Sí, interpretar las alertas JSON generadas por Suricata fue un reto. Al principio los campos resultaban confusos, pero luego comprendí cómo cada clave y valor representan datos críticos del evento.

**¿Ha cambiado su comprensión de la detección y respuesta ante incidentes desde que realizó este curso?**  
Definitivamente sí. Ahora entiendo cómo cada capa del proceso —desde la detección con IDS hasta la correlación con SIEM— forma parte de un ciclo integral de respuesta ante incidentes.

**¿Ha habido alguna herramienta o concepto específico que le haya gustado más?**  
Wireshark fue mi favorita. Permite visualizar el flujo real de datos en una red y comprender cómo pequeñas anomalías pueden convertirse en grandes pistas dentro de una investigación.

---

# 🧠 **Diario del Gestor de Incidentes (Incident Handler’s Journal)**

> 📄 _Plantilla universal para documentar investigaciones, análisis de herramientas y lecciones aprendidas en ciberseguridad._

---

### 🗓️ **Fecha:**

_(Indica el día en que realizas la actividad o registras el incidente.)_

### 🧾 **Entrada #:**

_(Número consecutivo de registro, por ejemplo: Entrada #1, Entrada #2…)_

---

### 🧩 **Descripción breve (50–80 palabras):**

Resume la actividad, incidente o hallazgo. Indica el propósito principal y el contexto (por ejemplo, análisis de tráfico, identificación de amenazas, uso de herramienta, etc.).

---

### 🧰 **Herramienta(s) utilizada(s):**

Lista las herramientas de ciberseguridad empleadas en esta entrada.  
Ejemplo: Wireshark, Splunk, Chronicle, Suricata, Nmap, Hydra, Fail2Ban, etc.  
Explica brevemente su función en la actividad (3–5 frases).

---

### ⚠️ **Las 5 W de la investigación (5W Method):**

|Pregunta|Detalle|
|---|---|
|**Who (Quién)**|¿Quién causó o estuvo involucrado en el incidente?|
|**What (Qué)**|¿Qué sucedió exactamente? Describe el tipo de ataque o evento.|
|**When (Cuándo)**|Fecha y hora aproximada del incidente o análisis.|
|**Where (Dónde)**|Ubicación o entorno afectado (host, red, servicio, etc.).|
|**Why (Por qué)**|Motivo o causa del evento: vulnerabilidad, error humano, fallo de seguridad, etc.|

---

### 🧮 **Fase del ciclo de vida NIST (opcional):**

Marca o escribe la fase principal según el **Ciclo de vida de respuesta a incidentes del NIST**:

-  Preparación
    
-  Detección y análisis
    
-  Contención, erradicación y recuperación
    
-  Actividad posterior al incidente
    

---

### 🧠 **Notas y hallazgos adicionales:**

Incluye pensamientos, observaciones o hipótesis sobre la actividad.  
Puedes añadir evidencia (hashes, IPs, eventos SIEM, patrones detectados, capturas, etc.).

---

## 🪞 **Reflexiones / Notas finales (40–60 palabras cada una)**

1. ¿Hubo alguna actividad específica que te resultó un reto? ¿Por qué?
    
2. ¿Cómo cambió tu comprensión de la detección y respuesta ante incidentes?
    
3. ¿Hubo alguna herramienta o concepto que te gustara más? ¿Por qué?
    

---

## 📘 **Ejemplo de uso rápido**

**Fecha:** 21/10/2025  
**Entrada #:** 1  
**Descripción:** Analicé un archivo de captura de red usando Wireshark para identificar posibles paquetes HTTP sospechosos. Aplicando filtros, detecté un intercambio anómalo entre dos hosts internos.  
**Herramientas:** Wireshark, usando filtro `http.request`.  
**Las 5 W:**

- **Quién:** usuario interno con IP 192.168.0.15
    
- **Qué:** transmisión de datos no cifrados
    
- **Cuándo:** 20/10/2025 14:25
    
- **Dónde:** Red interna corporativa
    
- **Por qué:** Configuración de proxy inseguro
    

---
## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[3- Desafío del módulo 4]]
- ➡️ Siguiente: [[5- Diario del Gestor de Incidentes]]
