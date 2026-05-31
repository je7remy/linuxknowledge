---
tipo: teoria
tags: [dns, networking, entity-page, redes]
actualizado: 2026-05-30
---

# DNS — Domain Name System

🏠 [[🔒🐧Hub|Hub Principal]]

**Entity page** del **Sistema de Nombres de Dominio** — protocolo
fundamental de internet que traduce nombres legibles (`google.com`) a
direcciones IP (`142.250.74.46`). Componente crítico de toda
infraestructura de red, blanco común de ataques y herramienta defensiva.

## Definición

**DNS** es un sistema jerárquico distribuido que mapea **nombres de
dominio** a **direcciones IP** (y otros datos). Funciona sobre **UDP/53**
(consultas) y **TCP/53** (transferencias de zona, respuestas grandes).

Sin DNS, internet sería inutilizable — tendrías que memorizar IPs.

## Tipos de registros DNS

| Tipo | Función | Ejemplo |
|---|---|---|
| **A** | Mapea nombre → IPv4 | `google.com → 142.250.74.46` |
| **AAAA** | Mapea nombre → IPv6 | `google.com → 2607:f8b0:::200e` |
| **CNAME** | Alias (apunta a otro nombre) | `www.example.com → example.com` |
| **MX** | Mail server | `example.com → mail.example.com` |
| **NS** | Name server autoritativo | `example.com → ns1.example.com` |
| **TXT** | Texto arbitrario (SPF, DKIM, verificación) | `v=spf1 include:_spf.google.com ~all` |
| **SOA** | Start of Authority (info de la zona) | (administrativo) |
| **PTR** | Reverse lookup (IP → nombre) | `46.74.250.142.in-addr.arpa → google.com` |
| **CAA** | Certificate Authority Authorization | restringe qué CAs emiten certs |
| **SRV** | Service location | `_kerberos._tcp.example.com → krb1.example.com:88` |

## Jerarquía DNS

```
Root (.) ← servers raíz
   └── TLD (.com, .org, .net) ← top-level domains
        └── Domain (example.com) ← second-level
             └── Subdomain (mail.example.com)
                  └── etc.
```

## Flujo de resolución (recursivo)

```
Cliente quiere "google.com":
1. Cliente → DNS recursivo (ISP/Cloudflare/etc.)
2. Recursivo → Root server (".")
   ← "pregunta a TLD .com server"
3. Recursivo → TLD ".com" server
   ← "pregunta a ns1.google.com"
4. Recursivo → ns1.google.com (autoritativo)
   ← "google.com = 142.250.74.46"
5. Recursivo cachea la respuesta + responde al cliente.
```

## DNS en ciberseguridad

### Uso ofensivo

#### 1. Reconocimiento ([[OSINT]])

- **DNS enumeration**: descubrir subdominios.
  - Herramientas: `dnsenum`, `dnsrecon`, `amass`, `subfinder`, `assetfinder`.
- **Reverse DNS**: descubrir hostnames desde IPs.
- **Zone transfer (AXFR)**: si está mal configurado, dump completo de la zona.

```bash
dig axfr example.com @ns1.example.com
dnsrecon -d example.com -t axfr
```

- **Certificate Transparency logs**: descubrir subdominios via `crt.sh`.

#### 2. DNS spoofing / cache poisoning

Atacante inyecta respuestas DNS falsas para redirigir tráfico:
- **Tipo MITM**: requiere posición en la red.
- **Tipo cache poisoning**: explota implementaciones débiles.

Herramientas: `bettercap`, `dnsspoof` (Dsniff suite).

#### 3. DNS tunneling

Exfiltrar data a través de queries DNS (que firewalls rara vez bloquean):
- Encoding de data en subdomains (`base32_encoded_data.attacker.com`).
- Herramientas: `iodine`, `dnscat2`.

#### 4. DNS rebinding

Atacante hace que un dominio resuelva primero a una IP suya, luego a una
IP interna del cliente (`127.0.0.1`, `192.168.x.x`). Bypassea Same-Origin
Policy.

#### 5. Domain Generation Algorithms (DGA)

Malware genera dominios dinámicamente para resistir takedowns
([[Malware|ver entity page]]).

#### 6. Fast Flux

Apunta el dominio C2 a IPs cambiantes (cada minutos) para resistir
bloqueos.

### Uso defensivo

#### 1. DNS firewall

Bloquear queries a dominios maliciosos. Productos: Cisco Umbrella,
Quad9 (`9.9.9.9`), Cloudflare for Teams.

#### 2. Sinkholing

Redirigir queries a dominios sospechosos a un servidor controlado.

#### 3. Análisis de logs DNS

- Patrones anómalos: cantidad alta de NXDOMAIN (signo de DGA).
- Subdomains exfiltrados (signo de DNS tunneling).
- Queries a TLDs raros.

#### 4. DNSSEC

Firmas criptográficas en respuestas DNS para garantizar integridad.
Defiende contra cache poisoning.

#### 5. DoH (DNS over HTTPS) / DoT (DNS over TLS)

Cifrado del tráfico DNS para privacidad. **Doble filo:** también dificulta
detección defensiva si el atacante usa DoH.

## DNS en infraestructura corporativa

### Split DNS

Dos vistas del DNS:
- **Internal**: empleados ven IPs internas (10.x.x.x).
- **External**: clientes ven IPs públicas.

### Conditional Forwarders

Forwardear queries de dominios específicos a DNS específicos. Común en
empresas con múltiples Active Directories.

### Active Directory + DNS

[[MOC - Active Directory Pentesting|AD]] depende fuertemente de DNS:
- `_kerberos._tcp.example.com` → KDC.
- `_ldap._tcp.example.com` → Domain Controllers.
- Sin DNS, AD no funciona.

## Herramientas comunes

| Herramienta | Función |
|---|---|
| `dig` (Linux) / `nslookup` (Windows) | Queries manuales |
| `host` | Lookup simplificado |
| `whois` | Info de registro de dominio |
| `dnsenum`, `dnsrecon` | Enumeration ofensiva |
| `amass`, `subfinder` | Subdomain enumeration moderna |
| `tshark` / `wireshark` | Análisis de tráfico DNS |
| `tcpdump -i any port 53` | Capture de queries DNS |

## Cobertura en el vault

- [[_3- Conectar y proteger, redes y seguridad de red|Curso Google Cyber 3 — Redes]] — DNS fundamentos.
- [[Networking|Networking (entity page)]] — DNS como capa L7.
- [[MOC - Networking del Pentester|MOC - Networking]] — DNS en pentesting.
- [[OSINT]] — DNS en reconocimiento.

## CVEs notables relacionados con DNS

- **CVE-2008-1447** (Kaminsky bug) — cache poisoning trivial en BIND.
- **SAD DNS (2020)** — side-channel attack revivió cache poisoning.
- **SIGRed (CVE-2020-1350)** — RCE en Windows DNS Server.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Networking|Networking (entity page)]] — DNS es protocolo de red L7.
- [[OSINT|OSINT (entity page)]] — DNS enum es recon pasivo.
- [[MOC - Networking del Pentester|MOC - Networking]] — DNS attacks por capa.
- [[Malware|Malware]] — DGA y C2 dependen de DNS.
- [[SIEM EDR y SOC|SIEM, EDR y SOC]] — logs DNS son fuente clave de detección.
