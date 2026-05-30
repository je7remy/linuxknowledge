---
tipo: teoria
tags: [networking, redes, entity-page, fundamentos]
actualizado: 2026-05-30
---

# Networking

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Entity page** del concepto de **redes de computadoras**. Esta nota
unifica los fundamentos teóricos con la práctica de pentesting. Para el
flujo aplicado al pentest, ver [[MOC - Networking del Pentester]].

## Definición

**Networking** es la disciplina que estudia cómo dispositivos
computacionales **comunican datos** entre sí mediante protocolos
estandarizados. Va desde la señalización física (cables, ondas) hasta
las aplicaciones (HTTP, DNS).

## Modelos de referencia

### Modelo OSI (7 capas — académico)

```
7. Aplicación   → HTTP, FTP, SMTP, DNS, SSH
6. Presentación → SSL/TLS, codificación, compresión
5. Sesión       → Establecer/mantener conexiones
4. Transporte   → TCP, UDP
3. Red          → IP, ICMP, routing
2. Enlace       → Ethernet, Wi-Fi, ARP, switches, MAC
1. Física       → Cables, ondas, voltajes, hubs
```

[[1- Modelo OSI|Ver nota detallada del Modelo OSI]].

### Modelo TCP/IP (4-5 capas — práctico)

Fusiona OSI 1-2 y OSI 5-7:

```
4. Aplicación (= OSI 5-7)
3. Transporte (= OSI 4)
2. Internet   (= OSI 3)
1. Acceso a red (= OSI 1-2)
```

## Protocolos por capa (mapa mental)

### Capa Aplicación (L7)

- **HTTP/HTTPS** (80/443) — web.
- **FTP / SFTP** (21/22) — transferencia archivos.
- **SSH** (22) — shell remota cifrada.
- **Telnet** (23) — shell remota plana (legacy, peligroso).
- **SMTP / IMAP / POP3** (25/143/110) — email.
- **DNS** (53) — resolución de nombres.
- **DHCP** (67/68) — asignación de IPs.
- **SNMP** (161) — monitoreo de dispositivos.
- **NTP** (123) — sincronización de tiempo.
- **LDAP** (389/636) — directorio.
- **Kerberos** (88) — autenticación AD.
- **SMB** (445) — compartir archivos Windows.
- **RDP** (3389) — escritorio remoto Windows.
- **MSSQL / MySQL / PostgreSQL** (1433/3306/5432) — bases de datos.

### Capa Transporte (L4)

| Protocolo | Características | Casos |
|---|---|---|
| **TCP** | Confiable, ordenado, conexión | HTTP, SSH, FTP |
| **UDP** | Sin conexión, rápido, sin garantía | DNS, DHCP, VoIP |

### Capa Red (L3)

- **IPv4** — direcciones de 32 bits.
- **IPv6** — direcciones de 128 bits.
- **ICMP** — diagnóstico (ping, traceroute).
- **Routing protocols**: OSPF, BGP, EIGRP, RIP.

### Capa Enlace (L2)

- **Ethernet** — IEEE 802.3.
- **Wi-Fi** — IEEE 802.11 (a/b/g/n/ac/ax).
- **ARP** — resolución MAC ↔ IP.
- **VLAN** — segmentación lógica de switches (802.1Q).

## Direccionamiento

### IPv4

```
Formato: 192.168.1.10
32 bits: 8.8.8.8 octetos

Clases (legacy):
A: 1.0.0.0 - 126.255.255.255    (/8)
B: 128.0.0.0 - 191.255.255.255  (/16)
C: 192.0.0.0 - 223.255.255.255  (/24)
D: multicast
E: experimental

Privadas (RFC 1918):
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

### Subnetting

CIDR notation `/N` indica los primeros N bits son red.

```
/8  = 16,777,214 hosts utilizables
/16 = 65,534
/24 = 254
/30 = 2  (point-to-point típico)
```

### IPv6

128 bits, hexadecimal, agrupado en 8 bloques de 16 bits:

```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
       ↓ comprimido
2001:db8:85a3::8a2e:370:7334
```

## Dispositivos de red

| Dispositivo | Capa | Función |
|---|---|---|
| **Repeater** | L1 | Amplifica señal |
| **Hub** | L1 | Broadcast a todos los puertos |
| **Bridge** | L2 | Conecta segmentos LAN |
| **Switch** | L2 | Forward por MAC (más inteligente que hub) |
| **Router** | L3 | Forward por IP, conecta redes distintas |
| **Firewall** | L3-L7 | Filtra tráfico según reglas |
| **Load balancer** | L4-L7 | Distribuye carga entre servidores |
| **Proxy** | L7 | Intermediario en peticiones |

## Conceptos clave para ciberseguridad

### Three-way handshake (TCP)

```
Cliente → SYN  → Servidor
Cliente ← SYN+ACK ← Servidor
Cliente → ACK → Servidor
[conexión establecida]
```

Base de **SYN scan** ([[_1- Nmap|Nmap]]) y **SYN flood** (DoS).

### MTU y fragmentación

**MTU** (Maximum Transmission Unit) típico Ethernet: 1500 bytes.
Paquetes mayores se fragmentan. Atacantes pueden evadir IDS con
fragmentación específica.

### NAT (Network Address Translation)

Un router con NAT permite que muchos hosts privados compartan una IP
pública. Modos:

- **PAT** (Port Address Translation) / **NAPT** — el común en routers domésticos.
- **Static NAT** — 1:1 mapping.
- **Dynamic NAT** — pool de IPs públicas.

### Routing

- **Static** — admin define rutas manualmente.
- **Dynamic** — protocolos descubren rutas (OSPF, BGP, RIP).
- **Default gateway** — ruta para destinos desconocidos.

## Aplicación en pentesting

[[MOC - Networking del Pentester|Ver MOC completo]]:

| Fase pentest | Conocimiento de red necesario |
|---|---|
| Recon | DNS, certificados SSL, ASN, BGP |
| Escaneo | Modelo TCP/IP, flags TCP, puertos |
| Enumeración | Protocolos específicos por puerto |
| Explotación | Protocolos vulnerables del servicio |
| Lateral | Pivoting, port forwarding, túneles |

## Cobertura en el vault

- [[_2- Redes Basico|2- Redes Básico]] — Modelo OSI fundamentos.
- [[1- Modelo OSI|Modelo OSI (nota)]] — detalle de 7 capas.
- [[_3- Conectar y proteger, redes y seguridad de red|Curso Google Cyber 3 — Redes]] —
  curso completo de Google Cybersecurity sobre seguridad de red.
- [[_1- Nmap|Nmap]] — la herramienta principal de red para pentester.
- [[_2- Shodan|Shodan]] — recon a escala de internet.

## Recursos para profundizar

- **Computer Networking: A Top-Down Approach** (Kurose-Ross) — libro clásico.
- **Network Warrior** (Donahue) — práctico para network engineers.
- **Cisco Press CCNA** — material oficial preparación CCNA.
- **PacketLife.net** — cheatsheets gratis.
- **Practical Networking on YouTube** — visualizaciones claras.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[MOC - Networking del Pentester|MOC - Networking del Pentester]] —
  aplicación práctica.
- [[Pentesting|Pentesting (entity page)]] — donde se aplica.
- [[OSINT|OSINT (entity page)]] — recon de red.
- [[Sintesis - Linux como sistema base del pentester|Linux como sistema base]] —
  tooling de red en Linux.
