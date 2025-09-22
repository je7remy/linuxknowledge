
# 📄 Evaluación de Seguridad – Resumen con Respuestas Explicadas

---

### **Pregunta 1**

**¿Qué factores utilizan los sistemas de autenticación para verificar la identidad de un usuario? (3 respuestas)**

- Conocimientos → algo que sabes (contraseña, PIN).
    
- Posesión (traducido como “Responsabilidad”) → algo que tienes (token, tarjeta, móvil).
    
- Características → algo que eres (huella, rostro, iris).  
    👉 Los tres forman el modelo clásico: _algo que sabes, algo que tienes, algo que eres_.
    

---

### **Pregunta 2**

**Beneficios de la implementación de inicio de sesión único (SSO) (2 respuestas)**

- Proporcionar mejor experiencia de usuario.
    
- Simplificar gestión de usuarios.  
    👉 Reduce carga de contraseñas y facilita la administración centralizada.
    

---

### **Pregunta 3**

**Una empresa minorista divide funciones entre empleados (comprar, aprobar, pagar). ¿Qué principio aplica?**

- Separación de funciones.  
    👉 Evita que una persona sola pueda manipular todo un proceso crítico.
    

---

### **Pregunta 4**

**Categorías de controles de acceso (3 respuestas)**

- Autenticación → ¿Quién eres?
    
- Autorización → ¿Qué puedes hacer?
    
- Contabilidad (Accounting) → ¿Qué hiciste y cuándo?  
    👉 Conocido como el modelo AAA.
    

---

### **Pregunta 5**

**¿Qué credencial utiliza OAuth para autenticar a los usuarios?**

- Token de API.  
    👉 Credencial digital que se comparte entre proveedor y servicio sin exponer la contraseña.
    

---

### **Pregunta 6**

**Categorías de controles de seguridad (3 respuestas)**

- Técnico → firewalls, antivirus, cifrado.
    
- Operativo → respuesta a incidentes, formación, políticas de uso.
    
- Administrativo (Dirección) → normas, gestión de riesgos, políticas internas.
    

---

### **Pregunta 7**

**Responsabilidades de un custodio de datos (3 respuestas)**

- Proteger datos en reposo.
    
- Proteger datos en uso.
    
- Proteger datos en tránsito (transporte seguro).  
    👉 La misión es preservar confidencialidad, integridad y disponibilidad.
    

---

### **Pregunta 8**

**¿Qué tipo de encriptación es más lenta porque usa par de claves?**

- Asimétrica.  
    👉 Ejemplo: RSA. Usa clave pública y privada, más segura pero más lenta que la simétrica.
    

---

### **Pregunta 9**

**¿Cómo verificar integridad de un archivo crítico?**

- Comparando el valor hash del archivo con un hash conocido.  
    👉 Si el archivo cambia, el hash también.
    

---

### **Pregunta 10**

**Un _____ se utiliza en PKI para probar identidad.**

- Certificado digital.  
    👉 Emitido por una CA, asocia claves criptográficas con una identidad.
    

---

### **Pregunta 11**

**Dos formas de identificación más usadas en autenticación (2 respuestas)**

- Nombre de usuario.
    
- Contraseña.  
    👉 Son el estándar global más común.
    

---

### **Pregunta 12**

**Ventaja de la autenticación multifactor frente a SSO**

- Requiere más de una forma de identificación.  
    👉 Aumenta la seguridad al combinar diferentes factores.
    

---

### **Pregunta 13**

**Separación de funciones en empresa de transporte (2 respuestas)**

- Un empleado aprueba pedidos de compra.
    
- Un empleado archiva pedidos de compra.  
    👉 Así no se concentran funciones críticas en la misma persona.
    

---

### **Pregunta 14**

**Tecnología para establecer la solicitud de un usuario a un servidor:**

- Autenticación básica.  
    👉 Método HTTP simple con usuario/contraseña en Base64.
    

---

### **Pregunta 15**

**¿Qué práctica describe monitorizar los registros de acceso?**

- Auditoría.  
    👉 Revisar logs para detectar anomalías o incidentes.
    

---

### **Pregunta 16**

**Funciones que son controles de seguridad operativos (2 respuestas)**

- Proporcionar entrenamiento de concienciación en seguridad.
    
- Responder a una alerta de incidente.  
    👉 Procesos y acciones humanas, no técnicas.
    

---

### **Pregunta 17**

**Un suscriptor de noticias, como propietario de sus datos, ¿qué debe poder hacer? (3 respuestas)**

- Detener su suscripción.
    
- Revisar usuario y contraseña.
    
- Actualizar datos de pago.  
    👉 Controla su cuenta, pero no puede modificar contenido del sitio.
    

---

### **Pregunta 18**

**¿Qué tipo de encriptación es más lenta por par de claves?**

- Asimétrica.  
    👉 Igual que la 8, respuesta consistente.
    

---

### **Pregunta 19**

**Uso principal de hash en seguridad:**

- Verificar integridad de datos.  
    👉 Un cambio altera el hash.
    

---

### **Pregunta 20**

**Primer paso ante alerta de múltiples intentos fallidos de inicio de sesión:**

- Revisar registros de acceso (contabilización).  
    👉 Antes de actuar drásticamente, se valida con evidencia.
    

---

💡 Con estas 20 preguntas + explicaciones tienes un **resumen maestro** de los conceptos clave:

- Controles de seguridad (técnicos, operativos, administrativos).
    
- Privilegios mínimos, separación de funciones.
    
- Criptografía simétrica vs asimétrica.
    
- Hash e integridad.
    
- AAA (autenticación, autorización, contabilidad).
    
- SSO vs MFA.
    
- PKI y certificados digitales.
    
- Auditoría de registros.
    

---
