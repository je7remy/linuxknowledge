---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos -  Inspección de paquetes

### ## Pregunta 1

**¿Qué opción de `tcpdump` se utiliza para especificar la interfaz de red?**

- -n
    
- ✅ **-i**
    
- -c
    
- -v
    

**Explicación:** La opción `-i` significa **interfaz** (_interface_) y se usa para decirle a `tcpdump` en qué tarjeta de red (ej. `eth0`, `en0`) debe escuchar.

---

### ## Pregunta 2

**¿Qué se necesita para acceder al analizador de protocolos de red `tcpdump`?**

- Salida
    
- ✅ **Interfaz de línea de comandos**
    
- Captura de paquetes
    
- Interfaz gráfica de usuario
    

**Explicación:** `tcpdump` es una herramienta clásica que se opera exclusivamente a través de una **terminal o línea de comandos** ⌨️, no tiene una interfaz gráfica.

---

### ## Pregunta 3

**¿Cuál es el primer campo que se encuentra en la salida de un comando `tcpdump`?**

- ✅ **Marca de tiempo**
    
- Protocolo
    
- Versión
    
- IP de origen
    

**Explicación:** Cada línea de una captura de `tcpdump` comienza con la **marca de tiempo** 🕒 (_timestamp_) que indica el momento exacto en que se capturó el paquete.

---

### ## Pregunta 4

**Está utilizando `tcpdump` para capturar el tráfico de red en su computadora local. Le gustaría guardar el tráfico de red en un archivo de captura de paquetes para su posterior análisis. ¿Qué opción de `tcpdump` debería utilizar?**

- -r
    
- -v
    
- -c
    
- ✅ **-w**
    

**Explicación:** La opción `-w` significa **escribir** (_write_) y se usa para guardar los paquetes capturados en un archivo `.pcap`. La opción `-r` se usaría después para **leer** (_read_) ese archivo.

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[5- Ejemplar - Capture su primer Paquete]]
