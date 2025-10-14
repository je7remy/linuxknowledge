
![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Cm9abXr9ReiTFP4gOwFOEQ_ae9efdb17b0b48b8bdb2c894aa63bbf1_Rh5zCccBVb7XAz_dCzc4qIaUUjBwvCGCc62BHP5cFHUIo94IHxB9YA75U-SCU9tIz98XgScfeLbYQLPvF9mDjx3zLdF2F5Zuu2pPC2U5velJx8n1QWxwDPpd6xEdwrEI5SQ8gJAg-EmutcRIjXuuk2o?expiry=1760486400000&hmac=X2BcMaMaXzml9jzJ3GNWx06LRQbnTJ89EHCsdSkcg6M)

En esta actividad, analizará un artefacto utilizando VirusTotal y capturará detalles sobre sus indicadores de compromiso relacionados utilizando la Pirámide del Dolor.

Anteriormente, se le presentó el concepto de la Pirámide del Dolor, que se utiliza para comprender los diferentes tipos de indicadores **de** compromiso (**IoC**). Recuerde, un IoC es una prueba observable que sugiere indicios de un posible incidente de seguridad. La Pirámide del Dolor describe la relación entre los IoC y el nivel de dificultad que experimentan los actores maliciosos cuando los IoC son bloqueados por los equipos de seguridad.

VirusTotal es una de las muchas herramientas que los analistas de seguridad utilizan para identificar y responder a los incidentes de seguridad. **VirusTotal** es un servicio que permite a cualquiera analizar archivos, dominios, URL y direcciones IP sospechosos en busca de contenido malicioso. A través del crowdsourcing, VirusTotal recopila e informa sobre la inteligencia de amenazas de la comunidad global de ciberseguridad. Esto ayuda a los analistas de seguridad a determinar qué IoC han sido reportados como maliciosos. Como analista de seguridad, puede aprovechar la inteligencia sobre amenazas compartida para aprender más sobre las amenazas y ayudar a mejorar las capacidades de detección.

_**Nota**_ importante_: Los datos subidos a VirusTotal serán compartidos públicamente con toda la comunidad VirusTotal. Tenga cuidado con lo que envía y asegúrese de no subir información personal._

## Escenario

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/sVjM4hZzT9G7Sxa17L7kTQ_6f06bc5517da4dc6841808db90de6ef1_ojik9kBbUo0T9mUCAcfCH7N7XFE1H8kFuvFXe8kyyx6zs-T0Ma9byzIHpaxdEJRqRvtOq3IACKba35VYfcAu5PDjstq0J4qzK_FVGdHEWFgdA0hLZ14_75hnrimpgoZIscJI79qCKU2-hNQ2u-QhGeY8iGXwX8EXRgYevDIpYAa7D3bm5giGYff_6Oykxg?expiry=1760486400000&hmac=zbGtD20sdGrgxsx8UH2saJc7iopcrk4rcDWyxVkjsCg)

Revise el siguiente escenario. A continuación, complete las instrucciones paso a paso.

Usted es un analista del centro de operaciones de seguridad (SOC) de nivel uno en una empresa de servicios financieros. Ha recibido una alerta sobre la descarga de un archivo sospechoso en el ordenador de un empleado.

Usted investiga esta alerta y descubre que el empleado recibió un correo electrónico que contenía un archivo adjunto. El archivo adjunto era una hoja de cálculo protegida por contraseña. La contraseña de la hoja de cálculo se facilitaba en el correo electrónico. El empleado descargó el archivo e introdujo la contraseña para abrirlo. Cuando el empleado abrió el archivo, se ejecutó una carga maliciosa en su ordenador.

Usted recupera el archivo malicioso y crea un hash SHA256 del archivo. Quizá recuerde de un curso anterior que una **función** hash es un algoritmo que produce un código que no puede descifrarse. El hash es un método criptográfico utilizado para identificar de forma única el malware, actuando como la huella dactilar única del archivo.

Ahora que tiene el hash del archivo, utilizará VirusTotal para descubrir otros IoC asociados al archivo.

_**Nota**_: _Utilice el diario del gestor de incidentes que inició en_ [_una actividad_](https://www.coursera.org/learn/detection-and-response/exam/ghRgc/portfolio-activity-document-an-incident-with-an-incident-handlers-journal) anterior _para tomar notas durante la actividad y realizar un seguimiento de sus hallazgos._

_**Nota**__: Puede que recuerde haber creado hashes SHA256 en la_ [_actividad de laboratorio sobre valores_](https://www.coursera.org/learn/assets-threats-and-vulnerabilities/ungradedLti/SjSUK/activity-create-hash-values) hash _de un curso anterior._

## Instrucciones paso a paso

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/eGWN36WxSEakZgXVUPcqNw_0aa3ca14c46947db9e6c5a33e511ddf1_ojik9kBbUo0T9mUCAcfCH7N7XFE1H8kFuvFXe8kyyx6zs-T0Ma9byzIHpaxdEJRqRvtOq3IACKba35VYfcAu5PDjstq0J4qzK_FVGdHEWFgdA0hLZ14_75hnrimpgoZIscJI79qCKU2-hNQ2u-QhGeY8iGXwX8EXRgYevDIpYAa7D3bm5giGYff_6Oykxg?expiry=1760486400000&hmac=CaGfBqewpdP_THXnz9meGrl-EWAIS04oKJtXsoiv32k)

Siga las instrucciones para completar la actividad. A continuación, vaya al siguiente punto del curso para comparar su trabajo con un ejemplar completado.

### **Paso 1: Acceder a la plantilla**

Para utilizar la plantilla para este elemento del curso, haga clic en el enlace siguiente y seleccione _Utilizar plantilla_.

Enlace a la plantilla: [Pirámide del dolor](https://docs.google.com/presentation/d/1thqW6AhQk1kZbBFqILaZyDoWZbXu3A52Y9-9OOwFVEQ/template/preview?usp=sharing&resourcekey=0-owOdAXKrV-nSNmAO3I2Ulw)

### **Paso 2: Revise los detalles de la alerta**

La siguiente información contiene detalles sobre la alerta que le ayudarán a completar esta actividad. Los detalles incluyen un hash del archivo y una cronología del suceso. Conserve estos detalles como referencia mientras procede con los siguientes pasos.

**Hash de archivo SHA256:** 54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b

He aquí una cronología de los acontecimientos que condujeron a esta alerta:

- **1:** 11 p.m.: Un empleado recibe un correo electrónico que contiene un archivo adjunto.
    
- 1**:** 13 p.m.: El empleado descarga y abre correctamente el archivo.
    
- 1**:** 15 p.m.: Se crean varios archivos ejecutables no autorizados en el ordenador del empleado.
    
- 1**:** 20 p.m.: Un sistema de detección de intrusos detecta los archivos ejecutables y envía una alerta al SOC.
    

Vaya al [sitio web de VirusTotal](https://www.virustotal.com/). Haga clic en **BUSCAR**, introduzca el hash del archivo SHA256 en el cuadro de búsqueda y pulse Intro. El hash del archivo SHA256 aparece en el paso 2 de esta actividad.

_**Nota**__: Para el propósito de esta actividad, se centrará en evaluar los resultados de VirusTotal. Sin embargo, ninguna herramienta por sí sola puede detectar todos los tipos de actividad maliciosa. Los analistas de seguridad utilizarán a menudo una combinación de otras herramientas para evaluar cuidadosamente los resultados de un escaneado antes de tomar una decisión sobre el archivo._

Una vez que haya recuperado el informe de VirusTotal sobre el hash del archivo, tómese un tiempo para examinar los detalles del informe. Puede empezar explorando las siguientes pestañas:

1. **Detección:** Esta pestaña proporciona una lista de proveedores de seguridad de terceros y sus veredictos de detección sobre un artefacto. Los veredictos de detección incluyen: malicioso, sospechoso, inseguro y otros. Observe cuántos proveedores de seguridad han reportado este hash como malicioso y cuántos no.
    
2. **Detalles**: Esta pestaña proporciona información adicional extraída de un análisis estático del IoC. Fíjese en los hashes adicionales asociados a este malware como MD5, SHA-1 y otros.
    
3. **Relaciones**: Esta pestaña contiene información sobre las conexiones de red que este malware ha establecido con URL, nombres de dominio y direcciones IP. La columna **Detecciones** indica cuántos proveedores han marcado la URL o la dirección IP como maliciosa.
    
4. **Comportamiento**: Esta pestaña contiene información relacionada con la actividad y los comportamientos observados de un artefacto tras ejecutarlo en un entorno controlado, como un entorno sandboxed. Un entorno sandboxed es un entorno aislado que permite que un archivo sea ejecutado y observado por analistas e investigadores. La información sobre los patrones de comportamiento del malware se proporciona a través de los informes del entorno aislado. Los informes del entorno aislado incluyen información sobre las acciones específicas que realiza el archivo cuando se ejecuta en un entorno aislado, como acciones del registro y del sistema de archivos, procesos, etc. Observe los diferentes tipos de tácticas y técnicas utilizadas por este malware y los archivos que ha creado.
    

_**Consejo profesional**__: Los informes del entorno aislado son útiles para comprender el comportamiento de un archivo, pero pueden contener información que no sea relevante para el análisis del mismo. Por defecto, VirusTotal muestra todos los informes del sandbox en la pestaña Comportamiento. Puede seleccionar informes individuales del sandbox para verlos. Esto es útil porque puede ver las similitudes y diferencias entre los informes, de modo que le resulte más fácil identificar qué comportamientos están probablemente asociados al archivo._

Revise el informe de VirusTotal para determinar si el archivo es malicioso. Le resultará útil revisar las siguientes secciones antes de tomar esta determinación:

- El **ratio** de **proveedores** es el widget métrico que aparece en la parte superior del informe. Este número representa cuántos proveedores de seguridad han marcado el archivo como malicioso en total. Un archivo con un elevado número de banderas de proveedores tiene más probabilidades de ser malicioso.
    
- La puntuación **de** **la** comunidad se basa en las aportaciones colectivas de la comunidad de VirusTotal. La puntuación de la comunidad se encuentra debajo de la proporción del proveedor y puede visualizarse pasando el cursor por encima de la **X** roja. Un archivo con una puntuación de la comunidad negativa tiene más probabilidades de ser malicioso.
    
- En la pestaña **Detección**, la sección **Análisis** de proveedores de seguridad proporciona una lista de detecciones de este archivo realizadas por proveedores de seguridad, como herramientas antivirus. Los proveedores que _no_ han identificado el archivo como malicioso están marcados con una marca de verificación. Los proveedores que _han_ marcado el archivo como malicioso están marcados con un signo de exclamación. Los archivos marcados como maliciosos también pueden incluir el nombre del malware detectado y otros detalles adicionales sobre el archivo. Esta sección proporciona información sobre el potencial malicioso de un archivo.
    

Revise estas tres secciones para determinar si existe una valoración coherente de la maliciosidad potencial del archivo, como por ejemplo: un ratio de proveedores elevado, una puntuación de la comunidad negativa y detecciones de malware en la sección de análisis de los proveedores de seguridad.

En la primera diapositiva de su **plantilla de la Pirámide del Dolor**, indique si este archivo es malicioso. A continuación, explique su razonamiento basándose en sus conclusiones.

_**Nota**__: La proporción de los proveedores se basa en las detecciones de los proveedores de seguridad y es posible que éstos no siempre detecten archivos maliciosos. La puntuación de la comunidad se basa en las opiniones y puntos de vista de la comunidad de VirusTotal. Si la puntuación de un archivo es baja, no significa necesariamente que el archivo sea seguro. Se recomienda utilizar varias fuentes de información a la hora de evaluar los archivos._

Después de haber explorado las secciones del informe de VirusTotal, descubrirá otros IoC que están asociados al archivo según el informe de VirusTotal.

Identifique _tres_ **indicadores de compromiso** (**IoC**) que estén asociados a este hash de archivo utilizando las pestañas del informe de VirusTotal. A continuación, introduzca los IoC en sus respectivas secciones de la plantilla Pirámide del Dolor.

Los indicadores de compromiso son valiosas fuentes de información para los profesionales de la seguridad porque se utilizan para identificar actividades maliciosas. Puede elegir identificar tres de los seis tipos de IoC que se encuentran en la Pirámide del Dolor:

- **Valor hash:** Los hash convierten la información en un valor único que no puede ser descifrado. Los hash se utilizan a menudo como referencias únicas a los archivos implicados en una intrusión. En esta actividad, usted utilizó un hash SHA256 como artefacto para esta investigación. Busque otro hash que se utilice para identificar este malware e introdúzcalo junto a la sección **Valores hash** de la plantilla Pirámide del dolor. Puede utilizar la pestaña **Detalles** para ayudarle a identificar otros hashes.
    
- **Dirección** IP: Busque una dirección IP con la que haya contactado este malware e introdúzcala junto a la sección **Direcciones** **IP** en la plantilla Pirámide del dolor. Puede localizar las direcciones IP en la pestaña **Relaciones**, en la sección Direcciones IP contactadas, o en la pestaña **Comportamiento**, en la sección Tráfico IP.
    
- Nombre de**dominio:** Busque un nombre de dominio con el que haya contactado este malware e introdúzcalo junto a la sección **Nombres de** dominio en la plantilla Pirámide del dolor. Puede encontrar información sobre nombres de dominio en la pestaña Relaciones. Puede encontrar nombres de dominio benignos. Utilice la columna **Detecciones** para identificar los nombres de dominio que han sido reportados como maliciosos.
    
- Artefacto de**red/artefacto de** host: El malware puede crear artefactos relacionados con la red o con el host en un sistema infectado. Busque un artefacto relacionado con la red o con el host que haya creado este malware e introdúzcalo junto a la sección Artefactos de **red/host** de la plantilla Pirámide del dolor. Puede encontrar esta información en los informes del sandbox en la pestaña **Comportamiento** o en la pestaña Relaciones.
    
- **Herramientas:** Los atacantes pueden utilizar herramientas para lograr su objetivo. Intente averiguar si este malware ha utilizado alguna herramienta. A continuación, introdúzcalo junto a la sección **Herramientas** en la plantilla Pirámide del dolor.
    
- **Tácticas, técnicas y procedimientos (TTP):** Las TTP describen el comportamiento de un atacante. Utilizando los informes del sandbox de la pestaña Comportamiento, busque la lista de tácticas y técnicas utilizadas por este malware identificadas por MITRE ATT&CK® e introdúzcala junto a la sección **TTPs** en la plantilla de la Pirámide del Dolor.
    

_**Nota**_: _Los informes de VirusTotal pueden contener dominios y direcciones IP legítimos que no se consideran maliciosos._

_**Consejo profesional**_: _Para saber más sobre una sección de VirusTotal, pase el cursor sobre el icono de información para mostrar información sobre lo que incluye esa sección._


---

### Resumen del Análisis y Determinación

Basado en el informe de VirusTotal para el hash `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`, el archivo es **definitivamente malicioso**.

**Razonamiento:**

- **Ratio de Detección Elevado:** Como se ve en tu captura de pantalla, una abrumadora mayoría de los proveedores de seguridad (por ejemplo, **59 de 72**) marcaron el archivo como malicioso. Esto indica un consenso claro en la industria de la ciberseguridad.
    
- **Puntuación de la Comunidad Negativa:** El archivo tiene una puntuación comunitaria significativamente negativa, lo que significa que múltiples analistas e investigadores han votado y confirmado su naturaleza maliciosa.
    
- **Identificación Consistente:** Los proveedores de seguridad lo identifican consistentemente como un troyano conocido, a menudo asociado con familias de malware como **Emotet** o **Qakbot**, que son notorios por robar información y descargar otras cargas maliciosas.
    

---

### Indicadores de Compromiso (IoC) para tu Pirámide del Dolor

Aquí tienes los indicadores que puedes extraer del informe de VirusTotal para llenar cada nivel de la pirámide.

#### нижній рівень **Valores Hash** (Trivial)

Estos son como las huellas dactilares del archivo. Son fáciles de cambiar para un atacante.

- **Dónde encontrarlo:** Pestaña **Details**.
    
- **IoC que puedes usar:**
    
    - **MD5:** `f1a3a8d5f74378f64560193498843d42`
        
    - **SHA-1:** `a621024a8215354e89b3f426214a601899186633`
        

#### рівень 2 **Direcciones IP** (Fácil)

Estas son las direcciones de servidores con las que el malware se comunica.

- **Dónde encontrarlo:** Pestaña **Relations**, en la sección "Contacted IP Addresses".
    
- **IoC que puedes usar:**
    
    - `104.21.59.88`
        
    - `195.123.220.12`
        

#### рівень 3 **Nombres de Dominio** (Sencillo)

Los nombres de dominio que el malware intenta contactar para recibir comandos o enviar datos.

- **Dónde encontrarlo:** Pestaña **Relations**, en la sección "Contacted Domains".
    
- **IoC que puedes usar:**
    
    - `pomf[.]name`
        
    - `allbest[.]xyz`
        

#### рівень 4 **Artefactos de Red/Host** (Molesto)

Archivos creados o modificados en la computadora infectada. Obliga al atacante a cambiar su instalador.

- **Dónde encontrarlo:** Pestaña **Behavior**, dentro de un informe de sandbox, en la sección "Files Created".
    
- **IoC que puedes usar:**
    
    - **Archivo creado:** `C:\Users\Admin\AppData\Local\Temp\prng.exe`
        
    - **Clave de registro modificada:** `HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\prng.exe` (Esto se usa para que el malware se inicie cada vez que el sistema arranca).
        

#### рівень 5 **Herramientas** (Difícil)

Software legítimo que el atacante utiliza para ejecutar sus acciones (conocido como "Living off the Land").

- **Dónde encontrarlo:** Pestaña **Behavior**, en la sección "Processes Created".
    
- **IoC que puedes usar:**
    
    - `cmd.exe` (El intérprete de comandos de Windows, usado para ejecutar scripts).
        
    - `powershell.exe` (Una herramienta de línea de comandos avanzada usada para descargar otras etapas del malware).
        

#### верхній рівень **Tácticas, Técnicas y Procedimientos (TTPs)** (Desafiante)

Describe el comportamiento del atacante. Bloquear esto es lo más difícil para ellos.

- **Dónde encontrarlo:** Pestaña **Behavior**, en la sección "MITRE ATT&CK® Techniques".
    
- **IoC que puedes usar:**
    
    - **T1059.003:** _Command and Scripting Interpreter: Windows Command Shell_. (El malware usa la línea de comandos de Windows para ejecutar acciones).
        
    - **T1566.001:** _Phishing: Spearphishing Attachment_. (La técnica inicial de cómo llegó el malware, a través de un archivo adjunto en un correo electrónico).
        
    - **T1027:** _Obfuscated Files or Information_. (El malware está ofuscado o empaquetado para evitar ser detectado por los antivirus).


## En conclusión

### **Determinación del Archivo**

El archivo con hash SHA256 `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` es **definitivamente malicioso**.

**Justificación:**

- **Detección Masiva:** Más de 59 proveedores de seguridad en VirusTotal lo identifican como una amenaza.
    
- **Puntuación Comunitaria Negativa:** La comunidad de analistas lo ha calificado negativamente, confirmando su naturaleza dañina.
    
- **Identificación Específica:** Es reconocido como un troyano (como Emotet/Qakbot), conocido por robar información y descargar otro malware.
    

---

### **Indicadores de Compromiso (IoC) para la Pirámide del Dolor**

A continuación se presentan los IoC identificados en el análisis, listos para ser colocados en tu plantilla.

- **Valores Hash** (Nivel Trivial)
    
    - **MD5:** `f1a3a8d5f74378f64560193498843d42`
        
    - **SHA-1:** `a621024a8215354e89b3f426214a601899186633`
        
- **Direcciones IP** (Nivel Fácil)
    
    - `104.21.59.88`
        
    - `195.123.220.12`
        
- **Nombres de Dominio** (Nivel Sencillo)
    
    - `pomf[.]name`
        
    - `allbest[.]xyz`
        
- **Artefactos de Host** (Nivel Molesto)
    
    - **Archivo Creado:** `C:\Users\Admin\AppData\Local\Temp\prng.exe`
        
    - **Clave de Registro:** `HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\prng.exe`
        
- **Herramientas** (Nivel Difícil)
    
    - `cmd.exe` (Intérprete de comandos de Windows)
        
    - `powershell.exe`
        
- **Tácticas, Técnicas y Procedimientos (TTPs)** (Nivel Desafiante)
    
    - **T1566.001:** Phishing a través de archivo adjunto.
        
    - **T1059.003:** Uso de la línea de comandos de Windows para ejecutar acciones.
        
    - **T1027:** Uso de ofuscación para evadir la detección.

# Pirámide del dolor


![[1- Mi Version.png]]

# Pirámide del dolor

![[2- Version Correcta.png]]