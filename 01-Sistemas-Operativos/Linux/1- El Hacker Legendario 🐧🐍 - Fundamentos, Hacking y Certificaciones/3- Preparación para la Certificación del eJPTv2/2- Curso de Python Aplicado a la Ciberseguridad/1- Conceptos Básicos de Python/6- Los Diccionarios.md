---
tipo: teoria
tags: [diccionarios, ejptv2, el-hacker-legendario, estructuras-de-datos, manejo-de-errores, pentesting, programacion, python]
actualizado: 2026-05-28
---

# Los Diccionarios

---
### **Código 1**

```python
diccionario = {'Nombre' : 'Jeremy', 'Edad' : 21, 'Profesion' : 'Estudiante'}
print(diccionario['Nombre'])
```

#### **Explicación:**

1. Se define un diccionario llamado `diccionario` con tres claves: `'Nombre'`, `'Edad'` y `'Profesion'`, con sus respectivos valores.
2. Se usa `print(diccionario['Nombre'])` para imprimir el valor asociado a la clave `'Nombre'`, que es `"Jeremy"`.

#### **Salida esperada:**

```
Jeremy
```

---

### **Código 2**

```python
diccionario = {'Nombre' : 'Jeremy', 'Edad' : 21, 'Profesion' : 'Estudiante'}
print(diccionario['Nombre'])
del diccionario['Profesion']
print(diccionario['Profesion'])
```

#### **Explicación:**

1. Se crea el diccionario con los mismos valores que antes.
2. Se imprime el valor de `'Nombre'`, que es `"Jeremy"`.
3. Se usa `del diccionario['Profesion']` para eliminar la clave `'Profesion'` y su valor.
4. Luego, se intenta imprimir `diccionario['Profesion']`, pero esta clave ya no existe en el diccionario.

#### **Error esperado:**

Dado que `'Profesion'` fue eliminada, al intentar acceder a `diccionario['Profesion']`, se genera un error:

```
Jeremy
Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
KeyError: 'Profesion'
```

🔴 **Error:** `KeyError: 'Profesion'`  
💡 **Solución:** Antes de acceder a una clave eliminada, se recomienda verificar si existe con `'Profesion' in diccionario`.

---

### **Código 3**

```python
diccionario = {'Nombre' : 'Jeremy', 'Edad' : 21, 'Profesion' : 'Estudiante'}
print(diccionario['Nombre'])
# del diccionario['Profesion']
print(diccionario['Profesion'])
```

#### **Explicación:**

1. Se crea el diccionario.
2. Se imprime `diccionario['Nombre']`, que es `"Jeremy"`.
3. La línea `del diccionario['Profesion']` está comentada, por lo que `'Profesion'` no se elimina.
4. Se imprime `diccionario['Profesion']`, que sigue existiendo en el diccionario.

#### **Salida esperada:**

```
Jeremy
Estudiante
```

✅ **No hay errores aquí porque `'Profesion'` sigue existiendo.**

---

### **Código 4**

```python
diccionario = {'Nombre' : 'Jeremy', 'Edad' : 21, 'Profesion' : 'Estudiante'}

print(diccionario['Nombre'])

# del diccionario['Profesion']

# print(diccionario['Profesion'])

print('Profesion' in diccionario)
```

#### **Explicación:**

1. Se define el diccionario con `'Nombre'`, `'Edad'` y `'Profesion'`.
2. Se imprime `diccionario['Nombre']`, que es `"Jeremy"`.
3. La línea `del diccionario['Profesion']` está comentada, por lo que `'Profesion'` sigue existiendo.
4. Se usa `'Profesion' in diccionario`, que devuelve `True` si la clave `'Profesion'` está en el diccionario.

#### **Salida esperada:**

```
Jeremy
True
```

✅ **El diccionario mantiene la clave `'Profesion'`, por lo que `'Profesion' in diccionario` devuelve `True`.**

---

### **Código 5**

```python
diccionario = {'Nombre' : 'Jeremy', 'Edad' : 21, 'Profesion' : 'Estudiante'}

print(diccionario['Nombre'])

# del diccionario['Profesion']

# print(diccionario['Profesion'])

print('h' in diccionario)
```

#### **Explicación:**

1. Se define el diccionario con `'Nombre'`, `'Edad'` y `'Profesion'`.
2. Se imprime `diccionario['Nombre']`, que es `"Jeremy"`.
3. La línea `del diccionario['Profesion']` está comentada, por lo que `'Profesion'` sigue existiendo.
4. Se evalúa `'h' in diccionario`.
    - `'h'` no es una clave en el diccionario, por lo que devuelve `False`.

#### **Salida esperada:**

```
Jeremy
False
```

✅ **El diccionario no tiene la clave `'h'`, por lo que `'h' in diccionario` devuelve `False`.**

---

### **Resumen de aprendizajes**

1. **Acceder a valores:** Se usa `diccionario['clave']` para obtener un valor. Si la clave no existe, ocurre un `KeyError`.
2. **Eliminar claves:** Se usa `del diccionario['clave']`, pero hay que asegurarse de que la clave existe antes de intentar acceder a ella nuevamente.
3. **Verificar existencia:** Se usa `'clave' in diccionario` para comprobar si una clave está en el diccionario antes de acceder a ella.

📌 **Recomendación:**  
Para evitar errores al acceder a claves inexistentes, se puede usar `.get()` en lugar de `diccionario['clave']`:

```python
print(diccionario.get('Profesion', 'Clave no encontrada'))
```

Esto imprimirá el valor si la clave existe o `"Clave no encontrada"` si no existe.






[[2- Las Listas]]
[[3- Las Tuplas]]
[[5- Entrada de Información por parte del Usuario (Argumentos)]]

---

## Navegación

- ⬆️ Carpeta: [[_1- Conceptos Básicos de Python|1- Conceptos Básicos de Python]]
- ⬅️ Anterior: [[5- Entrada de Información por parte del Usuario (Argumentos)]]
- ➡️ Siguiente: [[7- Los Operadores Lógicos]]
