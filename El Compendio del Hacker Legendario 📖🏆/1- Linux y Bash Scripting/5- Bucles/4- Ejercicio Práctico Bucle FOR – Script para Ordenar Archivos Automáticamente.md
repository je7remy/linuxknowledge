
```bash
#!/bin/bash


mkdir -p  imagenes videos documentos

for archivo in *
do

            nombre_base=$(basename "$archivo")
            extension=$(echo $nombre_base | awk -F '.' '{print $NF}')
     
            case "$extension" in
                   jpg|png)
                           mv "$archivo" imagenes/
                           echo "Movido $archivo a la carpeta imagenes"
                           ;; 

                   mp4)  
                           mv "$archivo" videos/
                           echo "Movido $archivo a la carpeta videos" 
                           ;;    
                    
                   pdf|docx)
                           mv "$archivo" documentos/
                           echo "Movido $archivo a la carpeta documentos" 
                           ;;    
                     
                   *)
                           echo "Archivo $archivo no se movio porque la extension es desconocida" 
                           ;;    
            esac
done

```

Aquí está el paso a paso explicado:

1. **Creación de carpetas**:
    
    ```bash
    mkdir -p imagenes videos documentos
    ```
    
    - Crea tres carpetas: `imagenes`, `videos` y `documentos`. El comando `-p` asegura que no arrojará un error si las carpetas ya existen.
2. **Inicio del bucle**:
    
    ```bash
    for archivo in *
    ```
    
    - Itera sobre todos los archivos en el directorio actual. El carácter `*` incluye todos los archivos.
3. **Obtener el nombre base del archivo**:
    
    ```bash
    nombre_base=$(basename "$archivo")
    ```
    
    - Extrae el nombre del archivo con su extensión, sin el directorio.
4. **Extraer la extensión del archivo**:
    
    ```bash
    extension=$(echo $nombre_base | awk -F '.' '{print $NF}')
    ```
    
    - Usa `awk` para dividir el nombre del archivo por el carácter `.` y tomar la última parte (la extensión).
5. **Evaluación del caso**:
    
    ```bash
    case "$extension" in
    ```
    
    - Comienza un bloque de `case` para manejar diferentes extensiones de archivo.
6. **Mover imágenes (jpg y png)**:
    
    ```bash
    jpg|png)
        mv "$archivo" imagenes/
        echo "Movido $archivo a la carpeta imagenes"
        ;;
    ```
    
    - Si la extensión es `jpg` o `png`, mueve el archivo a la carpeta `imagenes` y muestra un mensaje.
7. **Mover videos (mp4)**:
    
    ```bash
    mp4)
        mv "$archivo" videos/
        echo "Movido $archivo a la carpeta videos"
        ;;
    ```
    
    - Si la extensión es `mp4`, mueve el archivo a `videos` y muestra un mensaje.
8. **Mover documentos (pdf y docx)**:
    
    ```bash
    pdf|docx)
        mv "$archivo" documentos/
        echo "Movido $archivo a la carpeta documentos"
        ;;
    ```
    
    - Si la extensión es `pdf` o `docx`, mueve el archivo a `documentos` y muestra un mensaje.
9. **Archivos con extensiones desconocidas**:
    
    ```bash
    *)
        echo "Archivo $archivo no se movio porque la extension es desconocida"
        ;;
    ```
    
    - Para cualquier otra extensión, muestra un mensaje indicando que el archivo no se movió.
10. **Fin del bloque `case` y del bucle**:
    
    - Finaliza el bloque `case` con `esac` y el bucle con `done`.

Este script organiza archivos en carpetas según sus extensiones y proporciona retroalimentación para cada operación.