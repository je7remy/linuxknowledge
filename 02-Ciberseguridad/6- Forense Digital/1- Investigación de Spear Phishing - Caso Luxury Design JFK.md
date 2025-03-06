
---

#ForenseDigital #SpearPhishing #Ciberseguridad #HackerMentor #CasoPráctico

---

**Nota de Obsidian: Investigación de Spear Phishing - Caso Luxury Design JFK**  
**Fecha**: Clase previa al curso de informática forense (5-6 de marzo 2025)  
**Profesor**: Jonathan (Experto en informática forense)  
**Plataforma**: Hacker Mentor  

---

### **Contexto del Caso**  
- **Empresa afectada**: Luxury Design JFK (joyería de alta tecnología).  
- **Estafa**: Transferencia de $30,000 a una cuenta falsa tras recibir un correo urgente del "Gerente de Banca Empresarial".  
- **Objetivos de la investigación**:  
  1. Verificar si el correo fue enviado por el remitente real (Juan Pérez, Banco Panamá).  
  2. Identificar la dirección IP de origen del correo.  
  3. Analizar si el enlace o documento adjunto era malicioso.  

---

### **Metodología Forense**  
1. **Recolección de evidencia**:  
   - Cabecera del correo electrónico (fuente clave para rastrear IP y servidores).  
   - Archivo adjunto (factura falsa en PDF con posible malware).  

2. **Herramientas utilizadas**:  
   - **MXToolbox**: Para verificar registros SPF y direcciones IP autorizadas del dominio.  
   - **VirusTotal** y **Hybrid Analysis**: Analizar enlaces y archivos adjuntos.  
   - **IP Trackeronline**: Geolocalización de la dirección IP.  

3. **Pasos clave**:  
   - **Análisis de la cabecera del correo**:  
     - Extracción de la IP de origen (ej: 114.xx.xx.xx, vinculada a Hong Kong).  
     - Comparación con las IPs autorizadas del dominio real (ej: Banco Panamá usa IPs con formato 398.xx.xx.xx).  
   - **Validación del enlace**:  
     - Uso de VirusTotal para detectar reputación maliciosa (ej: categorizado como phishing).  
   - **Hash del archivo adjunto**:  
     - Generación del hash criptográfico (SHA-256) para comparar con bases de datos de amenazas.  

---

### **Hallazgos Principales**  
1. **IP Fraudulenta**:  
   - La IP de origen (114.xx.xx.xx) no estaba asociada al dominio legítimo del banco.  
   - Ubicada en Hong Kong, vinculada a actividad de spoofing.  
2. **Enlace Malicioso**:  
   - Redirigía a un sitio fraudulento que imitaba la página del banco.  
3. **Documento Adjunto**:  
   - Aunque se presentaba como PDF, contenía un ejecutable (.exe) camuflado.  

---

### **Técnicas de Spear Phishing Explicadas**  
- **Suplantación de dominio**: Uso de dominios falsos similares al original (ej: `bancopanamá.com` vs `bancopanáma.com`).  
- **Ingeniería social**: Urgencia en el mensaje para manipular a la víctima.  
- **Herramientas para creación de correos falsos**:  
  - Sitios como **emkei.cz** para simular remitentes legítimos.  

---

### **Recomendaciones de Seguridad**  
1. **Verificación de correos sospechosos**:  
   - Contactar al remitente por otro medio (teléfono, canal oficial).  
   - Analizar cabeceras con herramientas como **Email Header Analyzer**.  
2. **Protección proactiva**:  
   - Usar soluciones antispam y listas negras en entornos corporativos.  
   - Capacitar empleados en identificación de phishing.  
3. **Respuesta ante incidentes**:  
   - Aislar equipos comprometidos.  
   - Analizar memoria RAM y conexiones de red con herramientas como **Process Hacker** o **Wireshark**.  

---

### **Recursos Adicionales**  
- **Plantilla de informe forense**: Incluir cadena de custodia, metodología y hallazgos.  
- **Herramientas mencionadas**:  
  - Sandbox: **Any.Run** (análisis seguro de archivos).  
  - Geolocalización: **IPinfo.io**.  

---
