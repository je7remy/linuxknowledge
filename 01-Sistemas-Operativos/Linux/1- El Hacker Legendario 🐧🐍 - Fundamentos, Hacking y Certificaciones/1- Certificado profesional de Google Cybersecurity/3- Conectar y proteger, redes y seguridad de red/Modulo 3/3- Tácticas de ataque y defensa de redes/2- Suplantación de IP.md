---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Suplantación de IP

## 🔐 **Suplantación de IP (IP Spoofing)**

**Tipo de ataque de red donde un atacante falsifica la IP de origen para hacerse pasar por un sistema autorizado.**

---

### 🧠 ¿Qué busca lograr el atacante?

- Engañar al sistema objetivo para **parecer un dispositivo confiable.**
    
- **Superar firewalls** o reglas de red que bloquean tráfico externo.
    
- **Acceder a recursos restringidos**, interceptar datos o causar interrupciones.
    

---

## 🧨 **Tipos de ataques basados en suplantación de IP:**

---

### 1. 🛣️ **Ataque en ruta**

**(Man-in-the-Middle - MitM)**

- El atacante **se posiciona entre dos dispositivos** legítimos (ej. navegador y servidor).
    
- Rastrea IPs y MACs, luego se **hace pasar por uno de los dispositivos**.
    
- Puede **leer, alterar o interceptar paquetes**.
    

---

### 2. 🔁 **Ataque de repetición**

**(Replay Attack)**

- El atacante **intercepta un paquete válido** y:
    
    - Lo **retransmite más tarde**
        
    - O lo **retrasa intencionalmente**
        
- Busca:
    
    - Confundir el sistema destino
        
    - Repetir acciones como si fuera el usuario legítimo (ej. validaciones de sesión, autenticaciones)
        

---

### 3. 💣 **Ataque de pitufos**

**(Smurf Attack)**

- Es una **combinación de ataque DDoS y suplantación de IP.**
    
- El atacante:
    
    - Suplanta la IP de la víctima
        
    - Envía paquetes ICMP (ping) a una red con dirección de **broadcast**
        
    - Los dispositivos responden todos a la **IP de la víctima**, **saturándola**
        
- Consecuencia: caída del servidor o red.
    

---

## 🛡️ ¿Cómo protegerse contra la suplantación de IP?

### 1. **Cifrado de datos (encriptación):**

- Protege el contenido de los paquetes ante interceptación.
    
- Recomendado usar: **TLS/SSL, VPN**
    

---

### 2. **Configuración de firewalls:**

- Crear **reglas que bloqueen tráfico entrante** si:
    
    - La IP del remitente coincide con una IP **interna/local**.
        
    - Es probable que esa IP esté **falsificada**.
        

**Ejemplo:**

> Si un paquete desde Internet llega con una IP de origen `192.168.1.100` (local), el firewall lo **debe rechazar**, porque esa IP **no debería venir desde fuera**.

---

## ✅ **Resumen final:**

- La **suplantación de IP** es un engaño de identidad de red.
    
- Se usa en ataques como:
    
    - Ataque en ruta (MitM)
        
    - Ataque de repetición (Replay)
        
    - Ataque de pitufos (Smurf)
        
- Puedes **protegerte** con:
    
    - **Encriptación**
        
    - **Firewalls correctamente configurados**
        

---

### **Pregunta:**

**¿Cuál de los siguientes ataques utiliza la Suplantación de IP?**  
**Seleccione tres respuestas.**

---

### ✅ **Respuestas correctas:**

1. **Ataque en ruta**
    
    > El atacante se interpone entre dos dispositivos, suplantando IPs para interceptar o alterar la comunicación.
    
2. **Ataque de repetición**
    
    > El atacante intercepta y reutiliza paquetes con IP suplantada para hacerse pasar por un usuario legítimo.
    
3. **Ataque Smurf**
    
    > Se suplanta la IP de la víctima para enviar solicitudes a una red que responde en masa a esa IP, causando una inundación.
    

---

### ❌ Opción incorrecta:

- **Tailgating**
    
    > Es un ataque físico, no de red. Consiste en ingresar a un lugar restringido siguiendo de cerca a una persona autorizada.
    

---

---

## Navegación

- ⬆️ Carpeta: [[_3- Conectar y proteger, redes y seguridad de red|3- Conectar y proteger, redes y seguridad de red]]
- ⬅️ Anterior: [[1- Sniffing de paquetes malicioso]]
- ➡️ Siguiente: [[3- Visión general de las tácticas de interceptación]]
