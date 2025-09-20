
---

# 🔑 Controles de Acceso – Autorización

La **autorización** es el proceso que determina **qué puede hacer un usuario o sistema** después de haberse autenticado.

Trabaja en conjunto con la **autenticación**:

- La autenticación responde a **“¿Quién eres?”**.
    
- La autorización responde a **“¿Qué estás autorizado a hacer?”**.
    

---

## ⚖️ Principios Clave de la Autorización

1. **Principio de privilegio mínimo**
    
    - El acceso a la información o sistemas debe durar solo el tiempo necesario.
        
    - Reduce riesgos al limitar lo que un usuario o proceso puede realizar.
        
2. **Separación de funciones**
    
    - Evita que una sola persona tenga permisos excesivos que le permitan abusar de un sistema.
        
    - Ejemplo:
        
        - Un empleado de atención al cliente no debería evaluar su propio desempeño.
            
        - Un desarrollador no debería probar exclusivamente un sistema de seguridad que él mismo creó.
            

👉 Estos principios aplican a **usuarios, redes, bases de datos, procesos y sistemas completos**.

---

## 🌐 Ejemplos de Controles de Autorización

- **HTTP Basic Auth**
    
    - Envío de credenciales (usuario y contraseña) en texto plano con cada solicitud.
        
    - Considerado vulnerable → hoy en día se sustituye por **HTTPS** (cifrado).
        
- **OAuth (Open Authorization)**
    
    - Estándar abierto para autorización segura.
        
    - Usa **tokens de API** en lugar de compartir credenciales directamente.
        
    - Ejemplo: Usar tu cuenta de Google para registrarte en otra aplicación.
        

### 🛡️ Ventajas de OAuth

- Minimiza el riesgo de exposición de contraseñas.
    
- Los **tokens de API** contienen:
    
    - Identidad del usuario.
        
    - Permisos autorizados.
        
    - Datos adicionales de validación.
        
- Funciona con **MFA** si está habilitado en el servicio original (ejemplo: Google).
    

---

## 📌 Conclusión

La **autorización** garantiza que:

- El usuario autenticado solo acceda a lo que le corresponde.
    
- Se apliquen los principios de **mínimo privilegio** y **separación de funciones**.
    
- Se refuerce la seguridad mediante protocolos modernos como **HTTPS y OAuth**.
    

➡️ El siguiente paso en el framework AAA (Autenticación, Autorización y Contabilidad) es la **Contabilidad (Auditoría y seguimiento del acceso)**.

---

### ❓ Pregunta

Los controles de autorización están vinculados a dos principios de Seguridad. Uno es el principio de privilegio mínimo. ¿Cuál es el otro?

- Separación de funciones ✅
    
- El framework AAA
    
- Autenticación básica HTTP
    
- OAuth
    

---

### ✅ Respuesta Correcta

**Separación de funciones**

---

### 📝 Justificación

Los **controles de autorización** garantizan que los usuarios tengan acceso solo a lo estrictamente necesario y durante el tiempo adecuado. Para ello se basan en dos principios fundamentales:

1. **Principio de privilegio mínimo**
    
    - Los usuarios solo deben tener acceso a los recursos que necesitan para realizar sus funciones, ni más ni menos.
        
    - Minimiza el riesgo de accesos indebidos o abusos.
        
2. **Separación de funciones**
    
    - Evita que un mismo usuario tenga múltiples privilegios que, combinados, le permitan realizar un uso indebido del sistema.
        
    - Ejemplo: Un desarrollador no debe ser el único responsable de probar la seguridad de su propio código.
        

---

📌 En conjunto, estos principios reducen riesgos de **fallos, abusos y accesos indebidos**, reforzando la seguridad de la información en cualquier organización.

---
