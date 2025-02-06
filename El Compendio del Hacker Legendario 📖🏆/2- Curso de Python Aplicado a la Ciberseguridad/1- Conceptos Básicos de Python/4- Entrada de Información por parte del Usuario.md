### **Primer Fragmento: Solicitar y Mostrar un Nombre**

Código:

```python
variable = input("Por favor, introduce tu nombre: ")
print("El nombre insertado es: ", variable)
```

Explicación:

1. Se usa `input()` para solicitar al usuario que introduzca su nombre.
    - El mensaje mostrado es: `"Por favor, introduce tu nombre: "`.
    - La entrada del usuario se almacena en la variable `variable`.
2. Se usa `print()` para mostrar el nombre insertado con el mensaje:
    - `"El nombre insertado es: "` seguido del valor de `variable`.

---

### **Segundo Fragmento: Suma de Números Enteros**

Código:

```python
numero1 = int(input("Introduce un numero entero: "))
numero2 = int(input("Introduce otro numero entero: "))
resultado = numero1 + numero2
print("La suma de ambos numeros es:", resultado)
```

Explicación:

1. Se solicita al usuario que introduzca un número entero mediante `input()`.
    - Se convierte a `int` con `int(input(...))` y se almacena en `numero1`.
2. Se solicita un segundo número entero de la misma manera y se almacena en `numero2`.
3. Se realiza la suma de `numero1 + numero2` y se guarda en `resultado`.
4. Se muestra el resultado con `print()`:
    - `"La suma de ambos numeros es: "` seguido del valor de `resultado`.

---

### **Tercer Fragmento: Suma de Números Decimales**

Código:

```python
numero1 = float(input("Introduce un numero decimal: "))
numero2 = float(input("Introduce otro numero decimal: "))
resultado = numero1 + numero2
print("La suma de ambos numeros es:", resultado)
```

Explicación:

1. Se solicita un número decimal al usuario usando `input()`, convertido a `float()`, y almacenado en `numero1`.
2. Se solicita un segundo número decimal, se convierte a `float()` y se almacena en `numero2`.
3. Se suman `numero1 + numero2` y el resultado se almacena en `resultado`.
4. Se muestra la suma con `print()`:
    - `"La suma de ambos numeros es:"` seguido del valor de `resultado`.

---

### **Cuarto Fragmento: Solicitar Nombre y Edad**

Código:

```python
nombre = input("Introduce tu nombre: ")
edad = int(input("Introduce tu edad: "))
resultado = f"{nombre} {edad}"
print("tu nombre y tu edad es:", resultado)
print(f"tu nombre es {nombre} y tu edad es {edad}")
```

Explicación:

1. Se solicita el nombre del usuario con `input()` y se almacena en `nombre`.
2. Se solicita la edad con `input()`, se convierte a `int()` y se almacena en `edad`.
3. Se crea una cadena con `f-string` que une `nombre` y `edad` con un espacio en medio, almacenada en `resultado`.
4. Se imprime la cadena `"tu nombre y tu edad es: "` seguida del valor de `resultado`.
5. Se muestra otra línea de salida con `f-string`:
    - `"tu nombre es {nombre} y tu edad es {edad}"`  