
# 📑 Informe Paso a Paso – Modificación e Instalaciones en Chromebook Dell P22T

**Responsable:** Jeremy José de la Cruz Pérez  
**Equipo:** Dell Chromebook 11 P22T  
**Objetivo:** Habilitar la Chromebook para instalar y probar FydeOS, Windows 10, Linux (antiX) y PrimeOS, dejando operativo el sistema más cercano a lo solicitado por el cliente.

---

## 1) Desbloqueo del Firmware

### 1.1. Quitar bloqueo **físico** (Write Protect – WP)

1. **Apagar** la Chromebook.
    
2. **Retirar** todos los tornillos de la tapa inferior y **destapar**.
    
3. Identificar en la placa el **tornillo “WP” (Write Protect)**.
    
4. **Remover** el tornillo WP para permitir la escritura del firmware.
    
5. Cerrar la tapa (puedes dejarla abierta si vas a seguir con pruebas, pero evita cortos).
    

> 🔎 **Nota:** Este paso es imprescindible para instalar **UEFI completo (Full ROM)**.

---

### 1.2. Quitar bloqueo **de software** y entrar a **Modo Desarrollador**

1. Con el equipo **apagado**, mantener las teclas para ir a recuperación:
    
    - **Secuencia estándar en la mayoría:** `Esc` + `Refresh (↻)` + **Power**.
     
2. En la pantalla **“Chrome OS is missing or damaged / Recovery”**, presiona **`Ctrl` + `D`**.
    
3. Confirma cuando lo pida (en algunos modelos, **Enter**).
    
    > El equipo se **reiniciará** y activará el **Modo Desarrollador** (borra datos locales).
    
4. En posteriores arranques verás **“OS verification is OFF”**. Para continuar, presiona **`Ctrl` + `D`** (o espera el conteo).
    

---

### 1.3. Verificar/Desactivar **write-protect de software** (opcional pero recomendado)

> Normalmente el script de MrChromebox gestiona esto, pero si quieres hacerlo explícitamente:

1. En ChromeOS (ya en Modo Desarrollador), abre **crosh** con **`Ctrl` + `Alt` + `T`**.
    
2. Escribe:
    
    ```
    shell
    ```
    
3. Comprueba estado de write-protect:
    
    ```
    sudo flashrom --wp-status
    ```
    
4. Si aparece habilitado, **deshabilítalo**:
    
    ```
    sudo flashrom --wp-disable
    ```
    
5. Verifica de nuevo:
    
    ```
    sudo flashrom --wp-status
    ```
    

---

## 2) Instalar **UEFI completo** con MrChromebox

1. En la misma terminal (crosh → `shell`), descarga y ejecuta el script:
    
    ```bash
    cd
    curl -LO https://mrchromebox.tech/firmware-util.sh
    sudo bash firmware-util.sh
    ```
    
2. En el menú, elige **“Install/Update UEFI (Full ROM)”**.
    
3. **Haz copia de seguridad** cuando lo pida (recomendado guardar en **USB**).
    
4. Confirma los avisos y espera a que termine la escritura del firmware.
    
5. **Apaga** la Chromebook.
    

> ✅ A partir de aquí, el equipo **bootea como un PC UEFI** y acepta instaladores estándar (USB GPT/UEFI).

---

## 3) Preparación de USBs de instalación (resumen común)

- Formatea el USB en **GPT** y **FAT32** cuando lo requiera (p. ej., FydeOS/Android-x86).
    
- Crea el USB booteable con tu herramienta preferida (Ventoy/Rufus/Etcher).
    
    > Con **Ventoy**, usa **partición GPT** para maximizar compatibilidad UEFI.
    

---

## 4) Pruebas de Sistemas Operativos

### 4.1. **FydeOS** (ChromeOS modificado)

1. Bootea desde el USB (UEFI).
    
2. Instala FydeOS en el disco interno.
    
3. Intenta activar **Google Play** (opción integrada según build).
    
4. **Resultado real:**
    
    - La **Play Store** no funcionó correctamente (subsistema Android no levantaba).
        
    - **Sin audio** por falta de **driver** para este modelo.
        
5. **Decisión:** descartar FydeOS para el cliente por limitaciones de Play y audio.
    

---

### 4.2. **Windows 10** (desatendido)

1. Bootea el instalador UEFI y completa la instalación.
    
2. **Resultado real:**
    
    - **Touchpad** sin driver → se controló con **mouse USB**.
        
    - **Audio** sin driver (chip tipo Intel SST/Max98090) → **sin sonido interno**.
        
3. **Decisión:** operativo pero con **demasiadas carencias de drivers** para el uso del cliente.
    

---

### 4.3. **Linux antiX OS** (distro ligera)

1. Bootea el instalador UEFI.
    
2. **Particionado recomendado:**
    
    - **ESP (UEFI):** 100–300 MB, FAT32, flag `esp`/`boot`
        
    - **/** (raíz): ≥ 14 GB, **ext4**
        
    - **swap:** opcional según RAM (2–4 GB si lo deseas)
        
3. Completa la instalación y primer arranque.
    
4. **Red:** si hace falta, usa `ceni` para configurar.
    
5. **Resultado real:**
    
    - **Rápido y estable** en este hardware.
        
    - **Audio** presente pero **con volumen bajo/limitado**.
        
    - **Sin Google Play** (es Linux puro).
        
6. **Decisión:** excelente como Linux ligero, pero no cumple el requisito Play Store.
    

---

### 4.4. **PrimeOS** (Android-x86 orientado a PC)

1. Bootea el instalador UEFI de PrimeOS.
    
2. Instala en el disco interno (formato **ext4**) y permite que configure su **GRUB**.
    
3. Primer arranque:
    
    - Completa el **setup** de Android.
        
    - **Inicia sesión** en **Google Play** (viene **de fábrica**, sin parches extra).
        
4. **Resultado real:**
    
    - **Rendimiento** fluido; **Play Store** funcionando **correctamente**.
        
    - **Único faltante:** **audio interno** (no hay driver para este modelo).
        
    - **Alternativas de audio:** **Bluetooth**, **USB** o **HDMI** → no operativos.
        
5. **Decisión:** es **lo más cercano a lo que pidió el cliente** (Android con Play Store).
    

---

## 5) Estado final y entrega

- Se deja el equipo con **PrimeOS instalado y funcional**, **Google Play operativo**.
    
- Se informa claramente:
    
    - El **audio interno** no funciona por **falta de driver** para este hardware en PrimeOS.
        
    - El sonido no se puede usar por **Bluetooth/USB/HDMI**.
        
- Se documenta que FydeOS y Windows 10 también presentaron **limitaciones de audio**, y Windows además **faltó driver de touchpad**.
    
- **antiX OS** quedó como opción Linux **muy estable y ligera**, pero **sin Play Store**.
    

---

## 6) Apéndice: Atajos y comandos usados

**Atajos clave**

- Recuperación / Developer Mode:
    
    - Estándar: `Esc` + `Refresh (↻)` + **Power** → luego `Ctrl` + `D`.
        
- Saltar aviso “OS verification is OFF”: **`Ctrl` + `D`**.
    

**Terminal (crosh)**

```bash
# Abrir crosh y entrar a shell
Ctrl+Alt+T
shell

# (Opcional) Revisar/desactivar write-protect por software
sudo flashrom --wp-status
sudo flashrom --wp-disable
sudo flashrom --wp-status

# Script MrChromebox (UEFI Full ROM)
cd
curl -LO https://mrchromebox.tech/firmware-util.sh
sudo bash firmware-util.sh
# Elegir: Install/Update UEFI (Full ROM)
```

---

### ✅ Conclusión

- **UEFI completo** instalado correctamente tras quitar **WP físico** y bloquear/desbloquear software donde aplicó.
    
- **PrimeOS** entrega la **experiencia Android con Play Store** que el cliente quería.
    
- La **limitación estructural** es el **driver de audio interno**.
    

---
