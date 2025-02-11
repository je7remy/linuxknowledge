
------------

#SSH #OpenSSH #sshd_config #X11Forwarding #ConfiguracionPeligrosa #SSHAudit #Rsync #TransferenciaDeArchivos #RemoteAdministration #RServices #RCommands #HostsEquiv #PenTesting #Ciberseguridad #InfoSec

--------------

## Configuración predeterminada

El archivo [sshd_config](https://www.ssh.com/academy/ssh/sshd_config), responsable del servidor OpenSSH, tiene solo algunas de las configuraciones configuradas de forma predeterminada. Sin embargo, la configuración predeterminada incluye el reenvío X11, que contenía una vulnerabilidad de inyección de comandos en la versión 7.2p1 de OpenSSH en 2016. Sin embargo, no necesitamos una interfaz gráfica de usuario para administrar nuestros servidores.

#### Configuración predeterminada

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ cat /etc/ssh/sshd_config  | grep -v "#" | sed -r '/^\s*$/d'

Include /etc/ssh/sshd_config.d/*.conf
ChallengeResponseAuthentication no
UsePAM yes
X11Forwarding yes
PrintMotd no
AcceptEnv LANG LC_*
Subsystem       sftp    /usr/lib/openssh/sftp-server
```

La mayoría de los ajustes de este archivo de configuración están comentados y requieren una configuración manual.

---

## Configuraciones peligrosas

A pesar de que el protocolo SSH es uno de los protocolos más seguros disponibles en la actualidad, algunas configuraciones incorrectas pueden hacer que el servidor SSH sea vulnerable a ataques fáciles de ejecutar. Echemos un vistazo a las siguientes configuraciones:

|**Ajuste**|**Descripción**|
|---|---|
|`PasswordAuthentication yes`|Permite la autenticación basada en contraseña.|
|`PermitEmptyPasswords yes`|Permite el uso de contraseñas vacías.|
|`PermitRootLogin yes`|Permite iniciar sesión como usuario root.|
|`Protocol 1`|Utiliza una versión obsoleta de cifrado.|
|`X11Forwarding yes`|Permite el reenvío X11 para aplicaciones GUI.|
|`AllowTcpForwarding yes`|Permite el reenvío de puertos TCP.|
|`PermitTunnel`|Permite la tunelización.|
|`DebianBanner yes`|Muestra un banner específico al iniciar sesión.|

Permitir la autenticación de contraseña nos permite forzar un nombre de usuario conocido para posibles contraseñas. Se pueden utilizar muchos métodos diferentes para adivinar las contraseñas de los usuarios. Para ello, se suelen utilizar específicos para mutar las contraseñas más utilizadas y, aterradoramente, corregirlas. Esto se debe a que los humanos somos perezosos y no queremos recordar contraseñas complejas y complicadas. Por lo tanto, creamos contraseñas que podemos recordar fácilmente, y esto lleva al hecho de que, por ejemplo, los números o caracteres se agregan solo al final de la contraseña. Creyendo que la contraseña es segura, los patrones mencionados se utilizan para adivinar con precisión tales "ajustes" de estas contraseñas. Sin embargo, algunas instrucciones y [guías de endurecimiento](https://www.ssh-audit.com/hardening_guides.html) se pueden utilizar para endurecer nuestros servidores SSH.`patterns`

---

## Huella del servicio

Una de las herramientas que podemos utilizar para tomar las huellas dactilares del servidor SSH es [ssh-audit](https://github.com/jtesta/ssh-audit). Comprueba la configuración del lado del cliente y del lado del servidor y muestra información general y qué algoritmos de cifrado siguen utilizando el cliente y el servidor. Por supuesto, esto podría explotarse atacando el servidor o el cliente a nivel críptico más adelante.

#### Auditoría SSH

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ git clone https://github.com/jtesta/ssh-audit.git && cd ssh-audit
zunderrubb@htb[/htb]$ ./ssh-audit.py 10.129.14.132

# general
(gen) banner: SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.3
(gen) software: OpenSSH 8.2p1
(gen) compatibility: OpenSSH 7.4+, Dropbear SSH 2018.76+
(gen) compression: enabled (zlib@openssh.com)                                   

# key exchange algorithms
(kex) curve25519-sha256                     -- [info] available since OpenSSH 7.4, Dropbear SSH 2018.76                            
(kex) curve25519-sha256@libssh.org          -- [info] available since OpenSSH 6.5, Dropbear SSH 2013.62
(kex) ecdh-sha2-nistp256                    -- [fail] using weak elliptic curves
                                            `- [info] available since OpenSSH 5.7, Dropbear SSH 2013.62
(kex) ecdh-sha2-nistp384                    -- [fail] using weak elliptic curves
                                            `- [info] available since OpenSSH 5.7, Dropbear SSH 2013.62
(kex) ecdh-sha2-nistp521                    -- [fail] using weak elliptic curves
                                            `- [info] available since OpenSSH 5.7, Dropbear SSH 2013.62
(kex) diffie-hellman-group-exchange-sha256 (2048-bit) -- [info] available since OpenSSH 4.4
(kex) diffie-hellman-group16-sha512         -- [info] available since OpenSSH 7.3, Dropbear SSH 2016.73
(kex) diffie-hellman-group18-sha512         -- [info] available since OpenSSH 7.3
(kex) diffie-hellman-group14-sha256         -- [info] available since OpenSSH 7.3, Dropbear SSH 2016.73

# host-key algorithms
(key) rsa-sha2-512 (3072-bit)               -- [info] available since OpenSSH 7.2
(key) rsa-sha2-256 (3072-bit)               -- [info] available since OpenSSH 7.2
(key) ssh-rsa (3072-bit)                    -- [fail] using weak hashing algorithm
                                            `- [info] available since OpenSSH 2.5.0, Dropbear SSH 0.28
                                            `- [info] a future deprecation notice has been issued in OpenSSH 8.2: https://www.openssh.com/txt/release-8.2
(key) ecdsa-sha2-nistp256                   -- [fail] using weak elliptic curves
                                            `- [warn] using weak random number generator could reveal the key
                                            `- [info] available since OpenSSH 5.7, Dropbear SSH 2013.62
(key) ssh-ed25519                           -- [info] available since OpenSSH 6.5
...SNIP...
```

Lo primero que podemos ver en las primeras líneas de la salida es el banner que revela la versión del servidor OpenSSH. Las versiones anteriores tenían algunas vulnerabilidades, como [CVE-2020-14145](https://www.cvedetails.com/cve/CVE-2020-14145/), que permitían al atacante la capacidad de Man-In-The-Middle y atacar el intento de conexión inicial. El resultado detallado de la configuración de la conexión con el servidor OpenSSH también puede proporcionar a menudo información importante, como los métodos de autenticación que puede utilizar el servidor.

#### Cambiar el método de autenticación

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ ssh -v cry0l1t3@10.129.14.132

OpenSSH_8.2p1 Ubuntu-4ubuntu0.3, OpenSSL 1.1.1f  31 Mar 2020
debug1: Reading configuration data /etc/ssh/ssh_config 
...SNIP...
debug1: Authentications that can continue: publickey,password,keyboard-interactive
```

Para posibles ataques de fuerza bruta, podemos especificar el método de autenticación con la opción de cliente SSH .`PreferredAuthentications`

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ ssh -v cry0l1t3@10.129.14.132 -o PreferredAuthentications=password

OpenSSH_8.2p1 Ubuntu-4ubuntu0.3, OpenSSL 1.1.1f  31 Mar 2020
debug1: Reading configuration data /etc/ssh/ssh_config
...SNIP...
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: password

cry0l1t3@10.129.14.132's password:
```

Incluso con este servicio obvio y seguro, recomendamos configurar nuestro propio servidor OpenSSH en nuestra máquina virtual, experimentar con él y familiarizarnos con las diferentes configuraciones y opciones.

Es posible que encontremos varios banners para el servidor SSH durante nuestras pruebas de penetración. De forma predeterminada, los banners comienzan con la versión del protocolo que se puede aplicar y, a continuación, la versión del propio servidor. Por ejemplo, con , sabemos que podemos usar ambas versiones de protocolo SSH-1 y SSH-2, y estamos tratando con la versión 3.9p1 del servidor OpenSSH. Por otro lado, para un banner con , estamos tratando con una versión 8.2p1 de OpenSSH que solo acepta la versión del protocolo SSH-2.`SSH-1.99-OpenSSH_3.9p1``SSH-2.0-OpenSSH_8.2p1`

---

## Rsync

[Rsync](https://linux.die.net/man/1/rsync) es una herramienta rápida y eficiente para copiar archivos de forma local y remota. Se puede utilizar para copiar archivos localmente en una máquina determinada y hacia/desde hosts remotos. Es muy versátil y conocido por su algoritmo de transferencia delta. Este algoritmo reduce la cantidad de datos transmitidos a través de la red cuando ya existe una versión del archivo en el host de destino. Para ello, envía solo las diferencias entre los archivos de origen y la versión anterior de los archivos que residen en el servidor de destino. A menudo se utiliza para copias de seguridad y duplicación. Encuentra los archivos que deben transferirse mirando los archivos que han cambiado de tamaño o la hora de la última modificación. De forma predeterminada, utiliza el puerto y se puede configurar para usar SSH para transferencias seguras de archivos aprovechando una conexión de servidor SSH establecida.`873`

Esta [guía](https://book.hacktricks.xyz/network-services-pentesting/873-pentesting-rsync) cubre algunas de las formas en que se puede abusar de Rsync, sobre todo enumerando el contenido de una carpeta compartida en un servidor de destino y recuperando archivos. Esto a veces se puede hacer sin autenticación. Otras veces necesitaremos credenciales. Si encuentra credenciales durante una prueba de penetración y se encuentra con Rsync en un host interno (o externo), siempre vale la pena verificar la reutilización de contraseñas, ya que es posible que pueda extraer algunos archivos confidenciales que podrían usarse para obtener acceso remoto al objetivo.

Hagamos un poco de huella rápida. Podemos ver que Rsync está en uso usando el protocolo 31.

#### Escaneo de Rsync

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ sudo nmap -sV -p 873 127.0.0.1

Starting Nmap 7.92 ( https://nmap.org ) at 2022-09-19 09:31 EDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0058s latency).

PORT    STATE SERVICE VERSION
873/tcp open  rsync   (protocol version 31)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.13 seconds
```

#### Sondeo de recursos compartidos accesibles

A continuación, podemos sondear un poco el servicio para ver a qué podemos acceder.

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ nc -nv 127.0.0.1 873

(UNKNOWN) [127.0.0.1] 873 (rsync) open
@RSYNCD: 31.0
@RSYNCD: 31.0
#list
dev            	Dev Tools
@RSYNCD: EXIT
```

#### Enumeración de un recurso compartido abierto

Aquí podemos ver una acción llamada , y podemos enumerarla más.`dev`

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ rsync -av --list-only rsync://127.0.0.1/dev

receiving incremental file list
drwxr-xr-x             48 2022/09/19 09:43:10 .
-rw-r--r--              0 2022/09/19 09:34:50 build.sh
-rw-r--r--              0 2022/09/19 09:36:02 secrets.yaml
drwx------             54 2022/09/19 09:43:10 .ssh

sent 25 bytes  received 221 bytes  492.00 bytes/sec
total size is 0  speedup is 0.00
```

A partir de la salida anterior, podemos ver algunos archivos interesantes que puede valer la pena extraer para investigar más a fondo. También podemos ver que se puede acceder a un directorio que probablemente contenga claves SSH. A partir de aquí, podríamos sincronizar todos los archivos con nuestro host de ataque con el comando . Si Rsync está configurado para usar SSH para transferir archivos, podríamos modificar nuestros comandos para incluir la bandera, o si se usa un puerto no estándar para SSH. Esta [guía](https://phoenixnap.com/kb/how-to-rsync-over-ssh) es útil para comprender la sintaxis para usar Rsync a través de SSH.`rsync -av rsync://127.0.0.1/dev``-e ssh``-e "ssh -p2222"`

---

## R-Servicios

Los R-Services son un conjunto de servicios alojados para permitir el acceso remoto o emitir comandos entre hosts Unix a través de TCP/IP. Inicialmente desarrollados por el Grupo de Investigación de Sistemas Computacionales () de la Universidad de California, Berkeley, fueron el estándar de facto para el acceso remoto entre sistemas operativos Unix hasta que fueron reemplazados por los protocolos y comandos Secure Shell () debido a fallas de seguridad inherentes incorporadas en ellos. Al igual que , los r-services transmiten información del cliente al servidor (y viceversa) a través de la red en un formato no cifrado, lo que hace posible que los atacantes intercepten el tráfico de la red (contraseñas, información de inicio de sesión, etc.) mediante la realización de ataques de intermediario ().`CSRG``r-services``SSH``telnet``MITM`

`R-services` se extienden a través de los puertos , y y solo se puede acceder a ellos a través de un conjunto de programas conocidos como . Son los más utilizados por sistemas operativos comerciales como Solaris, HP-UX y AIX. Si bien es menos común hoy en día, nos encontramos con ellos de vez en cuando durante nuestras pruebas de penetración internas, por lo que vale la pena comprender cómo abordarlos.`512``513``514``r-commands`

El conjunto [de comandos de R](https://en.wikipedia.org/wiki/Berkeley_r-commands) consta de los siguientes programas:

- RCP (`remote copy`)
- rexec (`remote execution`)
- rlogin (`remote login`)
- rsh (`remote shell`)
- rstat
- Tiempo de ruptura
- rwho (`remote who`)

Cada comando tiene su funcionalidad prevista; sin embargo, solo cubriremos los abusos más comunes. La siguiente tabla proporcionará una descripción general rápida de los comandos de los que se abusa con más frecuencia, incluido el demonio de servicio con el que interactúan, el puerto y el método de transporte al que se puede acceder, y una breve descripción de cada uno.`r-commands`

|**Mandar**|**Demonio de servicio**|**Puerto**|**Protocolo de transporte**|**Descripción**|
|---|---|---|---|---|
|`rcp`|`rshd`|514|TCP|Copie un archivo o directorio bidireccionalmente desde el sistema local al sistema remoto (o viceversa) o de un sistema remoto a otro. Funciona como el comando en Linux, pero proporciona .`cp``no warning to the user for overwriting existing files on a system`|
|`rsh`|`rshd`|514|TCP|Abre un shell en un equipo remoto sin un procedimiento de inicio de sesión. Se basa en las entradas de confianza de los archivos y para la validación.`/etc/hosts.equiv``.rhosts`|
|`rexec`|`rexecd`|512|TCP|Permite a un usuario ejecutar comandos de shell en un equipo remoto. Requiere autenticación mediante el uso de un y a través de un socket de red sin cifrar. La autenticación se anula mediante las entradas de confianza de los archivos y.`username``password``/etc/hosts.equiv``.rhosts`|
|`rlogin`|`rlogind`|513|TCP|Permite a un usuario iniciar sesión en un host remoto a través de la red. Funciona de manera similar, pero solo puede conectarse a hosts similares a Unix. La autenticación se anula mediante las entradas de confianza de los archivos y.`telnet``/etc/hosts.equiv``.rhosts`|

El archivo /etc/hosts.equiv contiene una lista de hosts de confianza y se utiliza para conceder acceso a otros sistemas de la red. Cuando los usuarios de uno de estos hosts intentan acceder al sistema, se les concede acceso automáticamente sin necesidad de autenticación adicional.

#### /etc/hosts.equiv

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ cat /etc/hosts.equiv

# <hostname> <local username>
pwnbox cry0l1t3
```

Ahora que tenemos una comprensión básica de , hagamos un poco de uso rápido de huellas para determinar si todos los puertos necesarios están abiertos.`r-commands``Nmap`

#### Escaneo de R-Services

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ sudo nmap -sV -p 512,513,514 10.0.17.2

Starting Nmap 7.80 ( https://nmap.org ) at 2022-12-02 15:02 EST
Nmap scan report for 10.0.17.2
Host is up (0.11s latency).

PORT    STATE SERVICE    VERSION
512/tcp open  exec?
513/tcp open  login?
514/tcp open  tcpwrapped

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 145.54 seconds
```

#### Control de acceso y relaciones de confianza

La principal preocupación de , y una de las principales razones por las que se introdujo para reemplazarlo, son los problemas inherentes al control de acceso para estos protocolos. Los R-services se basan en información de confianza enviada desde el cliente remoto a la máquina host en la que intentan autenticarse. De forma predeterminada, estos servicios utilizan [módulos de autenticación conectables (PAM)](https://debathena.mit.edu/trac/wiki/PAM) para la autenticación de usuarios en un sistema remoto; sin embargo, también eluden esta autenticación mediante el uso de los archivos and en el sistema. Los archivos and contienen una lista de hosts ( o ) y usuarios que están junto al host local cuando se realiza un intento de conexión mediante . Las entradas de cualquiera de los archivos pueden aparecer de la siguiente manera:`r-services``SSH``/etc/hosts.equiv``.rhosts``hosts.equiv``.rhosts``IPs``Hostnames``trusted``r-commands`

**Nota:** El archivo se reconoce como la configuración global de todos los usuarios de un sistema, mientras que proporciona una configuración por usuario. `hosts.equiv``.rhosts`

#### Ejemplo de archivo .rhosts

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ cat .rhosts

htb-student     10.0.17.5
+               10.0.17.10
+               +
```

Como podemos ver en este ejemplo, ambos archivos siguen la sintaxis específica de los pares or. Además, el modificador se puede usar dentro de estos archivos como comodín para especificar cualquier cosa. En este ejemplo, el modificador permite a cualquier usuario externo acceder a los comandos r desde la cuenta de usuario a través del host con la dirección IP .`<username> <ip address>``<username> <hostname>``+``+``htb-student``10.0.17.10`

Las configuraciones incorrectas en cualquiera de estos archivos pueden permitir que un atacante se autentique como otro usuario sin credenciales, con el potencial de obtener la ejecución de código. Ahora que entendemos cómo podemos abusar potencialmente de las configuraciones incorrectas en estos archivos, intentemos iniciar sesión en un host de destino usando .`rlogin`

#### Inicio de sesión con Rlogin

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ rlogin 10.0.17.2 -l htb-student

Last login: Fri Dec  2 16:11:21 from localhost

[htb-student@localhost ~]$
```

Hemos iniciado sesión con éxito en la cuenta en el host remoto debido a los errores de configuración en el archivo. Una vez que iniciamos sesión con éxito, también podemos abusar del comando para enumerar todas las sesiones interactivas en la red local enviando solicitudes al puerto UDP 513.`htb-student``.rhosts``rwho`

#### Listado de usuarios autenticados usando Rwho

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ rwho

root     web01:pts/0 Dec  2 21:34
htb-student     workstn01:tty1  Dec  2 19:57  2:25       
```

A partir de esta información, podemos ver que el usuario está autenticado actualmente en el host, mientras que el usuario está autenticado en el host. Podemos usar esto a nuestro favor cuando exploramos posibles nombres de usuario para usar durante futuros ataques a hosts a través de la red. Sin embargo, el demonio transmite periódicamente información sobre los usuarios que han iniciado sesión, por lo que podría ser beneficioso observar el tráfico de red.`htb-student``workstn01``root``web01``rwho`

#### Listado de usuarios autenticados mediante Rusers

Para proporcionar información adicional junto con , podemos emitir el comando. Esto nos dará una cuenta más detallada de todos los usuarios que han iniciado sesión a través de la red, incluida información como el nombre de usuario, el nombre de host de la máquina a la que se accede, el TTY en el que el usuario ha iniciado sesión, la fecha y la hora en que el usuario ha iniciado sesión, la cantidad de tiempo desde que el usuario escribió en el teclado y el host remoto desde el que inició sesión (si corresponde).`rwho``rusers`

  Protocolos de administración remota de Linux

```shell-session
zunderrubb@htb[/htb]$ rusers -al 10.0.17.5

htb-student     10.0.17.5:console          Dec 2 19:57     2:25
```

Como podemos ver, los servicios R se utilizan con menos frecuencia hoy en día debido a sus fallos de seguridad inherentes y a la disponibilidad de protocolos más seguros como SSH. Para ser un profesional completo de la seguridad de la información, debemos tener un conocimiento amplio y profundo de muchos sistemas, aplicaciones, protocolos, etc. Por lo tanto, archiva este conocimiento sobre los servicios R porque nunca se sabe cuándo puedes encontrarlos.


**[[SQL]]**