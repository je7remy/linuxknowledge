---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Defectos del sistema

# 📘 Repaso: Gestión de Vulnerabilidades, CVE y Defensa en Profundidad

---

### **Pregunta 1**

**¿Cuáles de las siguientes son etapas del proceso de gestión de vulnerabilidades? (2 respuestas)**

- **✅ Identificar vulnerabilidades**
    
- **✅ Preparar las defensas contra las amenazas**
    

**Por qué:**  
La gestión de vulnerabilidades es un proceso **interno y cíclico** que busca encontrar debilidades y aplicar medidas correctivas.  
Incluye 4 pasos:

1. Identificar vulnerabilidades.
    
2. Considerar posibles exploits.
    
3. Preparar defensas.
    
4. Evaluar defensas.
    

Asignar un CVE lo hace MITRE (no es parte del proceso interno de una empresa) y catalogar recursos corresponde a **gestión de activos**, no de vulnerabilidades.

---

### **Pregunta 2**

**Una organización es atacada por una vulnerabilidad hasta entonces desconocida. ¿De qué es un ejemplo este exploit?**

- **✅ Día cero**
    

**Por qué:**  
Un exploit de **día cero** es aquel que aprovecha una vulnerabilidad **recién descubierta**, sin parches ni solución disponible. Se llama así porque el proveedor tiene “cero días” para corregirla.

---

### **Pregunta 3**

**¿Qué capa de la estrategia de defensa en profundidad es una capa de autenticación de usuarios que filtra principalmente el acceso externo?**

- **✅ Perímetro**
    

**Por qué:**  
La **capa perimetral** es la primera línea de defensa. Se encarga de **validar quién entra** al sistema, usando autenticación (usuario/contraseña, VPN, firewalls perimetrales).  
Las otras capas protegen otros aspectos:

- Red → controla tráfico interno.
    
- Punto de conexión → protege dispositivos.
    
- Datos → protege la información crítica.
    

---

### **Pregunta 4**

**Un investigador informa de una vulnerabilidad al CVE®. ¿Qué criterios debe cumplir antes de recibir un ID CVE®? (2 respuestas)**

- **✅ Debe poder arreglarse de forma independiente**
    
- **✅ La presentación debe contar con pruebas que la respalden**
    

**Por qué:**  
El proceso de asignación de un CVE exige que:

1. El fallo sea **independiente** y pueda corregirse sin depender de otras vulnerabilidades.
    
2. Se presenten **pruebas verificables** (PoC, logs, evidencia técnica).
    

No es requisito que afecte a múltiples aplicaciones (de hecho, debe ser específico a una sola base de código) ni que sea desconocido para el desarrollador.

---

---

## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ⬅️ Anterior: [[6- Inteligencia de fuentes abiertas]]
