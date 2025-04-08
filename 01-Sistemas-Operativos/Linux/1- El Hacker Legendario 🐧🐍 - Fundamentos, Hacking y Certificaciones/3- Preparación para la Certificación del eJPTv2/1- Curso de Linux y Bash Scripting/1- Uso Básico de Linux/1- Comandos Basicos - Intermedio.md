![[1.PNG]]

1. `ls`: Muestra la lista de archivos y directorios en el directorio actual.
2. `ls -l`: Lista con formato largo, mostrando detalles como permisos, número de enlaces, propietario, grupo, tamaño y fecha de modificación.
3. `ls -1`: Lista los archivos y directorios en una sola columna, es decir, cada nombre de archivo o directorio se muestra en una línea separada.
4. `cd`: Cambia el directorio de trabajo actual.
5. `mkdir`: Crea un nuevo directorio.
6. `rmdir`: Elimina un directorio vacío.
7. `rm -d`: "dirección de la carpeta", este comando eliminara las carpetas sin contenido en ellas.
8. `rm`: Elimina un archivo. 
9. `rm -r`: Este comando eliminara las carpetas con contenido en ellas.
10. `rm -f`:  Este comando eliminara las carpetas con contenido en ellas aunque no tengas permiso de escritura en ellas.
11. `mv`: Mueve un archivo, (también podemos cambiar el nombre de un archivo). ejemplo (mv "/home/tetta-kisaki/Escritorio/Como eliminar carpeta.md" /home/tetta-kisaki/Escritorio/linuxknowledge/)
12. `cp`: Copia un archivo, como copiar archivos de una carpeta a otra? (cp "/home/tetta-kisaki/Escritorio/Como eliminar carpeta.md" /home/tetta-kisaki/Escritorio/linuxknowledge/)
13. `touch`: Crea un nuevo archivo.
14. `grep`: Busca una palabra en un archivo o lista. (ejemplo apt list | grep -i google
- **`apt list`:**  
    Lista todos los paquetes disponibles en los repositorios configurados y los instalados en tu sistema.
    
- **`|`:**  
    El operador "pipe" (`|`) envía la salida de `apt list` como entrada al comando `grep`.
    
- **`grep -i google`:**  
    Filtra las líneas que contienen la palabra "google" sin importar si están en mayúsculas o minúsculas. Este comando mostrará una lista de paquetes relacionados con "google" disponibles en los repositorios o instalados en tu sistema.)
14. `man`: Muestra el manual de un comando.
15. `ping`: Verifica la conexión a internet.
16. `ifconfig`: Muestra los detalles de la interfaz de red.
17. `wget`: Descarga un archivo.
18. `sudo apt install`: Instala un paquete.
19. `sudo apt remove`: Elimina un paquete.
20. `sudo apt upgrade`: Actualiza los paquetes en el sistema.
21. `sudo apt update`: Obtiene las actualizaciones de los paquetes.
22. `whoami`: Muestra el nombre de usuario actual.
23. `sudo su`: Cambia el usuario actual a super usuario o root.
24. `pwd`: Muestra la ruta del directorio actual.
25. `nano`: Editor de texto en la terminal.
26. `chmod`: Cambia los permisos de un archivo o directorio.
27. `passwd`: Cambiar contraseña.
28. `--help`: Proporciona una breve descripción de la funcionalidad de los comandos y sus opciones.
29. `su` (Switch user): Permite cambiar a otro usuario o asumir el rol de superusuario, Ejemplo: `su nombre_usuario` o `su -` (cambia a superusuario).
30. `who`: Muestra información sobre los usuarios que están actualmente conectados al sistema.
31. `w`: Proporciona información más detallada sobre los usuarios que están conectados y sus actividades.
32. `history`: `(!his)`El **historial** de comandos le permite ver todos los comandos que ha utilizado recientemente en el mismo terminal, (Puede usar una combinación del signo de exclamación (!) y el número de historial o la cadena de comandos para repetir los comandos usados anteriormente.)
33. `hostname`: Este comando simplemente muestra el nombre del host actual del sistema.
34. `hostname -I`: Este comando muestra la ip privada de la maquina o sistema operativo.
35. `id`: Mostrar la información del usuario actual.
36. `cat /etc/passwd`: Contiene información sobre los usuarios del sistema.
37. `cat /etc/group`: Contiene información sobre los grupos del sistema.
38. `cat /etc/shadow`: Contiene las contraseñas cifradas de los usuarios y otra información  relacionada con la seguridad.
39. `chown nuevo_usuario:nuevo_grupo archivo.txt`:  Para cambiar el propietario de un archivo a `nuevo_usuario` y el grupo a `nuevo_grupo`.
40. `openssl passwd -1 "tu contraseña"` : Encripta la contraseña que desees.
41. `useradd nombre usuario -p "tu contraseña encriptada" -g nombre grupo`:  Crea un usuario, le asigna una contraseña y un grupo.
42. `deluser`: Eliminar usuario.
43. `find`: Busca archivos y directorios en un sistema de archivos, Ejemplo: `find ruta -name "nombre_archivo"`.
44. `locate`: Encuentra archivos mediante una base de datos de nombres de archivos, Uso: `locate nombre_archivo`.
45. `ps`: El comando `ps` se emplea para ver los procesos activos en el sistema. La opción `ps aux` muestra detalladamente los procesos en ejecución, su propietario y el consumo de recursos. Esto es útil para identificar procesos específicos por usuario, como se muestra al utilizar `ps -u <usuario>`.

-----------------------


# Caso Practico
## Como Sincronizar Archivos de una Carpeta a Otra:
en este caso se quiere copiar el contenido de una carpeta, excluyendo la propia carpeta. Puedes lograrlo con rsync utilizando la opción --include junto con --exclude. Aquí te muestro cómo hacerlo:

rsync -av --include='*/' --include='*' --exclude='*' /home/tetta-kisaki/Documentos /repos


Este comando copiará solo el contenido de la carpeta de origen a la carpeta de destino, excluyendo la carpeta de origen misma. Explicación de los argumentos:

- -av: Opciones estándar de rsync para una copia recursiva y verbosa.
- --include='*/': Incluye todos los directorios dentro de la carpeta de origen.
- --include='*': Incluye todos los archivos dentro de la carpeta de origen.
- --exclude='*': Excluye la carpeta de origen misma.
- /ruta/de/la/carpeta/origen/: Ruta de la carpeta de origen.
- /ruta/de/la/carpeta/destino/: Ruta de la carpeta de destino.

Este comando copiará solo el contenido de la carpeta de origen, incluyendo sus archivos y subdirectorios, pero sin copiar la carpeta de origen misma.

-------------

---
tags:
  - #comandos
  - #linux
  - #bash
  - #tabla
  - #scripting
---

---
## Comandos Básicos

| Comando | Ejemplo                           | Descripción                                           |
| ------- | --------------------------------- | ----------------------------------------------------- |
| ls      | `ls -l`                           | Lista archivos y directorios en el directorio actual. |
| cd      | `cd /ruta/al/directorio`          | Cambia de directorio.                                 |
| pwd     | `pwd`                             | Muestra la ruta del directorio actual.                |
| mkdir   | `mkdir nombre_directorio`         | Crea un nuevo directorio.                             |
| rm      | `rm archivo.txt`                  | Elimina archivos o directorios.                       |
| cp      | `cp archivo.txt carpeta_destino/` | Copia archivos o directorios.                         |
| mv      | `mv archivo.txt nuevo_nombre.txt` | Mueve o renombra archivos o directorios.              |
| touch   | `touch nuevo_archivo.txt`         | Crea un archivo vacío o actualiza la fecha de acceso. |
| cat     | `cat archivo.txt`                 | Muestra el contenido de un archivo en la terminal.    |
| grep    | `grep "patrón" archivo.txt`       | Busca patrones de texto en archivos.                  |

## Gestión de Permisos y Propietarios

| Comando   | Ejemplo                     | Descripción                                      |
|-----------|-----------------------------|--------------------------------------------------|
| chmod     | `chmod 755 archivo`        | Cambia los permisos de archivos o directorios.   |
| chown     | `chown usuario:grupo archivo` | Cambia el propietario de archivos o directorios. |

## Monitoreo y Gestión de Procesos

| Comando   | Ejemplo                     | Descripción                                      |
|-----------|-----------------------------|--------------------------------------------------|
| ps        | `ps aux`                    | Muestra información sobre los procesos en ejecución. |
| top       | `top`                       | Muestra información en tiempo real sobre el uso de recursos. |

## Gestión de Espacio en Disco

| Comando   | Ejemplo                     | Descripción                                      |
|-----------|-----------------------------|--------------------------------------------------|
| df        | `df -h`                     | Muestra el espacio en disco utilizado y disponible en particiones. |
| du        | `du -sh directorio`         | Muestra el uso del espacio en disco de directorios y archivos. |

## Compresión y Archivos

| Comando   | Ejemplo                     | Descripción                                      |
|-----------|-----------------------------|--------------------------------------------------|
| tar       | `tar -czvf archivo.tar.gz directorio` | Crea o extrae archivos comprimidos en formato tar. |
| find      | `find /ruta -name "archivo.txt"` | Busca archivos o directorios en el sistema de archivos. |

## Red y Conexiones Remotas

| Comando | Ejemplo                | Descripción                                                      |
| ------- | ---------------------- | ---------------------------------------------------------------- |
| ssh     | `ssh usuario@hostname` | Inicia una sesión segura de shell remoto.                        |
| wget    | `wget URL`             | Descarga archivos desde la web a través de la línea de comandos. |

## Comandos de Sistema

| Comando   | Ejemplo                     | Descripción                                      |
|-----------|-----------------------------|--------------------------------------------------|
| uname     | `uname -a`                  | Muestra información sobre el sistema operativo. |
| date      | `date`                      | Muestra la fecha y hora actual.                 |
| uptime    | `uptime`                    | Muestra el tiempo de actividad del sistema.     |
| who       | `who`                       | Muestra quién está conectado al sistema.        |
| dmesg     | `dmesg`                     | Muestra registros del kernel.                   |

## Redes y Conectividad

| Comando   | Ejemplo                     | Descripción                                      |
|-----------|-----------------------------|--------------------------------------------------|
| ifconfig  | `ifconfig`                  | Muestra información de las interfaces de red.   |
| ping      | `ping ejemplo.com`          | Prueba la conectividad con un host remoto.      |
| netstat   | `netstat -tuln`             | Muestra información sobre puertos de red abiertos. |
| traceroute| `traceroute ejemplo.com`     | Rastrea la ruta de paquetes hacia un host remoto. |
| ssh-keygen| `ssh-keygen -t rsa`          | Genera pares de claves SSH para autenticación segura. |
## Comandos de networking en Linux

- **ifconfig**: Muestra información detallada sobre las interfaces de red, como dirección IP, máscara de subred y más.
    
- **ping**: Permite verificar la conectividad entre dos nodos al enviar paquetes de datos a un destino específico y recibir respuestas.
    
- **netstat**: Proporciona estadísticas y detalles sobre conexiones de red abiertas, puertos y enrutamiento.
    
- **nslookup**: Se utiliza para consultar servidores de nombres de dominio (DNS) y obtener información sobre direcciones IP asociadas a nombres de dominio y viceversa.
    
- **ip**: Ofrece una gama de funcionalidades para configurar y mostrar información de las interfaces de red, tablas de enrutamiento, políticas de enrutamiento, y más.
    
- **route**: Muestra y modifica la tabla de enrutamiento del kernel.
    
- **traceroute**: Muestra la ruta que toman los paquetes de datos desde tu dispositivo hasta un destino específico en la red, indicando todos los saltos intermedios.
    
- **wget/curl**: Herramientas para la descarga de archivos desde servidores remotos utilizando varios protocolos como HTTP, HTTPS, FTP, etc.

# Bash


| Comando Bash             | Ejemplo                                                                                                | Descripción                                            |
| ------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| **echo**                 | `echo "Hola, mundo"`                                                                                   | Imprime texto en la pantalla.                          |
| **variables**            | `nombre="Juan"; edad=30`                                                                               | Declaración y asignación de variables.                 |
| **if...else**            | ```bash if [ condición ]; then comando; else otro_comando; fi```                                       | Estructura condicional.                                |
| **for loop**             | ```bash for i in {1..5}; do echo $i; done```                                                           | Bucle que itera a través de elementos.                 |
| **while loop**           | ```bash while [ condición ]; do comando; done```                                                       | Bucle que se ejecuta mientras se cumple una condición. |
| **funciones**            | ```bash function saludo() { echo "Hola, $1"; }; saludo "Juan"```                                       | Declaración y uso de funciones.                        |
| **read**                 | ```bash read -p "Ingresa un valor: " valor; echo "Ingresaste: $valor"```                               | Lee la entrada del usuario.                            |
| **case**                 | ```bash case $opcion in 1) echo "Opción 1";; 2) echo "Opción 2";; *) echo "Opción no válida";; esac``` | Estructura de selección múltiple.                      |
| **arreglos (arrays)**    | ```bash colores=("rojo" "verde" "azul"); echo ${colores[0]}```                                         | Declaración y uso de arreglos.                         |
| **grep**                 | `grep "patrón" archivo`                                                                                | Busca patrones de texto en archivos.                   |
| **sed**                  | `sed 's/antiguo/nuevo/g' archivo`                                                                      | Edita y transforma texto en archivos.                  |
| **awk**                  | `awk '{print $1}' archivo`                                                                             | Procesa y formatea texto en archivos.                  |
| **pipes** \|             | ```comando1 \| comando2```                                                                             | Canaliza la salida de un comando a otro.               |
| **redirección**          | `comando > archivo.txt`                                                                                | Redirige la salida estándar a un archivo.              |
| **condicional ternario** | ```bash edad=20; resultado=$((edad >= 18 ? "Mayor de edad" : "Menor de edad"))```                      | Operador ternario para condicionales.                  |


```bash
cat /etc/issue
```

se utiliza en sistemas basados en Linux para mostrar el mensaje de bienvenida del sistema antes de iniciar sesión. Este archivo generalmente contiene información sobre la distribución del sistema operativo.

Si lo ejecutas en una terminal, podrías ver algo como:

```plaintext
Ubuntu 22.04 LTS \n \l
```

o en otras distribuciones:

```plaintext
Debian GNU/Linux 12 \n \l
```

Si tienes acceso a un sistema Linux, puedes probarlo directamente.
# Systemctl

**`systemctl`** es una herramienta de línea de comandos en sistemas basados en Linux que interactúa con **systemd**, el gestor de sistemas y servicios más comúnmente usado en las distribuciones modernas de Linux. Permite a los usuarios administrar servicios, controlar el sistema de inicio, monitorear el estado de los servicios y más.

### **Definición**

`systemctl` es una herramienta que actúa como interfaz principal para **systemd**, permitiendo realizar operaciones como iniciar, detener, habilitar, deshabilitar, recargar o reiniciar servicios.

### Como Habilitar el Bluetooth

habilitar servicio:
sudo systemctl enable bluetooth

iniciar servicio:
sudo systemctl start bluetooth 

detener sevicio:
sudo systemctl stop bluetooth

### Como Habilitar Paqueteria Snap

habilitar servicio:
sudo systemctl enable snapd

reiniciar servicio:
sudo systemctl restart snapd

verificar estado del sevicio:
sudo systemctl status snapd

----

# Comandos de arch (Athena OS)

```bash
sudo pacman -Syyu
```

El comando `sudo pacman -Syyu` en Arch Linux y sus derivados (como Manjaro) hace lo siguiente:

1. **`sudo`**: Ejecuta el comando con privilegios de superusuario.
2. **`pacman`**: Es el gestor de paquetes de Arch Linux.
3. **`-S`**: Indica que se quiere sincronizar e instalar paquetes.
4. **`-yy`**: Fuerza la actualización de la base de datos de paquetes desde los repositorios, incluso si ya está actualizada.
5. **`-u`**: Actualiza todos los paquetes del sistema a sus versiones más recientes disponibles en los repositorios.

### ⚠️ Precaución:

- Usar `-yy` innecesariamente puede aumentar la carga en los servidores espejo.
- Antes de actualizar, es recomendable verificar el [sitio de Arch Linux](https://archlinux.org/) para asegurarte de que no haya problemas recientes con paquetes críticos.
- Si hay una actualización importante del sistema, puede ser necesario revisar el [Arch Linux News](https://archlinux.org/news/) para instrucciones adicionales.

Si quieres una actualización más segura y controlada, puedes simplemente usar:

```bash
sudo pacman -Syu
```

Si tienes dudas sobre dependencias o posibles conflictos, ejecuta:

```bash
sudo pacman -Syu --ask 4
```

Esto te pedirá confirmación antes de cada paso.





**[[3- Análisis De La Red Desde Linux – Comandos Básicos Parte 1]]**
**[[9- Uso de Grep]]**
**[[7- Uso de Tuberías o Pipes]]**
**[[8- Gestión de Procesos]]**