
# 🛡️ Sistemas de Detección y Prevención de Intrusiones (IDS / IPS)

### 🔍 Analogía inicial

Imagina un **sistema de seguridad en el hogar**:

- Los **sensores** detectan movimiento o entrada no autorizada (como puertas o ventanas abiertas).
    
- Si algo toca una onda de sonido, el sensor **envía una alerta** al teléfono.
    

➡️ En ciberseguridad, un **IDS (Intrusion Detection System)** cumple una función similar: **monitorea** la actividad del sistema o red y **envía alertas** ante comportamientos sospechosos.

---

### 🧠 ¿Qué es un IDS?

**IDS (Intrusion Detection System)** = Sistema de Detección de Intrusos.

**Función:**

- Monitorea la red y los sistemas.
    
- Analiza la información para identificar actividades **anómalas o maliciosas**.
    
- **Genera alertas** cuando detecta posibles intrusiones.
    

➡️ Ejemplo: como el sensor que avisa al dueño cuando alguien intenta entrar por la ventana.

---

### 🛑 ¿Qué es un IPS?

**IPS (Intrusion Prevention System)** = Sistema de Prevención de Intrusos.

**Función:**

- Hace todo lo que hace un IDS (**detección y alerta**)
    
- **Actúa automáticamente** para detener la amenaza detectada.
    

➡️ Ejemplo: cuando el sensor detecta que se rompe el vidrio y **activa una puerta de acero** para bloquear el acceso.

---

### ⚙️ Funciones clave

|Sistema|Función principal|Acción tomada|
|---|---|---|
|**IDS**|Detecta y alerta|Solo notifica|
|**IPS**|Detecta, alerta y responde|Bloquea o mitiga|

---

### 🧰 Herramientas comunes IDS/IPS

- **Snort**
    
- **Zeek** (antes Bro)
    
- **Kismet**
    
- **Sagan**
    
- **Suricata** 🔜 (se explorará más adelante en el curso)
    

Estas herramientas pueden **cumplir ambas funciones** (detección y prevención), según su configuración.

---

### 📡 Próximo tema

Las alertas generadas por un IDS/IPS se **envían a canales y personal** responsables, generalmente gestionadas a través de un **SIEM** (_Security Information and Event Management_), que centraliza, organiza y analiza los eventos de seguridad.

---

✅ **Conclusión:**

- IDS = Detecta amenazas.
    
- IPS = Detecta y bloquea amenazas.
    
- Ambas son fundamentales para la **defensa en profundidad**.
    
- Permiten al analista de seguridad **reaccionar rápidamente** ante ataques y **automatizar respuestas** frente a intrusiones.
    

¿Qué puede hacer un Sistema de detección de intrusiones (IDS)? Seleccione tres respuestas.

---

✅ **Respuestas correctas:**

- **Alerta sobre posibles intrusiones**
    
- **Monitorea la actividad del sistema y de la red**
    
- **Recopila y analiza la información del sistema para detectar actividades anómalas**
    

---

📘 **Explicación:**  
Un **IDS (Intrusion Detection System)** se encarga de **vigilar** el tráfico de red y la actividad del sistema, **analizarla** en busca de patrones sospechosos y **generar alertas** cuando identifica una posible intrusión.

👉 No **detiene** la actividad intrusiva (esa función pertenece al **IPS**, Intrusion Prevention System).