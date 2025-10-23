
Hasta ahora, has aprendido cómo puedes utilizar las herramientas de **administración de información y eventos de seguridad (SIEM** ) para buscar eventos de seguridad como intentos fallidos de inicio de sesión. Recuerde que SIEM es una aplicación que recopila y analiza datos de registro para supervisar actividades críticas en una organización. En esta lectura, examinarás cómo las herramientas SIEM como Splunk y Google SecOps (Chronicle) utilizan diferentes métodos de búsqueda para encontrar, filtrar y transformar los resultados de la búsqueda.

No todas las organizaciones utilizan la misma herramienta SIEM para recopilar y centralizar sus datos de seguridad. Como analista de seguridad, tendrás que estar preparado para aprender a utilizar diferentes herramientas SIEM. Es importante comprender los diferentes tipos de búsquedas que puede realizar con las herramientas SIEM para poder encontrar datos de eventos relevantes que respalden sus investigaciones de seguridad.

## Búsquedas en Splunk

Como has aprendido, Splunk tiene su propio lenguaje de consulta llamado **Lenguaje de Procesamiento de Búsqueda (SPL)**. SPL se utiliza para buscar y recuperar eventos de los índices utilizando la aplicación Splunk Search & Reporting. Una búsqueda SPL puede contener muchos comandos y argumentos diferentes. Por ejemplo, puede utilizar comandos para transformar los resultados de la búsqueda en un formato de gráfico o filtrar los resultados para obtener información específica.

![Página de búsqueda de Splunk Cloud.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/zmjvpMvASVuLzBl6p1-KJg_48cf882e1ea14f6ca2f3ceee91e1f2e1_cIW5xo7oKZMktF78z_u5eTeEJANj9wPgAG39QVCd8PDuvdrztqt2N1fJMbJOFms1QoIgAk0YNgHWjR1LQMLg__bhWqMMWmWke6kQmoWLpyxM5eVwNDyW7_2KttYjVSz2fYPCX4arj1TUHKrSfANwCU8?expiry=1761350400000&hmac=Ojurd4urXPxSTlLq8EI_GC3AsowXYYqe2KQq_mQs2UU)

A continuación se muestra un ejemplo de una búsqueda SPL básica que está consultando un índice para un evento fallido:

index=main fail 

- index=main: Este es el comienzo del comando de búsqueda que le dice a Splunk que recupere eventos de un index llamado main. Un índice almacena datos de eventos que han sido recolectados y procesados por Splunk.
    
- fail: Este es el término de búsqueda. Esto le dice a Splunk que devuelva cualquier evento que contenga el término fail.
    

Saber cómo utilizar eficazmente SPL tiene muchos beneficios. Ayuda a acortar el tiempo que se tarda en devolver los resultados de búsqueda. También le ayuda a obtener los resultados exactos que necesita de varias fuentes de datos. SPL soporta muchos tipos diferentes de búsquedas que están más allá del alcance de esta lectura. Si desea obtener más información acerca de SPL, explore [la Referencia de Búsqueda de Splunk](https://docs.splunk.com/Documentation/Splunk/9.0.2/SearchReference/UnderstandingSPLsyntax).

### **Tuberías**

Anteriormente, es posible que haya aprendido acerca de cómo tuberías se utiliza en el shell Linux Bash. Como recordatorio, la tubería envía la salida de un comando como entrada a otro comando.

SPL también utiliza el carácter de tubería | para separar los comandos individuales en la búsqueda. También se utiliza para encadenar comandos de modo que la salida de un comando se combine en el siguiente comando. Esto es útil porque puedes refinar los datos de varias maneras para obtener los resultados que necesitas usando un solo comando.

A continuación se muestra un ejemplo de dos comandos que se encadenan:

index=main fail| chart count by host

- index=main fail: Este es el comienzo del comando de búsqueda que le dice a Splunk que recupere eventos de un index llamado main para eventos que contengan el término de búsqueda fail.
    
- |: El carácter pipe separa y encadena los dos comandos index=main y chart count by host. Esto significa que la salida del primer comando index=main se utiliza como entrada del segundo comandochart count by host.
    
- chart count by host: Este comando indica a Splunk que transforme los resultados de la búsqueda creando un chart según el count o el número de eventos. El argumento by host indica a Splunk que enumere los eventos por host, que son los nombres de los dispositivos de los que proceden los eventos. Este comando puede ser útil en la identificación de hosts con excesivo recuento de fallos en un entorno.
    

### **Comodín**

Un **comodín** es un carácter especial que puede ser sustituido por cualquier otro carácter. Un comodín suele simbolizarse con un asterisco *. Los comodines coinciden con caracteres en valores de cadena. En Splunk, el comodín que se utiliza depende del comando con el que se está utilizando el comodín. Los comodines son útiles porque pueden ayudar a encontrar eventos que contienen datos que son similares pero no totalmente idénticos. A continuación se muestra un ejemplo de uso de un comodín para ampliar los resultados de búsqueda para un término de búsqueda:

index=main fail*

- index=main: Este comando recupera eventos de un index llamado main.
    
- fail*: El comodín después de fail representa cualquier carácter. Esto indica a Splunk que busque todas las terminaciones posibles que contengan el término fail. Esto expande los resultados de la búsqueda para devolver cualquier evento que contenga el término fail como "failed" o "failure".
    

**Consejo profesional**: Las comillas dobles se utilizan para especificar una búsqueda de una frase o cadena exacta. Por ejemplo, si desea buscar sólo los eventos que contengan la frase exacta login failure, puede encerrar la frase entre comillas dobles "login failure". Esta búsqueda sólo coincidirá con los eventos que contengan la frase exacta login failure y no con otros eventos que contengan las palabras failure o login por separado.

## Búsquedas en Google Security Operations (Chronicle)

En Google SecOps (Chronicle), puede buscar eventos mediante el campo Buscar. También puede utilizar el filtrado de procedimiento para aplicar filtros a una búsqueda y refinar aún más los resultados de la búsqueda. Por ejemplo, puedes utilizar el filtrado de procedimiento para incluir o excluir resultados de búsqueda que contengan información específica relacionada con un tipo de evento o una fuente de registro. Existen dos tipos de búsquedas que puedes realizar para encontrar eventos en Google SecOps (Chronicle): una búsqueda en el Modelo unificado de datos (UDM) o una búsqueda en el registro sin procesar.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/_f2c6abf5fc9e4246ba4225efa90979f1_GoogleSecOpsLogo.png?expiry=1761350400000&hmac=CvT3IB9iuAipk_vJ7UAOdD4eNL-AHtt54IRoXxXnGc4)

### **Búsqueda en el Modelo unificado de datos (UDM)**

La búsqueda UDM es el tipo de búsqueda predeterminado que se utiliza en Google SecOps (Chronicle). Puedes realizar una búsqueda UDM escribiendo tu búsqueda, haciendo clic en "Buscar" y seleccionando "Búsqueda UDM" Mediante una búsqueda UDM, Google SecOps (Chronicle) busca datos de seguridad que se han ingestado, analizado y normalizado. Una búsqueda UDM recupera los resultados de la búsqueda más rápidamente que una búsqueda de registro sin procesar porque busca a través de datos indexados y estructurados que se han normalizado en UDM.

Una búsqueda UDM recupera eventos formateados en UDM y estos eventos contienen campos UDM. Existen muchos tipos diferentes de campos UDM que se pueden utilizar para buscar información específica de un evento. Tratar todos estos campos UDM va más allá del alcance de esta lectura, pero puede obtener más información sobre los campos UDM explorando [la lista de campos UDM de Google Security Operations](https://cloud.google.com/chronicle/docs/reference/udm-field-list). Sepa que todos los eventos UDM contienen un conjunto de campos comunes, entre los que se incluyen:

- **Entidades**: Las entidades también se conocen como sustantivos. Todos los eventos UDM deben contener al menos una entidad. Este campo proporciona contexto adicional sobre un dispositivo, usuario o proceso implicado en un evento. Por ejemplo, un evento UDM que contiene información de entidad incluye los detalles del origen de un evento, como el nombre de host, el nombre de usuario y la dirección IP del evento.
    
- **Metadatos del evento**: Este campo proporciona una descripción básica de un evento, incluyendo de qué tipo de evento se trata, marcas de tiempo, etc.
    
- **Metadatos de red**: Este campo proporciona información sobre los eventos relacionados con la red y detalles del protocolo.
    
- **Resultados** de seguridad: Este campo proporciona los resultados de los sucesos relacionados con la seguridad. Un ejemplo de resultado de seguridad puede ser que un software antivirus detecte y ponga en cuarentena un archivo malicioso informando de "virus detectado y puesto en cuarentena".
    

A continuación se muestra un ejemplo de una búsqueda UDM sencilla que utiliza el campo de metadatos de eventos para localizar eventos relacionados con inicios de sesión de usuario:

metadata.event_type = “USER_LOGIN” 

- metadata.event_type = “USER_LOGIN”: Este campo UDM metadata.event_type contiene información sobre el tipo de evento. Esto incluye información como la marca de tiempo, la conexión de red, la autenticación del usuario y más. Aquí, el tipo de evento especifica USER_LOGIN, que busca eventos relacionados con la autenticación.
    

Utilizando sólo los campos de metadatos, puedes empezar a buscar eventos rápidamente. A medida que continúe practicando la búsqueda en Google SecOps (Chronicle) mediante la búsqueda UDM, encontrará más campos. Pruebe a utilizar estos campos para realizar búsquedas específicas con el fin de localizar distintos eventos.

### **Búsqueda de registros sin procesar**

Si no puede encontrar la información que busca a través de los datos normalizados, puede utilizar una búsqueda de registro sin procesar para buscar en los registros sin procesar. Puede realizar una búsqueda de registros sin procesar escribiendo su búsqueda, haciendo clic en "Buscar" y seleccionando "Búsqueda de registros sin procesar" Como se trata de una búsqueda en registros sin procesar, tarda más que una búsqueda estructurada. En el campo Buscar, puedes realizar una búsqueda de registros sin procesar especificando información como nombres de usuario, nombres de archivo, hashes, etc. Google SecOps (Chronicle) recuperará los eventos asociados a la búsqueda.

**Consejo profesional**: la búsqueda de registros sin procesar admite el uso de expresiones regulares, que pueden ayudarte a limitar la búsqueda para que coincida con patrones específicos.

## Puntos clave

Las herramientas SIEM como Splunk y Google SecOps (Chronicle) tienen sus propios métodos para buscar y recuperar datos de eventos. Como analista de seguridad, es importante saber cómo aprovechar estas herramientas para encontrar rápida y eficazmente la información que necesita. Esto le permitirá explorar los datos de forma que le ayuden a detectar amenazas, así como a responder rápidamente a los incidentes de seguridad.

## Recursos para obtener más información

Aquí tienes algunos recursos por si quieres saber más sobre la búsqueda de eventos con Splunk y Google SecOps (Chronicle):

- [Manual de Búsqueda de Splunk](https://docs.splunk.com/Documentation/Splunk/9.0.1/Search/GetstartedwithSearch) sobre cómo utilizar el Lenguaje de Procesamiento de Búsqueda de Splunk (SPL)
    
- [Guía rápida de Google Security Operations](https://cloud.google.com/chronicle/docs/review-security-alert) sobre los distintos tipos de búsqueda