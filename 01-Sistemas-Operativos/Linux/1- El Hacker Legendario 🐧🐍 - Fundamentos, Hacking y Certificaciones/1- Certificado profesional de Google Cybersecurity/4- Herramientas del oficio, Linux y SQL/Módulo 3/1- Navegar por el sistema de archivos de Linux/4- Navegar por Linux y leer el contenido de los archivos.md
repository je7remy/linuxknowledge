
En esta lectura, revisará cómo navegar por el sistema de archivos utilizando comandos Linux en Bash. Explorará más a fondo la organización del Estándar de jerarquía del sistema de archivos de Linux, revisará varios comandos comunes de Linux para la navegación y la lectura del contenido de los archivos, y aprenderá un par de comandos nuevos.

## Estándar de jerarquía del sistema de archivos (FHS)

Anteriormente, usted aprendió que el **Estándar de jerarquía del sistema de archivos** (FHS **)** es el componente de Linux que organiza los datos. El FHS es importante porque define cómo se organizan los directorios, el contenido de los directorios y otros tipos de almacenamiento en el sistema operativo.

Este diagrama ilustra la jerarquía de relaciones bajo el FHS:

![El diagrama de flujo comienza con el directorio raíz en la parte superior y se ramifica en varios subdirectorios.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/j0RYvFG7TpGNNfni5SSa0Q_012d7d577b564b4fa3ead21d3f69ebf1_Dvcfull14z4M8iWFX3SE6wnrTefQLql8gas9ICAiKpixcG31SsHLbQmACjE1B4qfpEwTcHfkiD1hxEVGhjyYngw0-fXASC-TSuTgXTBpz_qS4pmXtp-Y7i7giD3GJKCkvajg0PzNebmAf6wDKOBNL-SrMDhBJhsE4yH5Es2_bKRVPC0goRafLVPJs81beg?expiry=1753920000000&hmac=zEoGDJYlt0qqfLOy6qafjl1igl5xiNoTewt_KgmKaXk)

Bajo el FHS, la ubicación de un archivo puede describirse mediante una ruta de archivo. Una **ruta de** archivo es la ubicación de un archivo o directorio. En la ruta de archivo, los distintos niveles de la jerarquía están separados por una barra oblicua (/).

### **Directorio raíz**

El **directorio raíz** es el directorio de más alto nivel en Linux, y siempre se representa con una barra oblicua (/). Todos los subdirectorios se ramifican a partir del directorio raíz. Los subdirectorios pueden continuar ramificándose hasta tantos niveles como sea necesario.

### Directorios FHS estándar

Directamente debajo del directorio raíz, encontrará los directorios FHS estándar. En el diagrama, home, bin, y etc son directorios FHS estándar. He aquí algunos ejemplos de lo que contienen los directorios estándar:

- /home: Cada usuario del sistema tiene su propio directorio personal.
    
- /bin: Este directorio significa "binario" y contiene archivos binarios y otros ejecutables. Los ejecutables son archivos que contienen una serie de órdenes que una computadora debe seguir para ejecutar programas y realizar otras funciones.
    
- /etc: Directorio que almacena los archivos de configuración del sistema.
    
- /tmp: Este Directorio almacena muchos archivos temporales. El directorio /tmp es utilizado habitualmente por los atacantes porque cualquier persona del sistema puede modificar los datos de estos archivos.
    
- /mnt: Este Directorio significa "montar" y almacena soportes, como unidades USB y discos duros.
    

**Consejo profesional**: Puede utilizar el comando man hier para obtener más información sobre el FHS y sus directorios estándar.

### **Subdirectorios específicos de usuario**

Bajo home hay subdirectorios para usuarios específicos. En el diagrama, estos usuarios sonanalyst y analyst2. Cada usuario tiene sus propios subdirectorios personales, como projects, logs o reports.

**Nota:** Cuando la ruta de acceso conduce a un subdirectorio por debajo del directorio personal del usuario, el directorio personal del usuario puede representarse con la tilde (~). Por ejemplo, /home/analyst/logs también puede representarse como ~/logs.

Puede navegar a subdirectorios específicos utilizando sus rutas de archivo absolutas o relativas. La **ruta de archivo absoluta** es la ruta de archivo completa, que parte de la raíz. Por ejemplo, /home/analyst/projects es una ruta de archivo absoluta. La **ruta de** archivo relativa es la ruta de archivo que parte del directorio actual de un usuario.

**Nota:** Las rutas de archivo relativas pueden utilizar un punto (.) para representar el directorio actual, o dos puntos (..) para representar el padre del directorio actual. Un ejemplo de ruta de archivo relativa podría ser ../projects.

## Comandos clave para navegar por el sistema de archivos

Los siguientes comandos de Linux pueden utilizarse para navegar por el sistema de archivos: pwd, ls, y cd.

### **pwd**

El comando pwd imprime en pantalla el directorio de trabajo. En otras palabras, devuelve el Directorio en el que se encuentra actualmente.

La salida le proporciona la ruta de acceso absoluta a este directorio. Por ejemplo, si se encuentra en el directorio home y su nombre de usuario es analyst, al introducir pwd se obtiene /home/analyst.

**Consejo profesional**: Para saber cuál es su nombre de usuario, utilice el comando whoami. El comando whoami devuelve el nombre de usuario del usuario actual. Por ejemplo, si su nombre de usuario es analyst, al introducir whoami se obtiene analyst.

### **ls**

El comando ls muestra los nombres de los archivos y directorios del directorio de trabajo actual. Por ejemplo, en el vídeo, ls devuelve directorios como logs, y un archivo llamado updates.txt.

**Nota**: Si desea devolver el contenido de un directorio que no es su directorio de trabajo actual, puede añadir un argumento después de ls con la ruta de acceso absoluta o relativa al directorio deseado. Por ejemplo, si se encuentra en el directorio /home/analyst pero desea listar el contenido de su subdirectorio projects, puede introducir ls /home/analyst/projects o simplemente ls projects.

### **cd**

El comando cd navega entre directorios. Cuando necesite cambiar de directorio, debe utilizar este comando.

Para navegar a un subdirectorio del directorio actual, puede añadir un argumento después de cd con el nombre del subdirectorio. Por ejemplo, si se encuentra en el directorio /home/analyst y desea navegar a su subdirectorio projects, puede introducir cd projects.

También puede navegar a cualquier directorio específico introduciendo la ruta de archivo absoluta. Por ejemplo, si se encuentra en /home/analyst/projects, al introducir cd /home/analyst/logs cambiará su directorio actual a /home/analyst/logs.

**Consejo profesional**: Puede utilizar la ruta de archivo relativa e introducir cd .. para subir un nivel en la estructura de archivos. Por ejemplo, si el directorio actual es /home/analyst/projects, al introducir cd .. cambiaría su directorio de trabajo a /home/analyst.

## Comandos comunes para leer el contenido de los archivos

Los siguientes comandos de Linux son útiles para leer el contenido de los archivos: cat, head, tail, y less.

### **cat**

El comando cat muestra el contenido de un archivo. Por ejemplo, al introducir cat updates.txt se devuelve todo lo que hay en el archivo updates.txt.

### **head**

El comando head muestra sólo el principio de un archivo, por defecto 10 líneas. El comando head puede ser útil cuando desea conocer el contenido básico de un archivo pero no necesita el contenido completo. Si introduce head updates.txt sólo obtendrá las 10 primeras líneas del archivo updates.txt.

**Consejo profesional**: Si desea cambiar el número de líneas devueltas por head, puede especificar el número de líneas incluyendo -n. Por ejemplo, si sólo desea mostrar las cinco primeras líneas del archivo updates.txt, introduzca head -n 5 updates.txt.

### **tail**

El comando tail hace lo contrario que head. Este comando puede utilizarse para mostrar sólo el final de un archivo, por defecto 10 líneas. Si introduce tail updates.txt obtendrá sólo las 10 últimas líneas del archivo updates.txt.

**Consejo profesional**: Puede utilizar tail para leer la información más reciente de un archivo de registro.

### **menos**

El comando less devuelve el contenido de un archivo página a página. Por ejemplo, si introduce less updates.txt, la ventana del terminal cambiará para mostrar el contenido de updates.txt página a página. Esto le permite avanzar y retroceder fácilmente por el contenido.

Una vez que haya accedido al contenido con el comando less, puede utilizar varios controles de teclado para desplazarse por el archivo:

- Space bar: Avanzar una página
    
- b: Retroceder una página
    
- Down arrow: Avanzar una línea
    
- Up arrow: Retroceder una línea
    
- q: Salir y volver a la ventana de terminal anterior
    

## Puntos clave

Es importante que los analistas de Seguridad sean capaces de navegar por Linux y por el sistema de archivos del FHS. Algunos comandos clave para navegar por el sistema de archivos son pwd, ls y cd. Leer el contenido de los archivos también es una habilidad importante en la profesión de Seguridad. Esto puede hacerse con comandos como cat, head, tail, y less.
