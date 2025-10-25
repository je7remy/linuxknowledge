
Anteriormente, se le presentó la Guía de estilo PEP 8 y sus directrices de estilo para los programadores que trabajan en Python. También aprendió cómo añadir comentarios y utilizar una correcta indentación hace que su código sea más legible. Además, una correcta indentación garantiza que su código se ejecute correctamente. Esta lectura profundiza en estas ideas y también se centra en los elementos comunes que debe comprobar en la sintaxis de su código para asegurarse de que se ejecuta.

## Comentarios

Un **comentario** es una nota que hacen los programadores sobre las intenciones que hay detrás de su código. Los Comentarios le facilitan a usted y a otros programadores la lectura y comprensión de su código.

Es importante comenzar su código con un comentario que explique lo que hace el programa. Después, a lo largo del código, debería añadir comentarios adicionales sobre sus intenciones detrás de secciones específicas.

Cuando añada comentarios, puede añadir tanto comentarios de una sola línea como comentarios de varias líneas.

### **Comentarios de una sola línea**

Los comentarios de una sola línea en Python comienzan con el símbolo (#). De acuerdo con la Guía de estilo PEP 8, es una buena práctica mantener todas las líneas en Python por debajo de 79 caracteres para mantener la legibilidad, y esto incluye los comentarios.

Los comentarios de una sola línea se utilizan a menudo a lo largo de su programa para explicar la intención detrás de secciones específicas de código. Por ejemplo, esto podría ser cuando usted está explicando los componentes más simples de su programa, como el siguiente for bucle:

# Print elements of 'computer_assets' list

computer_assets = ["laptop1", "desktop20", "smartphone03"]

for asset in computer_assets:

    print(asset)

**Nota:** Los comentarios son importantes cuando se escribe código más complejo, como funciones, o bucles múltiples o sentencias condicionales. Sin embargo, son opcionales cuando se escribe código menos complejo, como la reasignación de una variable.

### **Comentarios multilínea**

Los comentarios multilínea se utilizan cuando se necesitan más de 79 caracteres en un solo comentario. Por ejemplo, esto puede ocurrir al definir una función si el comentario describe sus entradas y sus tipos de datos, así como su salida.

Hay dos formas habituales de escribir comentarios multilínea en Python. La primera es utilizando el símbolo Hashtag (#) sobre varias líneas:

# remaining_login_attempts() function takes two integer parameters,

# the maximum login attempts allowed and the total attempts made,

# and it returns an integer representing remaining login attempts

def remaining_login_attempts(maximum_attempts, total_attempts):

    return maximum_attempts - total_attempts

Otra forma de escribir comentarios multilínea es utilizando cadenas de documentación y no asignándolas a una variable. Las cadenas de documentación, también llamadas docstrings, son cadenas que se escriben sobre varias líneas y se utilizan para documentar código. Para crear una cadena de documentación, utilice comillas triples (""" """).

También podría añadir de este modo el comentario a la función del ejemplo anterior:

"""

remaining_login_attempts() function takes two integer parameters,

the maximum login attempts allowed and the total attempts made,

and it returns an integer representing remaining login attempts

"""

## Indentación correcta

La**indentación** es el espacio que se añade al principio de una línea de código. En Python, debe sangrar el cuerpo de las sentencias condicionales, las sentencias iterativas y las definiciones de funciones. La indentación no sólo es necesaria para que Python interprete correctamente esta sintaxis, sino que también puede facilitarle a usted y a otros programadores la lectura de su código.

La Guía de estilo PEP 8 recomienda que las indentaciones sean de cuatro espacios. Por ejemplo, si tuviera una sentencia condicional dentro de un bucle while, el cuerpo del bucle tendría una sangría de cuatro espacios y el cuerpo de la condicional tendría una sangría de cuatro espacios más allá. Esto significa que la condicional tendría una sangría de ocho espacios en total.

count = 0

login_status = True

while login_status == True:

    print("Try again.")

    count = count + 1

    if count == 4:

        login_status = False

## Mantener una sintaxis correcta

Los errores de sintaxis implican un uso no válido del lenguaje Python. Son increíblemente comunes con Python, por lo que centrarse en la sintaxis correcta es esencial para garantizar que su código funcione. Ser consciente de los errores comunes le ayudará a solucionarlos más fácilmente.

Los errores de sintaxis suelen producirse por equivocaciones con los tipos de datos o en los encabezados de las sentencias iterativas o condicionales o de las definiciones de funciones.

### Tipos de datos

La sintaxis correcta varía en función del tipo de datos:

- Coloque los Datos de cadena entre comillas.
    
    - Ejemplo: username = "bmoreno"
        
- No entrecomille los tipos de datos enteros, flotantes o booleanos.
    
    - Ejemplos: login_attempts = 5, percentage_successful = .8, login_status = True
        
- Coloque las listas entre paréntesis y separe los elementos de una lista con comas.
    
    - Ejemplo: username_list = ["bmoreno", "tshah"]
        

### Dos puntos en las cabeceras

El encabezado de una Sentencia iterativa o condicional o de una definición de función debe terminar con dos puntos. Por ejemplo, aparecen dos puntos al final de la cabecera en la siguiente definición de función:

def remaining_login_attempts(maximum_attempts, total_attempts):

    return maximum_attempts - total_attempts

## Puntos clave

La Guía de estilo PEP 8 ofrece recomendaciones para escribir código que pueda ser comprendido y leído fácilmente por otros programadores de Python. Para dejar claras sus intenciones, debe incorporar comentarios a su código. Dependiendo de la longitud del comentario, puede seguir las convenciones para comentarios de una o varias líneas. También es importante utilizar una indentación correcta; esto garantiza que su código se ejecute según lo previsto y también facilita su lectura. Por último, también debe ser consciente de los problemas de sintaxis más comunes para poder solucionarlos más fácilmente.

## Recursos para obtener más Información

Aprender a escribir código legible puede ser todo un reto, así que asegúrese de revisar la Guía de estilo PEP 8 y conocer otros aspectos de la legibilidad del código.

- PEP 8[- Guía de estilo para código Python](https://peps.python.org/pep-0008/): La Guía de estilo PEP 8 contiene todos los Estándares del Código Python. Cuando lea esta guía, es útil utilizar la tabla de contenidos para navegar por los conceptos que aún no ha aprendido.