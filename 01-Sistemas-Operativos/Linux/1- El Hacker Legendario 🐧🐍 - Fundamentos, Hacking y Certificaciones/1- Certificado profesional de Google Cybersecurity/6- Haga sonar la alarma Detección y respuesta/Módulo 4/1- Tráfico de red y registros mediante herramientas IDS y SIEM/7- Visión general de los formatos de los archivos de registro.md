
Ya ha aprendido cómo los registros registran los eventos que se producen en una red, o en un sistema. En Seguridad, los registros proporcionan detalles clave sobre las actividades ocurridas en una organización, como quién inició sesión en una aplicación en un momento determinado. Como analista de Seguridad, utilizará el **análisis** de registros, que es el proceso de examinar los registros para identificar los eventos de Interés. Es importante saber leer e interpretar los diferentes formatos de registro para poder descubrir los detalles clave que rodean a un evento e identificar actividades inusuales o maliciosas. En esta lectura, revisará los siguientes formatos de registro:

- JSON
    
- Syslog
    
- XML
    
- CSV
    
- CEF
    

## Notación de objetos JavaScript (JSON)

JavaScript Object Notation (JSON) es un formato de archivo que se utiliza para almacenar y transmitir Datos. JSON es conocido por ser ligero y fácil de leer y escribir. Se utiliza para transmitir Datos en tecnologías web y también es de uso común en entornos de Nube. La sintaxis de JSON se deriva de la sintaxis de JavaScript. Si está familiarizado con JavaScript, es posible que reconozca que JSON contiene componentes de JavaScript, entre los que se incluyen:

- Parejas clave-valor
    
- Comas
    
- Comillas dobles
    
- Paréntesis rizados
    
- Corchetes
    

### **Parejas clave-valor**

Un **par** **clave-valor** es un conjunto de datos que representa dos elementos vinculados: una clave y su correspondiente valor. Una pareja clave-valor está formada por una clave seguida de dos puntos y, a continuación, un valor. Un ejemplo de una pareja clave-valor es "Alert": "Malware".

**Nota**: Para facilitar la lectura, se recomienda que los pares clave-valor contengan un espacio antes o después de los dos puntos que separan la clave y el valor.

### **Comas**

Las comas se utilizan para separar datos. Por ejemplo: "Alert": "Malware", "Alert code": 1090, "severity": 10.

### **Comillas dobles**

Las comillas dobles se utilizan para encerrar datos de _texto_, que también se conocen como cadena, por ejemplo: "Alert": "Malware". Los Datos que contienen números _no van_ entre comillas, como por ejemplo: "Alert code": 1090.

### **Paréntesis rizados**

Las llaves encierran un **objeto**, que es un tipo de datos que almacena datos en una lista separada por comas de pares clave-valor. Los objetos se utilizan a menudo para describir múltiples propiedades de una clave determinada. Las entradas de registro JSON empiezan y terminan con una llave. En este ejemplo,User es el objeto que contiene múltiples propiedades:

"User": {  "id": "1234",  "name": "user", "role": "engineer" }

### **Corchetes**

Los corchetes se utilizan para encerrar un **Array**, que es un tipo de datos que almacena datos en una lista ordenada separada por comas. Los Arrays son útiles cuando desea almacenar datos como una colección ordenada, por ejemplo:["Administrators", "Users", "Engineering"].

## Syslog

Syslog es un estándar para el registro y la transmisión de datos. Puede utilizarse para referirse a cualquiera de sus tres capacidades diferentes:

1. **Protocolo**: El protocolo syslog se utiliza para transportar registros a un servidor de registros centralizado para su gestión. Utiliza el puerto 514 para los registros en texto plano y el puerto 6514 para los registros encriptados.
    
2. **Servicio**: El servicio syslog actúa como un servicio de reenvío de registros que consolida los registros de múltiples fuentes en una única ubicación. El servicio funciona mediante la recepción y posterior reenvío de cualquier entrada de registro syslog a un servidor remoto.
    
3. Formato de**registro**: El formato de registro syslog es uno de los formatos de registro más utilizados en los que se centrará. Es el formato de registro nativo utilizado en los sistemas Unix®. Consta de tres componentes: un encabezado, datos estructurados y un mensaje.
    

## Ejemplo de registro syslog

Este es un ejemplo de una entrada syslog que contiene los tres componentes: una cabecera, seguida de datos estructurados y un mensaje:

<236>1 2022-03-21T01:11:11.003Z virtual.machine.com evntslog - ID01 [user@32473 iut="1" eventSource="Application" eventID="9999"] This is a log entry!

### **Encabezado**

El encabezado contiene detalles como la marca de tiempo; el nombre de host, que es el nombre de la máquina que envía el registro; el nombre de la aplicación; y el ID del mensaje.

- **Marca** de tiempo: La marca de tiempo en este ejemplo es 2022-03-21T01:11:11.003Z, donde 2022-03-21 es la fecha en formato AAAA-MM-DD. T se utiliza para separar la fecha y la hora. 01:11:11.003 es el formato de 24 horas de la hora e incluye el número de milisegundos 003. Z indica la zona horaria, que es el Tiempo Universal Coordinado (UTC).
    
- **Nombre de host**: virtual.machine.com
    
- **Aplicación**: evntslog
    
- **ID** del**mensaje**: ID01
    

### **Datos estructurados**

La parte de datos estructurados de la entrada del registro contiene información adicional sobre el registro. Esta información va entre corchetes y está estructurada en pares clave-valor. Aquí hay tres claves con sus valores correspondientes: [user@32473 iut="1" eventSource="Application" eventID="9999"].

### **Mensaje**

El mensaje contiene un mensaje de registro detallado sobre el evento. Aquí, el mensaje es This is a log entry!.

### **Prioridad (PRI)**

El Campo de prioridad (PRI) indica la urgencia del evento registrado y está contenido entre corchetes angulares. En este ejemplo, el valor de prioridad es <236>. Generalmente, cuanto más bajo es el nivel de prioridad, más urgente es el evento.

**Nota**: Los encabezados Syslog pueden combinarse con formatos JSON y XML. También existen formatos de registro personalizados.

## XML (eXtensible Markup Language)

XML (eXtensible Markup Language) es un lenguaje y un formato utilizado para almacenar y transmitir Datos. XML es un formato de archivos nativo utilizado en los sistemas Windows. La sintaxis XML utiliza lo siguiente:

- Etiquetas
    
- Elementos
    
- Atributos
    

### **Etiquetas**

XML utiliza etiquetas para almacenar e identificar datos. Las etiquetas son vinculaciones que deben contener una etiqueta de inicio y una etiqueta de fin. La etiqueta de inicio encierra los datos entre paréntesis angulares, por ejemplo <tag>, mientras que el final de una etiqueta encierra los datos entre paréntesis angulares y una barra oblicua, así: </tag>.

### **Elementos**

Los elementos XML incluyen _tanto_ los datos contenidos dentro de una etiqueta como la propia etiqueta. Todas las entradas XML deben contener al menos un elemento raíz. Los elementos raíz contienen otros elementos que se sitúan debajo de ellos, conocidos como elementos hijo.

He aquí un ejemplo:

<Event> <EventID>4688</EventID> <Version>5</Version> </Event>

En este ejemplo, <Event> es el elemento raíz y contiene dos elementos hijos <EventID> y <Version>. Cada elemento hijo contiene datos.

### **Atributos**

Los elementos XML también pueden contener atributos. Los atributos se utilizan para proporcionar información adicional sobre los elementos. Los atributos se incluyen como segunda parte de la propia etiqueta y siempre deben entrecomillarse utilizando comillas simples o dobles.

Por ejemplo:

<EventData> <Data Name='SubjectUserSid'>S-2-3-11-160321</Data> <Data Name='SubjectUserName'>JSMITH</Data> <Data Name='SubjectDomainName'>ADCOMP</Data> <Data Name='SubjectLogonId'>0x1cf1c12</Data> <Data Name='NewProcessId'>0x1404</Data> </EventData>

En la primera línea de este ejemplo, la etiqueta es<Data> y utiliza el atributo Name='SubjectUserSid' para describir los datos incluidos en la etiqueta S-2-3-11-160321.

## CSV (Valores separados por comas)

CSV (Comma Separated Value) utiliza comas para separar los valores de los Datos. En los registros CSV, la posición de los Datos corresponde a su nombre de Campo, pero los propios nombres de Campo pueden no estar incluidos en el registro. Es fundamental comprender qué campos incluye en el registro el dispositivo de origen (como un IPS, firewall, escáner, etc.).

He aquí un ejemplo:

2009-11-24T21:27:09.534255,ALERT,192.168.2.7, 1041,x.x.250.50,80,TCP,ALLOWED,1:2001999:9,"ET MALWARE BTGrab.com Spyware Downloading Ads",1

## CEF (Formato de evento común)

**Formato de evento** común (CEF) es un formato de registro que utiliza pares clave-valor para estructurar los datos e identificar los campos y sus valores correspondientes. La sintaxis CEF se define por contener los siguientes campos:

CEF:Version|Device Vendor|Device Product|Device Version|Signature ID|Name|Severity|Extension

Todos los campos están separados por un carácter de tubería |. Sin embargo, todo lo que aparezca en la parte Extension de la entrada del registro CEF debe escribirse en un formato clave-valor. Syslog es un Método común utilizado para transportar registros como CEF. Cuando se utiliza Syslog, se anteponen al mensaje CEF una marca de tiempo y un nombre de host. He aquí un ejemplo de entrada de registro CEF que detalla la actividad maliciosa relacionada con la infección de un gusano:

Sep 29 08:26:10 host CEF:1|Security|threatmanager|1.0|100|worm successfully stopped|10|src=10.0.0.2 dst=2.1.2.2 spt=1232

He aquí un desglose de los campos:

- Syslog**Timestamp**: Sep 29 08:26:10
    
- **Nombre de host** Syslog: host
    
- **Versión** CEF:1
    
- **Proveedor** del dispositivo: Security
    
- **Producto** del dispositivo: threatmanager
    
- **Versión** del dispositivo: 1.0
    
- ID de**Firma**: 100
    
- **Nombre**: worm successfully stopped
    
- **Gravedad**: 10
    
- **Extensión**: Este Campo contiene Datos escritos como pares clave-valor. Hay dos direcciones IP, src=10.0.0.2 y dst=2.1.2.2, y un número de puerto de origen spt=1232. Las extensiones no son obligatorias y su adición es opcional.
    

Esta entrada de registro contiene detalles sobre una aplicación Security llamada threatmanager que successfully stopped a worm de propagando desde la red interna en 10.0.0.2 a la red externa 2.1.2.2 a través del puerto 1232. Se informa de un nivel de gravedad alto de 10.

**Nota**: Las extensiones y el prefijo syslog son opcionales para añadir a un registro CEF.

## Puntos clave

No existe un formato estándar utilizado en los registros y existen muchos formatos de registro diferentes. Como analista de Seguridad, analizará registros que se originan en diferentes fuentes. Saber interpretar los distintos formatos de registro le ayudará a determinar la información clave que puede utilizar para apoyar sus investigaciones.

## Recursos para obtener más Información

- Para saber más sobre el protocolo syslog, incluidos los niveles de prioridad, consulte [El protocolo syslog](https://www.rfc-editor.org/rfc/rfc5424).
    
- Si desea explorar la generación de formatos de registro, consulte esta [herramienta generadora de datos de prueba](https://generatedata.com/) de código abierto.
    
- Para saber más sobre los formatos de marcas de tiempo, consulte [Fecha y hora en Internet: Timestamps](https://www.rfc-editor.org/rfc/rfc3339).