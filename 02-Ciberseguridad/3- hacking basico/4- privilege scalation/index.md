---
tipo: indice
seccion: 02-Ciberseguridad/3- hacking basico/4- privilege scalation
actualizado: 2026-05-28
---

# 4 — Escalación de Privilegios

Métodos para escalar de un usuario sin privilegios (típicamente `www-data` o
similar tras un RCE inicial) hasta `root` (Linux) o `SYSTEM` (Windows).
Cubre checklists, scripts de enumeración (LinPEAS, WinPEAS), kernel exploits,
binarios SUID/sudo, cron jobs, credenciales expuestas, claves SSH y hijacking
de Python.

## Contenido

- [[1- privilege scalation basic]] — Visión general: PEASS/LinPEAS, kernel exploits, sudo/SUID, GTFOBins/LOLBAS, cron jobs, credenciales, claves SSH.
- [[2- python hijacking]] — Hijacking del path de Python para escalar privilegios.

## Navegación

- ⬆️ Carpeta: [[../index|3- hacking basico]]
- 🏠 Sección: [[../../index|02-Ciberseguridad]]

## Relacionadas

- [[../3- hosts/index|3- hosts]] — la fase previa: acceso inicial a un host.
- [[../5- shells/index|5- Shells]] — el shell que se usa para enumerar y escalar.
- [[../../5- Reconocimiento/1- Nmap/index|5- Reconocimiento → Nmap]] — versión de SO obtenida con `-O` informa qué kernel exploits buscar.
- [[../../../01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/1- Curso de Linux y Bash Scripting/2- Gestión de Permisos y Tratamiento de la Información/9- Permisos Especiales – BIt SUID|SUID en Bash]] — fundamentos teóricos del bit SUID.
