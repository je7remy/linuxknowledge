---
tipo: indice
seccion: 02-Ciberseguridad/3- hacking basico/5- shells
actualizado: 2026-05-28
---

# 5 — Shells

Tres tipos fundamentales de shell para mantener acceso a un host
comprometido tras un RCE inicial: **Reverse Shell** (el host se conecta
a nosotros), **Bind Shell** (escuchamos en el host comprometido), y
**Web Shell** (script PHP/ASP/JSP que ejecuta comandos vía HTTP).
Incluye técnicas de upgrade de TTY para shells interactivos completos.

## Contenido

- [[1- basic shells]] — Cheatsheet rápido de comandos: netcat listener, reverse shells (bash, mkfifo), bind shells, webshell PHP, upgrade TTY.
- [[2- tipos de shell]] — Teoría completa: Reverse vs Bind vs Web shell, ejemplos en Bash/Python/PowerShell, upgrade TTY paso a paso.

## Navegación

- ⬆️ Carpeta: [[_3- hacking basico|3- hacking basico]]
- 🏠 Sección: [[_02-Ciberseguridad|02-Ciberseguridad]]

## Relacionadas

- [[_3- hosts|3- hosts]] — protocolos sobre los que se inicia el shell.
- [[_4- privilege scalation|4- Escalación de privilegios]] — siguiente paso una vez con shell estable.
- [[../6- Web/1- Protocolo HTTP|6- Web → HTTP]] — vector del Web Shell.
- [[_14- Sockets|Python → 14- Sockets]] — implementar shells en Python con sockets.
- [[../../../01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/2- Curso de Python Aplicado a la Ciberseguridad/8- Interacción con Servicios Web/11- Automatización Reverse Shell Groovy Script en Jenkins – PARTE 1|Reverse Shell en Jenkins]] — caso aplicado real.
