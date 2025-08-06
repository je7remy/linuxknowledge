
**concepto base**  

el sistema de archivos de linux se puede visualizar como un árbol donde el directorio raíz es la base y de él se ramifican subdirectorios. organizar bien esta estructura facilita encontrar información y mantenerla segura.

**comandos clave**

- **crear y eliminar directorios**
    
    - `mkdir nombre_directorio` → crea un directorio
        
    - `rmdir nombre_directorio` → elimina un directorio vacío
        
- **crear y eliminar archivos**
    
    - `touch nombre_archivo` → crea un archivo vacío
        
    - `rm nombre_archivo` → elimina un archivo
        
- **mover y copiar**
    
    - `mv archivo destino` → mueve un archivo/directorio
        
    - `cp archivo destino` → copia un archivo/directorio
        

**ejemplos del vídeo**

1. eliminar directorio
    
    ```bash
    rmdir oldreports
    ```
    
2. crear directorio para borradores
    
    ```bash
    mkdir drafts
    ```
    
3. crear archivos dentro de drafts
    
    ```bash
    touch email_patches.txt
    touch OS_patches.txt
    ```
    
4. eliminar un archivo
    
    ```bash
    rm email_patches.txt
    ```
    
5. mover archivo de informes a borradores
    
    ```bash
    mv email_policy.txt drafts
    ```
    
6. copiar archivo de vulnerabilidades a proyectos
    
    ```bash
    cp vulnerabilities.txt ../projects
    ```
    

**edición de archivos con nano**

1. abrir archivo para editar
    
    ```bash
    nano OS_patches.txt
    ```
    
2. escribir contenido, por ejemplo:
    
    ```
    OS Patches
    ```
    
3. guardar → `Ctrl+O` → enter
    
4. salir → `Ctrl+X`
    

**pregunta:**  

¿cuál de los siguientes comandos puede utilizar para crear un nuevo archivo?

- touch ✅
    
- mv
    
- rmdir
    
- mkdir
    

**respuesta correcta:**  
puede utilizar el comando **touch** para crear un nuevo archivo.