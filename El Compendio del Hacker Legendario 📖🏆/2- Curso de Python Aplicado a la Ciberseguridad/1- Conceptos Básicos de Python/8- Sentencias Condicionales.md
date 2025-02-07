### **Definición de Sentencias Condicionales**

Las **sentencias condicionales** en programación permiten ejecutar diferentes bloques de código dependiendo de si una condición se evalúa como `True` o `False`. Estas condiciones suelen ser expresiones lógicas que comparan valores y devuelven un resultado booleano.

En Python, las sentencias condicionales principales son:

| Estructura | Descripción                                                      |
| ---------- | ---------------------------------------------------------------- |
| `if`       | Evalúa una condición y ejecuta un bloque de código si es `True`. |
| `elif`     | Evalúa una nueva condición si el `if` anterior es `False`.       |
| `else`     | Se ejecuta si ninguna condición anterior se cumple.              |

## **Primer bloque: Verificación de mayoría de edad**

```python
edad = 19

if edad > 18:
    print("Eres mayor de edad, puedes pasar")
elif edad < 18:
    print("Eres menor de edad, no puedes pasar")
else:
    print("Datos incorrecto, debes introducir una edad")
```

### **Explicación paso a paso:**

1. Se asigna el valor `19` a la variable `edad`.
2. Se evalúa la condición del `if`:
    - `edad > 18` → `19 > 18` → `True`
    - Como la condición es `True`, se ejecuta la instrucción dentro del `if`:
        
        ```python
        print("Eres mayor de edad, puedes pasar")
        ```
        
3. Como ya se ejecutó el `if`, el `elif` y el `else` no se evalúan.
4. **Salida:**
    
    ```
    Eres mayor de edad, puedes pasar
    ```
    

---

## **Segundo bloque: Verificación de rango de edad con límites**

```python
edad = -1

if edad > 18 and edad < 30:
    print("Eres mayor de edad, puedes pasar")
elif edad < 18 and edad > 0:
    print("Eres menor de edad, no puedes pasar")
else:
    print("Datos incorrecto, debes introducir una edad valida")
```

### **Explicación paso a paso:**

1. Se asigna el valor `-1` a la variable `edad`.
2. Se evalúa la primera condición del `if`:
    - `edad > 18 and edad < 30` → `-1 > 18 and -1 < 30` → `False and True` → `False`
    - Como es `False`, no se ejecuta el código del `if`.
3. Se evalúa la segunda condición del `elif`:
    - `edad < 18 and edad > 0` → `-1 < 18 and -1 > 0` → `True and False` → `False`
    - Como es `False`, no se ejecuta el código del `elif`.
4. Como ninguna condición anterior se cumplió, se ejecuta el `else`:
    
    ```python
    print("Datos incorrecto, debes introducir una edad valida")
    ```
    
5. **Salida:**
    
    ```
    Datos incorrecto, debes introducir una edad valida
    ```
    

---

## **Tercer bloque: Búsqueda de número de teléfono en texto**

```python
texto = "Mi numero de telefono es (829) 522-1765"
patron = "(829) 522-1765"

if patron in texto:
    print("El numero de telefono esta presente en el texto")
else:
    print("El numero de telefono no esta presente en el texto")
```

### **Explicación paso a paso:**

6. Se define la variable `texto` con el valor `"Mi numero de telefono es (829) 522-1765"`.
7. Se define la variable `patron` con el valor `"(829) 522-1765"`.
8. Se evalúa la condición del `if`:
    - `patron in texto` → `"(829) 522-1765" in "Mi numero de telefono es (829) 522-1765"` → `True`
    - Como la condición es `True`, se ejecuta:
        
        ```python
        print("El numero de telefono esta presente en el texto")
        ```
        
9. **Salida:**
    
    ```
    El numero de telefono esta presente en el texto
    ```
    

---

## **Cuarto bloque: Verificación de contraseña ingresada por el usuario**

```python
contraseña = "La contraseña es password1"
patron = input("Inserta tu contraseña: ")

if patron in contraseña:
    print("Contraseña correcta, puedes pasar")
else:
    print("Contraseña incorrecta, no puedes pasar")
```

### **Explicación paso a paso:**

10. Se define la variable `contraseña` con el valor `"La contraseña es password1"`.
11. Se pide al usuario que ingrese una contraseña mediante `input()` y se guarda en la variable `patron`.
12. Se evalúa la condición del `if`:
    - `patron in contraseña` verifica si el texto ingresado por el usuario está dentro de la variable `contraseña`.
    - Si la condición es `True`, se imprime `"Contraseña correcta, puedes pasar"`.
    - Si la condición es `False`, se imprime `"Contraseña incorrecta, no puedes pasar"`.
13. **Ejemplo de ejecución:**
    - Si el usuario introduce `"password1"` como entrada:
        
        ```
        Inserta tu contraseña: password1
        Contraseña correcta, puedes pasar
        ```
        
    - Si el usuario introduce `"clave123"` como entrada:
        
        ```
        Inserta tu contraseña: clave123
        Contraseña incorrecta, no puedes pasar
        ```
        

---

## **Resumen de salidas**

|Código|Entrada|Evaluación|Resultado|
|---|---|---|---|
|`edad = 19`|-|`edad > 18` → `True`|`"Eres mayor de edad, puedes pasar"`|
|`edad = -1`|-|Ninguna condición es `True`|`"Datos incorrecto, debes introducir una edad valida"`|
|`"(829) 522-1765" in texto`|-|`True`|`"El numero de telefono esta presente en el texto"`|
|`input("Inserta tu contraseña: ")`|`"password1"`|`"password1" in "La contraseña es password1"` → `True`|`"Contraseña correcta, puedes pasar"`|
|`input("Inserta tu contraseña: ")`|`"clave123"`|`"clave123" in "La contraseña es password1"` → `False`|`"Contraseña incorrecta, no puedes pasar"`|
