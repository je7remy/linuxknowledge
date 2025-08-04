
En esta lectura, continuarás explorando los comandos de Linux, que pueden ayudarte a filtrar la información que necesitas. Aprenderás un nuevo comando de Linux, find, que puede ayudarte a buscar información específica en archivos y directorios.

## Filtrar información

Anteriormente exploraste cómo filtrar información es una habilidad importante para los analistas de seguridad. **Filtrar** es seleccionar datos que coincidan con una determinada condición. Por ejemplo, si tuviera un virus en su sistema que sólo afectara a los archivos .txt, podría utilizar el filtrado para encontrar estos archivos rápidamente. El filtrado te permite buscar basándote en criterios específicos, como la extensión de archivo o una cadena de texto.

## grep

El comando **grep** busca en un archivo especificado y devuelve todas las líneas del archivo que contengan una cadena o texto especificado. El comando **grep** suele tomar dos argumentos: una cadena específica que buscar y un archivo específico en el que buscar.

Por ejemplo, si se introduce **grep** **OS** **updates****.txt**, se obtendrán todas las líneas que contengan **OS** en el archivo **updates****.txt**. En este ejemplo, **OS** es la cadena específica que se busca y **updates.** txt es el archivo específico que se busca.

Veamos otro ejemplo: **grep error time_logs.txt**. Aquí se utiliza grep para buscar el patrón de texto. **error** es el término que se busca en el archivo **time_logs.** txt. Cuando ejecutes este comando, grep escaneará el archivo time_logs.txt e imprimirá sólo las líneas que contengan la palabra **error**.

## Canalización

Para acceder al comando pipe se utiliza el carácter pipe (|). El comando **pipe** envía la salida estándar de un comando como entrada estándar a otro comando para su posterior procesamiento. Como recordatorio, **la salida estándar** es la información devuelta por el OS a través del shell, y **la entrada estándar** es la información recibida por el OS a través de la línea de comandos.

El carácter pipe (|) se encuentra en varios lugares del teclado. En muchos teclados, se encuentra en la misma tecla que el carácter de barra invertida (\). En algunos teclados, el | puede parecer diferente y tener un pequeño espacio en medio de la línea. Si no encuentra el |, busque en Internet su ubicación en su teclado concreto.

Cuando se utiliza con grep, la tubería puede ayudarle a encontrar directorios y archivos que contengan una palabra específica en sus nombres. Por ejemplo, ls /home/analyst/reports | grep users devuelve los nombres de archivos y directorios del directorio reports que contienen users. Antes de la tubería, ls indica que se listen los nombres de los archivos y directorios en reports. Luego, envía esta salida al comando después de la tubería. En este caso, grep users devuelve todos los nombres de archivos o directorios que contienen users de la entrada que recibió.

**Nota:** La canalización es una forma general de redirección en Linux y puede utilizarse para múltiples tareas además del filtrado. Puedes pensar en piping como una herramienta general que puedes usar siempre que quieras que la salida de un comando se convierta en la entrada de otro comando.

## buscar

El comando find busca directorios y archivos que cumplan los criterios especificados. Existe una amplia gama de criterios que pueden especificarse con find. Por ejemplo, puede buscar archivos y directorios que

- Contengan una cadena específica en el nombre,
    
- Tengan un determinado tamaño, o
    
- Hayan sido modificados por última vez en un periodo de tiempo determinado.
    

Cuando se utiliza find, el primer argumento después de find indica dónde empezar a buscar. Por ejemplo, si se introduce find /home/analyst/projects, se buscará todo a partir del directorio projects.

Después de este primer argumento, debe indicar sus criterios para la búsqueda. Si no incluye un criterio de búsqueda específico con el segundo argumento, es probable que la búsqueda devuelva muchos directorios y archivos.

La especificación de criterios implica opciones. **Las opciones** modifican el comportamiento de un comando y suelen comenzar con un guión (-).

### **-nombre y -nombre**

Un criterio clave que los analistas pueden utilizar con find es encontrar nombres de archivos o directorios que contengan una cadena específica. La cadena específica que se busca debe introducirse entre comillas después de las opciones -name o -iname. La diferencia entre estas dos opciones es que -name distingue entre mayúsculas y minúsculas, y -iname no.

Por ejemplo, puede que desee encontrar todos los archivos del directorio projects que contengan la palabra "log" en el nombre del archivo. Para ello, escriba find /home/analyst/projects -name "*log*". También podría introducir find /home/analyst/projects -iname "*log*".

En estos ejemplos, el resultado serían todos los archivos del directorio projects que contengan log rodeado de cero o más caracteres. La parte "*log*" del comando es el criterio de búsqueda que indica que se busque la cadena "log". Cuando -name es la opción, los archivos con nombres que incluyan Log o LOG, por ejemplo, no se devolverían porque esta opción distingue entre mayúsculas y minúsculas. Sin embargo, sí se devolverán si la opción es -iname.

**Nota**: Se utiliza un asterisco (*) como comodín para representar cero o más caracteres desconocidos.

### **-mtime**

Los analistas de seguridad también pueden utilizar find para buscar archivos o directorios modificados por última vez en un periodo de tiempo determinado. Para esta búsqueda se puede utilizar la opción -mtime. Por ejemplo, al introducir find /home/analyst/projects -mtime -3 se obtienen todos los archivos y directorios del directorio projects que se han modificado en los últimos tres días.

La búsqueda de la opción -mtime se basa en días, por lo que al introducir -mtime +1 se indican todos los archivos o directorios modificados por última vez hace más de un día, y al introducir -mtime -1 se indican todos los archivos o directorios modificados por última vez hace menos de un día.

**Nota:** Puede utilizarse la opción -mmin en lugar de -mtime si se desea basar la búsqueda en minutos en lugar de días.

## Puntos clave

El filtrado de información mediante comandos de Linux es una habilidad importante para los analistas de seguridad, de modo que puedan adaptar los datos a sus necesidades. Tres comandos clave de Linux para esto son grep, piping (|), y find. Estos comandos pueden utilizarse para navegar y filtrar información en el sistema de archivos.

- **Considera las implicaciones de la IA para la privacidad y la seguridad**. Considera cómo el uso de herramientas de IA puede afectar a la seguridad de otras personas u organizaciones.