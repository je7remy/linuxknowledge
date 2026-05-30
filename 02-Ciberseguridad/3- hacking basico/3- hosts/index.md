---
tipo: indice
seccion: 02-Ciberseguridad/3- hacking basico/3- hosts
actualizado: 2026-05-28
---

# 3 — Hosts (servicios por protocolo)

Catálogo de **12 protocolos comunes en hosts**, organizados como cheatsheets
de pentesting: configuración por defecto, configuraciones peligrosas,
huella del servicio (Nmap NSE) y vectores de explotación.
Material derivado mayoritariamente de HackTheBox Academy.

## Contenido

- [[1- FTP]] — File Transfer Protocol (puerto 21) + TFTP (UDP 69) + vsFTPd, anonymous login.
- [[2- IPMI]] — Intelligent Platform Management Interface (UDP 623), BMC, fallo RAKP IPMI 2.0.
- [[3- Ldap]] — LDAP _(stub)_.
- [[4- MSSQL]] — Microsoft SQL Server (TCP 1433), `mssqlclient.py`, Impacket.
- [[5- MySQL]] — MySQL (TCP 3306), enumeración y conexión.
- [[6- NFS]] — Network File System (TCP/UDP 111/2049), montaje, `showmount`.
- [[7- Oracle TNS]] — Oracle Database (TCP 1521), `odat.py`, sqlplus, SID brute.
- [[8- RDP]] — Remote Desktop Protocol (TCP 3389) — cheatsheet rápido de ataques.
- [[9- SMB]] — Server Message Block — cheatsheet de smbclient/smbmap/impacket.
- [[10- SNMP]] — Simple Network Management Protocol (UDP 161), snmpwalk, onesixtyone, braa.
- [[11- SSH]] — OpenSSH + Rsync + R-services (rlogin, rsh, rwho).
- [[12- Windows Hosts]] — RDP + WinRM + WMI (admin remoto Windows).

## Navegación

- ⬆️ Carpeta: [[../index|3- hacking basico]]
- 🏠 Sección: [[../../index|02-Ciberseguridad]]

## Relacionadas

- [[../../5- Reconocimiento/1- Nmap/index|5- Reconocimiento → Nmap]] — herramienta usada para huella en cada nota.
- [[../1- Teoria de Ciberseguridad/index|1- Teoría de Ciberseguridad]] — base conceptual.
- [[../4- privilege scalation/index|4- Escalación de privilegios]] — paso siguiente tras obtener acceso al host.
- [[../5- shells/index|5- Shells]] — establecer shell tras explotación.
- [[../../../01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/2- Curso de Python Aplicado a la Ciberseguridad/4- Gestión de Bases de Datos desde Python/index|Python → 4- Bases de Datos]] — automatización Python sobre MySQL/MSSQL/Oracle.
- [[../../../01-Sistemas-Operativos/Windows/7- Activie Directory/index|Active Directory]] — explotación combinada de SMB/RDP/WinRM en AD.
