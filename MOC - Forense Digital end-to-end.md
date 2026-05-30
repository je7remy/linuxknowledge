---
tipo: teoria
tags: [moc, forense-digital, dfir, defensa]
actualizado: 2026-05-30
---

# MOC — Forense Digital end-to-end

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Mapa de contenido (MOC)** que organiza el conocimiento del vault sobre
**forense digital y respuesta a incidentes (DFIR)**. A diferencia de
[[MOC - Pentesting end-to-end|Pentesting end-to-end]] (ofensivo), este
MOC es **defensivo**: cómo investigar un incidente _después_ de que ya
ocurrió.

## Las 5 fases del proceso forense

### Fase 1 — Identificación

Detectar que un incidente está ocurriendo o ya ocurrió.

- Alertas de SIEM ([[SIEM EDR y SOC|ver entity page]]).
- Reportes de usuarios.
- Comportamiento anómalo de sistemas.
- Indicadores de Compromiso (IoCs).

### Fase 2 — Preservación

Asegurar que la evidencia no se altera. **Cadena de custodia**.

- **Aislamiento del sistema**: desconectar de red, no apagar (memoria viva).
- **Imágenes forenses**: `dd`, `dcfldd`, FTK Imager, Guymager.
- **Hash de verificación**: MD5 + SHA256 de cada imagen.
- **Documentación**: quién, cuándo, qué, por qué.

### Fase 3 — Recolección de evidencia

Capturar todo lo relevante antes de que cambie.

- **Memoria RAM** (volátil): `volatility`, `LiME`, `winpmem`.
- **Disco** (no volátil): imágenes bit-a-bit.
- **Logs**: `/var/log/`, Event Viewer Windows, logs de aplicación.
- **Tráfico de red**: PCAPs (Wireshark, tcpdump).
- **Metadatos**: ExifTool ([[_2- Extraer Metadatos de imagenes|ver guía]]).

### Fase 4 — Análisis

Reconstruir qué pasó.

- **Análisis temporal**: timeline de eventos (`log2timeline`, `plaso`).
- **Análisis de malware**: si lo hubo (sandbox, reversing).
- **Análisis de tráfico**: PCAPs con Wireshark / NetworkMiner.
- **Análisis de memoria**: volatility plugins (`pslist`, `netscan`, etc.).
- **Análisis de archivos borrados**: carving con `foremost`, `scalpel`.

### Fase 5 — Presentación

Reporte forense para abogados, ejecutivos, autoridades.

- Lenguaje no técnico para no técnicos.
- Cadena de custodia documentada.
- Evidencia validada (hashes consistentes).
- Conclusiones defendibles legalmente.

## Cobertura en el vault

- [[_6- Forense Digital|6- Forense Digital]] — sección completa con:
  - [[1- Investigación de Spear Phishing - Caso Luxury Design JFK|Caso Spear Phishing JFK]]
  - [[2- Introducción Práctica y Demostración|Introducción práctica forense]]
  - [[_3- Caso Practico, Un hacker entró a mi equipo|Caso: Hacker en mi equipo]]
- [[_2- Extraer Metadatos de imagenes|2- Extraer Metadatos de imágenes]] —
  ExifTool para metadata forensics.

## Tipos de forense digital

| Tipo | Foco |
|---|---|
| **Forense de host** | Discos, memoria, registros del SO afectado. |
| **Forense de red** | PCAPs, logs de firewall, IDS/IPS. |
| **Forense móvil** | iOS / Android, apps, almacenamiento. |
| **Forense de cloud** | Logs AWS/Azure/GCP, snapshots, buckets. |
| **Forense de memoria** | Análisis de RAM en vivo o capturada. |
| **Forense de email** | Headers, attachments, phishing. |

## Herramientas clave

### Imaging y preservación

- **FTK Imager** (Windows, gratis) — imágenes forenses + visor.
- **dd / dcfldd** (Linux) — copia bit-a-bit.
- **Guymager** (Linux) — GUI para imágenes.

### Análisis de disco

- **Autopsy** + **Sleuth Kit** — suite open source completa.
- **EnCase** (comercial, estándar legal USA).
- **X-Ways Forensics** (comercial, eficiente).

### Análisis de memoria

- **Volatility** — framework Python para análisis RAM.
- **Rekall** — fork de Volatility.

### Análisis de red

- **Wireshark** — análisis de PCAPs.
- **NetworkMiner** — extracción de archivos desde PCAPs.
- **tshark** — Wireshark CLI.

### Análisis de malware

- **Sandbox**: Cuckoo, Any.Run, Hybrid Analysis.
- **Disassembler**: Ghidra (NSA, gratis), IDA Pro.
- **Debugger**: x64dbg, GDB, WinDbg.

### Línea de tiempo

- **Plaso / log2timeline** — supertimeline de todos los artefactos.
- **Timesketch** — visualización colaborativa de timelines.

## Frameworks y certificaciones

**Frameworks:**

- **NIST SP 800-86** — guía para integrar forense en IR.
- **ISO/IEC 27037** — guidelines para identificación, recolección, preservación.
- **SWGDE** — Scientific Working Group on Digital Evidence.

**Certificaciones:**

- **GIAC GCFA / GCFE** — SANS (la referencia del campo).
- **EnCE** — EnCase Certified Examiner.
- **CHFI** — Computer Hacking Forensic Investigator (EC-Council).
- **CCFP** — (ISC)² Certified Cyber Forensics Professional.

## DFIR vs Pentesting

Ambos usan herramientas similares pero filosofía opuesta:

| Aspecto | Pentesting | DFIR |
|---|---|---|
| **Timing** | Proactivo (antes del ataque) | Reactivo (después) |
| **Foco** | Encontrar vulnerabilidades | Reconstruir lo ocurrido |
| **Output** | Lista de findings + remediación | Timeline + atribución |
| **Stakeholder** | Equipo de seguridad | Legal + ejecutivos + autoridades |
| **Cliente típico** | CISO buscando hardening | CISO post-incident |
| **Notas vault** | [[MOC - Pentesting end-to-end]] | esta nota |

Ver [[Sintesis - Forense vs Pentesting|síntesis comparativa]].

## Aspectos legales

- **Cadena de custodia**: documentación de cada manipulación.
- **Admisibilidad**: la evidencia debe seguir procedimientos validados.
- **Privacidad**: GDPR, HIPAA, LGPD limitan qué se puede examinar.
- **Jurisdicción**: cloud forensics cruza fronteras (problema legal).

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[MOC - Pentesting end-to-end|MOC - Pentesting end-to-end]] — el otro lado.
- [[Sintesis - Forense vs Pentesting|Síntesis: Forense vs Pentesting]] —
  comparativa explícita.
- [[OSINT|OSINT (entity page)]] — OSINT apoya investigaciones forenses.
- [[_6- Forense Digital|6- Forense Digital (carpeta)]] — contenido físico.
