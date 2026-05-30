---
tipo: laboratorio
tags: [hwid, iex, irm, kms38, mas, microsoft-activation-scripts, powershell]
actualizado: 2026-05-28
---

# Microsoft Activation Scripts (MAS)

#PowerShell ⚡ #WindowsActivation 🖥️ #MicrosoftActivationScripts 🔑 #MAS #KMS38 #HWID #Windows #Office #SysAdmin 🛠️ #CyberSecurity 🔒 #SecurityAwareness ⚠️ #Scripting #InvokeRestMethod #InvokeExpression #EthicalHacking #Infosec #WindowsTips #TechSecurity 🚀

---

El comando `irm https://get.activated.win | iex` está diseñado para descargar y ejecutar un script de PowerShell que forma parte de los **Microsoft Activation Scripts (MAS)**, una herramienta de código abierto destinada a activar productos de Microsoft como Windows y Office.

[massgrave.dev](https://massgrave.dev/?utm_source=chatgpt.com)

**Propósito del comando:**

Este comando facilita la activación de sistemas operativos Windows y suites de Office sin necesidad de adquirir una licencia oficial de Microsoft. El script ofrece métodos de activación como HWID y KMS38.

Escribimos el siguiente comando en la **PowerShell** de Windows:

```powershell
irm https://get.activated.win | iex
```

hace lo siguiente en PowerShell:

1. **`irm` (Invoke-RestMethod)**: Descarga el contenido de la URL proporcionada.
2. **`iex` (Invoke-Expression)**: Ejecuta el contenido descargado como código en PowerShell.

### ⚠️ **Precaución** ⚠️

Este comando ejecuta código remoto sin mostrarlo primero, lo cual **puede ser extremadamente peligroso**. Es una técnica comúnmente utilizada para instalar software o ejecutar scripts maliciosos sin que el usuario lo note.

### 🚀 **Recomendaciones de seguridad**

Si deseas verificar qué hace este script antes de ejecutarlo, puedes hacer lo siguiente:

```powershell
irm https://get.activated.win
```

Esto solo mostrará el contenido del script sin ejecutarlo.

Si necesitas analizarlo más a fondo, puedes guardarlo en un archivo y revisarlo con un editor de texto o un entorno seguro:

```powershell
irm https://get.activated.win > script.ps1
notepad script.ps1
```

Si el script es malicioso, **no lo ejecutes** en tu máquina principal. Usa una máquina virtual o un entorno aislado para pruebas.

---

## Navegación

- ⬆️ Sección: [[_Windows|01 → Windows]]

## Relacionadas

- [[12- Windows Hosts]] — admin remoto Windows.
- [[../3- Guía de Instalación Office Lite 2016/Guía de Instalación Office Lite 2016|Office Lite]] — instalación que requiere activación.
- [[../../../02-Ciberseguridad/3- hacking basico/3- hosts/12- Windows Hosts|02 → Windows Hosts]] — WinRM/WMI con `irm`/`iex` también.
- [[../../../02-Ciberseguridad/3- hacking basico/4- privilege scalation/2- python hijacking|Python hijacking]] — patrón análogo: ejecutar código remoto sin verificar.