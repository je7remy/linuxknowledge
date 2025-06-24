
---

## 🔐 Zonas de Seguridad en Redes

Las **zonas de seguridad** son segmentos de una red diseñados para proteger los sistemas internos del acceso externo no autorizado. Forman parte de una práctica llamada **segmentación de red**, que divide la red en partes controladas con reglas y permisos específicos.

### 🧱 ¿Qué hacen las Zonas de Seguridad?

- Controlan quién puede acceder a cada segmento.
    
- Aíslan problemas para evitar que se propaguen por toda la red.
    
- Aumentan la privacidad y la protección interna.
    

---

### 🧭 Clasificación de Zonas

#### 🌐 Zona No Controlada

- Red **fuera del control de la organización**.
    
- Ejemplo: **Internet**.
    

#### 🛡️ Zona Controlada

- **Subred protegida** que separa la red interna de la zona no controlada.
    
- Incluye:
    
    ✅ **Zona DMZ (Desmilitarizada)**
    
    - Aloja servicios accesibles públicamente (servidores web, DNS, proxy, correo, etc.).
        
    - Ubicada entre dos **firewalls** para proteger tanto del exterior como del acceso a la red interna.
        
    
    ✅ **Red Interna**
    
    - Contiene servidores y datos **privados**.
        
    - Aislada de la DMZ y accesible solo desde redes internas autorizadas.
        
    
    ✅ **Zona Restringida**
    
    - Aún más protegida dentro de la red interna.
        
    - Accesible solo por personal con **altos privilegios**.
        
    - Utiliza un tercer **firewall** para mayor aislamiento.
        

---

### 🏨 Ejemplo de Segmentación de Red

> Un hotel ofrece Wi-Fi público separado de la red privada del personal.  
> Otro ejemplo: una universidad con subredes independientes para estudiantes y profesores.

---

### 🔧 Funciones del Analista de Seguridad

- Administrar **firewalls** entre zonas.
    
- Aplicar reglas de acceso por **puerto** e **IP** (ej.: permitir solo tráfico **HTTPS** a la DMZ).
    
- Supervisar el tráfico y limitar los riesgos de propagación de amenazas.
    

---

### 🛡️ Áreas dentro de la Zona Controlada

**Pregunta:**

> ¿Cuál de las siguientes áreas se encuentra en la zona controlada?  
> Seleccione todas las que correspondan.

---

### ✅ Respuestas Correctas:

- **🔐 Red interna**  
    Contiene servidores y datos **privados** que deben estar protegidos dentro de la organización.
    
- **🌐 Zona desmilitarizada (DMZ)**  
    Incluye servicios **accesibles públicamente**, como servidores web o correo, **expuestos a Internet** pero **aislados** del resto de la red interna.
    
- **🚫 Zona restringida**  
    Contiene **información altamente confidencial** a la que solo pueden acceder usuarios con **privilegios específicos**.
    

---

### ❌ Respuesta Incorrecta:

- **Zona no controlada**  
    No pertenece a la zona controlada. Generalmente es el espacio fuera del firewall, como **Internet o redes externas** sin protección directa.
    

---

