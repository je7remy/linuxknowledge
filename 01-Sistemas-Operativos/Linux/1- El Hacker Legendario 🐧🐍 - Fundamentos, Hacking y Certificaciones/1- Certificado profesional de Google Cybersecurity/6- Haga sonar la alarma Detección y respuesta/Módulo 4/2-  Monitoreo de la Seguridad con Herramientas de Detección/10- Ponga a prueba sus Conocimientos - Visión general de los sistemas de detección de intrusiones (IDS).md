
## ✅ Evaluación completada — Resultados del módulo Suricata

---

### **Pregunta 1**
**Un analista de seguridad utiliza un analizador de protocolos de red para capturar el tráfico HTTP y analizar patrones. ¿Qué tipo de datos están utilizando?**

**✔ Respuesta correcta:**  
**Telemetría de redes**

**💡 Explicación:**  
La **telemetría de red** se refiere a la **recopilación y transmisión de datos de red** (como el tráfico HTTP) para su análisis. Estos datos permiten estudiar flujos, detectar anomalías y comprender el comportamiento del tráfico en tiempo real.

---

### **Pregunta 2**
**¿Qué afirmación describe con exactitud la diferencia entre un NIDS y un HIDS?**

**✔ Respuesta correcta:**  
**Un NIDS se instala en una red; un HIDS se instala en dispositivos individuales.**

**💡 Explicación:**  
- El **NIDS (Network Intrusion Detection System)** analiza el **tráfico que circula por la red** para detectar amenazas.  
- El **HIDS (Host Intrusion Detection System)** se instala en **equipos individuales (hosts)** y supervisa la actividad interna (procesos, archivos, logs).  

---

### **Pregunta 3**
**Rellene el espacio en blanco:**  
El componente _____ de una firma IDS incluye información sobre el tráfico de red.

**✔ Respuesta correcta:**  
**Encabezado**

**💡 Explicación:**  
El **encabezado** de una firma IDS define los detalles del tráfico monitoreado:  
- **Dirección IP de origen y destino**  
- **Puertos**  
- **Protocolo**  
- **Dirección del flujo del tráfico**

---

### **Pregunta 4**
**Un analista crea una firma Suricata para identificar amenazas basándose en la dirección del tráfico de red. ¿Qué opción de regla debe usar?**

**✔ Respuesta correcta:**  
**Flujo (flow)**

**💡 Explicación:**  
La opción `flow:` se utiliza para **emparejar la dirección del tráfico** (por ejemplo, de cliente a servidor).  
Permite definir si el tráfico fluye hacia el servidor (`to_server`), hacia el cliente (`to_client`), o en ambos sentidos.

---

### 🏁 **Conclusión general**
Este conjunto de preguntas refuerza conceptos esenciales sobre:
- **Telemetría de red**
- **Tipos de sistemas IDS (NIDS vs HIDS)**
- **Estructura de una firma IDS (acción, encabezado, opciones)**
- **Uso de opciones clave en Suricata (flow, content, msg, sid, rev)**

Estas habilidades son fundamentales para desempeñarse eficazmente como **Analista de Seguridad Cibernética** y comprender cómo funcionan las alertas y detecciones dentro de herramientas como **Suricata**.
