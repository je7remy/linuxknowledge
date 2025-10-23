
# 🧠 Evaluación sobre SIEM, Splunk y Chronicle

---

### **1️⃣ Pregunta 1**

**Pregunta:**

> En el Lenguaje de Procesamiento de Búsqueda (SPL), ¿qué carácter especial es un comodín que puede utilizarse para sustituir por cualquier otro carácter?

**✅ Respuesta correcta:** `*`

**📘 Explicación:**  
En **SPL (Search Processing Language)**, el asterisco (`*`) actúa como **comodín universal**, reemplazando cualquier conjunto de caracteres.  
Ejemplo:

```spl
index=security user="admin*"
```

Busca todos los usuarios cuyo nombre comience con “admin”.

---

### **2️⃣ Pregunta 2**

**Pregunta:**

> ¿Cuáles de los siguientes pasos forman parte del proceso de administración de información y eventos de seguridad (SIEM)?  
> _(Seleccione tres respuestas.)_

**✅ Respuestas correctas:**

- Recoger y procesar datos
    
- Normalización de datos para su lectura y análisis
    
- Indexación de datos para mejorar el rendimiento de las búsquedas
    

**📘 Explicación:**  
El **proceso SIEM** consta de tres fases principales:

1. **Recopilar y procesar:** se agrupan los registros de múltiples dispositivos.
    
2. **Normalizar:** se les da un formato común, eliminando datos irrelevantes.
    
3. **Indexar:** se ordenan para permitir búsquedas rápidas y análisis eficientes.
    

---

### **3️⃣ Pregunta 3**

**Pregunta:**

> Rellene el espacio en blanco: Google SecOps (Chronicle) utiliza _____ para buscar en registros no estructurados.

**✅ Respuesta correcta:**  
**Búsqueda de registros en bruto**

**📘 Explicación:**  
En **Chronicle**, la **búsqueda de registros sin procesar (Raw Log Search)** permite examinar los datos **no normalizados**, útiles para investigar campos que no fueron incluidos durante el proceso de normalización o para resolver fallos de ingesta.

---

### **4️⃣ Pregunta 4**

**Pregunta:**

> ¿Cuál de los siguientes es el Lenguaje de consulta de Splunk?

**✅ Respuesta correcta:**  
**SPL (Search Processing Language)**

**📘 Explicación:**  
**Splunk** utiliza su propio lenguaje de consultas, **SPL**, diseñado para filtrar, transformar y analizar grandes volúmenes de datos de registros.  
Ejemplo:

```spl
index=firewall action=blocked | stats count by src_ip
```

Muestra cuántas veces fue bloqueada cada IP de origen.

---

### **📋 Resumen Final**

|Herramienta|Lenguaje / Proceso|Propósito principal|
|---|---|---|
|**Splunk**|**SPL**|Analizar y visualizar registros mediante búsquedas y comandos personalizados|
|**Chronicle (Google SecOps)**|**UDM y búsqueda en bruto**|Buscar datos normalizados o sin procesar|
|**SIEM**|**Recopilar → Normalizar → Indexar**|Unificar, analizar y monitorear eventos de seguridad|

---

