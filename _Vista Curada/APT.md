---
tipo: teoria
tags: [apt, threat-actors, entity-page, ciberseguridad, espionaje]
actualizado: 2026-05-30
---

# APT — Advanced Persistent Threat

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Entity page** del concepto **APT** (Advanced Persistent Threat) —
actores de amenaza sofisticados, con recursos significativos, que
mantienen acceso no autorizado durante períodos prolongados con objetivos
estratégicos específicos.

## Definición

**APT** = adversario que cumple las 3 A:

1. **Advanced** — capacidad técnica alta (zero-days, malware custom).
2. **Persistent** — mantiene acceso meses o años, no oportunista.
3. **Threat** — intención y recursos para causar daño significativo.

Lo que distingue una APT de un atacante común:

- **Objetivo específico** (target seleccionado, no oportunista).
- **Recursos masivos** (a menudo estado-nación).
- **Paciencia** (operaciones de meses/años).
- **OPSEC** alto (operaciones cuidadosamente compartimentadas).
- **TTPs únicas** (mapeo MITRE ATT&CK distintivo).

## Categorías por motivación

| Motivación | Ejemplos |
|---|---|
| **Espionaje estatal** | APT28 (RU), APT29 (RU), APT41 (CN), Lazarus (KP) |
| **Sabotaje industrial** | Stuxnet (USA/IL → Irán), Industroyer (RU → Ucrania) |
| **Financiero** | Lazarus (bancos), Carbanak/FIN7 |
| **Hacktivismo extremo** | Algunos grupos pro-causa con capacidad APT |
| **Ciberguerra** | NotPetya, Olympic Destroyer |

## APTs famosas (selección)

### APT28 / Fancy Bear / Sofacy

- **Origen**: Rusia (GRU, Unidad 26165).
- **Targets**: gobiernos OTAN, partidos políticos, periodistas.
- **Operaciones notables**: hack del DNC (2016), Bundestag (2015),
  TV5Monde (2015).
- **Malware típico**: X-Agent, Sednit, Zebrocy.

### APT29 / Cozy Bear / The Dukes

- **Origen**: Rusia (SVR).
- **Targets**: gobiernos, think tanks, infraestructura.
- **Operaciones notables**: SolarWinds supply chain (2020), Microsoft
  Exchange (2021).
- **Estilo**: stealth, paciente, OPSEC excepcional.

### Lazarus Group / Hidden Cobra

- **Origen**: Corea del Norte.
- **Targets**: financiero + ciberguerra.
- **Operaciones notables**:
  - Sony Pictures (2014).
  - Bangladesh Bank heist (2016, $81M robados).
  - WannaCry (2017).
  - Criptocurrency exchanges (recurrente, billones USD).

### APT41 / Wicked Panda

- **Origen**: China.
- **Targets**: dual — espionaje + financial (atípico).
- **Sectores**: tech, gaming, healthcare, telco.
- **Notable**: supply chain attacks (CCleaner 2017).

### Equation Group

- **Origen**: presunto NSA (USA).
- **Capacidad técnica**: top-tier (firmware implants, zero-days).
- **Exposed by**: Shadow Brokers leak (2016).
- **Tools leaked**: EternalBlue (usado luego por WannaCry).

### Stuxnet operators

- **Origen**: USA + Israel (presunto).
- **Target**: programa nuclear iraní (Natanz).
- **Sofisticación**: 4 zero-days, primer gusano que dañó hardware físico
  (centrifugadoras).
- **Impacto**: primer ciberataque público con daño cinético real.

## TTPs típicas de una APT

Mapeo a **Cyber Kill Chain** (Lockheed Martin):

### 1. Reconnaissance

- OSINT exhaustivo del target.
- Identificar empleados, tecnologías, proveedores.
- Ver [[OSINT|OSINT (entity page)]].

### 2. Weaponization

- Desarrollo de malware custom para este target.
- Combinación de zero-days + 1-days.

### 3. Delivery

- **Spear phishing** (lo más común) — emails ultra-personalizados.
- **Watering hole** — comprometer sitio web que la víctima visita.
- **Supply chain** — comprometer software/vendor upstream.

### 4. Exploitation

- Exploit de la vuln (browser, document, app).

### 5. Installation

- Persistencia (registry, scheduled tasks, services).
- Múltiples backdoors para resilience.

### 6. Command & Control (C2)

- Beacons cifrados a infrastructure compleja.
- **DGA** (Domain Generation Algorithm) para resiliencia.
- Fast flux DNS, dominios bulletproof hosting.

### 7. Actions on Objectives

- Lateral movement (semanas/meses).
- Privilege escalation gradual.
- Exfiltración cuidadosa de data.

## Diferencia APT vs cibercrimen común

| Aspecto | APT | Cibercrimen común |
|---|---|---|
| Target | Específico, estratégico | Cualquier víctima vulnerable |
| Tiempo de operación | Meses/años | Horas/días |
| Recursos | Masivos (estado) | Limitados |
| Malware | Custom, zero-days | Off-the-shelf, kits |
| Atribución | Política/estratégica | Comercial/oportunista |
| Defensa requerida | EDR + threat hunting + intel | AV moderno + parches |

## Cobertura en el vault

- [[_0- Cómo PREPARAR una ENTREVISTA TÉCNICA para un Puesto de CIBERSEGURIDAD|Entrevista técnica]] —
  APT mencionado como concepto clave en entrevistas.
- [[_8- Amenazas de CIberataques Impulsados por IA|8- Amenazas con IA]] —
  IA potencia operaciones APT.
- [[_6- Forense Digital|6- Forense Digital]] — investigación de
  intrusiones APT.

## Defensa contra APTs

No hay defensa perfecta — pero medidas que aumentan dramáticamente el
costo del atacante:

### Prevención

- **Patch management** disciplinado (cierra los 1-days).
- **Network segmentation** (limita lateral movement).
- **Zero Trust** architecture (verifica cada acción).
- **Least privilege** (cuentas con permisos mínimos).
- **MFA** universal (especialmente admins).
- **Email security** (sandbox, DKIM/DMARC).

### Detección

- **EDR** con threat hunting activo ([[SIEM EDR y SOC]]).
- **SIEM** con reglas de correlación avanzadas.
- **Threat intelligence** feeds (IOCs de APTs conocidas).
- **Deception** (honeypots, canary tokens).
- **Behavior analytics** (UEBA — User and Entity Behavior Analytics).

### Respuesta

- **IR plan** específico para APT (asumen meses comprometidos).
- **Forensics** profesional ([[MOC - Forense Digital end-to-end]]).
- **Eradication** completa (puede requerir wipe + restore).
- **Communication plan** (legal, regulators, customers, prensa).

## MITRE ATT&CK — el lenguaje de las APTs

**MITRE ATT&CK** ([attack.mitre.org](https://attack.mitre.org)) es el
catálogo estándar de **tácticas** (objetivos) y **técnicas** (cómo) que
usan los adversarios.

Estructura:

```
Tactic (por qué)
└── Technique (cómo)
    └── Sub-technique (variante específica)
```

14 tácticas (post-Enterprise Matrix v15):

1. Reconnaissance
2. Resource Development
3. Initial Access
4. Execution
5. Persistence
6. Privilege Escalation
7. Defense Evasion
8. Credential Access
9. Discovery
10. Lateral Movement
11. Collection
12. Command and Control
13. Exfiltration
14. Impact

Ejemplo: `T1566.001 — Phishing: Spearphishing Attachment` es una técnica
específica usada por muchas APTs.

## Threat Intelligence — fuentes

- **Mandiant** (Google Cloud) — reportes APT detallados.
- **CrowdStrike** — Global Threat Report anual.
- **Microsoft** — Defender Threat Intelligence.
- **MITRE** — Groups database (descripciones de cada APT).
- **CISA Alerts** — alertas gubernamentales USA.
- **Recorded Future** — comercial premium.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Malware|Malware (entity page)]] — la herramienta principal de APTs.
- [[SIEM EDR y SOC|SIEM, EDR y SOC]] — defensa contra APTs.
- [[MOC - Pentesting end-to-end|MOC - Pentesting end-to-end]] — los pentesters
  simulan TTPs de APTs (purple team).
- [[Sintesis - IA y Ciberseguridad|Síntesis: IA y Ciberseguridad]] — IA
  potencia operaciones APT.
- [[Hacking Etico|Hacking Ético]] — Red Team simula APTs autorizadamente.
