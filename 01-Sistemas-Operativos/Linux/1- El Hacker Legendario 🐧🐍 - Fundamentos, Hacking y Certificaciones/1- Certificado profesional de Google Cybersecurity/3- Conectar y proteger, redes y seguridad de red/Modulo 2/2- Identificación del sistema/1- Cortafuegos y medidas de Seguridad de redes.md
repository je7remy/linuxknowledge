---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Cortafuegos y medidas de Seguridad de redes
## 🔥 Cortafuegos: Tipos, Funcionamiento y Seguridad

### 🔐 ¿Qué es un cortafuegos (firewall)?

Un **firewall** es un **dispositivo de seguridad de red** que monitorea el tráfico de entrada y salida, permitiéndolo o bloqueándolo según un conjunto de **reglas de seguridad** definidas.

- **Filtrado por puertos**: Permite o bloquea puertos específicos, como:
    
    - `443` para HTTPS
        
    - `25` para correo electrónico
        

---

### 🧱 Tipos de cortafuegos

1. **Cortafuegos de hardware**
    
    - Dispositivo físico independiente
        
    - Inspecciona paquetes antes de entrar a la red
        
    - Básico pero efectivo
        
2. **Cortafuegos de software**
    
    - Instalado en un equipo o servidor
        
    - Protege solo al dispositivo donde se instala
        
    - Menor coste, pero usa recursos del sistema
        
3. **Cortafuegos en la nube (FaaS: Firewall as a Service)**
    
    - Ofrecido por proveedores de servicios en la nube
        
    - Configurable desde la nube y protege tráfico entrante a la red local
        
    - También protege los recursos cloud de la organización
        

---

### ⚙️ Tipos de funcionamiento

- **Con estado (Stateful)**
    
    - Monitorea y analiza continuamente los paquetes
        
    - Detecta patrones y comportamientos sospechosos
        
    - **Más seguro**
        
- **Sin estado (Stateless)**
    
    - Se basa solo en reglas predefinidas
        
    - No guarda contexto de paquetes anteriores
        
    - **Menos seguro**
        

---

### 🛡️ Cortafuegos de nueva generación (NGFW)

- Incluyen funcionalidades avanzadas:
    
    - **Inspección profunda de paquetes**
        
    - **Protección contra intrusiones**
        
    - **Conexión a inteligencia en la nube**
        
- Se actualizan automáticamente contra amenazas nuevas
    

---

### ✅ Conclusión

- Existen **tres tipos de firewalls** principales: hardware, software y en la nube.
    
- Su funcionamiento puede ser **con estado o sin estado**.
    
- Los **NGFW** ofrecen el nivel más alto de protección.
    

---

¿Qué clase de firewall funciona basándose en reglas predefinidas y no hace un seguimiento de la información de los paquetes de datos?

La respuesta correcta es:

✅ **Sin estado**

Los **firewalls sin estado**:

- Funcionan **únicamente con reglas predefinidas**.
    
- **No realizan seguimiento** del tráfico previo.
    
- No detectan comportamientos sospechosos.
    
- Son **menos seguros** que los cortafuegos con estado.

---

## Navegación

- ⬆️ Carpeta: [[_3- Conectar y proteger, redes y seguridad de red|3- Conectar y proteger, redes y seguridad de red]]
- ➡️ Siguiente: [[2- Redes privadas virtuales (VPN)]]
