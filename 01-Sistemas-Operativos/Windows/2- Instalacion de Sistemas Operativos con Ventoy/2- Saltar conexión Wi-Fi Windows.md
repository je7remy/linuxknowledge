
Para saltarte la conexión a una red Wi-Fi durante la configuración inicial de Windows 11, puedes seguir estos métodos:

### **Método 1: Usando el comando `OOBE\BYPASSNRO`**

1. En la pantalla que te pide conectarte a una red, presiona `Shift + F10` para abrir el símbolo del sistema.
2. Escribe el siguiente comando y presiona `Enter`:
    
    ```
    OOBE\BYPASSNRO
    ```
    
3. Tu PC se reiniciará y volverá al proceso de configuración, pero ahora aparecerá la opción **"No tengo Internet"**.
4. Haz clic en esa opción y luego selecciona **"Continuar con configuración limitada"**.

---

### **Método 2: Usando `Alt + F4`** (A veces funciona)

1. Cuando Windows 11 te pida conectarte a una red, intenta presionar `Alt + F4`.
2. En algunos casos, esto cierra la ventana y permite continuar con la configuración sin conexión.

---

### **Método 3: Deshabilitando la tarjeta Wi-Fi temporalmente**

1. Cuando llegues a la pantalla de conexión a Internet, presiona `Shift + F10` para abrir el símbolo del sistema.
2. Escribe este comando y presiona `Enter`:
    
    ```
    netsh wlan disconnect
    ```
    
3. Cierra la ventana del símbolo del sistema y revisa si ahora te deja continuar sin conexión.

---

Estos métodos funcionan en la mayoría de los casos. 