### Explicación del script

El script realiza lo siguiente:

1. **Declara variables en Bash**:  
    Se definen dos variables:
    
    - `variable`: Almacena el nombre `Jeremy`.
    - `edad`: Almacena el valor `21` como un texto.
2. **Imprime las variables**:  
    Usando el comando `echo`, se imprime un mensaje que combina texto literal y el contenido de las variables utilizando la sintaxis `$variable` y `$edad`.
    
3. **Permisos de ejecución**:  
    El archivo llamado `script.sh` se le asignaron permisos de ejecución mediante el comando `chmod`.
    

### Código del script

```bash
#!/bin/bash

variable='Jeremy'
edad='21'
echo "Mi nombre es: $variable y mi edad es: $edad"
```

### Explicación de los pasos

1. **Primera línea (`#!/bin/bash`)**:  
    Es el _shebang_, que indica al sistema operativo que use el intérprete Bash para ejecutar el script.
    
2. **Declaración de variables**:
    
    - `variable='Jeremy'`: Se asigna el texto `Jeremy` a la variable `variable`.
    - `edad='21'`: Se asigna el texto `21` a la variable `edad`.
3. **Uso de las variables en el mensaje**:
    
    - `echo`: Es un comando que imprime texto en la terminal.
    - `"Mi nombre es: $variable y mi edad es: $edad"`: Se utiliza la interpolación de variables para incluir los valores de `variable` y `edad` en el texto.
4. **Dar permisos de ejecución al script**: Antes de ejecutar el script, es necesario asegurarse de que el archivo tiene permisos de ejecución. Esto se hace con el comando:
    
    ```bash
    chmod +x script.sh
    ```
    
    - `chmod`: Cambia los permisos del archivo.
    - `+x`: Otorga permisos de ejecución.
    - `script.sh`: Es el nombre del archivo.
5. **Ejecución del script**: Una vez otorgados los permisos de ejecución, el script se ejecuta con:
    
    ```bash
    ./script.sh
    ```
    

### Resultado esperado al ejecutar el script:

Al ejecutarlo, la salida en la terminal será:

```
Mi nombre es: Jeremy y mi edad es: 21
```


