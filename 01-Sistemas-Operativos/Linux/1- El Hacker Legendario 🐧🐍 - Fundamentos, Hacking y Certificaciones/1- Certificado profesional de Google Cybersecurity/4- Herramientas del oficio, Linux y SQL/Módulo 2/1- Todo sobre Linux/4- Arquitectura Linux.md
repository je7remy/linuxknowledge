---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Arquitectura Linux

## 🏛️ **Arquitectura de Linux: Componentes clave**

Así como un edificio está compuesto por ventanas, paredes y estructuras internas, **Linux también tiene una arquitectura**, formada por partes que trabajan en conjunto para permitir que el sistema funcione.

---

### 🔹 **1. Usuario**

- Eres **la persona que interactúa con el sistema**.
    
- Inicias tareas y comandos que serán ejecutados por Linux.
    
- Linux es un sistema **multiusuario**, lo que significa que **varios usuarios pueden usar los recursos simultáneamente**.
    

---

### 🔹 **2. Aplicaciones**

- Son programas que ejecutan tareas específicas, como:
    
    - 📝 Procesadores de texto
        
    - 🧮 Calculadoras
        
    - 📂 Editores de texto (ej. **Nano**)
        
- Las aplicaciones en Linux suelen instalarse mediante **gestores de paquetes** (como `apt`, `yum`, `dnf`...).
    

---

### 🔹 **3. Shell**

- El **shell** es un **intérprete de línea de comandos (CLI)**.
    
- Su función es:
    
    - Recibir comandos del usuario
        
    - Procesarlos
        
    - Mostrar los resultados
        
- Es la **principal forma de comunicación entre el usuario y el sistema operativo** en entornos técnicos.
    

---

### 🔹 **4. Estándar de Jerarquía del Sistema de Archivos (FHS)**

- Es la **estructura de carpetas y archivos** que organiza todo el contenido del sistema Linux.
    
- Puedes imaginarlo como un **archivador bien organizado**, con cada tipo de archivo en su sitio correspondiente.
    
- Algunos ejemplos comunes del FHS:
    
    - `/home` → carpetas personales
        
    - `/etc` → archivos de configuración
        
    - `/bin` → comandos esenciales del sistema
        

---

### 🔹 **5. Kernel**

- Es el **núcleo del sistema operativo**.
    
- Funciones clave:
    
    - Gestiona **procesos**, **memoria** y **recursos del sistema**
        
    - Se comunica directamente con el **hardware**
        
    - Usa **drivers** (controladores) para ejecutar las instrucciones del shell y las aplicaciones
        
- El kernel es esencial para que el sistema funcione de forma eficiente.
    

---

### 🔹 **6. Hardware**

- Son los **componentes físicos del sistema**, como:
    
    - 💻 CPU
        
    - 🖱 Mouse
        
    - ⌨ Teclado
        
    - 🧠 Memoria RAM
        
- El kernel actúa como **puente entre el software y el hardware**, permitiendo que el sistema realice tareas físicas.
    

---

## 🎓 Conclusión

> Comprender los componentes de la arquitectura de Linux —desde el usuario hasta el hardware— te dará una base sólida para usar el sistema con confianza, especialmente en contextos de seguridad informática.

---

### 🧩 Resumen visual:

|Componente|Función principal|
|---|---|
|Usuario|Inicia comandos y tareas|
|Aplicaciones|Realizan tareas específicas|
|Shell|Interfaz de línea de comandos para comunicarse con el OS|
|FHS|Organiza el sistema de archivos|
|Kernel|Controla los recursos y comunica con el hardware|
|Hardware|Componentes físicos que ejecutan las órdenes|

---

### ❓ Pregunta:

**¿Cuál es la función del kernel en el sistema operativo Linux?**

A) Organiza los datos.  
B) Gestiona los procesos y la memoria.  
C) Ayuda a los usuarios a realizar cálculos.  
D) Procesa los comandos y emite los resultados.

---

### ✅ Respuesta correcta:

**B) Gestiona los procesos y la memoria.**

---

La función principal del **kernel** en un sistema operativo como Linux es:

> **Gestionar los procesos y la memoria.**

---

### 📌 Explicación rápida:

El **kernel** es el **núcleo** del sistema operativo. Actúa como un puente entre el **hardware** y el **software**. Sus funciones principales incluyen:

- 👨‍💻 **Gestión de procesos**: controla qué procesos se ejecutan, en qué orden y con qué recursos.
    
- 🧠 **Gestión de memoria**: asigna y libera memoria a los programas.
    
- 📡 **Gestión de dispositivos**: coordina la comunicación entre el software y el hardware.
    
- 🔐 **Gestión de seguridad y permisos**: controla el acceso a recursos críticos del sistema.
    

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[3- Phil, Aprender y crecer en el campo de la ciberseguridad]]
- ➡️ Siguiente: [[5- Explicación de la arquitectura de Linux]]
