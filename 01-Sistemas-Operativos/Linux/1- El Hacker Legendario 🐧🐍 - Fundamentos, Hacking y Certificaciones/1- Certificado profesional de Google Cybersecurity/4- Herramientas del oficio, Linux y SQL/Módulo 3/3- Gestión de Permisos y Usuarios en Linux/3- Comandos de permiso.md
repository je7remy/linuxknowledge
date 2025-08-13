
Anteriormente, usted exploró los permisos de archivo y los comandos que puede utilizar para mostrarlos y cambiarlos. En esta lectura, repasará estos conceptos y también se centrará en un ejemplo de cómo estos comandos funcionan juntos al poner en práctica el principio de privilegio mínimo.

## Permisos de lectura

En Linux, los permisos se representan con una cadena de 10 caracteres. Los permisos incluyen:

- **leer**: para archivos, esta es la capacidad de leer el contenido del archivo; para directorios, esta es la capacidad de leer todo el contenido en el directorio incluyendo tanto archivos como subdirectorios
    
- **escribir**: para archivos, esta es la capacidad de hacer modificaciones en el contenido del archivo; para directorios, esta es la capacidad de crear nuevos archivos en el directorio
    
- **ejecutar**: para los archivos, es la capacidad de ejecutar el archivo si se trata de un programa; para los directorios, es la capacidad de entrar en el directorio y acceder a sus archivos
    

Estos permisos se otorgan a estos tipos de propietarios:

- **usuario**: el propietario del archivo
    
- **grupo**: un grupo mayor del que forma parte el propietario
    
- **otro**: todos los demás usuarios del sistema
    

Cada carácter de la cadena de 10 caracteres transmite información diferente sobre estos permisos. La siguiente tabla describe el propósito de cada carácter:

|**Carácter**|**Ejemplo**|**Significado**|
|---|---|---|
|1|**drwxrwxrwx**|tipo de archivo<br><br>- d para un directorio<br>    <br>- - para un archivo regular|
|2º|**drwxrwxrwx**|permisos de lectura para el usuario<br><br>- r si el usuario tiene permisos de lectura<br>    <br>- - si el usuario carece de permisos de lectura|
|3º|**drwxrwxrwx**|permisos de escritura para el usuario<br><br>- w si el usuario tiene permisos de escritura<br>    <br>- - si el usuario carece de permisos de escritura|
|4º|**drwxrwxrwx**|permisos de ejecución para el usuario<br><br>- x si el usuario tiene permisos de ejecución<br>    <br>- - si el usuario carece de permisos de ejecución|
|5º|**drwxrwxrwx**|permisos de lectura para el grupo<br><br>- r si el grupo tiene permisos de lectura<br>    <br>- - si el grupo carece de permisos de lectura|
|6º|**drwxrwxrwx**|permisos de escritura para el grupo<br><br>- w si el grupo tiene permisos de escritura<br>    <br>- - si el grupo carece de permisos de escritura|
|7º|**drwxrwxrwx**|permisos de ejecución para el grupo<br><br>- x si el grupo tiene permisos de ejecución<br>    <br>- - si el grupo carece de permisos de ejecución|
|8vo|**drwxrwxrwx**|permisos de lectura para otros<br><br>- r si el otro tipo de propietario tiene permisos de lectura<br>    <br>- - si el otro tipo de propietario carece de permisos de lectura|
|9º|**drwxrwxrwx**|permisos de escritura para otro<br><br>- w si el otro tipo de propietario tiene permisos de escritura<br>    <br>- - si el otro tipo de propietario carece de permisos de escritura|
|10º|**drwxrwxrwx**|permisos de ejecución para otro<br><br>- x si el otro tipo de propietario tiene permisos de ejecución<br>    <br>- - si el otro tipo de propietario carece de permisos de ejecución|

## Exploración de los permisos existentes

Puede utilizar el comando ls para investigar quién tiene permisos sobre archivos y directorios. Anteriormente, aprendió que ls muestra los nombres de los archivos en los directorios en el directorio de trabajo actual.

Existen opciones adicionales que puede añadir al comando ls para que su comando sea más específico. Algunas de estas opciones proporcionan detalles sobre los permisos. He aquí algunas opciones de ls importantes para los analistas de Seguridad:

- ls -a: Muestra los archivos ocultos. Los archivos ocultos comienzan con un punto (.) al principio.
    
- ls -l: Muestra los permisos de archivos y directorios. También muestra otra información adicional, como el nombre del propietario, el grupo, el tamaño del archivo y la hora de la última modificación.
    
- ls -la: Muestra los permisos de archivos y directorios, incluidos los archivos ocultos. Es una combinación de las otras dos opciones.
    

## Cambio de permisos

El **principio de privilegio mínimo** es el concepto de conceder sólo el acceso y la autorización mínimos necesarios para completar una tarea o función. En otras palabras, los usuarios no deben tener privilegios que vayan más allá de lo necesario. No seguir el principio de privilegio mínimo puede crear riesgos de Seguridad.

El comando chmod puede ayudarle a gestionar esta autorización. El comando chmod cambia los permisos de archivos y directorios.

### **Uso de chmod**

El comando chmod requiere dos argumentos. El primer argumento indica cómo cambiar los permisos, y el segundo argumento indica el archivo o directorio para el que desea cambiar los permisos. Por ejemplo, el siguiente comando añadiría todos los permisos a login_sessions.txt:

chmod u+rwx,g+rwx,o+rwx login_sessions.txt

Si quisiera quitar todos los permisos, podría utilizar

chmod u-rwx,g-rwx,o-rwx login_sessions.txt

Otra forma de asignar estos permisos es utilizar el signo igual (=) en este primer argumento. El uso de = con chmod establece, o asigna, los permisos exactamente como se especifican. Por ejemplo, el siguiente comando establecería permisos de lectura para login_sessions.txt para usuario, grupo y otros:

chmod u=r,g=r,o=r login_sessions.txt

Este Comando sobrescribe los permisos existentes. Por ejemplo, si el usuario tenía previamente permisos de escritura, estos permisos de escritura se eliminan después de que usted especifique sólo permisos de lectura con =.

La siguiente tabla repasa cómo se utiliza cada carácter dentro del primer argumento de chmod:

|**Carácter**|**Descripción**|
|---|---|
|u|indica que se realizarán cambios en los permisos de usuario|
|g|indica que se realizarán cambios en los permisos de grupo|
|o|indica que se realizarán cambios en otros permisos|
|+|añade permisos al usuario, grupo u otro|
|-|elimina permisos del usuario, grupo u otro|
|=|asigna permisos al usuario, grupo u otro|

**Nota:** Cuando hay cambios de permisos a más de un tipo de propietario, se necesitan comas para separar los cambios para cada tipo de propietario. No debe añadir espacios después de esas comas.

### **El principio de privilegio mínimo en acción**

COMO analista de Seguridad, puede encontrarse con una situación como la siguiente: Hay un archivo llamado bonuses.txt dentro de un directorio de compensación. El propietario de este archivo es un miembro del departamento de Recursos Humanos con el nombre de usuario hrrep1. Se ha decidido que hrrep1 necesita acceder a este archivo. Pero, como este archivo contiene información confidencial, nadie más del grupo hr necesita acceso.

Usted ejecuta ls -l para comprobar los permisos de los archivos en el directorio de compensación y descubre que los permisos para bonuses.txt son -rw-rw----. El tipo de propietario del grupo tiene permisos de lectura y escritura que no se ajustan al principio de privilegio mínimo.

Para remediar la situación, usted introduce chmod g-rw bonuses.txt. Ahora, sólo el usuario que necesita acceder a este archivo para llevar a cabo sus responsabilidades laborales puede acceder a este archivo.

## Puntos clave

Gestionar los permisos de directorio y de archivo puede formar parte de su trabajo como analista de Seguridad. El uso de ls con las opciones -l y -la le permite investigar los permisos de directorio y archivo. El uso de chmod le permite cambiar los permisos de usuario y asegurarse de que están alineados con el principio de privilegio mínimo.