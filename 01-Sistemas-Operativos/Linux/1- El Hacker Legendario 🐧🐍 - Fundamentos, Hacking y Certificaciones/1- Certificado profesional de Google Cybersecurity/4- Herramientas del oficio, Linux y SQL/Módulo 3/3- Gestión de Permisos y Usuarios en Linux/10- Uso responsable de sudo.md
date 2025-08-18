
Anteriormente, usted exploró la autorización, autenticación y comandos de Linux con sudo, useradd y userdel. El comando sudo es importante para los analistas de Seguridad porque permite a los usuarios tener permisos elevados sin poner en riesgo el sistema ejecutando comandos como usuario raíz. Continuará explorando la autorización, autenticación y comandos de Linux en esta lectura y aprenderá dos comandos más que pueden utilizarse con sudo: usermod y chown.

## Uso responsable de sudo

Para gestionar la autorización y autenticación, necesita ser un **usuario raíz,** o un usuario con privilegios elevados para modificar el sistema. Al usuario raíz también se le puede llamar "superusuario" Usted se convierte en usuario raíz iniciando sesión como usuario root. Sin embargo, ejecutar comandos como usuario raíz no es recomendable en Linux porque puede crear Riesgos de Seguridad si actores maliciosos comprometen esa cuenta. También es fácil cometer errores irreversibles, y el sistema no puede rastrear quién ejecutó un comando. Por estas razones, en lugar de registrarse como usuario raíz, se recomienda utilizar sudo en Linux cuando necesite privilegios elevados.

El comando sudo otorga temporalmente permisos elevados a usuarios específicos. El nombre de este comando proviene de "superusuario do" Los usuarios deben tener acceso en un archivo de configuración para utilizar sudo. Este archivo se llama "archivo sudoers" Aunque utilizar sudo es preferible a iniciar sesión como usuario raíz, es importante ser consciente de que los usuarios con permisos elevados para utilizar sudo podrían correr más riesgos en caso de ataque.

Puede comparar esto a un hotel con una llave maestra. La llave maestra puede utilizarse para acceder a cualquier habitación del hotel. Hay algunos trabajadores del hotel que necesitan esta clave para realizar su trabajo. Por ejemplo, para limpiar todas las habitaciones, el conserje escanearía su tarjeta de identificación y luego utilizaría esta llave maestra. Sin embargo, si alguien ajeno a la red del hotel obtuviera acceso a la tarjeta de identificación y a la llave maestra del conserje, podría acceder a cualquier habitación del hotel. En este ejemplo, el conserje con la clave maestra representa a un usuario que utiliza sudo para obtener privilegios elevados. Debido a los peligros de sudo, sólo los usuarios que realmente necesiten utilizarlo deberían tener estos permisos.

Además, incluso si necesita acceso a sudo, debe tener cuidado de utilizarlo sólo con los comandos que necesite y nada más. Ejecutar comandos con sudo permite a los usuarios saltarse los típicos Controles de seguridad que existen para impedir el acceso elevado a un atacante.

**Nota**: Tenga cuidado con sudo si copia comandos de una fuente en línea. Es importante que no utilice sudo accidentalmente.

## Autenticación y autorización con sudo

Puede utilizar sudo con muchas tareas de gestión de autenticación y autorización. Como recordatorio, **la autenticación** es el proceso de verificar quién es alguien, y **la autorización** es el concepto de conceder acceso a recursos específicos en un sistema. Algunos de los comandos clave utilizados para estas tareas son los siguientes:

### **useradd**

El comando useradd añade un usuario al sistema. Para añadir un usuario con el nombre de usuario de fgarcia con sudo, introduzca sudo useradd fgarcia. Existen opciones adicionales que puede utilizar con useradd:

- -g: Establece el grupo por defecto del usuario, también llamado su grupo primario
    
- -G: Añade al usuario a grupos adicionales, también llamados grupos suplementarios o secundarios
    

Para utilizar la opción -g, el grupo primario debe especificarse después de -g. Por ejemplo, al introducir sudo useradd -g security fgarcia se añade fgarcia como nuevo usuario y se asigna que su grupo primario sea security.

Para utilizar la opción -G, el grupo suplementario debe pasarse al comando después de -G. Puede añadir más de un grupo suplementario a la vez con la opción -G. Al introducir sudo useradd -G finance,admin fgarcia se añade fgarcia como nuevo usuario y se añade a los grupos existentes finance y admin.

### **usermod**

El comando usermod modifica las cuentas de usuario existentes. Las mismas opciones -g y -G del comando useradd pueden utilizarse con usermod si ya existe un usuario.

Para cambiar el grupo primario de un usuario existente, necesita la opción -g. Por ejemplo, si introduce sudo usermod -g executive fgarcia cambiará el grupo primario de fgarciapor el grupo executive.

Para añadir un grupo suplementario para un usuario existente, necesita la opción -G. También necesita la opción -a, que añade el usuario a un grupo existente y sólo se utiliza con la opción -G. Por ejemplo, introduciendo sudo usermod -a -G marketing fgarcia añadiría el usuario existente fgarcia al grupo suplementario marketing.

**Nota:** Al cambiar el grupo suplementario de un usuario existente, si no incluye la opción -a, -G sustituirá cualquier grupo suplementario existente por los grupos especificados después de usermod. El uso de -a con -G garantiza que se añadan los nuevos grupos pero que no se sustituyan los grupos existentes.

Existen otras opciones que puede utilizar con usermod para especificar cómo desea modificar el usuario, entre las que se incluyen:

- -d: Cambia el Directorio personal del usuario.
    
- -l: Cambia el nombre de usuario.
    
- -L: Bloquea la cuenta para que el usuario no pueda registrarse.
    

La opción siempre va después del comando usermod. Por ejemplo, para cambiar el directorio principal de fgarciaa /home/garcia_f, introduzca sudo usermod -d /home/garcia_f fgarcia. La opción -d sigue directamente al comando usermod antes de los otros dos argumentos necesarios.

### **userdel**

El comando userdel borra un usuario del sistema. Por ejemplo, si introduce sudo userdel fgarcia borrará fgarcia como usuario. Tenga cuidado antes de borrar un usuario utilizando este Comando.

El comando userdel no borra los archivos del directorio personal del usuario a menos que utilice la opción -r. Introducir sudo userdel -r fgarcia eliminaría fgarcia como usuario y borraría todos los archivos de su directorio personal. Antes de borrar cualquier archivo de usuario, debe asegurarse de que tiene copias de seguridad por si las necesita más adelante.

**Nota**: En lugar de borrar al usuario, podría considerar desactivar su cuenta con usermod -L. Esto evita que el usuario se registre mientras le sigue dando acceso a su cuenta y a los permisos asociados. Por ejemplo, si un usuario abandonara una organización, esta opción le permitiría identificar sobre qué archivos tiene la propiedad, de modo que podría mover esta propiedad a otros usuarios.

### **chown**

El comando chown cambia la propiedad de un archivo o directorio. Puede utilizar chown para cambiar la propiedad del usuario o del grupo. Para cambiar el usuario propietario del archivo access.txt a fgarcia, introduzca sudo chown fgarcia access.txt. Para cambiar el propietario de grupo de access.txt a security, introduzca sudo chown :security access.txt. Debe introducir dos puntos (:) antes de security para designarlo como nombre de grupo.

De forma similar a useradd, usermod, y userdel, existen opciones adicionales que pueden utilizarse con chown.

## Claves

La autenticación es el proceso por el que un usuario verifica su identidad, y la autorización es el proceso por el que se determina a qué tiene acceso. Puede utilizar el comando sudo para ejecutar temporalmente comandos con privilegios elevados para completar las tareas de gestión de autenticación y autorización. En concreto, useradd, userdel, usermod , y chown pueden utilizarse para gestionar usuarios y la propiedad de archivos.