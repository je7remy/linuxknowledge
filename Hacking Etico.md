---
tipo: teoria
tags: [hacking-etico, entity-page, ciberseguridad, etica, legal]
actualizado: 2026-05-30
---

# Hacking Ético

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Entity page** del marco ético y legal que distingue el hacking
**autorizado** del **ilegal**. Esta nota agrupa los principios, los códigos
de conducta, las certificaciones y las consideraciones legales que rigen
toda la actividad ofensiva del vault.

## Definición

**Hacking ético** (también _ethical hacking_, _white hat hacking_) es la
práctica de aplicar técnicas de un atacante **con autorización del dueño**
del sistema target, con el objetivo de **mejorar la seguridad**.

Las técnicas son las mismas que las de un atacante malicioso. Lo que cambia
es:

1. **Autorización formal** previa.
2. **Alcance limitado** acordado.
3. **Intención constructiva** (reporte + remediación).
4. **No exfiltración** de datos reales más allá del PoC.

## Los tres sombreros

| Color | Autorización | Intención |
|---|---|---|
| **White hat** | Sí | Mejorar seguridad |
| **Grey hat** | Ambigua | Encontrar bugs sin pedir permiso (zona gris legal) |
| **Black hat** | No | Daño / lucro ilegal |

El _grey hat_ es problemático: aunque la intención sea buena, sin
autorización es ilegal en la mayoría de jurisdicciones.

## Cobertura en el vault

- [[_3- hacking basico|3- Hacking básico]] — sección entera con teoría
  inicial:
  - [[_1- Teoria de Ciberseguridad|Teoría de Ciberseguridad]] — incluye
    nota sobre qué quieren los hackers, principios éticos, demostrar
    mentalidad de hacking ético.
- [[_4- Hacking Intermedio Teoria|4- Hacking Intermedio]] — Módulos PTS:
  Módulo 1 incluye "Demostrar una mentalidad de hacking ético".
- [[Pentesting|Pentesting (entity page)]] — la aplicación profesional del
  hacking ético.

## Marcos legales (selección)

| Jurisdicción | Ley clave |
|---|---|
| **USA** | Computer Fraud and Abuse Act (CFAA) |
| **EU** | Directiva 2013/40/EU sobre ataques contra sistemas de información |
| **España** | Código Penal Art. 197bis y 264 |
| **México** | Ley Federal de Protección de Datos + Código Penal Federal |
| **República Dominicana** | Ley 53-07 contra Crímenes y Delitos de Alta Tecnología |
| **Argentina** | Ley 26.388 de Delitos Informáticos |
| **Colombia** | Ley 1273/2009 |

**Punto común a todas:** acceso no autorizado a sistemas = delito. Las penas
varían pero típicamente incluyen prisión efectiva.

## Códigos de ética profesionales

- **EC-Council Code of Ethics** (aplica a CEH).
- **(ISC)² Code of Ethics** (aplica a CISSP).
- **OSCP / Offensive Security Code of Ethics**.

Principios comunes:

1. **No divulgar** información del cliente.
2. **Reportar** vulnerabilidades inmediatamente cuando son críticas.
3. **No dañar** sistemas más allá de lo necesario para el PoC.
4. **No usar** conocimiento profesional para fines ilegales.
5. **Mantener competencia** mediante formación continua.

## Bug bounty — versión legal del grey hat

Programas donde la empresa **autoriza explícitamente** la búsqueda de
vulnerabilidades, con scope y reward definidos.

- **HackerOne**, **Bugcrowd**, **Intigriti** — plataformas principales.
- Cada programa publica reglas, scope, rewards, exclusiones.
- Reporte vía la plataforma, NO vía contacto directo a la empresa.

Bug bounty es como pentesting pero "abierto al mundo" — cualquiera puede
participar dentro del scope publicado.

## Documentos típicos en un engagement

- **Statement of Work (SoW)** — qué se va a hacer.
- **Rules of Engagement (RoE)** — cómo se va a hacer.
- **Letter of Authorization (LoA)** — autorización explícita por escrito.
- **NDA (Non-Disclosure Agreement)** — confidencialidad.
- **Master Service Agreement (MSA)** — marco contractual general.

## Diferencia con Red Team / Blue Team / Purple Team

| Team | Rol |
|---|---|
| **Red Team** | Simula atacantes reales, evasión incluida, scope amplio. |
| **Blue Team** | Defensores. Monitorean, responden, hardening. |
| **Purple Team** | Colaboración Red ↔ Blue para mejorar detección. |
| **Pentester** | Subset del Red Team con scope más acotado y tiempo limitado. |

## Carrera profesional

Roles típicos (entry → senior):

1. **SOC Analyst** (defensa, entry).
2. **Junior Pentester** (ofensiva, entry) — equivalente a [[MOC - Camino al eJPTv2|eJPTv2 holder]].
3. **Senior Pentester / Red Teamer**.
4. **Security Consultant / Architect**.
5. **CISO** (management).

[[_0- Cómo PREPARAR una ENTREVISTA TÉCNICA para un Puesto de CIBERSEGURIDAD|Guía de entrevista técnica]]
del vault cubre conceptos clave para entrevistas (SIEM, EDR, Kerberos, AD,
APT, C2, MITRE ATT&CK).

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Pentesting|Pentesting (entity page)]] — la práctica concreta del
  hacking ético.
- [[OSINT|OSINT (entity page)]] — recolección de información dentro del
  marco ético.
- [[MOC - Pentesting end-to-end|MOC - Pentesting end-to-end]] — metodología
  profesional.
- [[_0- Cómo PREPARAR una ENTREVISTA TÉCNICA para un Puesto de CIBERSEGURIDAD|Entrevista técnica ciberseguridad]]
  — preparación para roles del campo.
