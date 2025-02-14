
**_El reconocimiento activo_** es un método de recopilación de información en el que las herramientas utilizadas envían sondas a la red o sistemas objetivo con el fin de obtener respuestas que luego se utilizan para determinar la posición de la red o sistema. Estas sondas pueden utilizar varios protocolos y múltiples niveles de agresividad, normalmente en función de lo que se está analizando y cuándo. Por ejemplo, es posible que esté escaneando un dispositivo, como una impresora, que no tiene una pila TCP/IP muy robusta o hardware de red. Al enviar sondeos activos, es posible que se bloquee un dispositivo de este tipo. La mayoría de los dispositivos modernos no tienen este problema; Sin embargo, es posible, por lo que al realizar un escaneo activo, debe ser consciente de esto y ajustar la configuración de su escáner en consecuencia.

**_El reconocimiento pasivo_** es un método de recopilación de información en el que las herramientas no interactúan directamente con el dispositivo o la red objetivo. Existen múltiples métodos de reconocimiento pasivo. Algunos implican el uso de bases de datos de terceros para recopilar información. Otros también utilizan las herramientas de tal manera que no serán detectados por el objetivo. Estas herramientas, en particular, funcionan simplemente escuchando el tráfico en la red y utilizando la inteligencia para deducir información sobre la comunicación del dispositivo en la red. Este enfoque es mucho menos invasivo en una red, y es muy poco probable que este tipo de reconocimiento bloquee un sistema como una impresora. Debido a que no produce ningún tráfico, también es poco probable que sea detectado y no genera ninguna bandera en la red que está inspeccionando. Otro escenario en el que un escáner pasivo sería útil sería para un probador de penetración que necesita realizar análisis en una red de producción que no se puede interrumpir. La técnica de reconocimiento pasivo que utilice depende del tipo de información que desee obtener. Uno de los aspectos más importantes de aprender sobre las pruebas de penetración es desarrollar una buena metodología que te ayude a seleccionar las herramientas y tecnologías adecuadas para usar durante el compromiso.

Entre las herramientas y métodos comunes de reconocimiento activo se incluyen los siguientes:

- Enumeración de hosts
- Enumeración de red
- Enumeración de usuarios
- Enumeración de grupos
- Enumeración de recursos compartidos de red
- Enumeración de páginas web
- Enumeración de aplicaciones
- Enumeración de servicios
- Elaboración de paquetes

Entre las herramientas y métodos comunes de reconocimiento pasivo se incluyen los siguientes:

- Enumeración de dominios
- Inspección de paquetes
- Inteligencia de código abierto (OSINT)
- Reconocimiento
- Escuchando


---

# **Reconocimiento en Ciberseguridad: Pasivo y Activo**

#Ciberseguridad #HackingÉtico #Reconocimiento #OSINT #Pentesting

**Reconocimiento en Ciberseguridad**

El reconocimiento es una de las fases fundamentales dentro de la ciberseguridad y el hacking ético. Se trata de la recopilación de información sobre un objetivo antes de lanzar cualquier ataque o auditoría. Esta fase se divide en dos categorías principales: reconocimiento pasivo y reconocimiento activo.

### 1. Reconocimiento Pasivo

El reconocimiento pasivo implica la recopilación de información sin interactuar directamente con el sistema objetivo. Esto significa que no se generan alertas ni registros en los sistemas de seguridad del objetivo. Algunas técnicas comunes incluyen:

- **Búsqueda en Motores de Búsqueda**: Uso de Google Dorking para encontrar información sensible en páginas web.
- **Consulta de WHOIS**: Para obtener detalles sobre la propiedad de dominios.
- **Análisis de Redes Sociales**: Revisión de perfiles en LinkedIn, Facebook, Twitter, entre otros, para obtener información sobre empleados, infraestructura y políticas de la empresa.
- **Investigación en Bases de Datos Públicas**: Acceso a registros de empresas, filtraciones de datos y foros especializados.

### 2. Reconocimiento Activo

El reconocimiento activo implica la interacción directa con el sistema objetivo para obtener información. A diferencia del reconocimiento pasivo, este método puede generar registros en los sistemas de detección de intrusos. Algunas técnicas incluyen:

- **Escaneo de Puertos**: Uso de herramientas como Nmap para identificar servicios y puertos abiertos.
- **Fingerprinting de Sistemas y Servicios**: Detección del sistema operativo y versiones de software mediante herramientas como Netcat o WhatWeb.
- **Enumeración de DNS**: Obtención de subdominios y registros DNS mediante herramientas como dnsenum y fierce.
- **Fuerza Bruta de Directorios y Archivos**: Uso de herramientas como Gobuster o Dirb para descubrir rutas ocultas en servidores web.

### Herramientas Comunes

Existen diversas herramientas utilizadas en la fase de reconocimiento. Algunas de las más populares incluyen:

- **Shodan**: Motor de búsqueda de dispositivos conectados a internet.
- **Maltego**: Plataforma de inteligencia para análisis de relaciones y conexiones de datos.
- **theHarvester**: Herramienta de recolección de correos electrónicos, nombres de dominio y más.
- **Recon-ng**: Framework para la automatización del reconocimiento en ciberseguridad.
- **Metasploit**: Aunque es una herramienta de explotación, también incluye módulos para reconocimiento.

### Ejemplo Práctico

Supongamos que queremos realizar un reconocimiento sobre un dominio objetivo, `example.com`.

1. **Consulta WHOIS**:
    
    ```bash
    whois example.com
    ```
    
2. **Enumeración de subdominios con Sublist3r**:
    
    ```bash
    sublist3r -d example.com
    ```
    
3. **Escaneo de puertos con Nmap**:
    
    ```bash
    nmap -sS -Pn -p- example.com
    ```
    
4. **Recolección de correos con theHarvester**:
    
    ```bash
    theHarvester -d example.com -b google
    ```
    

Este proceso ayuda a obtener información crucial sobre el objetivo, facilitando la identificación de posibles vectores de ataque.

### Conclusión

El reconocimiento es una fase esencial en ciberseguridad y hacking ético. Un buen uso de estas técnicas permite fortalecer la seguridad de los sistemas y prevenir ataques. Sin embargo, es importante recordar que cualquier actividad debe realizarse con autorización y dentro del marco legal correspondiente.

---
