
### **Respuestas del Cuestionario**

1. Pregunta 1

Rellene el espacio en blanco: _____ describe la cantidad de Datos que se mueven a través de una red.

- **Respuesta correcta:** **Tráfico de red**
    
- **Explicación:** El término "tráfico de red" se refiere específicamente al volumen o la cantidad de datos que fluyen por una red en un momento dado.
    

---

2. Pregunta 2

¿Cuál de los siguientes comportamientos puede sugerir un ataque de robo de datos en curso? Seleccione dos respuestas.

- **Respuestas correctas:**
    
    - **Modificaciones inesperadas de archivos que contienen Datos sensibles**
        
    - **Tráfico de red saliente hacia un servicio de alojamiento de archivos no autorizado**
        
- **Explicación:** El robo de datos a menudo implica acceder a archivos sensibles (modificándolos) y luego enviarlos fuera de la red (tráfico saliente a destinos no autorizados). Los otros dos son eventos de red normales.
    

---

3. Pregunta 3

¿Qué información contienen los encabezados de los paquetes? Seleccione tres respuestas.

- **Respuestas correctas:**
    
    - **Puertos**
        
    - **Direcciones IP**
        
    - **Protocolos**
        
- **Explicación:** El encabezado de un paquete contiene la información de control necesaria para enrutarlo, como las direcciones IP de origen/destino, los puertos (en la capa de transporte) y el protocolo que se está utilizando (ej. TCP, UDP). Los datos de la carga útil (payload) son el contenido del paquete, no parte del encabezado.
    

---

4. Pregunta 4

Rellene el espacio en blanco: Los analizadores de protocolos de red pueden guardar las comunicaciones de red en archivos conocidos como _____.

- **Respuesta correcta:** **captura de paquetes**
    
- **Explicación:** Un archivo de captura de paquetes (comúnmente con extensión `.pcap`) es el formato estándar que usan herramientas como Wireshark y tcpdump para guardar el tráfico de red capturado.
    

---

5. Pregunta 5

Rellene el espacio en blanco: tcpdump es un analizador de protocolos de red que utiliza una(n) interfaz _____.

- **Respuesta correcta:** **línea de comandos**
    
- **Explicación:** tcpdump es una herramienta basada en texto que se opera exclusivamente a través de una interfaz de línea de comandos (CLI), a diferencia de Wireshark que tiene una interfaz de usuario gráfica (GUI).
    

---

6. Pregunta 6

¿Qué capa del Modelo TCP/IP es responsable de aceptar y entregar paquetes en una red?

- **Respuesta correcta:** **Internet**
    
- **Explicación:** La capa de Internet (o capa de red) es responsable del direccionamiento, enrutamiento y empaquetado de los datos en paquetes IP para entregarlos a través de diferentes redes.
    

---

7. Pregunta 7

¿Qué campos del encabezado IPv4 implican fragmentación? Seleccione tres respuestas.

- **Respuestas correctas:**
    
    - **Desplazamiento de fragmentos**
        
    - **Identificación**
        
    - **Banderas (Flags)**
        
- **Explicación:** Cuando un paquete se fragmenta, el campo de **Identificación** es el mismo para todos los fragmentos. Las **Banderas** indican si hay más fragmentos por venir, y el **Desplazamiento de fragmentos** indica la posición de ese fragmento en el paquete original.
    

---

8. Pregunta 8

¿Qué Campo IPv4 utiliza un valor para representar un estándar, como TCP?

- **Respuesta correcta:** **Protocolo**
    
- **Explicación:** El campo "Protocolo" en el encabezado IPv4 contiene un número que identifica el protocolo de la capa siguiente (por ejemplo, el número 6 para TCP o el 17 para UDP).
    

---

9. Pregunta 9

¿Qué opción de tcpdump se utiliza para especificar la captura de 5 paquetes?

- **Respuesta correcta:** **-c 5**
    
- **Explicación:** La opción `-c` (de "count" o contar) en tcpdump se utiliza para especificar el número de paquetes a capturar antes de detenerse.
    

---

10. Pregunta 10

Examine la siguiente salida de tcpdump:

22:00:19.538395 IP (tos 0x10, ttl 64, id 33842, offset 0, flags [P], proto TCP (6), length 196) 198.168.105.1.41012 > 198.111.123.1.61012: Flags [P.], cksum 0x50af (correct), seq 169, ack 187, win 501, length 42

¿Qué protocolos se están utilizando? Seleccione dos respuestas.

- **Respuestas correctas:**
    
    - **IP**
        
    - **TCP**
        
- **Explicación:** La salida muestra claramente "IP" al principio de la descripción del paquete y "proto TCP (6)" que indica explícitamente que el protocolo de la capa de transporte es TCP.