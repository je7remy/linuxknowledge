
------------------------


--------------
## RDP

El Protocolo de escritorio remoto (en inglés: [Remote Desktop Protocol](https://docs.microsoft.com/en-us/troubleshoot/windows-server/remote/understanding-remote-desktop-protocol)) es un protocolo desarrollado por Microsoft para el acceso remoto a un equipo que ejecuta el sistema operativo Windows. Este protocolo permite que los comandos de visualización y control se transmitan a través de la GUI cifrados a través de redes IP. RDP funciona en la capa de aplicación en el modelo de referencia TCP/IP, normalmente utilizando el puerto TCP 3389 como protocolo de transporte. Sin embargo, el protocolo UDP sin conexión también puede utilizar el puerto 3389 para la administración remota.`RDP`

Para que se establezca una sesión RDP, tanto el firewall de red como el firewall del servidor deben permitir conexiones desde el exterior. Si se utiliza la [traducción de direcciones de red](https://en.wikipedia.org/wiki/Network_address_translation) () en la ruta entre el cliente y el servidor, como suele ocurrir con las conexiones a Internet, el equipo remoto necesita la dirección IP pública para llegar al servidor. Además, el reenvío de puertos debe configurarse en el router NAT en la dirección del servidor.`NAT`

RDP ha manejado la seguridad de la [capa de transporte](https://en.wikipedia.org/wiki/Transport_Layer_Security) () desde Windows Vista, lo que significa que todos los datos, y especialmente el proceso de inicio de sesión, están protegidos en la red por su buen cifrado. Sin embargo, muchos sistemas Windows no insisten en esto, pero aún aceptan un cifrado inadecuado a través [de RDP Security](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/8e8b2cca-c1fa-456c-8ecb-a82fc60b2322). Sin embargo, incluso con esto, un atacante todavía está lejos de ser bloqueado porque los certificados que proporcionan la identidad son simplemente autofirmados de forma predeterminada. Esto significa que el cliente no puede distinguir un certificado genuino de uno falsificado y genera una advertencia de certificado para el usuario.`TLS/SSL`

El servicio se instala de forma predeterminada en los servidores Windows y no requiere aplicaciones externas adicionales. Este servicio se puede activar mediante el comando y viene con la configuración predeterminada para permitir conexiones al servicio solo a hosts con [autenticación de nivel de red](https://en.wikipedia.org/wiki/Network_Level_Authentication) ().`Remote Desktop``Server Manager``NLA`

---

## Huella del servicio

Escanear el servicio RDP puede darnos rápidamente mucha información sobre el host. Por ejemplo, podemos determinar si está habilitado en el servidor o no, la versión del producto y el nombre de host.`NLA`

#### Nmap

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ nmap -sV -sC 10.129.201.248 -p3389 --script rdp*

Starting Nmap 7.92 ( https://nmap.org ) at 2021-11-06 15:45 CET
Nmap scan report for 10.129.201.248
Host is up (0.036s latency).

PORT     STATE SERVICE       VERSION
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-enum-encryption: 
|   Security layer
|     CredSSP (NLA): SUCCESS
|     CredSSP with Early User Auth: SUCCESS
|_    RDSTLS: SUCCESS
| rdp-ntlm-info: 
|   Target_Name: ILF-SQL-01
|   NetBIOS_Domain_Name: ILF-SQL-01
|   NetBIOS_Computer_Name: ILF-SQL-01
|   DNS_Domain_Name: ILF-SQL-01
|   DNS_Computer_Name: ILF-SQL-01
|   Product_Version: 10.0.17763
|_  System_Time: 2021-11-06T13:46:00+00:00
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.26 seconds
```

Además, podemos utilizar para rastrear los paquetes individuales e inspeccionar su contenido manualmente. Podemos ver que el () utilizado por Nmap para interactuar con el servidor RDP puede ser identificado por varios servicios de seguridad como [Endpoint Detection and Response](https://en.wikipedia.org/wiki/Endpoint_detection_and_response) (), y puede bloquearnos como probadores de penetración en redes reforzadas.`--packet-trace``RDP cookies``mstshash=nmap``threat hunters``EDR`

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ nmap -sV -sC 10.129.201.248 -p3389 --packet-trace --disable-arp-ping -n

Starting Nmap 7.92 ( https://nmap.org ) at 2021-11-06 16:23 CET
SENT (0.2506s) ICMP [10.10.14.20 > 10.129.201.248 Echo request (type=8/code=0) id=8338 seq=0] IP [ttl=53 id=5122 iplen=28 ]
SENT (0.2507s) TCP 10.10.14.20:55516 > 10.129.201.248:443 S ttl=42 id=24195 iplen=44  seq=1926233369 win=1024 <mss 1460>
SENT (0.2507s) TCP 10.10.14.20:55516 > 10.129.201.248:80 A ttl=55 id=50395 iplen=40  seq=0 win=1024
SENT (0.2517s) ICMP [10.10.14.20 > 10.129.201.248 Timestamp request (type=13/code=0) id=8247 seq=0 orig=0 recv=0 trans=0] IP [ttl=38 id=62695 iplen=40 ]
RCVD (0.2814s) ICMP [10.129.201.248 > 10.10.14.20 Echo reply (type=0/code=0) id=8338 seq=0] IP [ttl=127 id=38158 iplen=28 ]
SENT (0.3264s) TCP 10.10.14.20:55772 > 10.129.201.248:3389 S ttl=56 id=274 iplen=44  seq=2635590698 win=1024 <mss 1460>
RCVD (0.3565s) TCP 10.129.201.248:3389 > 10.10.14.20:55772 SA ttl=127 id=38162 iplen=44  seq=3526777417 win=64000 <mss 1357>
NSOCK INFO [0.4500s] nsock_iod_new2(): nsock_iod_new (IOD #1)
NSOCK INFO [0.4500s] nsock_connect_tcp(): TCP connection requested to 10.129.201.248:3389 (IOD #1) EID 8
NSOCK INFO [0.4820s] nsock_trace_handler_callback(): Callback: CONNECT SUCCESS for EID 8 [10.129.201.248:3389]
Service scan sending probe NULL to 10.129.201.248:3389 (tcp)
NSOCK INFO [0.4830s] nsock_read(): Read request from IOD #1 [10.129.201.248:3389] (timeout: 6000ms) EID 18
NSOCK INFO [6.4880s] nsock_trace_handler_callback(): Callback: READ TIMEOUT for EID 18 [10.129.201.248:3389]
Service scan sending probe TerminalServerCookie to 10.129.201.248:3389 (tcp)
NSOCK INFO [6.4880s] nsock_write(): Write request for 42 bytes to IOD #1 EID 27 [10.129.201.248:3389]
NSOCK INFO [6.4880s] nsock_read(): Read request from IOD #1 [10.129.201.248:3389] (timeout: 5000ms) EID 34
NSOCK INFO [6.4880s] nsock_trace_handler_callback(): Callback: WRITE SUCCESS for EID 27 [10.129.201.248:3389]
NSOCK INFO [6.5240s] nsock_trace_handler_callback(): Callback: READ SUCCESS for EID 34 [10.129.201.248:3389] (19 bytes): .........4.........
Service scan match (Probe TerminalServerCookie matched with TerminalServerCookie line 13640): 10.129.201.248:3389 is ms-wbt-server.  Version: |Microsoft Terminal Services|||

...SNIP...

NSOCK INFO [6.5610s] nsock_write(): Write request for 54 bytes to IOD #1 EID 27 [10.129.201.248:3389]
NSE: TCP 10.10.14.20:36630 > 10.129.201.248:3389 | 00000000: 03 00 00 2a 25 e0 00 00 00 00 00 43 6f 6f 6b 69    *%      Cooki
00000010: 65 3a 20 6d 73 74 73 68 61 73 68 3d 6e 6d 61 70 e: mstshash=nmap
00000020: 0d 0a 01 00 08 00 0b 00 00 00  

...SNIP...

NSOCK INFO [6.6820s] nsock_write(): Write request for 57 bytes to IOD #2 EID 67 [10.129.201.248:3389]
NSOCK INFO [6.6820s] nsock_trace_handler_callback(): Callback: WRITE SUCCESS for EID 67 [10.129.201.248:3389]
NSE: TCP 10.10.14.20:36630 > 10.129.201.248:3389 | SEND
NSOCK INFO [6.6820s] nsock_read(): Read request from IOD #2 [10.129.201.248:3389] (timeout: 5000ms) EID 74
NSOCK INFO [6.7180s] nsock_trace_handler_callback(): Callback: READ SUCCESS for EID 74 [10.129.201.248:3389] (211 bytes)
NSE: TCP 10.10.14.20:36630 < 10.129.201.248:3389 | 
00000000: 30 81 d0 a0 03 02 01 06 a1 81 c8 30 81 c5 30 81 0          0  0
00000010: c2 a0 81 bf 04 81 bc 4e 54 4c 4d 53 53 50 00 02        NTLMSSP
00000020: 00 00 00 14 00 14 00 38 00 00 00 35 82 8a e2 b9        8   5
00000030: 73 b0 b3 91 9f 1b 0d 00 00 00 00 00 00 00 00 70 s              p
00000040: 00 70 00 4c 00 00 00 0a 00 63 45 00 00 00 0f 49  p L     cE    I
00000050: 00 4c 00 46 00 2d 00 53 00 51 00 4c 00 2d 00 30  L F - S Q L - 0
00000060: 00 31 00 02 00 14 00 49 00 4c 00 46 00 2d 00 53  1     I L F - S
00000070: 00 51 00 4c 00 2d 00 30 00 31 00 01 00 14 00 49  Q L - 0 1     I
00000080: 00 4c 00 46 00 2d 00 53 00 51 00 4c 00 2d 00 30  L F - S Q L - 0
00000090: 00 31 00 04 00 14 00 49 00 4c 00 46 00 2d 00 53  1     I L F - S
000000a0: 00 51 00 4c 00 2d 00 30 00 31 00 03 00 14 00 49  Q L - 0 1     I
000000b0: 00 4c 00 46 00 2d 00 53 00 51 00 4c 00 2d 00 30  L F - S Q L - 0
000000c0: 00 31 00 07 00 08 00 1d b3 e8 f2 19 d3 d7 01 00  1
000000d0: 00 00 00

...SNIP...
```

[Cisco CX Security Labs](https://github.com/CiscoCXSecurity) también ha desarrollado un script Perl llamado [rdp-sec-check.pl](https://github.com/CiscoCXSecurity/rdp-sec-check) que puede identificar de forma no auténtica la configuración de seguridad de los servidores RDP en función de los protocolos de enlace.

#### Comprobación de seguridad RDP - Instalación

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ sudo cpan

Loading internal logger. Log::Log4perl recommended for better logging

CPAN.pm requires configuration, but most of it can be done automatically.
If you answer 'no' below, you will enter an interactive dialog for each
configuration option instead.

Would you like to configure as much as possible automatically? [yes] yes


Autoconfiguration complete.

commit: wrote '/root/.cpan/CPAN/MyConfig.pm'

You can re-run configuration any time with 'o conf init' in the CPAN shell

cpan shell -- CPAN exploration and modules installation (v2.27)
Enter 'h' for help.


cpan[1]> install Encoding::BER

Fetching with LWP:
http://www.cpan.org/authors/01mailrc.txt.gz
Reading '/root/.cpan/sources/authors/01mailrc.txt.gz'
............................................................................DONE
...SNIP...
```

#### Comprobación de seguridad RDP

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check
zunderrubb@htb[/htb]$ ./rdp-sec-check.pl 10.129.201.248

Starting rdp-sec-check v0.9-beta ( http://labs.portcullis.co.uk/application/rdp-sec-check/ ) at Sun Nov  7 16:50:32 2021

[+] Scanning 1 hosts

Target:    10.129.201.248
IP:        10.129.201.248
Port:      3389

[+] Checking supported protocols

[-] Checking if RDP Security (PROTOCOL_RDP) is supported...Not supported - HYBRID_REQUIRED_BY_SERVER
[-] Checking if TLS Security (PROTOCOL_SSL) is supported...Not supported - HYBRID_REQUIRED_BY_SERVER
[-] Checking if CredSSP Security (PROTOCOL_HYBRID) is supported [uses NLA]...Supported

[+] Checking RDP Security Layer

[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_NONE...Not supported
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_40BIT...Not supported
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_128BIT...Not supported
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_56BIT...Not supported
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_FIPS...Not supported

[+] Summary of protocol support

[-] 10.129.201.248:3389 supports PROTOCOL_SSL   : FALSE
[-] 10.129.201.248:3389 supports PROTOCOL_HYBRID: TRUE
[-] 10.129.201.248:3389 supports PROTOCOL_RDP   : FALSE

[+] Summary of RDP encryption support

[-] 10.129.201.248:3389 supports ENCRYPTION_METHOD_NONE   : FALSE
[-] 10.129.201.248:3389 supports ENCRYPTION_METHOD_40BIT  : FALSE
[-] 10.129.201.248:3389 supports ENCRYPTION_METHOD_128BIT : FALSE
[-] 10.129.201.248:3389 supports ENCRYPTION_METHOD_56BIT  : FALSE
[-] 10.129.201.248:3389 supports ENCRYPTION_METHOD_FIPS   : FALSE

[+] Summary of security issues


rdp-sec-check v0.9-beta completed at Sun Nov  7 16:50:33 2021
```

La autenticación y la conexión a dichos servidores RDP se pueden realizar de varias maneras. Por ejemplo, podemos conectarnos a servidores RDP en Linux usando , o , e interactuar con la GUI del servidor en consecuencia.`xfreerdp``rdesktop``Remmina`

#### Iniciar una sesión RDP

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248

[16:37:47:135] [95319:95320] [INFO][com.freerdp.core] - freerdp_connect:freerdp_set_last_error_ex resetting error state
[16:37:47:135] [95319:95320] [INFO][com.freerdp.client.common.cmdline] - loading channelEx rdpdr
[16:37:47:135] [95319:95320] [INFO][com.freerdp.client.common.cmdline] - loading channelEx rdpsnd
[16:37:47:135] [95319:95320] [INFO][com.freerdp.client.common.cmdline] - loading channelEx cliprdr
[16:37:47:447] [95319:95320] [INFO][com.freerdp.primitives] - primitives autodetect, using optimized
[16:37:47:453] [95319:95320] [INFO][com.freerdp.core] - freerdp_tcp_is_hostname_resolvable:freerdp_set_last_error_ex resetting error state
[16:37:47:453] [95319:95320] [INFO][com.freerdp.core] - freerdp_tcp_connect:freerdp_set_last_error_ex resetting error state
[16:37:47:523] [95319:95320] [INFO][com.freerdp.crypto] - creating directory /home/cry0l1t3/.config/freerdp
[16:37:47:523] [95319:95320] [INFO][com.freerdp.crypto] - creating directory [/home/cry0l1t3/.config/freerdp/certs]
[16:37:47:523] [95319:95320] [INFO][com.freerdp.crypto] - created directory [/home/cry0l1t3/.config/freerdp/server]
[16:37:47:599] [95319:95320] [WARN][com.freerdp.crypto] - Certificate verification failure 'self signed certificate (18)' at stack position 0
[16:37:47:599] [95319:95320] [WARN][com.freerdp.crypto] - CN = ILF-SQL-01
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] - @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] - @           WARNING: CERTIFICATE NAME MISMATCH!           @
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] - @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] - The hostname used for this connection (10.129.201.248:3389) 
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] - does not match the name given in the certificate:
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] - Common Name (CN):
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] -      ILF-SQL-01
[16:37:47:600] [95319:95320] [ERROR][com.freerdp.crypto] - A valid certificate for the wrong name should NOT be trusted!
Certificate details for 10.129.201.248:3389 (RDP-Server):
        Common Name: ILF-SQL-01
        Subject:     CN = ILF-SQL-01
        Issuer:      CN = ILF-SQL-01
        Thumbprint:  b7:5f:00:ca:91:00:0a:29:0c:b5:14:21:f3:b0:ca:9e:af:8c:62:d6:dc:f9:50:ec:ac:06:38:1f:c5:d6:a9:39
The above X.509 certificate could not be verified, possibly because you do not have
the CA certificate in your certificate store, or the certificate has expired.
Please look at the OpenSSL documentation on how to add a private CA to the store.


Do you trust the above certificate? (Y/T/N) y

[16:37:48:801] [95319:95320] [INFO][com.winpr.sspi.NTLM] - VERSION ={
[16:37:48:801] [95319:95320] [INFO][com.winpr.sspi.NTLM] -      ProductMajorVersion: 6
[16:37:48:801] [95319:95320] [INFO][com.winpr.sspi.NTLM] -      ProductMinorVersion: 1
[16:37:48:801] [95319:95320] [INFO][com.winpr.sspi.NTLM] -      ProductBuild: 7601
[16:37:48:801] [95319:95320] [INFO][com.winpr.sspi.NTLM] -      Reserved: 0x000000
```

Tras una autenticación exitosa, aparecerá una nueva ventana con acceso al escritorio del servidor al que nos hemos conectado.

---

## WinRM

La administración remota de Windows () es un protocolo simple de administración remota integrado de Windows basado en la línea de comandos. WinRM utiliza el protocolo simple de acceso a objetos () para establecer conexiones con hosts remotos y sus aplicaciones. Por lo tanto, WinRM debe estar habilitado y configurado explícitamente a partir de Windows 10. WinRM se basa en los puertos y para la comunicación, con el último puerto, ya que los puertos 80 y 443 se usaban anteriormente para esta tarea. Sin embargo, dado que el puerto 80 se bloqueó principalmente por razones de seguridad, los puertos más nuevos 5985 y 5986 se utilizan hoy en día.`WinRM``SOAP``TCP``5985``5986``5986 using HTTPS`

Otro componente que se ajusta a WinRM para la administración es Windows Remote Shell (), que nos permite ejecutar comandos arbitrarios en el sistema remoto. El programa incluso está incluido en Windows 7 de forma predeterminada. Por lo tanto, con WinRM, es posible ejecutar un comando remoto en otro servidor.`WinRS`

Los servicios como las sesiones remotas con PowerShell y la combinación de registros de eventos requieren WinRM. Está habilitado de forma predeterminada a partir de la versión, pero primero debe configurarse para versiones de servidor y clientes anteriores, y crear las excepciones de firewall necesarias.`Windows Server 2012`

---

## Huella del servicio

Como ya sabemos, WinRM utiliza por defecto los puertos TCP () y (), que podemos escanear usando Nmap. Sin embargo, a menudo veremos que solo se usa HTTP () en lugar de HTTPS ().`5985``HTTP``5986``HTTPS``TCP 5985``TCP 5986`

#### Nmap WinRM

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ nmap -sV -sC 10.129.201.248 -p5985,5986 --disable-arp-ping -n

Starting Nmap 7.92 ( https://nmap.org ) at 2021-11-06 16:31 CET
Nmap scan report for 10.129.201.248
Host is up (0.030s latency).

PORT     STATE SERVICE VERSION
5985/tcp open  http    Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 7.34 seconds
```

Si queremos saber si se puede acceder a uno o más servidores remotos a través de WinRM, podemos hacerlo fácilmente con la ayuda de PowerShell. El cmdlet [Test-WsMan](https://docs.microsoft.com/en-us/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2) es responsable de esto y se le pasa el nombre del host en cuestión. En entornos basados en Linux, podemos utilizar la herramienta llamada [evil-winrm](https://github.com/Hackplayers/evil-winrm), otra herramienta de pruebas de penetración diseñada para interactuar con WinRM.

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ evil-winrm -i 10.129.201.248 -u Cry0l1t3 -p P455w0rD!

Evil-WinRM shell v3.3

Warning: Remote path completions is disabled due to ruby limitation: quoting_detection_proc() function is unimplemented on this machine

Data: For more information, check Evil-WinRM Github: https://github.com/Hackplayers/evil-winrm#Remote-path-completion

Info: Establishing connection to remote endpoint

*Evil-WinRM* PS C:\Users\Cry0l1t3\Documents>
```

---

## WMI (en inglés)

Instrumental de administración de Windows () es la implementación de Microsoft y también una extensión del modelo de información común (), funcionalidad principal de la administración empresarial basada en web estandarizada () para la plataforma Windows. WMI permite el acceso de lectura y escritura a casi todas las configuraciones de los sistemas Windows. Comprensiblemente, esto la convierte en la interfaz más crítica en el entorno Windows para la administración y el mantenimiento remoto de computadoras con Windows, independientemente de si son PC o servidores. Normalmente, se accede a WMI a través de PowerShell, VBScript o la Consola de Instrumental de administración de Windows (). WMI no es un solo programa, sino que consta de varios programas y varias bases de datos, también conocidas como repositorios.`WMI``CIM``WBEM``WMIC`

---

## Huella del servicio

La inicialización de la comunicación WMI siempre tiene lugar en el puerto y, después del establecimiento correcto de la conexión, la comunicación se mueve a un puerto aleatorio. Por ejemplo, para ello se puede utilizar el [wmiexec.py](https://github.com/SecureAuthCorp/impacket/blob/master/examples/wmiexec.py) de programa del kit de herramientas Impacket.`TCP``135`

#### WMIexec.py

  Protocolos de administración remota de Windows

```shell-session
zunderrubb@htb[/htb]$ /usr/share/doc/python3-impacket/examples/wmiexec.py Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"

Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation

[*] SMBv3.0 dialect used
ILF-SQL-01
```