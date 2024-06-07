
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