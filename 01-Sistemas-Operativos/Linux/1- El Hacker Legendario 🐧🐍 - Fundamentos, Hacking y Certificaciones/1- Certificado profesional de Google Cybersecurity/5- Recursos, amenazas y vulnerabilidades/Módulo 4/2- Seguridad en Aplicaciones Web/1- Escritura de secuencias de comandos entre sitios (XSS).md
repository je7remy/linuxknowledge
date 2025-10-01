
# Explotaciones Basadas en la Web y Ataques XSS

## Introducción

- Todo el software malicioso necesita **ser entregado al objetivo** antes de funcionar.
    
- Métodos comunes de distribución:
    
    - **Phishing** y otras técnicas de ingeniería social.
        
    - **Exploits basados en la web**, que aprovechan fallas en aplicaciones.
        

---

## ¿Qué son las explotaciones basadas en la web?

- Son **códigos o comportamientos malintencionados** que aprovechan fallos de programación en aplicaciones web.
    
- Objetivo: obtener **información personal confidencial**.
    
- Razón de vulnerabilidad: las aplicaciones web interactúan con muchos usuarios en varias redes.
    
- Ejemplo común: **ataques de inyección**.
    

---

## Ataques de Inyección

- Insertan **código malicioso** en una aplicación vulnerable.
    
- La aplicación parece funcionar normalmente, pero el código se ejecuta en **segundo plano**.
    
- Causa principal: las aplicaciones **reciben entradas de datos** (texto, clics, parámetros compartidos).
    

### Validación de datos

- Ejemplo: una aplicación espera un **número de teléfono**.
    
- Debe validar que el usuario ingrese solo dígitos y un máximo de 10 caracteres.
    
- Problema: es difícil para los desarrolladores **cubrir todos los escenarios** de validación.
    

---

## XSS – Cross-Site Scripting (Secuencias de Comandos entre Sitios)

- Un tipo de **ataque de inyección** que inserta código en un sitio o aplicación vulnerable.
    
- Usualmente explota **HTML y JavaScript**.
    
- Puede dar acceso a:
    
    - Cookies de sesión.
        
    - Geolocalización.
        
    - Cámaras web y micrófonos.
        

---

## Tipos de XSS

### 1. **XSS Reflejado**

- El script malicioso se envía al servidor y se refleja en la respuesta.
    
- Ejemplo: barra de búsqueda.
    
- Flujo:
    
    1. El atacante envía un **enlace malicioso** a la víctima.
        
    2. La víctima hace clic → el servidor responde con la secuencia inyectada.
        
    3. El navegador ejecuta el script y devuelve datos (cookies de sesión) al atacante.
        

---

### 2. **XSS Almacenado**

- El script malicioso se **inyecta directamente en el servidor**.
    
- Se activa cuando un usuario visita el sitio, sin necesidad de enlaces especiales.
    
- Ejemplo: elementos como imágenes o botones cargados en la página.
    
- Peligro: el usuario **no tiene forma de saber** que el sitio está infectado.
    

---

### 3. **XSS Basado en DOM**

- DOM = **Modelo de Objetos de Documento**, es decir, el código fuente del sitio.
    
- El script malicioso se encuentra en el **lado del cliente** (navegador).
    
- No necesita enviarse al servidor.
    
- Ejemplo:
    
    - Una URL con parámetros que reflejan la entrada del usuario (p. ej., selección de temas de color).
        
    - El atacante **modifica el parámetro** con JavaScript malicioso.
        
    - El navegador procesa el HTML y ejecuta el código.
        

---

## Impacto

- Los atacantes usan XSS para **robar información confidencial**.
    
- Los analistas de seguridad deben conocer bien este tipo de ataques por inyección.
    
- Sin embargo, los XSS no son los únicos ataques basados en inyección, y se verán más en adelante.
    


---

### ❓ Pregunta

**¿Cuáles de los siguientes son tipos de ataques de secuencia de comandos entre sitios (XSS)?** _(Seleccione tres respuestas)_

- **Basado en DOM** ✅
    
- **Almacenado** ✅
    
- Criptojacking
    
- **Reflejado** ✅
    

---

### ✔️ Respuesta Correcta

Los tres tipos de ataques **XSS** son:

1. **Reflejado** → El script malicioso se envía al servidor y se ejecuta en la respuesta.
    
2. **Almacenado** → El script se guarda en el servidor y se activa cuando otros usuarios visitan el sitio.
    
3. **Basado en DOM** → El script está en el cliente (navegador), ejecutándose desde el código fuente o parámetros de la URL.
    

---

