---
tipo: teoria
tags: [ejptv2, moc, pentesting, ruta-aprendizaje]
actualizado: 2026-05-30
---

# MOC — Camino al eJPTv2

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Mapa de contenido (MOC)** que organiza el aprendizaje progresivo hacia la
certificación **eLearnSecurity Junior Penetration Tester v2**. A diferencia
de un index de carpeta (organiza por jerarquía física), este MOC organiza
por **ruta de aprendizaje cross-dominio**: el orden recomendado para llegar
al examen desde cero.

## Pre-requisitos (orden secuencial)

### 1. Fundamentos de Linux

- [[_1- Uso Básico de Linux|1- Uso básico de Linux]] — comandos esenciales,
  navegación, manipulación de archivos.
- [[_2- Gestión de Permisos y Tratamiento de la Información|2- Permisos y tratamiento de información]]
- [[_3- Las Variables y Procesamiento de la Información|3- Variables y procesamiento]]

### 2. Bash scripting

- [[_4- Sentencias Condicionales|4- IF, ELIF, ELSE]]
- [[_5- Bucles|5- FOR, WHILE, UNTIL]]
- [[_6- Funciones|6- Funciones en Bash]]
- [[_7- Colores en mi Script|7- Colores en scripts]]
- [[_8- Gestión de Servidores con Scripts de Bash|8- Gestión de servidores con Bash]]
- [[_9- Ejercicios Prácticos|9- Ejercicios prácticos]] — detector SO, fuzzing web,
  backup SSH, análisis de red. Punto de inflexión: aplicas Bash a contextos
  reales de pentesting.

### 3. Python aplicado

- [[_2- Curso de Python Aplicado a la Ciberseguridad|2- Python para Ciberseguridad]] —
  módulo completo: I/O archivos, automatización, sockets, scripts ofensivos.
- [[_7- Cifrado y Criptografía en Python|7- Cifrado y Criptografía en Python]] —
  algoritmos clásicos y modernos.

## Metodología pentesting

### 4. Teoría hacking básico/intermedio

- [[_3- hacking basico|3- Hacking básico]] — teoría inicial: tipos de hackers,
  metodologías, hosts.
- [[_4- Hacking Intermedio Teoria|4- Hacking Intermedio Teoría]] — Módulos
  PTS (Penetration Testing Student) basados en eJPTv2.

### 5. Reconocimiento (la primera fase de cualquier pentest)

- [[_5- Reconocimiento|5- Reconocimiento]] — la sección entera.
- [[_1- Nmap|Nmap]] — herramienta principal de escaneo de red.
- [[_2- Shodan|Shodan]] — buscador de dispositivos expuestos.

### 6. Hosts y servicios

- [[_3- hosts|3- Hosts]] — enumeración de servicios.
- Subdominios: FTP, SSH, HTTP, SMB, MSSQL — cada uno con sus técnicas.

### 7. Privilege escalation

- [[_4- privilege scalation|4- Privilege Escalation]] — sección entera.
- Linux: SUID, sudo misconfig, cron jobs.
- Windows: services, registry, tokens.

## Examen y entrevista

### 8. Preparación final

- [[_0- Cómo PREPARAR una ENTREVISTA TÉCNICA para un Puesto de CIBERSEGURIDAD|0- Entrevista técnica de ciberseguridad]] —
  Conceptos clave: SIEM, EDR, Kerberos, AD, APT, C2, MITRE ATT&CK.
- [[_4- Preparación para la Certificación del eJPTv2|4- Preparación final eJPTv2]] —
  _(pendiente — ver [[_roadmap]])_.

## Laboratorios prácticos

- [[_04-Laboratorios|04-Laboratorios]] — el catálogo central.
- [[1- Laboratorios de Bash|1- Labs de Bash]] — completos (4 scripts
  reales).
- [[2- Laboratorios de Python|2- Labs de Python]] — _(pendiente)_.
- [[3- Laboratorios de Herramientas|3- Labs de Herramientas]] — _(pendiente)_.

## Plataformas para practicar

- **HackTheBox** — máquinas vulnerables CTF-style.
- **TryHackMe** — rooms guiadas (más amigable para principiantes).
- **VulnHub** — VMs descargables offline.

## Tiempo estimado de preparación

- **Fundamentos Linux + Bash**: 2-4 semanas dedicación constante.
- **Python para ciberseguridad**: 3-4 semanas.
- **Teoría hacking + Recon + Hosts**: 4-6 semanas.
- **Labs reales (HTB/THM)**: 4-8 semanas (clave para aprobar).
- **Total estimado**: 3-5 meses con dedicación de tarde + fines de semana.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[MOC - Pentesting end-to-end|MOC - Pentesting end-to-end]] — la
  metodología que se aplica en el examen.
- [[MOC - Python para Ciberseguridad|MOC - Python para Ciberseguridad]] —
  detalle de la pieza Python del camino.
- [[_3- Preparación para la Certificación del eJPTv2|3- Preparación eJPTv2 (carpeta)]] —
  contenido físico de los cursos.
