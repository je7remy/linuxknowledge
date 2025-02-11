
---

#Python #WhileLoop #CicloWhile #BucleInfinito #ControlDeFlujo #Programación #EjemplosPython #Automatización #AprenderPython 🚀

---
### **Definición de Bucle `while` en Python**

Un **bucle `while`** es una estructura de control en Python que permite ejecutar un bloque de código **mientras una condición sea verdadera (`True`)**.

---

### **Sintaxis de `while`**

```python
while condición:
    # Código que se ejecuta mientras la condición sea True
```

- La **condición** se evalúa antes de cada iteración.
- Si la condición es **True**, se ejecuta el bloque de código.
- Cuando la condición se vuelve **False**, el bucle se detiene.

### **1. Primer bloque: Bucle while sin incremento**

```python
contador = 0
while contador < 10:
    print("Voy a imprimir mientras la variable sea inferior a 10")
```

#### **Paso a paso:**

1. Se inicializa la variable `contador` con el valor `0`.
2. Se entra en el bucle `while`, que continuará ejecutándose mientras `contador < 10`.
3. Se imprime el mensaje **"Voy a imprimir mientras la variable sea inferior a 10"** en cada iteración.
4. **Problema:** Como `contador` nunca cambia dentro del bucle, la condición `contador < 10` siempre es `True`, lo que genera un **bucle infinito**.

---

### **2. Segundo bloque: Bucle while con incremento**

```python
contador = 0
while contador < 10:
    print("En esta vuelta la variable contador vale:", contador)
    contador += 1
```

#### **Paso a paso:**

1. Se inicializa `contador` en `0`.
2. Se entra en el `while`, que se ejecuta mientras `contador < 10`.
3. En cada iteración:
    - Se imprime el valor actual de `contador`.
    - Se incrementa `contador` en `1`.
4. Cuando `contador` llega a `10`, la condición `contador < 10` es **False**, por lo que el bucle termina.

**Salida esperada:**

```
En esta vuelta la variable contador vale: 0
En esta vuelta la variable contador vale: 1
En esta vuelta la variable contador vale: 2
...
En esta vuelta la variable contador vale: 9
```

---

### **3. Tercer bloque: Bucle while con condición `<=`**

```python
contador = 0
while contador <= 10:
    print("En esta vuelta la variable contador vale:", contador)
    contador += 1
```

#### **Paso a paso:**

1. Se inicializa `contador` en `0`.
2. Se ejecuta el `while` mientras `contador <= 10` (incluyendo `10`).
3. Se imprime el valor de `contador` y luego se incrementa en `1`.
4. Cuando `contador` llega a `11`, la condición `contador <= 10` es **False**, por lo que el bucle termina.

**Diferencia con el bloque anterior:** Este código imprime hasta `10` en lugar de `9`.

**Salida esperada:**

```
En esta vuelta la variable contador vale: 0
En esta vuelta la variable contador vale: 1
...
En esta vuelta la variable contador vale: 10
```

---

### **4. Bucle infinito con `while True`**

```python
while True:
    print("Esto es un bucle infinito")
```

#### **Paso a paso:**

1. `while True` establece una condición que **siempre** es `True`, por lo que el bucle nunca termina.
2. En cada iteración se imprime `"Esto es un bucle infinito"`, sin cambios en ninguna variable.

**Problema:** Este código nunca termina a menos que se detenga manualmente (con `Ctrl + C` en la terminal).

---

### **5. Bucle con condición booleana y parada manual**

```python
condicion = True
contador = 0

while condicion == True:
    print("La condición se está cumpliendo, seguimos dentro del bucle:", contador)
    contador += 1
    if contador == 10:
        condicion = False
```

#### **Paso a paso:**

1. Se inicializa `condicion = True` y `contador = 0`.
2. El `while` sigue ejecutándose mientras `condicion` sea `True`.
3. En cada iteración:
    - Se imprime el valor de `contador`.
    - `contador` se incrementa en `1`.
    - Cuando `contador == 10`, `condicion` se vuelve `False`, lo que termina el bucle.

**Salida esperada:**

```
La condición se está cumpliendo, seguimos dentro del bucle: 0
La condición se está cumpliendo, seguimos dentro del bucle: 1
...
La condición se está cumpliendo, seguimos dentro del bucle: 9
```

Después de imprimir el mensaje con `contador = 9`, el bucle se detiene.

---

### **6. Bucle con `else` para controlar la impresión**

```python
condicion = True
contador = 0

while condicion == True:
    contador += 1
    if contador == 10:
        condicion = False
    else:
        print("La condición se está cumpliendo, seguimos dentro del bucle:", contador)
```

#### **Paso a paso:**

4. Se inicializa `condicion = True` y `contador = 0`.
5. En cada iteración:
    - Se incrementa `contador` primero.
    - Si `contador == 10`, se establece `condicion = False`, terminando el bucle.
    - **Si `contador` es menor que `10`, se imprime el mensaje.**
6. Cuando `contador == 10`, el `if` impide imprimir y el bucle termina.

**Diferencia con el bloque anterior:**  
Este código **no imprime cuando `contador == 10`**.

**Salida esperada:**

```
La condición se está cumpliendo, seguimos dentro del bucle: 1
La condición se está cumpliendo, seguimos dentro del bucle: 2
...
La condición se está cumpliendo, seguimos dentro del bucle: 9
```

Después de imprimir `9`, el bucle se detiene sin mostrar `10`.

---

### **Resumen general**

- **Primer bloque:** **Bucle infinito** (porque `contador` no cambia).
- **Segundo bloque:** Bucle que imprime `0` a `9` y se detiene.
- **Tercer bloque:** Bucle que imprime `0` a `10` y se detiene.
- **Cuarto bloque:** **Bucle infinito** (`while True` nunca cambia).
- **Quinto bloque:** Bucle con **parada manual cuando `contador == 10`**.
- **Sexto bloque:** Igual que el quinto, pero **no imprime cuando `contador == 10`**.




[[7- Los Operadores Lógicos]]
[[8- Sentencias Condicionales]]
[[9- Bucle FOR]]
