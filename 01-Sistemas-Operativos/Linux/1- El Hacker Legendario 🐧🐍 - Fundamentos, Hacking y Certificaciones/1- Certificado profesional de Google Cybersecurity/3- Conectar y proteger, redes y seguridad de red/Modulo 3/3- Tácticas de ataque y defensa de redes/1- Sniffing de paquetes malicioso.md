---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Sniffing de paquetes malicioso

## 🎯 **Sniffing de Paquetes - Contenido Completo del Video**

---

### 🔍 ¿Qué es el sniffing de paquetes?

- Es la práctica de usar herramientas de software para **observar los datos** mientras viajan por una red.
    
- Sirve para:
    
    - **Analizar incidentes de seguridad**
        
    - **Depurar problemas de red**
        
- **Los analistas de ciberseguridad** lo utilizan de forma legítima.
    
- **Los actores maliciosos** lo usan para **espiar paquetes de datos** que **no se les han enviado**.
    

---

### 📦 ¿Qué contienen los paquetes de datos?

- **Encabezado:** contiene IP del remitente y del receptor.
    
- ✅ **Cuerpo:** contiene información valiosa como:
    
    - Nombres
        
    - Fechas de nacimiento
        
    - Mensajes personales
        
    - Información financiera
        
    - Números de tarjetas de crédito
        

---

### 🧨 ¿Cómo atacan con sniffing?

- El atacante **se interpone en medio de una conexión legítima**.
    
- Usa software o hardware para capturar y examinar paquetes.
    
- Pueden incluso **modificar los datos**, por ejemplo:
    
    - Cambiar el número de cuenta bancaria del destinatario.
        
- Es como si **abrieran y alteraran una carta antes de entregarla**.
    

---

### 🧭 Tipos de sniffing:

#### 📥 **Sniffing Pasivo**

- Solo **lee los datos en tránsito** sin modificarlos.
    
- Ocurre en redes donde **todo el tráfico es visible** (por ejemplo, redes con hub).
    
- 🧾 Ejemplo: Un cartero que **lee el correo** antes de entregarlo, sin modificarlo.
    

#### 🔁 **Sniffing Activo**

- **Manipula los paquetes** en tránsito.
    
- Puede:
    
    - Inyectar paquetes falsos.
        
    - Redirigir tráfico a puertos no deseados.
        
    - **Alterar la información** del paquete.
        
- 🧾 Ejemplo: Un vecino que le dice al cartero “yo lo entrego”, pero **lee y cambia la carta** antes de dejarla en el buzón.
    

---

### 🔐 ¿Cómo prevenir el sniffing malicioso?

1. ✅ **Usar VPN (Virtual Private Network):**
    
    - Cifra los datos mientras viajan por la red.
        
    - Un atacante puede interceptar el tráfico, **pero no puede leerlo**.
        
2. ✅ **Navegar por sitios con HTTPS:**
    
    - HTTPS utiliza **SSL/TLS** para cifrar datos.
        
    - Previene el espionaje durante la transmisión.
        
3. ✅ **Evitar redes WiFi abiertas (no protegidas):**
    
    - Las redes públicas (cafeterías, aeropuertos) **no tienen cifrado**.
        
    - Cualquiera puede ver el tráfico de otros usuarios.
        
    - Solución: **No usar redes públicas sin VPN.**
        

---

### ✅ Conclusión

Como profesional de seguridad:

- Debes **comprender tanto el uso legítimo como el malicioso** del sniffing.
    
- Estar preparado para **detectar, prevenir y responder** a intentos de espionaje en red.
    
- Utilizar herramientas defensivas como VPN y HTTPS.
    
- Educar a otros sobre los **riesgos de las redes públicas**.
    

---


**¿Qué parte de un paquete de datos podría contener información valiosa sobre los Datos en tránsito?**

🔘 **Opciones:**

- Pie de página
    
- Encabezado  
    ✅ **Cuerpo**
    
- Red
    

---

✅ **Respuesta correcta:** **Cuerpo**

> El cuerpo de un paquete de datos (también llamado "payload") puede contener datos confidenciales como credenciales, información personal, mensajes o archivos. Es el objetivo principal de los atacantes que interceptan datos en tránsito.

---

---

## Navegación

- ⬆️ Carpeta: [[_3- Conectar y proteger, redes y seguridad de red|3- Conectar y proteger, redes y seguridad de red]]
- ➡️ Siguiente: [[2- Suplantación de IP]]
