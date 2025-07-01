
En esta lectura, aprenderá sobre los ataques de fuerza bruta. Estudiará cómo se pueden evaluar las vulnerabilidades utilizando máquinas virtuales y cajas de arena, y aprenderá formas de prevenir los ataques de fuerza bruta utilizando una combinación de medidas de autenticación. Implementar varias tareas de endurecimiento del OS puede ayudar a prevenir los ataques de fuerza bruta. Un atacante puede utilizar un ataque de fuerza bruta para obtener acceso y comprometer una red.

Los nombres de usuario y las contraseñas se encuentran entre los Controles de seguridad más comunes e importantes de la actualidad. Se utilizan y se hacen cumplir en todo lo que almacena o accede a información sensible o privada, como los teléfonos personales, las computadoras y las aplicaciones restringidas dentro de una organización. Sin embargo, un Problema importante de confiar en las credenciales de acceso como línea crítica de defensa es que son vulnerables a ser robadas y adivinadas por actores maliciosos.

## Ataques de fuerza bruta

Un **ataque de fuerza bruta** es un proceso de ensayo y error para descubrir información privada. Existen diferentes tipos de ataques de fuerza bruta que los actores maliciosos utilizan para adivinar contraseñas, entre ellos:

- _Ataques de fuerza bruta simples._ Cuando los atacantes intentan adivinar las credenciales de inicio de sesión de un usuario, se considera un ataque de fuerza bruta simple. Pueden hacerlo introduciendo cualquier combinación de nombres de usuario y contraseñas que se les ocurra hasta encontrar la que funcione.
    
- _Los ataques de diccionario_ utilizan una técnica similar. En los ataques de diccionario, los atacantes utilizan una lista de contraseñas de uso común y credenciales robadas en violaciones anteriores para acceder a un sistema. Se denominan ataques de diccionario porque los atacantes utilizaban originalmente una lista de palabras del diccionario para adivinar las contraseñas, antes de que las reglas de contraseñas complejas se convirtieran en una práctica habitual de Seguridad.
    

Utilizar la fuerza bruta para acceder a un sistema puede ser un proceso tedioso y lento, sobre todo cuando se hace manualmente. Existe un Rango de herramientas que los atacantes utilizan para llevar a cabo sus ataques.

## Evaluar las vulnerabilidades

Antes de que se produzca un ataque de fuerza bruta u otro incidente de ciberseguridad, las empresas pueden realizar una serie de pruebas en su red o en sus aplicaciones web para evaluar las vulnerabilidades. Los analistas pueden utilizar máquinas virtuales y cajas de arena para probar archivos sospechosos, comprobar vulnerabilidades antes de que se produzca un evento o simular un incidente de ciberseguridad.

### **Máquinas virtuales (VM)**

Las máquinas virtuales (VM) son versiones de software de las computadoras físicas. Las VM proporcionan una capa adicional de Seguridad para una organización porque pueden utilizarse para ejecutar código en un entorno aislado, evitando que el código malicioso afecte al resto de la computadora o del sistema. Las VM también pueden eliminarse y sustituirse por una imagen prístina después de probar software malicioso.

Las VM son útiles cuando se investigan máquinas potencialmente infectadas o se ejecuta software malicioso en un entorno restringido. El uso de una VM puede evitar daños en su sistema en el caso de que sus herramientas se utilicen de forma inadecuada. Las VM también le ofrecen la posibilidad de volver a un estado anterior. Sin embargo, las máquinas virtuales conllevan algunos Riesgos. Todavía existe un pequeño Riesgo de que un programa malicioso pueda escapar a la virtualización y acceder a la máquina anfitriona.

Puede probar y explorar aplicaciones fácilmente con las máquinas virtuales, y es fácil cambiar entre diferentes máquinas virtuales desde su computadora. Esto también puede ayudar a agilizar muchas tareas de Seguridad.

### **Espacios aislados**

Un entorno aislado es un tipo de entorno de pruebas que le permite ejecutar software o programas separados de su red. Suelen utilizarse para probar parches, Identificar y solucionar errores o Detectar vulnerabilidades de ciberseguridad. Los espacios aislados también pueden utilizarse para evaluar software sospechoso, evaluar archivos que contienen código malicioso y simular escenarios de ataque.

Los cajones de arena pueden ser ordenadores físicos autónomos que no están conectados a una red; sin embargo, a menudo es más rentable y económico utilizar software o máquinas virtuales basadas en la nube como entornos de cajones de arena. Tenga en cuenta que algunos autores de software malicioso saben cómo escribir código para detectar si el software malicioso se ejecuta en una VM o en un entorno de caja de arena. Los atacantes pueden programar su software malicioso para que se comporte como software inofensivo cuando se ejecuta dentro de este tipo de entornos de pruebas.

## Medidas de prevención

Algunas medidas comunes que las organizaciones utilizan para evitar que se produzcan ataques de fuerza bruta y ataques similares incluyen:

- **Salting y hash:** El hash convierte la información en un valor único que puede utilizarse para determinar su integridad. Es una función unidireccional, lo que significa que es imposible desencriptar y obtener el texto original. El salting añade caracteres aleatorios a las contraseñas hash. Esto aumenta la Longitud y la complejidad de los valores hash, haciéndolos más seguros.
    
- **Autenticación de múltiples factores (MFA) y autenticación de dos factores (2FA):** MFA es una medida de seguridad que requiere que un usuario verifique su identidad de dos o más formas para acceder a un sistema o red. Esta autenticación se realiza mediante una combinación de factores de autenticación: un nombre de usuario y una contraseña, huellas dactilares, reconocimiento facial o una contraseña de un solo uso (OTP) enviada a un número de teléfono o a un correo electrónico. la 2FA es similar a la MFA, salvo que sólo utiliza dos formas de verificación.
    
- **CAPTCHA y reCAPTCHA:** CAPTCHA son las siglas de Completely Automated Public Turing test to tell Computers and Humans Apart (Prueba de Turing pública completamente automatizada para distinguir entre ordenadores y humanos). Pide a los usuarios que completen una sencilla prueba que demuestra que son humanos. Esto ayuda a evitar que el software intente forzar una contraseña. reCAPTCHA es un servicio CAPTCHA gratuito de Google que ayuda a proteger los sitios web de bots y software malicioso.
    
- **Políticas de contraseñas:** Las organizaciones utilizan políticas de contraseñas para estandarizar las buenas prácticas de contraseñas en toda la empresa. Las políticas pueden incluir directrices sobre lo compleja que debe ser una contraseña, la frecuencia con la que los usuarios deben actualizar las contraseñas, si las contraseñas se pueden reutilizar o no, y si hay límites en el número de veces que un usuario puede intentar iniciar sesión antes de que se suspenda su cuenta.
    

## Puntos clave

Los ataques de fuerza bruta son un proceso de ensayo y error para adivinar contraseñas. Los ataques pueden lanzarse manualmente o mediante herramientas de software. Los métodos incluyen ataques de fuerza bruta simples y ataques de diccionario. Para protegerse contra los ataques de fuerza bruta, los analistas de ciberseguridad pueden utilizar sandboxes para probar archivos sospechosos, comprobar vulnerabilidades o simular ataques reales y máquinas virtuales para realizar pruebas de vulnerabilidad. Algunas medidas comunes para prevenir los ataques de fuerza bruta incluyen: hash y salting, MFA y/o 2FA, CAPTCHA y reCAPTCHA, y políticas de contraseña.

