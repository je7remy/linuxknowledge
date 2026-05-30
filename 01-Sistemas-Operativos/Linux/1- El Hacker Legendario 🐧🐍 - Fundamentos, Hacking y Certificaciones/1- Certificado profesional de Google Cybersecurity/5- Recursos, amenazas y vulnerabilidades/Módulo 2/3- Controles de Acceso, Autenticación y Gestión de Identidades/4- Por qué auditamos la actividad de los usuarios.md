---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Por qué auditamos la actividad de los usuarios

# 📊 Contabilidad en el Framework AAA

La **contabilidad** es la **tercera función** del framework de **Autenticación, Autorización y Contabilización (AAA)**.  
Se centra en **supervisar y registrar el acceso** de los usuarios a los sistemas.

---

## 🔑 Definición

La contabilidad consiste en el **registro de accesos** que recopila datos como:

- **Quién** accedió al sistema.
    
- **Cuándo** lo hizo.
    
- **Qué recursos** utilizó.
    

Los **analistas de seguridad** emplean estos registros para:

- Identificar tendencias (ej. intentos fallidos de inicio de sesión).
    
- Descubrir accesos no autorizados.
    
- Detectar incidentes de seguridad (ej. violación de datos).
    

---

## ⚙️ Funcionamiento de la contabilidad

Cada vez que un usuario entra en un sistema, se inicia una **sesión**, que se registra.

En una sesión ocurren dos acciones clave:

1. **Creación de identificador de sesión (Session ID):**
    
    - Token único que identifica a un usuario y su dispositivo.
        
    - Permanece activo hasta cerrar el navegador o hasta el timeout de la sesión.
        
2. **Intercambio de cookies de sesión:**
    
    - Tokens que validan y determinan la duración de la sesión.
        
    - Permiten que el servidor sepa qué información mostrar al usuario.
        
    - Aumentan la seguridad al no transmitir credenciales sensibles (usuario/contraseña).
        

---

## ⚠️ Vulnerabilidades: Secuestro de sesión

Aunque las cookies fortalecen la seguridad, presentan riesgos:

- **Secuestro de sesión (Session Hijacking):**
    
    - Ocurre cuando un atacante roba un ID de sesión.
        
    - Permite al atacante **suplantar al usuario legítimo**.
        
    - Consecuencias: robo de dinero, datos privados o acceso a múltiples sistemas (si se roba una cookie de inicio de sesión único, SSO).
        

---

## 🛡️ Importancia de la Contabilidad

- Permite **detectar actividades inusuales** en registros.
    
- Ayuda a identificar accesos indebidos o robos de información.
    
- Proporciona **estadísticas valiosas** que contribuyen a la seguridad global de la información.
    

---

✅ En resumen, la **contabilidad** no solo monitorea el acceso, sino que también ayuda a **prevenir, detectar y responder a incidentes de seguridad** mediante el análisis de registros.

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ⬅️ Anterior: [[3- Los mecanismos de autorización]]
- ➡️ Siguiente: [[5- Tim - Encontrar un propósito en la protección de los recursos]]
