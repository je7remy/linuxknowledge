### **Captura de tráfico con `tcpdump` y compartirlo con un servidor HTTP:**

#### **Objetivo:**

1. Capturar tráfico en una interfaz de red específica (por ejemplo, `eth0`) y guardar el tráfico en un archivo `.pcap`.
2. Servir el archivo capturado a través de un servidor HTTP para descargarlo.
3. Filtrar la captura en Wireshark para obtener credenciales de FTP.

---

### **Paso 1: Crear el script Bash**

Escribimos un script en Bash para automatizar el proceso. El siguiente ejemplo incluye:

- Captura de tráfico con `tcpdump`.
- Inicio de un servidor HTTP con Python.
- Terminación de procesos después de un período de tiempo.

#### **Contenido del script (simple):


```bash
#!/bin/bash

INTERFAZ="eth0" 
ARCHIVO_DUMP="captura.pcap"
PUERTO_HTTP="80"

tcpdump -i $INTERFAZ -w $ARCHIVO_DUMP &

sleep 5

python3 -m http.server $PUERTO_HTTP &

sleep 30

proceso_tcpdump=$(pgrep tcpdump)
proceso_python=$(pgrep python3)

kill $proceso_tcpdump
kill $proceso_python

echo "Captura Finalizada y .pcap compartido por la web"
```

### **1. Declaración del intérprete**

```bash
#!/bin/bash
```

- Indica que el script debe ejecutarse usando el intérprete de comandos `bash`.

---

### **2. Definición de variables**

```bash
INTERFAZ="eth0"
ARCHIVO_DUMP="captura.pcap"
PUERTO_HTTP="80"
```

- **`INTERFAZ`**: Especifica la interfaz de red en la que `tcpdump` capturará el tráfico (en este caso, `eth0`).
- **`ARCHIVO_DUMP`**: Nombre del archivo donde se guardará el tráfico capturado (formato `.pcap`).
- **`PUERTO_HTTP`**: Puerto en el que se ejecutará el servidor HTTP (por defecto, `80`).

---

### **3. Captura de tráfico con `tcpdump`**

```bash
tcpdump -i $INTERFAZ -w $ARCHIVO_DUMP &
```

- **`tcpdump`**: Herramienta para capturar paquetes en la red.
    - **`-i $INTERFAZ`**: Captura tráfico en la interfaz especificada (`eth0`).
    - **`-w $ARCHIVO_DUMP`**: Escribe los datos capturados en el archivo `captura.pcap`.
- **`&`**: Ejecuta el proceso en segundo plano, permitiendo que el script continúe con los siguientes comandos.

---

### **4. Pausa antes de iniciar el servidor HTTP**

```bash
sleep 5
```

- Pausa la ejecución del script durante 5 segundos para permitir que `tcpdump` inicie y capture datos antes de levantar el servidor web.

---

### **5. Iniciar un servidor HTTP con Python**

```bash
python3 -m http.server $PUERTO_HTTP &
```

- **`python3 -m http.server`**: Inicia un servidor HTTP básico.
    - **`$PUERTO_HTTP`**: Especifica el puerto en el que se ejecutará el servidor (en este caso, `80`).
- **`&`**: Ejecuta el servidor HTTP en segundo plano.

---

### **6. Pausa para permitir captura y servicio activo**

```bash
sleep 30
```

- Pausa el script durante 30 segundos para permitir que:
    - `tcpdump` capture tráfico.
    - El servidor HTTP esté disponible para servir el archivo `.pcap`.

---

### **7. Obtener los IDs de los procesos**

```bash
proceso_tcpdump=$(pgrep tcpdump)
proceso_python=$(pgrep python3)
```

- **`pgrep tcpdump`**: Busca el ID del proceso de `tcpdump`.
- **`pgrep python3`**: Busca el ID del proceso del servidor HTTP (Python).
- Estos IDs se guardan en las variables `proceso_tcpdump` y `proceso_python`, respectivamente, para finalizar los procesos más adelante.

---

### **8. Terminar ambos procesos**

```bash
kill $proceso_tcpdump
kill $proceso_python
```

- **`kill`**: Envía una señal para finalizar los procesos especificados.
    - **`$proceso_tcpdump`**: Finaliza la captura de tráfico.
    - **`$proceso_python`**: Detiene el servidor HTTP.

---

### **9. Mensaje final**

```bash
echo "Captura Finalizada y .pcap compartido por la web"
```

- **`echo`**: Muestra un mensaje informando que la captura ha finalizado y que el archivo `.pcap` se compartió a través del servidor HTTP.

```bash
# NOTA IMPORTANTE: 
# 1. Antes de ejecutar este script, asegúrate de que un servidor FTP esté activo # y accesible en la red. 

# 2. Durante la ejecución del script: # - Inicia sesión en el servidor FTP. 
# - Esto permitirá que las credenciales (usuario y contraseña) sean capturadas. 

# 3. Una vez que finalice el script: # - Usa Wireshark para analizar el archivo .pcap generado. 
# - Filtra por tráfico FTP (ftp) para visualizar las credenciales capturadas.
```

---

### **Resumen del Flujo**

1. Configura las variables para la interfaz de red, el archivo de captura y el puerto HTTP.
2. Inicia la captura de tráfico con `tcpdump`.
3. Pausa brevemente para asegurar que `tcpdump` comience a capturar.
4. Levanta un servidor HTTP básico para compartir el archivo `.pcap`.
5. Captura datos y sirve el archivo durante 30 segundos.
6. Finaliza ambos procesos (`tcpdump` y el servidor HTTP).
7. Muestra un mensaje indicando que la captura ha terminado.

#### **Contenido del script (adaptado):**

```bash
#!/bin/bash

# Configuración de variables
INTERFAZ="eth0"                      # Interfaz de red a capturar
ARCHIVO_DUMP="captura.pcap"          # Archivo donde se almacenará el tráfico
PUERTO_HTTP="80"                     # Puerto para el servidor HTTP

# Paso 1: Iniciar captura con tcpdump
tcpdump -i "$INTERFAZ" -w "$ARCHIVO_DUMP" &

# Guardar el ID del proceso tcpdump
proceso_tcpdump=$!

# Paso 2: Esperar unos segundos para iniciar el servidor HTTP
sleep 5

# Paso 3: Iniciar un servidor HTTP simple
python3 -m http.server "$PUERTO_HTTP" &

# Guardar el ID del proceso del servidor HTTP
proceso_python=$!

# Paso 4: Esperar mientras la captura y el servidor están activos
sleep 30

# Paso 5: Finalizar ambos procesos
kill "$proceso_tcpdump"
kill "$proceso_python"

echo "Captura finalizada. El archivo $ARCHIVO_DUMP está disponible durante 30 segundos en el puerto $PUERTO_HTTP."
```

### **Desglose por partes**

#### **1. Shebang y configuración inicial**

```bash
#!/bin/bash
```

- **`#!/bin/bash`**: Especifica que el script debe ejecutarse con el intérprete de Bash.

Variables:

```bash
INTERFAZ="eth0"          # Nombre de la interfaz de red a capturar
ARCHIVO_DUMP="captura.pcap"  # Nombre del archivo de salida para guardar los paquetes capturados
PUERTO_HTTP="8080"       # Puerto en el que se ejecutará el servidor web
```

- Se definen las variables para facilitar la configuración:
    - `INTERFAZ`: La interfaz de red a monitorear.
    - `ARCHIVO_DUMP`: Nombre del archivo `.pcap` donde se guardará el tráfico capturado.
    - `PUERTO_HTTP`: Puerto en el que se abrirá el servidor HTTP.

---

#### **2. Captura de tráfico con `tcpdump`**

```bash
tcpdump -i "$INTERFAZ" -w "$ARCHIVO_DUMP" &
```

- **`tcpdump`**: Herramienta para capturar tráfico de red.
- **`-i "$INTERFAZ"`**: Especifica la interfaz de red (por ejemplo, `eth0`).
- **`-w "$ARCHIVO_DUMP"`**: Indica que la salida se escribirá en un archivo (`captura.pcap`).
- **`&`**: Ejecuta `tcpdump` en segundo plano para que el script continúe ejecutándose.

```bash
proceso_tcpdump=$!
```

- **`$!`**: Obtiene el ID del proceso (`PID`) del último comando que se ejecutó en segundo plano. Esto nos permite controlar el proceso más adelante.

---

#### **3. Retraso para iniciar el servidor HTTP**

```bash
sleep 5
```

- **`sleep 5`**: Pausa el script durante 5 segundos. Esto permite que `tcpdump` capture algo de tráfico antes de iniciar el servidor web.

---

#### **4. Iniciar el servidor HTTP**

```bash
python3 -m http.server "$PUERTO_HTTP" &
```

- **`python3 -m http.server`**: Inicia un servidor HTTP básico.
- **`"$PUERTO_HTTP"`**: Especifica el puerto en el que se ejecutará el servidor (en este caso, `8080`).
- **`&`**: Ejecuta el servidor HTTP en segundo plano.

```bash
proceso_python=$!
```

- Al igual que con `tcpdump`, se guarda el ID del proceso del servidor HTTP para poder finalizarlo más tarde.

---

#### **5. Esperar mientras se capturan datos**

```bash
sleep 30
```

- **`sleep 30`**: Pausa el script durante 30 segundos, permitiendo que:
    - `tcpdump` capture más tráfico.
    - El servidor HTTP esté disponible para descargar el archivo.

---

#### **6. Finalizar ambos procesos**

```bash
kill "$proceso_tcpdump"
kill "$proceso_python"
```

- **`kill`**: Envía una señal para terminar los procesos.
- **`$proceso_tcpdump`** y **`$proceso_python`**: Son los IDs de los procesos capturados anteriormente.

---

#### **7. Mensaje final**

```bash
echo "Captura finalizada. El archivo $ARCHIVO_DUMP está disponible durante 30 segundos en el puerto $PUERTO_HTTP."
```

- Muestra un mensaje indicando que la captura se completó y el archivo se sirvió en el puerto HTTP especificado.

```bash
# NOTA IMPORTANTE: 
# 1. Antes de ejecutar este script, asegúrate de que un servidor FTP esté activo # y accesible en la red. 

# 2. Durante la ejecución del script: # - Inicia sesión en el servidor FTP. 
# - Esto permitirá que las credenciales (usuario y contraseña) sean capturadas. 

# 3. Una vez que finalice el script: # - Usa Wireshark para analizar el archivo .pcap generado. 
# - Filtra por tráfico FTP (ftp) para visualizar las credenciales capturadas.
```

---

### **Funcionamiento Completo**

1. El script inicia la captura de tráfico en `eth0` y guarda los datos en `captura.pcap`.
2. Después de 5 segundos, inicia un servidor HTTP en el puerto `8080`.
3. Captura tráfico durante 30 segundos y permite acceder al archivo a través del servidor HTTP.
4. Finaliza los procesos de captura (`tcpdump`) y el servidor HTTP.
5. Imprime un mensaje indicando el final del proceso.

---

### **Paso 2: Ejecución del script**

1. Copia el script en un archivo, por ejemplo, `captura.sh`.
2. Asigna permisos de ejecución:
    
    ```bash
    chmod +x captura.sh
    ```
    
3. Ejecuta el script como superusuario:
    
    ```bash
    sudo ./captura.sh
    ```
    

Al ejecutarlo, el script:

- Captura el tráfico de la interfaz `eth0` y guarda los datos en `captura.pcap`.
- Inicia un servidor web accesible desde `http://<IP_DEL_SISTEMA>:8080/captura.pcap`.

---

### **Paso 3: Analizar el archivo `.pcap` con Wireshark**

1. Abre Wireshark:
    
    ```bash
    wireshark captura.pcap
    ```
    
2. Aplica un filtro para tráfico FTP:
    
    - Filtro: `ftp`
    - Wireshark mostrará solo el tráfico FTP, que incluye comandos y respuestas.
3. Busca los comandos `USER` y `PASS` en el tráfico filtrado para identificar credenciales de usuario y contraseña enviados en texto claro.
    

---

### **Notas importantes:**

- **Legalidad y ética:** Solo realiza este procedimiento en sistemas donde tengas autorización explícita para realizar pruebas.
- **Seguridad:** Asegúrate de que tu entorno de pruebas esté aislado para evitar interferencias externas.

