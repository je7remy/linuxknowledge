---
tipo: teoria
tags: [sintesis, bash, python, dfir, forense]
actualizado: 2026-05-30
---

# Síntesis — Bash y Python en DFIR

🏠 [[🔒🐧Hub|Hub Principal]]

**Nota de síntesis cross-dominio** que aplica el contenido de
[[MOC - Python para Ciberseguridad]] y [[_1- Curso de Linux y Bash Scripting|el curso de Bash]]
al dominio **defensivo** ([[MOC - Forense Digital end-to-end]]).
Complementa [[Sintesis - Python vs Bash en pentesting|Sintesis Python vs Bash en pentesting]]
(ofensivo).

## Mismo lenguaje, contexto opuesto

| Tarea | Ofensivo (pentest) | Defensivo (DFIR) |
|---|---|---|
| Sockets | reverse shells | analizar conexiones C2 capturadas |
| Hashing | crackear hashes | verificar integridad de evidencia |
| Sniffing | interceptar credentials | analizar PCAPs post-incident |
| Parse files | extraer secrets | analizar logs, registry, prefetch |
| Networking | escanear targets | mapear movimiento lateral |

**Insight clave**: las mismas herramientas, distinto rol. Un buen DFIR
debe entender lo ofensivo para reconocer las técnicas usadas.

## Bash en DFIR — donde brilla

### 1. Triage rápido en máquina comprometida

Bash es ubicuo. Comandos de triage común:

```bash
# Procesos sospechosos
ps auxf | head -50

# Conexiones de red activas
ss -tunap        # moderno
netstat -tunap   # legacy

# Últimas líneas de syslog
tail -n 100 /var/log/syslog | grep -iE "fail|error|denied"

# Usuarios con login reciente
last -n 20

# Archivos modificados en últimas 24h
find / -mtime -1 -type f -not -path "/proc/*" -not -path "/sys/*" 2>/dev/null

# SUID binaries (privilege escalation potential)
find / -perm -4000 -type f 2>/dev/null

# Cron jobs (persistencia común)
for u in $(cut -f1 -d: /etc/passwd); do crontab -u $u -l 2>/dev/null; done
ls -la /etc/cron.* /var/spool/cron/

# Auth logs
grep "Failed password" /var/log/auth.log | tail -20
```

### 2. Recolección masiva de artifacts

```bash
#!/bin/bash
# triage.sh - rápida recolección de evidencia inicial
EVID="/tmp/triage_$(hostname)_$(date +%Y%m%d_%H%M%S)"
mkdir -p $EVID/{logs,configs,processes,network}

# Procesos
ps auxf > $EVID/processes/ps.txt
ls -la /proc/*/exe 2>/dev/null > $EVID/processes/exe_links.txt

# Red
ss -tunap > $EVID/network/connections.txt
ip a > $EVID/network/interfaces.txt
arp -a > $EVID/network/arp.txt

# Logs
cp -r /var/log/auth.log /var/log/syslog $EVID/logs/ 2>/dev/null

# Configs
cp /etc/passwd /etc/shadow /etc/sudoers $EVID/configs/ 2>/dev/null
cp -r /etc/cron* $EVID/configs/ 2>/dev/null

# Tarball
tar czf "$EVID.tar.gz" -C /tmp "$(basename $EVID)"
echo "Evidence: $EVID.tar.gz"
```

### 3. Parseo de logs

Bash + `awk`/`sed`/`grep` es excelente para grep masivo:

```bash
# Top 10 IPs con failed logins
grep "Failed password" /var/log/auth.log | \
  awk '{for(i=1;i<=NF;i++) if($i=="from") print $(i+1)}' | \
  sort | uniq -c | sort -rn | head

# Usuarios sospechosos (logins fuera de horario)
last | awk '$5~/^0[0-6]:/' 

# Tamaño de logs por servicio
find /var/log -type f -name "*.log" -exec du -h {} \; | sort -rh | head
```

### 4. Búsqueda de IOCs

```bash
# Buscar un hash en todos los archivos
HASH="abc123def456..."
find / -type f -exec sha256sum {} \; 2>/dev/null | grep "$HASH"

# Buscar IPs maliciosas en logs
grep -E "${IOC_IP_1}|${IOC_IP_2}|${IOC_IP_3}" /var/log/*.log
```

[[_1- Curso de Linux y Bash Scripting|Ver curso completo de Bash]] en el vault.

## Python en DFIR — donde brilla

### 1. Análisis de memoria con Volatility

```python
# Volatility es una herramienta Python para análisis de RAM
# Uso típico:
import volatility3.framework
# (en práctica se usa CLI: vol -f memory.dump windows.pslist)
```

CLI rápido:
```bash
vol -f memory.raw windows.pslist                # procesos
vol -f memory.raw windows.netstat              # conexiones
vol -f memory.raw windows.cmdline              # command lines
vol -f memory.raw windows.malfind              # injected code
vol -f memory.raw windows.dumpfiles --pid 1234 # dump archivos del proceso
```

### 2. Parsing avanzado de PCAPs

```python
# Con pyshark (wrapper de Wireshark)
import pyshark

cap = pyshark.FileCapture('capture.pcap', display_filter='http')
for packet in cap:
    if hasattr(packet, 'http'):
        host = packet.http.host if hasattr(packet.http, 'host') else 'N/A'
        uri = packet.http.request_uri if hasattr(packet.http, 'request_uri') else 'N/A'
        print(f"{packet.ip.src} → {host}{uri}")

# Con scapy (manipulación raw)
from scapy.all import rdpcap, IP, TCP
packets = rdpcap('capture.pcap')
for pkt in packets:
    if IP in pkt and TCP in pkt:
        if pkt[TCP].dport == 443:
            print(f"{pkt[IP].src}:{pkt[TCP].sport} → {pkt[IP].dst}:443")
```

[[Wireshark|Ver entity page Wireshark]] para más sobre análisis de pcaps.

### 3. Extracción de metadatos

```python
from PIL import Image
from PIL.ExifTags import TAGS

img = Image.open('suspicious.jpg')
exif = img._getexif() or {}
for tag_id, value in exif.items():
    tag = TAGS.get(tag_id, tag_id)
    print(f"{tag}: {value}")
# GPS coords, modelo de cámara, software, fecha exacta
```

[[_2- Extraer Metadatos de imagenes|Ver carpeta Extraer Metadatos en el vault]].

### 4. Análisis de archivos sospechosos

```python
# Verificar tipo de archivo real (no por extensión)
import magic
file_type = magic.from_file('archivo.pdf.exe')
# → "PE32 executable (GUI) Intel 80386"

# Hashes
import hashlib
def hashes(path):
    md5, sha256 = hashlib.md5(), hashlib.sha256()
    with open(path, 'rb') as f:
        while chunk := f.read(8192):
            md5.update(chunk)
            sha256.update(chunk)
    return md5.hexdigest(), sha256.hexdigest()

# Strings extraction
import re
with open('malware.bin', 'rb') as f:
    data = f.read()
strings = re.findall(rb'[\x20-\x7E]{6,}', data)
for s in strings[:50]:
    print(s.decode('latin-1'))
```

### 5. APIs de threat intel

```python
import requests

# VirusTotal lookup
def vt_lookup(file_hash, api_key):
    headers = {'x-apikey': api_key}
    r = requests.get(
        f'https://www.virustotal.com/api/v3/files/{file_hash}',
        headers=headers
    )
    return r.json()

# AbuseIPDB
def abuseipdb_check(ip, api_key):
    r = requests.get(
        'https://api.abuseipdb.com/api/v2/check',
        headers={'Key': api_key, 'Accept': 'application/json'},
        params={'ipAddress': ip, 'maxAgeInDays': 90}
    )
    return r.json()

# MISP, OTX AlienVault, Shodan, Censys — todos con APIs Python
```

### 6. Timeline construction

```python
# log2timeline / plaso (Python) — supertimeline de artifacts forenses
# CLI: log2timeline.py timeline.plaso disk_image.dd
#      psort.py -o l2tcsv -w timeline.csv timeline.plaso

# Análisis post-procesamiento:
import pandas as pd
df = pd.read_csv('timeline.csv')
df['datetime'] = pd.to_datetime(df['datetime'])
df_sorted = df.sort_values('datetime')
# Filtrar eventos sospechosos por palabras clave
suspicious = df_sorted[df_sorted['message'].str.contains('powershell|encoded|invoke-expression', case=False, na=False)]
```

## Patrón híbrido en DFIR

En la práctica se combinan:

```bash
# Bash recolecta evidencia rápida
./triage.sh > triage.log

# Python procesa lo recolectado
python3 analyze_triage.py triage.log --output report.html
```

O:

```bash
# Bash + Python pipeline para detectar anomalías
tshark -r capture.pcap -T fields -e ip.src -e ip.dst -e tcp.dstport | \
  python3 detect_anomalies.py --baseline normal_traffic.json
```

## Frameworks Python notables en DFIR

| Framework | Función |
|---|---|
| **Volatility 3** | Memory forensics |
| **Plaso / log2timeline** | Timeline construction |
| **Velociraptor** (también Bash) | EDR open source con queries VQL |
| **GRR Rapid Response** | Live forensics a escala (Google) |
| **TheHive + Cortex** | Incident response platform (parte Python) |
| **MISP** | Threat intelligence sharing (Python web app) |
| **dfvfs / dfdatetime** | Forensic libraries de Google |
| **pyshark / scapy** | Análisis de red |
| **YARA-Python** | Pattern matching para malware |

## Habilidades del DFIR analyst

### Bash imprescindible

- Comandos forensic-friendly: `find`, `stat`, `ls -la`, `lsof`.
- One-liners: `awk`, `sed`, `grep`, `cut`, `sort`, `uniq`.
- Pipes y redirección.
- Encoding (`base64`, `xxd`).

### Python imprescindible

- File I/O eficiente (chunks).
- `requests` para APIs de threat intel.
- `pandas` para procesamiento de timelines.
- `re` para regex.
- `hashlib`, `subprocess`.
- Conocer **Volatility plugins** clave.

## Cobertura en el vault

- [[_1- Curso de Linux y Bash Scripting|Curso de Bash]] — base.
- [[_2- Curso de Python Aplicado a la Ciberseguridad|Curso de Python]] — base.
- [[MOC - Forense Digital end-to-end|MOC - Forense Digital]] — el flujo.
- [[Wireshark|Wireshark (entity page)]] — herramienta clave.
- [[Sintesis - Python vs Bash en pentesting|Python vs Bash (ofensivo)]] — el otro lado.

## Próximos pasos sugeridos

Si quieres profundizar:

1. **SANS FOR508** — Advanced Incident Response, Threat Hunting, and
   Digital Forensics (Bash + Python intensivo).
2. **SANS FOR610** — Reverse-Engineering Malware (Python + IDA/Ghidra).
3. **Velociraptor labs** — gratuitos, learning VQL + queries.
4. **Crear tu propio toolkit personal** de scripts triage en GitHub.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Sintesis - Python vs Bash en pentesting|Síntesis: Python vs Bash en pentesting]] — comparativa ofensiva.
- [[MOC - Forense Digital end-to-end|MOC - Forense Digital]] — el flujo completo.
- [[MOC - Python para Ciberseguridad|MOC - Python para Ciberseguridad]] — Python aplicado.
- [[Wireshark|Wireshark]] — análisis de PCAPs.
- [[Malware|Malware]] — análisis de samples con Python.
