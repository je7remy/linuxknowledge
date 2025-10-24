
Anteriormente, usted exploró cómo definir y llamar sus propias funciones. En esta lectura, revisará lo que aprendió sobre funciones y examinará cómo las funciones pueden mejorar la eficiencia en un entorno de ciberseguridad.

## Funciones en ciberseguridad

Una **función** es una sección de código que puede ser reutilizada en un programa. Las funciones son importantes en Python porque te permiten automatizar partes repetitivas de tu código. En ciberseguridad, es probable que adoptes algunos procesos que repetirás a menudo.

Cuando trabajes con registros de seguridad, a menudo te encontrarás con tareas que necesitan ser repetidas. Por ejemplo, si fueras responsable de encontrar actividad de inicio de sesión maliciosa basada en intentos de inicio de sesión fallidos, podrías tener que repetir el proceso para múltiples registros.

Para evitarlo, puedes definir una función que tome un registro como entrada y devuelva todos los inicios de sesión potencialmente maliciosos. Sería fácil aplicar esta función a diferentes registros.

## Definir una función

En Python, trabajarás con funciones integradas y funciones definidas por el usuario. **Funciones integradas** son funciones que existen dentro de Python y pueden ser llamadas directamente. La función print() es un ejemplo de función integrada.

**Funciones definidas por el usuario** son funciones que los programadores diseñan para sus necesidades específicas. Para definir una función, necesitas incluir una cabecera de función y el cuerpo de tu función.

### **Cabecera de la función**

La cabecera de la función es lo que indica a Python que estás empezando a definir una función. Por ejemplo, si quieres definir una función que muestre un mensaje "investigate activity", puedes incluir esta cabecera de función:

def display_investigation_message():

La palabra clave def se coloca antes del nombre de una función para definirla. En este caso, el nombre de esa función es display_investigation_message.

Los paréntesis que siguen al nombre de la función y los dos puntos (:) al final de la cabecera de la función son también partes esenciales de la sintaxis.

**Truco profesional**: Cuando nombres una función, dale un nombre que indique lo que hace. Esto hará que sea más fácil de recordar cuando la llame más tarde.

### **Cuerpo de la función**

El cuerpo de la función es un bloque de código con sangría que aparece después de la cabecera de la función y que define lo que hace la función. La sangría es muy importante cuando se escribe una función porque separa la definición de una función del resto del código.

Para añadir un cuerpo a su definición de la función display_investigation_message(), añada una línea sangrada con la función print(). Su definición de función se convierte en lo siguiente:

def display_investigation_message():

    print("investigate activity")

## Llamada a una función

Después de definir una función, puedes utilizarla tantas veces como necesites en tu código. El uso de una función después de definirla se denomina llamada a una función . Para llamar a una función, escriba su nombre seguido de un paréntesis. Así, para la función que definiste previamente, puedes usar el siguiente código para llamarla:

display_investigation_message()

Aunque utilizarás funciones de formas más complejas a medida que amplíes tus conocimientos, el siguiente código proporciona una introducción a cómo la función display_investigation_message() puede formar parte de una sección de código mayor. Puedes ejecutarla y analizar su resultado:

1

2

3

4

5

6

7

8

9

10

11

12

Restablecer

La función display_investigation_message() se utiliza dos veces en el código. Imprimirá mensajes "investigate activity" sobre dos registros diferentes cuando las condiciones especificadas se evalúen a True. En este ejemplo, sólo la primera sentencia condicional se evalúa a True, por lo que el mensaje se imprime una vez.

Este código llama a la función desde dentro de las condicionales, pero usted podría llamar a una función desde una variedad de lugares dentro del código.

**Nota:** Llamar a una función dentro del cuerpo de su definición de función puede crear un bucle infinito. Esto ocurre cuando no se combina con lógica que detiene la llamada a la función cuando se cumplen ciertas condiciones. Por ejemplo, en la siguiente definición de función, después de llamar por primera vez a func1(), continuará llamándose a sí misma y creará un bucle infinito:

def func1():

    func1()

## Puntos clave

Las funciones de Python son importantes a la hora de escribir código. Para definir tus propias funciones, necesitas los dos componentes esenciales de la cabecera de la función y el cuerpo de la función. Después de definir una función, puedes llamarla cuando sea necesario.