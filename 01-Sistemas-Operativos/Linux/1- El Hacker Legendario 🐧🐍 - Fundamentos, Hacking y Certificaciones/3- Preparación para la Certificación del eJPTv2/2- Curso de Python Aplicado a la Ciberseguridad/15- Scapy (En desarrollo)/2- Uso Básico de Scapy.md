
---

Biblioteca Scapy en Python para manipular y capturar paquetes de red.

---

### **1. Primer Script: Envío Básico de Paquete ICMP**
```python
from scapy.all import IP, ICMP, send, sr1
paquete = IP(dst="8.8.8.8")
paquete = IP(dst="8.8.8.8")/ICMP()
send(paquete)
respuesta = sr1(paquete)
print(respuesta)
```

#### **Explicación y Análisis Paso a Paso**

1. **Importación de Módulos de Scapy**:
   ```python
   from scapy.all import IP, ICMP, send, sr1
   ```
   - **Propósito**: Importa las clases y funciones necesarias de Scapy.
   - **Detalles**:
     - `IP`: Representa la capa IP de un paquete, permitiendo configurar encabezados IP (como IP de origen y destino).
     - `ICMP`: Representa la capa ICMP (Protocolo de Mensajes de Control de Internet), usado comúnmente para ping (solicitud/respuesta de eco).
     - `send`: Envía paquetes en la capa 3 (capa de red) sin esperar respuesta.
     - `sr1`: Envía un paquete y devuelve la primera respuesta recibida (ideal para protocolos de solicitud-respuesta como ICMP).

2. **Creación de un Paquete IP**:
   ```python
   paquete = IP(dst="8.8.8.8")
   ```
   - **Propósito**: Define un paquete IP con dirección de destino `8.8.8.8` (servidor DNS público de Google).
   - **Detalles**:
     - La clase `IP` crea un paquete con valores predeterminados para campos como la IP de origen (la IP local de la máquina), TTL (tiempo de vida), etc.
     - Aquí solo se establece explícitamente la IP de destino.

3. **Añadir una Capa ICMP**:
   ```python
   paquete = IP(dst="8.8.8.8")/ICMP()
   ```
   - **Propósito**: Sobrescribe la variable `paquete` para incluir una capa ICMP, creando un paquete completo de solicitud de eco ICMP (ping).
   - **Detalles**:
     - El operador `/` en Scapy apila capas de protocolo (IP sobre ICMP).
     - `ICMP()` crea por defecto una solicitud de eco ICMP (tipo 8, código 0).
     - Esta línea podría combinarse con la anterior, pero el script redefine `paquete` de manera redundante.

4. **Envío del Paquete**:
   ```python
   send(paquete)
   ```
   - **Propósito**: Envía el paquete a `8.8.8.8` en la capa de red.
   - **Detalles**:
     - `send` opera en la capa 3 (capa IP) y no espera una respuesta.
     - Esta línea envía una solicitud de eco ICMP (ping) a `8.8.8.8`.

5. **Envío y Recepción de una Respuesta**:
   ```python
   respuesta = sr1(paquete)
   ```
   - **Propósito**: Envía el mismo paquete nuevamente y captura la primera respuesta.
   - **Detalles**:
     - `sr1` (send/receive one) envía el paquete y espera una única respuesta, típicamente una respuesta de eco ICMP (tipo 0, código 0) si el destino es alcanzable.
     - Si no se recibe respuesta dentro del tiempo de espera (por defecto ~2 segundos), `respuesta` será `None`.

6. **Impresión de la Respuesta**:
   ```python
   print(respuesta)
   ```
   - **Propósito**: Muestra el paquete de respuesta (si se recibió).
   - **Detalles**:
     - Si `respuesta` no es `None`, imprime un resumen del paquete (por ejemplo, IP de origen, tipo ICMP).
     - Si no se recibe respuesta, imprime `None`.

#### **Problemas y Observaciones**
- **Redundancia**: El script envía el paquete dos veces: una con `send` (sin capturar respuesta) y otra con `sr1`. La llamada a `send` es innecesaria si el objetivo es capturar una respuesta.
- **Sin Manejo de Errores**: Si no se recibe respuesta, `respuesta` es `None`, y `print(respuesta)` solo muestra `None` sin contexto.
- **Caso de Uso**: Este script realiza un ping básico para probar si `8.8.8.8` es alcanzable, similar al comando `ping` en una terminal.

---

### **2. Segundo Script: Mostrar la Respuesta**
```python
from scapy.all import IP, ICMP, send, sr1
paquete = IP(dst="8.8.8.8")
paquete = IP(dst="8.8.8.8")/ICMP()
send(paquete)
respuesta = sr1(paquete)
respuesta.show()
```

#### **Evolución desde el Primer Script**
- El único cambio es reemplazar `print(respuesta)` por `respuesta.show()`.
- **Propósito del Cambio**: En lugar de imprimir un resumen básico de la respuesta, `show()` proporciona un desglose detallado de los campos del paquete.

#### **Análisis Detallado del Cambio**
1. **Mostrar la Respuesta**:
   ```python
   respuesta.show()
   ```
   - **Propósito**: Muestra una vista detallada del paquete de respuesta, incluyendo todos los campos de las capas IP e ICMP.
   - **Detalles**:
     - `show()` es un método de Scapy que imprime una representación legible del paquete, incluyendo:
       - **Capa IP**: IP de origen/destino, TTL, protocolo, etc.
       - **Capa ICMP**: Tipo (por ejemplo, 0 para respuesta de eco), código, número de secuencia, etc.
     - Ejemplo de salida para una respuesta de ping exitosa:
       ```
       ###[ IP ]###
         version   = 4
         src       = 8.8.8.8
         dst       = <tu_IP_local>
       ###[ ICMP ]###
         type      = echo-reply
         code      = 0
         id        = <algún_id>
         seq       = <alguna_secuencia>
       ```
   - **Mejora**: Esto es más informativo que `print(respuesta)`, que solo muestra un resumen como `<IP src=8.8.8.8 | ICMP>`.

#### **Problemas y Observaciones**
- **Llamada `send` Redundante**: El script aún envía el paquete dos veces innecesariamente.
- **Sin Manejo de Errores**: Si `respuesta` es `None`, llamar a `respuesta.show()` generará un error de tipo AttributeError (`NoneType no tiene el atributo show`).
- **Caso de Uso**: Útil para aprendizaje o depuración, ya que muestra la estructura completa del paquete de respuesta.

---

### **3. Tercer Script: Añadir Manejo de Errores**
```python
from scapy.all import IP, ICMP, send, sr1
paquete = IP(dst="8.8.8.85")
paquete = IP(dst="8.8.8.85")/ICMP()
send(paquete)
respuesta = sr1(paquete)
if respuesta:
    respuesta.show()
else:
    print("No se ha recibido respuesta")
```

#### **Evolución desde el Segundo Script**
- **Cambio en la IP de Destino**: La IP de destino ahora es `8.8.8.85` (no un servidor público conocido, probablemente inalcanzable).
- **Manejo de Errores**: Añade una verificación condicional para manejar casos en los que no se recibe respuesta.
- **Propósito de los Cambios**:
  - Prueba la conectividad a una IP potencialmente inalcanzable.
  - Evita errores cuando `respuesta` es `None` al verificar si existe una respuesta antes de llamar a `show()`.

#### **Análisis Detallado**
1. **Nueva IP de Destino**:
   ```python
   paquete = IP(dst="8.8.8.85")
   paquete = IP(dst="8.8.8.85")/ICMP()
   ```
   - **Propósito**: Apunta a `8.8.8.85` en lugar de `8.8.8.8`.
   - **Detalles**:
     - `8.8.8.85` no es un servidor público conocido (a diferencia de `8.8.8.8`). Probablemente se eligió para demostrar un caso donde no se recibe respuesta.
     - Esto prueba el comportamiento del script con un host inalcanzable.

2. **Manejo de Errores**:
   ```python
   if respuesta:
       respuesta.show()
   else:
       print("No se ha recibido respuesta")
   ```
   - **Propósito**: Verifica si `respuesta` no es `None` antes de llamar a `show()`.
   - **Detalles**:
     - Si se recibe una respuesta, `respuesta.show()` muestra los detalles del paquete.
     - Si no se recibe respuesta (por ejemplo, debido a un host inalcanzable o tiempo de espera), imprime un mensaje claro: `"No se ha recibido respuesta"`.
     - Esto evita el error AttributeError del segundo script.

#### **Problemas y Observaciones**
- **Llamada `send` Redundante**: El script aún envía el paquete dos veces, lo cual es ineficiente.
- **Prueba con Host Inalcanzable**: Usar `8.8.8.85` probablemente resulte en no recibir respuesta, activando la rama `else`. Esto es útil para demostrar el manejo de errores.
- **Caso de Uso**: Este script es más robusto para uso en el mundo real, ya que maneja fallos de manera elegante e informa al usuario cuando no se recibe respuesta.

---

### **4. Cuarto Script: Captura de Paquetes (TCP)**
```python
from scapy.all import sniff
paquetes_tcp = sniff(filter="tcp", count=10)
paquetes_tcp.show()
```

#### **Evolución y Contexto**
- **Cambio en la Funcionalidad**: Este script pasa de enviar paquetes (redes activas) a capturar paquetes (monitoreo pasivo).
- **Propósito**: Captura y muestra paquetes TCP en la interfaz de red.

#### **Análisis Detallado**
1. **Importación de `sniff`**:
   ```python
   from scapy.all import sniff
   ```
   - **Propósito**: Importa la función `sniff` para capturar paquetes de red.
   - **Detalles**: `sniff` es una función poderosa de Scapy que escucha en una interfaz de red y captura paquetes que coinciden con un filtro especificado.

2. **Captura de Paquetes TCP**:
   ```python
   paquetes_tcp = sniff(filter="tcp", count=10)
   ```
   - **Propósito**: Captura 10 paquetes TCP de la red.
   - **Detalles**:
     - **filter="tcp"**: Usa una sintaxis BPF (Berkeley Packet Filter) para capturar solo paquetes TCP (protocolo 6 en IP).
     - **count=10**: Limita la captura a 10 paquetes. Sin esto, `sniff` correría indefinidamente hasta que se detuviera.
     - **Interfaz**: Por defecto, `sniff` usa la interfaz de red predeterminada (por ejemplo, `eth0` o `wlan0` en Linux). Se puede especificar una interfaz con `iface=<nombre_interfaz>`.
     - **Salida**: Almacena los paquetes capturados en `paquetes_tcp`, un objeto tipo lista (`PacketList` en Scapy).

3. **Mostrar Paquetes Capturados**:
   ```python
   paquetes_tcp.show()
   ```
   - **Propósito**: Muestra los detalles de todos los paquetes capturados.
   - **Detalles**:
     - `show()` itera sobre la `PacketList` e imprime los campos de cada paquete (por ejemplo, IP, TCP, carga útil).
     - Ejemplo de salida para un paquete TCP:
       ```
       ###[ IP ]###
         src       = 192.168.1.100
         dst       = 93.184.216.34
       ###[ TCP ]###
         sport     = 12345
         dport     = 80
         seq       = <número_secuencia>
         flags     = S (SYN)
       ```
     - Esto es útil para inspeccionar el contenido de los paquetes, como IPs de origen/destino, puertos y banderas TCP.

#### **Notas Importantes**
- **Permisos**: La captura de paquetes normalmente requiere privilegios de administrador (por ejemplo, ejecutar con `sudo` en Linux) porque accede a interfaces de red en modo crudo.
- **Dependencia de la Red**: Los paquetes capturados dependen del tráfico en la interfaz. En una red tranquila, puede tomar tiempo capturar 10 paquetes TCP, o no capturar ninguno.
- **Caso de Uso**: Útil para monitoreo de red, depuración o aprendizaje sobre tráfico TCP (por ejemplo, análisis de HTTP, SSH u otros protocolos basados en TCP).

---

### **5. Quinto Script: Captura Específica de TCP (Puertos FTP)**
```python
from scapy.all import sniff
paquetes_tcp = sniff(filter="tcp port 21 or tcp port 20", count=10)
paquetes_tcp.show()
```

#### **Evolución desde el Cuarto Script**
- **Filtro Refinado**: El filtro es más específico, apuntando a paquetes TCP en los puertos 21 (control FTP) o 20 (datos FTP).
- **Propósito del Cambio**: Se centra en capturar tráfico relacionado con FTP en lugar de todo el tráfico TCP.

#### **Análisis Detallado**
1. **Filtro Refinado**:
   ```python
   paquetes_tcp = sniff(filter="tcp port 21 or tcp port 20", count=10)
   ```
   - **Propósito**: Captura 10 paquetes TCP donde el puerto de origen o destino es 21 (control FTP) o 20 (datos FTP).
   - **Detalles**:
     - **Filtro BPF**: `"tcp port 21 or tcp port 20"` es una expresión BPF:
       - `tcp`: Coincide con paquetes TCP.
       - `port 21`: Coincide con paquetes donde el puerto de origen o destino es 21.
       - `port 20`: Coincide con paquetes donde el puerto de origen o destino es 20.
       - `or`: Combina las condiciones.
     - **Contexto FTP**:
       - El puerto 21 se usa para comandos/control FTP (por ejemplo, autenticación, listado de directorios).
       - El puerto 20 se usa para transferencia de datos FTP en modo activo.
     - **Count**: Limita la captura a 10 paquetes.
     - **Probabilidad de Captura**: FTP es menos común hoy (reemplazado por SFTP o HTTPS para transferencias de archivos), por lo que capturar paquetes en estos puertos puede requerir tráfico FTP activo (por ejemplo, ejecutando un cliente/servidor FTP localmente).

2. **Mostrar Paquetes**:
   ```python
   paquetes_tcp.show()
   ```
   - **Propósito**: Igual que en el cuarto script—muestra los detalles de los paquetes capturados.
   - **Detalles**: Solo se muestran los paquetes que coinciden con el filtro FTP, haciendo la salida más relevante para el análisis de FTP.

#### **Problemas y Observaciones**
- **Caso de Uso Específico**: Capturar tráfico FTP es específico y puede no producir resultados a menos que se use FTP activamente en la red.
- **Permisos**: Todavía requiere privilegios de administrador.
- **Caso de Uso**: Ideal para monitorear o depurar servidores/clientes FTP, o para fines educativos para estudiar el comportamiento del protocolo FTP.

---

### **Evolución General y Lecciones Aprendidas**
1. **De Redes Activas a Pasivas**:
   - Los primeros tres scripts se centran en **redes activas** (crear y enviar paquetes ICMP para probar conectividad).
   - Los últimos dos scripts cambian a **redes pasivas** (capturar tráfico existente para observar el comportamiento de la red).
   - Esta progresión refleja un camino de aprendizaje: comenzar con el envío simple de paquetes, luego mejorar la robustez y finalmente explorar la captura de paquetes.

2. **Mejoras en el Código**:
   - **Manejo de Errores**: El tercer script introduce una verificación para `respuesta`, haciéndolo más robusto.
   - **Salida Detallada**: Reemplazar `print` con `show()` proporciona información más rica sobre los paquetes.
   - **Análisis Específico**: Los scripts de captura evolucionan de capturar todo el tráfico TCP a puertos FTP específicos, mostrando cómo enfocarse en datos relevantes.

3. **Consideraciones Prácticas**:
   - **Permisos**: Enviar paquetes crudos (`send`, `sr1`) y capturar (`sniff`) a menudo requieren privilegios de administrador (`sudo`).
   - **Contexto de Red**: La efectividad de estos scripts depende del entorno de red (por ejemplo, hosts alcanzables para pings, tráfico activo para captura).
   - **Redundancia**: Las llamadas redundantes a `send` en los primeros tres scripts destacan la necesidad de un diseño de código más limpio.

4. **Casos de Uso**:
   - **Scripts ICMP**: Útiles para diagnósticos de red (por ejemplo, probar si un host está activo, similar a `ping`).
   - **Scripts de Captura**: Útiles para monitoreo de red, análisis de seguridad (por ejemplo, detectar tráfico FTP inesperado) o estudio de protocolos.
   - **Valor Educativo**: Estos scripts enseñan conceptos fundamentales de redes (IP, ICMP, TCP, puertos) y cómo manipular paquetes programáticamente.

---

### **Mejoras Sugeridas**
1. **Eliminar la Llamada `send` Redundante**:
   - En los primeros tres scripts, eliminar `send(paquete)` ya que `sr1` ya envía el paquete y captura la respuesta.
   - Versión modificada (para el tercer script):
     ```python
     from scapy.all import IP, ICMP, sr1
     paquete = IP(dst="8.8.8.85")/ICMP()
     respuesta = sr1(paquete)
     if respuesta:
         respuesta.show()
     else:
         print("No se ha recibido respuesta")
     ```

2. **Añadir Configuración de Tiempo de Espera**:
   - `sr1` tiene un tiempo de espera predeterminado (~2 segundos). Añadir un tiempo de espera explícito para mayor claridad:
     ```python
     respuesta = sr1(paquete, timeout=3)
     ```

3. **Mejorar la Captura**:
   - Añadir una especificación de interfaz para portabilidad:
     ```python
     paquetes_tcp = sniff(filter="tcp port 21 or tcp port 20", count=10, iface="eth0")
     ```
   - Guardar los paquetes capturados en un archivo para análisis posterior:
     ```python
     paquetes_tcp = sniff(filter="tcp port 21 or tcp port 20", count=10)
     paquetes_tcp.to_pcap("captura_ftp.pcap")
     ```

4. **Manejo de Errores para Captura**:
   - Manejar casos donde no se capturan paquetes:
     ```python
     paquetes_tcp = sniff(filter="tcp port 21 or tcp port 20", count=10)
     if paquetes_tcp:
         paquetes_tcp.show()
     else:
         print("No se capturaron paquetes")
     ```

---

### **Conclusión**
La secuencia de scripts demuestra una progresión desde la creación básica de paquetes (pings ICMP) hasta el manejo robusto de errores y finalmente la captura de paquetes (TCP y específico de FTP). Cada script se basa en conceptos de redes, introduciendo las capacidades de Scapy para manipular y analizar paquetes. La evolución refleja mejoras prácticas (manejo de errores, filtrado específico) y un cambio de interacción activa a pasiva con la red. Estos scripts son excelentes para aprender programación de redes, depuración o monitoreo, pero requieren privilegios de administrador y un entorno de red activo para funcionar eficazmente.

### **Todo junto**

````python
from scapy.all import IP, ICMP, sr1, sniff

def ping_host(ip):
    """Envía un ping ICMP a la IP especificada y muestra la respuesta."""
    print(f"Enviando ping a {ip}...")
    paquete = IP(dst=ip)/ICMP()
    respuesta = sr1(paquete, timeout=3, verbose=0)  # Timeout de 3 segundos
    if respuesta:
        print("Respuesta recibida:")
        respuesta.show()
    else:
        print(f"No se ha recibido respuesta de {ip}")

def capture_tcp(filter_str, count, iface=None, save_file=None):
    """Captura paquetes TCP con el filtro especificado y los muestra."""
    print(f"Capturando {count} paquetes con filtro '{filter_str}'...")
    try:
        paquetes = sniff(filter=filter_str, count=count, iface=iface, timeout=10)
        if paquetes:
            print(f"Se capturaron {len(paquetes)} paquetes:")
            paquetes.show()
            if save_file:
                paquetes.to_pcap(save_file)
                print(f"Paquetes guardados en {save_file}")
        else:
            print("No se capturaron paquetes")
    except PermissionError:
        print("Error: Se requieren privilegios de administrador (ejecuta con sudo)")

def main():
    # Prueba de ping a 8.8.8.8
    ping_host("8.8.8.8")
    
    # Prueba de ping a 8.8.8.85 (probablemente inalcanzable)
    ping_host("8.8.8.85")
    
    # Captura de 10 paquetes TCP genéricos
    capture_tcp(filter_str="tcp", count=10)
    
    # Captura de 10 paquetes FTP (puertos 21 o 20)
    capture_tcp(filter_str="tcp port 21 or tcp port 20", count=10, save_file="ftp_capture.pcap")

if __name__ == "__main__":
    main()
    ````

