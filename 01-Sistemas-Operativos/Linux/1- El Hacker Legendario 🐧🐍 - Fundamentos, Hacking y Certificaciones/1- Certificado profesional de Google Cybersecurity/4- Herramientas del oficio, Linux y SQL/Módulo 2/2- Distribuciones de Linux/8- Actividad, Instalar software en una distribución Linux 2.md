# Actividad: Instalar software en una distribución de Linux

## Resumen de la actividad

En esta actividad de laboratorio, usará Advanced Package Tool (APT) e instalará y desinstalará aplicaciones en un shell de Linux Bash.`sudo`

Si bien la instalación de aplicaciones Linux puede ser una tarea compleja, el administrador de paquetes APT administra la mayor parte de esta complejidad por usted y le permite administrar las aplicaciones de manera rápida y confiable en un entorno Linux.

Usarás Suricata y tcpdump como ejemplo. Estas son aplicaciones de seguridad de red que se pueden utilizar para capturar y analizar el tráfico de red.

La máquina virtual a la que accede en este laboratorio tiene una distribución de Linux basada en Debian en ejecución y que funciona con el administrador de paquetes APT. El uso de una máquina virtual evita daños a un sistema en caso de que sus herramientas se utilicen incorrectamente. También le brinda la capacidad de volver a un estado anterior.

Como analista de seguridad, es probable que necesite saber cómo instalar y administrar aplicaciones en un sistema operativo Linux. ¡En esta actividad de laboratorio, aprenderás cómo hacer exactamente eso!

## Escenario

Su función como analista de seguridad requiere que tenga instaladas las aplicaciones de seguridad de red Suricata y tcpdump en el sistema.

En este escenario, debe instalar, desinstalar y volver a instalar estas aplicaciones en el shell de Linux Bash. También debe confirmar que los ha instalado correctamente.

Así es como lo harás: **Primero**, confirmarás que APT está instalado en tu shell Linux Bash. **A continuación**, usará APT para instalar la aplicación Suricata y confirmar que está instalada. **Luego**, desinstalará la aplicación Suricata y confirmará esto también. **A continuación**, instalará la aplicación tcpdump y enumerará las aplicaciones instaladas actualmente. **Finalmente**, volverá a instalar la aplicación Suricata y confirmará que ambas aplicaciones están instaladas.

Bien, ¡es hora de aprender a instalar algunas aplicaciones!

_**Nota:** El laboratorio comienza con su cuenta de usuario, llamada `analista`, que ya ha iniciado sesión en el shell de Bash. Esto significa que puede comenzar con las tareas tan pronto como haga clic en el botón **Iniciar laboratorio**._

**Renuncia:** Para un rendimiento y compatibilidad óptimos, se recomienda utilizar los navegadores **Google Chrome** o **Mozilla Firefox** al acceder a los laboratorios.

## Inicie su laboratorio

Deberá comenzar el laboratorio antes de poder acceder a los materiales. Para hacer esto, haga clic en el botón verde "Iniciar laboratorio" en la parte superior de la pantalla.

![Se muestra el botón Inicio de laboratorio.](https://cdn.qwiklabs.com/m8bGh8IYyYTzRYAJCj2t0DqCOLRDVcr%2BFy5bwhKxwvU%3D)

Después de hacer clic en el botón **Iniciar laboratorio**, verá un shell, donde realizará más pasos en el laboratorio. Deberías tener un shell como este:

![Se muestra la Terminal de Linux.](https://cdn.qwiklabs.com/fSLMzp%2BzoZ1B5rg%2FrrvIdOBQf0bpnzgi6y8IYLeMBUo%3D)

Cuando haya completado todas las tareas, consulte la sección Finalizar el laboratorio que sigue a las tareas para obtener información sobre cómo finalizar el laboratorio.

## Tarea 1. Asegúrese de que APT esté instalado

Primero, verificará que la aplicación APT esté instalada para que pueda usarla para administrar aplicaciones. La forma más sencilla de hacer esto es ejecutar el comando apt en el shell de Bash y verificar la respuesta.

El shell de Bash es el intérprete de línea de comandos actualmente abierto en el lado izquierdo de la pantalla. Usará el shell de Bash escribiendo comandos después del mensaje. El símbolo del sistema se representa mediante un signo de dólar ($) seguido del cursor de entrada.

- Confirme que el administrador de paquetes APT esté instalado en su entorno Linux. Para ello, escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`apt`

Cuando se instala, muestra información de uso básica cuando se ejecuta. Esto incluye la información de la versión y una descripción de la herramienta:`apt`

apt 1.8.2.3 (amd64)
Usage: apt [options] command

apt is a commandline package manager and provides commands for
searching and managing as well as querying information about packages.
It provides the same functionality as the specialized APT tools,
like apt-get and apt-cache, but enables options more suitable for
interactive use by default.
...

APT ya está instalado de forma predeterminada en el shell de Linux Bash en este laboratorio porque este es un sistema basado en Debian. APT es también el gestor de paquetes recomendado para Debian. Si está utilizando otra distribución, es posible que esté disponible un administrador de paquetes diferente, como YUM, en su lugar.

Haga clic en **Comprobar mi progreso** para comprobar que ha completado esta tarea correctamente.

Asegúrese de que APT esté instalado

## Tarea 2. Instalar y desinstalar la aplicación Suricata

En esta tarea, debe instalar Suricata, una herramienta de análisis de red utilizada para la detección de intrusos, y verificar que se instaló correctamente. Luego, desinstalará la aplicación.

1. Utilice el administrador de paquetes APT para instalar la aplicación Suricata.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`sudo apt install suricata`

_**Nota:** Los comandos `apt install` y `apt remove` deben tener el prefijo `sudo` command, ya que se requieren privilegios elevados para instalar y desinstalar software en Linux._

_La aplicación Suricata puede tardar unos minutos en instalarse._

Cuando instala una aplicación con APT, el resultado muestra detalles de todo el software que se va a instalar. Esto puede incluir aplicaciones adicionales que dependen del nuevo software. Estas aplicaciones adicionales se denominan dependencias del software que se va a instalar.

Cuando se le solicite que continúe, presione la tecla **ENTER** para responder con la respuesta predeterminada. (En este caso, la respuesta predeterminada es **Sí**).

2. Compruebe que Suricata está instalado ejecutando la aplicación recién instalada.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`suricata`

Cuando se instala Suricata, se muestra la información de versión y uso:

Suricata 4.1.2
USAGE: suricata [OPTIONS] [BPF FILTER]

    -c <path>  : path to configuration file
    -T         : test configuration file (use with -c)
...
</path>

3. Utilice el administrador de paquetes APT para desinstalar Suricata.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.** Pulse **ENTER** (**Sí**) cuando se le pida que continúe.`sudo apt remove suricata`

Cuando se le solicite que continúe, presione la tecla **ENTER** para responder con la respuesta predeterminada. (En este caso, la respuesta predeterminada es **Sí**).

4. Compruebe que Suricata se ha desinstalado ejecutando de nuevo el comando de la aplicación.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`suricata`

Si ha desinstalado Suricata, el resultado es un mensaje de error:

-bash: /usr/bin/suricata: No such file or directory

Este mensaje indica que Suricata ya no se puede encontrar.

Haga clic en **Comprobar mi progreso** para comprobar que ha completado esta tarea correctamente.

Instalar y desinstalar la aplicación Suricata

## Tarea 3. Instalar la aplicación tcpdump

En esta tarea, debe instalar la aplicación tcpdump. Esta es una herramienta de línea de comandos que se puede usar para capturar el tráfico de red en un shell de Linux Bash.

- Utilice el administrador de paquetes APT para instalar tcpdump.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`sudo apt install tcpdump`

Haga clic en **Comprobar mi progreso** para comprobar que ha completado esta tarea correctamente.

Instalar la aplicación tcpdump

## Tarea 4. Enumerar las aplicaciones instaladas

A continuación, debe confirmar que ha instalado las aplicaciones necesarias. Es importante poder validar que se instalan las aplicaciones correctas. A menudo, es posible que desee verificar que también estén instaladas las versiones correctas.

1. Utilice el administrador de paquetes APT para enumerar todas las aplicaciones instaladas.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`apt list --installed`

Esto produce una larga lista de aplicaciones porque Linux tiene una gran cantidad de software instalado de forma predeterminada.

2. Busque en la lista para encontrar la aplicación tcpdump que instaló.

La aplicación Suricata no aparece en la lista porque instaló y luego desinstaló esa aplicación:

...
tcpdump/oldstable,now 4.9.3-1~deb10u2 amd64 [installed]
...

_**Nota:** La versión específica de `tcpdump` que ve en pantalla puede ser diferente de la que se muestra arriba._

Haga clic en **Comprobar mi progreso** para comprobar que ha completado esta tarea correctamente.

Enumerar las aplicaciones instaladas

## Tarea 5. Reinstalar la aplicación Suricata

En esta tarea, debe reinstalar la aplicación Suricata y verificar que se haya instalado correctamente.

1. Ejecute el comando para instalar la aplicación Suricata.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`sudo apt install suricata`

Cuando se le solicite que continúe, presione la tecla **ENTER** para responder con la respuesta predeterminada. (En este caso, la respuesta predeterminada es **Sí**).

2. Utilice el administrador de paquetes APT para enumerar las aplicaciones instaladas.

Escriba después del símbolo del sistema de la línea de comandos y presione **ENTRAR.**`apt list --installed`

3. Busque en la lista para confirmar que se ha instalado la aplicación Suricata.

El resultado debe incluir las siguientes líneas:

...
suricata/oldstable,now 1:4.1.2-2+deb10u1 amd64 [installed]
...
tcpdump/oldstable,now 4.9.3-1~deb10u2 amd64 [installed]
...

Haga clic en **Comprobar mi progreso** para comprobar que ha completado esta tarea correctamente.

Reinstalar la aplicación Suricata

## Conclusión

¡Buen trabajo!

Ahora tiene experiencia práctica con el administrador de paquetes APT. Aprendiste a

- instalar aplicaciones,
- desinstalar aplicaciones y
- Enumerar las aplicaciones instaladas.

Ser capaz de administrar aplicaciones instaladas en Linux es una habilidad clave para cualquier analista de seguridad.

## Finaliza tu laboratorio

Antes de finalizar el laboratorio, asegúrese de que está satisfecho de haber completado todas las tareas y siga estos pasos:

1. Haga clic en **Finalizar laboratorio**. Aparecerá un cuadro emergente. Haz clic en **Enviar** para confirmar que has terminado. Al finalizar el laboratorio, se eliminará el acceso al shell de Bash. No podrás volver a acceder al trabajo que has completado en él.
2. Otro cuadro emergente le pedirá que califique el laboratorio y proporcione comentarios. Puede completar esto si así lo desea.
3. Cierre la pestaña del navegador que contiene el laboratorio para volver a su curso.
4. Actualice la pestaña del navegador del curso para marcar el laboratorio como completo.