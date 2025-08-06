
Anteriormente, usted exploró cómo gestionar el sistema de archivos utilizando los comandos de Linux. Se introdujeron los siguientes comandos: mkdir, rmdir, touch, rm, mv, y cp. En esta lectura, revisará estos comandos, el editor de texto nano, y aprenderá otra forma de escribir en archivos.

## Creación y modificación de directorios

### **mkdir**

El comando mkdir crea un nuevo directorio. Como todos los comandos presentados en esta lectura, puede proporcionar el nuevo directorio como una ruta de archivo absoluta, que comienza desde la raíz, o como una ruta de archivo relativa, que comienza desde su directorio actual.

Por ejemplo, si desea crear un nuevo directorio llamado network en su directorio /home/analyst/logs, puede introducir mkdir /home/analyst/logs/network para crear este nuevo directorio. Si ya se encuentra en el directorio /home/analyst/logs, también puede crear este nuevo directorio introduciendo mkdir network.

**Consejo profesional**: Puede utilizar el comando ls para confirmar que se ha añadido el nuevo directorio.

### **rmdir**

El comando rmdir elimina, o borra, un directorio. Por ejemplo, si introduce rmdir /home/analyst/logs/network eliminará este directorio vacío del sistema de archivos.

**Nota**: El comando rmdir no puede eliminar directorios con archivos o subdirectorios en su interior. Por ejemplo, introducir rmdir /home/analyst devuelve un mensaje de error.

## Creación y modificación de archivos

### **touch y rm**

El comando touch crea un nuevo archivo. Este archivo no tendrá ningún contenido en su interior. Si su directorio actual es /home/analyst/reports, al introducir touch permissions.txt se crea un nuevo archivo en el subdirectorio reports llamado permissions.txt.

El comando rm elimina, o borra, un archivo. Este comando debe utilizarse con cuidado porque no es fácil recuperar los archivos borrados con rm. Para eliminar el archivo de permisos que acaba de crear, introduzca rm permissions.txt.

**Consejo profesional:** Puede verificar que permissions.txt se ha creado o eliminado correctamente introduciendo ls.

### **mv y cp**

También puede utilizar mv y cp cuando trabaje con archivos. El comando mv mueve un archivo o directorio a una nueva ubicación, y el comando cp copia un archivo o directorio en una nueva ubicación. El primer argumento después de mv o cp es el archivo o directorio que desea mover o copiar, y el segundo argumento es la ubicación a la que desea moverlo o copiarlo.

Para mover permissions.txt al subdirectorio logs, introduzca mv permissions.txt /home/analyst/logs. Al mover un archivo, éste se elimina de su ubicación original. Sin embargo, copiar un archivo no lo elimina de su ubicación original. Para copiar permissions.txt en el subdirectorio logs manteniéndolo también en su ubicación original, introduzca cp permissions.txt /home/analyst/logs.

**Nota**: El comando mv también puede utilizarse para renombrar archivos. Para renombrar un archivo, introduzca el nuevo nombre como segundo argumento en lugar de la nueva ubicación. Por ejemplo, si introduce mv permissions.txt perm.txt renombrará el archivo permissions.txt a perm.txt.

## editor de texto nano

**nano** es un editor de archivos de línea de comandos que está disponible por defecto en muchas distribuciones de Linux. Muchos principiantes lo encuentran fácil de usar, y es muy utilizado en la profesión de Seguridad. Puede realizar múltiples tareas básicas en nano, como crear nuevos archivos y modificar su contenido.

Para abrir un archivo existente en nano desde el directorio que lo contiene, introduzca nano seguido del nombre del archivo. Por ejemplo, si introduce nano permissions.txt desde el directorio /home/analyst/reports, se abrirá una nueva ventana de edición de nano con el archivo permissions.txt abierto para su edición. También puede proporcionar la ruta de acceso absoluta al archivo si no se encuentra en el directorio que lo contiene.

También puede crear un nuevo archivo en nano introduciendo nano seguido de un nuevo nombre de archivo. Por ejemplo, al introducir nano authorized_users.txt desde el directorio /home/analyst/reports se crea el archivo authorized_users.txt dentro de ese directorio y se abre en una nueva ventana de edición de nano.

Dado que no existe una función de autoguardado en nano, es importante que guarde su trabajo antes de salir. Para guardar un archivo en nano, utilice el acceso directo del teclado Ctrl + O. Se le pedirá que confirme el nombre del archivo antes de guardarlo. Para salir de nano, utilice el acceso directo del teclado Ctrl + X.

**Nota**: Vim y Emacs también son editores de texto de línea de comandos muy populares.

## Redirección de la salida estándar

Hay una forma adicional de escribir en archivos. Anteriormente, aprendió sobre la entrada estándar y la salida estándar. La **entrada** estándar es la información que recibe el OS a través de la línea de comandos, y **la salida estándar** es la información que devuelve el OS a través del shell.

También ha aprendido sobre la canalización. La **canalización** envía la salida estándar de un comando como entrada estándar a otro comando para su posterior proceso. Utiliza el carácter de tubería (|).

Además de la tubería (|), también puede utilizar los operadores corchete de ángulo recto (>) y doble corchete de ángulo recto (>>) para redirigir la salida estándar.

Cuando se utilizan con echo, los operadores > y >> pueden emplearse para enviar la salida de echo a un archivo especificado en lugar de a la pantalla. La diferencia entre ambos es que > sobrescribe el archivo existente, y >> añade su contenido al final del archivo existente en lugar de sobrescribirlo. El operador > debe utilizarse con cuidado, porque no es fácil recuperar los archivos sobrescritos.

Cuando se encuentre dentro del directorio que contiene el archivo permissions.txt, al introducir echo "last updated date" >> permissions.txt se añade la cadena "última fecha de actualización" al contenido del archivo. Si introduce echo "time" > permissions.txt después de este comando, se sobrescribirá todo el contenido del archivo permissions.txt con la cadena "hora".

**Nota:** Tanto el operador > como el >> crearán un nuevo archivo si no existe ya uno con el nombre especificado.

## Puntos clave

Saber cómo gestionar el sistema de archivos en Linux es una habilidad importante para los analistas de Seguridad. Los comandos útiles para esto incluyen: mkdir, rmdir, touch, rm, mv, y cp. Cuando los analistas de Seguridad necesitan escribir en archivos, pueden utilizar el editor de texto nano, o los operadores > y >>.