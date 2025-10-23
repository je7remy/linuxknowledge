
## 🧠 **Actividad: Examina alertas, registros y reglas con Suricata**

---

### 🧩 **Resumen de la actividad**

En este laboratorio práctico aprenderás a **crear, ejecutar y analizar reglas personalizadas en Suricata**, un sistema de detección y prevención de intrusiones (**IDS/IPS**) de código abierto.  
Al finalizar, comprenderás cómo se generan las **alertas**, cómo se registran los eventos y cómo interpretar los archivos de salida **fast.log** y **eve.json**.

---

### 🧰 **Objetivos de la práctica**

1. Examinar la estructura de una **regla personalizada** en Suricata.  
2. **Activar** una regla y observar las alertas generadas.  
3. **Analizar los registros** generados en los archivos `fast.log` y `eve.json`.  

---

### ⚙️ **Archivos utilizados**

| Archivo | Descripción | Ubicación |
|----------|-------------|-----------|
| **sample.pcap** | Captura de tráfico de red de ejemplo. | `/home/analyst/sample.pcap` |
| **custom.rules** | Contiene reglas personalizadas para ejecutar con Suricata. | `/home/analyst/custom.rules` |
| **fast.log** | Registro rápido de alertas (formato simple). | `/var/log/suricata/fast.log` |
| **eve.json** | Registro principal en formato JSON, con datos detallados de eventos. | `/var/log/suricata/eve.json` |

---

### 🧩 **Tarea 1: Examina una regla personalizada**

Comando:
```bash
cat custom.rules
````

📘 **Ejemplo de regla:**

```
alert http $HOME_NET any -> $EXTERNAL_NET any (msg:"GET on wire"; flow:established,to_server; content:"GET"; http_method; sid:12345; rev:3;)
```

**Componentes de la regla:**

- **Acción:** `alert` (genera una alerta).
    
- **Encabezado:** especifica protocolo, dirección, IPs y puertos.
    
- **Opciones:** definen parámetros adicionales:
    
    - `msg:` mensaje mostrado en la alerta.
        
    - `flow:` dirección del tráfico (cliente a servidor).
        
    - `content:` busca coincidencias específicas (“GET”).
        
    - `sid:` ID único de la regla.
        
    - `rev:` número de revisión.
        

🔎 **Interpretación:**  
La regla genera una alerta cuando detecta una solicitud HTTP con el método `GET` que proviene de la red interna (`$HOME_NET`) hacia una red externa (`$EXTERNAL_NET`).

---

### 🚀 **Tarea 2: Activa una regla personalizada en Suricata**

Antes de ejecutar, verifica los archivos del directorio:

```bash
ls -l /var/log/suricata
```

Ejecuta Suricata con la regla personalizada y el tráfico de muestra:

```bash
sudo suricata -r sample.pcap -S custom.rules -k none
```

📘 **Parámetros:**

- `-r sample.pcap` → archivo de captura de paquetes.
    
- `-S custom.rules` → reglas personalizadas a aplicar.
    
- `-k none` → desactiva la verificación de checksum (no necesaria en archivos pcap).
    

Suricata procesará los paquetes y generará alertas que se guardarán en:

```
/var/log/suricata/fast.log
```

Visualiza las alertas:

```bash
cat /var/log/suricata/fast.log
```

📄 **Ejemplo de salida:**

```
11/23/2022-12:38:34.624866 [**] [1:12345:3] GET on wire [**] {TCP} 172.21.224.2:49652 -> 142.250.1.139:80
```

Cada línea representa una alerta con:

- **Hora del evento**
    
- **ID de la regla**
    
- **Mensaje**
    
- **Protocolo**
    
- **Dirección y puerto de origen/destino**
    

---

### 📊 **Tarea 3: Examina el resultado de `eve.json`**

El archivo `eve.json` contiene **alertas y telemetría de red** en formato **JSON**.  
Es el registro más detallado y completo de Suricata.

Visualiza el contenido:

```bash
cat /var/log/suricata/eve.json
```

Para una vista más legible:

```bash
jq . /var/log/suricata/eve.json | less
```

📘 **Ejemplo de alerta en JSON:**

```json
{
  "timestamp": "2022-11-23T12:38:34.624866",
  "event_type": "alert",
  "src_ip": "172.21.224.2",
  "dest_ip": "142.250.1.139",
  "proto": "TCP",
  "alert": {
    "signature": "GET on wire",
    "severity": 3,
    "category": "Unknown",
    "sid": 12345
  }
}
```

🔹 **Propiedad de gravedad:** `3`  
🔹 **Dirección IP de destino (último evento):** `142.250.1.139`  
🔹 **Firma de alerta (primera entrada):** `"GET on wire"`

Extrae campos específicos con:

```bash
jq -c "[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]" /var/log/suricata/eve.json
```

---

### 🧠 **Conclusión**

✅ Has aprendido a:

- **Examinar** una regla personalizada en Suricata.
    
- **Activarla** y generar alertas con tráfico de ejemplo.
    
- **Interpretar** los registros `fast.log` y `eve.json`.
    

Este ejercicio te brinda una comprensión práctica de cómo Suricata **detecta, registra y reporta eventos de red**, una habilidad esencial en el trabajo de un **analista de seguridad**.

---

