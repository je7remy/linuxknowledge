
Anteriormente, aprendiste estos términos:

- **Cifrado**: proceso de conversión de datos de un formato legible a un formato codificado
    
- **Infraestructura de clave pública** (PKI): marco de cifrado que protege el intercambio de información en línea
    
- **Cifrado**: algoritmo que cifra la información
    

Toda la información digital merece mantenerse privada, segura y protegida. El cifrado es una de las claves para conseguirlo Sirve para transformar la información en una forma que los destinatarios no deseados no puedan entender. En esta lectura, compararás la criptografía simétrica y la asimétrica y conocerás algunos algoritmos conocidos de cada una de ellas.

## Tipos de cifrado

Existen dos tipos principales de cifrado:

- **Cifrado simétrico**: consiste en utilizar una única clave secreta para intercambiar información. Como utiliza una sola clave para cifrar y descifrar, el emisor y el receptor deben conocer la clave secreta para bloquear o desbloquear el cifrado.
    
- La**criptografía asimétrica** es el uso de un par de claves pública y privada para cifrar y descifrar datos. Utiliza dos claves distintas: una pública y otra privada. La clave pública se utiliza para cifrar los datos y la privada para descifrarlos. La clave privada sólo se entrega a los usuarios con acceso autorizado.
    

## La importancia de la longitud de la clave

Los cifradores son vulnerables a **los ataques de fuerza bruta**, que utilizan un proceso de ensayo y error para descubrir información privada. Esta táctica es el equivalente digital de probar todos los números de una cerradura de combinación intentando dar con el correcto. En el cifrado moderno, las longitudes de la clave más largas se consideran más seguras. Una longitud de la clave más larga significa más posibilidades de que un atacante intente descifrar un cifrado.

Uno de los inconvenientes de tener claves de cifrado largas es que los tiempos de procesamiento son más lentos. Aunque las longitudes de la clave cortas suelen ser menos seguras, su cálculo es mucho más rápido. Proporcionar una comunicación de datos rápida en línea y, al mismo tiempo, mantener la seguridad de la información es un delicado ejercicio de equilibrio.

## Algoritmos aprobados

Muchas aplicaciones web utilizan una combinación de criptografía asimétrica y simétrica. Así equilibran la experiencia del usuario con la salvaguarda de la información. Como analista, debe conocer los algoritmos más utilizados.

### **Algoritmos simétricos**

- _Triple DES (3DES)_ se conoce como algoritmo de cifrado por bloques por la forma en que convierte el texto plano en texto cifrado en "bloques" Sus orígenes se remontan al Data Encryption Standard (DES), desarrollado a principios de la década de 1970. DES fue uno de los primeros algoritmos de encriptación simétrica que generaba claves de 64 bits, aunque sólo se utilizan 56 bits para la encriptación. Un **bit** es la unidad más pequeña de medida de datos en un ordenador. Como se puede imaginar, Triple DES genera claves tres veces más largas. Triple DES aplica el algoritmo DES tres veces, utilizando tres claves diferentes de 56 bits. El resultado es una longitud de la clave efectiva de 168 bits. A pesar de que las claves son más largas, muchas organizaciones están dejando de utilizar Triple DES debido a las limitaciones en la cantidad de datos que pueden cifrarse. Sin embargo, es probable que Triple DES siga utilizándose por motivos de retrocompatibilidad.
    
- _Estándar de encriptación avanzada (AES)_ es uno de los algoritmos simétricos más seguros de la actualidad. AES genera claves de 128, 192 o 256 bits. Se considera que las claves criptográficas de este tamaño están a salvo de ataques de fuerza bruta. Se calcula que forzar una clave AES de 128 bits podría llevarle a un ordenador moderno miles de millones de años
    

### **Algoritmos asimétricos**

- _Rivest Shamir Adleman (RSA_) debe su nombre a sus tres creadores, que lo desarrollaron en el Instituto Tecnológico de Massachusetts (MIT). RSA es uno de los primeros algoritmos de criptografía asimétrica que produce un par de claves pública y privada. Los algoritmos asimétricos como RSA producen longitudes de la clave aún más largas. En parte, esto se debe al hecho de que estas funciones crean dos claves. Los tamaños de la clave RSA son de 1.024, 2.048 o 4.096 bits. RSA se utiliza principalmente para proteger datos muy sensibles.
    
- _Algoritmo de firma digital (DSA)_ es un algoritmo asimétrico estándar que introdujo el NIST a principios de la década de 1990. DSA también genera longitudes de la clave de 2.048 bits. Este algoritmo se utiliza mucho hoy en día como complemento de RSA en infraestructuras de clave pública.
    

### **Generación de claves**

Estos algoritmos deben implementarse cuando una organización elige uno para proteger sus datos. Una forma de hacerlo es utilizando OpenSSL, que es una herramienta de línea de comandos de código abierto que puede utilizarse para generar claves públicas y privadas. OpenSSL se utiliza habitualmente en ordenadores para verificar certificados digitales que se intercambian como parte de la Infraestructura de clave pública.

**Nota:** OpenSSL es sólo una opción. Hay varias otras disponibles que pueden generar claves con cualquiera de estos algoritmos comunes.

A principios de 2014, OpenSSL reveló una vulnerabilidad, conocida como el [bug Heartbleed](https://en.wikipedia.org/wiki/Heartbleed), que exponía datos sensibles en la memoria de sitios web y aplicaciones. Aunque todavía existen versiones no parcheadas de OpenSSL, el fallo Heartbleed fue parcheado a finales de ese mismo año (2014). En la actualidad, muchas empresas utilizan las versiones seguras de OpenSSL para generar claves públicas y privadas, lo que demuestra la importancia de utilizar software actualizado.

## La oscuridad no es seguridad

En el mundo de la criptografía, hay que demostrar que un cifrado es indescifrable antes de afirmar que es seguro. Según [el principio de Kerckhoffs](https://en.wikipedia.org/wiki/Kerckhoffs%27s_principle), la criptografía debe diseñarse de forma que todos los detalles de un algoritmo -excepto la clave privada- sean conocibles sin sacrificar su seguridad. Por ejemplo, se puede acceder en línea a todos los detalles sobre el funcionamiento del cifrado AES y, sin embargo, sigue siendo indescifrable.

En ocasiones, las organizaciones implementan sus propios algoritmos de encriptación personalizados. Ha habido casos en los que esos sistemas criptográficos secretos han sido rápidamente descifrados tras hacerse públicos.

**Consejo profesional:** un sistema criptográfico _no debe_ considerarse seguro si requiere que se mantenga en secreto su funcionamiento.

### El cifrado está en todas partes

Las empresas utilizan tanto la criptografía simétrica como la asimétrica. A menudo trabajan en equipo, equilibrando la seguridad con la experiencia del usuario.

Por ejemplo, los sitios web tienden a utilizar la criptografía asimétrica para proteger pequeños bloques de datos que son importantes. Los nombres de usuario y las contraseñas suelen protegerse con criptografía asimétrica mientras se procesan las solicitudes de acceso. Una vez que el usuario obtiene acceso, el resto de su sesión web suele pasar a utilizar cifrado simétrico por su rapidez.

La ley exige cada vez más el uso de este tipo de cifrado de datos. Reglamentos como el Federal Information Processing Standard (FIPS 140-3) y el Reglamento General de Protección de Datos (GDPR) describen cómo deben recopilarse, utilizarse y manejarse los datos. Lograr el cumplimiento de cualquiera de estas normativas es fundamental para demostrar a los socios comerciales y a los gobiernos que los datos de los clientes se manejan de forma responsable.

## Puntos clave

Conocer los fundamentos del cifrado es importante para todos los profesionales de la seguridad. El Cifrado simétrico se basa en una única clave secreta para proteger los datos. Por otro lado, el asimétrico utiliza un par de claves pública y privada. Sus algoritmos de encriptación crean diferentes tamaños de la clave. Ambos tipos de cifrado se utilizan para cumplir la normativa y proteger los datos en línea.