
# 🧪 **Lab: Examina alertas, registros y reglas con Suricata**

**Tipo:** Lab · **Duración:** 1 hora · **Costo:** Sin costo · **Nivel:** Introductorio  
**Nota:** Este lab puede incorporar herramientas de IA para facilitar tu aprendizaje.

---

## 🎯 Objetivos de aprendizaje
- Comprender la estructura de una **regla/firma Suricata** (acción, encabezado, opciones).
- **Ejecutar** Suricata contra un `pcap` usando reglas personalizadas.
- **Interpretar** salidas en `fast.log` y `eve.json` (EVE JSON).
- Usar `jq` para **filtrar y leer** eventos en formato JSON.

---

## 🧰 Archivos y ubicaciones
| Archivo / Recurso | Descripción | Ubicación |
|---|---|---|
| `sample.pcap` | Tráfico de red de ejemplo para pruebas | `/home/analyst/sample.pcap` |
| `custom.rules` | Reglas personalizadas iniciales | `/home/analyst/custom.rules` |
| `fast.log` | Registro rápido de alertas (obsoleto para IR/Detección) | `/var/log/suricata/fast.log` |
| `eve.json` | Registro principal en formato EVE JSON | `/var/log/suricata/eve.json` |
| `suricata.yaml` | Configuración (incluye `$HOME_NET`, `$EXTERNAL_NET`) | `/etc/suricata/suricata.yaml` |

> **Variables clave:**  
> - `$HOME_NET` → red local (en el lab: `172.21.224.0/20`)  
> - `$EXTERNAL_NET` → red externa  
> - `$` indica variable en reglas.

---

## 🧭 Flujo del lab
1) **Comienza el lab** → Se abrirá una shell Bash con el usuario `analyst`.  
2) **Tarea 1** → Examina una regla personalizada.  
3) **Tarea 2** → Activa la regla y revisa `fast.log`.  
4) **Tarea 3** → Inspecciona `eve.json` con `jq`.  
5) **Finaliza el lab** → `End Lab` → `Submit`.

---

## 🧩 Tarea 1: Examina una regla personalizada en Suricata
Mostrar la regla:
```bash
cat /home/analyst/custom.rules
````

**Ejemplo de regla:**

```
alert http $HOME_NET any -> $EXTERNAL_NET any (msg:"GET on wire"; flow:established,to_server; content:"GET"; http_method; sid:12345; rev:3;)
```

**Estructura de la regla:**

- **Acción:** `alert` (otras comunes: `drop`, `pass`, `reject`).
    
- **Encabezado:** `http $HOME_NET any -> $EXTERNAL_NET any`
    
    - Protocolo, direcciones/puertos, dirección del flujo (`->`).
        
- **Opciones:** dentro de `(...)` y separadas con `;`
    
    - `msg:"GET on wire"` → texto de la alerta
        
    - `flow:established,to_server` → flujo cliente→servidor
        
    - `content:"GET"; http_method;` → busca método HTTP GET
        
    - `sid:12345` → ID único de firma
        
    - `rev:3` → revisión de la firma
        

> **Prioridad de evaluación en Suricata:** `pass` → `drop` → `reject` → `alert`.

---

## 🚀 Tarea 2: Activa una regla personalizada y revisa `fast.log`

Verifica el directorio de logs **antes**:

```bash
ls -l /var/log/suricata
```

Ejecuta Suricata con `pcap` y reglas:

```bash
sudo suricata -r /home/analyst/sample.pcap -S /home/analyst/custom.rules -k none
```

- `-r` → archivo de entrada (pcap)
    
- `-S` → archivo de reglas
    
- `-k none` → omite verificación de checksums (útil con pcap)
    

Ver logs **después**:

```bash
ls -l /var/log/suricata
cat /var/log/suricata/fast.log
```

**Ejemplo de salida `fast.log`:**

```
11/23/2022-12:38:34.624866  [**] [1:12345:3] GET on wire [**] [Classification: (null)] [Priority: 3] {TCP} 172.21.224.2:49652 -> 142.250.1.139:80
11/23/2022-12:38:58.958203  [**] [1:12345:3] GET on wire [**] [Classification: (null)] [Priority: 3] {TCP} 172.21.224.2:58494 -> 142.250.1.139:80
```

**Interpretación rápida por línea:**

- Fecha/hora
    
- `[gid:sid:rev]`
    
- Mensaje de firma
    
- Prioridad
    
- Protocolo
    
- `src_ip:src_port -> dest_ip:dest_port`
    

---

## 📊 Tarea 3: Examina el resultado de `eve.json`

Inspección básica:

```bash
cat /var/log/suricata/eve.json
```

Formato legible con `jq`:

```bash
jq . /var/log/suricata/eve.json | less
# Teclas: f (avanza), b (retrocede), q (salir), Ctrl+C (forzar salida)
```

**Campos típicos en alerta (ejemplo):**

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
    "sid": 12345
  }
}
```

**Consultas útiles con `jq`:**

- Selección de campos clave:
    

```bash
jq -c '[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]' /var/log/suricata/eve.json
```

- Filtrar por `flow_id` (reemplaza `X` por un valor real):
    

```bash
jq 'select(.flow_id==X)' /var/log/suricata/eve.json
```

---

## ✅ Comprobaciones del lab (Q&A del ejercicio)

- **Gravedad (severity) de la primera alerta (`eve.json`):** `3`
    
- **IP de destino del último evento (`eve.json`):** `142.250.1.102`
    
- **Firma de la primera entrada de alerta (`eve.json`):** `GET on wire`
    

---

## 🧠 Conclusión

Al finalizar, podrás:

- **Crear/ajustar** reglas personalizadas y ejecutarlas en Suricata.
    
- **Reproducir análisis** sobre tráfico de ejemplo (`pcap`).
    
- **Leer e interpretar** `fast.log` y **EVE JSON** en `eve.json` con apoyo de `jq`.
    

---

# Repaso del repaso


# 📘 Ejemplar: **Explorar las firmas con Suricata**
**Estado:** Traducido automáticamente del Inglés

---

## 🧩 Resumen de la actividad
Anteriormente, aprendiste sobre análisis de paquetes y la sintaxis básica de **firmas/reglas IDS**. Aquí explorarás **alertas** y **registros** de Suricata (fast.log y eve.json) y el **proceso general de creación de reglas**.

Suricata **supervisa interfaces de red** y aplica **reglas** a los paquetes que pasan; decide si **alerta**, **descarta (drop)**, **rechaza (reject)** o **permite (pass)** el tráfico.  
Las redes **origen/destino** se definen en la configuración, y puedes **escribir reglas personalizadas**.

> Este ejemplo es un **recorrido resuelto** del lab anterior (Qwiklabs): incluye instrucciones detalladas y **soluciones** para que puedas repasar o preparar el cuestionario del módulo.  
> **Nota:** en este lab, *reglas* y *firmas* se usan indistintamente.

---

## 🧭 Escenario
Eres analista de seguridad y debes **monitorear el tráfico** de la red de tu empleador con Suricata y **activar alertas**.

**Flujo de trabajo:**
1. Explorar reglas personalizadas en Suricata.  
2. Ejecutar Suricata con una regla personalizada para **disparar alertas** y revisar **fast.log**.  
3. Analizar la salida adicional en **eve.json** (EVE JSON).

**Archivos provistos en tu HOME:**
- `sample.pcap` — captura de paquetes para probar reglas.  
- `custom.rules` — regla inicial; aquí añadirás tus reglas.

**Registros generados por Suricata (tras la ejecución):**
- `/var/log/suricata/fast.log` — formato simple/obsoleto (útil para verificaciones rápidas).  
- `/var/log/suricata/eve.json` — **registro principal** (EVE JSON), detallado y apto para parsing.

> Cuando crees reglas nuevas, **verifica su funcionamiento** comparando el número de alertas en `fast.log` al ejecutar contra el mismo `sample.pcap`.

---

## ✅ Precondición
El lab inicia con usuario `analyst` autenticado en una **shell Bash**. Puedes empezar al pulsar **Iniciar laboratorio**.

---

## 🧩 Tarea 1 — Examinar una regla personalizada
Mostrar la regla:
```bash
cat ~/custom.rules
````

**Salida esperada (ejemplo):**

```
alert http $HOME_NET any -> $EXTERNAL_NET any (msg:"GET on wire"; flow:established,to_server; content:"GET"; http_method; sid:12345; rev:3;)
```

**Componentes clave:**

- **Acción:** `alert` (otras comunes: `drop`, `pass`, `reject`).
    
- **Encabezado:** `http $HOME_NET any -> $EXTERNAL_NET any`
    
    - Protocolo + dirección del flujo + IP/puertos origen/destino.
        
    - `$HOME_NET` está en `/etc/suricata/suricata.yaml` (en este lab: `172.21.224.0/20`).
        
- **Opciones:** `(...)` separadas por `;`
    
    - `msg:"GET on wire"` — texto de alerta
        
    - `flow:established,to_server` — tráfico cliente ➜ servidor
        
    - `content:"GET"; http_method;` — busca método HTTP **GET**
        
    - `sid:12345` — identificador único de la firma
        
    - `rev:3` — revisión de la firma
        

> **Orden de evaluación interno:** `pass` → `drop` → `reject` → `alert`.

---

## 🚀 Tarea 2 — Activar una regla y revisar `fast.log`

Antes de ejecutar:

```bash
ls -l /var/log/suricata
# (vacío antes de correr Suricata)
```

Ejecutar Suricata con pcap y reglas:

```bash
sudo suricata -r sample.pcap -S custom.rules -k none
```

- `-r sample.pcap` — tráfico de prueba
    
- `-S custom.rules` — reglas a aplicar
    
- `-k none` — omite verificación de checksums (pcap de laboratorio)
    

Verifica archivos creados:

```bash
ls -l /var/log/suricata
cat /var/log/suricata/fast.log
```

**Ejemplo de alertas en `fast.log`:**

```
11/23/2022-12:38:34.624866 [**] [1:12345:3] GET on wire [**] [Classification: (null)] [Priority: 3] {TCP} 172.21.224.2:49652 -> 142.250.1.139:80
11/23/2022-12:38:58.958203 [**] [1:12345:3] GET on wire [**] [Classification: (null)] [Priority: 3] {TCP} 172.21.224.2:58494 -> 142.250.1.139:80
```

Cada línea = 1 alerta (mensaje, gid:sid:rev, prioridad, protocolo, src ➜ dst).

---

## 📊 Tarea 3 — Examinar la salida `eve.json`

Mostrar entradas:

```bash
cat /var/log/suricata/eve.json
```

Formato legible con `jq`:

```bash
jq . /var/log/suricata/eve.json | less
# f/b para avanzar/retroceder, q para salir, Ctrl+C si es necesario
```

**Pregunta (rellena el espacio en blanco) — severidad de la primera alerta:**  
**Respuesta:** `3`

Extraer campos útiles:

```bash
jq -c '[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]' /var/log/suricata/eve.json
```

**Pregunta (rellena el espacio en blanco) — IP destino del último evento:**  
**Respuesta:** `142.250.1.102`

**Pregunta (rellena el espacio en blanco) — firma de la primera alerta:**  
**Respuesta:** `GET on wire`

Ejemplo de filas (salida compacta):

```
["2022-11-23T12:38:34.624866+0000",14500150016149,"GET on wire","TCP","142.250.1.139"]
["2022-11-23T12:38:58.958203+0000",1647223379236084,"GET on wire","TCP","142.250.1.102"]
```

Filtrar por un `flow_id` específico (sustituye `X`):

```bash
jq "select(.flow_id==X)" /var/log/suricata/eve.json
```

---

