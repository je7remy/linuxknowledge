
---------

#nmap #enumeration #firewall

-----------


`Nmap` nos da muchas formas diferentes de eludir los cortafuegos, las reglas y los IDS/IPS. Estos métodos incluyen la fragmentación de paquetes, el uso de señuelos y otros que discutiremos en esta sección.

---

## Cortafuegos

Un firewall es una medida de seguridad contra intentos de conexión no autorizados desde redes externas. Cada sistema de seguridad de firewall se basa en un componente de software que monitorea el tráfico de red entre el firewall y las conexiones de datos entrantes y decide cómo manejar la conexión en función de las reglas que se han establecido. Comprueba si los paquetes de red individuales se están pasando, ignorando o bloqueando. Este mecanismo está diseñado para evitar conexiones no deseadas que podrían ser potencialmente peligrosas.

---

## IDS/IPS

Al igual que el cortafuegos, el sistema de detección de intrusiones () y el sistema de prevención de intrusiones () también son componentes basados en software. Escanea la red en busca de posibles ataques, los analiza e informa de los ataques detectados. complementa la adopción de medidas defensivas específicas en caso de que se haya detectado un posible ataque. El análisis de estos ataques se basa en la coincidencia de patrones y firmas. Si se detectan patrones específicos, como un examen de detección de servicios, puede impedir los intentos de conexión pendientes.`IDS``IPS``IDS``IPS``IDS``IPS`

---

#### Determinar los cortafuegos y sus reglas

Ya sabemos que cuando un puerto se muestra como filtrado, puede tener varias razones. En la mayoría de los casos, los firewalls tienen ciertas reglas establecidas para manejar conexiones específicas. Los paquetes pueden ser , o . Los paquetes se ignoran y no se devuelve ninguna respuesta del host.`dropped``rejected``dropped`

Esto es diferente para los paquetes que se devuelven con una marca. Estos paquetes contienen diferentes tipos de códigos de error ICMP o no contienen nada en absoluto.`rejected``RST`

Dichos errores pueden ser:

- Red inalcanzable
- Prohibido el neto
- Host inalcanzable
- Anfitrión prohibido
- Puerto inalcanzable
- Proto Inalcanzable

El método TCP ACK scan () de Nmap es mucho más difícil de filtrar para firewalls y sistemas IDS/IPS que los escaneos SYN () o Connect () normales porque solo envían un paquete TCP con solo la bandera. Cuando un puerto está cerrado o abierto, el host debe responder con un indicador. A diferencia de las conexiones salientes, todos los intentos de conexión (con la bandera) de redes externas suelen estar bloqueados por firewalls. Sin embargo, los paquetes con el indicador a menudo son pasados por el firewall porque el firewall no puede determinar si la conexión se estableció primero desde la red externa o desde la red interna.`-sA``-sS``sT``ACK``RST``SYN``ACK`

Si nos fijamos en estos escaneos, veremos cómo difieren los resultados.

#### SYN-Scan

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p 21,22,25 -sS -Pn -n --disable-arp-ping --packet-trace

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-21 14:56 CEST
SENT (0.0278s) TCP 10.10.14.2:57347 > 10.129.2.28:22 S ttl=53 id=22412 iplen=44  seq=4092255222 win=1024 <mss 1460>
SENT (0.0278s) TCP 10.10.14.2:57347 > 10.129.2.28:25 S ttl=50 id=62291 iplen=44  seq=4092255222 win=1024 <mss 1460>
SENT (0.0278s) TCP 10.10.14.2:57347 > 10.129.2.28:21 S ttl=58 id=38696 iplen=44  seq=4092255222 win=1024 <mss 1460>
RCVD (0.0329s) ICMP [10.129.2.28 > 10.10.14.2 Port 21 unreachable (type=3/code=3) ] IP [ttl=64 id=40884 iplen=72 ]
RCVD (0.0341s) TCP 10.129.2.28:22 > 10.10.14.2:57347 SA ttl=64 id=0 iplen=44  seq=1153454414 win=64240 <mss 1460>
RCVD (1.0386s) TCP 10.129.2.28:22 > 10.10.14.2:57347 SA ttl=64 id=0 iplen=44  seq=1153454414 win=64240 <mss 1460>
SENT (1.1366s) TCP 10.10.14.2:57348 > 10.129.2.28:25 S ttl=44 id=6796 iplen=44  seq=4092320759 win=1024 <mss 1460>
Nmap scan report for 10.129.2.28
Host is up (0.0053s latency).

PORT   STATE    SERVICE
21/tcp filtered ftp
22/tcp open     ssh
25/tcp filtered smtp
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds
```

#### Escaneo ACK

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p 21,22,25 -sA -Pn -n --disable-arp-ping --packet-trace

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-21 14:57 CEST
SENT (0.0422s) TCP 10.10.14.2:49343 > 10.129.2.28:21 A ttl=49 id=12381 iplen=40  seq=0 win=1024
SENT (0.0423s) TCP 10.10.14.2:49343 > 10.129.2.28:22 A ttl=41 id=5146 iplen=40  seq=0 win=1024
SENT (0.0423s) TCP 10.10.14.2:49343 > 10.129.2.28:25 A ttl=49 id=5800 iplen=40  seq=0 win=1024
RCVD (0.1252s) ICMP [10.129.2.28 > 10.10.14.2 Port 21 unreachable (type=3/code=3) ] IP [ttl=64 id=55628 iplen=68 ]
RCVD (0.1268s) TCP 10.129.2.28:22 > 10.10.14.2:49343 R ttl=64 id=0 iplen=40  seq=1660784500 win=0
SENT (1.3837s) TCP 10.10.14.2:49344 > 10.129.2.28:25 A ttl=59 id=21915 iplen=40  seq=0 win=1024
Nmap scan report for 10.129.2.28
Host is up (0.083s latency).

PORT   STATE      SERVICE
21/tcp filtered   ftp
22/tcp unfiltered ssh
25/tcp filtered   smtp
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 0.15 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.28`|Examina el destino especificado.|
|`-p 21,22,25`|Analiza solo los puertos especificados.|
|`-sS`|Realiza un análisis SYN en los puertos especificados.|
|`-sA`|Realiza un análisis de confirmación en los puertos especificados.|
|`-Pn`|Deshabilita las solicitudes de eco ICMP.|
|`-n`|Deshabilita la resolución DNS.|
|`--disable-arp-ping`|Deshabilita el ping ARP.|
|`--packet-trace`|Muestra todos los paquetes enviados y recibidos.|

Preste atención a los paquetes RCVD y su indicador establecido que recibimos de nuestro objetivo. Con el escaneo SYN () nuestro objetivo intenta establecer la conexión TCP enviando un paquete de vuelta con los indicadores SYN-ACK () establecidos y con el escaneo ACK () obtenemos el indicador porque el puerto TCP 22 está abierto. Para el puerto TCP 25, no recibimos ningún paquete de vuelta, lo que indica que los paquetes se descartarán.`-sS``SA``-sA``RST`

---

## Detección de IDS/IPS

A diferencia de los firewalls y sus reglas, la detección de sistemas IDS/IPS es mucho más difícil porque se trata de sistemas pasivos de monitorización del tráfico. Examine todas las conexiones entre hosts. Si el IDS encuentra paquetes que contienen el contenido o las especificaciones definidas, se notifica al administrador y toma las medidas adecuadas en el peor de los casos.`IDS systems`

`IPS systems` Tomar medidas configuradas por el administrador de forma independiente para prevenir posibles ataques de forma automática. Es fundamental saber que IDS e IPS son aplicaciones diferentes y que IPS sirve como complemento a IDS.

Se recomiendan varios servidores privados virtuales () con diferentes direcciones IP para determinar si dichos sistemas están en la red de destino durante una prueba de penetración. Si el administrador detecta un ataque potencial de este tipo en la red de destino, el primer paso es bloquear la dirección IP de la que proviene el posible ataque. Como resultado, ya no podremos acceder a la red utilizando esa dirección IP, y nuestro proveedor de servicios de Internet () será contactado y bloqueado de todo acceso a Internet.`VPS``ISP`

- `IDS systems` Por lo general, están ahí para ayudar a los administradores a detectar posibles ataques en su red. A continuación, pueden decidir cómo manejar dichas conexiones. Podemos activar ciertas medidas de seguridad de un administrador, por ejemplo, escaneando agresivamente un solo puerto y su servicio. En función de si se toman medidas de seguridad específicas, podemos detectar si la red tiene alguna aplicación de monitorización o no.
    
- Un método para determinar si está presente en la red de destino es escanear desde un solo host (). Si en algún momento este host está bloqueado y no tiene acceso a la red de destino, sabemos que el administrador ha tomado algunas medidas de seguridad. En consecuencia, podemos continuar nuestra prueba de penetración con otro .`IPS system``VPS``VPS`
    

En consecuencia, sabemos que necesitamos ser más silenciosos con nuestros escaneos y, en el mejor de los casos, disimular todas las interacciones con la red de destino y sus servicios.

---

## Señuelos

Hay casos en los que, en principio, los administradores bloquean subredes específicas de diferentes regiones. Esto impide cualquier acceso a la red de destino. Otro ejemplo es cuando IPS debería bloquearnos. Por esta razón, el método de escaneo Señuelo () es la elección correcta. Con este método, Nmap genera varias direcciones IP aleatorias insertadas en el encabezado IP para disfrazar el origen del paquete enviado. Con este método, podemos generar aleatoriamente () un número específico (por ejemplo: ) de direcciones IP separadas por dos puntos (). Nuestra dirección IP real se coloca aleatoriamente entre las direcciones IP generadas. Por lo tanto, en el siguiente ejemplo, nuestra dirección IP real se coloca en la segunda posición. Otro punto crítico es que los señuelos deben estar vivos. De lo contrario, es posible que no se pueda acceder al servicio en el destino debido a los mecanismos de seguridad que inundan SYN.`-D``RND``5``:`

#### Escaneo mediante señuelos

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p 80 -sS -Pn -n --disable-arp-ping --packet-trace -D RND:5

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-21 16:14 CEST
SENT (0.0378s) TCP 102.52.161.59:59289 > 10.129.2.28:80 S ttl=42 id=29822 iplen=44  seq=3687542010 win=1024 <mss 1460>
SENT (0.0378s) TCP 10.10.14.2:59289 > 10.129.2.28:80 S ttl=59 id=29822 iplen=44  seq=3687542010 win=1024 <mss 1460>
SENT (0.0379s) TCP 210.120.38.29:59289 > 10.129.2.28:80 S ttl=37 id=29822 iplen=44  seq=3687542010 win=1024 <mss 1460>
SENT (0.0379s) TCP 191.6.64.171:59289 > 10.129.2.28:80 S ttl=38 id=29822 iplen=44  seq=3687542010 win=1024 <mss 1460>
SENT (0.0379s) TCP 184.178.194.209:59289 > 10.129.2.28:80 S ttl=39 id=29822 iplen=44  seq=3687542010 win=1024 <mss 1460>
SENT (0.0379s) TCP 43.21.121.33:59289 > 10.129.2.28:80 S ttl=55 id=29822 iplen=44  seq=3687542010 win=1024 <mss 1460>
RCVD (0.1370s) TCP 10.129.2.28:80 > 10.10.14.2:59289 SA ttl=64 id=0 iplen=44  seq=4056111701 win=64240 <mss 1460>
Nmap scan report for 10.129.2.28
Host is up (0.099s latency).

PORT   STATE SERVICE
80/tcp open  http
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 0.15 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.28`|Examina el destino especificado.|
|`-p 80`|Analiza solo los puertos especificados.|
|`-sS`|Realiza un análisis SYN en los puertos especificados.|
|`-Pn`|Deshabilita las solicitudes de eco ICMP.|
|`-n`|Deshabilita la resolución DNS.|
|`--disable-arp-ping`|Deshabilita el ping ARP.|
|`--packet-trace`|Muestra todos los paquetes enviados y recibidos.|
|`-D RND:5`|Genera cinco direcciones IP aleatorias que indican la IP de origen de la que procede la conexión.|

Los paquetes falsificados a menudo son filtrados por ISP y enrutadores, a pesar de que provienen del mismo rango de red. Por lo tanto, también podemos especificar las direcciones IP de nuestros servidores VPS y usarlas en combinación con la manipulación "" en los encabezados IP para escanear el objetivo.`IP ID`

Otro escenario sería que solo las subredes individuales no tendrían acceso a los servicios específicos del servidor. Por lo tanto, también podemos especificar manualmente la dirección IP de origen () para probar si obtenemos mejores resultados con este. Los señuelos se pueden utilizar para análisis SYN, ACK, ICMP y análisis de detección del sistema operativo. Así que echemos un vistazo a este ejemplo y determinemos qué sistema operativo es más probable que sea.`-S`

#### Prueba de la regla de firewall

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -n -Pn -p445 -O

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-22 01:23 CEST
Nmap scan report for 10.129.2.28
Host is up (0.032s latency).

PORT    STATE    SERVICE
445/tcp filtered microsoft-ds
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 3.14 seconds
```

#### Escaneo con diferentes IP de origen

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -n -Pn -p 445 -O -S 10.129.2.200 -e tun0

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-22 01:16 CEST
Nmap scan report for 10.129.2.28
Host is up (0.010s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Linux 2.6.32 (96%), Linux 3.2 - 4.9 (96%), Linux 2.6.32 - 3.10 (96%), Linux 3.4 - 3.10 (95%), Linux 3.1 (95%), Linux 3.2 (95%), AXIS 210A or 211 Network Camera (Linux 2.6.17) (94%), Synology DiskStation Manager 5.2-5644 (94%), Linux 2.6.32 - 2.6.35 (94%), Linux 2.6.32 - 3.5 (94%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 4.11 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.28`|Examina el destino especificado.|
|`-n`|Deshabilita la resolución DNS.|
|`-Pn`|Deshabilita las solicitudes de eco ICMP.|
|`-p 445`|Analiza solo los puertos especificados.|
|`-O`|Realiza un análisis de detección del sistema operativo.|
|`-S`|Examina el destino mediante una dirección IP de origen diferente.|
|`10.129.2.200`|Especifica la dirección IP de origen.|
|`-e tun0`|Envía todas las solicitudes a través de la interfaz especificada.|

---

## Proxy DNS

De forma predeterminada, realiza una resolución DNS inversa a menos que se especifique lo contrario para encontrar información más importante sobre nuestro objetivo. Estas consultas de DNS también se pasan en la mayoría de los casos porque se supone que el servidor web dado debe ser encontrado y visitado. Las consultas DNS se realizan a través del archivo . Anteriormente, solo se usaba para el llamado "" entre los servidores DNS o la transferencia de datos de más de 512 bytes. Cada vez más, esto está cambiando debido a las expansiones de IPv6 y DNSSEC. Estos cambios hacen que muchas solicitudes DNS se realicen a través del puerto TCP 53.`Nmap``UDP port 53``TCP port 53``Zone transfers`

Sin embargo, todavía nos da una forma de especificar los servidores DNS nosotros mismos (). Este método podría ser fundamental para nosotros si estamos en una zona de distensión (). Los servidores DNS de la empresa suelen ser más fiables que los de Internet. Así, por ejemplo, podríamos utilizarlos para interactuar con los hosts de la red interna. Como otro ejemplo, podemos usar como puerto de origen () para nuestros escaneos. Si el administrador utiliza el cortafuegos para controlar este puerto y no filtra IDS/IPS correctamente, nuestros paquetes TCP serán de confianza y se pasarán a través de ellos.`Nmap``--dns-server <ns>,<ns>``DMZ``TCP port 53``--source-port`

#### Escaneo SYN de un puerto filtrado

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p50000 -sS -Pn -n --disable-arp-ping --packet-trace

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-21 22:50 CEST
SENT (0.0417s) TCP 10.10.14.2:33436 > 10.129.2.28:50000 S ttl=41 id=21939 iplen=44  seq=736533153 win=1024 <mss 1460>
SENT (1.0481s) TCP 10.10.14.2:33437 > 10.129.2.28:50000 S ttl=46 id=6446 iplen=44  seq=736598688 win=1024 <mss 1460>
Nmap scan report for 10.129.2.28
Host is up.

PORT      STATE    SERVICE
50000/tcp filtered ibm-db2

Nmap done: 1 IP address (1 host up) scanned in 2.06 seconds
```

#### SYN-Scan desde el puerto DNS

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.28 -p50000 -sS -Pn -n --disable-arp-ping --packet-trace --source-port 53

SENT (0.0482s) TCP 10.10.14.2:53 > 10.129.2.28:50000 S ttl=58 id=27470 iplen=44  seq=4003923435 win=1024 <mss 1460>
RCVD (0.0608s) TCP 10.129.2.28:50000 > 10.10.14.2:53 SA ttl=64 id=0 iplen=44  seq=540635485 win=64240 <mss 1460>
Nmap scan report for 10.129.2.28
Host is up (0.013s latency).

PORT      STATE SERVICE
50000/tcp open  ibm-db2
MAC Address: DE:AD:00:00:BE:EF (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 0.08 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.28`|Examina el destino especificado.|
|`-p 50000`|Analiza solo los puertos especificados.|
|`-sS`|Realiza un análisis SYN en los puertos especificados.|
|`-Pn`|Deshabilita las solicitudes de eco ICMP.|
|`-n`|Deshabilita la resolución DNS.|
|`--disable-arp-ping`|Deshabilita el ping ARP.|
|`--packet-trace`|Muestra todos los paquetes enviados y recibidos.|
|`--source-port 53`|Realiza los análisis desde el puerto de origen especificado.|

---

Ahora que hemos descubierto que el cortafuegos acepta, es muy probable que los filtros IDS/IPS también estén configurados mucho más débiles que otros. Podemos probar esto tratando de conectarnos a este puerto usando .`TCP port 53``Netcat`

#### Conéctese al puerto filtrado

  Firewall y evasión de IDS/IPS

```shell-session
zunderrubb@htb[/htb]$ ncat -nv --source-port 53 10.129.2.28 50000

Ncat: Version 7.80 ( https://nmap.org/ncat )
Ncat: Connected to 10.129.2.28:50000.
220 ProFTPd
```


[[1- Comandos Basicos - Intermedio]]
**[[4- Análisis de la Red con Bash – PARTE 2]]** 
**[[6- Análisis de Red con TCPdump y WireShark – PARTE 1]]**
**[[1- Hoja de trucos NMAP]]**
**[[3- Análisis De La Red Desde Linux – Comandos Básicos Parte 1]]**
**[[4- nmap output]]**
[[2- nmap comands]]
[[5- nmap scripts]]
