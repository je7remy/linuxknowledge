---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Monitoreo de la Seguridad con herramientas de Detección

## 🧠 **Fundamentos de la Detección y Monitoreo de la Seguridad**

---

### 📄 **Contenido introductorio**

La detección requiere datos, y estos pueden provenir de diversas fuentes. Los **dispositivos de red y sistemas** generan registros que capturan eventos específicos, mientras que las **tecnologías de detección** monitorean la actividad y recopilan **telemetría**, es decir, la recolección y transmisión de datos para su análisis.

Mientras los **registros** documentan los eventos que ocurren en los sistemas, la **telemetría** describe los datos en sí. Por ejemplo, las **capturas de paquetes** se consideran telemetría de red.  
Para los profesionales de la ciberseguridad, **registros y telemetría** son fuentes esenciales de evidencia, utilizadas para responder preguntas durante investigaciones y detectar anomalías.

---

### 🔍 **Sistemas de Detección de Intrusiones (IDS)**

Un **IDS (Intrusion Detection System)** es una aplicación que supervisa la actividad de un sistema o red y alerta sobre posibles intrusiones.  
Estos sistemas pueden centrarse en distintas partes de la infraestructura, como los **puntos finales (endpoints)** —dispositivos conectados a la red tales como laptops, servidores o smartphones—, los cuales son **objetivos frecuentes de atacantes** que buscan acceso no autorizado.

---

### 💻 **IDS basados en Host (HIDS)**

Un **HIDS** se instala directamente en un dispositivo o servidor individual.  
Actúa como un **agente local** que monitorea los procesos, archivos, registros y actividades del host donde está instalado.  
Cuando detecta comportamientos sospechosos, **genera un registro y una alerta**.  
Por ejemplo, puede registrar intentos reiterados de acceso fallidos o modificaciones inusuales de archivos del sistema.

---

### 🌐 **IDS basados en Red (NIDS)**

En cambio, un **NIDS** recopila y analiza el **tráfico y los datos de red**.  
Funciona de manera similar a un **sniffer de paquetes**, evaluando el tráfico que fluye por puntos estratégicos de la red.  
Suele implementarse en varios lugares para lograr una **mayor visibilidad y cobertura**, identificando patrones anómalos en la comunicación entre hosts o con Internet.  
Cuando se detecta una actividad inusual, el sistema **registra el evento y genera una alerta** para su análisis posterior.

---

### ⚙️ **Métodos de Detección: Análisis de Firmas**

Uno de los métodos más comunes utilizados por los IDS es el **Análisis de Firmas**, que consiste en comparar la actividad observada con **reglas o patrones predefinidos**.  
Por ejemplo, una firma puede especificar que si se producen **tres intentos de inicio de sesión fallidos consecutivos**, se dispare una alerta, indicando un posible **ataque de fuerza bruta**.

Estas firmas permiten automatizar la detección de comportamientos conocidos y repetitivos, agilizando la respuesta ante amenazas.

---

### 🧩 **Registros IDS y Centralización**

Las tecnologías IDS registran toda la información observada en forma de **registros IDS**, que pueden incluir datos sobre dispositivos, sistemas y tráfico de red.  
Estos registros suelen enviarse a un **repositorio centralizado o SIEM (Security Information and Event Management)**, donde son almacenados, correlacionados y analizados junto con otros eventos del entorno.

---

### 📘 **Conclusión**

Este contenido introduce los fundamentos del monitoreo de la seguridad mediante **tecnologías de detección**.  
Permite comprender cómo los sistemas IDS, tanto en red como en host, **recolectan, analizan y correlacionan datos** para detectar comportamientos sospechosos y reforzar la defensa ante incidentes.  
El siguiente paso es explorar cómo **configurar y leer firmas IDS**, profundizando en la **automatización de alertas y respuesta ante amenazas**.

---

### 🧩 Pregunta

A la hora de monitorizar la actividad, ¿qué especifica las reglas que utiliza un Sistema de detección de intrusiones (IDS)?

- [ ] Una alerta  
- [x] Una Firma  
- [ ] Un punto de conexión  
- [ ] Un registro  

---

### ✅ Respuesta correcta
**Una Firma**

---

### 💡 Explicación
Una **firma** define las **reglas y patrones** que un **IDS (Sistema de Detección de Intrusiones)** utiliza para monitorear la actividad y detectar comportamientos sospechosos.  
El **análisis de firmas** es uno de los métodos de detección más comunes, ya que permite identificar ataques conocidos mediante la comparación de eventos con reglas predefinidas.

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ➡️ Siguiente: [[2- Herramientas y técnicas de Detección]]
