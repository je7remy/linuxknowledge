
## 🧠 **Registros Generados por Suricata (EVE JSON)**

---

### 🧩 **Introducción**

Suricata genera y almacena sus eventos y alertas en un formato llamado **EVE JSON**, que significa **Extensible Event Format en formato JSON (JavaScript Object Notation)**.  
Este formato permite representar la información mediante **pares clave–valor**, lo que facilita la **búsqueda, lectura y extracción de datos** en los archivos de registro.

---

### ⚙️ **Tipos de registros generados por Suricata**

Suricata produce **dos tipos principales de registros**:

1. **Registros de alerta**  
   Contienen información **relevante para la seguridad**, generalmente relacionada con **firmas que se han activado**.  
   Ejemplo: una firma que detecta tráfico sospechoso o malware genera una alerta con detalles como:
   - Tipo de evento (`alert`)
   - Direcciones IP de origen y destino  
   - Protocolo utilizado  
   - Mensaje de la firma  
   - Identificador único (SID)

   📘 **Ejemplo simplificado:**
   ```json
   {
     "event_type": "alert",
     "src_ip": "192.168.1.10",
     "dest_ip": "203.0.113.45",
     "proto": "TCP",
     "alert": {
       "msg": "Malware Detected - Suspicious Traffic",
       "sid": 100001
     }
   }
```

2. **Registros de telemetría de red**  
    Estos registros documentan **flujos de tráfico normales**, no necesariamente relacionados con seguridad.  
    Ejemplo: conexiones HTTP legítimas, puertos activos o solicitudes a sitios web.
    
    📘 **Ejemplo simplificado:**
    
    ```json
    {
      "event_type": "http",
      "src_ip": "192.168.1.15",
      "dest_ip": "93.184.216.34",
      "http": {
        "hostname": "example.com",
        "user_agent": "Mozilla/5.0",
        "content_type": "text/html"
      }
    }
    ```
    

---

### 🔍 **Diferencias clave entre ambos tipos de registros**

|Característica|Registro de Alerta 🛑|Registro de Telemetría 🌐|
|---|---|---|
|**Propósito**|Indicar actividad sospechosa o maliciosa.|Mostrar tráfico o actividad general.|
|**Origen**|Firmas activadas por Suricata.|Flujo normal de red capturado.|
|**Campo principal (`event_type`)**|`alert`|`http`, `dns`, `flow`, etc.|
|**Relevancia para seguridad**|Alta|Variable|
|**Ejemplo de uso**|Detección de malware o ataques.|Monitoreo del rendimiento de red.|

---

### 🧩 **Campos importantes en los registros**

- **`event_type`** → identifica el tipo de evento (`alert`, `http`, `dns`, etc.).
    
- **`src_ip` / `dest_ip`** → direcciones IP de origen y destino.
    
- **`proto`** → protocolo de comunicación (TCP, UDP, ICMP...).
    
- **`alert.msg`** → mensaje descriptivo de la firma que se activó.
    
- **`alert.sid`** → ID único de la firma.
    
- **`http.hostname`** → sitio web o dominio al que se accede.
    
- **`http.user_agent`** → software que realiza la solicitud (ej. navegador).
    
- **`http.content_type`** → tipo de contenido devuelto (ej. `text/html`).
    

---

### 🧠 **Conclusión**

- Los **registros de alerta** permiten identificar comportamientos sospechosos o ataques en la red.
    
- Los **registros de telemetría** ayudan a comprender el tráfico y las conexiones en curso.
    
- Ambos tipos de registros son esenciales para construir una **narrativa completa de un incidente de seguridad**.
    

Como analista, comprender el formato **EVE JSON** y la estructura de los registros te permitirá **investigar eficazmente eventos de seguridad y validar la efectividad de las firmas IDS**.