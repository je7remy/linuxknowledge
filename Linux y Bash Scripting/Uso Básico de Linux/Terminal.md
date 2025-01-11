-----------------------

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


# Bash


| Comando Bash                    | Ejemplo                                          | Descripción                                  |
|--------------------------------|--------------------------------------------------|----------------------------------------------|
| **echo**                        | `echo "Hola, mundo"`                            | Imprime texto en la pantalla.               |
| **variables**                   | `nombre="Juan"; edad=30`                        | Declaración y asignación de variables.      |
| **if...else**                   | ```bash if [ condición ]; then comando; else otro_comando; fi``` | Estructura condicional.       |
| **for loop**                    | ```bash for i in {1..5}; do echo $i; done```   | Bucle que itera a través de elementos.      |
| **while loop**                  | ```bash while [ condición ]; do comando; done``` | Bucle que se ejecuta mientras se cumple una condición. |
| **funciones**                   | ```bash function saludo() { echo "Hola, $1"; }; saludo "Juan"``` | Declaración y uso de funciones.          |
| **read**                        | ```bash read -p "Ingresa un valor: " valor; echo "Ingresaste: $valor"``` | Lee la entrada del usuario.          |
| **case**                        | ```bash case $opcion in 1) echo "Opción 1";; 2) echo "Opción 2";; *) echo "Opción no válida";; esac``` | Estructura de selección múltiple.          |
| **arreglos (arrays)**           | ```bash colores=("rojo" "verde" "azul"); echo ${colores[0]}``` | Declaración y uso de arreglos.          |
| **grep**                        | `grep "patrón" archivo`                         | Busca patrones de texto en archivos.       |
| **sed**                         | `sed 's/antiguo/nuevo/g' archivo`              | Edita y transforma texto en archivos.      |
| **awk**                         | `awk '{print $1}' archivo`                     | Procesa y formatea texto en archivos.      |
| **pipes** \|                  | ```comando1 \| comando2```                            | Canaliza la salida de un comando a otro.  |
| **redirección**                 | `comando > archivo.txt`                        | Redirige la salida estándar a un archivo.  |
| **condicional ternario**        | ```bash edad=20; resultado=$((edad >= 18 ? "Mayor de edad" : "Menor de edad"))``` | Operador ternario para condicionales.  |