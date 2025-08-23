
## Navegar el sistema de archivos
Los siguientes comandos de Linux son útiles para navegar por el sistema de archivos.

### `cd`
Navega entre directorios

- `cd reports`  
  Navega desde el directorio de trabajo actual a su subdirectorio `reports`
- `cd /home/analyst/reports`  
  Navega al directorio `reports`; se requiere la ruta completa cuando `reports` no es un subdirectorio del directorio de trabajo actual
- `cd ..`  
  Navega al directorio que está un nivel por encima del directorio de trabajo actual

### `ls`
Muestra los nombres de archivos y directorios

- `ls`  
  Muestra los nombres de archivos y directorios en el directorio de trabajo actual
- `ls /home/analyst/reports`  
  Muestra los nombres de archivos y directorios en el directorio `reports`; es necesario proporcionar un argumento que especifique la ruta a un directorio para mostrar el contenido de un directorio que no sea el directorio de trabajo actual del usuario
- `ls -a`  
  Muestra archivos ocultos al mostrar los nombres de archivos y directorios dentro del directorio de trabajo actual
- `ls -l`  
  Muestra permisos de archivos y directorios en el directorio de trabajo actual; también muestra otra información adicional, incluido el nombre del propietario, grupo, tamaño del archivo y la hora de la última modificación
- `ls -la`  
  Muestra permisos de archivos y directorios en el directorio de trabajo actual, incluidos archivos ocultos; también muestra otra información adicional, incluido el nombre del propietario, grupo, tamaño del archivo y la hora de la última modificación

### `pwd`
Imprime el directorio de trabajo actual en pantalla

- `pwd`  
  Imprime el directorio de trabajo actual en pantalla, por ejemplo `/home/analyst`

### `whoami`
Devuelve el nombre de usuario del usuario actual

- `whoami`  
  Devuelve el nombre de usuario del usuario actual, como `analyst` o `fgarcia`

## Leer archivos
Los siguientes comandos de Linux son útiles para leer archivos.

### `cat`
Muestra el contenido de un archivo

- `cat updates.txt`  
  Muestra el contenido del archivo `updates.txt`

### `head`
Muestra solo el principio de un archivo, por defecto 10 líneas

- `head updates.txt`  
  Muestra solo las primeras 10 líneas del archivo `updates.txt`
- `head -n 5 updates.txt`  
  Muestra solo las primeras cinco líneas del archivo `updates.txt`; la opción `-n` permite a los usuarios especificar el número de líneas a devolver

### `less`
Devuelve el contenido de un archivo una página a la vez

- `less updates.txt`  
  Devuelve el contenido de `updates.txt` una página a la vez; el comando `less` cambia la ventana de terminal a una pantalla que permite a los usuarios moverse fácilmente hacia adelante y hacia atrás a través del contenido

### `tail`
Muestra solo el final de un archivo, por defecto 10 líneas

- `tail updates.txt`  
  Muestra solo las últimas 10 líneas del archivo `updates.txt`
- `tail -n 5 updates.txt`  
  Devuelve solo las últimas cinco líneas del archivo `updates.txt`; la opción `-n` permite a los usuarios especificar el número de líneas a devolver

## Gestionar el sistema de archivos
Los siguientes comandos de Linux son útiles para gestionar el sistema de archivos.

### `cp`
Copia un archivo o directorio a una nueva ubicación; el archivo no se elimina de la ubicación anterior

- `cp permissions.txt /home/analyst/logs`  
  Copia el archivo `permissions.txt` del directorio de trabajo actual del usuario al directorio `logs`

### `mkdir`
Crea un nuevo directorio

- `mkdir network`  
  Crea un nuevo directorio llamado `network` en el directorio de trabajo actual del usuario
- `mkdir /home/analyst/logs network`  
  Crea un nuevo directorio llamado `network` en el directorio `logs`; se requiere la ruta completa cuando `logs` no es un subdirectorio del directorio actual

### `mv`
Mueve un archivo o directorio a una nueva ubicación; el archivo también se elimina de la ubicación anterior

- `mv permissions.txt /home/analyst/logs`  
  Mueve el archivo `permissions.txt` del directorio de trabajo actual del usuario al directorio `logs`
- `mv permissions.txt perm.txt`  
  Mueve el archivo `permissions.txt` del directorio de trabajo actual del usuario al nuevo nombre de archivo `perm.txt` en el directorio de trabajo actual del usuario; esto resulta en renombrar el archivo `permissions.txt` como `perm.txt`

### `nano`
Abre o crea un archivo en el editor de archivos de línea de comandos nano

- `nano permissions.txt`  
  Abre un archivo existente `permissions.txt` en el editor de archivos nano, o crea el archivo `permissions.txt` en el editor de archivos nano si aún no existe en el directorio de trabajo actual

### `rm`
Elimina o borra un archivo

- `rm permissions.txt`  
  Elimina el archivo `permissions.txt` del directorio de trabajo actual del usuario
- `rm home/analyst/reports/permissions.txt`  
  Elimina el archivo `permissions.txt` del directorio `reports`; se requiere la ruta completa si el directorio de trabajo actual del usuario no es `reports`

### `rmdir`
Elimina o borra un directorio; solo elimina directorios si están vacíos

- `rmdir network`  
  Elimina el subdirectorio `network` vacío del directorio de trabajo actual del usuario del sistema de archivos
- `rmdir /home/analyst/logs/network`  
  Elimina el directorio `network` vacío del sistema de archivos; se requiere la ruta completa cuando `network` no es un subdirectorio del directorio actual

### `touch`
Crea un nuevo archivo

- `touch permissions.txt`  
  Crea un nuevo archivo llamado `permissions.txt` en el directorio de trabajo actual del usuario
- `touch /home/analyst/reports/permissions.txt`  
  Crea un nuevo archivo llamado `permissions.txt` en el directorio `reports`; se requiere la ruta completa si el usuario quiere crear `permissions.txt` en cualquier directorio que no sea el directorio de trabajo actual

## Filtrar contenido
Los siguientes comandos de Linux son útiles para filtrar contenido.

### `find`
Busca directorios y archivos que cumplan criterios específicos

- `find /home/analyst/projects`  
  Busca todos los archivos comenzando desde el directorio `projects`
- `find /home/analyst/projects -name "*log*"`  
  Busca todos los archivos en el directorio `projects` que contengan la palabra `log` en el nombre del archivo; la opción `-name` busca una cadena especificada y distingue entre mayúsculas y minúsculas; el comodín `*` representa cero o más caracteres desconocidos
- `find /home/analyst/projects -iname "*log*"`  
  Busca todos los archivos en el directorio `projects` que contengan la palabra `log` en el nombre del archivo; la opción `-iname` busca una cadena especificada y no distingue entre mayúsculas y minúsculas; el comodín `*` representa cero o más caracteres desconocidos
- `find /home/analyst/projects -mtime -3`  
  Busca todos los archivos en el directorio `projects` que han sido modificados en los últimos tres días; la opción `-mtime` basa su búsqueda en archivos o directorios que fueron modificados por días
- `find /home/analyst/projects -mmin -15`  
  Busca todos los archivos en el directorio `projects` que han sido modificados en los últimos 15 minutos; la opción `-mmin` basa su búsqueda en archivos o directorios que fueron modificados por minutos

### `grep`
Busca en un archivo especificado y devuelve todas las líneas del archivo que contienen una cadena especificada

- `grep OS updates.txt`  
  Busca en el archivo `updates.txt` y devuelve todas las líneas que contienen la cadena `OS`

### `|` (tubería)
Envía la salida estándar de un comando como entrada estándar a otro comando para su posterior procesamiento; se accede mediante el carácter de tubería (`|`)

- `ls /home/analyst/reports | grep users`  
  Redirige la salida estándar de `ls /home/analyst/reports` para que sea la entrada estándar para el comando `grep users`, lo que significa que `grep users` identifica archivos y subdirectorios en el directorio `/home/analyst/reports` que contienen la cadena `users` dentro de su nombre de archivo

## Gestionar usuarios y sus permisos
Los siguientes comandos de Linux son útiles para gestionar permisos de usuarios. (También revisar los subapartados de `ls -l` y `ls -la` en la entrada `ls` de la sección Navegar el sistema de archivos.)

### `chmod`
Cambia permisos en archivos y directorios

- `chmod u+rwx,g+rwx,o+rwx login_sessions.txt`  
  Cambia permisos de usuario (u), grupo (g) y otros (o) para agregar (+) permisos de lectura (r), escritura (w) y ejecución (x) para el archivo `login_sessions.txt`
- `chmod g-rw bonuses.txt`  
  Cambia los permisos del grupo (g) para eliminar (-) permisos de lectura (r) y escritura (w) para el archivo `bonuses.txt`
- `chmod u=r,g=r,o=r login_sessions.txt`  
  Cambia permisos de usuario (u), grupo (g) y otros (o) para asignar (=) permisos de lectura (r) para el archivo `login_sessions.txt`

### `chown`
Cambia la propiedad de un archivo o directorio; se usa con `sudo`

- `sudo chown fgarcia access.txt`  
  Cambia el propietario usuario del archivo `access.txt` a `fgarcia`
- `sudo chown :security access.txt`  
  Cambia el propietario grupo de `access.txt` a `security`; se debe ingresar dos puntos (`:`) antes del nombre del grupo

### `groupdel`
Elimina un grupo del sistema; se usa con `sudo`

- `sudo groupdel accounting`  
  Elimina `accounting` como grupo

### `sudo`
Otorga temporalmente permisos elevados a usuarios específicos; los usuarios deben estar en un archivo sudoers para tener acceso a `sudo`

- `sudo useradd fgarcia`  
  Otorga permisos elevados al usuario que ejecuta este comando para que pueda usar el comando `useradd` para agregar `fgarcia` como nuevo usuario al sistema

### `useradd`
Agrega un usuario al sistema; se usa con `sudo`

- `sudo useradd fgarcia`  
  Agrega `fgarcia` como nuevo usuario al sistema
- `sudo useradd -g security fgarcia`  
  Agrega `fgarcia` como nuevo usuario y usa la opción `-g` para establecer su grupo principal como `security`
- `sudo useradd -G finance,admin fgarcia`  
  Agrega `fgarcia` como nuevo usuario y usa la opción `-G` para agregarlos a los grupos suplementarios de `finance` y `admin`

### `userdel`
Elimina un usuario del sistema; se usa con `sudo`

- `sudo userdel fgarcia`  
  Elimina `fgarcia` como usuario
- `sudo userdel -r fgarcia`  
  Elimina `fgarcia` como usuario y elimina todos los archivos en su directorio home

### `usermod`
Modifica cuentas de usuario existentes; se usa con `sudo`

- `sudo usermod -g executive fgarcia`  
  Usa la opción `-g` para cambiar el grupo principal del usuario existente `fgarcia` al grupo `executive`
- `sudo usermod -G accounting fgarcia`  
  Usa la opción `-G` para reemplazar cualquier grupo suplementario en el que esté el usuario existente `fgarcia` con el grupo suplementario `accounting`; elimina todos los otros grupos suplementarios en los que esté `fgarcia`
- `sudo usermod -a -G marketing fgarcia`  
  Usa las opciones `-a -G` para agregar el usuario existente `fgarcia` al grupo suplementario `marketing`; no elimina a `fgarcia` de otros grupos suplementarios
- `sudo usermod -d /home/garcia_f fgarcia`  
  Usa la opción `-d` para cambiar el directorio home del usuario existente `fgarcia` a `/home/garcia_f`
- `sudo usermod -L fgarcia`  
  Usa la opción `-L` para bloquear la cuenta del usuario existente `fgarcia` para que no pueda iniciar sesión
- `sudo usermod -l garcia_f fgarcia`  
  Usa la opción `-l` para cambiar el nombre de inicio de sesión del usuario existente `fgarcia` a `garcia_f`

## Obtener ayuda en Linux
Los siguientes comandos de Linux son útiles para obtener ayuda en Linux.

### `apropos`
Busca en las descripciones de las páginas del manual una cadena especificada

- `apropos password`  
  Devuelve las páginas de manual de comandos que contienen la palabra clave `password`
- `apropos -a graph editor`  
  Devuelve las páginas de manual de comandos que contienen ambas palabras clave `graph` y `editor`; la opción `-a` especifica devolver solo comandos que contengan todas las cadenas especificadas

### `man`
Muestra información sobre otros comandos y cómo funcionan; la salida se llama "página man", abreviatura de "página de manual"

- `man chown`  
  Muestra información detallada sobre `chown` y cómo funciona

### `whatis`
Muestra una descripción de un comando en una sola línea

- `whatis nano`  
  Muestra la descripción de `nano` en una sola línea