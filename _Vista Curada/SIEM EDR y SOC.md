---
tipo: teoria
tags: [siem, edr, soc, entity-page, defensa, blue-team]
actualizado: 2026-05-30
---

# SIEM, EDR y SOC

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Entity page** del trío defensivo central del **Blue Team**: las
herramientas (SIEM, EDR) y la organización (SOC) que defienden una
empresa de ataques cibernéticos. Complementa a [[Pentesting|Pentesting]]
(la cara ofensiva).

## Definiciones rápidas

| Sigla | Expansión | Qué es |
|---|---|---|
| **SIEM** | Security Information and Event Management | Plataforma que **agrega y correlaciona logs** de toda la empresa para detectar incidentes. |
| **EDR** | Endpoint Detection and Response | Agente instalado en cada **endpoint** que detecta y responde a comportamiento malicioso. |
| **SOC** | Security Operations Center | **Equipo de personas** que monitorea SIEM/EDR 24/7 y responde a incidentes. |

## SIEM — Detalle

### Función

Centraliza **logs** de:

- Firewalls (Cisco, Palo Alto, Fortinet).
- Servidores Windows/Linux (Event Logs, syslog).
- Aplicaciones (web servers, DBs).
- IDS/IPS (Snort, Suricata).
- EDR agents.
- Cloud (AWS CloudTrail, Azure Monitor, GCP Logging).

Aplica **reglas de correlación** para detectar patrones:

```
Ejemplo regla:
SI (failed_login > 5 en 1 min desde misma IP)
   AND (successful_login después)
ENTONCES (alerta: brute force exitoso)
```

### Productos principales (2025)

| Vendor | Producto | Notas |
|---|---|---|
| **Splunk** | Splunk Enterprise Security | Líder histórico, costoso, SPL query language. |
| **Microsoft** | Sentinel | Cloud-native, integrado con M365/Azure. |
| **IBM** | QRadar | Empresa grande, AQL. |
| **Elastic** | Elastic SIEM / Security | Open source-friendly, ELK stack. |
| **Wazuh** | Wazuh | Open source completo, fork de OSSEC. |
| **Chronicle (Google)** | Chronicle SIEM | Velocidad de Google, YARA-L. |
| **Devo** | Devo Platform | Cloud-native, escalable. |

### Workflow típico SOC con SIEM

```
1. Logs llegan al SIEM
2. SIEM aplica reglas de detección
3. Genera alerta (con severity)
4. Analista L1 hace triage
5. Si confirma incidente → escalar a L2/L3
6. L2/L3 investiga, contiene, erradica
7. Post-incident review
```

## EDR — Detalle

### Diferencia con antivirus tradicional

- **Antivirus**: detección por **firma** (hash conocido de malware).
- **EDR**: detección por **comportamiento** (qué hace el proceso, no qué es).

EDR es **proactivo**: detecta APTs y zero-days que antivirus no ve.

### Capacidades

- **Detection**: behavior analytics + threat intel + ML.
- **Investigation**: timeline de procesos, network connections, archivos.
- **Response**: aislamiento de endpoint, kill process, rollback de cambios.
- **Threat Hunting**: queries proactivas buscando IOCs.

### Productos principales (2025)

| Vendor | Producto |
|---|---|
| **CrowdStrike** | Falcon |
| **Microsoft** | Defender for Endpoint |
| **SentinelOne** | Singularity |
| **Sophos** | Intercept X |
| **Carbon Black** (VMware) | Carbon Black Cloud |
| **Cybereason** | Defense Platform |
| **Wazuh** (open source) | Wazuh (incluye EDR funcionalidad) |

### EDR vs XDR vs MDR

- **EDR** — Endpoint Detection and Response (solo endpoints).
- **XDR** — eXtended Detection and Response (endpoints + red + cloud + email).
- **MDR** — Managed Detection and Response (SOC tercerizado).

## SOC — Detalle

### Estructura típica

```
Tier 1 — Analista de monitoreo
├─ Triage de alertas
├─ Filtrar falsos positivos
└─ Escalar lo real

Tier 2 — Analista de investigación
├─ Análisis profundo
├─ Pivot entre fuentes (SIEM + EDR + logs)
└─ Containment inicial

Tier 3 — Threat Hunter / IR
├─ Análisis forense
├─ Reverse de malware si aplica
└─ Coordinar con equipos externos (legal, comms)

SOC Manager
└─ Reporta a CISO
```

### Métricas clave (SLAs)

- **MTTD** (Mean Time To Detect) — desde compromiso hasta detección.
- **MTTR** (Mean Time To Respond) — desde detección hasta contención.
- **Dwell time** — tiempo que el atacante estuvo no detectado (industria
  típica: 200+ días pre-EDR moderno, ~30 días con EDR moderno).

### Frameworks de operación

- **NIST CSF** (Cybersecurity Framework) — Identify, Protect, Detect,
  Respond, Recover.
- **MITRE ATT&CK** — clasificación de TTPs (Tactics, Techniques, Procedures).
- **MITRE D3FEND** — contramedidas defensivas.
- **Cyber Kill Chain** (Lockheed Martin) — 7 fases del ataque.
- **The Diamond Model** — modelo de actor + capability + infra + víctima.

## Cobertura en el vault

- [[_6- Haga sonar la alarma Detección y respuesta|Curso Google Cybersecurity 6 — Detección y respuesta]] —
  cubre SIEM, SOC workflow, IR.
- [[_0- Cómo PREPARAR una ENTREVISTA TÉCNICA para un Puesto de CIBERSEGURIDAD|Entrevista técnica]] —
  conceptos SIEM, EDR, MITRE ATT&CK como preguntas.
- [[_8- Amenazas de CIberataques Impulsados por IA|8- Amenazas IA]] — la IA
  potencia SIEM defensivo + ataques.

## Reglas de detección — lenguajes

- **Sigma** — formato genérico YAML, traducible a múltiples SIEMs.
- **Splunk SPL** — Splunk Processing Language.
- **KQL** — Kusto Query Language (Sentinel, Defender).
- **EQL** — Event Query Language (Elastic).
- **YARA** — para matching de archivos/memoria (malware).
- **Snort/Suricata rules** — para tráfico de red (IDS/IPS).

Ejemplo Sigma rule:

```yaml
title: Suspicious Powershell Encoded Command
detection:
  selection:
    Image|endswith: 'powershell.exe'
    CommandLine|contains: '-encodedcommand'
  condition: selection
level: high
```

## Threat Intelligence

Feed externo de IOCs (Indicators of Compromise) que SIEM/EDR consume:

- **MISP** (Malware Information Sharing Platform) — open source.
- **VirusTotal** — agregador de scanners.
- **AlienVault OTX** — comunidad.
- **Recorded Future** — comercial premium.
- **CISA Alerts** — alertas gubernamentales USA.

## Carrera en Blue Team

Roles típicos:

- **SOC Analyst L1** (entry, $40-60k USD).
- **SOC Analyst L2** ($60-90k).
- **Threat Hunter / Detection Engineer** ($90-130k).
- **DFIR Specialist** ($100-140k).
- **Security Engineer** ($120-180k).
- **CISO** (management, $200k+).

Certificaciones más demandadas:

- **CompTIA Security+** (entry, vendor-neutral).
- **CySA+** (CompTIA, analyst-focused).
- **GIAC GCIH / GCED** (SANS).
- **CISSP** (mid-senior, broad).
- **CISM** (management focus).
- **Splunk / Microsoft Sentinel certs** (vendor-specific).

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Pentesting|Pentesting (entity page)]] — la cara ofensiva opuesta.
- [[Hacking Etico|Hacking Ético]] — Red/Blue/Purple Team detallado.
- [[MOC - Forense Digital end-to-end|MOC - Forense Digital]] — DFIR como
  parte del SOC.
- [[APT|APT (entity page)]] — adversario que SIEM/EDR deben detectar.
- [[Sintesis - IA y Ciberseguridad|Síntesis: IA y Ciberseguridad]] — IA
  potencia SIEM/EDR.
