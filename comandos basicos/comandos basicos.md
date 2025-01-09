1. `ls`: Muestra la lista de archivos y directorios en el directorio actual.
2. `ls -l`: Lista con formato largo, mostrando detalles como permisos, número de enlaces, propietario, grupo, tamaño y fecha de modificación.
3. `ls -1`: Lista los archivos y directorios en una sola columna, es decir, cada nombre de archivo o directorio se muestra en una línea separada.
4. `cd`: Cambia el directorio de trabajo actual.
5. `mkdir`: Crea un nuevo directorio.
6. `rmdir`: Elimina un directorio vacío.
7. `rm`: Elimina un archivo. 
8. `rm -r`: Este comando eliminara las carpetas con contenido en ellas.
9. `rm -f`:  Este comando eliminara las carpetas con contenido en ellas aunque no tengas permiso de escritura en ellas.
10. `mv`: Mueve un archivo, (también podemos cambiar el nombre de un archivo).
11. `cp`: Copia un archivo.
12. `touch`: Crea un nuevo archivo.
13. `grep`: Busca una palabra en un archivo o lista. (ejemplo apt list | grep -i google
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
