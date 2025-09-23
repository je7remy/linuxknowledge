
# 📚 Vulnerabilidades, Exposiciones y CVE

### 🔑 Diferencia entre **Vulnerabilidad** y **Exposición**

- **Vulnerabilidad** → una **debilidad técnica** que puede ser explotada.
    
    - Ejemplo: software sin parche, puerto abierto, mala configuración.
        
- **Exposición** → un **error que aumenta el riesgo** aunque no sea un fallo técnico en sí.
    
    - Ejemplo: colocar un documento cerca de una ventana abierta → no está roto, pero está mal ubicado y expuesto.
        

---

### 📖 **Lista CVE (Common Vulnerabilities and Exposures)**

- Es un **diccionario abierto** de vulnerabilidades y exposiciones conocidas.
    
- Creado en **1999 por MITRE Corporation** (organización sin fines de lucro patrocinada por el gobierno de EE. UU.).
    
- Objetivo: **identificar y categorizar vulnerabilidades** con un estándar global.
    

---

### 🛡️ **Proceso de revisión y asignación**

1. La vulnerabilidad debe ser **independiente** de otros problemas.
    
2. Debe reconocerse como un **riesgo potencial de seguridad**.
    
3. Debe presentarse con **pruebas que la respalden**.
    
4. Solo puede afectar a **una base de código específica** (ejemplo: Chrome Desktop vulnerable ≠ Chrome Android).
    

👉 Si cumple con todo, una **CNA (CVE Numbering Authority)** asigna un **ID CVE**.

---

### 📊 **NVD (National Vulnerability Database – NIST)**

- Complementa a la lista CVE.
    
- Usa el **CVSS (Common Vulnerability Scoring System)** para medir severidad.
    
- Escala de **0 a 10**:
    
    - **<4.0** → bajo riesgo (no urgente).
        
    - **4.0 – 6.9** → medio.
        
    - **7.0 – 8.9** → alto.
        
    - **≥9.0** → crítico (requiere corrección inmediata).
        

👉 CVSS ayuda a priorizar: qué parche instalar primero, qué actualización no puede esperar.

---

### 🌍 **Importancia global**

- La lista CVE y el CVSS son usados mundialmente por:
    
    - Equipos de seguridad.
        
    - Empresas tecnológicas.
        
    - Investigadores y hackers éticos.
        
- Permiten una **colaboración internacional** para mejorar defensas y priorizar incidentes.
    

---

✅ **Conclusión:**  
El sistema CVE + NVD + CVSS es la columna vertebral de la **gestión moderna de vulnerabilidades**. Proporciona un lenguaje común, criterios claros y una escala para medir y priorizar riesgos.

---

### **Pregunta**

**¿Qué criterios deben cumplirse antes de optar a una identificación CVE®? (3 respuestas)**

✅ **Las vulnerabilidades deben reconocerse como un riesgo potencial para la seguridad**

- El CVE (Common Vulnerabilities and Exposures) solo cataloga debilidades que realmente suponen un **riesgo de seguridad**.
    
- Si no afecta la seguridad, no califica como CVE.
    

✅ **Las vulnerabilidades solo deben afectar a una única base de código**

- El CVE identifica vulnerabilidades **concretas** y **únicas**, no problemas generales ni múltiples proyectos al mismo tiempo.
    
- Ejemplo: una falla en el código de _Apache HTTP Server_ recibe un CVE específico, separado de otra falla en _Nginx_.
    

✅ **Las vulnerabilidades deben presentarse con pruebas que las respalden**

- Debe existir evidencia técnica verificable: PoC (proof of concept), logs, informes técnicos.
    
- Sin pruebas, no se asigna un CVE porque podría ser un reporte falso o sin impacto.
    

❌ **Las vulnerabilidades deben explotarse antes de informar**

- No es requisito. Un CVE puede asignarse aunque la vulnerabilidad aún no haya sido explotada, siempre que represente un **riesgo real**.
    

---

👉 En resumen:  
Un CVE se asigna si la vulnerabilidad **(1)** representa un riesgo de seguridad, **(2)** afecta a una sola base de código y **(3)** tiene pruebas que la respalden.

