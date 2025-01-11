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

