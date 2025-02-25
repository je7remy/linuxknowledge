
---

#ManInTheMiddle #MitM #Bettercap #KaliLinux #ARPSpoofing #Sniffer #SSLStrip #Ciberseguridad #Hacking #Redes

---

Aquí tienes un paso a paso para desarrollar la técnica de ataque **Man-in-the-Middle (MitM)** con **Bettercap** en **Kali Linux**, capturando el tráfico de red y almacenando los resultados en un documento.

---
### **1. Instalación de Bettercap**
```bash
sudo apt install bettercap
```
- **Qué hace**: Instala el framework Bettercap (herramienta para análisis de redes y ataques MITM).
- **Nota**: En algunas distribuciones, Bettercap no está en los repositorios oficiales. Si falla, se recomienda instalarlo desde [su GitHub](https://github.com/bettercap/bettercap).

---

### **2. Ejecución de Bettercap**
```bash
sudo bettercap
```
- **Qué hace**: Inicia Bettercap en modo interactivo con privilegios de superusuario (necesarios para manipular tráfico de red).
- **Advertencia**: Operar con `sudo` otorga capacidades de bajo nivel de red. Errores pueden afectar la red.


---

### **3. Comandos Dentro de Bettercap (Modo Interactivo)**
Una vez dentro de Bettercap, se ejecutan estos comandos:

#### a) **`help`**
- **Qué hace**: Muestra la lista de comandos y módulos disponibles.

#### b) **`net.probe on`**
- **Qué hace**: Activa el descubrimiento pasivo de hosts en la red enviando sondas ARP y analizando tráfico.
- **Resultado**: Bettercap detectará dispositivos en la red (similar a `nmap`).

#### c) **`net.show`**
- **Qué hace**: Muestra una tabla con los hosts descubiertos (direcciones IP, MAC, nombres, etc.).

#### d) **`set arp.spoof.target 192.168.1.105`**
- **Qué hace**: Define la víctima del ataque ARP spoofing (en este caso, el dispositivo con IP `192.168.1.105`).

#### e) **`arp.spoof on`**
- **Qué hace**: Inicia el ARP spoofing contra el objetivo. Bettercap envía respuestas ARP falsas para envenenar la caché ARP de la víctima y el router, redirigiendo el tráfico a través del atacante.
- **Efecto**: El tráfico de la víctima pasa por tu máquina (MITM).

#### f) **`net.sniff on`**
- **Qué hace**: Activa el sniffer de paquetes para capturar tráfico de red (HTTP, DNS, etc.).
- **Datos capturados**: Credenciales HTTP, cookies, consultas DNS, etc. (si no hay cifrado como HTTPS).

---

### **Flujo Completo del Ataque**
1. **Instalación**: Se asegura que Bettercap esté disponible.
2. **Modo Interactivo**: Se inicia la herramienta.
3. **Descubrimiento de Red**: `net.probe on` y `net.show` identifican dispositivos.
4. **ARP Spoofing**: Redirige el tráfico de `192.168.1.105` a través de tu máquina.
5. **Sniffing**: Captura tráfico de la víctima para análisis.

---

### **Advertencias Éticas y Legales**
- **ARP Spoofing**: Es **ilegal** sin consentimiento explícito del propietario de la red y el dispositivo objetivo.
- **HTTPS**: La mayoría del tráfico moderno está cifrado. El sniffing solo capturará metadatos o tráfico no cifrado.
- **Alternativas Éticas**: Usar en redes propias o laboratorios controlados para aprendizaje.

---
### **Conclusión**
El flujo ejecuta un ataque MITM clásico usando ARP spoofing y sniffing, pero requiere permisos y contexto ético adecuado. Siempre verifica la legalidad de tus acciones.




[[2- Bash Scripting Aplicado a Ciberseguridad – Script para Hacer Fuzzing Web]]
[[3- Análisis De La Red Desde Linux – Comandos Básicos Parte 1]]
[[6- Análisis de Red con TCPdump y WireShark – PARTE 1]]

