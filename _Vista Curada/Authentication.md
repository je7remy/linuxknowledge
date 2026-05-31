---
tipo: teoria
tags: [authentication, autenticacion, entity-page, identidad, iam]
actualizado: 2026-05-30
---

# Authentication — Autenticación

🏠 [[🔒🐧Hub|Hub Principal]]

**Entity page** del concepto de **autenticación** — el proceso de
verificar que una entidad (usuario, dispositivo, servicio) es **quien
dice ser**. Es la primera línea de defensa de cualquier sistema y blanco
constante de ataques.

## Definición

**Authentication** (autenticación) = **¿quién eres?**

A diferencia de **Authorization** (autorización) = **¿qué puedes hacer?**

Las 3 son el "AAA" de seguridad de acceso:
1. **Authentication** — verificar identidad.
2. **Authorization** — qué puedes hacer una vez autenticado.
3. **Accounting** (auditing) — registrar qué hiciste.

## Factores de autenticación

| Factor | Algo que... | Ejemplos |
|---|---|---|
| **1. Knowledge** | sabes | password, PIN, respuestas de seguridad |
| **2. Possession** | tienes | token físico, smartphone, smart card, OTP app |
| **3. Inherence** | eres | biometría: huella, cara, iris, voz |
| **4. Location** | estás | GPS, IP corporativa, geofencing |
| **5. Behavior** | haces | typing patterns, mouse dynamics |

**MFA (Multi-Factor Authentication)**: requerir 2+ factores **distintos**.
- ❌ Password + PIN = NO es MFA (ambos son knowledge).
- ✅ Password + OTP app = MFA real.

## Métodos de autenticación

### 1. Password-based

Algo simple pero el método más usado y vulnerable.

**Buenas prácticas:**
- Longitud > 14 caracteres.
- Sin reutilización entre sitios.
- Password manager (Bitwarden, 1Password, KeePassXC).
- **Hashing seguro** server-side: bcrypt, Argon2, scrypt.

**Ataques** ([[Pentesting|ver MOC pentesting]]):
- Brute force, dictionary attack.
- Credential stuffing (passwords filtradas en otras breaches).
- Password spraying (1 password × muchos usuarios).
- Phishing.
- Keylogging.

### 2. Multi-Factor Authentication (MFA / 2FA)

#### Tipos de segundo factor

| Tipo | Pros | Contras |
|---|---|---|
| **SMS OTP** | Fácil de usar | Vulnerable a SIM swapping, NIST lo deprecó |
| **TOTP app** (Google Auth, Authy) | Offline, fuerte | Requiere smartphone |
| **Push notification** (Duo, Okta) | UX excelente | Fatiga MFA (atacante spamming) |
| **Hardware token** (YubiKey, Titan) | El más fuerte (FIDO2) | Costo, perdible |
| **Email OTP** | Universal | Tan débil como el email |
| **Biometría local** (Touch ID, Face ID) | UX excelente | Limitado a dispositivo |

#### FIDO2 / WebAuthn / Passkeys

Estándar moderno **passwordless**. Usa criptografía asimétrica:
- Clave privada en device (TPM, secure enclave, YubiKey).
- Clave pública en server.
- Resistente a phishing por diseño (origin binding).

**Passkeys** (Apple, Google, Microsoft, 2023+) hacen FIDO2 mainstream.

### 3. Single Sign-On (SSO)

Un solo login para múltiples aplicaciones. Protocolos:
- **SAML 2.0** — XML-based, enterprise (Okta, Azure AD).
- **OAuth 2.0** — autorización (no autenticación per se).
- **OpenID Connect (OIDC)** — autenticación sobre OAuth.
- **Kerberos** — clásico en Active Directory.

### 4. Certificate-based authentication

Cliente presenta certificado X.509:
- VPNs (OpenVPN con `--auth cert`).
- mTLS (mutual TLS) en APIs.
- 802.1X en redes corporativas.

### 5. Risk-based / Adaptive authentication

Sistema evalúa factores contextuales (IP, device, geolocation, hora) y
decide si requiere step-up (MFA adicional).

## Kerberos — el caso de Active Directory

Protocolo de autenticación basado en **tickets** centralizados (KDC).
Componentes:

- **KDC** (Key Distribution Center): emite tickets.
- **TGT** (Ticket Granting Ticket): permite solicitar otros tickets.
- **TGS** (Ticket Granting Service): tickets para servicios específicos.

**Flujo:**
```
1. Usuario → AS-REQ → KDC          (pide TGT)
2. KDC → AS-REP → Usuario          (TGT cifrado con hash del usuario)
3. Usuario descifra TGT (su hash).
4. Usuario → TGS-REQ + TGT → KDC   (pide ticket para servicio X)
5. KDC → TGS-REP → Usuario         (ticket de servicio)
6. Usuario → ticket → Servicio     (acceso autenticado)
```

**Ataques contra Kerberos** ([[MOC - Active Directory Pentesting]]):
- **AS-REP Roasting** (preauth disabled).
- **Kerberoasting** (cracking TGS de service accounts).
- **Pass-the-Ticket** (PtT) — reutilizar TGT capturado.
- **Golden Ticket** — TGT falsificado con hash de `krbtgt`.
- **Silver Ticket** — TGS falsificado con hash de service account.

## Vulnerabilidades comunes en authentication

### OWASP A07 — Authentication Failures

Ver [[MOC - Web Pentesting OWASP|MOC OWASP]] A07:

- Default credentials (admin/admin).
- Session fixation (no rota session id post-login).
- Insecure password recovery (resetear con email comprometido).
- Weak password policies.
- No rate limiting en login → brute force.
- JWT vulns: `alg: none`, weak secret, signature stripping.

### Account enumeration

Login devuelve error distinto entre "user no existe" y "password incorrecta"
→ atacante enumera usuarios válidos.

### Insecure direct authentication

Ejemplo: cookie `user=admin` sin firma. Cambias a `user=root` y entras.

## Defensa en profundidad

```
┌──────────────────────────────────────────────────┐
│ User presents credentials                        │
├──────────────────────────────────────────────────┤
│ Rate limiting (ban tras N intentos fallidos)     │
├──────────────────────────────────────────────────┤
│ Password verification (hash compare bcrypt/Argon)│
├──────────────────────────────────────────────────┤
│ MFA step (TOTP / FIDO2 / push)                   │
├──────────────────────────────────────────────────┤
│ Risk evaluation (geolocation, device fingerprint)│
├──────────────────────────────────────────────────┤
│ Session creation (secure cookie, short lifetime) │
├──────────────────────────────────────────────────┤
│ Logging (success + failures)                     │
└──────────────────────────────────────────────────┘
```

## Cobertura en el vault

- [[_3- Controles de Acceso, Autenticación y Gestión de Identidades|Curso Google Cyber 5 → Controles de Acceso (Módulo 2)]] —
  IAM, autorización fundamentos.
- [[_0- Cómo PREPARAR una ENTREVISTA TÉCNICA para un Puesto de CIBERSEGURIDAD|Entrevista técnica]] —
  conceptos AAA, Kerberos en preguntas.
- [[MOC - Active Directory Pentesting]] — Kerberos attacks en detalle.
- [[Cryptography|Cryptography]] — JWT, hashing de passwords, PKI.

## Mejores prácticas en código

```python
# ❌ MAL — SHA-256 directo, vulnerable a GPU brute force
import hashlib
pw_hash = hashlib.sha256(password.encode()).hexdigest()

# ✅ BIEN — bcrypt con salt automático
import bcrypt
pw_hash = bcrypt.hashpw(password.encode(), bcrypt.gensalt(rounds=12))

# ✅ MEJOR — Argon2id (PHC winner)
from argon2 import PasswordHasher
ph = PasswordHasher()
pw_hash = ph.hash(password)
```

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Cryptography|Cryptography]] — JWT, password hashing, PKI.
- [[MOC - Active Directory Pentesting|MOC - AD Pentesting]] — Kerberos attacks.
- [[MOC - Web Pentesting OWASP|MOC - OWASP]] — A07 auth failures.
- [[SIEM EDR y SOC|SIEM, EDR y SOC]] — logs de login son fuente clave.
- [[Pentesting|Pentesting (entity page)]] — auth bypass es objetivo común.
