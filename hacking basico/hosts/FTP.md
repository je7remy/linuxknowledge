------------
#ftp 

----------
## TFTP

`Trivial File Transfer Protocol` (`TFTP`) es más simple que FTP y realiza transferencias de archivos entre los procesos del cliente y del servidor. Sin embargo, proporciona autenticación de usuario y otras funciones valiosas compatibles con FTP. Además, mientras que FTP usa TCP, TFTP usa , lo que lo convierte en un protocolo poco confiable y hace que use la recuperación de la capa de aplicación asistida por UDP.`does not``UDP`

Esto se refleja, por ejemplo, en el hecho de que TFTP, a diferencia de FTP, no requiere la autenticación del usuario. No admite el inicio de sesión protegido a través de contraseñas y establece límites de acceso basados únicamente en los permisos de lectura y escritura de un archivo en el sistema operativo. En la práctica, esto lleva a que TFTP funcione exclusivamente en directorios y con archivos que se han compartido con todos los usuarios y que se pueden leer y escribir globalmente. Debido a la falta de seguridad, TFTP, a diferencia de FTP, solo se puede usar en redes locales y protegidas.

Echemos un vistazo a algunos comandos de:`TFTP`

|**Comandos**|**Descripción**|
|---|---|
|`connect`|Establece el host remoto y, opcionalmente, el puerto, para las transferencias de archivos.|
|`get`|Transfiere un archivo o conjunto de archivos desde el host remoto al host local.|
|`put`|Transfiere un archivo o conjunto de archivos desde el host local al host remoto.|
|`quit`|Sale de tftp.|
|`status`|Muestra el estado actual de tftp, incluido el modo de transferencia actual (ascii o binario), el estado de conexión, el valor de tiempo de espera, etc.|
|`verbose`|Activa o desactiva el modo detallado, que muestra información adicional durante la transferencia de archivos.|

A diferencia del cliente FTP, no tiene funcionalidad de listado de directorios.`TFTP`

---

## Configuración predeterminada

Uno de los servidores FTP más utilizados en las distribuciones basadas en Linux es [vsFTPd](https://security.appspot.com/vsftpd.html). La configuración predeterminada de vsFTPd se puede encontrar en , y algunas configuraciones ya están predefinidas de forma predeterminada. Se recomienda encarecidamente instalar el servidor vsFTPd en una máquina virtual y echar un vistazo más de cerca a esta configuración.`/etc/vsftpd.conf`

#### Instalar vsFTPd

  FTP

```shell-session
zunderrubb@htb[/htb]$ sudo apt install vsftpd 
```

El servidor vsFTPd es solo uno de los pocos servidores FTP disponibles para nosotros. Hay muchas alternativas diferentes, que también traen, entre otras cosas, muchas más funciones y opciones de configuración con ellas. Usaremos el servidor vsFTPd porque es una excelente manera de mostrar las posibilidades de configuración de un servidor FTP de una manera simple y fácil de entender sin entrar en los detalles de las páginas de manual. Si nos fijamos en el fichero de configuración de vsFTPd, veremos muchas opciones y ajustes que o bien están comentados o bien comentados. Sin embargo, el archivo de configuración no contiene todos los ajustes posibles que se pueden realizar. Los existentes y los que faltan se pueden encontrar en la [página del manual](http://vsftpd.beasts.org/vsftpd_conf.html).

#### Archivo de configuración vsFTPd

  FTP

```shell-session
zunderrubb@htb[/htb]$ cat /etc/vsftpd.conf | grep -v "#"
```

|**Ajuste**|**Descripción**|
|---|---|
|`listen=NO`|¿Ejecutar desde inetd o como un demonio independiente?|
|`listen_ipv6=YES`|¿Escuchar en IPv6?|
|`anonymous_enable=NO`|¿Habilitar el acceso anónimo?|
|`local_enable=YES`|¿Permitir que los usuarios locales inicien sesión?|
|`dirmessage_enable=YES`|¿Mostrar mensajes de Active Directory cuando los usuarios entran en determinados directorios?|
|`use_localtime=YES`|¿Usas la hora local?|
|`xferlog_enable=YES`|¿Activar el registro de cargas/descargas?|
|`connect_from_port_20=YES`|¿Conectarse desde el puerto 20?|
|`secure_chroot_dir=/var/run/vsftpd/empty`|Nombre de un directorio vacío|
|`pam_service_name=vsftpd`|Esta cadena es el nombre del servicio PAM que usará vsftpd.|
|`rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem`|Las tres últimas opciones especifican la ubicación del certificado RSA que se usará para las conexiones cifradas SSL.|
|`rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key`||
|`ssl_enable=NO`||

Además, hay un archivo llamado al que también debemos prestar atención, ya que este archivo se utiliza para denegar a ciertos usuarios el acceso al servicio FTP. En el siguiente ejemplo, los usuarios , , y no pueden iniciar sesión en el servicio FTP, incluso si existen en el sistema Linux.`/etc/ftpusers``guest``john``kevin`

#### FTPUSERS

  FTP

```shell-session
zunderrubb@htb[/htb]$ cat /etc/ftpusers

guest
john
kevin
```

---

## Configuraciones peligrosas

Hay muchas configuraciones diferentes relacionadas con la seguridad que podemos realizar en cada servidor FTP. Estos pueden tener varios propósitos, como probar conexiones a través de los firewalls, probar rutas y mecanismos de autenticación. Uno de estos mecanismos de autenticación es el usuario. Esto se usa a menudo para permitir que todos en la red interna compartan archivos y datos sin acceder a las computadoras de los demás. Con vsFTPd, la [configuración opcional](http://vsftpd.beasts.org/vsftpd_conf.html) que se puede agregar al archivo de configuración para el inicio de sesión anónimo tiene el siguiente aspecto:`anonymous`

|**Ajuste**|**Descripción**|
|---|---|
|`anonymous_enable=YES`|¿Permitir el inicio de sesión anónimo?|
|`anon_upload_enable=YES`|¿Permitir que el anonimato cargue archivos?|
|`anon_mkdir_write_enable=YES`|¿Permitir que los anónimos creen nuevos directorios?|
|`no_anon_password=YES`|¿No pides contraseña a personas anónimas?|
|`anon_root=/home/username/ftp`|Directorio para anónimos.|
|`write_enable=YES`|¿Permitir el uso de comandos FTP: STOR, DELE, RNFR, RNTO, MKD, RMD, APPE y SITE?|

Con el cliente FTP estándar (), podemos acceder al servidor FTP en consecuencia e iniciar sesión con el usuario anónimo si se han utilizado los ajustes mostrados anteriormente. El uso de la cuenta anónima puede ocurrir en entornos internos e infraestructuras donde todos los participantes son conocidos. El acceso a este tipo de servicio se puede configurar temporalmente o con la configuración para acelerar el intercambio de archivos.`ftp`

Tan pronto como nos conectamos al servidor vsFTPd, se muestra con el banner del servidor FTP. A menudo, este banner contiene la descripción del y hasta el del mismo. También nos dice qué tipo de sistema es el servidor FTP. Una de las configuraciones más comunes de los servidores FTP es permitir el acceso, que no requiere credenciales legítimas pero proporciona acceso a algunos archivos. Aunque no podamos descargarlos, a veces basta con enumerar los contenidos para generar más ideas y anotar información que nos ayudará en otro enfoque.`response code 220``service``version``anonymous`

#### Inicio de sesión anónimo

  FTP

```shell-session
zunderrubb@htb[/htb]$ ftp 10.129.14.136

Connected to 10.129.14.136.
220 "Welcome to the HTB Academy vsFTP service."
Name (10.129.14.136:cry0l1t3): anonymous

230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.


ftp> ls

200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-rw-r--    1 1002     1002      8138592 Sep 14 16:54 Calender.pptx
drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Clients
drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Documents
drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Employees
-rw-rw-r--    1 1002     1002           41 Sep 14 16:45 Important Notes.txt
226 Directory send OK.

```

Sin embargo, para obtener una primera visión general de la configuración del servidor, podemos usar el siguiente comando:

#### Estado de vsFTPd

  FTP

```shell-session
ftp> status

Connected to 10.129.14.136.
No proxy connection.
Connecting using address family: any.
Mode: stream; Type: binary; Form: non-print; Structure: file
Verbose: on; Bell: off; Prompting: on; Globbing: on
Store unique: off; Receive unique: off
Case: off; CR stripping: on
Quote control characters: on
Ntrans: off
Nmap: off
Hash mark printing: off; Use of PORT cmds: on
Tick counter printing: off
```

Algunos comandos deben usarse de vez en cuando, ya que estos harán que el servidor nos muestre más información que podemos usar para nuestros propósitos. Estos comandos incluyen y .`debug``trace`

#### Salida detallada de vsFTPd

  FTP

```shell-session
ftp> debug

Debugging on (debug=1).


ftp> trace

Packet tracing on.


ftp> ls

---> PORT 10,10,14,4,188,195
200 PORT command successful. Consider using PASV.
---> LIST
150 Here comes the directory listing.
-rw-rw-r--    1 1002     1002      8138592 Sep 14 16:54 Calender.pptx
drwxrwxr-x    2 1002     1002         4096 Sep 14 17:03 Clients
drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Documents
drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Employees
-rw-rw-r--    1 1002     1002           41 Sep 14 16:45 Important Notes.txt
226 Directory send OK.
```

|**Setting**|**Description**|
|---|---|
|`dirmessage_enable=YES`|Show a message when they first enter a new directory?|
|`chown_uploads=YES`|Change ownership of anonymously uploaded files?|
|`chown_username=username`|User who is given ownership of anonymously uploaded files.|
|`local_enable=YES`|Enable local users to login?|
|`chroot_local_user=YES`|Place local users into their home directory?|
|`chroot_list_enable=YES`|Use a list of local users that will be placed in their home directory?|

|**Setting**|**Description**|
|---|---|
|`hide_ids=YES`|All user and group information in directory listings will be displayed as "ftp".|
|`ls_recurse_enable=YES`|Allows the use of recurse listings.|

En el siguiente ejemplo, podemos ver que si la configuración está presente, se sobrescribirá la representación UID y GUID del servicio, lo que nos dificultará identificar con qué derechos se escriben y cargan estos archivos.`hide_ids=YES`

#### Ocultar identificaciones - SÍ

  FTP

```shell-session
ftp> ls

---> TYPE A
200 Switching to ASCII mode.
ftp: setsockopt (ignored): Permission denied
---> PORT 10,10,14,4,223,101
200 PORT command successful. Consider using PASV.
---> LIST
150 Here comes the directory listing.
-rw-rw-r--    1 ftp     ftp      8138592 Sep 14 16:54 Calender.pptx
drwxrwxr-x    2 ftp     ftp         4096 Sep 14 17:03 Clients
drwxrwxr-x    2 ftp     ftp         4096 Sep 14 16:50 Documents
drwxrwxr-x    2 ftp     ftp         4096 Sep 14 16:50 Employees
-rw-rw-r--    1 ftp     ftp           41 Sep 14 16:45 Important Notes.txt
-rw-------    1 ftp     ftp            0 Sep 15 14:57 testupload.txt
226 Directory send OK.
```

Esta configuración es una característica de seguridad para evitar que se revelen los nombres de usuario locales. Con los nombres de usuario, podríamos atacar los servicios como FTP y SSH y muchos otros con un ataque de fuerza bruta en teoría. Sin embargo, en realidad, [las soluciones fail2ban](https://en.wikipedia.org/wiki/Fail2ban) son ahora una implementación estándar de cualquier infraestructura que registra la dirección IP y bloquea todo el acceso a la infraestructura después de un cierto número de intentos fallidos de inicio de sesión.

Otra configuración útil que podemos usar para nuestros propósitos es el archivo . Esto a menudo se configura en el servidor vsFTPd para tener una mejor visión general de la estructura de directorios FTP, ya que nos permite ver todo el contenido visible a la vez.`ls_recurse_enable=YES`

#### Listado recursivo

  FTP

```shell-session
ftp> ls -R

---> PORT 10,10,14,4,222,149
200 PORT command successful. Consider using PASV.
---> LIST -R
150 Here comes the directory listing.
.:
-rw-rw-r--    1 ftp      ftp      8138592 Sep 14 16:54 Calender.pptx
drwxrwxr-x    2 ftp      ftp         4096 Sep 14 17:03 Clients
drwxrwxr-x    2 ftp      ftp         4096 Sep 14 16:50 Documents
drwxrwxr-x    2 ftp      ftp         4096 Sep 14 16:50 Employees
-rw-rw-r--    1 ftp      ftp           41 Sep 14 16:45 Important Notes.txt
-rw-------    1 ftp      ftp            0 Sep 15 14:57 testupload.txt

./Clients:
drwx------    2 ftp      ftp          4096 Sep 16 18:04 HackTheBox
drwxrwxrwx    2 ftp      ftp          4096 Sep 16 18:00 Inlanefreight

./Clients/HackTheBox:
-rw-r--r--    1 ftp      ftp         34872 Sep 16 18:04 appointments.xlsx
-rw-r--r--    1 ftp      ftp        498123 Sep 16 18:04 contract.docx
-rw-r--r--    1 ftp      ftp        478237 Sep 16 18:04 contract.pdf
-rw-r--r--    1 ftp      ftp           348 Sep 16 18:04 meetings.txt

./Clients/Inlanefreight:
-rw-r--r--    1 ftp      ftp         14211 Sep 16 18:00 appointments.xlsx
-rw-r--r--    1 ftp      ftp         37882 Sep 16 17:58 contract.docx
-rw-r--r--    1 ftp      ftp            89 Sep 16 17:58 meetings.txt
-rw-r--r--    1 ftp      ftp        483293 Sep 16 17:59 proposal.pptx

./Documents:
-rw-r--r--    1 ftp      ftp         23211 Sep 16 18:05 appointments-template.xlsx
-rw-r--r--    1 ftp      ftp         32521 Sep 16 18:05 contract-template.docx
-rw-r--r--    1 ftp      ftp        453312 Sep 16 18:05 contract-template.pdf

./Employees:
226 Directory send OK.

```

`Downloading` Los archivos de un servidor FTP de este tipo son una de las características principales, así como los archivos creados por nosotros. Esto nos permite, por ejemplo, utilizar vulnerabilidades LFI para hacer que el host ejecute comandos del sistema. Aparte de los archivos, podemos ver, descargar e inspeccionar. Los ataques también son posibles con los registros FTP, lo que lleva a (). Esto se aplica a los servicios FTP y a todos aquellos que podamos detectar durante nuestra fase de enumeración.`uploading``Remote Command Execution``RCE`

#### Descargar un archivo

  FTP

```shell-session
ftp> ls

200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rwxrwxrwx    1 ftp      ftp             0 Sep 16 17:24 Calendar.pptx
drwxrwxrwx    4 ftp      ftp          4096 Sep 16 17:57 Clients
drwxrwxrwx    2 ftp      ftp          4096 Sep 16 18:05 Documents
drwxrwxrwx    2 ftp      ftp          4096 Sep 16 17:24 Employees
-rwxrwxrwx    1 ftp      ftp            41 Sep 18 15:58 Important Notes.txt
226 Directory send OK.


ftp> get Important\ Notes.txt

local: Important Notes.txt remote: Important Notes.txt
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for Important Notes.txt (41 bytes).
226 Transfer complete.
41 bytes received in 0.00 secs (606.6525 kB/s)


ftp> exit

221 Goodbye.
```

  FTP

```shell-session
zunderrubb@htb[/htb]$ ls | grep Notes.txt

'Important Notes.txt'
```

También podemos descargar todos los archivos y carpetas a los que tenemos acceso a la vez. Esto es especialmente útil si el servidor FTP tiene muchos archivos diferentes en una estructura de carpetas más grande. Sin embargo, esto puede causar alarmas porque nadie de la empresa suele querer descargar todos los archivos y contenidos a la vez.

#### Descargar todos los archivos disponibles

  FTP

```shell-session
zunderrubb@htb[/htb]$ wget -m --no-passive ftp://anonymous:anonymous@10.129.14.136

--2021-09-19 14:45:58--  ftp://anonymous:*password*@10.129.14.136/                                         
           => ‘10.129.14.136/.listing’                                                                     
Connecting to 10.129.14.136:21... connected.                                                               
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD not needed.
==> PORT ... done.    ==> LIST ... done.                                                                 
12.12.1.136/.listing           [ <=>                                  ]     466  --.-KB/s    in 0s       
                                                                                                         
2021-09-19 14:45:58 (65,8 MB/s) - ‘10.129.14.136/.listing’ saved [466]                                     
--2021-09-19 14:45:58--  ftp://anonymous:*password*@10.129.14.136/Calendar.pptx   
           => ‘10.129.14.136/Calendar.pptx’                                       
==> CWD not required.                                                           
==> SIZE Calendar.pptx ... done.                                                                                                                            
==> PORT ... done.    ==> RETR Calendar.pptx ... done.       

...SNIP...

2021-09-19 14:45:58 (48,3 MB/s) - ‘10.129.14.136/Employees/.listing’ saved [119]

FINISHED --2021-09-19 14:45:58--
Total wall clock time: 0,03s
Downloaded: 15 files, 1,7K in 0,001s (3,02 MB/s)
```

Una vez hayamos descargado todos los archivos, crearemos un directorio con el nombre de la dirección IP de nuestro objetivo. Todos los archivos descargados se almacenan allí, que luego podemos inspeccionar localmente.`wget`

  FTP

```shell-session
zunderrubb@htb[/htb]$ tree .

.
└── 10.129.14.136
    ├── Calendar.pptx
    ├── Clients
    │   └── Inlanefreight
    │       ├── appointments.xlsx
    │       ├── contract.docx
    │       ├── meetings.txt
    │       └── proposal.pptx
    ├── Documents
    │   ├── appointments-template.xlsx
    │   ├── contract-template.docx
    │   └── contract-template.pdf
    ├── Employees
    └── Important Notes.txt

5 directories, 9 files
```

A continuación, podemos comprobar si tenemos los permisos para subir archivos al servidor FTP. Especialmente con los servidores web, es común que los archivos se sincronicen y los desarrolladores tengan acceso rápido a los archivos. FTP se usa a menudo para este propósito y, la mayoría de las veces, los errores de configuración se encuentran en servidores que los administradores creen que no se pueden detectar. La actitud de que no se puede acceder a los componentes de la red interna desde el exterior significa que el endurecimiento de los sistemas internos a menudo se descuida y conduce a configuraciones incorrectas.

La capacidad de cargar archivos en el servidor FTP conectado a un servidor web aumenta la probabilidad de obtener acceso directo al servidor web e incluso a un shell inverso que nos permite ejecutar comandos internos del sistema y tal vez incluso escalar nuestros privilegios.

#### Cargar un archivo

  FTP

```shell-session
zunderrubb@htb[/htb]$ touch testupload.txt
```

Con el comando, podemos subir los archivos de la carpeta actual al servidor FTP.`PUT`

  FTP

```shell-session
ftp> put testupload.txt 

local: testupload.txt remote: testupload.txt
---> PORT 10,10,14,4,184,33
200 PORT command successful. Consider using PASV.
---> STOR testupload.txt
150 Ok to send data.
226 Transfer complete.


ftp> ls

---> TYPE A
200 Switching to ASCII mode.
---> PORT 10,10,14,4,223,101
200 PORT command successful. Consider using PASV.
---> LIST
150 Here comes the directory listing.
-rw-rw-r--    1 1002     1002      8138592 Sep 14 16:54 Calender.pptx
drwxrwxr-x    2 1002     1002         4096 Sep 14 17:03 Clients
drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Documents
drwxrwxr-x    2 1002     1002         4096 Sep 14 16:50 Employees
-rw-rw-r--    1 1002     1002           41 Sep 14 16:45 Important Notes.txt
-rw-------    1 1002     133             0 Sep 15 14:57 testupload.txt
226 Directory send OK.

```

---

## Huella del servicio

La huella utilizando varios escáneres de red también es un enfoque práctico y generalizado. Estas herramientas nos facilitan la identificación de diferentes servicios, incluso si no son accesibles en puertos estándar. Una de las herramientas más utilizadas para este fin es Nmap. Nmap también trae el [Nmap Scripting Engine](https://nmap.org/book/nse.html) (), un conjunto de muchos scripts diferentes escritos para servicios específicos. Puede encontrar más información sobre las capacidades de Nmap y NSE en el módulo [Enumeración de red con Nmap](https://academy.hackthebox.com/course/preview/network-enumeration-with-nmap). Podemos actualizar esta base de datos de scripts NSE con el comando mostrado.`NSE`

#### Nmap FTP Scripts

  FTP

```shell-session
zunderrubb@htb[/htb]$ sudo nmap --script-updatedb

Starting Nmap 7.80 ( https://nmap.org ) at 2021-09-19 13:49 CEST
NSE: Updating rule database.
NSE: Script Database updated successfully.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.28 seconds
```

Todos los scripts NSE se encuentran en el Pwnbox en , pero en nuestros sistemas, podemos encontrarlos usando un simple comando en nuestro sistema.`/usr/share/nmap/scripts/`

  FTP

```shell-session
zunderrubb@htb[/htb]$ find / -type f -name ftp* 2>/dev/null | grep scripts

/usr/share/nmap/scripts/ftp-syst.nse
/usr/share/nmap/scripts/ftp-vsftpd-backdoor.nse
/usr/share/nmap/scripts/ftp-vuln-cve2010-4221.nse
/usr/share/nmap/scripts/ftp-proftpd-backdoor.nse
/usr/share/nmap/scripts/ftp-bounce.nse
/usr/share/nmap/scripts/ftp-libopie.nse
/usr/share/nmap/scripts/ftp-anon.nse
/usr/share/nmap/scripts/ftp-brute.nse
```

Como ya sabemos, el servidor FTP suele ejecutarse en el puerto TCP estándar 21, que podemos escanear mediante Nmap. También usamos el escaneo de versión (), el escaneo agresivo () y el escaneo de script predeterminado () contra nuestro objetivo .`-sV``-A``-sC``10.129.14.136`

#### Nmap

  FTP

```shell-session
zunderrubb@htb[/htb]$ sudo nmap -sV -p21 -sC -A 10.129.14.136

Starting Nmap 7.80 ( https://nmap.org ) at 2021-09-16 18:12 CEST
Nmap scan report for 10.129.14.136
Host is up (0.00013s latency).

PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 2.0.8 or later
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| -rwxrwxrwx    1 ftp      ftp       8138592 Sep 16 17:24 Calendar.pptx [NSE: writeable]
| drwxrwxrwx    4 ftp      ftp          4096 Sep 16 17:57 Clients [NSE: writeable]
| drwxrwxrwx    2 ftp      ftp          4096 Sep 16 18:05 Documents [NSE: writeable]
| drwxrwxrwx    2 ftp      ftp          4096 Sep 16 17:24 Employees [NSE: writeable]
| -rwxrwxrwx    1 ftp      ftp            41 Sep 16 17:24 Important Notes.txt [NSE: writeable]
|_-rwxrwxrwx    1 ftp      ftp             0 Sep 15 14:57 testupload.txt [NSE: writeable]
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 10.10.14.4
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
```

El análisis de scripts predeterminado se basa en las huellas dactilares, las respuestas y los puertos estándar de los servicios. Una vez que Nmap ha detectado el servicio, ejecuta los scripts marcados uno tras otro, proporcionando información diferente. Por ejemplo, el script [NSE ftp-anon](https://nmap.org/nsedoc/scripts/ftp-anon.html) comprueba si el servidor FTP permite el acceso anónimo. Si es así, el contenido del directorio raíz FTP se representa para el usuario anónimo.

El , por ejemplo, ejecuta el comando, que muestra información sobre el estado del servidor FTP. Esto incluye las configuraciones, así como la versión del servidor FTP. Nmap también proporciona la capacidad de rastrear el progreso de los scripts NSE a nivel de red si usamos la opción en nuestros escaneos. Esto nos permite ver qué comandos envía Nmap, qué puertos se utilizan y qué respuestas recibimos del servidor escaneado.`ftp-syst``STAT``--script-trace`

#### Seguimiento de script de Nmap

  FTP

```shell-session
zunderrubb@htb[/htb]$ sudo nmap -sV -p21 -sC -A 10.129.14.136 --script-trace

Starting Nmap 7.80 ( https://nmap.org ) at 2021-09-19 13:54 CEST                                                                                                                                                   
NSOCK INFO [11.4640s] nsock_trace_handler_callback(): Callback: CONNECT SUCCESS for EID 8 [10.129.14.136:21]                                   
NSOCK INFO [11.4640s] nsock_trace_handler_callback(): Callback: CONNECT SUCCESS for EID 16 [10.129.14.136:21]             
NSOCK INFO [11.4640s] nsock_trace_handler_callback(): Callback: CONNECT SUCCESS for EID 24 [10.129.14.136:21]
NSOCK INFO [11.4640s] nsock_trace_handler_callback(): Callback: CONNECT SUCCESS for EID 32 [10.129.14.136:21]
NSOCK INFO [11.4640s] nsock_read(): Read request from IOD #1 [10.129.14.136:21] (timeout: 7000ms) EID 42
NSOCK INFO [11.4640s] nsock_read(): Read request from IOD #2 [10.129.14.136:21] (timeout: 9000ms) EID 50
NSOCK INFO [11.4640s] nsock_read(): Read request from IOD #3 [10.129.14.136:21] (timeout: 7000ms) EID 58
NSOCK INFO [11.4640s] nsock_read(): Read request from IOD #4 [10.129.14.136:21] (timeout: 11000ms) EID 66
NSE: TCP 10.10.14.4:54226 > 10.129.14.136:21 | CONNECT
NSE: TCP 10.10.14.4:54228 > 10.129.14.136:21 | CONNECT
NSE: TCP 10.10.14.4:54230 > 10.129.14.136:21 | CONNECT
NSE: TCP 10.10.14.4:54232 > 10.129.14.136:21 | CONNECT
NSOCK INFO [11.4660s] nsock_trace_handler_callback(): Callback: READ SUCCESS for EID 50 [10.129.14.136:21] (41 bytes): 220 Welcome to HTB-Academy FTP service...
NSOCK INFO [11.4660s] nsock_trace_handler_callback(): Callback: READ SUCCESS for EID 58 [10.129.14.136:21] (41 bytes): 220 Welcome to HTB-Academy FTP service...
NSE: TCP 10.10.14.4:54228 < 10.129.14.136:21 | 220 Welcome to HTB-Academy FTP service.
```

El historial de análisis muestra que se están ejecutando cuatro exámenes paralelos diferentes en el servicio, con varios tiempos de espera. Para los scripts NSE, vemos que nuestra máquina local utiliza otros puertos de salida (, , , ) e inicia primero la conexión con el comando. Desde la primera respuesta del servidor, podemos ver que estamos recibiendo el banner del servidor a nuestro segundo script NSE () del servidor FTP de destino. Si es necesario, podemos, por supuesto, utilizar otras aplicaciones como o para interactuar con el servidor FTP.`54226``54228``54230``54232``CONNECT``54228``netcat``telnet`

#### Interacción con el servicio

  FTP

```shell-session
zunderrubb@htb[/htb]$ nc -nv 10.129.14.136 21
```

  FTP

```shell-session
zunderrubb@htb[/htb]$ telnet 10.129.14.136 21
```

Se ve ligeramente diferente si el servidor FTP se ejecuta con cifrado TLS/SSL. Porque entonces necesitamos un cliente que pueda manejar TLS/SSL. Para ello, podemos utilizar el cliente y comunicarnos con el servidor FTP. Lo bueno de usarlo es que podemos ver el certificado SSL, que también puede ser útil.`openssl``openssl`

  FTP

```shell-session
zunderrubb@htb[/htb]$ openssl s_client -connect 10.129.14.136:21 -starttls ftp

CONNECTED(00000003)                                                                                      
Can't use SSL_get_servername                        
depth=0 C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
verify error:num=18:self signed certificate
verify return:1

depth=0 C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
verify return:1
---                                                 
Certificate chain
 0 s:C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
 
 i:C = US, ST = California, L = Sacramento, O = Inlanefreight, OU = Dev, CN = master.inlanefreight.htb, emailAddress = admin@inlanefreight.htb
---
 
Server certificate

-----BEGIN CERTIFICATE-----

MIIENTCCAx2gAwIBAgIUD+SlFZAWzX5yLs2q3ZcfdsRQqMYwDQYJKoZIhvcNAQEL
...SNIP...
```

Esto se debe a que el certificado SSL nos permite reconocer el , por ejemplo, y en la mayoría de los casos también un para la organización o empresa. Además, si la empresa tiene varias ubicaciones en todo el mundo, también se pueden crear certificados para ubicaciones específicas, que también se pueden identificar mediante el certificado SSL.`hostname``email address`