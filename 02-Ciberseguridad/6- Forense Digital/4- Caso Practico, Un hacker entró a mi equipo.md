
# Informe Forense Digital: Caso "¿Un Hacker entró a mi equipo?"  

---

## **Escenario del Incidente**  

Un usuario de una organización reportó comportamiento anómalo en su equipo, incluyendo la presencia de archivos PDF encriptados (`important_document.pdf`) y sospechas de robo de credenciales. El equipo DFIR (Respuesta a Incidentes y Forense Digital) capturó una imagen de la memoria RAM del equipo afectado para su análisis.  

**Equipo afectado**:  

- Dirección IP: `192.168.182.139`  

---

## **Objetivos del Análisis**  

1. Determinar la versión del sistema operativo y arquitectura.  
2. Identificar la dirección IP origen de una conexión RDP no autorizada.  
3. Detectar la dirección IP de destino de una conexión en el puerto 80.  
4. Identificar procesos sospechosos en ejecución.  
5. Determinar la URL sospechosa a la que accedió el proceso `updater.exe`.  
6. Recuperar la clave utilizada para cifrar el archivo `important_document.pdf`.  

---

#### **Herramientas Forenses Destacadas 

- **Kali Linux:** Distribución de Linux para pruebas de seguridad y análisis forense.
- **Autopsy:** Plataforma de código abierto para investigaciones forenses.
- **Caine:** Entorno Linux con herramientas forenses integradas.
- **FTK Imager:** Herramienta para crear imágenes forenses de discos y memoria.
- **Volatility:** Herramienta principal del webinar para el análisis de memoria RAM.
- **Normativas:** RFC 3227 e ISO/IEC 27037, que establecen directrices para la recolección y manejo de evidencia digital.

Estas herramientas y normativas resaltan las mejores prácticas de la industria, y *Volatility* se convierte en el foco principal del ejercicio práctico.

---

## **Herramientas Utilizadas**  

- **Volatility**: Para análisis forense de memoria RAM.  
- **WhatIsMyIPAddress**: Para geolocalización y detalles de direcciones IP.  
- **Inteligencia Artificial (Copilot)**: Para verificación de procesos legítimos vs. sospechosos.  

---
#### **Uso de Volatility en el Análisis Forense **

- **`windows.netscan`:** Muestra conexiones de red activas y cerradas.
- **`windows.pstree`:** Presenta una vista jerárquica de los procesos en la memoria.
- **`windows.filescan`:** Identifica archivos accedidos que оставan rastros en la RAM.
- **`windows.mftscan`:** Revela la última fecha de acceso o modificación de archivos.
- **`windows.memmap --dump --pid`:** Permite un análisis detallado de un proceso específico.

Estos comandos se aplican directamente al análisis del caso práctico, como se describe a continuación.

---

## **Metodología y Resultados**  

### **1. Determinar versión del sistema operativo y arquitectura** 

**Comando utilizado**:  
```bash  
vol.py -f mem.raw windows.info  
```  
**Resultados**:  
- **Sistema Operativo**: Windows 10 (64 bits).  
- **Kernel**: Versión 10.0.19041.  

---

### **2. Identificar conexión RDP sospechosa**  

**Comando utilizado**:  
```bash  
vol.py -f mem.raw windows.netscan  
```  
**Filtro aplicado**:  
```bash  
grep "ESTABLISHED" | grep ":3389"  
```  
**Resultados**:  
- **IP origen**: `192.168.182.150` (dentro de la red interna).  
- **Puerto destino**: `3389` (RDP).  
- **Conclusión**: Un equipo interno (`192.168.182.150`) estableció una conexión remota no autorizada al equipo afectado.  

---

### **3. Detectar conexión en puerto 80**  

**Filtro aplicado**:  
```bash  
grep "ESTABLISHED" | grep ":80"  
```  
**Resultados**:  
- **IP destino**: `192.168.182.128` (dentro de la red interna).  
- **Actividad**: El equipo afectado estableció una conexión HTTP a un servidor interno.  

---

### **4. Identificar procesos sospechosos**  

**Comando utilizado**:  
```bash  
vol.py -f mem.raw windows.pstree  
```  
**Análisis**:  
- **Proceso padre**: `critical_updater.exe` (PID: 1648).  
- **Proceso hijo**: `updater.exe` (PID: 1612).  
- **Ubicación**: Carpeta del usuario (`C:\Users\User01\Documents\`).  
- **Verificación con IA**:  
  - `critical_updater.exe` y `updater.exe` no son procesos legítimos de Windows.  
  - Sospecha de malware (posible ransomware).  

---

### **5. URL sospechosa accedida por `updater.exe`**  

**Comando utilizado**:  
```bash  
vol.py -f mem.raw windows.memmap --dump --pid 1612  
```  
**Análisis de strings**:  
```bash  
strings pid_1612.dmp | grep "http"  
```  
**Resultados**:  
- **URL accedida**: `http://critical-updates.com/en.txt`.  
- **Contenido del archivo `en.txt`**: Clave de cifrado `cafebabe`.  

---

### **6. Clave de cifrado del PDF**  

**Evidencia encontrada**:  
- En el volcado de memoria del proceso `updater.exe`, se identificó una cadena relacionada con el cifrado:  
```  
Encryption Key: cafebabe  
```  
**Conclusión**: La clave `cafebabe` se utilizó para cifrar `important_document.pdf`.  

---
#### **Conclusiones del Análisis**

El análisis revela que el proceso **updater.exe** (PID 1612) es malicioso y responsable de las siguientes acciones:

- **Encriptación del Archivo:** Utilizó la clave **cafate_cafe** para cifrar *important_document.pdf*.
- **Conexión Sospechosa:** Estableció una conexión con **critical_update.com**, probablemente para comunicaciones con el atacante.
- **Ransomware:** Generó *ransom_note.txt*, indicando un ataque de ransomware.

Además, se identifican vectores de ataque potenciales:
- La conexión RDP desde **192.168.182.150** sugiere un acceso remoto interno como posible punto de entrada.
- La conexión al puerto 80 hacia **192.168.182.128** podría estar relacionada con un servidor web comprometido dentro de la red.

La conexión a **20.7.1.246** (Microsoft) se descarta como maliciosa.

## **En Pocas Palabras**

1. **Vector de ataque**: La conexión RDP desde `192.168.182.150` permitió al atacante ejecutar `critical_updater.exe`.  
2. **Propagación**: El malware estableció conexiones HTTP internas (`192.168.182.128:80`) y externas (`20.71.246.253:443`).  
3. **Cifrado de archivos**: El proceso `updater.exe` encriptó el PDF usando la clave `cafebabe` y dejó una nota de rescate (`ransom_note.txt`).  

---

## **Recomendaciones**  

1. **Aislamiento**: Desconectar el equipo `192.168.182.150` para evitar propagación.  
2. **Eliminación de malware**: Usar herramientas antimalware para remover `critical_updater.exe` y `updater.exe`.  
3. **Recuperación de datos**: Utilizar la clave `cafebabe` para descifrar `important_document.pdf`.  
4. **Refuerzo de seguridad**:  
   - Auditar políticas de RDP.  
   - Implementar autenticación multifactor.  
   - Capacitar al personal en identificación de phishing.  

---











