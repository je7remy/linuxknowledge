
Anteriormente, usted exploró las sentencias condicionales y cómo son útiles en la automatización de tareas en Python. Hasta ahora, se ha centrado en las palabras clave if y else. En esta lectura, las revisará y aprenderá otra palabra clave, elif. También aprenderá cómo puede aplicar los operadores and, or y not a sus condiciones.

## Cómo funcionan las sentencias condicionales

Una sentencia **condicional** es una sentencia que evalúa el código para determinar si cumple un conjunto específico de condiciones. Cuando se cumple una condición, se evalúa a un valor booleano de True y realiza las acciones especificadas. Cuando la condición no se cumple, evalúa un valor booleano de False y no realiza las acciones especificadas.

En las sentencias condicionales, la condición suele basarse en la comparación de dos valores. Esta tabla resume los operadores de comparación más comunes utilizados para comparar valores numéricos.

|**operador**|**uso**|
|---|---|
|>|mayor que|
|<|menor que|
|>=|mayor que o igual a|
|<=|menor o igual que|
|==|igual a|
|!=|no igual a|

**Nota:** Los operadores igual a (==) y no igual a (!=) también se utilizan habitualmente para comparar datos de cadenas.

## sentencias if

La palabra clave if inicia una sentencia condicional. Es un componente necesario de cualquier sentencia condicional. En el siguiente ejemplo, if inicia una sentencia que indica a Python que imprima un mensaje "OK" cuando el código de estado de la respuesta HTTP sea igual a 200:

if status == 200:

    print("OK")

Este código consta de una cabecera y un cuerpo.

### **Encabezado de una sentencia if**

La primera línea de este código es el encabezado. En la cabecera de una sentencia if, la palabra clave if va seguida de la condición. Aquí, la condición es que la variable status sea igual a un valor de 200. La condición puede colocarse entre paréntesis:

if (status == 200):

    print("OK")

En casos como éste, colocar paréntesis alrededor de las condiciones en Python es opcional. Puede incluirlos si le ayuda con la legibilidad del código. Sin embargo, esta condición se procesará de la misma manera si se escribe sin paréntesis.

En otras situaciones, debido a que Python evalúa primero las condiciones entre paréntesis, los paréntesis pueden afectar a la forma en que Python procesa las condiciones. Leerá más sobre una de ellas en la sección de esta lectura sobre not.

**Nota:** Siempre debe colocar dos puntos (:) al final del encabezado. Sin esta sintaxis, el código producirá un error.

**El cuerpo de una sentencia if**

Después del encabezado de una sentencia if viene el cuerpo de la sentencia if. Esto le dice a Python qué acción o acciones debe realizar cuando la condición se evalúa a True. En este ejemplo, sólo hay una acción, imprimir "OK" en la pantalla. En otros casos, puede haber más líneas de programación con acciones adicionales.

**Nota:** Para que el cuerpo de la sentencia if se ejecute según lo previsto, debe tener una sangría mayor que la de la cabecera. Además, si hay varias líneas de código dentro del cuerpo, todas deben tener una sangría coherente.

## Continuación de condicionales con else y elif

En el ejemplo anterior, si el código de respuesta de estado HTTP no fuera igual a 200, la condición se evaluaría como False y Python continuaría con el resto del programa. Sin embargo, también es posible especificar acciones alternativas con else y elif.

### **sentencias else**

La palabra clave else precede a una sección de código que sólo se evalúa cuando todas las condiciones que la preceden dentro de la sentencia condicional se evalúan a False.

En el siguiente ejemplo, cuando el código de estado de la respuesta HTTP no es igual a 200, imprime un mensaje alternativo de "check other status":

if status == 200:

    print("OK")

else:

    print("check other status")

**Nota:** Al igual que con if, se requieren dos puntos (:) después de else, y el cuerpo que sigue al encabezado else está sangrado.

### **sentencias elif**

En algunos casos, puede tener múltiples acciones alternativas que dependen de nuevas condiciones. En ese caso, puede utilizar elif. La palabra clave elif precede a una condición que sólo se evalúa cuando las condiciones previas se evalúan a False. A diferencia de else, puede haber múltiples sentencias elif a continuación de if.

Por ejemplo, es posible que desee imprimir un mensaje si el código de estado de respuesta HTTP es 200, otro mensaje si es 400, y otro si es 500. El siguiente código demuestra cómo puede utilizar elif para ello:

if status == 200:

    print("OK")

elif status == 400:

    print("Bad Request")

elif status == 500:

    print("Internal Server Error") 

Python comprobará primero si el valor de status es 200, y si éste se evalúa como False, pasará a la primera sentencia elif. Allí, comprobará si el valor de status es 400. Si se evalúa como True, imprimirá "Bad Request", pero si se evalúa como False, pasará a la siguiente sentencia elif.

Si desea que el código imprima otro mensaje cuando todas las condiciones se evalúen a False, entonces puede incorporar else después de la última elif. En este ejemplo, si llega a la sentencia else, imprime un mensaje para comprobar el estado:

if status == 200:

    print("OK")

elif status == 400:

    print("Bad Request")

elif status == 500:

    print("Internal Server Error")

else:

    print("check other status")

Al igual que con if y else, es importante colocar dos puntos (:) después del encabezado elif y aplicar una sangría al código que sigue a este encabezado.

**Nota:** Python procesa las sentencias elif múltiples de forma diferente a las sentencias if múltiples. Cuando llega a una sentencia elif que se evalúa como True, no comprobará las siguientes sentencias elif. En cambio, Python ejecutará todas las sentencias if.

## Operadores lógicos para condiciones múltiples

En algunos casos, puede querer que Python realice una acción basándose en una condición más compleja. Podría requerir que dos condiciones se evalúen en True. O puede necesitar que sólo una de las dos condiciones se evalúe en True. O puede que quiera que Python realice una acción cuando una condición se evalúe a False. Los operadores and, or, y not se pueden utilizar en estos casos.

### **y**

El operador and requiere que ambas condiciones a ambos lados del operador se evalúen a True. Por ejemplo, todos los códigos de estado HTTP entre 200 y 226 se refieren a respuestas satisfactorias. Puede utilizar and para unir una condición de ser mayor o igual que 200 con otra condición de ser menor o igual que 226:

if status >= 200 and status <= 226:

    print("successful response")

Si ambas condiciones son True, se imprimirá el mensaje "successful response".

### **o**

El operador or requiere que sólo una de las condiciones a ambos lados del operador se evalúe como True. Por ejemplo, tanto un código de estado de 100 como un código de estado de 102 son respuestas informativas. Utilizando or, podría pedir a Python que imprima un mensaje "informational response" cuando el código sea 100 o 102:

if status == 100 or status == 102:

    print("informational response")

Sólo es necesario que se cumpla una de estas condiciones para que Python imprima el mensaje.

### **no**

El operador not niega una condición dada de forma que se evalúa a False si la condición es True y a True si es False. Por ejemplo, si quiere indicar que Python debe comprobar el código de estado cuando es algo fuera del rango de éxito, puede utilizar not:

if not(status >= 200 and status <= 226):

    print("check status")

Python comprueba primero si el valor de estado es mayor o igual que 200 y menor o igual que 226, y luego, debido al operador not, lo invierte. Esto significa que imprimirá el mensaje si status es menor que 200 o mayor que 226.

**Nota:** En este caso, los paréntesis son necesarios para que el código aplique not a ambas condiciones. Python evaluará primero las condiciones dentro de los paréntesis. Esto significa que primero evaluará las condiciones a ambos lados del operador and y después aplicará not a ambas.

## Puntos clave

Es importante que los analistas de Seguridad se familiaricen con las Sentencias condicionales. Las sentencias condicionales requieren la palabra clave if. También puede utilizar else y elif cuando trabaje con condicionales para especificar acciones adicionales a realizar. Los operadores lógicos and, or y not también son útiles al escribir condicionales.