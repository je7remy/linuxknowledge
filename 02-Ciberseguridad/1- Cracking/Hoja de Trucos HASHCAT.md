---
tipo: cheatsheet
tags: [hashcat, password-cracking, md5, ntlm, dictionary-attack, brute-force]
actualizado: 2026-05-28
---

# Hoja de Trucos HASHCAT

#Hashcat #CyberSecurity #PasswordCracking #EthicalHacking #InfoSec #Pentesting #HackingÉtico #MD5 #NTLM #BruteForce #DictionaryAttack #CyberDefense #SecurityTools #CrackingHashes #RedTeam #CyberAttack #Forensics #Linux #SysAdmin #SecurityTesting #HackThePlanet

---

| Comando                 | Propósito                                            |
| ----------------------- | ---------------------------------------------------- |
| **hashcat**             | El programa que estamos usando                       |
| **-m 0**                | Define el tipo de hash (MD5)                         |
| **-a 0**                | Configura hashcat para usar un ataque de diccionario |
| **--show**              | Mostrará los hashes crackeados                       |
| **../md5-hashes-2.txt** | Ruta al archivo que contiene los hashes              |
| **../wordlist.txt**     | Ruta a la lista de palabras                          |

- `   -m 1000`: Esto define el tipo de hash que se utilizará. En este caso, `1000` representa el tipo de hash NTLM.
- `-a 0`: Configura hashcat para utilizar un ataque de diccionario. El valor `0` indica que se utilizará un ataque de diccionario.
- `--show`: Esta opción indica a hashcat que muestre los hashes descifrados.
- `../password-hashes`: Es la ruta al archivo que contiene los hashes que quieres descifrar.
- `../wordlist-intro.txt`: Es la ruta al archivo de la lista de palabras que hashcat utilizará como diccionario para intentar descifrar las contraseñas.

---

## Navegación

- ⬆️ Sección: [[_02-Ciberseguridad|02-Ciberseguridad]]

## Relacionadas

- [[12- Herramienta para hacer cracking de contraseñas]] — laboratorio aplicado en Bash.
- [[13- Automatización de Cracking de Contraseñas]] — pipeline automatizado.
- [[../3- hacking basico/1- Teoria de Ciberseguridad/4- Tiempos de craqueo|Cisco → Tiempos craqueo]] — teoría del cracking.
- [[../3- hacking basico/3- hosts/2- IPMI|02 → IPMI]] — Hashcat modo 7300 para hashes IPMI RAKP.
- [[../3- hacking basico/3- hosts/9- SMB|02 → SMB]] — Hashcat para hashes NTLM extraídos por impacket-ntlmrelayx.
- [[../../01-Sistemas-Operativos/Windows/7- Activie Directory/2- Tools|AD → Tools]] — Kerberoasting/ASREPRoasting + Hashcat.



  **[[12- Herramienta para hacer cracking de contraseñas]]**
  **[[13- Automatización de Cracking de Contraseñas]]**