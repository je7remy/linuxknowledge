## Introducción a Redes y Scapy en Python para Ciberseguridad

Bienvenidos a este curso de Python aplicado a la ciberseguridad. Antes de comenzar con temas más avanzados, es necesario tener claros algunos conceptos básicos sobre redes, ya que pronto utilizaremos una librería de Python llamada **Scapy**.

### ¿Qué es Scapy?

Scapy es una poderosa herramienta que permite analizar y manipular paquetes dentro de una red. Con Scapy, es posible realizar acciones como:

- Analizar paquetes de red
    
- Manipular el contenido de los paquetes
    
- Realizar ataques como ARP Spoofing o DNS Spoofing
    
- Redirigir tráfico (por ejemplo, hacer que una víctima que visita "facebook.com" sea redirigida a otra URL o sitio falso en el equipo atacante)
    

### Conceptos Básicos de Redes

#### ¿Cómo viaja la información por la red?

La información no viaja como un solo bloque completo. En su lugar, **se segmenta** en paquetes más pequeños para facilitar una transferencia más eficiente y confiable. Este proceso se conoce como **segmentación de datos**.

Por ejemplo, si enviamos un archivo por la red, este se divide en múltiples partes (paquetes). Esto permite que, si hay un error en la transferencia de un paquete, no se pierda todo el archivo, sino solo ese paquete, lo cual puede ser reenviado.

#### Encapsulación

Cada paquete de datos no solo contiene la parte del archivo o información que queremos enviar, sino también **instrucciones** sobre cómo debe manejarse. Estas instrucciones incluyen datos como:

- Dirección IP de origen y destino
    
- Puerto de origen y destino
    
- Protocolo utilizado
    

Este proceso se llama **encapsulación**, y permite que los datos se muevan correctamente a través de la red mediante diferentes **capas** del modelo de red.

### Capas en la Red

Cuando se transmite un paquete, este pasa por diferentes capas, cada una añadiendo o utilizando información específica para asegurar que el paquete llegue correctamente a su destino:

1. **Capa de Aplicación**: Donde se generan los datos (por ejemplo, un archivo para enviar).
    
2. **Capa de Transporte**: Se asignan puertos de origen y destino (por ejemplo, protocolo TCP).
    
3. **Capa de Red**: Se asignan direcciones IP de origen y destino.
    
4. **Capa de Enlace**: Se prepara el paquete para ser enviado físicamente (MAC address, por ejemplo).
    
5. **Capa Física**: El paquete se transmite a través del medio físico (cable, ondas, etc.).
    

### Importancia para la Ciberseguridad

Conocer cómo viajan los paquetes y cómo se encapsulan es esencial para tareas como:

- Inspeccionar tráfico de red
    
- Identificar vulnerabilidades en protocolos no cifrados (como HTTP o FTP)
    
- Realizar pruebas de penetración o auditorías de seguridad
    

En resumen, la comprensión de estos conceptos es fundamental antes de comenzar a trabajar con Scapy y herramientas similares en el ámbito de la ciberseguridad. La próxima clase profundizaremos directamente en la manipulación de paquetes usando Scapy.

---
