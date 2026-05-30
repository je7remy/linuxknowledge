---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-1]
actualizado: 2026-05-28
---

# Dentro del sistema operativo

# Funcionamiento de un Sistema Operativo

Anteriormente, ha aprendido qué son los sistemas operativos. Ahora, vamos a hablar de cómo funcionan. En este vídeo, aprenderá lo que ocurre con un sistema operativo, o OS, cuando alguien utiliza una computadora para realizar una tarea.

Piense en cuando alguien conduce un coche. Pisa el acelerador y el coche avanza. No necesita prestar atención a todos los mecanismos que permiten que el coche se mueva. Al igual que un coche no puede funcionar sin su motor, un ordenador no puede funcionar sin su sistema operativo.

> El trabajo de un OS es ayudar a que otros programas de ordenador funcionen de forma eficiente.

El OS hace esto ocupándose de todos los detalles engorrosos relacionados con el control del hardware de la computadora, para que usted no tenga que hacerlo.

---

## 🔌 Proceso de Encendido

Primero, veamos lo que ocurre cuando enciende la computadora:

1. Presiona el botón de encendido → interactúa con el **hardware**.
    
2. Se activa un microchip especial llamado **BIOS** (o **UEFI** en modelos posteriores a 2007).
    
3. El BIOS/UEFI ejecuta instrucciones de arranque y carga un **cargador de arranque**.
    
4. El cargador de arranque inicia el **sistema operativo**.
    

> Así de sencillo, su computadora está encendida.

---

## 🔐 Seguridad en el Proceso de Arranque

Como analista de seguridad, comprender estos procesos puede serle útil:

- **La BIOS no suele ser explorada por software antivirus**, lo que la hace vulnerable.
    
- Es una posible puerta de entrada para **malware persistente**.
    
- Entender este flujo es crucial para **analizar eventos de seguridad**.
    

---

## 🧠 Comunicación entre Usuario, OS y Hardware

El proceso comienza con **usted, el usuario**, y sigue este flujo:

1. Usa una **aplicación** para realizar una tarea (ej. calculadora).
    
2. La aplicación envía una solicitud al **sistema operativo**.
    
3. El OS interpreta la solicitud y la dirige al **hardware** (como la CPU).
    
4. El hardware procesa la información y envía el resultado al OS.
    
5. El OS lo devuelve a la aplicación para que usted vea el resultado.
    

---

## 🧮 Ejemplo: Calculadora

- Usted hace clic en la aplicación de **calculadora**.
    
- Escribe un número → la app se comunica con el **sistema operativo**.
    
- El OS envía el cálculo a la **CPU**.
    
- La CPU procesa el cálculo y envía la respuesta al OS.
    
- El OS la muestra en la app de calculadora.
    

---

## 🎯 Importancia para el Analista de Seguridad

> Comprender este proceso es útil a la hora de **investigar eventos de seguridad**.

- Un analista debe poder **rastrear el flujo** entre usuario, OS y hardware.
    
- Así como un mecánico entiende el motor de un auto, un analista debe entender el sistema operativo.
    
- Este conocimiento permite:
    
    - Detectar **fallos o anomalías**
        
    - Analizar **puntos de vulnerabilidad**
        
    - Implementar **medidas preventivas**
        

---

¿Cómo se comunican las aplicaciones y el hardware?

La respuesta **correcta** es:

> **Las aplicaciones envían solicitudes al sistema operativo y éste las dirige al hardware.**

🔁 Y el ciclo continúa así:

- El **hardware** procesa la solicitud y envía una respuesta al **sistema operativo**.
    
- Luego, el **sistema operativo** se la devuelve a la **aplicación**, que la presenta al usuario.
    

Esto permite que el usuario no tenga que interactuar directamente con el hardware —el sistema operativo hace de intermediario eficiente y seguro.

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ➡️ Siguiente: [[2- Solicitudes al sistema operativo]]
