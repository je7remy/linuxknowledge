
Anteriormente, usted exploró cómo abrir archivos en Python, convertirlos en cadenas y leerlos. En esta lectura, revisará la sintaxis necesaria para ello. También se centrará en por qué la capacidad de trabajar con archivos es importante para los analistas de Seguridad que utilizan Python, y aprenderá sobre la escritura de archivos.

## Trabajar con archivos en ciberseguridad

Los analistas de Seguridad pueden necesitar acceder a una variedad de archivos cuando trabajan en Python. Muchos de estos archivos serán registros. Un **registro** A es un registro de los eventos que ocurren dentro de los sistemas de una organización.

Por ejemplo, puede haber un registro que contenga información sobre los intentos de inicio de sesión. Esto podría utilizarse para identificar una actividad inusual que señale los intentos realizados por un actor malicioso para acceder al sistema.

Como otro ejemplo, los actores maliciosos que hayan accedido al sistema podrían ser capaces de atacar aplicaciones de software. Un analista puede necesitar acceder a un registro que contenga información sobre aplicaciones de software que estén experimentando problemas.

## Abrir archivos en Python

Para abrir un archivo llamado "update_log.txt" en Python con el fin de leerlo, puede incorporar la siguiente línea de código:

with open("update_log.txt", "r") as file:

Esta línea consta de la palabra clave with, la función open() con sus dos parámetros, y la palabra clave as seguida de un nombre de variable. Debe colocar dos puntos (:) al final de la línea.

### con

La palabra clave with maneja errores y gestiona recursos externos cuando se utiliza con otras funciones. En este caso, se utiliza con la función open() para abrir un archivo. A continuación, gestionará los recursos cerrando el archivo tras salir de la sentencia with.

**Nota:** También puede utilizar la función open() sin la palabra clave with. Sin embargo, debe cerrar el archivo que abrió para garantizar un manejo adecuado del mismo.

### abrir()

La función open() abre un archivo en Python.

El primer parámetro identifica el archivo que desea abrir. En la siguiente estructura de archivos, "update_log.txt" se encuentra en el mismo directorio que el archivo Python que accederá a él, "log_parser.ipynb":

![En esta estructura de archivos, update_log.txt está en el mismo directorio que el archivo log_parser.ipynb, pero access_log.txt no.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/6yIriXeSRVusqdhshMgJzw_cde2e1d0308344e8ac1b9e276eeb41f1_gt1HZ_gwphon8kMUtMEps3S4sKej_tYPtBVgjNJ57LQh7spBmdJXNv_AEmjVXO1R9a9UW3aO7e-JyFD8QXS-r8-p7HQewrQRhKDLu6SNT4WGe6Ww8nLBSf6CgCNKHXecffXKLpmuG30GUV36lMve1C5f?expiry=1761609600000&hmac=dBPJDY4HM5zhMc9Azrc4-JWpZ9KwV3uct7S26haR9dA)

Como están en el mismo directorio, sólo se requiere el nombre del archivo. El Código puede escribirse como with open("update_log.txt", "r") as file:.

Sin embargo, "access_log.txt" no está en el mismo directorio que el archivo Python "log_parser.ipynb". Por lo tanto, es necesario especificar su ruta de archivo absoluta. Una **ruta de** archivo es la ubicación de un archivo o directorio. Una ruta de archivo absoluta comienza en el directorio de nivel más alto, el raíz. En el código siguiente, el primer parámetro de la función open() incluye la ruta de acceso absoluta a "access_log.txt":

with open("/home/analyst/logs/access_log.txt", "r") as file:

**Nota:** En Python, los nombres de archivos o sus rutas de acceso pueden manejarse como datos de cadena, y como todos los datos de cadena, debe colocarlos entre comillas.

El segundo parámetro de la función open() indica lo que desea hacer con el archivo. En estos dos ejemplos, el segundo parámetro es "r", que indica que desea leer el archivo. Alternativamente, puede utilizar "w" si desea escribir en un archivo o "a" si desea anexar a un archivo.

### como

Cuando abra un archivo utilizando with open(), debe proporcionar una variable que pueda almacenar el archivo mientras se encuentra dentro de la sentencia with. Puede hacerlo mediante la palabra clave as seguida de este nombre de variable. La palabra clave as asigna una variable que hace referencia a otro objeto. El código with open("update_log.txt", "r") as file: asigna file para referenciar la salida de la función open() dentro del bloque de código con sangría que le sigue.

## Lectura de archivos en Python

Después de utilizar el código with open("update_log.txt", "r") as file: para importar "update_log.txt" a la variable file, debe indicar qué hacer con el archivo en las líneas con sangría que le siguen. Por ejemplo, este código utiliza el método .read() para leer el contenido del archivo:

with open("update_log.txt", "r") as file:

    updates = file.read()

print(updates)

El método .read() convierte los archivos en cadenas. Esto es necesario para poder utilizar y mostrar el contenido del archivo que se ha leído.

En este ejemplo, la variable file se utiliza para generar una cadena del contenido del archivo a través de .read(). A continuación, esta cadena se almacena en otra variable llamada updates. A continuación, print(updates) muestra la cadena.

Una vez leído el archivo en la cadena updates, puede realizar sobre ella las mismas operaciones que podría realizar con cualquier otra cadena. Por ejemplo, podría utilizar el método .index() para devolver el índice donde aparece un determinado carácter o subcadena. O bien, podría utilizar len() para devolver la longitud de esta cadena.

## Escribir archivos en Python

Los analistas de Seguridad también pueden necesitar escribir en archivos. Esto podría ocurrir por una variedad de razones. Por ejemplo, podrían necesitar crear un archivo que contenga los nombres de usuario aprobados en una nueva lista de permitidos. O puede que necesiten editar archivos existentes para añadir datos o adherirse a políticas de normalización.

Para escribir en un archivo, deberá abrirlo con "w" o "a" como segundo argumento de open().

Deberá utilizar el argumento "w" cuando desee sustituir el contenido de un archivo existente. Cuando trabaje con el archivo existente update_log.txt, el código with open("update_log.txt", "w") as file: lo abre para poder reemplazar su contenido.

Además, puede utilizar el argumento "w" para crear un nuevo archivo. Por ejemplo, with open("update_log2.txt", "w") as file: crea y abre un nuevo archivo llamado "update_log2.txt".

Debe utilizar el argumento "a" si desea añadir nueva información al final de un archivo existente en lugar de escribir sobre él. El código with open("update_log.txt", "a") as file: abre "update_log.txt" para poder añadir nueva información al final. La información existente no se borrará.

Al igual que cuando se abre un archivo para leer de él, se debe indicar qué hacer con el archivo en las líneas con sangría que siguen cuando se abre un archivo para escribir en él. Tanto con "w" como con "a", puede utilizar el método .write(). El método .write() escribe datos de cadena en un archivo especificado.

El siguiente ejemplo utiliza el método .write() para añadir el contenido de la variable line al archivo "access_log.txt".

line = "jrafael,192.168.243.140,4:56:27,True"

with open("access_log.txt", "a") as file:

    file.write(line)

**Nota:** Si llama al método .write() sin utilizar la palabra clave with al importar el archivo, es posible que sus argumentos no se escriban completamente en el archivo si éste no se cierra correctamente de otra forma.

## Puntos clave

Es importante para los analistas de Seguridad ser capaces de importar archivos a Python y luego leer o escribir en ellos. Importar archivos en Python implica utilizar la palabra clave with, la función open() y la palabra clave as. La lectura desde y la escritura en archivos requiere el conocimiento de los métodos .read() y .write() y los argumentos para la función open() de "r", "w" y "a".

