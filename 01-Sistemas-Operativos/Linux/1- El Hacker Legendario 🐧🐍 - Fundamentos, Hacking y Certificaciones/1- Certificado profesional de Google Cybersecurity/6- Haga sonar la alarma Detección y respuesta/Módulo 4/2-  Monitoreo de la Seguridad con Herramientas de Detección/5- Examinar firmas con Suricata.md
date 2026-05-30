---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Examinar firmas con Suricata

## 🧠 **Análisis de Firmas con Suricata (IDS Basado en Firmas)**

---

### 🧩 **Introducción**

Después de aprender sobre el análisis basado en firmas, ahora profundizaremos en cómo **examinar y comprender firmas dentro de Suricata**, un **IDS (Sistema de Detección de Intrusiones) de código abierto**.  
Suricata permite **analizar, personalizar y probar firmas** que definen reglas para detectar comportamientos sospechosos en la red.

Las **firmas preescritas** funcionan como **plantillas**: sirven como punto de partida para crear o modificar reglas según las necesidades de cada entorno.  
También se pueden **escribir nuevas reglas** adaptadas a escenarios específicos.

---

### ⚙️ **Exploración de Firmas en Suricata**

1. En un sistema Linux (por ejemplo, Ubuntu), los archivos de configuración de Suricata se encuentran en el directorio:  
```

/etc/suricata/

```
2. Dentro de esta carpeta, las **reglas (rules)** se almacenan en:  
```

/etc/suricata/rules/

````
3. Para visualizar las reglas personalizadas, se pueden usar los comandos:
```bash
cd /etc/suricata/rules
ls
less custom.rules
````

- El comando `less` permite revisar el contenido del archivo página por página.
    
- Las líneas que comienzan con `#` son **comentarios**, y Suricata las **ignora** durante la ejecución.
    

---

### 🧱 **Estructura de una Firma en Suricata**

Cada **firma** contiene tres secciones principales:

1. **Acción**  
    Indica lo que debe hacer el IDS cuando se cumplen las condiciones.  
    En el ejemplo, la acción es `alert`, lo que significa que Suricata **generará una alerta** al detectar el patrón indicado.
    
2. **Encabezado (Header)**  
    Define el **tipo de tráfico** que se evaluará.  
    Ejemplo:
    
    ```
    alert http HOME_NET any -> EXTERNAL_NET any
    ```
    
    - `alert`: acción a ejecutar.
        
    - `http`: protocolo analizado.
        
    - `HOME_NET`: red interna (origen).
        
    - `EXTERNAL_NET`: red externa (destino).
        
    - `any`: cualquier puerto.
        
    - `->`: dirección del tráfico (saliente de la red interna hacia la externa).
        
    
    📘 **Interpretación:**  
    Esta regla activa una alerta cada vez que detecta **tráfico HTTP saliente** desde la red doméstica hacia una red externa.
    
3. **Opciones (Options)**  
    Son parámetros adicionales encerrados entre paréntesis y separados por punto y coma `;`.
    
    Ejemplo:
    
    ```
    (msg:"GET on wire"; flow:established; content:"GET";)
    ```
    
    - `msg:` define el mensaje que mostrará la alerta.
        
    - `flow:` especifica la dirección o estado de la conexión (aquí indica que la conexión está _establecida_).
        
    - `content:` busca una coincidencia dentro del contenido del paquete.  
        En este caso, busca el texto `"GET"`, correspondiente a una **petición HTTP** de lectura.
        

---

### 🌐 **Ejemplo de Firma Completa**

```
alert http HOME_NET any -> EXTERNAL_NET any (msg:"GET on wire"; flow:established; content:"GET"; sid:1001; rev:1;)
```

📖 **Desglose:**

- `alert` → acción: genera una alerta.
    
- `http` → protocolo HTTP.
    
- `HOME_NET any -> EXTERNAL_NET any` → tráfico de salida desde la red interna a la externa.
    
- `msg:"GET on wire"` → mensaje de alerta.
    
- `flow:established` → conexión establecida.
    
- `content:"GET"` → busca peticiones HTTP.
    
- `sid:1001` → identificador único de la firma.
    
- `rev:1` → número de revisión de la firma.
    

🔎 **Resultado:**  
Esta firma alerta cada vez que **Suricata detecta la palabra “GET” en una conexión HTTP saliente**, lo que indica una **petición hacia un servidor externo**.

---

### 🧰 **Aplicación Práctica**

Cada entorno de red es diferente.  
Por eso, las firmas deben **probarse, ajustarse o reescribirse** para mejorar su precisión.  
Como analista de seguridad, puedes:

- **Modificar firmas existentes** para adaptarlas a tu tráfico de red.
    
- **Reducir falsos positivos** mediante filtros más específicos.
    
- **Crear nuevas firmas** para detectar comportamientos únicos de tu entorno.
    

---

### 🧠 **Conclusión**

Suricata es una herramienta poderosa que permite:

- Analizar y personalizar **firmas NIDS**.
    
- Detectar tráfico sospechoso con precisión.
    
- Registrar alertas detalladas para su análisis posterior.
    

Dominar la lectura y configuración de firmas en Suricata es un paso clave en el desarrollo de tus **habilidades como analista de seguridad**, permitiéndote fortalecer la defensa activa de los sistemas frente a amenazas.
### 🧩 Pregunta

¿Cuál de las siguientes afirmaciones es cierta cuando se trata de analizar firmas de Suricata?

- [x] El primer campo especifica la acción.  
- [ ] Las opciones de las reglas van encerradas entre punto y coma.  
- [ ] La opción de mensaje inspecciona el contenido de un paquete.  
- [ ] Las flechas especifican la gravedad de una amenaza.  

---

### ✅ Respuesta correcta
**El primer campo especifica la acción.**

---

### 💡 Explicación
En una **firma de Suricata**, el **primer campo** define la **acción** que el sistema debe realizar cuando se cumplen las condiciones de la regla.  
Algunas acciones comunes son:
- `alert` → genera una alerta.  
- `pass` → ignora el tráfico.  
- `drop` o `reject` → bloquea el tráfico.  

Esto permite que el IDS reaccione adecuadamente ante comportamientos sospechosos detectados en la red.

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[4- Componentes de una firma de Detección]]
- ➡️ Siguiente: [[6- Examinar los registros de Suricata]]
