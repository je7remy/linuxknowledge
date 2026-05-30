---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Fundamentos de la criptografía

# 🔐 Fundamentos de la Criptografía

## 🌐 Internet y la privacidad

Internet es un sistema abierto y público con una gran cantidad de datos que fluyen a través de él.  
Aunque todos enviamos y almacenamos información en línea, hay cierta información que decidimos mantener en privado.

En materia de seguridad, este tipo de datos se conoce como **información de identificación personal (PII)**.

### 📌 Ejemplos de PII

- Nombre de una persona
    
- Información médica
    
- Información financiera
    
- Fotos
    
- Correos electrónicos
    
- Huellas dactilares
    

👉 Mantener la privacidad de la PII en línea es difícil. Para ello se necesitan **controles de seguridad adecuados**.

---

## 🔑 La criptografía

Uno de los principales controles de seguridad es la **criptografía**, que consiste en **transformar la información en una forma ilegible para terceros no deseados**.

### Proceso básico

1. **Texto plano** → Información original y legible.
    
2. **Cifrado** → Se transforma en **texto cifrado** (ilegible).
    
3. **Desencriptación** → Se devuelve a **texto plano** para hacerlo comprensible otra vez.
    

Ejemplo: enviar un correo a un amigo y protegerlo mediante encriptación.

---

## 🏺 Orígenes históricos

La criptografía se utiliza desde hace siglos.  
Uno de los primeros métodos fue el **Cifrado de César**, usado por Julio César en el siglo I a.C. para comunicarse con sus generales.

### ⚙️ Cómo funciona

- Es un algoritmo simple que **desplaza las letras del alfabeto** un número fijo de posiciones.
    
- Ejemplo con desplazamiento de 3:
    
    - A → D
        
    - B → E
        
    - C → F
        
- Mensaje: **hola** → **khoor**
    

---

## 🔑 La importancia de la clave

- Un **cifrado** es el algoritmo que transforma la información.
    
- Una **clave criptográfica** es el mecanismo que permite descifrar el mensaje.
    
- En el ejemplo de César, la clave sería **“desplazamiento de 3”**.
    

👉 Todas las formas modernas de encriptación se basan en **cifrado + clave**.

---

## ⚠️ Limitaciones del Cifrado de César

1. **Fuerza bruta**: solo 26 posibles desplazamientos en el alfabeto inglés, fácil de romper probando todas las opciones.
    
2. **Una sola clave**: si se pierde o es robada, cualquiera puede descifrar el mensaje.
    

---

## 🔐 Seguridad de las claves

- No almacenar claves en lugares públicos.
    
- Compartirlas por separado de la información cifrada.
    
- Mantener un control riguroso sobre ellas.
    

---

## 🚀 Criptografía moderna

El **Cifrado de César** es solo un ejemplo histórico.  
Debido a sus defectos, hoy se usan **algoritmos mucho más complejos y seguros** para proteger la privacidad de la información en línea.

👉 El siguiente paso es explorar cómo funcionan los **algoritmos criptográficos modernos**.

---

### ❓ Pregunta

**Rellene el espacio en blanco:**  
**_____ es el proceso de transformar la información en una forma que los lectores no intencionados no puedan entender.**

Opciones:

- Algoritmo
    
- Criptografía ✅
    
- Descriptación
    
- Cifrado
    

---

### ✅ Respuesta correcta:

**Criptografía**

**Justificación:**  
La criptografía es el proceso de transformar la información en una forma que los lectores no intencionados no puedan entender.  
Dentro de la criptografía se utiliza un **cifrado** para ocultar o encriptar la información.

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ➡️ Siguiente: [[2- Infraestructura de clave pública]]
