---
tipo: teoria
tags: [vpn, networking, entity-page, privacidad, ciberseguridad]
actualizado: 2026-05-30
---

# VPN — Virtual Private Network

🏠 [[🔒🐧Hub|Hub Principal]]

**Entity page** del concepto **VPN** — túnel cifrado sobre una red
pública (típicamente internet) que permite comunicación segura como si
los dispositivos estuvieran en una LAN privada.

## Definición

Una **VPN** crea una conexión virtual cifrada punto a punto. Dos casos
típicos:

1. **Remote access VPN**: usuario remoto se conecta a la red corporativa.
2. **Site-to-site VPN**: dos redes (oficinas) conectadas vía VPN tunnel.

Adicionalmente, las VPNs comerciales (NordVPN, Mullvad, ProtonVPN) ofrecen
**privacy VPN** — el usuario sale a internet a través del VPN provider
para ocultar su IP real.

## Protocolos VPN

| Protocolo | Año | Estado | Uso |
|---|---|---|---|
| **WireGuard** | 2016 | ✅ Estándar moderno | Mejor rendimiento, código pequeño, criptografía moderna |
| **OpenVPN** | 2001 | ✅ Maduro | Muy común, configurable, SSL/TLS based |
| **IKEv2/IPsec** | 2005 | ✅ Bueno en mobile | Resilient a roaming, nativo en iOS |
| **L2TP/IPsec** | 1999 | ⚠️ Legacy | Usa puerto fijo (500/4500), bloqueable |
| **PPTP** | 1996 | ❌ Roto | NO USAR (criptografía rota desde 2012) |
| **SSTP** | 2007 | ⚠️ Microsoft only | Funciona sobre HTTPS (443) |

**Recomendación 2025**: WireGuard para nuevos despliegues, OpenVPN si
necesitas compatibilidad amplia.

## Cómo funciona (alto nivel)

```
Cliente VPN                       VPN Server
    │                                  │
    │── 1. Authentication ──────────→  │ (cert, credentials, MFA)
    │                                  │
    │←── 2. Key exchange ─────────────│ (Diffie-Hellman)
    │                                  │
    │── 3. Tunnel established ──────→ │ (todo el tráfico cifrado)
    │                                  │
    │── (encrypted packet) ─────────→ │
    │                                  │── (decrypted) → internet/LAN
```

## VPN en ciberseguridad

### Uso defensivo (empresarial)

- **Acceso remoto seguro**: empleados desde casa acceden a recursos
  internos (servidores, intranet, file shares).
- **Site-to-site**: conectar oficinas geográficamente distintas.
- **Cloud access**: AWS Site-to-Site VPN, Azure VPN Gateway.
- **Zero Trust alternative**: cada vez más empresas reemplazan VPN
  tradicional por modelos Zero Trust (BeyondCorp).

### Uso ofensivo (pentesting)

- **Pivoting**: tras comprometer un host con VPN, usar el túnel para
  acceder a la red interna.
- **Evasión**: cambiar geo-location para bypasear geo-blocking.
- **Anonimato relativo**: combinar con TOR para evitar atribución.

### Uso personal (privacy)

- Cifrar tráfico en redes Wi-Fi públicas (cafés, aeropuertos).
- Ocultar IP de servicios web (ISP no ve qué visitas).
- Bypass de censura en países restrictivos.
- Acceso a contenido geo-restringido (Netflix de otros países).

## Vulnerabilidades históricas notables

### En productos VPN

- **Pulse Secure** (CVE-2019-11510): file disclosure pre-auth, masivamente
  explotado.
- **Fortinet FortiGate** (CVE-2018-13379): path traversal, usado por
  APTs y ransomware groups.
- **Palo Alto GlobalProtect** (CVE-2024-3400): RCE pre-auth (2024).
- **Cisco ASA** (varias CVEs incl. memory leaks que filtran credenciales).

**Patrón**: gateways VPN son **blanco prioritario** de APTs porque dan
acceso directo a red interna ([[APT|ver entity page APT]]).

### Configuraciones débiles

- **Split tunneling**: tráfico no-corporativo sale fuera del VPN. Si el
  host se infecta, puede ser pivote.
- **Sin MFA**: credenciales solas en gateway = compromiso fácil.
- **DNS leaks**: queries DNS salen fuera del VPN, revelan sitios visitados.
- **WebRTC leaks**: navegador filtra IP real vía WebRTC.

## VPN vs alternativas modernas

### VPN tradicional

- ✅ Madurez, herramientas, conocido.
- ❌ Once inside, full network access (lateral movement).
- ❌ "Trust the network" model.

### Zero Trust Network Access (ZTNA)

- Cada request autenticado y autorizado individualmente.
- Productos: Cloudflare Access, Zscaler ZTNA, Twingate.
- No hay "inside" o "outside" — todo es verificado.

### TOR

- Anonimato superior (multi-hop).
- Lentitud, no apto para uso corporativo.
- Riesgo de exit nodes maliciosos.

### Tailscale / Headscale

- Mesh VPN basado en WireGuard.
- Sin servidor central (peer-to-peer).
- UX excepcional para developers.

## Herramientas relacionadas (pentesting)

| Herramienta | Función |
|---|---|
| **OpenVPN client** | Conectar a VPN OpenVPN |
| **WireGuard** | Conectar a VPN WireGuard |
| **proxychains** | Forzar otros tools a salir por VPN/proxy |
| **sshuttle** | "Poor man's VPN" usando SSH |
| **Chisel** | TCP/UDP tunneling sobre HTTP |
| **ligolo-ng** | Pivoting VPN moderno para Red Team |

## Cobertura en el vault

- [[_2- Identificación del sistema|Curso Google Cyber 3 → VPN (módulo redes)]] — fundamentos.
- [[Networking|Networking (entity page)]] — VPN como capa L3.
- [[MOC - Networking del Pentester|MOC - Networking]] — pivoting.
- [[MOC - Pentesting end-to-end|MOC - Pentesting]] — VPN como vector de
  entrada (gateways vulnerables).

## Configuración rápida: WireGuard

```bash
# Server
wg genkey | tee privatekey | wg pubkey > publickey
cat > /etc/wireguard/wg0.conf <<EOF
[Interface]
PrivateKey = <server_private_key>
Address = 10.0.0.1/24
ListenPort = 51820

[Peer]
PublicKey = <client_public_key>
AllowedIPs = 10.0.0.2/32
EOF
wg-quick up wg0

# Client
cat > /etc/wireguard/wg0.conf <<EOF
[Interface]
PrivateKey = <client_private_key>
Address = 10.0.0.2/24

[Peer]
PublicKey = <server_public_key>
Endpoint = vpn.example.com:51820
AllowedIPs = 0.0.0.0/0       # tunneling completo
PersistentKeepalive = 25
EOF
wg-quick up wg0
```

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Networking|Networking (entity page)]] — VPN sobre L3.
- [[Cryptography|Cryptography]] — TLS, IPsec, key exchange.
- [[Authentication|Authentication]] — VPN gateway usa auth (MFA crítico).
- [[MOC - Networking del Pentester|MOC - Networking]] — VPN attacks y pivoting.
- [[APT|APT]] — VPN gateways como vector de APTs.
