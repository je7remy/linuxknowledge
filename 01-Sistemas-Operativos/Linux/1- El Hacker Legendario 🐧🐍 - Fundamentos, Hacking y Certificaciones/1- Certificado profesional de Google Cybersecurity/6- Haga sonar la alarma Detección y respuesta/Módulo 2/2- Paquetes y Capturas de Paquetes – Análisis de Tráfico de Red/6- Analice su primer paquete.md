
## **Resumen de la actividad**

Como analista de seguridad, deberás examinar el tráfico de red para saber qué tipo de tráfico se envía hacia y desde los sistemas de las redes con las que trabajes.

Anteriormente, aprendiste sobre la captura y el análisis de paquetes. El análisis de paquetes puede ayudar a los equipos de seguridad a interpretar y comprender las comunicaciones de red. Los analizadores de protocolos de red como **Wireshark**, que tiene una interfaz gráfica de usuario o GUI, pueden ayudarte a examinar los datos de paquetes durante tus investigaciones. Dado que los datos de paquetes de red son complejos, los analizadores de protocolos de red (detectores de paquetes) como Wireshark están diseñados para ayudarte a encontrar patrones y filtrar los datos a fin de concentrarse en el tráfico de red más relevante para tus investigaciones de seguridad.

Ahora, usarás Wireshark para inspeccionar datos de paquetes y aplicar filtros con el objetivo de ordenar la información de paquetes de manera eficiente.

En este lab, usarás Wireshark para analizar un archivo de captura de paquetes de muestra y filtrar los datos de tráfico de red.

---

## **Situación**

En esta situación, tu trabajo es investigar el tráfico a un sitio web como analista de seguridad.

Analizarás un archivo de captura de paquetes de red que contiene datos de tráfico relacionados con un usuario que se conecta a un sitio de Internet. La capacidad de filtrar el tráfico de red con detectores de paquetes para recopilar información pertinente es una habilidad esencial para un analista de seguridad.

Debes filtrar los datos para hacer lo siguiente:

- Identificar las direcciones IP de origen y de destino involucradas en esta sesión de navegación web.
    
- Examinar los protocolos que se utilizan cuando el usuario se conecta al sitio web.
    
- Analizar algunos de los paquetes de datos para identificar el tipo de información enviada y recibida por los sistemas que se conectan entre sí cuando se capturan los datos de red.
    

Estos son los pasos que seguirás:

1. **En primer lugar**, abrirás el archivo de captura de paquetes y explorarás la interfaz gráfica de usuario básica de Wireshark.
    
2. **En segundo lugar**, abrirás una vista detallada de un paquete individual y explorarás cómo examinar las diferentes capas de protocolos y datos dentro de un paquete de red.
    
3. **En tercer lugar**, aplicarás filtros para seleccionar e inspeccionar paquetes según criterios específicos.
    
4. **En cuarto lugar**, filtrarás e inspeccionarás el tráfico de DNS por UDP para examinar los datos de protocolo.
    
5. **Por último**, aplicarás filtros a los datos de un paquete de TCP para buscar datos de texto específicos de la carga útil.
    

Ya está todo listo para que uses Wireshark con el objetivo de inspeccionar datos de paquetes de red.

**Renuncia de responsabilidad:** Para obtener un rendimiento y una compatibilidad óptimos, se recomienda que uses los navegadores **Google Chrome** o **Mozilla Firefox** para acceder a los labs.

---

## **Comienza el lab**

Para poder acceder a los materiales, primero debes comenzar el lab. Para hacerlo, haz clic en el botón verde **"Comenzar lab"** en la parte superior de la pantalla.

Luego de que hagas clic en el botón **"Comenzar lab"**, en el lugar donde estaba el botón de comenzar lab aparecerá un panel que tiene el botón **Abrir la VM de Windows**.

Haz clic en el botón **Abrir la VM de Windows** y se abrirá una nueva pestaña con una interfaz visual para Windows OS. Allí realizarás más pasos en el lab. Deberías tener una interfaz visual para Windows que se vea así:

**Nota:** Si la VM de Windows se detiene y se desconecta de forma automática, puedes volver a conectarla de las siguientes maneras:

- Regresa a la página del lab y vuelve a hacer clic en **Abrir la VM de Windows**. De esta forma, volverás a conectarte a la misma VM de Windows.
    
- Usa las siguientes credenciales en la página de acceso y no realices cambios en los otros campos:
    
    - **Servidor:** localhost
        
    - **Nombre de usuario:** qwiklabs
        
    - **Contraseña:** qwiklabs-bb-8f893ffa-622a-485a-bb2c-3ff506775a4d
        

---

## **Tarea 1: Explora datos con Wireshark**

En esta tarea, debes abrir un archivo de captura de paquetes de red que contiene datos capturados de un sistema que realizó solicitudes web a un sitio. Abrirás estos datos con Wireshark para obtener un panorama de cómo se muestran los datos en la aplicación.

1. Para abrir el archivo de captura de paquetes, haz doble clic en el archivo de **ejemplo** que se encuentra en el escritorio de Windows. Esta acción iniciará Wireshark.
    
    El archivo de captura de paquetes tiene el ícono de archivo de captura de paquetes de Wireshark, que muestra la aleta de un tiburón. Este archivo tiene una extensión **.pcap** que está oculta de forma predeterminada.
    
    **Nota:** Es posible que aparezca un cuadro de diálogo con el título **Software Update**. Haz clic en **Skip this version**.
    
2. Haz doble clic en la barra de título de Wireshark junto al nombre de archivo **sample.pcap** para maximizar la ventana.
    
    Se mostrará una lista con una gran cantidad de tráfico de paquetes de red. A continuación, te mostramos una descripción general de las columnas:
    
    - **No.:** El número de índice del paquete.
        
    - **Time:** La marca de tiempo.
        
    - **Source:** La dirección IP de origen.
        
    - **Destination:** La dirección IP de destino.
        
    - **Protocol:** El protocolo contenido en el paquete.
        
    - **Length:** La longitud total del paquete.
        
    - **Info:** Información sobre los datos en el paquete.
        
3. Desplázate hacia abajo en la lista de paquetes hasta que aparezca un paquete donde la columna de información comience con las palabras **"Echo (ping) request"**.
    

❓ **¿Cuál es el protocolo del primer paquete de la lista donde la columna de información comienza con las palabras 'Echo (ping) request'?**

- [ ] HTTP
    
- [ ] SSH
    
- [x] ICMP
    
- [ ] TCP
    

---

## **Tarea 2: Aplica un filtro de Wireshark básico e inspecciona un paquete**

En esta tarea, abrirás un paquete en Wireshark para realizar una exploración más detallada.

1. Ingresa el siguiente filtro en el cuadro de texto **Apply a display filter…**: `ip.addr == 142.250.1.139` y presiona **Intro**.
    
2. Haz doble clic en el primer paquete de la lista que tenga **TCP** como protocolo. Se abrirá una ventana de detalles.
    
    - **Frame:** Detalles sobre el paquete de red general.
        
    - **Ethernet II:** Detalles a nivel de Ethernet (direcciones MAC).
        
    - **Internet Protocol Version 4:** Datos relacionados con el Protocolo de Internet (IP).
        
    - **Transmission Control Protocol:** Información detallada sobre el paquete de TCP (puertos, secuencias, etc.).
        

❓ **¿Cuál es el puerto de destino TCP de este paquete TCP?**

- [ ] 66
    
- [ ] 53
    
- [x] 80
    
- [ ] 200
    

3. Haz clic en el ícono **X** para cerrar la ventana de inspección y luego haz clic en el ícono **X Clear display filter** para quitar el filtro.
    

---

## **Tarea 3: Usa filtros para seleccionar paquetes**

En esta tarea, usarás filtros para analizar paquetes según su origen, destino o dirección MAC.

1. Filtra por IP de origen: `ip.src == 142.250.1.139`
    
2. Limpia el filtro.
    
3. Filtra por IP de destino: `ip.dst == 142.250.1.139`
    
4. Limpia el filtro.
    
5. Filtra por dirección MAC: `eth.addr == 42:01:ac:15:e0:02`
    
6. Haz doble clic en el primer paquete de la lista y expande el subárbol **Internet Protocol Version 4**.
    

❓ **¿Cuál es el protocolo contenido en el subárbol Internet Protocol Version 4 del primer paquete relacionado con la dirección MAC 42:01:ac:15:e0:02?**

- [ ] ICMP
    
- [x] TCP
    
- [ ] UDP
    
- [ ] ESP
    

7. Cierra la ventana de inspección y limpia el filtro.
    

---

## **Tarea 4: Usa filtros para explorar paquetes de DNS**

En esta tarea, usarás filtros para seleccionar y examinar el tráfico de DNS.

1. Ingresa el siguiente filtro para seleccionar el tráfico del puerto UDP 53 (DNS): `udp.port == 53`
    
2. Haz doble clic en el primer paquete, expande el subárbol **Domain Name System (query)** y luego **Queries**. Verás que el nombre consultado es **opensource.google.com**.
    
3. Cierra la ventana. Haz doble clic en el cuarto paquete de la lista.
    
4. Expande el subárbol **Domain Name System (query)** y luego **Answers**.
    

❓ **¿Cuál de estas direcciones IP se muestra en la sección Answers expandida?**

- [ ] 139.1.250.142
    
- [x] 142.250.1.139
    
- [ ] 169.254.169.254
    
- [ ] 172.21.224.1
    

5. Cierra la ventana de inspección y limpia el filtro.
    

---

## **Tarea 5: Usa filtros para explorar paquetes de TCP**

En esta tarea, usarás filtros adicionales para examinar paquetes de TCP.

1. Ingresa el siguiente filtro para tráfico web (puerto 80): `tcp.port == 80`
    
2. Haz doble clic en el primer paquete de la lista (IP de destino **169.254.169.254**).
    

❓ **¿Cuál es el valor de Time to Live del paquete como se especifica en el subárbol Internet Protocol Version 4?**

- [ ] 16
    
- [ ] 128
    
- [ ] 32
    
- [x] 64
    

❓ **¿Cuál es el valor de Frame Length del paquete como se especifica en el subárbol Frame?**

- [ ] 60 bytes
    
- [x] 54 bytes
    
- [ ] 40 bytes
    
- [ ] 74 bytes
    

❓ **¿Cuál es el valor de Header Length del paquete como se especifica en el subárbol Internet Protocol Version 4?**

- [ ] 54 bytes
    
- [ ] 60 bytes
    
- [x] 20 bytes
    
- [ ] 74 bytes
    

❓ **¿Cuál es el valor de Destination Address como se especifica en el subárbol Internet Protocol Version 4?**

- [x] 169.254.169.254
    
- [ ] 142.250.1.139
    
- [ ] 239.1.250.142
    
- [ ] 172.21.224.2
    

3. Cierra la ventana de inspección y limpia el filtro.
    
4. Ingresa el siguiente filtro para buscar texto específico: `tcp contains "curl"` y presiona **Intro**. Esto filtra los paquetes que contienen solicitudes web realizadas con el comando **curl**.
    

---

## **Conclusión**

**¡Muy bien!**

Ahora tienes experiencia práctica en el uso de Wireshark para:

- Abrir archivos de captura de paquetes guardados.
    
- Visualizar datos de paquetes de alto nivel.
    
- Usar filtros para inspeccionar datos de paquetes detallados.
    

Este es un hito importante en tu recorrido para aprender a usar las herramientas de análisis de paquetes de red.

---

## **Finaliza el lab**

Antes de finalizar el lab, asegúrate de haber completado todas las tareas.

1. Haz clic en **End Lab** y, luego, en **Submit**.
    
2. Después de finalizar, aparecerá un diálogo de encuesta.
    
3. Cierra la pestaña del navegador del lab para volver al curso.
    
4. Actualiza la pestaña del navegador del curso para marcar este elemento como completo.


---


# Repaso:

## Resumen de la actividad

Como analista de seguridad, examinarás el tráfico de red para comprender:
- Qué tipo de tráfico se envía hacia y desde los sistemas.  
- Cómo identificar direcciones IP de origen y destino.  
- Qué protocolos se utilizan y qué información se envía o recibe.

Herramienta principal: **Wireshark**, un analizador de protocolos de red (GUI) que permite:
- Filtrar paquetes según criterios específicos.
- Inspeccionar datos de diferentes capas (Ethernet, IP, TCP/UDP, DNS).

---

## Tarea 1: Explora datos con Wireshark
1. Abre el archivo de captura de paquetes `sample.pcap`.
2. Observa la interfaz de tres paneles de Wireshark:  
   - **Lista de paquetes**: resumen de todos los paquetes.  
   - **Detalles del paquete**: información de capas y protocolos.  
   - **Datos del paquete**: hexadecimal y ASCII de la carga útil.
3. Revisa columnas clave:
   - No., Time, Source, Destination, Protocol, Length, Info.
4. Observa los colores de paquetes: azul claro para DNS, verde para TCP/HTTP, etc.
5. Identifica el protocolo del primer paquete "Echo (ping) request":  
   ✅ **ICMP**

---

## Tarea 2: Aplica un filtro básico e inspecciona un paquete
1. Filtra paquetes con dirección IP específica:  
```

ip.addr == 142.250.1.139

```
2. Haz doble clic en el primer paquete TCP y explora subárboles:
- **Frame:** longitud total y hora de llegada.  
- **Ethernet II:** direcciones MAC origen/destino.  
- **IPv4:** direcciones IP, protocolo interno (TCP/UDP).  
- **TCP:** puertos origen/destino, secuencias y flags.
3. Puerto de destino TCP:  
✅ **80**

---

## Tarea 3: Usa filtros para seleccionar paquetes
1. Filtra por IP de origen:  
```

ip.src == 142.250.1.139

```
2. Filtra por IP de destino:  
```

ip.dst == 142.250.1.139

```
3. Filtra por dirección MAC de Ethernet:  
```

eth.addr == 42:01:ac:15:e0:02

```
4. Protocolo contenido en IPv4:  
✅ **TCP**

---

## Tarea 4: Explora paquetes de DNS
1. Filtra tráfico DNS (puerto UDP 53):  
```

udp.port == 53

```
2. Examina subárbol **Domain Name System**:  
- Queries: nombres consultados  
- Answers: direcciones IP devueltas  
3. Dirección IP de `opensource.google.com` en Answers:  
✅ **142.250.1.139**

---

## Tarea 5: Explora paquetes de TCP
1. Filtra tráfico TCP (puerto 80):  
```

tcp.port == 80

```
2. Inspecciona subárbol IPv4 de un paquete TCP:
- **Time to Live (TTL):** 64  
- **Frame Length:** 54 bytes  
- **Header Length:** 20 bytes  
- **Destination Address:** 169.254.169.254
3. Filtra paquetes TCP con datos de texto específicos:  
```

tcp contains "curl"

```

---

## Conclusión

Después de completar este lab, aprendiste a:
- Abrir archivos de captura de paquetes (`.pcap`).  
- Visualizar datos de paquetes de alto nivel.  
- Aplicar filtros por IP, MAC, protocolo o contenido.  
- Inspeccionar capas Ethernet, IP, TCP/UDP y DNS.  

Esto es un hito importante para analizar **tráfico de red y detectar posibles incidentes de seguridad**.