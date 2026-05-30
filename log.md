---
tipo: log
actualizado: 2026-05-28
---

## 2026-05-28 — Sesión de cross-references en dominios densos (109 archivos)

**`02-Ciberseguridad` completamente procesada.**
**`01-Sistemas-Operativos` completamente procesada.**

Último bloque añadido:
- 5 notas planas restantes de 02-Ciberseguridad (entrevista, Hashcat, ExifTool, Fernet, Fortinet/IA).
- Shodan + Geolocalización IPs (5- Reconocimiento) — completando esa subsección.
- 6 notas planas de Windows (UAC bypass, descargar ISO, Office Lite, MAS, Apps Android, Chromebook).
- Índices padre creados: `Linux/index.md` y `Windows/index.md`.
- Correcciones a `02-Ciberseguridad/index.md` y `5- Reconocimiento/index.md` para apuntar a archivos directos en lugar de índices inexistentes.

`02-Ciberseguridad/3- hacking basico/` y `02-Ciberseguridad/4- Hacking Intermedio Teoria/`
quedan completamente procesados.

**Nuevo bloque (Hacking Intermedio Teoria, 24 archivos):**
- [[02-Ciberseguridad/4- Hacking Intermedio Teoria/Módulo 1 Introducción al Hacking Ético y a las Pruebas de Penetración/index|Módulo 1]] — Introducción al Hacking Ético (9 notas + index): definiciones, actores, justificación, metodologías (MITRE ATT&CK, OWASP, OSSTMM, PTES, NIST 800-115, ISSAF), laboratorio.
- [[02-Ciberseguridad/4- Hacking Intermedio Teoria/Módulo 2 Planificación y Alcance de una Evaluación de Pruebas de Penetración/index|Módulo 2]] — Planificación y Alcance (8 notas + index): GRC, contratos, ética profesional, código de conducta personal.
- [[02-Ciberseguridad/4- Hacking Intermedio Teoria/Módulo 3 Recopilación de información y análisis de vulnerabilidades/index|Módulo 3]] — Recopilación de información (4 notas + index): reconocimiento activo/pasivo, OSINT con SpiderFoot.

Aplicado el patrón completo (frontmatter + Navegación + Relacionadas) a **44 archivos**
en cinco dominios de 02-Ciberseguridad y el curso HackTheBox del eJPTv2.

**Dominios procesados:**
- [[02-Ciberseguridad/5- Reconocimiento/1- Nmap/index|Nmap]] (7 archivos) — piloto del patrón.
- [[01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/7- HackTheBox/index|HackTheBox]] (7 archivos).
- [[02-Ciberseguridad/3- hacking basico/3- hosts/index|3- hosts]] (13 archivos — 12 protocolos + index): FTP, IPMI, LDAP, MSSQL, MySQL, NFS, Oracle TNS, RDP, SMB, SNMP, SSH, Windows Hosts.
- [[02-Ciberseguridad/3- hacking basico/4- privilege scalation/index|privesc]] + [[02-Ciberseguridad/3- hacking basico/5- shells/index|shells]] + Web (7 archivos).
- [[02-Ciberseguridad/6- Forense Digital/index|Forense Digital]] (4 archivos).
- [[02-Ciberseguridad/3- hacking basico/2- basico/index|2- basico]] (6 archivos).
- [[01-Sistemas-Operativos/Windows/7- Activie Directory/index|7- Active Directory]] (3 archivos): OSINT teórico, catálogo de Tools, guía práctica de OSINT sobre personas.

**Cross-references más densas que aparecieron:**
- hosts ↔ Nmap (cada protocolo enlaza al cheatsheet/scripts NSE correspondiente).
- hosts ↔ Linux/Bash y Python (servidores FTP/SSH/MySQL desde ambas perspectivas).
- shells ↔ Python/Sockets ↔ privesc ↔ Web (cadena ofensiva completa).
- Forense Digital ↔ Python/Defensiva ↔ Google/Detección y Respuesta.
- 2- basico/4- Metasploit ↔ 3- hosts (cada protocolo usa módulos MSF).

**Pendiente significativo:**
- [[02-Ciberseguridad/3- hacking basico/1- Teoria de Ciberseguridad|1- Teoría de Ciberseguridad]] (15 notas, no procesado).
- [[02-Ciberseguridad/4- Hacking Intermedio Teoria/index|4- Hacking Intermedio]] (3 módulos × varias lecciones).
- [[02-Ciberseguridad/5- Reconocimiento/2- Shodan]] y `3- Geolocalización`.
- Notas planas en `02/0`, `02/1`, `02/2`, `02/7`, `02/8`.
- Notas planas en `01-Sistemas-Operativos/Windows/{0,1,2,3,4,5,6}` (1 archivo cada una).
- Cursos completos de Google Cybersecurity y de IA.
- `03-Desarrollo` (tesis, BBDD, proyecto web).
- `05-Recursos` (guías rápidas).


# Bitácora del Vault

Cambios significativos del vault en orden cronológico inverso.
No reemplaza al historial git: solo entradas que vale la pena recordar
(nuevas secciones, reorganizaciones, hitos de estudio, publicaciones).

Formato: `## YYYY-MM-DD — Título corto` + descripción de 1-3 líneas con enlaces `[[...]]`.

---

## 2026-05-28 — Cobertura de índices hasta nivel 4 (eJPTv2)

Generados **65 `index.md`** adicionales en cuatro rondas, completando la
estructura navegable del vault hasta el nivel 4 en las ramas más densas:

- **Nivel 1 (7):** índices raíz de cada sección numerada.
- **Nivel 2 (19):** subcarpetas con ≥2 archivos o subdirs con contenido.
- **Nivel 3 (14):** dentro de [[01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/index|El Hacker Legendario]]
  (Google Cybersecurity ×8, CompTIA ×1, eJPTv2 ×5).
- **Nivel 4 (25):** módulos del curso de [[01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/1- Curso de Linux y Bash Scripting/index|Linux y Bash Scripting]]
  (×10) y [[01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/2- Curso de Python Aplicado a la Ciberseguridad/index|Python para Ciberseguridad]] (×15).

**Cross-references introducidas (parejas más importantes):**
Bash↔Python en módulos paralelos (uso básico, colores/estética, gestión
de servidores, defensiva); eJPTv2 → [[02-Ciberseguridad/index|02-Ciberseguridad]]
(cracking, privesc, web, shells); eJPTv2 → [[04-Laboratorios/index|04-Laboratorios]]
(scripts curados como vitrina); Google Cybersecurity → eJPTv2 cuando hay curso paralelo.

**Inconsistencia detectada:** la carpeta `eJPTv2/3- Curso de Splunk Introductorio`
contiene una subcarpeta llamada `1- Conceptos Básicos de Docker`. Marcada como
`⚠️ revisar` en el índice correspondiente; podría ser un movimiento erróneo
desde `5- Curso de Docker`.

**Pendiente:** nivel 4+ en Google Cybersecurity (~33), nivel 3 en
`02-Ciberseguridad/3- hacking basico` y `5- Reconocimiento`, módulos de
cursos de IA. Y lo más importante: empezar a poblar las notas existentes
con enlaces `[[...]]` — los índices son andamiaje; el grafo real lo construyen
los enlaces dentro de las notas.

## 2026-05-28 — Adopción del patrón wiki estilo Karpathy

Se introducen tres artefactos base para tratar el vault como un wiki vivo
en lugar de una jerarquía de carpetas: [[schema]] (convenciones del vault),
[[log]] (este archivo) e índices `index.md` por sección.

Motivación: gist de Karpathy sobre LLM-maintained wikis
(https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).
Pendiente: poblar los 7 `index.md` y empezar a añadir cross-references
`[[...]]` en notas existentes.
