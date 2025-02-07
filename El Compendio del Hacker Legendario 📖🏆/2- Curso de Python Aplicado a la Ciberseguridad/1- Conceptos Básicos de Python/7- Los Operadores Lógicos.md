### **Definición de Operadores Lógicos en Python**

Los **operadores lógicos** en Python son utilizados para combinar condiciones y evaluar expresiones booleanas (`True` o `False`). Permiten realizar operaciones de lógica booleana para la toma de decisiones en el código.

### **Principales operadores lógicos en Python**

|Operador|Descripción|Ejemplo|Resultado|
|---|---|---|---|
|`and`|Devuelve `True` si **ambas** condiciones son `True`|`(5 > 2) and (3 < 4)`|`True`|
|`or`|Devuelve `True` si **al menos una** condición es `True`|`(5 > 2) or (3 > 4)`|`True`|
|`not`|Invierte el valor booleano de una condición|`not (5 > 2)`|`False`|

### **Ejemplos prácticos**

```python
# Uso de AND: Ambas condiciones deben ser verdaderas
print(10 > 5 and 8 < 12)  # True, porque ambas son ciertas

# Uso de OR: Al menos una condición debe ser verdadera
print(10 > 5 or 8 > 12)   # True, porque la primera es cierta

# Uso de NOT: Invierte el resultado
print(not (10 > 5))       # False, porque "10 > 5" es True, y not lo invierte
```

Los operadores lógicos son ampliamente utilizados en estructuras de control como `if`, `while`, y en expresiones condicionales.

### **Primer bloque: Uso del operador lógico `and`**

```python
numero = 5
print(numero > 0 and numero < 10)
```

1. Se asigna el valor `5` a la variable `numero`.
2. Se evalúa la expresión con el operador lógico `and`:
    - `numero > 0` → `5 > 0` → `True`
    - `numero < 10` → `5 < 10` → `True`
3. Como **ambas condiciones** son `True`, el operador `and` devuelve `True`.
4. Se imprime:  
    **Salida:** `True`

---

### **Segundo bloque: Uso del operador lógico `and` con condiciones diferentes**

```python
numero = 5
print(numero > 0 and numero < 4)
```

1. `numero = 5`
2. Se evalúa la expresión con `and`:
    - `numero > 0` → `5 > 0` → `True`
    - `numero < 4` → `5 < 4` → `False`
3. Como **una de las condiciones** es `False`, el operador `and` devuelve `False`.
4. Se imprime:  
    **Salida:** `False`

---

### **Tercer bloque: Uso del operador lógico `or`**

```python
print(numero > 0 or numero < 4)
```

1. `numero` sigue siendo `5`.
2. Se evalúa la expresión con `or`:
    - `numero > 0` → `5 > 0` → `True`
    - `numero < 4` → `5 < 4` → `False`
3. Con `or`, basta con que **una de las condiciones** sea `True` para que toda la expresión sea `True`.
4. Como `numero > 0` es `True`, la expresión completa devuelve `True`.
5. Se imprime:  
    **Salida:** `True`

---

### **Cuarto bloque: Uso del operador `not` con una variable booleana**

```python
verdadero = True
print(not verdadero)
```

6. Se asigna `True` a la variable `verdadero`.
7. Se evalúa `not verdadero`, lo que invierte el valor lógico de `True` a `False`.
8. Se imprime:  
    **Salida:** `False`

---

### **Quinto bloque: Uso del operador `not` con una comparación**

```python
numero = 10
print(not numero > 5)
```

9. Se asigna `10` a la variable `numero`.
10. Se evalúa la condición `numero > 5`:
    - `10 > 5` → `True`
11. Se aplica `not` a `True`, lo que invierte el resultado a `False`.
12. Se imprime:  
    **Salida:** `False`

---

### **Resumen de salidas**

| Código                       | Evaluación       | Resultado |
| ---------------------------- | ---------------- | --------- |
| `numero > 0 and numero < 10` | `True and True`  | `True`    |
| `numero > 0 and numero < 4`  | `True and False` | `False`   |
| `numero > 0 or numero < 4`   | `True or False`  | `True`    |
| `not verdadero`              | `not True`       | `False`   |
| `not numero > 5`             | `not True`       | `False`   |

