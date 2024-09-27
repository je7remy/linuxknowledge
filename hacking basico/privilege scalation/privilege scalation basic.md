----------
#privilegeescalation  

-----------

Nuestro acceso inicial a un servidor remoto suele estar en el contexto de un usuario con pocos privilegios, lo que no nos daría acceso completo a través de la caja. Para obtener acceso completo, necesitaremos encontrar una vulnerabilidad interna/local que escale nuestros privilegios al usuario activado o al usuario activado . Repasemos algunos métodos comunes para aumentar nuestros privilegios.`root``Linux``administrator``SYSTEM``Windows`

---

## Listas de verificación de PrivEsc

Una vez que obtenemos acceso inicial a una caja, queremos enumerarla minuciosamente para encontrar cualquier vulnerabilidad potencial que podamos explotar para lograr un nivel de privilegios más alto. Podemos encontrar muchas listas de verificación y hojas de trucos en línea que tienen una colección de verificaciones que podemos ejecutar y los comandos para ejecutar estas verificaciones. Un excelente recurso es [HackTricks](https://book.hacktricks.xyz/), que tiene una excelente lista de verificación para la escalada de privilegios locales de [Linux](https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist) y [Windows](https://book.hacktricks.xyz/windows/checklist-windows-privilege-escalation). Otro excelente repositorio es [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings), que también tiene listas de verificación tanto para [Linux](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md) como para [Windows](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md). Debemos comenzar a experimentar con varios comandos y técnicas y familiarizarnos con ellos para comprender las múltiples debilidades que pueden llevar a escalar nuestros privilegios.

---

## Scripts de enumeración

Muchos de los comandos anteriores se pueden ejecutar automáticamente con un script para revisar el informe y buscar cualquier debilidad. Podemos ejecutar muchos scripts para enumerar automáticamente el servidor mediante la ejecución de comandos comunes que devuelven cualquier hallazgo interesante. Algunos de los scripts de enumeración comunes de Linux incluyen [LinEnum](https://github.com/rebootuser/LinEnum.git) y [linuxprivchecker](https://github.com/sleventyeleven/linuxprivchecker), y para Windows incluyen [Seatbelt](https://github.com/GhostPack/Seatbelt) y [JAWS](https://github.com/411Hall/JAWS).

Otra herramienta útil que podemos utilizar para la enumeración de servidores es [Privilege Escalation Awesome Scripts SUITE (PEASS),](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite) ya que está bien mantenida para mantenerse actualizada e incluye scripts para enumerar tanto Linux como Windows.

Nota: Estos scripts ejecutarán muchos comandos conocidos por identificar vulnerabilidades y crearán mucho "ruido" que puede activar el software antivirus o el software de monitoreo de seguridad que busca este tipo de eventos. Esto puede impedir que los scripts se ejecuten o incluso activar una alarma de que el sistema se ha visto comprometido. En algunos casos, es posible que deseemos hacer una enumeración manual en lugar de ejecutar scripts.

Tomemos un ejemplo de ejecución del script de Linux desde llamado :`PEASS``LinPEAS`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ ./linpeas.sh
...SNIP...

Linux Privesc Checklist: https://book.hacktricks.xyz/linux-unix/linux-privilege-escalation-checklist
 LEYEND:
  RED/YELLOW: 99% a PE vector
  RED: You must take a look at it
  LightCyan: Users with console
  Blue: Users without console & mounted devs
  Green: Common things (users, groups, SUID/SGID, mounts, .sh scripts, cronjobs)
  LightMangenta: Your username


====================================( Basic information )=====================================
OS: Linux version 3.9.0-73-generic
User & Groups: uid=33(www-data) gid=33(www-data) groups=33(www-data)
...SNIP...
```

Como podemos ver, una vez que el script se ejecuta, comienza a recopilar información y mostrarla en un excelente informe. Analicemos algunas de las vulnerabilidades que debemos buscar en la salida de estos scripts.

---

## Kernel Exploits

Siempre que nos encontremos con un servidor que ejecute un sistema operativo antiguo, debemos comenzar por buscar posibles vulnerabilidades del kernel que puedan existir. Supongamos que el servidor no se mantiene con las últimas actualizaciones y parches. En ese caso, es probable que sea vulnerable a exploits específicos del kernel que se encuentran en versiones sin parches de Linux y Windows.

Por ejemplo, el script anterior nos mostró que la versión de Linux era . Si buscamos exploits en Google para esta versión o usemos , nos encontraríamos con un , también conocido como . Podemos buscar y descargar el exploit [DirtyCow](https://github.com/dirtycow/dirtycow.github.io/wiki/PoCs) y ejecutarlo en el servidor para obtener acceso de root.`3.9.0-73-generic``searchsploit``CVE-2016-5195``DirtyCow`

El mismo concepto también se aplica a Windows, ya que hay muchas vulnerabilidades en versiones anteriores o sin parches de Windows, con varias vulnerabilidades que se pueden usar para la escalada de privilegios. Debemos tener en cuenta que los exploits del kernel pueden causar inestabilidad en el sistema, y debemos tener mucho cuidado antes de ejecutarlos en los sistemas de producción. Lo mejor es probarlos en un entorno de laboratorio y solo ejecutarlos en sistemas de producción con la aprobación explícita y la coordinación con nuestro cliente.

---

## Vulnerable Software

Otra cosa que debemos buscar es el software instalado. Por ejemplo, podemos usar el comando en Linux o mirar en Windows para ver qué software está instalado en el sistema. Debemos buscar exploits públicos para cualquier software instalado, especialmente si hay versiones anteriores en uso, que contengan vulnerabilidades sin parches.`dpkg -l``C:\Program Files`

---

## Privilegios de usuario

Otro aspecto crítico a tener en cuenta después de obtener acceso a un servidor son los privilegios disponibles para el usuario al que tenemos acceso. Supongamos que se nos permite ejecutar comandos específicos como root (o como otro usuario). En ese caso, es posible que podamos escalar nuestros privilegios a usuarios root/del sistema u obtener acceso como un usuario diferente. A continuación se muestran algunas formas comunes de explotar ciertos privilegios de usuario:

1. Sudo
2. SUID
3. Privilegios de token de Windows

El comando en Linux permite a un usuario ejecutar comandos como un usuario diferente. Por lo general, se usa para permitir que los usuarios con menos privilegios ejecuten comandos como root sin darles acceso al usuario root. Esto generalmente se hace ya que los comandos específicos solo se pueden ejecutar como root 'like' o permitir que el usuario acceda a ciertos directorios solo root. Podemos comprobar qué privilegios tenemos con el comando:`sudo``tcpdump``sudo``sudo -l`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ sudo -l

[sudo] password for user1:
...SNIP...

User user1 may run the following commands on ExampleServer:
    (ALL : ALL) ALL
```

El resultado anterior dice que podemos ejecutar todos los comandos con , lo que nos da acceso completo, y podemos usar el comando con para cambiar al usuario root:`sudo``su``sudo`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ sudo su -

[sudo] password for user1:
whoami
root
```

El comando anterior requiere una contraseña para ejecutar cualquier comando con . Hay ciertas ocasiones en las que se nos puede permitir ejecutar ciertas aplicaciones, o todas las aplicaciones, sin tener que proporcionar una contraseña:`sudo`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ sudo -l

    (user : user) NOPASSWD: /bin/echo
```

La entrada muestra que el comando se puede ejecutar sin contraseña. Esto sería útil si obtuviéramos acceso al servidor a través de una vulnerabilidad y no tuviéramos la contraseña del usuario. Como dice, podemos ejecutarlo como ese usuario y no como root. Para ello, podemos especificar el usuario con:`NOPASSWD``/bin/echo``user``sudo``-u user`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ sudo -u user /bin/echo Hello World!

    Hello World!
```

Una vez que encontramos una aplicación en particular con la que podemos ejecutar, podemos buscar formas de explotarla para obtener un shell como usuario root. [go awayBins](https://gtfobins.github.io/) contiene una lista de comandos y cómo se pueden explotar a través de . Podemos buscar la aplicación sobre la que tenemos privilegios, y si existe, puede decirnos el comando exacto que debemos ejecutar para obtener acceso root usando el privilegio que tenemos.`sudo``sudo``sudo``sudo`

[LOLBAS](https://lolbas-project.github.io/#) también contiene una lista de aplicaciones de Windows que podemos aprovechar para realizar ciertas funciones, como descargar archivos o ejecutar comandos en el contexto de un usuario privilegiado.

---

## Tareas programadas

Tanto en Linux como en Windows, existen métodos para que los scripts se ejecuten a intervalos específicos para llevar a cabo una tarea. Algunos ejemplos son tener un análisis antivirus que se ejecuta cada hora o un script de copia de seguridad que se ejecuta cada 30 minutos. Por lo general, hay dos formas de aprovechar las tareas programadas (Windows) o los trabajos cron (Linux) para escalar nuestros privilegios:

1. Agregar nuevas tareas programadas/trabajos cron
2. Engañarlos para que ejecuten un software malicioso

La forma más fácil es comprobar si se nos permite añadir nuevas tareas programadas. En Linux, una forma común de mantener las tareas programadas es a través de . Hay directorios específicos que podemos utilizar para agregar nuevos trabajos cron si tenemos los permisos sobre ellos. Entre ellas se encuentran:`Cron Jobs``write`

1. `/etc/crontab`
2. `/etc/cron.d`
3. `/var/spool/cron/crontabs/root`

Si podemos escribir en un directorio llamado por un cron job, podemos escribir un script bash con un comando de shell inverso, que debería enviarnos un shell inverso cuando se ejecute.

---

## Credenciales expuestas

A continuación, podemos buscar archivos que podamos leer y ver si contienen alguna credencial expuesta. Esto es muy común con archivos, archivos y archivos de historial de usuario (en Linux y en Windows). Los scripts de enumeración que discutimos al principio generalmente buscan contraseñas potenciales en los archivos y nos las proporcionan, como se muestra a continuación:`configuration``log``bash_history``PSReadLine`

  Escalada de privilegios

```shell-session
...SNIP...
[+] Searching passwords in config PHP files
[+] Finding passwords inside logs (limit 70)
...SNIP...
/var/www/html/config.php: $conn = new mysqli(localhost, 'db_user', 'password123');
```

Como podemos ver, la contraseña de la base de datos '' está expuesta, lo que nos permitiría iniciar sesión en las bases de datos locales y buscar información interesante. También podemos verificar , ya que el usuario del sistema puede haber usado su contraseña para las bases de datos, lo que puede permitirnos usar la misma contraseña para cambiar a ese usuario, de la siguiente manera:`password123``mysql``Password Reuse`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ su -

Password: password123
whoami

root
```

También podemos usar las credenciales de usuario para ingresar al servidor como ese usuario.`ssh`

---

## Claves SSH

Por último, hablemos de las claves SSH. Si hemos leído el acceso sobre el directorio de un usuario específico, podemos leer sus claves ssh privadas que se encuentran en o , y usarlas para iniciar sesión en el servidor. Si podemos leer el directorio y podemos leer el archivo, podemos copiarlo en nuestra máquina y usar el indicador para iniciar sesión con él:`.ssh``/home/user/.ssh/id_rsa``/root/.ssh/id_rsa``/root/.ssh/``id_rsa``-i`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ vim id_rsa
zunderrubb@htb[/htb]$ chmod 600 id_rsa
zunderrubb@htb[/htb]$ ssh user@10.10.10.10 -i id_rsa

root@remotehost#
```

Tenga en cuenta que usamos el comando 'chmod 600 id_rsa' en la clave después de crearla en nuestra máquina para cambiar los permisos del archivo para que sean más restrictivos. Si las claves ssh tienen permisos laxos, es decir, pueden ser leídas por otras personas, el servidor ssh les impediría funcionar.

Si nos encontramos con acceso de escritura a un directorio de usuarios, podemos colocar nuestra clave pública en el directorio ssh del usuario en . Esta técnica se usa generalmente para obtener acceso a ssh después de obtener un shell como ese usuario. La configuración actual de SSH no aceptará claves escritas por otros usuarios, por lo que solo funcionará si ya hemos ganado el control sobre ese usuario. Primero debemos crear una nueva clave con y el flag para especificar el archivo de salida:`/.ssh/``/home/user/.ssh/authorized_keys``ssh-keygen``-f`

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ ssh-keygen -f key

Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): *******
Enter same passphrase again: *******

Your identification has been saved in key
Your public key has been saved in key.pub
The key fingerprint is:
SHA256:...SNIP... user@parrot
The key's randomart image is:
+---[RSA 3072]----+
|   ..o.++.+      |
...SNIP...
|     . ..oo+.    |
+----[SHA256]-----+
```

Esto nos dará dos archivos: (que usaremos con ) y , que copiaremos a la máquina remota. Copiemos, luego en la máquina remota, lo agregaremos a:`key``ssh -i``key.pub``key.pub``/root/.ssh/authorized_keys`

  Escalada de privilegios

```shell-session
user@remotehost$ echo "ssh-rsa AAAAB...SNIP...M= user@parrot" >> /root/.ssh/authorized_keys
```

Ahora, el servidor remoto debería permitirnos iniciar sesión como ese usuario utilizando nuestra clave privada:

  Escalada de privilegios

```shell-session
zunderrubb@htb[/htb]$ ssh root@10.10.10.10 -i key

root@remotehost# 
```

Como podemos ver, ahora podemos ssh en el usuario . Los módulos [Escalada de privilegios de Linux](https://academy.hackthebox.com/module/details/51) y Escalada de [privilegios de Windows](https://academy.hackthebox.com/module/details/67) ofrecen más detalles sobre cómo usar cada uno de estos métodos para la escalada de privilegios y muchos otros.`root`