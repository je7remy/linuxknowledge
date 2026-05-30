---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Componentes de una firma de Detección

## 🧩 **Lectura de Firmas en Sistemas de Detección de Intrusiones (IDS)**

---

### 🧠 **Introducción**

Como **analista de seguridad**, una de tus funciones puede ser **escribir, personalizar o probar firmas**.  
Las firmas son **reglas de detección** que describen los tipos de intrusiones en la red que deseas que un IDS (Intrusion Detection System) identifique.

Por ejemplo, una firma puede configurarse para detectar y alertar sobre **tráfico sospechoso** que intenta conectarse a un puerto específico.

---

### 🌐 **NIDS (Network Intrusion Detection System)**

El término **Sistema de Detección de Intrusiones en la Red** se abrevia como **NIDS**.  
Las **reglas NIDS** generalmente se componen de **tres elementos principales**:

1. **Acción**  
2. **Encabezado (Header)**  
3. **Opciones de la regla**

---

### ⚙️ **1. Acción**

La **acción** es el primer elemento de una firma.  
Determina **qué hará el sistema** cuando se cumplan los criterios de detección.

Acciones comunes incluyen:
- `alert` → genera una alerta ante tráfico sospechoso.  
- `pass` → ignora o deja pasar el tráfico.  
- `reject` → bloquea la conexión.

📘 *Ejemplo:*  
Si una firma especifica “alertar” sobre tráfico que establece una conexión inusual, el IDS inspeccionará los paquetes y enviará una **alerta** al detectar coincidencias.

---

### 🧾 **2. Encabezado**

El **encabezado** define el **tráfico de red** al que aplica la regla.  
Incluye información como:
- **Dirección IP de origen y destino**  
- **Puertos de origen y destino**  
- **Protocolo (TCP, UDP, ICMP)**  
- **Dirección del tráfico**

📘 *Ejemplo básico de encabezado:*


Explicación:
- `msg:` → texto de alerta que aparecerá cuando se active la firma.  
- `sid:` → identificador único de la firma (*Signature ID*).  
- `rev:` → número de revisión; aumenta con cada actualización de la firma.

Estas opciones hacen que las reglas sean más específicas, por ejemplo, al buscar **ciertos contenidos** dentro de los paquetes de red o detectar **cargas útiles maliciosas (payloads)**.

---

### 🧨 **Cargas útiles maliciosas (Payloads)**

Las cargas útiles maliciosas se encuentran dentro de los **datos de un paquete** y pueden realizar acciones como:
- Borrar archivos  
- Encriptar información  
- Instalar malware  

Configurar correctamente las opciones de una regla permite **delimitar el tráfico sospechoso** y mejorar la precisión de la detección.

---

### 🧭 **Conclusión**

Ahora sabes cómo **leer y comprender una firma NIDS**, identificando sus tres componentes esenciales:

1. **Acción** → qué hace el IDS.  
2. **Encabezado** → define el tráfico.  
3. **Opciones** → personalizan la detección.  

Esta habilidad es fundamental para todo analista de seguridad, ya que permite crear reglas efectivas para **detectar intrusiones** y proteger las redes frente a amenazas.

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[3- Gracia - Mentalidad de seguridad en la detección y respuesta]]
- ➡️ Siguiente: [[5- Examinar firmas con Suricata]]
