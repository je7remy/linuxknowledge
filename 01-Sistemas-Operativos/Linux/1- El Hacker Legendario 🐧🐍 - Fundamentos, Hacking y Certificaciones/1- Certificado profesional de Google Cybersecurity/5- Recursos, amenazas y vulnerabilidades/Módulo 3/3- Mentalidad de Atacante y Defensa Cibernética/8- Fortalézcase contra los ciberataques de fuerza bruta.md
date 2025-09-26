
Los nombres de usuario y las contraseñas son uno de los controles de Seguridad más comunes e importantes que se utilizan hoy en día. Son como la cerradura de la puerta que las organizaciones utilizan para restringir el acceso a sus redes, servicios y datos. Pero un Problema importante de confiar en las credenciales de inicio de sesión como línea crítica de defensa es que son vulnerables a ser robadas y adivinadas por los atacantes.

En un vídeo, aprendió que **los ataques de fuerza bruta** son un proceso de ensayo y error para descubrir información privada. En esta lectura, conocerá las numerosas tácticas y herramientas que utilizan los Agentes de amenaza para realizar ataques de fuerza bruta. También aprenderá estrategias de prevención que las organizaciones pueden utilizar para defenderse de ellos.

## Cuestión de ensayo y error

Una forma de abrir una cerradura cerrada es probar tantas combinaciones como sea posible. Los Agentes de amenaza utilizan a veces tácticas similares para obtener acceso a una aplicación o a una red.

Los atacantes utilizan una gran variedad de tácticas para encontrar la forma de entrar en un sistema:

- Los_ataques de fuerza bruta simples_ son un método en el que los atacantes adivinan las credenciales de inicio de sesión de un usuario. Pueden hacerlo introduciendo cualquier combinación de nombre de usuario y contraseña que se les ocurra hasta encontrar la que funcione.
    
- _Los ataques de diccionario_ son una técnica similar, salvo que en estos casos los atacantes utilizan una lista de credenciales de uso común para acceder a un sistema. Esta lista es similar a hacer coincidir una definición con una palabra de un diccionario.
    
- Los_ataques de fuerza bruta inversa_ son similares a los ataques de diccionario, salvo que comienzan con una única credencial y la prueban en varios sistemas hasta encontrar una coincidencia.
    
- El relleno de_credenciales_ es una táctica en la que los atacantes utilizan credenciales de inicio de sesión robadas de anteriores violaciones de datos para acceder a cuentas de usuarios en otra organización. Un tipo especializado de relleno de credenciales se denomina _pasar el hash_. Estos ataques reutilizan credenciales robadas y sin hash para engañar a un sistema de autenticación para que cree una nueva sesión de usuario autenticada en la red.
    

**Nota:** Además de las credenciales de acceso, la información encriptada a veces puede ser forzada mediante una técnica conocida como _búsqueda exhaustiva de claves_.

Cada uno de estos métodos implica muchas conjeturas. La fuerza bruta para entrar en un sistema puede ser un proceso tedioso y lento, sobre todo cuando se hace manualmente. Por eso los agentes de amenaza suelen utilizar herramientas para llevar a cabo sus ataques.

## Herramientas del oficio

Existen muchas combinaciones que pueden utilizarse para crear un único conjunto de credenciales de inicio de sesión. El número de caracteres, letras y números que pueden mezclarse es realmente increíble. Si se hace manualmente, alguien podría tardar años en probar todas las combinaciones posibles.

En lugar de dedicar el tiempo necesario para hacerlo, los atacantes suelen utilizar software que hace el trabajo de adivinación por ellos. Estas son algunas herramientas comunes de fuerza bruta:

- Aircrack-ng
    
- Hashcat
    
- John el Destripador
    
- Ophcrack
    
- THC Hydra
    

A veces, los profesionales de la Seguridad utilizan estas herramientas para probar y analizar sus propios sistemas. Cada una de ellas sirve para fines diferentes. Por ejemplo, puede utilizar Aircrack-ng para probar una red Wi-Fi en busca de vulnerabilidades ante ataques de fuerza bruta.

## Medidas de prevención

Las organizaciones se defienden de los ataques de fuerza bruta con una combinación de controles técnicos y de gestión. Cada uno de ellos hace que sea menos probable descifrar los sistemas de defensa mediante la fuerza bruta:

- Hashing y salting
    
- Autenticación de múltiples factores (MFA)
    
- CAPTCHA
    
- Políticas de contraseñas
    

Las tecnologías, como la autenticación de múltiples factores (MFA), refuerzan cada intento de inicio de sesión exigiendo una segunda o tercera forma de identificación. Otras herramientas importantes son los CAPTCHA y las políticas de contraseñas eficaces.

### **Hashing y salting**

El hash convierte la información en un valor único que puede utilizarse para determinar su integridad. **El** salting es una salvaguarda adicional que se utiliza para reforzar las funciones hash. Funciona añadiendo caracteres aleatorios a los Datos, como las contraseñas. Esto aumenta la longitud y la complejidad de los valores hash, haciéndolos más difíciles de forzar y menos susceptibles a los ataques de diccionario.

### **Autenticación de múltiples factores (MFA)**

La**autenticación de múltiples** factores (MFA) es una medida de seguridad que requiere que un usuario verifique su identidad de dos o más formas para acceder a un sistema o red. MFA es un enfoque por capas para proteger la Información. MFA limita las posibilidades de ataques de fuerza bruta porque es poco probable que los usuarios no autorizados cumplan cada uno de los requisitos de autenticación, incluso si una credencial se ve comprometida.

### **CAPTCHA**

CAPTCHA son las siglas de Completely Automated Public Turing test to tell Computers and Humans Apart (Prueba de Turing Pública Completamente Automatizada para distinguir ordenadores y humanos). Se conoce como un sistema de autenticación desafío-respuesta. CAPTCHA pide a los usuarios que completen una sencilla prueba que demuestra que son humanos y no un software que intenta forzar una contraseña.

Aquí tiene ejemplos comunes de CAPTCHA:

![Comparación de un CAPTCHA basado en texto y otro basado en imagen para verificar si un usuario es humano.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/tPsircWORfqlMVM3Pj3fEw_4ef34f0193e5481e8cac9e2379a02cf1_S36G003.png?expiry=1759017600000&hmac=o5Wi9gmlpospSqTz72jGLpSg1eeE-KaLGGARf9ct0HM)

Existen dos tipos de pruebas CAPTCHA. Una codifica y distorsiona una secuencia de letras y/o números generada aleatoriamente y pide a los usuarios que la introduzcan en un cuadro de texto. La otra prueba pide a los usuarios que emparejen imágenes con una palabra generada aleatoriamente. Es probable que haya tenido que pasar una prueba CAPTCHA al acceder a un servicio web que contiene información confidencial, como una cuenta bancaria en línea.

### **Política de contraseñas**

Las organizaciones utilizan estos controles de gestión para estandarizar las buenas prácticas de contraseñas en toda su empresa. Por ejemplo, una de estas políticas puede exigir a los usuarios que creen contraseñas que tengan al menos 8 caracteres y que incluyan una letra, un número y un símbolo. Otros requisitos comunes pueden incluir políticas de bloqueo de contraseñas. Por ejemplo, un bloqueo de contraseñas puede limitar el número de intentos de inicio de sesión antes de que se suspenda el acceso a una cuenta y exigir a los usuarios que creen contraseñas nuevas y únicas después de un tiempo determinado.

El objetivo de cada uno de estos requisitos es crear más combinaciones posibles de contraseñas. Esto alarga el tiempo que tarda un atacante en encontrar una que funcione. La [Publicación Especial 800-63B del Instituto Nacional de Estándares y Tecnología (NIST](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b.pdf) ) proporciona una guía detallada que las organizaciones pueden consultar a la hora de crear sus propias políticas de contraseñas.

## Puntos clave

Los ataques de fuerza bruta son formas sencillas pero fiables de obtener acceso no autorizado a los sistemas. Generalmente, cuanto más fuerte es una contraseña, más resistente es a ser descifrada. COMO profesional de la seguridad, es posible que se encuentre utilizando las herramientas descritas anteriormente para comprobar la Seguridad de los sistemas de su organización. Reconocer las tácticas y herramientas utilizadas para llevar a cabo un ataque de fuerza bruta es el primer paso para detener a los atacantes.