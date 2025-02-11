### Código:

```bash
#!/bin/bash

read -p "Introduce el numero que quieras adivinar: " numero_usuario
numero_secreto=2

while [ $numero_secreto -ne $numero_usuario ]; do
    read -p "Intentalo otra vez: " numero_usuario
    if  [ $numero_secreto -eq $numero_usuario ]; then
        echo "Nice, es ese, adivinaste"
        break
    fi
done
```

---

### Paso a paso:

1. **Declaración del intérprete (`#!/bin/bash`)**:
    
    - Indica que el script debe ejecutarse con el intérprete de Bash.
2. **Primera lectura del número del usuario**:
    
    - `read -p "Introduce el numero que quieras adivinar: " numero_usuario`
    - Se pide al usuario que introduzca un número. La entrada se guarda en la variable `numero_usuario`.
3. **Declaración del número secreto**:
    
    - `numero_secreto=2`
    - Se define una variable `numero_secreto` con el valor `2`, que es el número que el usuario debe adivinar.
4. **Estructura de bucle `while`**:
    
    - `while [ $numero_secreto -ne $numero_usuario ]; do`
    - El bucle se ejecutará mientras `numero_usuario` no sea igual a `numero_secreto` (`-ne` significa "no igual").
5. **Intentos adicionales**:
    
    - Dentro del bucle:
        
        ```bash
        read -p "Intentalo otra vez: " numero_usuario
        ```
        
    - Se solicita nuevamente al usuario que introduzca un número.
6. **Condicional para verificar si el número coincide**:
    
    - Si el número introducido coincide con el número secreto:
        
        ```bash
        if  [ $numero_secreto -eq $numero_usuario ]; then
            echo "Nice, es ese, adivinaste"
            break
        fi
        ```
        
    - Se imprime el mensaje "Nice, es ese, adivinaste" y el bucle termina (`break`).
7. **Finalización del bucle**:
    
    - El bucle termina cuando el usuario introduce el número correcto, ya sea dentro de la condición `if` o porque el número inicial coincide.

---

### Resultado esperado:

Cuando ejecutas este script:

1. Pide un número al usuario.
2. Si el número no coincide con el `numero_secreto` (2), sigue pidiendo intentos.
3. Cuando el usuario acierta, muestra el mensaje "Nice, es ese, adivinaste" y termina la ejecución.