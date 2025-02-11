
--------------

#nmap #enumeration 

---------

El rendimiento del escaneo juega un papel importante cuando necesitamos escanear una red extensa o estamos lidiando con un ancho de banda de red bajo. Podemos usar varias opciones para saber qué tan rápido (), con qué frecuencia (), qué tiempos de espera () deben tener los paquetes de prueba, cuántos paquetes deben enviarse simultáneamente (), y con el número de reintentos () para los puertos escaneados se deben escanear los objetivos.`Nmap``-T <0-5>``--min-parallelism <number>``--max-rtt-timeout <time>``--min-rate <number>``--max-retries <number>`

---

## Timeouts

Cuando Nmap envía un paquete, tarda algún tiempo ( - ) en recibir una respuesta del puerto escaneado. Generalmente, comienza con un tiempo de espera alto () de 100 ms. Veamos un ejemplo escaneando toda la red con 256 hosts, incluidos los 100 puertos principales.`Round-Trip-Time``RTT``Nmap``--min-RTT-timeout`

#### Análisis predeterminado

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F

<SNIP>
Nmap done: 256 IP addresses (10 hosts up) scanned in 39.44 seconds
```

#### RTT optimizado

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F --initial-rtt-timeout 50ms --max-rtt-timeout 100ms

<SNIP>
Nmap done: 256 IP addresses (8 hosts up) scanned in 12.29 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.0/24`|Explora la red de destino especificada.|
|`-F`|Analiza los 100 puertos principales.|
|`--initial-rtt-timeout 50ms`|Establece el valor de tiempo especificado como tiempo de espera RTT inicial.|
|`--max-rtt-timeout 100ms`|Establece el valor de tiempo especificado como tiempo de espera RTT máximo.|

Al comparar los dos escaneos, podemos ver que encontramos dos hosts menos con el escaneo optimizado, pero el escaneo tomó solo una cuarta parte del tiempo. A partir de esto, podemos concluir que establecer el tiempo de espera RTT inicial () en un período de tiempo demasiado corto puede hacer que pasemos por alto los hosts.`--initial-rtt-timeout`

---

## Número máximo de reintentos

Otra forma de aumentar la velocidad de los análisis es especificar la tasa de reintento de los paquetes enviados (). El valor predeterminado para la tasa de reintentos es , por lo que si no recibe una respuesta para un puerto, no enviará más paquetes al puerto y se omitirá.`--max-retries``10``Nmap`

#### Análisis predeterminado

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F | grep "/tcp" | wc -l

23
```

#### Reducción de reintentos

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F --max-retries 0 | grep "/tcp" | wc -l

21
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.0/24`|Explora la red de destino especificada.|
|`-F`|Analiza los 100 puertos principales.|
|`--max-retries 0`|Establece el número de reintentos que se realizarán durante el examen.|

Una vez más, reconocemos que acelerar también puede tener un efecto negativo en nuestros resultados, lo que significa que podemos pasar por alto información importante.

---

## Tarifas

Durante una prueba de penetración de caja blanca, es posible que nos incluyan en la lista blanca de los sistemas de seguridad para verificar los sistemas en la red en busca de vulnerabilidades y no solo probar las medidas de protección. Si conocemos el ancho de banda de la red, podemos trabajar con la velocidad de paquetes enviados, lo que acelera significativamente nuestros escaneos con . Al establecer la velocidad mínima () para el envío de paquetes, le decimos que envíe simultáneamente el número especificado de paquetes. Tratará de mantener la tasa en consecuencia.`Nmap``--min-rate <number>``Nmap`

#### Análisis predeterminado

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F -oN tnet.default

<SNIP>
Nmap done: 256 IP addresses (10 hosts up) scanned in 29.83 seconds
```

#### Escaneo optimizado

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F -oN tnet.minrate300 --min-rate 300

<SNIP>
Nmap done: 256 IP addresses (10 hosts up) scanned in 8.67 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.0/24`|Explora la red de destino especificada.|
|`-F`|Analiza los 100 puertos principales.|
|`-oN tnet.minrate300`|Guarda los resultados en formatos normales, iniciando el nombre de archivo especificado.|
|`--min-rate 300`|Establece el número mínimo de paquetes que se enviarán por segundo.|

---

#### Escaneo predeterminado: puertos abiertos encontrados

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ cat tnet.default | grep "/tcp" | wc -l

23
```

#### Escaneo optimizado: puertos abiertos encontrados

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ cat tnet.minrate300 | grep "/tcp" | wc -l

23
```

---

## Cronometraje

Debido a que estos ajustes no siempre se pueden optimizar manualmente, como en una prueba de penetración de caja negra, ofrece seis plantillas de tiempo diferentes () para que las utilicemos. Estos valores () determinan la agresividad de nuestros escaneos. Esto también puede tener efectos negativos si el escaneo es demasiado agresivo, y los sistemas de seguridad pueden bloquearnos debido al tráfico de red producido. La plantilla de temporización predeterminada que se usa cuando no hemos definido nada más es la normal ().`Nmap``-T <0-5>``0-5``-T 3`

- `-T 0` / `-T paranoid`
- `-T 1` / `-T sneaky`
- `-T 2` / `-T polite`
- `-T 3` / `-T normal`
- `-T 4` / `-T aggressive`
- `-T 5` / `-T insane`

Estas plantillas contienen opciones que también podemos configurar manualmente, y ya hemos visto algunas de ellas. Los desarrolladores determinaron los valores establecidos para estas plantillas de acuerdo con sus mejores resultados, lo que nos facilitó adaptar nuestros escaneos al entorno de red correspondiente. Las opciones exactas utilizadas con sus valores las podemos encontrar aquí: [https://nmap.org/book/performance-timing-templates.html](https://nmap.org/book/performance-timing-templates.html)

#### Análisis predeterminado

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F -oN tnet.default 

<SNIP>
Nmap done: 256 IP addresses (10 hosts up) scanned in 32.44 seconds
```

#### Escaneo loco

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.2.0/24 -F -oN tnet.T5 -T 5

<SNIP>
Nmap done: 256 IP addresses (10 hosts up) scanned in 18.07 seconds
```

|**Opciones de escaneo**|**Descripción**|
|---|---|
|`10.129.2.0/24`|Explora la red de destino especificada.|
|`-F`|Analiza los 100 puertos principales.|
|`-oN tnet.T5`|Guarda los resultados en formatos normales, iniciando el nombre de archivo especificado.|
|`-T 5`|Especifica la plantilla de temporización insensata.|

---

#### Escaneo predeterminado: puertos abiertos encontrados

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ cat tnet.default | grep "/tcp" | wc -l

23
```

#### Escaneo loco - Puertos abiertos encontrados

  Rendimiento

```shell-session
zunderrubb@htb[/htb]$ cat tnet.T5 | grep "/tcp" | wc -l

23
```