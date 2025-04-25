
---

### **Contexto General**
El código tiene como objetivo capturar paquetes de red en el puerto TCP 21, que corresponde al protocolo **FTP** (File Transfer Protocol). FTP es un protocolo que transmite datos, incluidos comandos como `USER` (nombre de usuario) y `PASS` (contraseña), en texto plano, lo que lo hace vulnerable a la interceptación. El script utiliza **Scapy**, una biblioteca de Python para manipulación y análisis de paquetes de red, para "olfatear" (sniff) el tráfico y extraer información del campo `Raw` (carga útil) de los paquetes.

**Advertencia ética y legal**: Interceptar tráfico de red sin autorización es ilegal en muchos países y puede violar leyes de privacidad. Este tipo de código debe usarse únicamente en entornos controlados, con consentimiento explícito (por ejemplo, en pruebas de seguridad autorizadas o en redes propias). El análisis que sigue es puramente educativo.

---

### **Fragmento 1: Código Básico**
```python
from scapy.all import sniff, Raw

def analisis(paquete):
    if paquete.haslayer(Raw):
        texto = paquete[Raw].load.decode('utf-8', errors='ignore')
        print(texto)

paquetes = sniff(filter="tcp port 21", count=9999)

for paquete in paquetes:
    analisis(paquete)
```

#### **Explicación Paso a Paso**
1. **Importación de módulos**:
   - `from scapy.all import sniff, Raw`: Importa la función `sniff` para capturar paquetes y la clase `Raw` para acceder a la carga útil de los paquetes.
   - **Scapy** es una biblioteca poderosa que permite capturar, analizar y manipular paquetes de red a nivel de bajo nivel.

2. **Función `analisis(paquete)`**:
   - Recibe un paquete capturado como argumento.
   - `if paquete.haslayer(Raw)`: Verifica si el paquete tiene una capa `Raw` (carga útil), que contiene los datos enviados en el protocolo (en este caso, comandos o datos FTP).
   - `texto = paquete[Raw].load.decode('utf-8', errors='ignore')`:
     - `paquete[Raw].load`: Accede a los datos crudos (bytes) de la capa `Raw`.
     - `.decode('utf-8', errors='ignore')`: Convierte los bytes a una cadena de texto en codificación UTF-8. Si hay bytes no válidos, los ignora en lugar de generar un error.
   - `print(texto)`: Imprime el texto decodificado, que podría incluir comandos FTP como `USER`, `PASS`, o cualquier otro dato.

3. **Captura de paquetes**:
   - `paquetes = sniff(filter="tcp port 21", count=9999)`:
     - `sniff`: Función de Scapy que captura paquetes de red.
     - `filter="tcp port 21"`: Aplica un filtro **BPF** (Berkeley Packet Filter) para capturar solo paquetes TCP en el puerto 21 (FTP).
     - `count=9999`: Limita la captura a un máximo de 9999 paquetes.
     - Nota: No se especifica una interfaz de red (`iface`), por lo que Scapy usará la interfaz predeterminada del sistema.

4. **Procesamiento de paquetes**:
   - `for paquete in paquetes`: Itera sobre los paquetes capturados.
   - `analisis(paquete)`: Llama a la función `analisis` para cada paquete.

#### **Propósito y Limitaciones**
- **Propósito**: Capturar e imprimir cualquier dato en la capa `Raw` de los paquetes FTP, lo que podría incluir credenciales.
- **Limitaciones**:
  - Imprime **todos** los datos de la capa `Raw`, lo que puede generar mucho ruido (datos irrelevantes).
  - No filtra específicamente credenciales (`USER`, `PASS`), por lo que el usuario debe inspeccionar manualmente la salida.
  - No maneja errores (por ejemplo, si el paquete no se puede decodificar como UTF-8).
  - Captura hasta 9999 paquetes, lo que podría ser excesivo o insuficiente dependiendo del caso.
  - No especifica la interfaz de red, lo que puede causar problemas en sistemas con múltiples interfaces.

---

### **Fragmento 2: Filtrado de Comandos FTP**
```python
from scapy.all import sniff, Raw

def analisis(paquete):
    if paquete.haslayer(Raw):
        try:
            texto = paquete[Raw].load.decode('utf-8', errors='ignore')
            if any(cmd in texto for cmd in ["USER", "PASS", "EPRT", "EPSV", "MDTM", "PASV", "REST", "SIZE", "TVFS", "211"]):
                print(">>", texto.strip())
        except:
            pass

paquetes = sniff(filter="tcp port 21", count=9999)

for paquete in paquetes:
    analisis(paquete)
```

#### **Cambios y Evolución**
1. **Manejo de Errores**:
   - Se agrega un bloque `try`/`except` alrededor del procesamiento del texto.
   - `except: pass`: Ignora cualquier error (por ejemplo, problemas al decodificar los bytes).
   - Esto hace que el script sea más robusto, ya que no se detendrá si encuentra un paquete malformado o datos no decodificables.

2. **Filtrado Específico de Comandos FTP**:
   - `if any(cmd in texto for cmd in ["USER", "PASS", "EPRT", "EPSV", "MDTM", "PASV", "REST", "SIZE", "TVFS", "211"])`:
     - Verifica si el texto contiene alguno de los comandos FTP especificados en la lista.
     - Comandos clave:
       - `USER`: Nombre de usuario.
       - `PASS`: Contraseña.
       - Otros (`EPRT`, `EPSV`, `PASV`, etc.): Comandos FTP relacionados con la transferencia de datos o configuración.
       - `211`: Código de respuesta FTP (estado del servidor).
     - Solo imprime el texto si contiene uno de estos comandos, reduciendo el ruido en la salida.
   - `print(">>", texto.strip())`:
     - Agrega un prefijo `>>` para destacar los resultados relevantes.
     - `texto.strip()`: Elimina espacios en blanco o caracteres de nueva línea al inicio y final del texto.

3. **Sin Cambios en la Captura**:
   - La línea `sniff(filter="tcp port 21", count=9999)` permanece igual, con las mismas limitaciones (sin interfaz específica, límite de 9999 paquetes).

#### **Propósito y Mejoras**
- **Propósito**: Enfocarse en comandos FTP específicos, especialmente `USER` y `PASS`, para capturar credenciales y otros datos relevantes.
- **Mejoras**:
  - Filtrado de comandos reduce la cantidad de datos irrelevantes impresos.
  - Manejo de errores evita que el script falle ante paquetes problemáticos.
- **Limitaciones**:
  - La lista de comandos es extensa y puede incluir algunos irrelevantes para capturar credenciales (por ejemplo, `211` o `TVFS`).
  - Sigue capturando 9999 paquetes, lo que puede ser ineficiente.
  - No especifica interfaz de red.

---

### **Fragmento 3: Cambio a Timeout**
```python
from scapy.all import sniff, Raw

def analisis(paquete):
    if paquete.haslayer(Raw):
        texto = paquete[Raw].load.decode('utf-8', errors='ignore')
        print(texto)

paquetes = sniff(filter="tcp port 21", timeout=60)

for paquete in paquetes:
    analisis(paquete)
```

#### **Cambios y Evolución**
1. **Vuelta a la Simplicidad**:
   - La función `analisis` regresa al diseño del Fragmento 1: imprime todo el contenido de la capa `Raw` sin filtrar comandos específicos.
   - Se elimina el manejo de errores (`try`/`except`) y el filtrado de comandos.

2. **Cambio en el Modo de Captura**:
   - `paquetes = sniff(filter="tcp port 21", timeout=60)`:
     - Reemplaza `count=9999` por `timeout=60`.
     - Ahora el script captura paquetes durante **60 segundos** en lugar de un número fijo de paquetes.
     - Esto permite un enfoque basado en tiempo, útil para pruebas rápidas o cuando no se sabe cuántos paquetes se necesitarán.

#### **Propósito y Limitaciones**
- **Propósito**: Probar la captura de paquetes FTP durante un período de tiempo fijo (60 segundos) e imprimir todos los datos de la capa `Raw`.
- **Ventajas**:
  - El uso de `timeout` permite controlar la duración de la captura, lo que es más práctico en algunos casos.
- **Limitaciones**:
  - Vuelve a imprimir todos los datos, generando ruido.
  - No maneja errores, por lo que puede fallar con paquetes malformados.
  - No especifica interfaz de red.

---

### **Fragmento 4: Especificación de Interfaz**
```python
from scapy.all import sniff, Raw

def analisis(paquete):
    if paquete.haslayer(Raw):
        texto = paquete[Raw].load.decode('utf-8', errors='ignore')
        print(texto)

paquetes = sniff(filter="tcp port 21", iface="eth0", count=9999)

for paquete in paquetes:
    analisis(paquete)
```

#### **Cambios y Evolución**
1. **Sin Cambios en `analisis`**:
   - La función `analisis` es idéntica al Fragmento 3: imprime todo el contenido de la capa `Raw` sin filtrado ni manejo de errores.

2. **Especificación de Interfaz**:
   - `paquetes = sniff(filter="tcp port 21", iface="eth0", count=9999)`:
     - Agrega el parámetro `iface="eth0"`, que indica que la captura se realizará en la interfaz de red `eth0`.
     - Esto es importante en sistemas con múltiples interfaces (por ejemplo, Ethernet, Wi-Fi, VPN), ya que asegura que Scapy capture en la interfaz correcta.
   - Vuelve a usar `count=9999` en lugar de `timeout`, retomando el enfoque de capturar un número fijo de paquetes.

#### **Propósito y Mejoras**
- **Propósito**: Capturar paquetes FTP en una interfaz específica (`eth0`) e imprimir todos los datos de la capa `Raw`.
- **Mejoras**:
  - La especificación de `iface` hace que el script sea más preciso en entornos con múltiples interfaces.
- **Limitaciones**:
  - Sigue imprimiendo todos los datos, lo que genera ruido.
  - No maneja errores.
  - El límite de 9999 paquetes puede ser arbitrario.

---

### **Fragmento 5: Filtrado Simple de Credenciales**
```python
from scapy.all import sniff, Raw

def analisis(paquete):
    if paquete.haslayer(Raw):
        texto = paquete[Raw].load.decode('utf-8', errors='ignore')
        if 'USER' in texto or 'PASS' in texto:
            print(texto)

paquetes = sniff(filter="tcp port 21", iface="eth0", count=9999)

for paquete in paquetes:
    analisis(paquete)
```

#### **Cambios y Evolución**
1. **Filtrado Específico de Credenciales**:
   - `if 'USER' in texto or 'PASS' in texto`:
     - Filtra los paquetes para imprimir solo aquellos que contienen las cadenas `USER` o `PASS`, que corresponden al nombre de usuario y contraseña en FTP.
     - Es un enfoque más directo y enfocado que el del Fragmento 2, que incluía muchos comandos FTP adicionales.
   - `print(texto)`: Imprime el texto sin modificaciones adicionales (sin prefijo `>>` ni `strip()`).

2. **Captura Igual al Fragmento 4**:
   - `sniff(filter="tcp port 21", iface="eth0", count=9999)`: Mantiene la interfaz `eth0` y el límite de 9999 paquetes.

#### **Propósito y Mejoras**
- **Propósito**: Capturar e imprimir únicamente los paquetes FTP que contienen credenciales (`USER` o `PASS`), enfocándose en la interceptación de nombres de usuario y contraseñas.
- **Mejoras**:
  - Filtrado más específico que reduce el ruido al centrarse solo en credenciales.
  - Mantiene la especificación de la interfaz `eth0`.
- **Limitaciones**:
  - No maneja errores, lo que puede causar problemas con paquetes malformados.
  - El límite de 9999 paquetes sigue siendo arbitrario.
  - No usa `strip()` ni otros formateos, por lo que la salida puede incluir caracteres innecesarios.

---

### **Evolución General del Código**
El código evoluciona desde un enfoque básico y ruidoso (imprimir todos los datos de la capa `Raw`) hacia uno más específico y práctico (filtrar credenciales `USER` y `PASS`). Los principales hitos en la evolución son:

1. **Fragmento 1**: Captura básica sin filtrado, imprime todo el contenido de la capa `Raw`.
2. **Fragmento 2**: Introduce filtrado de comandos FTP y manejo de errores, pero incluye comandos irrelevantes.
3. **Fragmento 3**: Simplifica el análisis y cambia a un enfoque basado en tiempo (`timeout`).
4. **Fragmento 4**: Agrega la especificación de la interfaz de red (`eth0`).
5. **Fragmento 5**: Se enfoca exclusivamente en credenciales (`USER`, `PASS`), manteniendo la interfaz específica.

#### **Aspectos Clave de la Evolución**
- **Filtrado**: Pasa de no filtrar (Fragmentos 1, 3, 4) a filtrar comandos específicos (Fragmento 2) y finalmente a filtrar solo credenciales (Fragmento 5).
- **Robustez**: Solo el Fragmento 2 incluye manejo de errores.
- **Flexibilidad en Captura**: Alterna entre límite de paquetes (`count`) y tiempo (`timeout`).
- **Precisión**: La adición de `iface` en los Fragmentos 4 y 5 mejora la usabilidad en sistemas complejos.

---

### **Uso del Código**
Este tipo de script se utiliza en **pruebas de seguridad** o **análisis de red** para:
- Identificar vulnerabilidades en protocolos como FTP, que envía credenciales en texto plano.
- Demostrar la importancia de usar protocolos seguros (por ejemplo, SFTP o FTPS).
- Realizar auditorías de seguridad en entornos controlados.

**Pasos para Ejecutar**:
1. Instalar Scapy: `pip install scapy`.
2. Ejecutar el script con permisos de administrador (requerido para capturar paquetes):
   - En Linux: `sudo python3 script.py`.
   - En Windows: Ejecutar como administrador.
3. Asegurarse de que la interfaz `eth0` (o la especificada) existe. Puedes listar interfaces con:
   ```python
   from scapy.all import get_if_list
   print(get_if_list())
   ```
4. Configurar un entorno de prueba (por ejemplo, un servidor FTP local) para generar tráfico.

**Consideraciones**:
- El script debe ejecutarse en una red donde el tráfico FTP sea visible (por ejemplo, en modo promiscuo o en un punto de la red como un switch).
- En redes modernas, el tráfico FTP es raro debido a su inseguridad; protocolos como SFTP son más comunes.

---

### **Recomendaciones para Mejorar el Código**
Basado en la evolución:
1. **Manejo de Errores Completo**:
   - Reintroducir `try`/`except` para manejar errores de decodificación y otros problemas.
2. **Filtrado Más Inteligente**:
   - Usar expresiones regulares para capturar `USER` y `PASS` con mayor precisión (por ejemplo, `r'^USER\s+(.+)$'`).
3. **Salida Formateada**:
   - Guardar las credenciales en un archivo o mostrarlas con un formato claro (por ejemplo, separar usuario y contraseña).
4. **Captura Dinámica**:
   - Combinar `timeout` y `count` para detener la captura tras un tiempo o un número de paquetes, según ocurra primero.
5. **Interfaz Configurable**:
   - Permitir al usuario especificar la interfaz mediante argumentos de línea de comandos.
6. **Soporte para Otros Protocolos**:
   - Extender el script para capturar credenciales en otros protocolos en texto plano (por ejemplo, HTTP con `tcp port 80`).

Ejemplo:
```python
from scapy.all import sniff, Raw
import argparse

def analisis(paquete):
    if paquete.haslayer(Raw):
        try:
            texto = paquete[Raw].load.decode('utf-8', errors='ignore')
            if 'USER' in texto or 'PASS' in texto:
                print(f"[+] Capturado: {texto.strip()}")
        except Exception as e:
            print(f"[-] Error al procesar paquete: {e}")

def main():
    parser = argparse.ArgumentParser(description="Captura credenciales FTP")
    parser.add_argument('--iface', default='eth0', help='Interfaz de red')
    parser.add_argument('--timeout', type=int, default=60, help='Tiempo de captura (segundos)')
    args = parser.parse_args()

    print(f"[*] Capturando en {args.iface} durante {args.timeout} segundos...")
    paquetes = sniff(filter="tcp port 21", iface=args.iface, timeout=args.timeout)
    for paquete in paquetes:
        analisis(paquete)

if __name__ == "__main__":
    main()
```


---

### **Conclusión**
Los cinco fragmentos muestran una progresión en el desarrollo de un script para capturar credenciales FTP. El código evoluciona desde una captura básica y ruidosa hacia un enfoque más específico y práctico, aunque sigue teniendo limitaciones como la falta de manejo de errores en los últimos fragmentos y un límite arbitrario de paquetes. Este tipo de script es útil para fines educativos o pruebas de seguridad, pero debe usarse con responsabilidad y en cumplimiento de las leyes locales.