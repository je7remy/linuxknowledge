
---

### 🧪 **Pasos del laboratorio**

#### ✅ **Tarea 1: Verificar que APT esté instalado**

1. Abrir la terminal Bash.
    
2. Ejecutar el comando:
    
    ```bash
    apt
    ```
    
3. Verificar que muestre información sobre el uso de APT.
    

---

#### ✅ **Tarea 2: Instalar y desinstalar Suricata**

1. Instalar Suricata:
    
    ```bash
    sudo apt install suricata
    ```
    
    - Presionar `Intro` cuando se solicite confirmación.
        
2. Verificar instalación:
    
    ```bash
    suricata
    ```
    
3. Desinstalar Suricata:
    
    ```bash
    sudo apt remove suricata
    ```
    
    - Presionar `Intro` cuando se solicite confirmación.
        
4. Verificar desinstalación:
    
    ```bash
    suricata
    ```
    
    - Esperar mensaje de error `No such file or directory`.
        

---

#### ✅ **Tarea 3: Instalar tcpdump**

1. Instalar tcpdump:
    
    ```bash
    sudo apt install tcpdump
    ```
    

---

#### ✅ **Tarea 4: Ver lista de aplicaciones instaladas**

1. Ejecutar:
    
    ```bash
    apt list --installed
    ```
    
2. Buscar `tcpdump` en la lista para confirmar su instalación.
    

---

#### ✅ **Tarea 5: Reinstalar Suricata y verificar**

1. Reinstalar Suricata:
    
    ```bash
    sudo apt install suricata
    ```
    
2. Verificar que Suricata y tcpdump estén instalados:
    
    ```bash
    apt list --installed
    ```
    
    - Confirmar que ambas aplicaciones aparecen en la lista.
        

---

#### ✅ **Finalizar el lab**

1. Haz clic en **End Lab** y luego en **Submit**.
    
2. Cierra la pestaña del lab.
    
3. Actualiza la pestaña del curso para marcarlo como completo.
    

---
