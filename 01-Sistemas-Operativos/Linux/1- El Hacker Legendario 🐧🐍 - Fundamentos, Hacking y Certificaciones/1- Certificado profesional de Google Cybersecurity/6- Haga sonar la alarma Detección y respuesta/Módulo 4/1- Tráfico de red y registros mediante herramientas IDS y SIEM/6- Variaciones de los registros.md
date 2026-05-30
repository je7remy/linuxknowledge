---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Variaciones de los registros


### **Entendiendo los Formatos de Registros**

Al igual que un recibo de una tienda, que documenta una compra, los **registros (logs)** documentan los **eventos** que ocurren en una red o sistema. 🧾 Y así como los recibos varían (una factura de auto es más detallada que un recibo de restaurante), los registros también vienen en diferentes formatos.

Como analista de seguridad, tu trabajo es interpretar estos registros. Aunque no todos se vean iguales, generalmente contienen información clave como **marcas de tiempo**, **características del sistema** (ej. direcciones IP) y una **descripción del evento** (qué acción se tomó y quién la realizó).

Algunos registros son legibles por humanos y otros por máquinas. Unos son _verbose_ (muy detallados), mientras que otros son simples.

---

### **Formatos de Registro Comunes**

#### **1. Syslog**

Es uno de los formatos más comunes. Funciona como un **protocolo** (para transportar registros) y como un **formato**. Una entrada Syslog tiene tres partes:

- **Encabezado:** Incluye la marca de tiempo, el nombre del host y el nombre de la aplicación.
    
- **Datos Estructurados:** Contiene pares clave-valor para información adicional (ej. `eventSource: Application`).
    
- **Mensaje:** El texto detallado del registro sobre el evento.
    

#### **2. JSON (JavaScript Object Notation)**

Es un formato de texto diseñado para ser fácil de leer tanto para humanos como para máquinas.

- Utiliza **pares clave-valor** para estructurar los datos (ej. `"Alerta": "Software malicioso"`).
    
- Los datos se encierran en corchetes rizados `{ }`.
    
- Es conocido por su simplicidad.
    

#### **3. XML (eXtensible Markup Language)**

Es un formato para almacenar y transmitir datos.

- En lugar de pares clave-valor, utiliza **etiquetas** para definir la estructura (ej. `<firstName>Juan</firstName>`).
    

#### **4. CSV (Valores Separados por Comas)**

Es un formato simple que utiliza un separador, como una coma, para distinguir los diferentes valores de los datos en una línea.

---

### **Próximos Pasos**

Ahora que conoces la diversidad de formatos de registro, el siguiente paso es aprender a evaluar los registros para construir un contexto en torno a una detección, explorando cómo se utilizan las firmas de los **Sistemas de Detección de Intrusiones (IDS)**.

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[5- Rebeca - Aprender nuevas herramientas y tecnologías]]
- ➡️ Siguiente: [[7- Visión general de los formatos de los archivos de registro]]
