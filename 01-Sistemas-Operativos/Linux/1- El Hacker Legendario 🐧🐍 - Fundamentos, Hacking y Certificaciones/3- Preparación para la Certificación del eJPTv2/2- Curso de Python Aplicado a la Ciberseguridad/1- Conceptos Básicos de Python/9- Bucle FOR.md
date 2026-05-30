---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, python, pentesting]
actualizado: 2026-05-28
---

# Bucle FOR

---

#Python #ForLoop #CicloFor #Iteraciones #Listas #Cadenas #Programación #EjemplosPython #Automatización #AprenderPython 🚀

---
### Definición del ciclo `for` en Python

En Python, el ciclo `for` se usa para iterar sobre una secuencia, como listas, cadenas de texto, tuplas, diccionarios o rangos. En cada iteración, una variable toma el valor del siguiente elemento de la secuencia hasta que se recorren todos los elementos.

---

### Análisis paso a paso de los ejemplos:

#### 1️⃣ **Iteración sobre una cadena**

```python
for variable in "Hola Mundo":
    print(variable)
```

- Se recorre la cadena `"Hola Mundo"`, caracter por caracter.
- En cada iteración, `variable` toma un carácter de la cadena y lo imprime en pantalla.

**Salida:**

```
H
o
l
a
 
M
u
n
d
o
```

---

#### 2️⃣ **Iteración sobre una lista**

```python
lista = ['naranja', 'limon', 'manzana']
for fruta in lista:
    print(fruta)
```

- Se recorre la lista `['naranja', 'limon', 'manzana']`.
- En cada iteración, `fruta` toma un elemento de la lista y lo imprime.

**Salida:**

```
naranja
limon
manzana
```

---

#### 3️⃣ **Mostrando el valor de la variable en cada iteración (uso de `print`)**

```python
for fruta in lista:
    print('En esta vuelta la variable fruta vale:', fruta)
```

- Similar al ejemplo anterior, pero con una descripción adicional al imprimir.

**Salida:**

```
En esta vuelta la variable fruta vale: naranja
En esta vuelta la variable fruta vale: limon
En esta vuelta la variable fruta vale: manzana
```

🔹 **Otra forma con `f-strings` (Python 3.6+):**

```python
for fruta in lista:
    print(f'En esta vuelta la variable fruta vale: {fruta}')
```

Produce el mismo resultado, pero es más limpio y fácil de leer.

---

#### 4️⃣ **Validación de un correo electrónico**

```python
correo = False

for caracter in input("Inserte una dirección de correo:"):
    print("En esta vuelta la variable caracter vale:", caracter)

    if caracter == "@":
        correo = True

if correo == True:
    print("El correo es válido, tiene un arroba")
else:
    print("Error, el correo no tiene un arroba")
```

- Se solicita un correo por teclado.
- Se recorre cada carácter de la cadena ingresada.
- Si se encuentra un `@`, se cambia la variable `correo` a `True`.
- Después del bucle, se verifica si `correo` es `True` para determinar si la entrada es válida.

**Ejemplo de entrada:**

```
usuario@example.com
```

**Salida:**

```
En esta vuelta la variable caracter vale: u
En esta vuelta la variable caracter vale: s
...
En esta vuelta la variable caracter vale: @
...
El correo es válido, tiene un arroba
```

---

#### 5️⃣ **Lista por comprensión**

```python
lista = ['platano', 'naranja', 'melon']
bucle = [_ for _ in lista]
print(bucle)
```

- Se usa **list comprehension** para copiar la lista original en `bucle`.
- El resultado es una lista con los mismos elementos.

**Salida:**

```
['platano', 'naranja', 'melon']
```

---

#### 6️⃣ **Uso del guion bajo `_` en un `for`**

```python
numeros = [1, 2, 3, 4, 5]
for _ in numeros:
    print("En estas vueltas no se imprime el contenido de la lista que estamos recorriendo")
```

- `_` se usa cuando no nos interesa el valor de la variable.
- Solo se ejecuta el `print()` sin importar los valores de `numeros`.

**Salida (5 veces):**

```
En estas vueltas no se imprime el contenido de la lista que estamos recorriendo
...
```

---

#### 7️⃣ **Ejecutar código 100 veces con `range`**

```python
for _ in range(1, 100):
    print("Código que se ejecuta 100 veces")
```

- `range(1, 100)` genera números de `1` a `99` (excluye `100`).
- `_` indica que no se usa el valor de la iteración.
- Se imprime el mensaje 99 veces.

---

#### 8️⃣ **Uso de `range` con una variable**

```python
for numero in range(1, 100):
    print("En cada vuelta la variable numero valdrá:", numero)
```

- `numero` toma valores de `1` a `99`.
- Se imprime el valor en cada iteración.

**Salida parcial:**

```
En cada vuelta la variable numero valdrá: 1
En cada vuelta la variable numero valdrá: 2
...
```

---

Estos ejemplos muestran cómo funciona el `for` en Python para recorrer distintos tipos de datos. 🚀




[[7- Los Operadores Lógicos]]
[[8- Sentencias Condicionales]]
[[10- Bucle WHILE]]

---

## Navegación

- ⬆️ Carpeta: [[_1- Conceptos Básicos de Python|1- Conceptos Básicos de Python]]
- ⬅️ Anterior: [[8- Sentencias Condicionales]]
- ➡️ Siguiente: [[10- Bucle WHILE]]
