---
tipo: teoria
tags: [moc, python, ciberseguridad, scripting]
actualizado: 2026-05-30
---

# MOC — Python para Ciberseguridad

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Mapa de contenido (MOC)** que organiza el conocimiento del vault sobre
Python aplicado a ciberseguridad — cross-dominio entre fundamentos del
lenguaje, scripts ofensivos, criptografía y forense.

## Capa 1 — Fundamentos del lenguaje

Antes de escribir scripts ofensivos, dominar Python básico.

- [[_Fundamentos de Python|Fundamentos de Python]] — guía rápida de
  sintaxis y patrones.
- [[_Microsoft Reactor Python + IA|Microsoft Reactor Python + IA]] —
  taller con énfasis en uso responsable.

## Capa 2 — Python aplicado a Ciberseguridad

El curso central del vault.

- [[_2- Curso de Python Aplicado a la Ciberseguridad|2- Curso de Python para Ciberseguridad]] —
  16 módulos:
  1. Conceptos previos — entornos virtuales, REPL, IDE.
  2. Sintaxis avanzada — list comprehensions, generators, decoradores.
  3. Funciones avanzadas — `*args`, `**kwargs`, lambdas.
  4. Gestión de bases de datos desde Python — SQLite, MySQL.
  5. Procesamiento de archivos — open, pickle, JSON, CSV, XML.
  6. Manejo de excepciones — try/except/finally, custom exceptions.
  7. Gestión automática de servidores — paramiko (SSH), fabric.
  8. Web scraping — requests, BeautifulSoup, Selenium.
  9. APIs REST — consumir y exponer endpoints.
  10. Hilos y procesos — threading, multiprocessing, asyncio.
  11. Sockets — TCP/UDP, cliente/servidor.
  12. Scapy básico — manipulación de paquetes (introducción).
  13. PyQt — GUIs para herramientas.
  14. Empaquetado — pyinstaller, cx_Freeze.
  15. **Scapy** — interceptar credenciales, ARP/DNS spoofing _(pendiente)_.

## Capa 3 — Criptografía

- [[_7- Cifrado y Criptografía en Python|7- Cifrado y Criptografía en Python]] —
  César, Vigenère, RSA, AES, hashing (MD5, SHA), HMAC, JWT.

## Capa 4 — Forense digital con Python

- [[_6- Forense Digital|6- Forense Digital]] — casos prácticos donde Python
  ayuda en:
  - **ExifTool / Pillow** — extracción de metadatos de imágenes
    ([[_2- Extraer Metadatos de imagenes|ver guía]]).
  - **pyshark / Scapy** — análisis de PCAPs.
  - **volatility** — análisis de memoria.

## Bibliotecas clave por dominio

| Dominio | Bibliotecas |
|---|---|
| Networking | `socket`, `scapy`, `pyshark`, `requests`, `paramiko` |
| Criptografía | `cryptography`, `pycryptodome`, `hashlib`, `hmac` |
| Web scraping | `requests`, `beautifulsoup4`, `selenium`, `playwright` |
| Forense | `pillow`, `exifread`, `volatility`, `pyshark` |
| Automatización | `paramiko`, `fabric`, `pexpect`, `subprocess` |
| Bases de datos | `sqlite3`, `pymysql`, `psycopg2`, `sqlalchemy` |
| Análisis binario | `pwntools`, `capstone`, `pefile`, `lief` |

## Scripts ofensivos típicos (proyecto de aprendizaje)

Cada uno como ejercicio dentro del curso o como lab independiente:

1. **Port scanner básico** — sockets puros.
2. **HTTP fuzzer** — requests + diccionario de paths.
3. **Banner grabber** — sockets + parseo.
4. **Reverse shell** — sockets + subprocess.
5. **Cracker de contraseñas hash** — hashlib + diccionario.
6. **Sniffer de red** — Scapy.
7. **ARP spoofer** — Scapy.
8. **DNS spoofer** — Scapy.
9. **Keylogger** — pynput (uso ético).
10. **Análisis de PCAPs** — pyshark.

## Comparación: Python vs Bash para tareas ofensivas

| Tarea | Bash | Python |
|---|---|---|
| Scripts de una línea | ✅ ideal | overkill |
| Manipulación de archivos rápida | ✅ | ✅ |
| Paralelismo / async | limitado | ✅ ideal |
| Manipulación de paquetes red | limitado (tcpdump) | ✅ Scapy |
| GUIs | no aplica | ✅ PyQt |
| Procesamiento estructurado (JSON/XML) | difícil | ✅ ideal |
| Portabilidad cross-OS | unix only | ✅ multiplataforma |

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[MOC - Pentesting end-to-end|MOC - Pentesting end-to-end]] — cómo
  Python encaja en cada fase del pentest.
- [[MOC - Camino al eJPTv2|MOC - Camino al eJPTv2]] — Python como
  pre-requisito del examen.
- [[Sintesis - Python vs Bash en pentesting|Síntesis: Python vs Bash en pentesting]] —
  cuándo usar cada lenguaje.
- [[_Fundamentos de Python|Fundamentos de Python (cheatsheet)]] — referencia
  rápida de sintaxis.
