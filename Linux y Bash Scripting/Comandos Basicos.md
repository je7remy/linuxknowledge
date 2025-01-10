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
