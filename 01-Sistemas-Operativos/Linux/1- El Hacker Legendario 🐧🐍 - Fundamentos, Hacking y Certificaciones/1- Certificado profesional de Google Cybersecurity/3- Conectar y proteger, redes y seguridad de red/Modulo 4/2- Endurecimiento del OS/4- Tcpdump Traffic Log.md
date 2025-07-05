
---

**1. Resolución DNS de yummyrecipesforme.com**

```
14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A? yummyrecipesforme.com. (24)
14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084 1/0/0 A 203.0.113.22 (40)
```

- A las 14:18:32.192571, tu máquina (puerto 52444) envía al servidor DNS de Google una consulta de tipo A (IP v4) para “yummyrecipesforme.com”.
    
- A las 14:18:32.204388, el DNS responde con un único registro A: la dirección 203.0.113.22.
    

---

**2. Inicio del handshake TCP hacia yummyrecipesforme.com (puerto 80)**

```
14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [S], seq 2873951608, win 65495, options […], length 0
14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086: Flags [S.], seq 3984334959, ack 2873951609, win 65483, options […], length 0
14:18:36.786529 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [.], ack 1, win 512, options […], length 0
```

1. **SYN**: tu máquina (puerto 36086) inicia la conexión enviando un paquete con `Flags [S]`.
    
2. **SYN-ACK**: el servidor en yummyrecipesforme.com (puerto http/80) contesta con `Flags [S.]`, confirmando recepción.
    
3. **ACK**: tu máquina remata el handshake enviando `Flags [.]`, estableciendo ya la conexión.
    

---

**3. Petición HTTP GET**

```
14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options […], length 73: HTTP: GET / HTTP/1.1
14:18:36.786595 IP yummyrecipesforme.com.http > your.machine.36086: Flags [.], ack 74, win 512, options […], length 0
…<mucho tráfico en el puerto 80>…
```

- Con `Flags [P.]` tu máquina envía 73 bytes que contienen la petición `GET / HTTP/1.1`, solicitando la página principal.
    
- El servidor responde con un ACK (`Flags [.]`) confirmando recepción de esos 74 bytes.
    
- Luego se intercambia “mucho tráfico” — sería la transferencia de datos HTTP (carga útil, respuestas, etc.).
    

---

**4. Nueva resolución DNS y redirección a greatrecipesforme.com**

```
14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A? greatrecipesforme.com. (24)
14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899 1/0/0 A 192.0.2.17 (40)
```

- A las 14:20:32.192571 vuelve a usarse el puerto 52444 para preguntar al DNS por “greatrecipesforme.com”.
    
- El DNS responde que su IP es 192.0.2.17, indicando un posible cambio de destino (o sitio falsificado).
    

---

**5. Handshake y GET hacia el nuevo host spoofeado**

```
14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http: Flags [S], seq …, win 65495, options […], length 0
14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378: Flags [S.], seq …, ack …, win 65483, options […], length 0
14:25:29.576524 IP your.machine.56378 > greatrecipesforme.com.http: Flags [.], ack 1, win 512, options […], length 0
14:25:29.576590 IP your.machine.56378 > greatrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options […], length 73: HTTP: GET / HTTP/1.1
14:25:29.576597 IP greatrecipesforme.com.http > your.machine.56378: Flags [.], ack 74, win 512, options […], length 0
…<mucho tráfico en el puerto 80>…
```

1. **SYN** desde tu máquina (ahora puerto 56378) hacia greatrecipesforme.com (puerto 80).
    
2. **SYN-ACK** de vuelta del servidor.
    
3. **ACK** de tu máquina para cerrar el handshake.
    
4. **GET /** con `Flags [P.]`, idéntico al anterior, solicitando la página principal.
    
5. **ACK** de confirmación del servidor.
    
6. Se observa de nuevo “mucho tráfico” HTTP tras el GET.
    

---

**Conclusión:**

- Durante los primeros minutos el tráfico sigue el flujo normal a yummyrecipesforme.com.
    
- A las 14:20 se redirige a un segundo dominio (greatrecipesforme.com) con una IP distinta, y vuelve a iniciarse un nuevo flujo HTTP.
    
- Este cambio repentino de DNS y de puerto local es un indicio de posible redireccionamiento malicioso o sitio spoofeado.