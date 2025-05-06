### 1. Primer Script

```bash
#!/bin/bash

variable="naranja"

case "$variable" in 
     "naranja")
             echo "La variable es una naranja" 
             ;;
     "manzana")
             echo "La variable es una manzana"
             ;;
esac
```

#### Explicación:

1. **Inicialización de la Variable**:
    
    - `variable="naranja"` asigna el valor `"naranja"` a la variable `variable`.
2. **Sentencia `case`**:
    
    - La sentencia `case` compara el valor de la variable con los patrones definidos:
        - Si el valor es `"naranja"`, se ejecuta el bloque que imprime "La variable es una naranja".
        - Si el valor es `"manzana"`, se ejecuta el bloque que imprime "La variable es una manzana".
3. **Resultado**:
    
    - Dado que `variable` tiene el valor `"naranja"`, el script imprimirá:
        
        ```
        La variable es una naranja
        ```
        

---

### 2. Segundo Script

```bash
#!/bin/bash

variable="manzana"

case "$variable" in 
     "naranja")
             echo "La variable es una naranja" 
             ;;
     "manzana")
             echo "La variable es una manzana"
             ;;
esac
```

#### Cambios:

- **Variable**: Ahora `variable="manzana"`.
- El script coincidirá con el caso `"manzana"` y imprimirá:
    
    ```
    La variable es una manzana
    ```
    

---

### 3. Tercer Script

```bash
#!/bin/bash

variable="platano"

case "$variable" in 
     "naranja" | "platano")
             echo "La variable es una naranja o platano " 
             ;;
     "manzana")
             echo "La variable es una manzana"
             ;;
esac
```

#### Mejoras:

1. **Agrupación de Patrones**:
    
    - `"naranja" | "platano"`: Un único caso cubre múltiples valores.
    - Si el valor de `variable` es `"naranja"` o `"platano"`, se ejecuta el primer bloque.
2. **Resultado**:
    
    - Dado que `variable="platano"`, el script imprimirá:
        
        ```
        La variable es una naranja o platano 
        ```
        

---

### 4. Cuarto Script

```bash
#!/bin/bash

variable="platanoes"

case "$variable" in 
     "naranja" | "platano")
             echo "La variable es una naranja o platano " 
             ;;
     "manzana")
             echo "La variable es una manzana"
            ;;
     *) 
             echo "has introducido un dato que no es ni naranja, platano y manzana"
esac
```

#### Nuevas Funcionalidades:

1. **Comodín (`*`)**:
    
    - Este caso se ejecuta para cualquier valor no definido explícitamente.
2. **Resultado**:
    
    - Dado que `variable="platanoes"`, no coincide con ningún caso específico y se ejecutará el bloque comodín:
        
        ```
        has introducido un dato que no es ni naranja, platano y manzana
        ```
        

---

### 5. Quinto Script

```bash
#!/bin/bash

read -p "Introduce o naranja o manzana o platano" variable

case "$variable" in 
     "naranja" | "platano")
             echo "La variable es una naranja o platano " 
             ;;
     "manzana")
             echo "La variable es una manzana"
            ;;
     *)
             echo "has introducido un dato que no es ni naranja, platano y manzana"
esac
```

#### Modificaciones:

1. **Entrada del Usuario**:
    
    - `read -p` muestra un mensaje solicitando al usuario que introduzca un valor, y asigna este valor a `variable`.
2. **Ejecución Interactiva**:
    
    - Dependiendo de lo que introduzca el usuario:
        - `"naranja"` o `"platano"`: Imprime "La variable es una naranja o platano".
        - `"manzana"`: Imprime "La variable es una manzana".
        - Otros valores: Imprime "has introducido un dato que no es ni naranja, platano y manzana".

---

### 6. Sexto Script

```bash
#!/bin/bash

read -p "Introduce la palabra archivo para crearlo o carpeta para crearla: " variable

case "$variable" in 
     "archivo")
            touch archivo_creado 
             ;;
     "carpeta")
             mkdir carpteta_creada/
            ;;
          *)  
             echo "Eres imbecil?"
esac
```

#### Funcionalidades:

1. **Crear Archivo**:
    
    - Si el usuario introduce `"archivo"`, se crea un archivo llamado `archivo_creado` con el comando `touch`.
2. **Crear Carpeta**:
    
    - Si el usuario introduce `"carpeta"`, se crea un directorio llamado `carpteta_creada/` con el comando `mkdir`.
3. **Comodín**:
    
    - Para cualquier otro valor, imprime:
        
        ```
        Eres imbecil?
        ```
        

#### Resultado:

- Si el usuario introduce `"archivo"`, se crea el archivo `archivo_creado`.
- Si introduce `"carpeta"`, se crea el directorio `carpteta_creada/`.
- Para cualquier otro valor, muestra el mensaje ofensivo.
