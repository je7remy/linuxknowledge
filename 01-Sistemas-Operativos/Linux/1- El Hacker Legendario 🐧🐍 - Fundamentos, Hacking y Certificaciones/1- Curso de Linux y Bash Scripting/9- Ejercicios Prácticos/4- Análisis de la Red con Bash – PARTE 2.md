
---

#Pentesting #CyberSecurity #HackingÉtico #Linux #KaliLinux #ARPscan #Nmap #Redes #EthicalHacking #InfoSec #CTF #RedTeam #BlueTeam #SeguridadInformática #ForenseDigital #SysAdmin #DevSecOps #EscaneoDeRed #EthicalHacker

---
### **Primera Parte: Escaneo con `arp-scan`**

```bash
sudo arp-scan -I eth0 --localnet > prueba.txt
```

- **Qué hace:** Se ejecuta `arp-scan` para escanear la red local (indicada por `--localnet`) utilizando la interfaz `eth0`.
- **Salida:** Los resultados del escaneo se guardan en un archivo llamado `prueba.txt`.
- **Propósito:** Identificar dispositivos conectados en la red local mediante sus direcciones IP y MAC.

---

### **Segunda Parte: Filtrar resultados irrelevantes**

```bash
cat prueba.txt | grep -v "Interface" | grep -v "Starting" | grep -v "packets" | grep -v "Ending"
```

- **Qué hace:**
    - `cat prueba.txt`: Muestra el contenido del archivo `prueba.txt`.
    - `grep -v`: Excluye las líneas que contienen palabras específicas como `Interface`, `Starting`, `packets` o `Ending`.
- **Resultado:** Se eliminan las líneas de encabezado y pie del escaneo, dejando únicamente las líneas relevantes con direcciones IP y MAC.

---

### **Tercer Paso: Obtener solo direcciones IP**

```bash
cat prueba.txt | grep -v "Interface" | grep -v "Starting" | grep -v "packets" | grep -v "Ending" | awk '{print $1}' | tr -d ' '
```

- **Qué hace:**
    - `awk '{print $1}'`: Extrae la primera columna de cada línea, que corresponde a las direcciones IP.
    - `tr -d ' '`: Elimina espacios en blanco en las líneas resultantes.
- **Resultado:** Una lista limpia de direcciones IP.

---

### **Cuarta Parte: Crear un script para automatizar todo**

```bash
#!/bin/bash

arp-scan -I eth0 --localnet | grep -v "Interface" | grep -v "Starting" | grep -v "packets" | grep -v "Ending" | awk '{print $1}' | tr -d ' ' > ips.txt

while read -r linea; do 
  echo "Escaneando con nmap la direccion $linea"
  nmap -p- -sS -sC -sV --min-rate=5000 -n -Pn $linea -oN "escaneo_$linea.txt"
done < ips.txt
rm ips.txt
```

1. **`arp-scan` con filtrado:** Escanea la red, limpia las líneas no relevantes y guarda solo las direcciones IP en `ips.txt`.
2. **Bucle `while`:**
    - Lee cada línea (dirección IP) del archivo `ips.txt`.
    - Para cada dirección IP:
        - Muestra un mensaje indicando que se está escaneando esa dirección con Nmap.
        - Ejecuta un escaneo con Nmap:
            - `-p-`: Escanea todos los puertos.
            - `-sS`: Realiza un escaneo SYN (rápido y sigiloso).
            - `-sC`: Ejecuta scripts NSE básicos de Nmap.
            - `-sV`: Detecta servicios y versiones.
            - `--min-rate=5000`: Configura una tasa mínima de paquetes por segundo.
            - `-n`: Desactiva resolución DNS para mayor velocidad.
            - `-Pn`: Omite el ping para tratar los hosts como activos.
            - `-oN`: Guarda los resultados del escaneo en un archivo nombrado `escaneo_IP.txt`.
3. **Eliminar `ips.txt`:** Una vez procesadas todas las direcciones IP, elimina el archivo temporal `ips.txt`.

---

### **Quinta Parte: Script con Colores**

```bash
#!/bin/bash

arp-scan -I eth0 --localnet | grep -v "Interface" | grep -v "Starting" | grep -v "packets" | grep -v "Ending" | awk '{print $1}' | tr -d ' ' > ips.txt

while read -r linea; do 
  echo -e "\033[0;33mEscaneando con nmap la direccion $linea\033[1;37m"
  nmap -p- -sS -sC -sV --min-rate=5000 -n -Pn $linea -oN "escaneo_$linea.txt"
done < ips.txt
rm ips.txt
```

- **Cambio principal:**
    - Añade colores al mensaje de salida utilizando códigos ANSI:
        - `\033[0;33m`: Cambia el color del texto a amarillo.
        - `\033[1;37m`: Restaura el color original (blanco).

---

### **Resumen del flujo de trabajo**

1. **Escaneo de red local:** `arp-scan` identifica los dispositivos conectados y sus direcciones IP.
2. **Filtrado de resultados:** Se eliminan líneas irrelevantes para centrarse únicamente en las direcciones IP.
3. **Escaneo con Nmap:** Cada dirección IP se analiza para detectar puertos abiertos, servicios y sus versiones.
4. **Resultados:** Los datos del escaneo se guardan en archivos separados por dirección IP.




[[3- Análisis De La Red Desde Linux – Comandos Básicos Parte 1]]
[[5- Análisis de la Red con Bash – PARTE 3]]
[[6- Análisis de Red con TCPdump y WireShark – PARTE 1]]
**[[1- Hoja de trucos NMAP]]**
**[[3- nmap firewall evasion]]**
**[[4- nmap output]]**
[[14- Man-in-the-Middle (MitM) con Bettercap en Kali Linux]]