
## 🧠 **Ejercicio Interactivo - Endurecimiento del Sistema Operativo, la Red y la Nube**

### 👋 **Coach**

Hola. Soy tu entrenador de Coursera para este ejercicio interactivo. Juntos exploraremos técnicas de protección para sistemas operativos, redes y la nube, y cómo estas abordan vulnerabilidades específicas.

---

### 🧩 **Temas que cubriremos:**

- 🔒 Contrarrestar vulnerabilidades del sistema operativo (25%)
    
- 🌐 Contrarrestar vulnerabilidades de la red y la nube (25%)
    
- 🔍 Técnicas de endurecimiento en investigación y prevención (25%)
    
- 🛡️ Técnicas para abordar vulnerabilidades específicas (25%)
    

---

### ✅ **Comenzamos**

**Coach:**  
_Considera los defectos de software explotables. ¿Qué técnica del sistema operativo ayuda a proteger contra esto?_

**Jeremy:**  
Una técnica clave es **DEP (Data Execution Prevention)**.  
Evita que se ejecute código malicioso en zonas de memoria destinadas solo a datos. Es eficaz contra desbordamientos de búfer.

---

**Coach:**  
_Ahora, piensa en los permisos de usuario excesivos. ¿Qué técnica mitiga esto?_

**Jeremy:**  
El **principio de mínimo privilegio**.  
Cada usuario solo tiene los permisos que necesita, lo que limita el daño si una cuenta es comprometida.

---

**Coach:**  
_¿Qué técnica protege contra credenciales débiles o robadas?_

**Jeremy:**  
La **autenticación multifactor (MFA)**.  
Requiere más de una forma de verificación. Si alguien roba una contraseña, no podrá acceder sin el segundo factor.

---

**Coach:**  
_¿Cómo se abordan los programas o servicios innecesarios?_

**Jeremy:**  
**Deshabilitándolos o eliminándolos**.  
Reduce la superficie de ataque al minimizar puntos que un atacante podría explotar.

---

**Coach:**  
_¿Qué hacer ante pérdida de dispositivos?_

**Jeremy:**  
Usar **cifrado de disco**.  
Aunque roben el dispositivo, sin la clave no podrán acceder a los datos.

---

## 🌐 **Endurecimiento de Red y Nube**

**Coach:**  
_Explica el filtrado de puertos._

**Jeremy:**  
Es como decirle al sistema: “usa solo los puertos necesarios y cierra los demás”.  
Así se bloquean puertas que los atacantes podrían usar para colarse.

---

**Coach:**  
_¿Qué es la segmentación de red?_

**Jeremy:**  
Es como dividir una casa en habitaciones con llave.  
Si un atacante entra a una parte, no puede moverse por toda la red.

---

**Coach:**  
_¿Qué son los IDPS y cómo previenen escuchas ilegales?_

**Jeremy:**  
Son sistemas que monitorean el tráfico en busca de comportamientos sospechosos.  
Pueden alertar (detección) o bloquear (prevención) tráfico malicioso en tiempo real.

---

**Coach:**  
_¿Qué son los protocolos seguros y cómo evitan ataques man-in-the-middle?_

**Jeremy:**  
Son versiones cifradas de protocolos como **HTTPS** o **SSH**.  
Protegen la información durante la transmisión, evitando que un atacante la intercepte o modifique.

---

**Coach:**  
_¿Qué son los grupos de seguridad en la nube?_

**Jeremy:**  
Son reglas que controlan quién puede acceder a un recurso en la nube y desde dónde.  
Actúan como un portero que solo deja pasar lo autorizado.

---

**Coach:**  
_¿Qué son las auditorías y los pentests?_

**Jeremy:**  
Son revisiones de seguridad.  
Las **auditorías** revisan configuraciones y registros, y los **pentests** simulan ataques reales para encontrar vulnerabilidades antes que lo hagan los atacantes.

---

## 🎯 **Escenario Final - Tráfico Inusual en la Red**

**Coach:**  
_Una IP desconocida intenta acceder a un servidor. ¿Qué harías para investigar y prevenirlo?_

**Jeremy:**

- Usaría los **registros del sistema y firewall** para ver qué está pasando.
    
- Reforzaría el **firewall** y bloquearía la IP sospechosa.
    
- Revisaría las **configuraciones del servidor** para asegurarme de que no haya vulnerabilidades.
    
- Activaría un **IDS/IPS** para bloquear tráfico similar en el futuro.
    
- Revisaría los **permisos de usuario** para evitar accesos indebidos.
    
- Añadiría un **escaneo de vulnerabilidades** como medida extra.
    

---

### 🏁 **Conclusión del Coach**

> Has cubierto exhaustivamente las técnicas de protección y su aplicación en un escenario real.  
> Has demostrado una sólida comprensión de cómo las técnicas del sistema operativo y la red pueden utilizarse para **investigar y prevenir actividades sospechosas**.  
> ¡Sigue con el buen trabajo!

---

