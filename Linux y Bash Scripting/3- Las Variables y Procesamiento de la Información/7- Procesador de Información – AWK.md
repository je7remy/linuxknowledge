### Explicación de los comandos y pasos

1. **`nano datos.txt`**
    
    - Crea o abre un archivo llamado `datos.txt` para editarlo en el editor de texto Nano.
    - El contenido ingresado tiene este formato:
        
        ```
        luis | 30 | Madrid
        reinaldo | 25 | Bogotá
        fernando | 35 | Buenos Aires
        ...
        ```
        
2. **`cat datos.txt | awk '{print $1}'`**
    
    - `cat datos.txt`: Muestra el contenido del archivo.
    - `awk '{print $1}'`: Extrae e imprime el primer campo (`$1`) de cada línea, separando los campos por defecto (espacios y tabulaciones).
    - **Salida**: Los nombres (`luis, reinaldo, fernando, ...`).
3. **`cat datos.txt | awk '{print $2}'`**
    
    - `awk '{print $2}'`: Extrae el segundo campo.
    - El segundo campo contiene solo el separador (`|`), porque el delimitador predeterminado es el espacio en blanco, no el carácter `|`.
4. **`cat datos.txt | awk '{print $3}'`**
    
    - Extrae el tercer campo: las edades (`30, 25, 35, ...`).
    - Esto funciona porque el espacio divide los campos antes y después de `|`.
5. **`cat datos.txt | awk '{print $NF}'`**
    
    - `$NF`: Se refiere al último campo de cada línea.
    - **Salida**: Las ciudades (`Madrid, Bogotá, Buenos Aires, ...`).
6. **`cat datos.txt | awk '{print $1 "-->" $5}'`**
    
    - Combina el primer campo (`$1`) con el quinto campo (`$5`) usando `-->`.
    - Como `awk` trata los campos separados por espacios en blanco, `$5` corresponde a la segunda parte del nombre de las ciudades compuestas.
    - Ejemplo:
        
        ```
        luis-->Madrid
        reinaldo-->Bogotá
        fernando-->Buenos
        ...
        ```
        
7. **`echo 'mario,luis pedro,jaime' | awk -F ',' '{print $1}'`**
    
    - `echo`: Imprime una cadena de texto.
    - `-F ','`: Define el delimitador como una coma `,`.
    - `{print $1}`: Extrae el primer campo (`mario`).
8. **`echo 'mario,luis pedro,jaime' | awk -F ',' '{print $2}'`**
    
    - Extrae el segundo campo (`luis pedro`).
9. **`echo 'mario,luis pedro,jaime' | awk -F ',' '{print $3}'`**
    
    - Extrae el tercer campo (`jaime`).
10. **`extencion=$(ls | awk -F '.' '{print $NF}')`**
    
    - `ls`: Lista los archivos en el directorio actual.
    - `awk -F '.' '{print $NF}'`: Extrae la última parte después del punto (`.`) en los nombres de archivo, que corresponde a la extensión.
    - Asigna el resultado a la variable `extencion`.
11. **`echo $extencion`**
    
    - Imprime el contenido de la variable `extencion`.
    - **Salida**: Incluye las extensiones detectadas como `zip`, `txt`, etc.

---

### Conceptos clave

- **Separador predeterminado en `awk`**: Por defecto, `awk` separa los campos por espacios en blanco (espacios o tabulaciones). Para manejar delimitadores personalizados como `|`, debes usar `-F`.
    
    ```bash
    awk -F '|' '{print $2}'
    ```
    
- **Campos con varias palabras**: Los campos con varias palabras pueden causar desalineación a menos que estén procesados correctamente o rodeados por comillas.

