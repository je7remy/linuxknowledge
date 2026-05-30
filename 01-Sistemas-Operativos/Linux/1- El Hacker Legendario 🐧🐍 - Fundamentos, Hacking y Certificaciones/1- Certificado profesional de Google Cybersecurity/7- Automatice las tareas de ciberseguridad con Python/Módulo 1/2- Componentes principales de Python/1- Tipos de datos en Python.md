---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-1]
actualizado: 2026-05-28
---

# Tipos de datos en Python

# 🧠 Tipos de Datos en Python

En Python, un **tipo de dato** define la **categoría** de información con la que trabajará un programa.  
Así como en la cocina clasificamos los ingredientes (por ejemplo, vegetales y carnes), Python clasifica los datos según su naturaleza y cómo deben manipularse.

Los **tipos de datos más comunes** en Python son:  
📘 _cadena (string)_  
🔢 _entero (int)_  
💧 _flotante (float)_  
⚙️ _booleano (bool)_  
📋 _lista (list)_

---

## 📘 1. Cadenas (Strings)

Una **cadena** es una **secuencia ordenada de caracteres**.  
Puede incluir letras, números, símbolos o espacios, siempre **entre comillas simples o dobles**.

```python
# Ejemplo de cadena
print("¡Hola Python!")
```

- Las cadenas se usan para mostrar texto o mensajes.
    
- Los números dentro de una cadena **no pueden usarse para cálculos**.
    
- Si olvidas las comillas, Python mostrará un **error de sintaxis**.
    

---

## 💧 2. Flotantes (Float)

Los **flotantes** representan **números con punto decimal**, incluso si el decimal es “.0”.

```python
# Ejemplo de número flotante
print(2.5)
print(10.0)
```

- Se utilizan para representar valores con **decimales** o **fracciones**.
    
- Son útiles en operaciones matemáticas más precisas, como porcentajes o promedios.
    

---

## 🔢 3. Enteros (Integer)

Los **enteros** son números **sin decimales**.  
Pueden ser positivos, negativos o cero.

```python
# Ejemplo de número entero
print(0)
print(-9)
print(5000)
```

- Python permite **operaciones aritméticas** con enteros y flotantes:
    

```python
# Operaciones matemáticas básicas
# Este código suma 1 + 1
print(1 + 1)  # Resultado: 2
```

- Puedes usar `print()` con enteros o flotantes para realizar suma, resta, multiplicación o división.
    

---

## ⚙️ 4. Booleanos (Bool)

Los **booleanos** solo pueden tener **dos valores posibles**:  
✅ `True` (verdadero)  
❌ `False` (falso)

Sirven para **comparar valores** y aplicar **lógica** dentro del programa.

```python
# Comparaciones booleanas
print(10 < 5)   # False
print(9 < 12)   # True
```

- Python evalúa las condiciones y devuelve un valor booleano según el resultado.
    
- Estos valores son la base para las **sentencias condicionales** como `if` y `else`.
    

---

## 📋 5. Listas (List)

Una **lista** es una colección **ordenada y modificable** de datos.  
Se escriben entre **corchetes [ ]**, y los elementos se separan por **comas**.

```python
# Esta lista contiene tres nombres de usuario
# que tienen acceso a un archivo confidencial
usuarios = ["ana", "carlos", "maria"]
print(usuarios)
```

🔹 La salida será:

```
['ana', 'carlos', 'maria']
```

- Las listas pueden contener **cadenas, números o incluso otras listas**.
    
- Más adelante podrás **acceder, modificar y eliminar elementos** individuales.
    

---

## 🧩 Resumen General

|Tipo de Dato|Ejemplo|Descripción|
|---|---|---|
|**String**|`"Hola"`|Texto entre comillas|
|**Integer**|`25`|Número entero sin decimales|
|**Float**|`3.14`|Número con decimales|
|**Boolean**|`True`, `False`|Valores lógicos|
|**List**|`["a", "b", "c"]`|Colección de elementos|

---

## 🧠 Conclusión

Los tipos de datos en Python son la **base** de cualquier programa.  
Comprenderlos permite:

- Manejar correctamente los valores.
    
- Evitar errores de tipo.
    
- Crear scripts más eficientes y lógicos.
    

En las siguientes lecciones aprenderás a **combinar estos tipos** para procesar datos, automatizar tareas y desarrollar herramientas útiles para la ciberseguridad.

---

Aquí tienes tu respuesta formateada y justificada para tus apuntes de estudio 👇

---

## 🧠 Pregunta

**¿Qué tipo de datos solo puede tener un valor de True o False?**

### ✅ Respuesta correcta:

**Booleana**

---

### 📘 Explicación:

El tipo de dato **booleano** en Python representa valores **lógicos**, y **solo puede tener dos posibles resultados**:

- `True` (verdadero)
    
- `False` (falso)
    

Los datos booleanos se utilizan en **comparaciones y estructuras de control**, permitiendo que los programas tomen decisiones según condiciones específicas.

Por ejemplo:

```python
print(10 < 5)   # False
print(9 < 12)   # True
```

En este caso, Python evalúa las comparaciones y devuelve el valor booleano correspondiente.

---

### 💡 En resumen:

|Tipo de dato|Ejemplo|Descripción|
|---|---|---|
|**Booleano**|`True`, `False`|Representa valores de verdad utilizados en lógica condicional|

Los booleanos son fundamentales en la **programación lógica**, la **validación de condiciones** y el **control de flujo** en los programas de ciberseguridad y automatización.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ➡️ Siguiente: [[2- Más información sobre los tipos de datos]]
