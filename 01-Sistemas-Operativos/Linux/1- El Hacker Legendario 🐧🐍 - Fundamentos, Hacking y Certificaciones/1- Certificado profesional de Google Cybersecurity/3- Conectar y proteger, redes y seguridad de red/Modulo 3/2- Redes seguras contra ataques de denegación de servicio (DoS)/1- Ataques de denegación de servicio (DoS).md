
## 🛡️ Ataques de Denegación de Servicio (DoS / DDoS)

### 🔹 ¿Qué es un ataque DoS?

Un **ataque de denegación de servicio (DoS)** tiene como objetivo **inundar un servidor o red con tráfico no deseado**, para que **no pueda responder a solicitudes legítimas**.

- **Objetivo:** Interrumpir operaciones normales de una organización.
    
- **Consecuencias:** Pérdida de funcionalidad, tiempo, dinero y vulnerabilidad a otros ataques.
    

---

### 🔹 ¿Qué es un ataque DDoS?

Un **ataque de denegación de servicio distribuido (DDoS)** es una variante de DoS donde **varios dispositivos (bots)** desde diferentes ubicaciones envían tráfico no deseado simultáneamente.

- **Ventaja para el atacante:** Multiplica la intensidad del ataque.
    
- **Ejemplo real:** Un paquete diseñado para forzar a un router a gastar más tiempo procesando solicitudes específicas.
    

---

## 📶 Tipos comunes de ataques DoS

### 1. SYN Flood 🌀

- **Objetivo:** Abrumar al servidor con solicitudes SYN sin completar el protocolo TCP.
    
- **Funcionamiento:**
    
    1. El atacante envía muchas solicitudes SYN.
        
    2. El servidor responde con SYN/ACK y mantiene el puerto abierto.
        
    3. Nunca se envía el ACK final.
        
- **Resultado:** Los puertos se saturan y el servidor no puede manejar nuevas conexiones.
    

---

### 2. ICMP Flood 📡

- **Protocolo usado:** ICMP (Internet Control Message Protocol)
    
- **Función original:** Diagnóstico de errores entre dispositivos (ej. PING).
    
- **Ataque:** El atacante envía repetidas solicitudes ICMP, forzando respuestas del servidor.
    
- **Resultado:** Consumo de ancho de banda, caída del servidor.
    

---

### 3. Ping of Death 💥

- **Técnica:** Se envía un **paquete ICMP sobredimensionado** (> 64 KB).
    
- **Efecto:** El sistema receptor no puede manejarlo, lo que provoca su **bloqueo o caída**.
    
- **Analogía:** Como lanzar una piedra gigante sobre un hormiguero: colapsa el sistema.
    

---

## 🧠 Conclusión

- Los **ataques DoS y DDoS** afectan la **disponibilidad** de los servicios de red.
    
- Explotan protocolos comunes como **TCP** y **ICMP** para colapsar la infraestructura.
    
- Entenderlos es esencial para **proteger redes corporativas** y mantener la continuidad operativa.
    

---

### 📝 Pregunta de evaluación

**Rellene el espacio en blanco:**  
Un ataque **_____** se produce cuando un atacante envía a un dispositivo o sistema paquetes ICMP sobredimensionados que superan los 64 KB.

**Opciones:**

- 🔘 Ping de la muerte
    
- 🔘 Inundación ICMP (Protocolo de mensajes de control de Internet)
    
- 🔘 Denegación de servicio distribuida (DDoS)
    
- 🔘 SYN flood (sincronización)
    

✅ **Respuesta correcta:**  
**Ping de la muerte**  
_Un ataque Ping de la muerte es un tipo de ataque DoS causado cuando un hacker hace ping a un sistema enviándole un paquete ICMP sobredimensionado que supera los 64 KB._

---

