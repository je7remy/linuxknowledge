---
tipo: laboratorio
tags: [bypass, ciberseguridad, fodhelper, living-off-the-land, privilege-escalation, runasinvoker, uac, windows]
actualizado: 2026-05-28
---

# BYPASS del UAC de Windows
---

**Bypass del UAC (User Account Control) de Windows**  
Es una técnica utilizada para **evadir el mecanismo de seguridad del UAC** (que solicita confirmación o credenciales de administrador ante cambios críticos en el sistema), permitiendo la **ejecución de procesos con privilegios elevados sin desencadenar la ventana de confirmación estándar**. Esto se logra explotando:  
- **Ejecutables de confianza del sistema** (como `fodhelper.exe`, `msconfig.exe`).  
- **Claves de registro mal configuradas**.  
- **Interfaces COM (Component Object Model)** con permisos laxos.  

**Contexto**:  
- Es útil en **pentesting** para escalar privilegios en entornos controlados.  
- No es una vulnerabilidad *per se*, sino un abuso de mecanismos legítimos del sistema (**Living-off-the-Land**).  

**Ejemplo**:  
El método `fodhelper.exe` (registrado en el registro de Windows) puede ser manipulado para ejecutar código malicioso como administrador sin alertar al UAC.  

⚠️ **Importante**: Su uso no autorizado es malicioso; siempre debe emplearse éticamente y con consentimiento explícito.  

---

## **Bypass del UAC en Windows para ejecutar programas sin permisos elevados**

El **Control de Cuentas de Usuario (UAC)** en Windows es un sistema de seguridad que evita que aplicaciones no autorizadas realicen cambios en el sistema sin el consentimiento del usuario. Sin embargo, en algunas situaciones, puede ser útil ejecutar un programa sin que se active el UAC, especialmente cuando no tenemos acceso a una cuenta de administrador.

A continuación, te explico **cómo ejecutar un programa sin privilegios elevados** sin que Windows solicite permisos de administrador.

---

### **🚀 Pasos para ejecutar un programa sin activar el UAC**

### 🔹 **Paso 1: Abrir CMD en la ubicación del programa**

1. Abre el **Explorador de archivos** (`Win + E`).
2. Navega hasta la carpeta donde se encuentra el ejecutable del programa.
3. En la barra de direcciones del Explorador de archivos, escribe `cmd.exe` y presiona **Enter**.  
    🔹 Esto abrirá una ventana de **Símbolo del sistema (CMD)** directamente en esa carpeta.

---

### 🔹 **Paso 2: Configurar el modo de ejecución**

Dentro de la ventana de CMD, escribe el siguiente comando y presiona **Enter**:

```
set __compat_layer=runasinvoker
```

📌 **Explicación:**  
Este comando configura una variable especial que le indica a Windows que ejecute la aplicación en un modo de compatibilidad que evita la solicitud de permisos administrativos.

---

### 🔹 **Paso 3: Ejecutar el programa**

Ahora, escribe el siguiente comando reemplazando `<nombre-del-ejecutable>` por el nombre del archivo `.exe` que deseas ejecutar:

```
start <nombre-del-ejecutable>
```

📌 **Ejemplo práctico:**  
Si queremos ejecutar un programa llamado `setup.exe`, escribimos:

```
start setup.exe
```

Esto iniciará el programa sin que Windows solicite permisos de administrador.

---

### **📌 Consideraciones Importantes**

4. **Sin permisos elevados:**
    
    - La aplicación se ejecutará con permisos de usuario normal.
    - No podrá hacer cambios en directorios protegidos como `C:\Program Files` o `C:\Windows`.
5. **Solución si la instalación falla por permisos:**
    
    - Durante la instalación, **elige una carpeta diferente** para instalar el programa, como:
        - `C:\Users\TuUsuario\Desktop\` (Escritorio)
        - `C:\Users\TuUsuario\AppData\Local\`
        - O cualquier otra carpeta dentro de tu perfil de usuario.
6. **Algunas aplicaciones pueden no ejecutarse correctamente:**
    
    - Si el programa requiere permisos de administrador para modificar configuraciones del sistema, el bypass no servirá.
    - Solo funcionará en aplicaciones que puedan ejecutarse sin privilegios elevados.

---

### **🌟 Conclusión**

Este método es útil para ejecutar programas sin activar el **Control de Cuentas de Usuario (UAC)**, especialmente cuando estamos en un entorno donde no tenemos privilegios administrativos. Sin embargo, siempre hay que considerar las limitaciones de no ejecutar el programa con permisos elevados.

---

## Navegación

- ⬆️ Sección: [[_Windows|01 → Windows]]

## Relacionadas

- [[_4- privilege scalation|02 → Escalación de privilegios]] — UAC bypass es vector clásico de privesc en Windows.
- [[../../../02-Ciberseguridad/3- hacking basico/3- hosts/12- Windows Hosts|02 → Windows Hosts]] — combinación con WinRM/WMI.
- [[../7- Activie Directory/2- Tools|AD → Tools]] — herramientas relacionadas (Mimikatz, evil-winrm).
