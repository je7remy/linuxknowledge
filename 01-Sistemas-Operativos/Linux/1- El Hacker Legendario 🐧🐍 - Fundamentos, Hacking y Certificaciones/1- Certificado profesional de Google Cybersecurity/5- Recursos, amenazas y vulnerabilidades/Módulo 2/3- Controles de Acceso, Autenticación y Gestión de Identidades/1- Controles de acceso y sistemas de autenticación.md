---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Controles de acceso y sistemas de autenticación

# 🛡️ Controles de Acceso y Autenticación

## Introducción

Proteger los datos es una característica fundamental de los **controles de seguridad**.  
Cuando se trata de mantener la información a salvo, **el hash y el cifrado** son herramientas poderosas, aunque limitadas.  
Pero **gestionar quién o qué tiene acceso a la información** también es clave para salvaguardarla.

👉 Aquí entran en juego los **Controles de acceso**, que:

- Mantienen la **confidencialidad**, **integridad** y **disponibilidad** de los datos (principios **CIA**).
    
- Garantizan que los usuarios obtengan rápidamente la información que necesitan.
    
- Se dividen en tres funciones del **framework AAA**:
    
    1. **Autenticación** → ¿Quién eres?
        
    2. **Autorización** → ¿Qué puedes hacer?
        
    3. **Contabilidad (Auditoría)** → ¿Qué hiciste?
        

---

## 🔑 Autenticación

Los sistemas de autenticación son el primer paso del framework.  
Su función es **verificar la identidad del usuario** preguntando: **¿Quién es usted?**

Existen **tres factores de autenticación principales**:

1. **Conocimiento** → Algo que el usuario **sabe** (ejemplo: contraseña, PIN, respuesta de seguridad).
    
2. **Propiedad** → Algo que el usuario **posee** (ejemplo: código OTP, token enviado por SMS o correo).
    
3. **Características biométricas** → Algo que el usuario **es** (ejemplo: huella digital, reconocimiento facial, escaneo de iris).
    

👉 La autenticación es exitosa solo si las credenciales coinciden con las registradas en el sistema.

---

## 🔗 Inicio de Sesión Único (SSO)

- **Definición**: Tecnología que combina varios inicios de sesión en uno solo.
    
- **Beneficio**: Facilita la experiencia del usuario al autenticarse una sola vez para acceder a múltiples recursos.
    
- **Ejemplo**: Ingresar al correo de la empresa y tener acceso automático a la suite de aplicaciones internas.
    

⚠️ **Riesgo**:

- Si el sistema depende de **un solo factor de autenticación**, una brecha compromete todos los accesos.
    

---

## 🔒 Autenticación Multifactor (MFA)

- **Definición**: Requiere que un usuario verifique su identidad de **dos o más formas** antes de acceder.
    
- **Ejemplo**: Contraseña (**conocimiento**) + código OTP (**propiedad**) o huella digital (**biometría**).
    

✅ **Ventajas**:

- Reduce el riesgo de acceso no autorizado.
    
- Hace más difícil que un atacante suplante la identidad de un usuario legítimo.
    

---

## 🔐 SSO + MFA = Seguridad y Comodidad

- El **SSO** agiliza el acceso.
    
- El **MFA** lo fortalece.
    
- Usados en conjunto, ofrecen un **equilibrio entre usabilidad y seguridad** en los sistemas modernos.
    

---

## 📌 Próximo tema

Ahora que entendemos la **autenticación**, el siguiente paso en el **framework AAA** es la **Autorización**.

---

## ❓ Pregunta

**¿Cuáles son los tres factores de autenticación?**  
Seleccione **tres respuestas**.

- Algoritmo
    
- **Responsabilidad (Propiedad)** ✅
    
- **Característica** ✅
    
- **Conocimientos** ✅
    

---

## ✅ Respuesta Correcta

Los tres factores de autenticación son:

1. **Conocimientos** → Algo que el usuario sabe (ejemplo: contraseña, PIN, respuesta secreta).
    
2. **Propiedad (Responsabilidad)** → Algo que el usuario posee (ejemplo: token, tarjeta, código OTP).
    
3. **Característica** → Algo que el usuario es (ejemplo: huella digital, reconocimiento facial, escaneo de iris).
    

---

## 📝 Justificación

La **autenticación** se basa en estos tres factores para verificar la identidad de un usuario.

- **Conocimiento** protege con datos recordados.
    
- **Propiedad** aporta un elemento físico o digital en posesión del usuario.
    
- **Característica biométrica** confirma la identidad mediante rasgos únicos e intransferibles.
    

👉 Estos tres factores se pueden combinar en la **Autenticación Multifactor (MFA)** para reforzar la seguridad.

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ➡️ Siguiente: [[2- El auge de SSO y MFA]]
