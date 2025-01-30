Uso del comando ADB para desinstalar aplicaciones del sistema sin necesidad de root:

---

## **Desinstalar aplicaciones del sistema sin root con ADB**

### **Pasos para usar ADB sin root**

---

### **1. Configura tu teléfono**

1. **Activa las Opciones de desarrollador:**
    - Ve a **Ajustes > Acerca del teléfono**.
    - Toca varias veces en **Número de compilación** hasta que se activen las Opciones de desarrollador.
2. **Activa Depuración USB:**
    - Ve a **Opciones de desarrollador > Depuración USB** y actívala.

---

### **2. Descarga e instala ADB**

1. **Descarga ADB**:
    - Descarga las **Android Platform Tools** desde [Google](https://developer.android.com/studio/releases/platform-tools).
2. **Instalación**:
    - Extrae los archivos descargados.
    - Abre una terminal o ventana de comandos en la carpeta donde están los ejecutables de ADB.

---

### **3. Conecta tu teléfono al PC**

- Conecta tu dispositivo al PC mediante un cable USB.
- En tu teléfono, acepta la solicitud de **depuración USB** cuando aparezca.

---

### **4. Identifica las aplicaciones a desinstalar**

1. **Verifica la conexión con ADB**:
    
    - Escribe el siguiente comando en la terminal:
        
        ```
        adb devices
        ```
        
    - Esto asegura que el dispositivo está conectado correctamente.
2. **Lista todas las aplicaciones instaladas**:
    
    - Ejecuta:
        
        ```
        adb shell pm list packages
        ```
        
    - Busca el **nombre del paquete** de la aplicación que deseas desinstalar. Ejemplo: 
        
        ```
        com.facebook.katana
        ```
        
        (para la aplicación de Facebook).
        
    - También podemos instalar en nuestro dispositivo android 'package manager' para verificar el nombre del paquete a desinstalar.

---

### **5. Comando para desinstalar la app**

- Para desinstalar una aplicación para el usuario actual (sin eliminarla permanentemente del sistema), usa:
    
    ```
    adb shell pm uninstall -k --user 0 [nombre.del.paquete]
    ```
    
    **Ejemplo**:
    
    ```
    adb shell pm uninstall -k --user 0 com.facebook.katana
    ```
    

---

### **6. (Opcional) Para reinstalar una app eliminada**

- Si necesitas restaurar la aplicación desinstalada, ejecuta:
    
    ```
    adb shell cmd package install-existing [nombre.del.paquete]
    ```
    

---

### **Notas finales**

- Este método es **seguro** y no requiere permisos de root.
- Asegúrate de identificar correctamente el nombre del paquete antes de ejecutar cualquier comando para evitar errores.

---