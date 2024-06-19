1. `hostname`: Este comando simplemente muestra el nombre del host actual del sistema.
2. `id`: Mostrar la información del usuario actual.
3. `cat /etc/passwd`: Contiene información sobre los usuarios del sistema.
4. `cat /etc/group`: Contiene información sobre los grupos del sistema.
5. `cat /etc/shadow`: Contiene las contraseñas cifradas de los usuarios y otra información relacionada con la seguridad.
6. `chown nuevo_usuario:nuevo_grupo archivo.txt`:  Para cambiar el propietario de un archivo a `nuevo_usuario` y el grupo a `nuevo_grupo`.
7. `openssl passwd -1 "tu contraseña"` : Encripta la contraseña que desees.
8. `useradd nombre usuario -p "tu contraseña encriptada" -g nombre grupo`:  Crea un usuario, le asigna una contraseña y un grupo.
9. `deluser`: Eliminar usuario.
10. `find`: Busca archivos y directorios en un sistema de archivos, Ejemplo: `find ruta -name "nombre_archivo"`.
11. `locate`: Encuentra archivos mediante una base de datos de nombres de archivos, Uso: `locate nombre_archivo`.
12. `ps`: El comando `ps` se emplea para ver los procesos activos en el sistema. La opción `ps aux` muestra detalladamente los procesos en ejecución, su propietario y el consumo de recursos. Esto es útil para identificar procesos específicos por usuario, como se muestra al utilizar `ps -u <usuario>`.