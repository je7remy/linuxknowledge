Un **script** es un conjunto de instrucciones que se escriben en un archivo de texto y se ejecutan secuencialmente por un intérprete, en este caso, el intérprete de **Bash** (Bourne Again Shell) en sistemas Linux o similares:

1. **Creación del archivo del script**:
    
    - Comenzaste editando un archivo llamado `script.sh` utilizando un editor de texto como `nano`:
        
        ```bash
        nano script.sh
        ```
        
    - Dentro del editor, añadiste el contenido del script:
        
        ```bash
        #!/bin/bash
        echo 'hola mundo'
        sleep 3
        echo 'este es el segundo mensaje de mi script'
        ```
        
2. **Guardar y salir del editor (`nano`)**:
    
    - Presionaste `Ctrl + O` para guardar los cambios en el archivo `script.sh`.
    - Luego, presionaste `Ctrl + X` para salir del editor.
3. **Hacer el archivo ejecutable**:
    
    - Usaste el comando `chmod` para otorgar permisos de ejecución al archivo:
        
        ```bash
        sudo chmod +x script.sh
        ```
        
    - Esto permite que el script pueda ejecutarse directamente como un comando.
4. **Ejecutar el script**:
    
    - Corres el script utilizando `./` seguido del nombre del archivo:
        
        ```bash
        ./script.sh
        ```
        

### Comportamiento del script

- Al ejecutar el script, primero muestra `hola mundo` en la terminal.
- Luego, hace una pausa de 3 segundos debido al comando `sleep 3`.
- Finalmente, imprime el mensaje `este es el segundo mensaje de mi script`.



[[11- Ejercicio Práctico, Script Siempre en Ejecución]] 