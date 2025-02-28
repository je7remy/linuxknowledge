# Guía de Instalación Office Lite 2016 desde Repositorio de GitHub

## Requisitos Previos

- Tener instalado [Git](https://git-scm.com/).
- Conexión a Internet.
- Ejecutar el CMD como **Administrador**.
- Haber desinstalado cualquier versión anterior de Office (si aplica).
## Pasos para la Instalación

1. **Clonar el Repositorio**  
   Abre una terminal (CMD o PowerShell) con privilegios de administrador y ejecuta el siguiente comando:
   ```bash
   git clone https://github.com/je7remy/Instalacion-de-Office-Lite.git
```

1. **Acceder al Directorio del Repositorio**  
    Una vez clonado, cambia al directorio del repositorio:
    
    ```bash
    cd Instalacion-de-Office-Lite
    ```
    
3. **Seleccionar la Carpeta Adecuada Según la Arquitectura de tu Sistema**
    
    - **Para sistemas 64 bits:** Ingresa a la carpeta `Setup x64`.
    - **Para sistemas 32 bits:** Ingresa a la carpeta `Setup x86 (32Bits)`.
4. **Ejecutar los Instaladores**  
    Dentro de la carpeta correspondiente encontrarás los siguientes instaladores:
    
    - **Access:** `[Access]Setup64.exe` o `[Access]Setup32.exe`
    - **Excel:** `[Excel]Setup64.exe` o `[Excel]Setup32.exe`
    - **PowerPoint:** `[PowerPoint]Setup64.exe` o `[PowerPoint]Setup32.exe`
    - **Word:** `[Word]Setup64.exe` o `[Word]Setup32.exe`
    
    Ejecuta cada instalador según las aplicaciones que necesites, asegurándote de hacerlo como **Administrador**.
    
5. **Solución de Errores Comunes**  
    Si surge algún error durante la instalación, consulta el archivo `SOLUCIÓN ERRORES.txt` presente en la carpeta correspondiente para obtener instrucciones detalladas.
    
6. **Configurar Office 2016 Mediante CMD**  
    Después de instalar las aplicaciones, ejecuta los comandos contenidos en el archivo `LÍNEAS CMD x64 x86 OFFICE 2016.txt`:
    
    - Abre una terminal CMD como **Administrador**.
    - Copia y pega los comandos en el orden indicado en el archivo.
7. **Reiniciar el Sistema**  
    Una vez completado el proceso, reinicia tu PC para que todos los cambios se apliquen correctamente.
    

## Notas Adicionales

- Sigue el orden de los pasos para evitar problemas durante la instalación.
- Asegúrate de cerrar cualquier sesión activa en Office antes de comenzar el proceso.
- Esta guía está pensada para una instalación "lite" de Office 2016, optimizada para configuraciones básicas.

---

> **Advertencia:** Utiliza este método de instalación de forma responsable y asegúrate de cumplir con las normativas de licencia de Microsoft.