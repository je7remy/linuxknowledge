---

#Ventoy #BootableUSB #OSInstallation #Windows #Linux #Cybersecurity #Tech #ITSupport #ISO #OperatingSystems #EthicalHacking #KaliLinux

---
## 🛠 **Requisitos Previos**

- Una memoria USB de al menos **8 GB** (recomendado 16 GB o más).
- Un equipo con **acceso a la BIOS/UEFI**.
- **ISOs de los sistemas operativos** que deseas instalar.
- **Ventoy**, que puedes descargar desde su [sitio oficial](https://www.ventoy.net/).

---

## 🚀 **Paso 1: Descargar e Instalar Ventoy en la USB**

1. Descarga **Ventoy** desde su [página oficial](https://www.ventoy.net/).
2. Extrae el archivo descargado en tu PC.
3. Conecta la **USB** en tu computadora.
4. Ejecuta **Ventoy2Disk.exe** (en Windows) o usa la terminal en Linux:
    
    ```bash
    sudo sh Ventoy2Disk.sh -i /dev/sdX
    ```
    
    (Reemplaza `/dev/sdX` por la unidad de tu USB).
5. Presiona **"Instalar"** y confirma la instalación. Esto formateará la USB.

---

## 📂 **Paso 2: Copiar las ISOs a la USB**

1. Una vez instalado Ventoy, **NO es necesario bootear la USB** con herramientas externas.
2. Simplemente **copia y pega** los archivos **ISO** de los sistemas operativos en la memoria USB.
    - Puedes copiar **varias ISOs** (Windows, Linux, etc.).
    - Se recomienda organizarlas en carpetas si tienes muchas.

---

## ⚙ **Paso 3: Configurar BIOS/UEFI para Bootear con Ventoy**

1. Reinicia tu computadora y entra en la **BIOS/UEFI** (normalmente con `F2`, `F12`, `DEL` o `ESC`).
2. Busca la opción de **"Boot Order"** o **"Boot Priority"** y selecciona la **USB** como primera opción.
3. Guarda los cambios y **reinicia**.

---

## 🎛 **Paso 4: Seleccionar e Instalar el Sistema Operativo**

1. Al iniciar desde la USB, aparecerá el menú de **Ventoy**.
2. Selecciona la **ISO** del sistema operativo que deseas instalar.
3. Sigue las instrucciones del instalador del sistema elegido.

---

## 🔧 **Extras y Opciones Avanzadas**

- **Persistence Mode**: Permite guardar cambios en sistemas Live USB.
- **Compatibilidad con Secure Boot**: Habilítalo en la configuración de Ventoy.
- **Personalización**: Puedes agregar temas y configuraciones en `ventoy.json`.

---

## 📝 **Conclusión**

Con Ventoy, puedes instalar múltiples sistemas operativos sin necesidad de volver a formatear la USB cada vez. Es una herramienta ideal para técnicos, entusiastas de la informática y quienes trabajan con sistemas operativos constantemente.

---

---

## Navegación

- ⬆️ Carpeta: [[_2- Instalacion de Sistemas Operativos con Ventoy|2- Instalacion de Sistemas Operativos con Ventoy]]
- ➡️ Siguiente: [[2- Saltar conexión Wi-Fi Windows]]
