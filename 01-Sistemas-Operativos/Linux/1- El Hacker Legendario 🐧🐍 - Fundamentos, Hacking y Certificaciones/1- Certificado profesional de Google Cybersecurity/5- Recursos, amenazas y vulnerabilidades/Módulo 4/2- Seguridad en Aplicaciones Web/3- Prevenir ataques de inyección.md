
Anteriormente, aprendió que el **Lenguaje de Consulta Estructurado** (SQL) es un lenguaje de programación utilizado para crear, interactuar y solicitar información a una base de datos. SQL es uno de los lenguajes de programación más utilizados para interactuar con bases de datos porque está ampliamente soportado por una amplia gama de productos de bases de datos.

Como recordará, **la inyección de** SQL maliciosa es un tipo de ataque que ejecuta consultas inesperadas en una base de datos. Agentes de amenaza realizan inyecciones de SQL para modificar, borrar o robar información de las bases de datos. Una inyección de SQL es un vector de ataque común que se utiliza para obtener acceso no autorizado a las aplicaciones web. Debido a la popularidad de este lenguaje entre los desarrolladores, las inyecciones de SQL aparecen regularmente en la Lista OWASP® Top 10 porque los desarrolladores tienden a centrarse en hacer que sus aplicaciones funcionen correctamente en lugar de proteger sus productos de las inyecciones.

En esta lectura, aprenderá sobre las consultas SQL y cómo se utilizan para solicitar información a una base de datos. También conocerá las tres clases de ataques de inyección de SQL que se utilizan para manipular consultas vulnerables. También aprenderá formas de identificar cuándo los sitios web son vulnerables y maneras de solucionar esas deficiencias.

## Consultas SQL

Cada bit de información al que se accede en línea se almacena en una base de datos. Una **base** de datos es una colección organizada de información o datos en un solo lugar. Una base de datos puede incluir datos como el Directorio de empleados de una organización o los métodos de pago de los clientes. En SQL, la información de la base de datos se organiza en tablas. SQL se utiliza habitualmente para recuperar, insertar, actualizar o eliminar información de las tablas mediante consultas.

Una consulta _SQL_ es una solicitud de datos de una base de datos. Por ejemplo, una consulta SQL puede solicitar datos del directorio de empleados de una organización, como ID, nombres y cargos de los empleados. Una aplicación de recursos humanos puede aceptar una entrada que consulte una tabla SQL para filtrar los datos y localizar a una persona concreta. Las inyecciones de SQL pueden producirse en cualquier lugar dentro de una aplicación vulnerable que pueda aceptar una consulta SQL.

Las consultas suelen iniciarse en lugares donde los usuarios pueden introducir información en una aplicación o un sitio web a través de un campo de entrada. Los campos de entrada incluyen elementos que aceptan la introducción de texto, como formularios de inicio de sesión, barras de búsqueda o cuadros de envío de comentarios. Una inyección de SQL se produce cuando un atacante explota campos de entrada que no están programados para filtrar el texto no deseado. Las inyecciones de SQL pueden utilizarse para manipular bases de datos, robar datos confidenciales o incluso tomar el control de aplicaciones vulnerables.

## Categorías de inyección de SQL

Existen tres categorías principales de inyección de SQL:

- Dentro de banda
    
- Fuera de banda
    
- Inferencial
    

En las siguientes secciones, aprenderá que cada tipo describe cómo se inicia una inyección de SQL y cómo devuelve los resultados del ataque.

### **Inyección de SQL en banda**

La inyección de SQL en banda, o clásica, es el tipo más común. Una inyección en banda es aquella que utiliza el _mismo canal de comunicación_ para lanzar el ataque y recoger los resultados.

Por ejemplo, esto podría ocurrir en el cuadro de búsqueda de la página web de un minorista que permite a los clientes encontrar productos para comprar. Si el cuadro de búsqueda es vulnerable a la inyección, un atacante podría introducir una consulta maliciosa que se ejecutaría en la base de datos, haciendo que ésta devolviera información sensible como las contraseñas de los usuarios. Los Datos devueltos se muestran de nuevo en el cuadro de búsqueda donde se inició el ataque.

### **Inyección de SQL fuera de banda**

Una inyección fuera de banda es aquella que utiliza un _canal de comunicación diferente_ para lanzar el ataque y recoger los resultados.

Por ejemplo, un atacante podría utilizar una consulta maliciosa para crear una conexión entre un sitio web vulnerable y una base de datos que controle. Este canal independiente les permitiría eludir cualquier control de seguridad existente en el servidor del sitio web, lo que les permitiría robar datos sensibles

**Nota:** Los ataques de inyección fuera de banda son muy poco comunes porque sólo funcionarán cuando ciertas características estén habilitadas en el servidor objetivo.

### **Inyección de SQL inferencial**

La inyección de SQL inferencial se produce cuando un atacante no puede ver directamente los resultados de su ataque. En su lugar, pueden interpretar los resultados analizando el _comportamiento_ del sistema.

Por ejemplo, un atacante puede realizar un ataque de inyección de SQL en el formulario de inicio de sesión de un sitio web que haga que el sistema responda con un mensaje de error. Aunque no se devuelven datos sensibles, el atacante puede averiguar la estructura de la base de datos basándose en el error. A continuación, puede utilizar esta información para elaborar ataques que le den acceso a datos sensibles o para hacerse con el control del sistema.

## Prevención de la inyección

Las consultas SQL se programan a menudo dando por sentado que los usuarios sólo introducirán información relevante. Por ejemplo, un formulario de acceso que espera que los usuarios introduzcan su dirección de correo electrónico asume que la entrada tendrá un formato determinado, como _jdoe@domain.com._ Por desgracia, no siempre es así.

Una clave para prevenir los ataques de inyección de SQL es _escapar_ de las entradas del usuario _, impidiendo_que alguien inserte cualquier código que un programa no esté esperando.

Existen varias formas de escapar a las entradas del usuario:

- **Sentencias preparadas**: una técnica de programación que ejecuta sentencias SQL antes de pasarlas a una base de datos
    
- **Saneamiento** de entradas: programación que elimina las entradas del usuario que podrían interpretarse como código.
    
- **Validación de** entrada: programación que garantiza que la entrada del usuario cumple las expectativas de un sistema.
    

El uso de una combinación de estas técnicas puede ayudar a prevenir los ataques de inyección de SQL. En el campo de la Seguridad, es posible que tenga que colaborar estrechamente con los desarrolladores de aplicaciones para abordar las vulnerabilidades que pueden dar lugar a inyecciones de SQL. [Las técnicas de detección de inyección de SQL de OWASP](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05-Testing_for_SQL_Injection) son un recurso útil si está interesado en investigar por su cuenta las vulnerabilidades de inyección de SQL.

## Puntos clave

Muchas aplicaciones web recuperan datos de bases de datos utilizando SQL, y los ataques de inyección son bastante comunes debido a la popularidad de este lenguaje. Como ocurre con otros tipos de ataques de inyección, las inyecciones de SQL son el resultado de una entrada inesperada del usuario. Es importante colaborar con los desarrolladores de aplicaciones para ayudar a prevenir este tipo de ataques compartiendo su conocimiento de las técnicas de inyección de SQL y las defensas que deben ponerse en marcha.