
Anteriormente, usted aprendió acerca de las distribuciones de Linux y que diferentes distribuciones derivan de diferentes fuentes, como Debian o la distribución Red Hat Enterprise Linux. También se le presentó a los administradores de paquetes, y aprendió que las aplicaciones de Linux se distribuyen comúnmente a través de administradores de paquetes. En esta lectura, aplicará estos conocimientos para aprender más sobre los administradores de paquetes.

## Introducción a los administradores de paquetes

Un **Paquete** es una pieza de software que puede combinarse con otros paquetes para formar una aplicación. Algunos paquetes pueden ser lo suficientemente grandes como para formar aplicaciones por sí solos.

Los paquetes contienen los archivos necesarios para instalar una aplicación. Estos archivos incluyen dependencias, que son archivos suplementarios utilizados para ejecutar una aplicación.

Los administradores de paquetes pueden ayudar a resolver cualquier problema con las dependencias y realizar otras tareas de gestión. Un **administrador de paquetes** es una herramienta que ayuda a los usuarios a instalar, gestionar y eliminar paquetes o aplicaciones. Linux utiliza varios administradores de paquetes.

**Nota:** Es importante utilizar la versión más reciente de un Paquete siempre que sea posible. La versión más reciente tiene las correcciones de errores y los parches de seguridad más actualizados. Estos ayudan a mantener su sistema más seguro.

## Tipos de administradores de paquetes

Muchas distribuciones de Linux de uso común derivan de la misma distribución madre. Por ejemplo, KALI LINUX, Ubuntu y Parrot provienen de Debian. CentOS proviene de Red Hat.

Estos conocimientos son útiles a la hora de instalar aplicaciones porque determinados administradores de paquetes funcionan con determinadas distribuciones. Por ejemplo, el administrador de paquetes de Red Hat (RPM) se puede utilizar para las distribuciones de Linux derivadas de Red Hat, y los administradores de paquetes como dpkg se pueden utilizar para las distribuciones de Linux derivadas de Debian.

Los distintos administradores de paquetes suelen utilizar diferentes extensiones de archivo. Por ejemplo, el administrador de paquetes de Red Hat (RPM) tiene archivos que utilizan la extensión de archivo .rpm, como Package-Version-Release_Architecture.rpm. Los administradores de paquetes para distribuciones Linux derivadas de Debian, como dpkg, tienen archivos que utilizan la extensión de archivo .deb, como Package_Version-Release_Architecture.deb.

## Herramientas de gestión de paquetes

Además de los administradores de paquetes como RPM y dpkg, también existen herramientas de gestión de paquetes que le permiten trabajar fácilmente con los paquetes a través del shell. Las herramientas de gestión de paquetes se utilizan a veces en lugar de los administradores de paquetes porque permiten a los usuarios realizar más fácilmente tareas básicas, como instalar un nuevo paquete. Dos herramientas notables son la Herramienta Avanzada de Paquetes (APT) y Yellowdog Updater Modified (YUM).

### **Herramienta avanzada de paquetes (APT)**

APT es una herramienta que se utiliza con las distribuciones derivadas de Debian. Se ejecuta desde la interfaz de línea de comandos para gestionar, buscar e instalar paquetes.

### **Yellowdog Updater Modificado (YUM)**

YUM es una herramienta utilizada con las distribuciones derivadas de Red Hat. Se ejecuta desde la interfaz de línea de comandos para gestionar, buscar e instalar paquetes. YUM trabaja con archivos .rpm.

## Puntos clave

Un paquete es una pieza de software que puede combinarse con otros paquetes para formar una aplicación. Los paquetes pueden gestionarse mediante un administrador de paquetes. Existen múltiples administradores de paquetes y herramientas de gestión de paquetes para diferentes distribuciones de Linux. Las herramientas de administrador de paquetes permiten a los usuarios trabajar fácilmente con los paquetes a través del shell. Las distribuciones de Linux derivadas de Debian utilizan administradores de paquetes como dpkg, así como herramientas de gestión de paquetes como Advanced Paquete Tool (APT). Las distribuciones derivadas de Red Hat utilizan el administrador de paquetes de Red Hat (RPM) o herramientas como Yellowdog Updater Modified (YUM).