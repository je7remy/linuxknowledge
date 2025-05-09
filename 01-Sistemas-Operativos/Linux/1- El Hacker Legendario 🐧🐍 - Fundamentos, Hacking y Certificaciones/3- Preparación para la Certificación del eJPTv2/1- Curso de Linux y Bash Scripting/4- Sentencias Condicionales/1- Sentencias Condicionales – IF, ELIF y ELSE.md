**Paso a paso de las sentencias condicionales en Bash:**

Las sentencias condicionales en Bash permiten evaluar condiciones y ejecutar comandos dependiendo de si esas condiciones se cumplen o no. Los ejemplos que mencionaste demuestran varios usos de estructuras condicionales. Aquí está el análisis paso a paso:

---

### **1. Condicional básica (`if`)**

```bash
fruta=naranja

if [ "$fruta" = "naranja" ]; then
    echo "La variable fruta es igual a Naranja"
fi
```

#### **Explicación:**

1. **Declaración de variable:**
    
    ```bash
    fruta=naranja
    ```
    
    Se define la variable `fruta` con el valor `"naranja"`.
    
2. **Inicio del bloque condicional:**
    
    ```bash
    if [ "$fruta" = "naranja" ]; then
    ```
    
    - `if`: Indica el inicio de una evaluación condicional.
    - `[ "$fruta" = "naranja" ]`: Evalúa si el valor de la variable `fruta` es igual a `"naranja"`.
        - Los corchetes `[ ]` ejecutan un test.
        - El operador `=` compara cadenas.
    - `"$fruta"`: Usa comillas dobles para manejar posibles valores con espacios.
3. **Acción si la condición es verdadera:**
    
    ```bash
    echo "La variable fruta es igual a Naranja"
    ```
    
    Si la condición se cumple, imprime el mensaje.
    
4. **Cierre del bloque:**
    
    ```bash
    fi
    ```
    
    Finaliza la estructura `if`.
    

---

### **2. Condicional `if-elif`**

```bash
fruta=manzana 
if [ "$fruta" = "naranja" ]; then
    echo "La variable fruta es igual a Naranja" 
elif [ "$fruta" = "manzana" ]; then
    echo "La variable fruta es manzana"
fi
```

#### **Explicación:**

1. **Primera condición:**
    
    ```bash
    if [ "$fruta" = "naranja" ]; then
    ```
    
    Evalúa si `fruta` es igual a `"naranja"`. Si es verdadera, ejecuta el bloque siguiente. De lo contrario, pasa al siguiente `elif`.
    
2. **Segunda condición (`elif`):**
    
    ```bash
    elif [ "$fruta" = "manzana" ]; then
    ```
    
    - `elif`: Evalúa una nueva condición si la anterior es falsa.
    - Compara si `fruta` es `"manzana"`.
3. **Mensaje asociado:**
    
    ```bash
    echo "La variable fruta es manzana"
    ```
    
4. **Finalización:** La estructura concluye con `fi`.
    

---

### **3. Condicional `if-elif-else`**

```bash
fruta=amanzana

if [ "$fruta" = "naranja" ]; then
    echo "La variable fruta es igual a Naranja"
elif [ "$fruta" = "manzana" ]; then
    echo "La variable fruta es manzana"
else
    echo "No se detectó el patrón dentro de la variable fruta"
fi
```

#### **Novedad aquí:**

1. **Uso del bloque `else`:**
    - `else`: Se ejecuta si ninguna condición previa se cumple.
    - En este caso, si `fruta` no es `"naranja"` ni `"manzana"`, se ejecutará el mensaje del bloque `else`.

---

### **4. Entrada por el usuario (`read`)**

```bash
read -p "Introduce tu nombre: jeremy o manzana " nombre 

if [ "$nombre" = "jeremy" ]; then
    echo "Tu nombre es Jeremy"
elif [ "$nombre" = "manzana" ]; then
    echo "El nombre que has puesto es manzana"
else
    echo "El nombre que has puesto no es jeremy ni manzana"
fi
```

#### **Explicación adicional:**

1. **Entrada dinámica:**
    
    ```bash
    read -p "Introduce tu nombre: jeremy o manzana " nombre
    ```
    
    - `read`: Captura un valor ingresado por el usuario.
    - `-p`: Permite mostrar un mensaje antes de capturar el input.
    - `nombre`: Variable donde se guarda la entrada del usuario.
2. **Condicionales:** Se aplican las mismas reglas de `if-elif-else`.
    

---

### **5. Argumentos posicionales**

```bash
nombre=$1 

if [ "$nombre" = "jeremy" ]; then
    echo "Tu nombre es Jeremy"
elif [ "$nombre" = "manzana" ]; then
    echo "El nombre que has puesto es manzana"
else
    echo "El nombre que has puesto no es jeremy ni manzana"
fi
```

#### **Diferencias clave:**

1. **Uso de `$1`:**
    - `$1`: Representa el primer argumento proporcionado al script desde la línea de comandos.
    - Ejemplo: Si se ejecuta `./script.sh jeremy`, entonces `$nombre` será `"jeremy"`.

---

### **Resumen de elementos importantes:**

1. **Sintaxis básica:**
    
    ```bash
    if [ condición ]; then
        comandos
    elif [ condición ]; then
        comandos
    else
        comandos
    fi
    ```
    
2. **Operadores comunes:**
    
    - Comparación de cadenas: `=`, `!=`.
    - Comparación numérica: `-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge`.
3. **Entrada dinámica:**
    
    - `read` para capturar datos del usuario.
    - Argumentos posicionales (`$1`, `$2`, etc.).
4. **Errores comunes:**
    
    - Olvidar los espacios en los corchetes: `[ "$variable" = "valor" ]`.
    - No usar comillas dobles, lo que puede causar problemas con valores vacíos o espacios.

Estos bloques condicionales son básicos pero fundamentales para automatizar tareas en scripts de Bash. 