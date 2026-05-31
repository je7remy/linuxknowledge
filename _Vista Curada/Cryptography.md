---
tipo: teoria
tags: [criptografia, cryptography, entity-page, cifrado, hashing]
actualizado: 2026-05-30
---

# Cryptography

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Entity page** del concepto de **criptografía** — la ciencia que permite
comunicaciones seguras incluso en presencia de adversarios. Es la base de
HTTPS, autenticación, integridad de datos y privacidad digital.

## Definición

**Criptografía** = matemáticas + computación para garantizar:

1. **Confidencialidad** — solo el destinatario puede leer.
2. **Integridad** — el mensaje no se alteró en tránsito.
3. **Autenticidad** — el mensaje viene de quien dice.
4. **No repudio** — el emisor no puede negar haberlo enviado.

## Tres ramas principales

### 1. Cifrado simétrico

Una sola clave compartida para cifrar y descifrar.

| Algoritmo | Tamaño clave | Estado |
|---|---|---|
| **AES** (Rijndael) | 128/192/256 bits | **Estándar actual** ✅ |
| **ChaCha20** | 256 bits | Moderno, mobile-friendly ✅ |
| **3DES** | 168 bits efectivos | Deprecated ⚠️ |
| **DES** | 56 bits | Roto desde 1999 ❌ |
| **RC4** | variable | Roto ❌ |

**Modos de operación AES**: CBC, GCM, CTR, ECB (no usar).

### 2. Cifrado asimétrico (clave pública)

Par de claves: **pública** (compartible) y **privada** (secreta). Lo
cifrado con la pública solo lo descifra la privada (y viceversa para
firmas).

| Algoritmo | Base matemática | Estado |
|---|---|---|
| **RSA** | Factorización de primos | Vigente (2048+ bits) ✅ |
| **ECDSA / Ed25519** | Curvas elípticas | Moderno, más eficiente ✅ |
| **Diffie-Hellman** | Logaritmo discreto | Para intercambio de claves ✅ |
| **DSA** | Logaritmo discreto | Vigente pero menos usado |
| **ElGamal** | Logaritmo discreto | Académico |

### 3. Funciones hash

Función unidireccional que produce un resumen de tamaño fijo.

| Algoritmo | Tamaño | Estado |
|---|---|---|
| **SHA-256 / SHA-512** | 256/512 bits | **Estándar actual** ✅ |
| **SHA-3 (Keccak)** | 224-512 bits | Moderno (2015+) ✅ |
| **BLAKE2 / BLAKE3** | variable | Más rápido que SHA ✅ |
| **bcrypt / scrypt / Argon2** | variable | Para passwords (slow by design) ✅ |
| **SHA-1** | 160 bits | Roto desde 2017 ⚠️ |
| **MD5** | 128 bits | Roto desde 2005 ❌ |

**Importante**: bcrypt/scrypt/Argon2 son hashes **diseñados para ser lentos**
para resistir cracking por fuerza bruta. NO usar SHA-256 para passwords.

## Aplicaciones prácticas

### HTTPS / TLS

Combina los tres:

1. **Asimétrico** (RSA/ECDSA) para autenticar el servidor + intercambio
   de clave de sesión.
2. **Simétrico** (AES-GCM/ChaCha20) para cifrar el tráfico.
3. **Hash** (SHA-256) para integridad de cada mensaje.

### Firmas digitales

1. Hash del mensaje (SHA-256).
2. Cifrar el hash con clave privada del firmante.
3. Cualquiera con la clave pública puede verificar.

### MAC y HMAC

- **MAC** (Message Authentication Code) — autenticidad + integridad con
  clave compartida.
- **HMAC** — MAC construido sobre función hash (HMAC-SHA256).

### JWT (JSON Web Tokens)

```
header.payload.signature
```

- **Header**: algoritmo (`HS256`, `RS256`, `ES256`).
- **Payload**: claims (datos).
- **Signature**: HMAC o firma asimétrica.

Vulns comunes: `alg: none`, weak secret, signature stripping.

### PKI (Public Key Infrastructure)

Sistema de **certificados** firmados por una jerarquía de CAs
(Certificate Authorities) que crea confianza distribuida.

```
Root CA → Intermediate CA → End-entity cert (servidor)
```

Estándar: X.509. Formato: PEM, DER.

### TOR / VPN

Cifrado de tráfico extremo a extremo + ofuscación de origen.

## Cobertura en el vault

- [[_7- Cifrado y Criptografía en Python|7- Cifrado y Criptografía en Python]] —
  sección completa con implementaciones:
  - César, Vigenère (clásicos didácticos).
  - RSA, AES (modernos).
  - Hashing (MD5, SHA, HMAC).
- [[_2- Fundamentos de la Criptografía|Fundamentos de la Criptografía (Google Cyber Curso 5)]] —
  teoría.
- [[_1- Cracking|1- Cracking]] — Hashcat para crackear hashes (uso ofensivo).

## Aspectos ofensivos (cómo se rompe criptografía)

### Ataques a algoritmos débiles

- **MD5/SHA1 collisions** — chosen-prefix collisions (HashClash, SHAttered).
- **DES brute force** — 56 bits son insuficientes hoy.

### Ataques a implementaciones

- **Padding Oracle Attack** — descubrir plaintext explotando errores
  específicos de padding (CBC).
- **Bleichenbacher attack** — contra RSA PKCS#1 v1.5.
- **Side channels** — timing, power analysis, cache attacks.

### Ataques a configuración

- **Weak random number generators** — predicción de claves.
- **Reusing nonces** (en GCM, CTR) — catastrófico.
- **Hardcoded keys** en código fuente.

### Cracking de hashes (caso del vault)

- **Diccionarios** — listas comunes (rockyou.txt).
- **Mascaras** — patrones (`?u?l?l?l?l?l?d?d`).
- **Hybrid** — diccionario + reglas de mutación.
- **Hashcat** — [[_1- Cracking|guía en el vault]].

### Quantum threat

- **Shor's algorithm** rompe RSA y ECC en computadora cuántica
  suficientemente grande.
- Solución: **Post-Quantum Cryptography** (CRYSTALS-Kyber, Dilithium
  estandarizados por NIST en 2024).

## Buenas prácticas (Cryptographic hygiene)

1. **No inventes tu propio algoritmo** ("Don't roll your own crypto").
2. Usa bibliotecas estándar (`libsodium`, `cryptography` Python, `OpenSSL`).
3. AES-GCM > AES-CBC para nuevos proyectos.
4. Para passwords: **Argon2** (winner del Password Hashing Competition).
5. Rotación de claves periódica.
6. **Forward Secrecy** (PFS) — comprometida la clave de hoy, no compromete el tráfico de ayer.
7. Verifica **certificados TLS** correctamente (pinning si aplica).

## Cryptographic agility

Diseñar sistemas que puedan **cambiar de algoritmo** fácilmente cuando
uno se rompe. Crítico para preparar la transición a post-quantum.

## Estándares y referencias

- **NIST FIPS** — Federal Information Processing Standards (140-2/3).
- **IETF RFCs** — TLS 1.3 (RFC 8446), JWT (RFC 7519), JWE (RFC 7516).
- **ISO/IEC 18033** — algoritmos cifrado.
- **OWASP Cryptographic Storage Cheat Sheet**.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[_7- Cifrado y Criptografía en Python|Carpeta Criptografía en Python]] —
  implementaciones prácticas.
- [[_1- Cracking|Cracking de hashes]] — uso ofensivo.
- [[Pentesting|Pentesting (entity page)]] — cripto en pentest webapp.
- [[MOC - Web Pentesting OWASP|MOC - Web Pentesting OWASP]] — A02 vuln
  específica de crypto.
