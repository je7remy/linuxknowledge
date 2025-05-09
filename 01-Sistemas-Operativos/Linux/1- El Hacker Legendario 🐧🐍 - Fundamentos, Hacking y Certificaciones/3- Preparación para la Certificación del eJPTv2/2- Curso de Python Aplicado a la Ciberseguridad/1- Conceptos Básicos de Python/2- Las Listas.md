
---

#Python #Listas #EstructurasDeDatos #ManipulaciónDeListas #Programación #AprenderPython 🚀

---
Las listas en Python son estructuras de datos ordenadas y mutables que pueden contener elementos de diferentes tipos, como cadenas, enteros y otros objetos. 

---

### Paso 1: Crear una lista y acceder a un elemento específico

```python
listas = ["jeremy", 28, "Informatico"]
print(listas[0])
```

📌 **Explicación**: Se crea una lista llamada `listas` con tres elementos y se imprime el primer elemento (`listas[0]`), que es `"jeremy"`.

---

### Paso 2: Acceder al segundo elemento

```python
listas = ["jeremy", 28, "Informatico"]
print(listas[1])
```

📌 **Explicación**: Se accede al segundo elemento (`listas[1]`), que es `28`.

---

### Paso 3: Acceder al tercer elemento

```python
listas = ["jeremy", 28, "Informatico"]
print(listas[2])
```

📌 **Explicación**: Se accede al tercer elemento (`listas[2]`), que es `"Informatico"`.

---

### Paso 4: Acceder al último elemento usando índice negativo

```python
listas = ["jeremy", 28, "Informatico"]
print(listas[-1])
```

📌 **Explicación**: Se accede al último elemento de la lista utilizando `listas[-1]`, que en este caso es `"Informatico"`.

---

### Paso 5: Obtener la longitud de la lista

```python
print(len(listas))
```

📌 **Explicación**: La función `len(listas)` devuelve el número de elementos en la lista, que en este caso es `3`.

---

### Paso 6: Imprimir el tercer elemento con un mensaje

```python
listas = ["jeremy", 28, "Informatico"]
print("El tercer elemento de la lista es:", listas[2])
```

📌 **Explicación**: Se imprime el tercer elemento con un mensaje descriptivo.

---

### Paso 7: Intentar acceder a un elemento eliminado

```python
listas = ["jeremy", 28, "Informatico"]
print("El tercer elemento de la lista es:", listas[2])
del listas[2]  # Elimina el tercer elemento
print("El tercer elemento de la lista es:", listas[2])
```

📌 **Explicación**:

1. Se imprime el tercer elemento (`listas[2]`), que es `"Informatico"`.
2. Se elimina ese elemento con `del listas[2]`.
3. Luego, se intenta acceder nuevamente a `listas[2]`, pero ahora la lista solo tiene dos elementos: `["jeremy", 28]`.
4. Esto provoca un error `IndexError: list index out of range`, ya que `listas[2]` ya no existe.

---

### Conclusión:

- Las listas son mutables, lo que significa que pueden cambiar después de su creación.
- Los índices comienzan desde `0`.
- Se puede acceder al último elemento con `-1`.
- Al eliminar un elemento, los índices de los elementos posteriores cambian, lo que puede causar errores si se intenta acceder a índices que ya no existen.

---

📌 **Corrección del último bloque para evitar el error:**

```python
listas = ["jeremy", 28, "Informatico"]
print("El tercer elemento de la lista es:", listas[2])
del listas[2]
if len(listas) > 2:
    print("El tercer elemento de la lista es:", listas[2])
else:
    print("El tercer elemento ya no existe en la lista.")
```

✅ **Esto evita el error `IndexError` al verificar si el índice aún existe antes de acceder a él.**

---




[[3- Las Tuplas]]
[[5- Entrada de Información por parte del Usuario (Argumentos)]]
[[6- Los Diccionarios]]