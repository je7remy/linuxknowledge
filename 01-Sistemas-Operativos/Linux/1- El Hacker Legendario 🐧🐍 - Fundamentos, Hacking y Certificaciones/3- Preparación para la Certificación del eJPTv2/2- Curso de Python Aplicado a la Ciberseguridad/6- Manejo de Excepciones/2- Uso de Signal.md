
---

#Linux #Python #SIGINT #SIGTERM #kill #pkill #procesos #señales #bucleInfinito #manejoDeErrores

---
### Paso a Paso de lo Ocurrido

1. **Virtualización de Kali Linux:**
    
    - Se virtualizó una máquina con Kali Linux.
    - Se accedió al directorio del escritorio con `cd /home/kali/Desktop/`.
    - Se creó y editó un script en Python con `nano script.py`.
2. **Primer Script: Bucle Infinito**
    
    ```python
    import time
    
    while True:
        time.sleep(1)
    ```
    
    - Este script entra en un **bucle infinito** que se ejecuta indefinidamente.
    - `time.sleep(1)` hace que el programa espere **1 segundo** en cada iteración para evitar que consuma demasiados recursos.
3. **Manejo de la Interrupción con `CTRL+C` (SIGINT)**
    
    ```python
    import signal
    import time
    
    def pulsarcontrolc(sig, frame):
        print("Has pulsado control c. Detenemos el script")
        exit(0)
    
    signal.signal(signal.SIGINT, pulsarcontrolc)
    
    print("Presiona control c para interrumpir")
    
    while True:
        time.sleep(1)
    ```
    
    - Se usa el **módulo `signal`** para capturar la señal `SIGINT`, que es enviada cuando se pulsa `CTRL+C`.
    - La función `pulsarcontrolc()` es llamada al recibir `SIGINT`, mostrando un mensaje y finalizando el programa con `exit(0)`.
4. **Manejo de la Terminación con `kill` (SIGTERM)**
    
    ```python
    import signal
    import time
    
    def detener(sig, frame):
        print("Se ha detenido el programa con el comando kill")
        exit(0)
    
    signal.signal(signal.SIGTERM, detener)
    
    print("Esperando a que este proceso sea detenido con el comando KILL")
    
    while True:
        time.sleep(1)
    ```
    
    - Aquí se captura la **señal `SIGTERM`**, que se envía con `kill <PID>`.
    - Al recibir `SIGTERM`, la función `detener()` muestra un mensaje y finaliza el programa.
5. **Visualización del Proceso en Ejecución**
    
    ```bash
    ps -e | grep python  
    ```
    
    - Se usa `ps -e` para listar los procesos en ejecución.
    - `grep python` filtra solo los procesos relacionados con Python.
6. **Detener el Proceso con `pkill`**
    
    ```bash
    sudo pkill -f python3
    ```
    
    - `pkill -f python3` busca y mata cualquier proceso de Python 3.
    - Como se ejecutó con `sudo`, se garantiza la terminación del proceso.

---

### Código Completo Integrado

```python
import signal
import time

def manejar_sigint(sig, frame):
    print("Has pulsado Control+C. Deteniendo el script...")
    exit(0)

def manejar_sigterm(sig, frame):
    print("Se ha detenido el programa con el comando kill")
    exit(0)

# Capturar señales
signal.signal(signal.SIGINT, manejar_sigint)
signal.signal(signal.SIGTERM, manejar_sigterm)

print("Presiona Control+C para interrumpir o usa 'kill <PID>' para terminar el proceso.")

while True:
    time.sleep(1)
```

---