
# 🧩 Encabezados IP y Campos del Paquete

> 💭 Analizar los encabezados IP es como leer toda la información escrita en el sobre de un paquete postal: origen, destino, prioridad y condiciones del envío.

---

## 🌐 Concepto general

Los **encabezados IP** forman parte esencial de cada paquete en una red.  
Su función es **garantizar que los datos lleguen correctamente a su destino** a través del **Protocolo de Internet (IP)**, que actúa como un **mensajero digital**.

El encabezado contiene **campos de datos esenciales** que permiten identificar, dirigir y validar el tráfico que circula en una red.

---

## 🏗️ Modelo TCP/IP y la capa de Internet

- El **modelo TCP/IP** es el marco que define cómo los datos se organizan, transmiten y reciben en una red.
    
- En este modelo, la **capa de Internet**:
    
    - Acepta y entrega paquetes.
        
    - Determina la ruta óptima para enviarlos.
        
    - Usa el **Protocolo de Internet (IP)** como base para la comunicación global.
        

---

## 🔢 Versiones del Protocolo IP

|Versión|Descripción|Características|
|---|---|---|
|**IPv4**|Base actual de Internet|Direcciones de 32 bits, formato decimal (ej. `192.168.1.1`)|
|**IPv6**|Versión más reciente|Direcciones de 128 bits, formato hexadecimal (ej. `2001:0db8::1`)|

> ⚙️ Ambos tienen encabezados distintos, pero comparten campos con funciones similares.

---

## 📦 Campos principales del encabezado IPv4

|Campo|Significado|Analogía|
|---|---|---|
|**Versión**|Indica la versión de IP utilizada (4 o 6)|Tipo de correo (prioritario, regular, etc.)|
|**IHL (Internet Header Length)**|Longitud del encabezado IP|Tamaño del sobre|
|**ToS (Tipo de Servicio)**|Prioridad o tratamiento especial del paquete|Etiqueta “frágil” o “urgente”|
|**Longitud total**|Tamaño completo del paquete (encabezado + datos)|Peso y dimensiones del sobre|
|**Identificación**|Número único de cada paquete|Código de seguimiento postal|
|**Indicadores y Desfase de fragmentos**|Indican si el paquete fue fragmentado y cómo reensamblarlo|Envío dividido en partes por distintas rutas|
|**TTL (Time to Live)**|Tiempo máximo que puede circular un paquete antes de descartarse|Fecha límite de entrega del correo|
|**Protocolo**|Indica qué protocolo usa (TCP=6, UDP=17, etc.)|Número de casa o código de dirección|
|**Suma de comprobación**|Verifica errores en el encabezado|Sello que confirma que el sobre está intacto|
|**Dirección de origen**|IP del remitente|Dirección del remitente|
|**Dirección de destino**|IP del destinatario|Dirección del destinatario|
|**Opciones**|Campo opcional para diagnóstico o pruebas|Seguro o servicios adicionales del envío|
|**Datos**|Contenido del mensaje o información real|Carta dentro del sobre|

---

## 🧠 En resumen

- Los **encabezados IP** permiten identificar, guiar y validar los paquetes en su recorrido.
    
- Comprenderlos es clave para **analizar capturas de red (PCAP)** con precisión.
    
- Saber leer manualmente los encabezados te ayuda a:
    
    - Reconocer anomalías.
        
    - Identificar ataques o configuraciones erróneas.
        
    - Comprender la estructura del tráfico real.
        

---

