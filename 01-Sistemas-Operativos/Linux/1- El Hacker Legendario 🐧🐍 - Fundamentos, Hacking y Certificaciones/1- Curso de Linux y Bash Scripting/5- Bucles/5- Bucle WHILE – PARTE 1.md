
---
### **Primer script: Contador con bucle `while`**

```bash
#!/bin/bash

contador=1

while [ $contador -lt 5 ]; do
    echo "En esta vuelta la variable contador vale: $contador"
    contador=$((contador + 1))
done
```

#### **Explicación paso a paso:**

1. **Definición de la variable inicial:**
    
    - `contador=1`: Inicializa la variable `contador` con el valor 1.
2. **Inicio del bucle `while`:**
    
    - `while [ $contador -lt 5 ]; do`: Este bucle se ejecutará mientras el valor de `contador` sea menor que 5 (`-lt` significa "less than" o menor que).
3. **Acción dentro del bucle:**
    
    - `echo "En esta vuelta la variable contador vale: $contador"`: Imprime en la terminal el valor actual de `contador`.
    - `contador=$((contador + 1))`: Incrementa el valor de `contador` en 1 en cada iteración.
4. **Finalización:**
    
    - Cuando `contador` llega a 5, la condición del `while` (`$contador -lt 5`) deja de ser verdadera y el bucle termina.

---

### **Segundo script: Verificación de edad con bucle infinito**

```bash
#!/bin/bash

while true; do
    read -p "Introduce tu edad: " edad
    if [ "$edad" -lt "120" ]; then
        echo "Bien, has puesto tu edad correctamente"
        break
    elif [ "$edad" -gt "121" ]; then
        echo "Pon una edad correcta, inferior a 120"
    else
        echo "Datos incorrectos, introduce tu edad"
    fi
done
```

#### **Explicación paso a paso:**

1. **Inicio del bucle infinito:**
    
    - `while true; do`: Este bucle se ejecutará indefinidamente hasta que se use un comando como `break` para salir.
2. **Lectura de la edad:**
    
    - `read -p "Introduce tu edad: " edad`: Solicita al usuario que introduzca su edad y almacena el valor en la variable `edad`.
3. **Condicional para verificar la edad:**
    
    - **Primera condición:** `if [ "$edad" -lt "120" ];` verifica si la edad es menor a 120. Si es verdadero:
        - Imprime `Bien, has puesto tu edad correctamente`.
        - Usa `break` para salir del bucle.
    - **Segunda condición:** `elif [ "$edad" -gt "121" ];` verifica si la edad es mayor a 121. Si es verdadero:
        - Imprime `Pon una edad correcta, inferior a 120`.
    - **Caso contrario:** Si el valor introducido no es numérico o no cumple ninguna de las condiciones anteriores:
        - Imprime `Datos incorrectos, introduce tu edad`.
4. **Repetición del bucle:**
    
    - Si no se cumple la primera condición, el bucle sigue pidiendo la edad.

---

### **Tercer script: Verificación robusta con manejo de errores**

```bash
#!/bin/bash

while true; do
    read -p "Introduce tu edad: " edad
    if [ "$edad" -lt "120" ] 2>/dev/null; then
        echo "Bien, has puesto tu edad correctamente"
        break
    elif [ "$edad" -gt "121" ] 2>/dev/null; then
        echo "Pon una edad correcta, inferior a 120"
    else
        echo "Datos incorrectos, introduce tu edad"
    fi
done
```

#### **Explicación paso a paso:**

1. **Estructura similar al segundo script:**
    
    - Igual que el script anterior, solicita la edad al usuario dentro de un bucle infinito y evalúa las condiciones para determinar si es válida.
2. **Manejo de errores:**
    
    - `2>/dev/null`: Redirige los errores producidos por comandos fallidos o entradas no válidas al dispositivo nulo, evitando que se muestren en pantalla. Esto es útil para manejar casos donde el usuario introduce algo que no es un número.
3. **Ventaja del manejo de errores:**
    
    - Si el usuario introduce texto en lugar de un número, el script no genera mensajes de error del sistema, solo imprime `Datos incorrectos, introduce tu edad`.

---
