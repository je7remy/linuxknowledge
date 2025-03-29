### Parametros:

---

### **Script 1: Mostrar argumentos**

```bash
#!/bin/bash

variable1=$1
variable2=$2

echo "El primer argumento es $variable1 y el segundo $variable2"
```

#### **Ejecución:**

1. **Parámetros de entrada**: Cuando se ejecuta el script, se proporcionan los valores `mario` y `27` como argumentos de línea de comandos.
    
    - `$1` se asigna el valor `mario`.
    - `$2` se asigna el valor `27`.
2. **Salida**: El script utiliza el comando `echo` para mostrar los valores proporcionados.
    
    - Se imprime el texto:
        
        ```bash
        El primer argumento es mario y el segundo 27
        ```
        
3. **Resultado final**:
    
    ```bash
    ./script.sh mario 27
    El primer argumento es mario y el segundo 27
    ```
    

**Este script muestra cómo acceder a los argumentos que se pasan al script y cómo utilizarlos.**

---

### **Script 2: Realizar una operación aritmética**

```bash
#!/bin/bash

numero1=$1
numero2=$2

resultado=$(( $numero1 + $numero2 ))
echo "El resultado es: $resultado"
```

#### **Ejecución:**

1. **Parámetros de entrada**: El script espera dos argumentos numéricos. Por ejemplo:
    
    ```bash
    ./addition.sh 5 10
    ```
    
    - `$1` se asigna el valor `5`.
    - `$2` se asigna el valor `10`.
2. **Cálculo**:
    
    - El operador `$(( ))` realiza operaciones aritméticas en Bash.
    - La variable `resultado` se calcula como `5 + 10`, dando `15`.
3. **Salida**:
    
    - El script imprime el resultado de la suma:
        
        ```bash
        El resultado es: 15
        ```
        
4. **Resultado final**:
    
    ```bash
    ./addition.sh 5 10
    El resultado es: 15
    ```
    

---

### **Resumen**

- Ambos scripts demuestran conceptos básicos de Bash:
    - Acceso a argumentos pasados en la línea de comandos (`$1`, `$2`, etc.).
    - Uso de `echo` para mostrar resultados.
    - Operaciones aritméticas con `$(( ))`.

Estos scripts son ideales para tareas simples como manejar argumentos o realizar cálculos básicos y sirven como base para desarrollar scripts más avanzados en Bash.