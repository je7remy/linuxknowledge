---
tipo: teoria
tags: [nota]
actualizado: 2026-05-28
---

# Configuración Básica de Máquina Virtual Parrot Os

## **Tutorial: Instalar Parrot OS en VMware ESXi (tipo 1)**

### **Requisitos previos**

1. **Servidor físico o PC compatible**:
    
    - CPU con **VT-x / AMD-V** habilitado en BIOS.
        
    - 4 GB de RAM mínimo (8 GB recomendado).
        
    - 20 GB de almacenamiento libre mínimo.
        
2. **Descargar ESXi 8.0U3** (gratuito):
    
    - [Descarga ESXi gratis](https://www.vmware.com/products/esxi-and-esx.html)
        
3. **Crear cuenta VMware** (necesaria para descargar ESXi).
    
4. **Descargar Parrot OS ISO**:
    
    - [Parrot OS Home Edition](https://www.parrotsec.org/download/)
        
    - Recomendado: versión **Security / Home / XFCE** según tu gusto.
        
5. **Cliente vSphere** o navegador para acceder a **ESXi Web UI**.
    

---

### **Paso 1: Instalar ESXi en el servidor físico**

1. **Grabar ESXi ISO en un USB** (Rufus / balenaEtcher).
    
2. Conectar USB al servidor y bootear desde él.
    
3. Seguir los pasos de instalación:
    
    - Aceptar **EULA**.
        
    - Seleccionar **disco de instalación** (el servidor se formateará).
        
    - Configurar **contraseña de root**.
        
4. Reiniciar el servidor cuando termine.
    

✅ Ahora tienes **ESXi corriendo** y listo para acceder vía web.

---

### **Paso 2: Acceder al ESXi Web Client**

1. Desde otro PC en la misma red, abre un navegador y escribe:
    
    ```
    https://IP_DEL_SERVIDOR_ESXI
    ```
    
2. Inicia sesión con usuario `root` y la contraseña que configuraste.
    
3. Verás la **interfaz de administración web de ESXi**.
    

---

### **Paso 3: Crear una máquina virtual para Parrot OS**

1. En la Web UI, haz clic en **“Máquinas Virtuales” → “Crear / Registrar VM”**.
    
2. Selecciona **“Crear nueva máquina virtual”**.
    
3. Configura:
    
    - **Nombre:** ParrotOS
        
    - **Compatibilidad:** ESXi 8.0 y superior
        
    - **Guest OS:** Linux → Debian 11 o 12 (Parrot OS está basado en Debian)
        
4. **CPU y RAM**:
    
    - CPU: 2 núcleos mínimo
        
    - RAM: 2-4 GB mínimo (recomendado 4 GB)
        
5. **Disco duro**:
    
    - Tipo: Thin Provision
        
    - Tamaño: 20 GB mínimo
        
6. **Conexión de red**: VM Network (NAT o Bridge según tu red)
    

---

### **Paso 4: Subir ISO de Parrot OS**

1. En la máquina virtual recién creada, ve a **Editar configuración → CD/DVD Drive → Datastore ISO file**.
    
2. **Sube el ISO** de Parrot OS al datastore de ESXi.
    
3. Marcar **Conectar al arrancar**.
    

---

### **Paso 5: Instalar Parrot OS**

1. En la Web UI, selecciona la VM y haz clic en **“Consola → Abrir consola”**.
    
2. Arranca la VM y selecciona **Instalación gráfica de Parrot OS**.
    
3. Sigue los pasos típicos de Debian:
    
    - Selecciona idioma y zona horaria.
        
    - Configura teclado.
        
    - Particiona disco (usar disco completo de la VM está bien).
        
    - Crear usuario y contraseña.
        
    - Instala GRUB en el disco virtual.
        
4. Espera que termine la instalación y reinicia la VM.
    

---

### **Paso 6: Configurar la VM después de instalar**

1. Quita el ISO de Parrot OS (para no bootear de nuevo desde el ISO).
    
2. Configura resolución de pantalla y red en Parrot OS.
    
3. Instala herramientas adicionales si quieres:
    
    ```bash
    sudo apt update && sudo apt upgrade -y
    sudo apt install open-vm-tools-desktop -y
    ```
    
    Esto ayuda con la integración de ESXi (resolución, mouse, etc.).
    

---

### **Paso 7: Comprobar que funciona**

1. La VM debe arrancar correctamente en Parrot OS.
    
2. Puedes usarla para pruebas de seguridad, desarrollo o hacking ético.
    
3. Opcional: Habilitar **Snapshots** en ESXi (si tienes versión con licencia o pruebas locales).
    

---

💡 **Tips adicionales**

- Si vas a usar muchas herramientas de seguridad, asigna **más RAM** y **más CPU**.
    
- Para laboratorios de ciberseguridad, considera **clonar la VM** para no tener que reinstalar.
    
- Siempre **mantén actualizado Parrot OS** con `sudo parrot-upgrade`.
    

---

---

## Navegación

- ⬆️ Carpeta: [[_0- Configuracion inicial|0- Configuracion inicial]]
- ⬅️ Anterior: [[1- Configuración Básica de Máquina Virtual Kali Linux]]
