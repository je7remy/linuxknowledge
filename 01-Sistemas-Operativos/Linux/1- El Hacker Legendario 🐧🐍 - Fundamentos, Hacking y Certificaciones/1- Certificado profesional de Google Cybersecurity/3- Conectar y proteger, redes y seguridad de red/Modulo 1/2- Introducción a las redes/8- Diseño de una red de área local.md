
# 📡 Diseño de una Red de Área Local (LAN)

## 🧱 Estructura de la Red:

### 1. **Internet**

- Es la fuente externa de conectividad.
    

### 2. **Firewall (Cortafuegos)**

- Colocado justo después de la entrada desde Internet.
    
- Su función es **filtrar el tráfico entrante y saliente**, protegiendo la red interna.
    

### 3. **Router (Enrutador)**

- Conecta la red interna con el Internet.
    
- También conecta al servidor directamente.
    
- **Lee las direcciones IP de destino** y **redirige el tráfico** correctamente.
    

### 4. **Servidor**

- Conectado directamente al router.
    
- Proporciona servicios o almacenamiento dentro de la red.
    

### 5. **Segundo Firewall**

- Agrega una **capa adicional de protección** entre el router y la red interna de dispositivos.
    

### 6. **Switch (Conmutador)**

- Dispositivo inteligente que **distribuye el tráfico solo al dispositivo de destino correcto**.
    
- Mejora el rendimiento de la red.
    

### 7. **Punto de Acceso Inalámbrico (Wireless Access Point)**

- Conectado al switch.
    
- Permite la **conexión WiFi de dispositivos inalámbricos** a la red.
    

### 8. **Dispositivos finales**

- Laptops, computadoras, etc., conectadas al switch o vía WiFi al punto de acceso.
    

---

## 🧠 Nota clave:

- Este diseño **separa claramente la red externa (Internet)** de la **red interna protegida**, utilizando dos firewalls.
    
- Integra tanto **dispositivos cableados** (mediante switch) como **inalámbricos** (a través del punto de acceso).
    
- El servidor queda protegido dentro de la red, pero con acceso directo al router.
    

---

![[ChatGPT Image 17 jun 2025, 11_29_39 a.m..png]]