---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Ejemplo, Instalar software en una distribución Linux

## 🧪 Ejemplo: Instalar software en una distribución Linux

### 🔐 Rol: Analista de seguridad

Necesitas instalar, desinstalar y reinstalar las aplicaciones **Suricata** y **tcpdump** para tareas de **seguridad de red**, utilizando el administrador de paquetes **APT** en un sistema Debian Linux.

---

### ✅ Tarea 1: Verificar que APT está instalado

1. Abre la terminal Bash.
    
2. Escribe el siguiente comando y presiona `Enter`:
    
    ```bash
    apt
    ```
    
3. Verifica que aparezca información sobre APT (versión y descripción de uso).
    
    - Si ves algo como `apt 1.8.2.3 (amd64)`, significa que APT está instalado correctamente.
        

---

### ✅ Tarea 2: Instalar y desinstalar Suricata

#### a) Instalar Suricata

1. Ejecuta:
    
    ```bash
    sudo apt install suricata
    ```
    
2. Presiona `Enter` para confirmar (respuesta predeterminada: **Yes**).
    
3. Verifica la instalación ejecutando:
    
    ```bash
    suricata
    ```
    
    - Si está bien instalado, verás algo como:
        
        ```
        Suricata 4.1.2
        USAGE: suricata [OPTIONS] [BPF FILTER]
        ```
        

#### b) Desinstalar Suricata

1. Ejecuta:
    
    ```bash
    sudo apt remove suricata
    ```
    
2. Presiona `Enter` para confirmar.
    
3. Verifica que fue desinstalado ejecutando:
    
    ```bash
    suricata
    ```
    
    - Deberías ver:
        
        ```
        -bash: /usr/bin/suricata: No such file or directory
        ```
        

---

### ✅ Tarea 3: Instalar tcpdump

1. Ejecuta:
    
    ```bash
    sudo apt install tcpdump
    ```
    

---

### ✅ Tarea 4: Verificar aplicaciones instaladas

1. Genera una lista de aplicaciones instaladas con:
    
    ```bash
    apt list --installed
    ```
    
2. Busca en la lista que aparezca:
    
    ```
    tcpdump/oldstable,now ... [installed]
    ```
    
    - Suricata **no aparecerá aún** porque fue desinstalada.
        

---

### ✅ Tarea 5: Reinstalar Suricata y confirmar

1. Reinstala Suricata con:
    
    ```bash
    sudo apt install suricata
    ```
    
2. Verifica nuevamente con:
    
    ```bash
    apt list --installed
    ```
    
3. Asegúrate de que ambas aplicaciones estén en la lista:
    
    ```
    suricata/... [installed]
    tcpdump/... [installed]
    ```
    

---

### ✅ Finaliza el lab

1. Haz clic en **End Lab**.
    
2. Luego, haz clic en **Submit**.
    
3. Cierra la pestaña del lab.
    
4. Vuelve al curso y actualiza la página para marcar el laboratorio como completado.
    

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[9- Laboratorio Practico]]
- ➡️ Siguiente: [[11- Cuestionario, Instalación de software en Linux]]
