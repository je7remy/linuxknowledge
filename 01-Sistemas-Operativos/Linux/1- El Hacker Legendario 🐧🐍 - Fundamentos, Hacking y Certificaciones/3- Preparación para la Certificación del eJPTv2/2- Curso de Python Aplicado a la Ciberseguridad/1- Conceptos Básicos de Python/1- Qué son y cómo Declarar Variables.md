### **¿Qué son las Variables?**

Las variables son espacios en la memoria del ordenador que almacenan datos que pueden ser utilizados y modificados durante la ejecución de un programa. En Python, las variables se crean simplemente asignándoles un valor con el operador `=`.

### **Cómo Declarar Variables en Python**

Para declarar una variable en Python, se sigue el formato:

```python
nombre_variable = valor
```

- **nombre_variable**: el identificador que asignamos a nuestra variable.
- **valor**: el dato que queremos almacenar.

Python es un lenguaje de tipado dinámico, lo que significa que no necesitamos especificar el tipo de dato al declarar la variable; Python lo infiere automáticamente.

---

## **Ejemplos Paso a Paso con Diferentes Formas de Imprimir Datos**

### **1. Declarar Variables de Texto y Número**

```python
nombre = "Jeremy"  # Variable de tipo cadena (str)
edad = 21          # Variable de tipo entero (int)
```

### **2. Imprimir Variables en la Consola con Diferentes Métodos**

```python
print("hola")  
```

- Este `print()` imprime simplemente la palabra `"hola"` sin ninguna variable.

#### **Usando comas (`,`) en `print()`**

```python
print("Tu nombre es:", nombre, "y tu edad es:", edad)
```

- **Explicación:**
    - Se separan los valores por comas dentro del `print()`, lo que permite imprimir diferentes elementos en una misma línea.
    - Python inserta automáticamente espacios entre los elementos separados por comas.
    - Es una forma sencilla de concatenar valores de diferentes tipos (texto y variables numéricas) sin necesidad de conversión manual.

**Salida esperada:**

```
Tu nombre es: Jeremy y tu edad es: 21
```

#### **Usando f-strings (`f""`)**

```python
print(f"Tu nombre es: {nombre} y tu edad es: {edad}")
```

- **Explicación:**
    - Las **f-strings** (formatted strings) permiten incluir variables dentro de una cadena de texto utilizando `{}`.
    - Se coloca una `f` antes de las comillas para indicar que se trata de una cadena formateada.
    - Es más legible y eficiente que la concatenación con comas o el operador `+`.

**Salida esperada:**

```
Tu nombre es: Jeremy y tu edad es: 21
```

---

### **3. Operaciones Aritméticas con Variables Numéricas**

```python
numero1 = 1  # Variable entera
numero2 = 2  # Otra variable entera
resultado = numero1 + numero2  # Suma de las variables
```

### **4. Diferentes Formas de Mostrar el Resultado**

```python
print("El resultado es:", resultado)
```

- **Explicación:**
    - Usa la separación con comas para imprimir el mensaje y el valor de la variable `resultado`.

**Salida esperada:**

```
El resultado es: 3
```

```python
print(f"La suma de los numeros {numero1} y {numero2} es: {resultado}")
```

- **Explicación:**
    - Usa una **f-string** para insertar los valores de `numero1`, `numero2` y `resultado` directamente dentro del texto sin necesidad de separarlos con comas.

**Salida esperada:**

```
La suma de los numeros 1 y 2 es: 3
```

---

### **Resumen**

|Método de impresión|Ventajas|Ejemplo|
|---|---|---|
|`print("Texto", variable)`|Fácil de usar, añade espacios automáticamente|`print("Tu edad es:", edad)`|
|`print(f"Texto {variable}")`|Más legible, permite formatear fácilmente|`print(f"Tu edad es: {edad}")`|

Las **f-strings** son más recomendadas por su claridad y eficiencia en comparación con otras formas de formateo.

---
