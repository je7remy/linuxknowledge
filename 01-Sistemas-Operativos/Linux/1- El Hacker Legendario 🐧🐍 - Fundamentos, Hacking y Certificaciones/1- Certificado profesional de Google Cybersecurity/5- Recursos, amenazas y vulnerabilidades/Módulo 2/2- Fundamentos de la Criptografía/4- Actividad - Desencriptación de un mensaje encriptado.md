
# 🧩 Laboratorio: Descifrar un mensaje cifrado

---

## 📌 Resumen de la actividad

Anteriormente, aprendiste sobre **criptografía** y cómo el cifrado y el descifrado pueden utilizarse para proteger la información en línea.  
También conociste el **cifrado César**, uno de los primeros algoritmos criptográficos utilizados para proteger la privacidad de las personas.

Como analista de seguridad, es importante que entiendas el papel del cifrado para proteger los datos en línea y que estés familiarizado con los **controles de seguridad adecuados** para hacerlo.

En esta actividad de laboratorio:

- Usarás **comandos de Linux** para desencriptar archivos.
    
- Aprenderás a **romper un cifrado César**.
    
- Recuperarás archivos encriptados para **revelar mensajes ocultos**.
    

Este ejemplo incluye instrucciones detalladas y soluciones que puedes usar si no pudiste completar el laboratorio, o como repaso para el cuestionario del módulo.

---

## 🔎 Escenario

Todos los archivos de tu directorio personal han sido encriptados.  
Tu misión es **romper el cifrado César** y **descifrar los archivos** para recuperar los mensajes ocultos.

Pasos generales:

1. Explorar el directorio y leer un archivo de instrucciones.
    
2. Encontrar un archivo oculto y descifrar el **cifrado César**.
    
3. Descifrar un archivo encriptado con **AES-256-CBC** usando `openssl`.
    

📌 Nota: El laboratorio comienza con tu sesión iniciada como **usuario `analyst`**, en el directorio **`/home/analyst`**.

---

## 📝 Tarea 1. Leer el contenido de un archivo

1. Explorar el directorio personal:
    
    ```bash
    ls /home/analyst
    ```
    
    **Salida esperada:**
    
    ```
    Q1.encrypted  README.txt  caesar
    ```
    
2. Mostrar el contenido de `README.txt`:
    
    ```bash
    cat README.txt
    ```
    
    **Salida esperada:**
    
    ```
    Hello,
    All of your data has been encrypted. To recover your data, you will need to solve a cipher. To get started look for a hidden file in the caesar subdirectory.
    ```
    

👉 El mensaje indica que el archivo oculto está en el subdirectorio **`caesar`**.

---

## 📝 Tarea 2. Encontrar un archivo oculto

1. Moverse al subdirectorio `caesar`:
    
    ```bash
    cd caesar
    ```
    
2. Listar archivos, incluyendo ocultos:
    
    ```bash
    ls -a
    ```
    
    **Salida esperada:**
    
    ```
    .  ..  .leftShift3
    ```
    
3. Mostrar el contenido de `.leftShift3`:
    
    ```bash
    cat .leftShift3
    ```
    
    El mensaje está cifrado con **cifrado César** (desplazamiento de 3 a la izquierda).
    
4. Descifrar con el comando `tr`:
    
    ```bash
    cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
    ```
    
    **Salida esperada:**
    
    ```
    In order to recover your files you will need to enter the following command:
    
    openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
    ```
    

👉 Este comando revela cómo descifrar el archivo cifrado principal.

5. Regresar al directorio principal:
    
    ```bash
    cd ~
    ```
    

---

## 📝 Tarea 3. Descifrar un archivo

1. Ejecutar el comando revelado para descifrar el archivo `Q1.encrypted`:
    
    ```bash
    openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
    ```
    
    - `openssl` → herramienta de cifrado/descifrado.
        
    - `aes-256-cbc` → algoritmo de cifrado simétrico usado.
        
    - `-pbkdf2` → agrega seguridad a la clave.
        
    - `-a` → salida en Base64.
        
    - `-d` → modo descifrado.
        
    - `-in` → archivo de entrada.
        
    - `-out` → archivo de salida.
        
    - `-k` → clave (en este caso: **ettubrute**).
        
2. Verificar que el archivo descifrado se creó:
    
    ```bash
    ls
    ```
    
    **Salida esperada:**
    
    ```
    Q1.encrypted  README.txt  caesar  Q1.recovered
    ```
    
3. Mostrar el contenido del archivo recuperado:
    
    ```bash
    cat Q1.recovered
    ```
    
    **Salida esperada (ejemplo):**
    
    ```
    Congratulations! You have successfully recovered your data.
    ```
    

---
