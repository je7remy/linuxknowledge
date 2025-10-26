
A lo largo de este curso, ha explorado la programación en Python. Se ha centrado en variables, sentencias condicionales, sentencias iterativas, funciones y una variedad de formas de trabajar con cadenas y listas. En esta lectura, explorará por qué todos estos son componentes esenciales a la hora de automatizar tareas mediante Python, y se le presentará otro componente necesario: el trabajo con archivos.

## Automatización de tareas en Python

La**Automatización** es el uso de la tecnología para reducir el esfuerzo humano y manual para realizar tareas comunes y repetitivas. Como analista de Seguridad, utilizará principalmente Python para automatizar tareas.

En este curso ha encontrado múltiples ejemplos de cómo utilizar Python para la automatización, incluyendo la investigación de inicios de sesión, Gestionar la accesibilidad y la actualización de dispositivos.

La automatización de tareas relacionadas con la ciberseguridad requiere la comprensión de los siguientes componentes de Python con los que ha trabajado en este curso:

### Variables

Una **variable** es un contenedor que almacena Datos. Las variables son esenciales para la Automatización. Sin ellas, tendría que reescribir individualmente los valores para cada acción que realice en Python.

### Sentencias condicionales

Una sentencia **condicional** es una sentencia que evalúa el código para determinar si cumple una serie de condiciones especificadas. Las sentencias condicionales le permiten comprobar las condiciones antes de realizar acciones. Esto es mucho más eficaz que evaluar manualmente si se debe aplicar una acción a cada dato por separado.

### Sentencias iterativas

Una **sentencia iterativa** es código que ejecuta repetidamente un conjunto de instrucciones. Ha explorado dos tipos de sentencias iterativas: los bucles for y los bucles while. En ambos casos, le permiten realizar las mismas acciones un cierto número de veces sin necesidad de volver a escribir el mismo código cada vez. El uso de un bucle for le permite automatizar la repetición de ese código basándose en una secuencia, y el uso de un bucle while le permite automatizar la repetición basándose en una condición.

### Funciones

Una **función** es una sección de código que puede reutilizarse en un programa. Las funciones le ayudan a automatizar sus tareas reduciendo la necesidad de incorporar el mismo código en múltiples lugares de un programa. En su lugar, puede definir la función una vez y llamarla donde la necesite.

Puede desarrollar sus propias funciones en función de sus necesidades particulares. También puede incorporar las funciones incorporadas que existen directamente en Python sin necesidad de codificarlas manualmente.

### Técnicas para trabajar con cadenas

Datos de cadena es uno de los tipos de datos más comunes que encontrará al automatizar tareas de ciberseguridad a través de Python, y hay un montón de técnicas que hacen que trabajar con cadenas sea eficiente. Puede utilizar la notación entre corchetes para acceder a los caracteres de una cadena a través de sus índices. También puede utilizar una gran variedad de funciones y métodos cuando trabaje con cadenas, como str(), len() y .index().

### Técnicas para trabajar con listas

Los Datos de lista son otro tipo de datos común. Al igual que con las cadenas, puede utilizar la notación entre corchetes para acceder a un elemento de la lista a través de su índice. Varios métodos también le ayudarán con la Automatización al trabajar con listas. Entre ellos se incluyen .insert(), .remove(), .append() y .index().

### Ejemplo: Contar los inicios de sesión realizados por un usuario marcado

COMO UN EJEMPLO, puede que necesite investigar los inicios de sesión de un usuario específico que ha sido marcado por actividad inusual. Concretamente, usted es responsable de contar cuántas veces se ha registrado este usuario durante el día. Si se le proporciona una Lista identificando el nombre de usuario asociado a cada intento de inicio de sesión realizado ese día, puede automatizar esta investigación en Python.

Para automatizar la investigación, necesitará incorporar los siguientes componentes de Python:

- Un bucle for le permitirá iterar a través de todos los nombres de usuario de la lista.
    
- Dentro del bucle for, deberá incorporar una sentencia condicional para examinar si cada nombre de usuario de la lista coincide con el nombre de usuario del usuario marcado.
    
- Cuando la condición se evalúe como True, también deberá incrementar una variable contador que lleve la cuenta del número de veces que el usuario marcado aparece en la lista.
    

Además, si desea reutilizar este código varias veces, puede incorporarlo a una función. La función puede incluir parámetros que acepten el nombre de usuario del usuario marcado y la lista por la que iterar. (La lista contendría los nombres de usuario asociados a todos los intentos de inicio de sesión realizados ese día) La función puede utilizar la variable contador para devolver el número de inicios de sesión de ese usuario marcado.

## Trabajar con archivos en Python

Un componente adicional de la automatización de tareas relacionadas con la ciberseguridad en Python es entender cómo trabajar con archivos. Los datos relacionados con la seguridad se encontrarán a menudo inicialmente en archivos de registro. Un **registro** A es un registro de los eventos que ocurren dentro de los sistemas de una organización. En los registros, a menudo se añaden líneas al registro a medida que pasa el tiempo.

Dos formatos de archivo comunes para los registros de Seguridad son los archivos .txt y los archivos .csv. Tanto los archivos .txt como los .csv son tipos de archivos de texto, lo que significa que sólo contienen texto sin formato. No contienen imágenes y no especifican propiedades gráficas del texto, como la fuente, el color o el espaciado. En un archivo .csv, o un archivo de "valores separados por comas", los Valores están separados por comas. En un archivo .txt, no existe un formato específico para separar los valores, y éstos pueden separarse de diversas formas, incluidos los espacios.

Puede extraer fácilmente datos de los archivos .txt y .csv. También puede convertir ambos a otros formatos de archivo.

A continuación, aprenderá a importar, leer de y escribir en archivos. También explorará cómo estructurar la información contenida en los archivos.

## Puntos clave

Es importante que los analistas de Seguridad sean capaces de automatizar tareas en Python. Para ello es necesario conocer los conceptos fundamentales de Python, incluidas las variables, las sentencias condicionales, las sentencias iterativas y las técnicas para trabajar con cadenas y listas. Además, la capacidad de trabajar con archivos también es esencial para la Automatización en Python.