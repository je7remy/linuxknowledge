###### Los **operadores lógicos** en Bash son herramientas que permiten combinar o comparar expresiones para tomar decisiones dentro de un script. Estas decisiones pueden ser condiciones simples o compuestas que determinan si un bloque de código se ejecuta o no.

---

#### **Script 1: Comparación simple**

```bash
#!/bin/bash

numero1=5
numero2=2

if [ "$numero1" -gt "$numero2" ]; then
    echo "El $numero1 es mayor que $numero2"
fi
```

**Explicación**:

1. **Declaración de variables**:
    - `numero1` y `numero2` se inicializan con los valores `5` y `2`.
2. **Condición (`-gt`)**:
    - El operador `-gt` (greater than) verifica si `numero1` es mayor que `numero2`.
3. **Acción**:
    - Si la condición es verdadera, se imprime el mensaje: "El 5 es mayor que 2".
4. **Resultado**:
    - En este caso, se cumple la condición y se imprime el mensaje.

---

#### **Script 2: Condiciones `if-elif`**

```bash
#!/bin/bash

numero1=5
numero2=5

if [ "$numero1" -gt "$numero2" ]; then
    echo "El $numero1 es mayor que $numero2"
elif [ "$numero1" -eq "$numero2" ]; then
    echo "El $numero1 es igual que $numero2"
fi
```

**Explicación**:

1. **Primera condición (`-gt`)**:
    - Comprueba si `numero1` es mayor que `numero2`.
2. **Segunda condición (`-eq`)**:
    - Si la primera condición es falsa, se evalúa si los números son iguales usando `-eq` (equal).
3. **Resultado**:
    - En este caso, como ambos números son iguales, se imprime: "El 5 es igual que 5".

---

#### **Script 3: Condiciones múltiples**

```bash
#!/bin/bash

numero1=5
numero2=6

if [ "$numero1" -gt "$numero2" ]; then
    echo "El $numero1 es mayor que $numero2"
elif [ "$numero1" -eq "$numero2" ]; then
    echo "El $numero1 es igual que $numero2"
elif [ "$numero1" -lt "$numero2" ]; then
    echo "El $numero1 es inferior que $numero2"
fi
```

**Explicación**:

1. **Condiciones (`-gt`, `-eq`, `-lt`)**:
    - Evalúa si `numero1` es mayor, igual o menor que `numero2`.
    - Los operadores son:
        - `-gt`: Mayor que.
        - `-eq`: Igual a.
        - `-lt`: Menor que.
2. **Resultado**:
    - Aquí, `numero1` es menor que `numero2`, por lo que imprime: "El 5 es inferior que 6".

---

#### **Script 4: Operador lógico `OR`**

```bash
#!/bin/bash

numero1=10
numero2=6

if [ "$numero1" -gt "$numero2" ] || [ "$numero1" -eq "$numero2" ]; then
    echo "El $numero1 es mayor que $numero2 o igual"
fi
```

**Explicación**:

1. **Operador lógico `||`**:
    - Este operador indica "O". Evalúa si al menos una de las condiciones es verdadera.
    - Condiciones evaluadas:
        - Si `numero1` es mayor que `numero2`.
        - Si `numero1` es igual a `numero2`.
2. **Resultado**:
    - Aquí, `numero1` es mayor que `numero2`, así que se imprime: "El 10 es mayor que 6 o igual".

---

#### **Script 5: Operador lógico `AND`**

```bash
#!/bin/bash

numero1=11
numero2=100

if [ "$numero1" -lt "$numero2" ] && [ "$numero2" -gt "$numero1" ]; then
    echo "El $numero1 es inferior que el $numero2 y a su vez el $numero2 es mayor que el $numero1"
fi
```

**Explicación**:

1. **Operador lógico `&&`**:
    - Este operador indica "Y". Ambas condiciones deben ser verdaderas.
    - Condiciones evaluadas:
        - Si `numero1` es menor que `numero2`.
        - Si `numero2` es mayor que `numero1`.
2. **Resultado**:
    - Ambas condiciones son verdaderas, así que imprime: "El 11 es inferior que el 100 y a su vez el 100 es mayor que el 11".

---

#### **Resumen de operadores lógicos en Bash**:

1. **`-gt`**: Mayor que (greater than).
2. **`-lt`**: Menor que (less than).
3. **`-eq`**: Igual a (equal to).
4. **`-ne`**: No igual (not equal).
5. **`-ge`**: Mayor o igual que (greater or equal).
6. **`-le`**: Menor o igual que (less or equal).
7. **`||`**: Lógico OR, al menos una condición verdadera.
8. **`&&`**: Lógico AND, todas las condiciones deben ser verdaderas.

