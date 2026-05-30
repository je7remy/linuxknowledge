---
tipo: cheatsheet
tags: [privilege-escalation, linpeas, sudo, ssh-keys]
actualizado: 2026-05-28
---

# Escalada de Privilegios — Cheatsheet

#privilegeescalation #comandos 

--------

|   |   |
|---|---|
|**Escalada de privilegios**||
|`./linpeas.sh`|Ejecutar script para enumerar el servidor remoto`linpeas`|
|`sudo -l`|Enumerar los privilegios disponibles`sudo`|
|`sudo -u user /bin/echo Hello World!`|Ejecute un comando con `sudo`|
|`sudo su -`|Cambiar a usuario root (si tenemos acceso a `sudo su`)|
|`sudo su user -`|Cambiar a un usuario (si tenemos acceso a `sudo su`)|
|`ssh-keygen -f key`|Crear una nueva clave SSH|
|`echo "ssh-rsa AAAAB...SNIP...M= user@parrot" >> /root/.ssh/authorized_keys`|Agregar la clave pública generada al usuario|
|`ssh root@10.10.10.10 -i key`|SSH al servidor con la clave privada generada|

---

## Navegación

- ⬆️ Carpeta: [[index|2- basico]]
- ⬅️ Anterior: [[1- basic tools]]
- ➡️ Siguiente: [[3- hoja de trucos de METASPLOIT]]

## Relacionadas

- [[1- privilege scalation basic]] — explicación detallada de cada comando de este cheatsheet.
- [[2- python hijacking]] — vector específico de Python.
- [[../4- privilege scalation/index|4- privesc]] — la sección dedicada a este tema.
- [[0- Comandos de Hacking]] — versión más extensa con explicación.
