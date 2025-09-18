
# 🔑 Infraestructura de Clave Pública (PKI)

## 🌐 ¿Qué es la PKI?

- **Infraestructura de Clave Pública (PKI)** es un **marco de encriptación** que asegura el intercambio de información en línea.
    
- Hace que el acceso a la información sea **rápido, fácil y seguro**.
    
- Funciona en **dos pasos principales**:
    
    1. **Intercambio de información cifrada** (asimétrica, simétrica o ambas).
        
    2. **Establecimiento de confianza** mediante certificados digitales.
        

---

## 🔒 Encriptación asimétrica

- Usa un **par de claves**:
    
    - **Clave pública** → se comparte libremente, sirve para **enviar información cifrada**.
        
    - **Clave privada** → la conserva solo el propietario, sirve para **descifrar la información**.
        
- Ejemplo: una caja que solo puede llenarse con la clave pública, pero abrirse completamente solo con la clave privada.
    
- ✅ Ventaja: seguridad en el intercambio.
    
- ⚠️ Desventaja: más **lenta** que otros métodos.
    

---

## 🔑 Encriptación simétrica

- Usa **una sola clave secreta** para cifrar y descifrar.
    
- Ejemplo: una caja que puede abrirse y cerrarse con la misma llave, la cual debe compartirse entre las personas que la usan.
    
- ✅ Ventaja: **rápida** y eficiente.
    
- ⚠️ Desventaja: menos segura, porque compartir la clave puede exponerla.
    

---

## ⚖️ PKI en acción

La PKI combina **ambos métodos**:

- Al inicio (por seguridad) → usa **cifrado asimétrico** para establecer la conexión.
    
- Después (por velocidad) → usa **cifrado simétrico** para mantener la comunicación.
    

Ejemplo: aplicaciones de chat móvil.

---

## 📜 El problema de la confianza

- Tanto en cifrado simétrico como asimétrico, existe una **vulnerabilidad común**: la clave puede perderse, robarse o usarse indebidamente.
    
- Los humanos diferenciamos en quién confiar, pero las computadoras no.
    
- Aquí entra en juego el **segundo paso de la PKI**: la **confianza mediante certificados digitales**.
    

---

## 🆔 Certificados digitales

- Un **certificado digital** es un archivo que **verifica la identidad** del titular de una clave pública.
    
- Funcionan como una **tarjeta de identificación digital**.
    
- Son emitidos por una **Autoridad Certificadora (CA)** confiable.
    

### 🔎 Proceso de emisión de un certificado digital

1. Una empresa registra su dominio y envía información (nombre, país, clave pública) a la **CA**.
    
2. La CA **verifica la identidad** de la empresa.
    
3. La CA **cifra los datos con su clave privada** y crea un certificado digital.
    
4. El certificado contiene:
    
    - Datos cifrados de la empresa.
        
    - La **firma digital** de la CA como garantía de autenticidad.
        

---

## ✅ Conclusión

La **PKI** resuelve el problema de la confianza al:

1. **Cifrar datos** con algoritmos asimétricos y simétricos.
    
2. **Validar identidades** con certificados digitales.
    

👉 Esto la convierte en un **control de seguridad esencial** para proteger la información en línea.

---

### ❓ Pregunta

La Infraestructura de clave pública (PKI) es un proceso de dos pasos que incluye el intercambio de información encriptada.  
**¿Qué otro paso interviene en el proceso de PKI?**

Opciones:

-  El almacenamiento de la información pública 
    
-  El establecimiento de la confianza mediante certificados digitales 👍
    
-  Los controles de autenticación del cifrado César
    
-  La desencriptación de claves secretas
    

---

### ✅ Respuesta correcta:

**El establecimiento de la confianza mediante certificados digitales**

**Justificación:**  
El proceso de **PKI** implica dos pasos:

1. **Intercambio de información encriptada** (con criptografía simétrica, asimétrica o ambas).
    
2. **Establecimiento de la confianza** mediante el uso de **certificados digitales**.
    

Estos certificados digitales vinculan la **clave pública** con la **identidad verificada** de un sitio web, organización, individuo, dispositivo o servidor, asegurando que la comunicación en línea sea confiable y segura.

---
