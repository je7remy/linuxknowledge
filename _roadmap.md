---
tipo: indice
seccion: vault-root
actualizado: 2026-05-30
---

# Roadmap — Pendientes del Vault

🏠 [[🔒🐧Hub|Hub Principal del vault]]

Inventario único de **lo que falta** por escribir o completar en el vault.
Lo que aquí aparece es contenido conocido como incompleto: cursos pendientes,
notas-placeholder, laboratorios sin desarrollar, módulos en construcción.

> **Cómo se usa:** cuando termines de aprender/escribir uno de estos items,
> elimínalo de aquí y muévelo al log con `## [YYYY-MM-DD] ingest | Título`.
> Cuando descubras nuevo contenido pendiente, apúntalo aquí.

## Cursos completos pendientes (alto esfuerzo)

- [ ] **[[_2- CompTIA Security+ (SY0-701) Complete Course & Exam|CompTIA Security+ SY0-701]]** —
  Curso completo sin desarrollar (carpeta `01- Introduction` con 1 nota,
  resto vacío). Decisión: ¿se aborda o se aparca?
- [ ] **[[_4- Preparación para la Certificación del eJPTv2|4- Preparación final eJPTv2]]** —
  Solo `Proximamente....md`. Pendiente material de revisión final pre-examen.
- [ ] **[[_5- Curso de Docker Aplicado a la Ciberseguridad|5- Docker para Ciberseguridad]]** —
  Solo `Proximamente....md`. Pendiente curso completo de Docker aplicado a
  pentesting/análisis de malware.
- [ ] **[[_6- Introducción al Hacking Web|6- Introducción al Hacking Web]]** —
  Solo `Proximamente....md`. Pendiente OWASP Top 10, SQLi, XSS, CSRF.

## Módulos en desarrollo (esfuerzo medio)

- [ ] **[[_10- Securización de Servidores Linux (EN DESARROLLO)|10- Securización de Servidores Linux]]** —
  Marcado "EN DESARROLLO" en el título. Pendiente: hardening SSH, fail2ban,
  AppArmor/SELinux, auditd, rkhunter.
- [ ] **[[_15- Scapy (En desarrollo)|15- Scapy]]** —
  Solo 2 notas (Conceptos Introductorios + Uso Básico). Pendiente:
  interceptar credenciales, ARP spoofing, DNS spoofing, MITM con Scapy.

## Laboratorios sin desarrollar (esfuerzo medio)

- [ ] **[[_04-Laboratorios|04-Laboratorios]] → `2- Laboratorios de Python`** —
  Solo "Proximamente...". Pendiente: equivalentes en Python de los labs de
  Bash (detector SO, fuzzing web, análisis red, backup automatizado).
- [ ] **[[_04-Laboratorios|04-Laboratorios]] → `3- Laboratorios de Herramientas`** —
  Solo "Proximamente...". Pendiente: labs con Nmap avanzado, Burp Suite,
  Wireshark, Metasploit, Hashcat.

## Tesis universitaria (esfuerzo alto, contenido propio)

Proyecto SGCM (Sistema de Gestión de Citas Médicas):

- [ ] **[[_5- Guia Completa de Tesis|5- Guía completa de tesis]]** —
  Carpeta vacía. Pendiente: manual de redacción (intro, marco teórico,
  metodología, resultados, conclusiones).
- [ ] **[[_3- Documentos de Word|3- Documentos de Word]]** —
  Solo `Proximamente....md`. Pendiente: documentos editables originales
  (defensa, presentación PowerPoint, etc.).

## Recursos / Cheatsheets pendientes (esfuerzo bajo)

- [ ] **[[_Excel|Excel]]** — Stub con secciones pendientes (atajos, fórmulas,
  tablas dinámicas, funciones de texto, funciones lógicas).
- [ ] Notas "Conclusión", "Recapitulación", "Resumen del curso" del curso
  Google Cybersecurity — varias marcadas como "_(pendiente)_" o vacías.

## Contenido conector cross-dominio (esfuerzo medio)

Notas-síntesis que conectarían múltiples dominios y aún no existen:

- [ ] **`MOC - Camino al eJPTv2`** — Ruta de aprendizaje (Linux básico →
  Bash → Python → Nmap → Metasploit → Hashcat → labs prácticos → examen).
  _(creado en esta sesión, ver [[MOC - Camino al eJPTv2]])_
- [ ] **`MOC - Pentesting end-to-end`** — Reconocimiento → Escaneo →
  Enumeración → Explotación → Post-explotación → Privilege escalation →
  Reporte. _(creado, ver [[MOC - Pentesting end-to-end]])_
- [ ] **`MOC - Python para Ciberseguridad`** — Fundamentos Python +
  bibliotecas (Scapy, requests, paramiko) + criptografía + scripts ofensivos.
  _(creado, ver [[MOC - Python para Ciberseguridad]])_

## Mejoras estructurales pendientes (opcionales)

- [ ] Dataview queries adicionales en indexes que aún no las usan.
- [ ] Glosario con wikilinks salientes a las notas detalladas (piloto hecho;
  expandir a los 200 términos).
- [ ] Plugin Templater configurado en Obsidian (ya hay plantillas en
  [[_templates|templates/]] listas para usar).

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[log|Bitácora]] — lo que ya está hecho (cronológico).
- [[index|Index]] — catálogo del contenido actual.
- [[CLAUDE|Instrucciones operativas]] — cómo el LLM debe procesar nuevos
  ingests para tachar items de esta lista.
