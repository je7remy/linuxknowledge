---
tipo: herramienta
tags: [wireshark, network-analysis, packet-capture, entity-page, herramienta]
actualizado: 2026-05-30
---

# Wireshark

🏠 [[🔒🐧Hub|Hub Principal]]

**Entity page** de **Wireshark** — el analizador de protocolos de red más
usado del mundo. Open source, multiplataforma, esencial tanto para
networking troubleshooting como para forense digital y pentesting.

## Definición

**Wireshark** es un **packet analyzer** (sniffer) que captura tráfico
de red en tiempo real o lee archivos PCAP existentes, y permite
**inspeccionar cada paquete** a nivel de bytes — útil para debugging,
forense, pentesting y aprendizaje de protocolos.

## Componentes del proyecto

| Componente | Tipo | Uso |
|---|---|---|
| **wireshark** | GUI | Análisis interactivo |
| **tshark** | CLI | Captures y filtros en terminal |
| **dumpcap** | CLI | Solo capture (no análisis) |
| **mergecap** | CLI | Combinar PCAPs |
| **editcap** | CLI | Editar PCAPs |
| **capinfos** | CLI | Estadísticas de un PCAP |
| **rawshark** | CLI | Stream processing |

## Casos de uso por dominio

### 🛡️ Pentesting (ofensivo)

- **Sniffing pasivo**: capturar credenciales en texto plano (FTP, HTTP, Telnet).
- **MITM analysis**: después de ARP spoofing, ver tráfico interceptado.
- **Reconocimiento**: identificar servicios, OSes, versiones.
- **Validación de exploits**: ver el payload de red de un exploit.

### 🔬 Forense digital (defensivo)

- **Análisis post-incident**: leer PCAPs capturados durante intrusión.
- **Reconstruir actividad**: qué dominios contactó el malware, qué
  exfiltró, cuándo.
- **Identificar C2**: tráfico anómalo a IPs/dominios sospechosos.
- **Extraer archivos**: `File → Export Objects → HTTP/SMB/etc`.

### 🌐 Networking troubleshooting

- Latencia alta: medir RTT en TCP handshakes.
- Conexiones fallidas: ver SYN sin ACK.
- DNS issues: ver queries que fallan.
- Misconfiguración: tráfico inesperado.

### 📚 Aprendizaje

- Ver el modelo OSI/TCP-IP en acción.
- Entender exactamente cómo funcionan los protocolos.

## Display Filters — el superpoder

Wireshark tiene **dos tipos de filtros**:

1. **Capture filters** (BPF syntax) — qué capturar al inicio.
2. **Display filters** (Wireshark syntax) — qué mostrar de lo capturado.

Display filters son MUCHO más potentes:

```
# Solo HTTP de un IP
ip.addr == 192.168.1.10 and http

# Solo tráfico DNS con NXDOMAIN
dns.flags.rcode == 3

# TCP SYN flag set (inicios de conexión)
tcp.flags.syn == 1 and tcp.flags.ack == 0

# HTTP requests
http.request

# HTTP responses con error 500
http.response.code >= 500

# Buscar string en payload
frame contains "password"

# Excluir tráfico de tu IP
not ip.addr == 192.168.1.5

# Tráfico SMB
smb or smb2

# Tráfico Kerberos (auth en AD)
kerberos
```

## Statistics y herramientas built-in

Wireshark incluye análisis avanzados sin scripting:

- **Statistics → Conversations**: top talkers (qué IPs hablan más).
- **Statistics → Endpoints**: lista de hosts y volumen.
- **Statistics → Protocol Hierarchy**: distribución de protocolos.
- **Statistics → IO Graphs**: gráfico temporal de tráfico.
- **Statistics → Flow Graph**: secuencia visual de paquetes entre 2 hosts.
- **Analyze → Expert Information**: warnings, errors detectados.
- **File → Export Objects**: extraer archivos transferidos (HTTP, SMB, FTP).

## Capturar tráfico — buenas prácticas

### Captura local

```bash
# tshark CLI — capturar 1000 paquetes en eth0
tshark -i eth0 -c 1000 -w capture.pcap

# Solo tráfico web
tshark -i eth0 -f "tcp port 80 or tcp port 443"

# Capturar solo en horario específico
tshark -i eth0 -a duration:60 -w capture.pcap   # 60 seg

# Display filter durante captura
tshark -i eth0 -Y "http.request" -T fields -e http.host -e http.user_agent
```

### Captura remota

```bash
# SSH + tshark + abrir en Wireshark local
ssh user@remote "tshark -w - -F pcap" | wireshark -k -i -
```

### Captura en cloud / containers

- **AWS VPC Traffic Mirroring**: replica tráfico de ENI a un sensor.
- **Kubernetes**: `tcpdump` en sidecar container.

## Casos prácticos del vault

- [[_3- Caso Practico, Un hacker entró a mi equipo|Caso forense: hacker en mi equipo]] — análisis de PCAP de intrusión.
- [[5.1- Registro TCP-HTTP-LOG – Wireshark (Tráfico Web Normal y Ataque SYN Flood)|Wireshark — Tráfico normal vs SYN flood]] — del curso Google Cyber.
- [[1- Investigación de Spear Phishing - Caso Luxury Design JFK|Caso Spear Phishing — Luxury Design JFK]] — Wireshark + ExifTool.

## Wireshark vs alternativas

| Herramienta | Mejor para |
|---|---|
| **Wireshark / tshark** | Análisis interactivo profundo |
| **tcpdump** | Captura rápida en CLI, scripts |
| **NetworkMiner** | Forense (extracción automática de archivos, sesiones) |
| **CapAnalysis** | Web UI para visualizar PCAPs grandes |
| **Zeek (antes Bro)** | Análisis automatizado de tráfico, scripts |
| **Suricata** | IDS/IPS con captura |
| **Brim** | Querying de PCAPs con SQL-like |

## Tips avanzados

### 1. Coloring rules

Crear reglas para colorear paquetes anómalos (ej: HTTP 5xx en rojo).
`View → Coloring Rules`.

### 2. Lua scripts

Wireshark soporta Lua para dissectors custom. Útil si trabajas con
protocolos propietarios.

### 3. Decrypt TLS

Si tienes la clave (o el `SSLKEYLOGFILE`):
`Preferences → Protocols → TLS → (Pre)-Master-Secret log filename`

Permite ver HTTPS en plaintext (con la clave correspondiente).

### 4. Reassembly

Wireshark reensambla flujos TCP/HTTP fragmentados automáticamente.
`Follow → TCP Stream` para ver conversación completa.

### 5. Filter macros

`Analyze → Display Filter Macros` para reutilizar filtros complejos.

## Limitaciones

- **No descifra TLS sin la key** (obvio pero importante).
- **No es real-time defense** (no bloquea, solo analiza).
- **Performance**: PCAPs muy grandes (>2GB) lentos en GUI; usar tshark.
- **No detecta amenazas automáticamente** — usa Suricata/Zeek/Snort.

## Cobertura en el vault

- [[_3- Conectar y proteger, redes y seguridad de red|Curso Google Cyber 3 — Redes]] — Wireshark fundamentos.
- [[_6- Forense Digital|6- Forense Digital]] — Wireshark en investigaciones.
- [[Networking|Networking (entity page)]].
- [[MOC - Networking del Pentester|MOC - Networking]] — análisis de capa por capa.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Networking|Networking (entity page)]] — Wireshark visualiza todo lo de Networking.
- [[DNS|DNS (entity page)]] — filtros para analizar tráfico DNS.
- [[MOC - Forense Digital end-to-end|MOC - Forense Digital]] — Wireshark es herramienta clave.
- [[Sintesis - Forense vs Pentesting|Síntesis Forense vs Pentesting]] — Wireshark se usa en ambos.
- [[Malware|Malware]] — análisis de tráfico C2 con Wireshark.
