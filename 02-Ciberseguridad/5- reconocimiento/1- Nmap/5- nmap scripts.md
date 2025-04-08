
---------

#nmap #enumeration #scripts

---------

|**Categoría**|**Descripción**|
|---|---|
|`auth`|Determinación de credenciales de autenticación.|
|`broadcast`|Los scripts, que se utilizan para la detección de hosts mediante la difusión y los hosts descubiertos, se pueden agregar automáticamente a los análisis restantes.|
|`brute`|Ejecuta scripts que intentan iniciar sesión en el servicio respectivo mediante fuerza bruta con credenciales.|
|`default`|Scripts predeterminados ejecutados mediante la opción.`-sC`|
|`discovery`|Evaluación de servicios accesibles.|
|`dos`|Estos scripts se utilizan para comprobar si los servicios tienen vulnerabilidades de denegación de servicio y se utilizan menos, ya que perjudica a los servicios.|
|`exploit`|Esta categoría de scripts intenta explotar vulnerabilidades conocidas para el puerto escaneado.|
|`external`|Scripts que utilizan servicios externos para su posterior procesamiento.|
|`fuzzer`|Esto utiliza scripts para identificar vulnerabilidades y manejo inesperado de paquetes mediante el envío de diferentes campos, lo que puede llevar mucho tiempo.|
|`intrusive`|Scripts intrusivos que podrían afectar negativamente al sistema de destino.|
|`malware`|Comprueba si algún malware infecta el sistema de destino.|
|`safe`|Scripts defensivos que no realizan accesos intrusivos y destructivos.|
|`version`|Extensión para la detección de servicios.|
|`vuln`|Identificación de vulnerabilidades específicas.|

Tenemos varias formas de definir los scripts deseados en .`Nmap`

#### Scripts predeterminados

  Motor de secuencias de comandos Nmap

```shell-session
zunderrubb@htb[/htb]$ sudo nmap <target> -sC
```

#### Categoría específica de scripts

  Motor de secuencias de comandos Nmap

```shell-session
zunderrubb@htb[/htb]$ sudo nmap <target> --script <category>
```

#### Scripts definidos

  Motor de secuencias de comandos Nmap

```shell-session
zunderrubb@htb[/htb]$ sudo nmap <target> --script <script-name>,<script-name>,...
```

Por ejemplo, sigamos trabajando con el puerto SMTP de destino y veamos los resultados que obtenemos con dos scripts definidos.

#### Nmap - Especificación de scripts

  Motor de secuencias de comandos Nmap

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p 25 --script banner,smtp-commands

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-16 23:21 CEST
Nmap scan report for 10.129.2.28
Host is up (0.050s latency).

PORT   STATE SERVICE
25/tcp open  smtp
|_banner: 220 inlane ESMTP Postfix (Ubuntu)
|_smtp-commands: inlane, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN, SMTPUTF8,
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.28`|Examina el destino especificado.|
|`-p 25`|Analiza solo el puerto especificado.|
|`--script banner,smtp-commands`|Utiliza scripts NSE especificados.|

Vemos que podemos reconocer la distribución **Ubuntu** de Linux usando el script 'banner'. El script nos muestra qué comandos podemos usar interactuando con el servidor SMTP de destino. En este ejemplo, dicha información puede ayudarnos a encontrar usuarios existentes en el objetivo. también nos da la posibilidad de escanear nuestro objetivo con la opción agresiva (). De este modo, se analiza el destino con varias opciones como detección de servicios (), detección del sistema operativo (), traceroute () y con los scripts NSE predeterminados ().`smtp-commands``Nmap``-A``-sV``-O``--traceroute``-sC`

#### Nmap - Escaneo Agresivo

  Motor de secuencias de comandos Nmap

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p 80 -A
Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-17 01:38 CEST
Nmap scan report for 10.129.2.28
Host is up (0.012s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-generator: WordPress 5.3.4
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: blog.inlanefreight.com
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Linux 2.6.32 (96%), Linux 3.2 - 4.9 (96%), Linux 2.6.32 - 3.10 (96%), Linux 3.4 - 3.10 (95%), Linux 3.1 (95%), Linux 3.2 (95%), 
AXIS 210A or 211 Network Camera (Linux 2.6.17) (94%), Synology DiskStation Manager 5.2-5644 (94%), Netgear RAIDiator 4.2.28 (94%), 
Linux 2.6.32 - 2.6.35 (94%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop

TRACEROUTE
HOP RTT      ADDRESS
1   11.91 ms 10.129.2.28

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.36 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.28`|Examina el destino especificado.|
|`-p 25`|Analiza solo el puerto especificado.|
|`-A`|Realiza la detección de servicios, la detección del sistema operativo, traceroute y utiliza scripts predeterminados para analizar el destino.|

Con la ayuda de la opción de escaneo utilizada (), descubrimos qué tipo de servidor web () se está ejecutando en el sistema, qué aplicación web () se utiliza y el título () de la página web. Además, muestra que es probable que sea () sistema operativo.`-A``Apache 2.4.29``WordPress 5.3.4``blog.inlanefreight.com``Nmap``Linux``96%`

---

## Evaluación de vulnerabilidades

Ahora pasemos al puerto HTTP 80 y veamos qué información y vulnerabilidades podemos encontrar usando la categoría de .`vuln``NSE`

#### Nmap - Categoría Vuln

  Motor de secuencias de comandos Nmap

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p 80 -sV --script vuln 

Nmap scan report for 10.129.2.28
Host is up (0.036s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-enum:
|   /wp-login.php: Possible admin folder
|   /readme.html: Wordpress version: 2
|   /: WordPress version: 5.3.4
|   /wp-includes/images/rss.png: Wordpress version 2.2 found.
|   /wp-includes/js/jquery/suggest.js: Wordpress version 2.5 found.
|   /wp-includes/images/blank.gif: Wordpress version 2.6 found.
|   /wp-includes/js/comment-reply.js: Wordpress version 2.7 found.
|   /wp-login.php: Wordpress login page.
|   /wp-admin/upgrade.php: Wordpress login page.
|_  /readme.html: Interesting, a readme.
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-stored-xss: Couldn't find any stored XSS vulnerabilities.
| http-wordpress-users:
| Username found: admin
|_Search stopped at ID #25. Increase the upper limit if necessary with 'http-wordpress-users.limit'
| vulners:
|   cpe:/a:apache:http_server:2.4.29:
|     	CVE-2019-0211	7.2	https://vulners.com/cve/CVE-2019-0211
|     	CVE-2018-1312	6.8	https://vulners.com/cve/CVE-2018-1312
|     	CVE-2017-15715	6.8	https://vulners.com/cve/CVE-2017-15715
<SNIP>
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.28`|Examina el destino especificado.|
|`-p 80`|Analiza solo el puerto especificado.|
|`-sV`|Realiza la detección de versiones de servicio en los puertos especificados.|
|`--script vuln`|Utiliza todos los scripts relacionados de la categoría especificada.|

Los scripts utilizados para el último escaneo interactúan con el servidor web y su aplicación web para obtener más información sobre sus versiones y verificar varias bases de datos para ver si hay vulnerabilidades conocidas. Más información sobre los scripts NSE y las categorías correspondientes la podemos encontrar en: [https://nmap.org/nsedoc/index.html](https://nmap.org/nsedoc/index.html)


**[[1- OSINT]]**
[[1- Hoja de trucos NMAP]]
[[2- nmap comands]]
[[3- nmap firewall evasion]]