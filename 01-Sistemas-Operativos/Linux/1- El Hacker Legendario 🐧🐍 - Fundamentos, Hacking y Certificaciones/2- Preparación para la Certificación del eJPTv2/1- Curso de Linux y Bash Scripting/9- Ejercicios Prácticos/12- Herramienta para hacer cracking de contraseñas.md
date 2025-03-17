
---

#Hashcat #CyberSecurity #PasswordCracking #EthicalHacking #InfoSec #Pentesting #HackingÉtico #MD5 #NTLM #BruteForce #DictionaryAttack #CyberDefense #SecurityTools #CrackingHashes #RedTeam #CyberAttack #Forensics #Linux #SysAdmin #SecurityTesting #HackThePlanet #HashBreaking #PenetrationTesting #CTF #CyberSecCommunity

---
### **1. Recuperación de contraseñas de archivos ZIP**

#### **Generar el hash del archivo ZIP**

```bash
zip2john archivo.zip > hash
```

📌 _Explicación:_

- `zip2john` extrae el hash del archivo ZIP protegido por contraseña y lo guarda en el archivo `hash`.

#### **Romper la contraseña con John the Ripper**

```bash
john --wordlist=rockyou.txt hash
```

📌 _Explicación:_

- `--wordlist=rockyou.txt` especifica la lista de palabras RockYou para intentar descifrar la contraseña.
- `hash` es el archivo que contiene el hash del ZIP.

#### **Mostrar la contraseña encontrada**

```bash
john --show hash
```

📌 _Explicación:_

- Muestra la contraseña recuperada si John the Ripper tuvo éxito.

---

### **2. Recuperación de contraseñas de una base de datos KeePass (.kdbx)**

#### **Generar el hash del archivo KeePass**

```bash
keepass2john database.kdbx > hash1
```

📌 _Explicación:_

- `keepass2john` convierte el archivo KeePass en un formato que John the Ripper puede entender.

#### **Romper la contraseña con John the Ripper**

```bash
john --wordlist=rockyou.txt hash1
```

📌 _Explicación:_

- Intenta descifrar la contraseña con el diccionario RockYou.

#### **Mostrar la contraseña encontrada**

```bash
john --show hash1
```

📌 _Explicación:_

- Muestra la contraseña de la base de datos KeePass si se encontró con éxito.

---

### **3. Recuperación de contraseñas de archivos RAR**

#### **Generar el hash del archivo RAR**

```bash
rar2john "Agregar Microsoft Store Windows (SR. JANCELL).rar" > hash2
```

📌 _Explicación:_

- `rar2john` convierte el archivo RAR protegido en un hash compatible con John the Ripper.

#### **Romper la contraseña con John the Ripper**

```bash
john --wordlist=rockyou.txt hash2
```

📌 _Explicación:_

- Usa RockYou para tratar de descifrar la contraseña del archivo RAR.

#### **Mostrar la contraseña encontrada**

```bash
john --show hash2
```

📌 _Explicación:_

- Muestra la contraseña del archivo RAR si se encontró con éxito.

---

### **Conclusión**

Este proceso es útil para recuperar contraseñas olvidadas de archivos protegidos. Es importante recordar que solo debes realizar este procedimiento en archivos de tu propiedad o con permiso explícito.

🔹 **Opcional:** Si deseas hacer ataques más avanzados puedes probar:

- **Fuerza bruta sin diccionario**:
    
    ```bash
    john --incremental hash
    ```
    
- **Usar múltiples hilos para acelerar el proceso**:
    
    ```bash
    john --fork=4 --wordlist=rockyou.txt hash
    ```



**[[Hoja de Trucos HASHCAT]]**
[[13- Automatización de Cracking de Contraseñas]]
[[14- Prueba de lápiz interno]]