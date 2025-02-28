# 🚀 Guía de Instalación Office Lite 2016 desde Repositorio de GitHub

---

## 📋 Requisitos Previos

- ✅ Tener instalado **[Git](https://git-scm.com/)**  
- ✅ Conexión a Internet estable  
- ✅ Ejecutar **CMD/PowerShell/Git Bash como Administrador**  
- 🗑️ Desinstalar versiones anteriores de Office (*si aplica*)  
- ⏳ 15-20 minutos disponibles para el proceso

---

## 🛠️ Pasos para la Instalación

### 1. Clonar el Repositorio

git clone https://github.com/je7remy/Instalacion-de-Office-Lite.git

> **Tip:** Asegúrate de ejecutar esto en CMD/PowerShell **como Administrador**.

---

### 2. Acceder al Directorio del Repositorio

cd Instalacion-de-Office-Lite


---

### 3. Seleccionar la Carpeta Según tu Sistema

| Arquitectura | Carpeta Destino |
|--------------|-----------------|
| **64 bits**  | `Setup x64`     |
| **32 bits**  | `Setup x86 (32Bits)` |

> 🔍 ¿No sabes tu arquitectura?  
> Presiona `Win + Pausa` → Mira *"Tipo de sistema"* en *Información del sistema*.

> 🔍 **¿No tienes tecla Pausa?** 
> Usa estos métodos alternativos para ver tu arquitectura:

📌 **Método 1 - Ejecutar:**  
1. Presiona `Win + R`  
2. Escribe `msinfo32` → Enter  
3. Busca *"Tipo de sistema"* en la ventana  

📌 **Método 2 - Propiedades del Sistema:**  
1. Haz clic derecho en **Este equipo**/**Mi PC**  
2. Selecciona **Propiedades**  
3. Mira en *"Tipo de sistema"* (sección *Especificaciones*)

📌 **Método 3 - Menú de Inicio:**  
1. Escribe *"Información del sistema"* en la búsqueda  
2. Abre la aplicación  
3. Verifica *"Tipo de sistema"* en los detalles  

### 4. Ejecutar los Instaladores

Dentro de la carpeta seleccionada:
- **📁 Aplicaciones Disponibles:**
  - 🗃️ Access: `[Access]SetupXX.exe`
  - 📊 Excel: `[Excel]SetupXX.exe`
  - � PowerPoint: `[PowerPoint]SetupXX.exe`
  - 📝 Word: `[Word]SetupXX.exe`

🔹 **Recomendación:**  
   Ejecuta cada instalador haciendo *clic derecho → Ejecutar como administrador*.

---

### 5. Solución de Errores (Opcional)

Si encuentras problemas:
1. Abre `SOLUCIÓN ERRORES.txt`
2. Sigue las instrucciones paso a paso

---

### 6. Configurar Office 2016 via CMD

Ejecuta los comandos del archivo:  
`LÍNEAS CMD x64 x86 OFFICE 2016.txt`

```bash
# Ejemplo de comandos (no ejecutar directamente)
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\16.0\Common\Licensing" /v "SkipLicenseCheck" /t REG_DWORD /d 1 /f
```

---

### 7. Reiniciar el Sistema

```bash
shutdown /r /t 0
```
> **⚠️ Importante:** Guarda todos tus trabajos antes de reiniciar.

---

## 📌 Notas Adicionales

- 🔄 **Orden de instalación:** Respetar los pasos 1 al 7 secuencialmente.
- 🚫 Cierra todas las ventanas de Office antes de comenzar.
- 🌐 Versión "Lite" incluye solo componentes esenciales (sin Outlook/Publisher).

---

## ⚠️ Advertencia Legal

```diff
- ¡ATENCIÓN!  
+ Este método es solo para fines educativos.  
+ Verifica que posees una licencia válida de Microsoft Office 2016.  
- El autor no se responsabiliza por mal uso del software.
```

---

<center>✨ **Instalación Completa** ✨</center>

