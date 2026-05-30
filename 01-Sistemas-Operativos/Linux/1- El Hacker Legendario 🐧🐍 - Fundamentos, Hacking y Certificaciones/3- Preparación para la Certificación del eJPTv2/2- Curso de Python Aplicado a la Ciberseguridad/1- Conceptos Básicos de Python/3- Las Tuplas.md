---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, python, pentesting]
actualizado: 2026-05-28
---

# Las Tuplas

---

#Python #Tuplas #EstructurasDeDatos #Inmutabilidad #Optimización #AprenderPython 🚀

---
### **¿Qué son las tuplas en Python?**

Las **tuplas** en Python son estructuras de datos **ordenadas e inmutables** que pueden contener diferentes tipos de datos. A diferencia de las listas, las tuplas **no pueden ser modificadas** una vez creadas, es decir, no se pueden agregar, eliminar o cambiar elementos después de su creación.

📌 **Características de las tuplas:**  
✅ Se definen con paréntesis `()` en lugar de corchetes `[]`.  
✅ Son más rápidas que las listas para acceder a elementos.  
✅ Se pueden recorrer con bucles e indexar como las listas.  
✅ Se utilizan cuando los datos no deben cambiar.

📌 **Ejemplo de una tupla:**

```python
mi_tupla = ("jeremy", 28, "Informático")
print(mi_tupla[0])  # Acceder al primer elemento
```

---

## **Desarrollo Paso a Paso**

## **Código 1: Intentar agregar un elemento a una tupla**

```python
tuplas = ("jeremy", 21, "informatico")
tuplas.append(6)
```

🚨 **Error esperado:**

```python
AttributeError: 'tuple' object has no attribute 'append'
```

📌 **Explicación:**

1. Se crea una **tupla** `tuplas = ("jeremy", 21, "informatico")`.
2. Se intenta agregar un nuevo elemento con `tuplas.append(6)`.
3. **Error:** Las **tuplas son inmutables**, lo que significa que **no pueden ser modificadas** después de su creación.
4. La función `.append()` **solo funciona con listas**, no con tuplas.

✅ **Solución para agregar un elemento a una tupla**  
Dado que las tuplas no se pueden modificar, la única manera de "agregar" un elemento es crear una nueva tupla combinando la original con un nuevo valor:

```python
tuplas = ("jeremy", 21, "informatico")
tuplas = tuplas + (6,)  # Crear una nueva tupla
print(tuplas)  # ('jeremy', 21, 'informatico', 6)
```

🚨 **Nota importante:** Se usa `(6,)` con una coma para que Python reconozca que es una tupla y no un número entre paréntesis.

---

## **Código 2: Agregar un elemento a una lista**

```python
tuplas = ["jeremy", 21, "informatico"]
tuplas.append(6)
```

✅ **Explicación:**

1. Se crea una **lista** `tuplas = ["jeremy", 21, "informatico"]`.
2. Se usa `tuplas.append(6)`, lo cual es válido porque las listas **sí son mutables**.
3. Ahora la lista contiene:
    
    ```python
    ['jeremy', 21, 'informatico', 6]
    ```
    

📌 **Diferencia clave:**

- **Las listas** permiten agregar elementos dinámicamente con `.append()`.
- **Las tuplas** no pueden modificarse después de su creación.

---

## **Código 3: Intentar modificar un elemento de una tupla**

```python
tuplas = ("jeremy", 21, "informatico")
tuplas[1] = 5
```

🚨 **Error esperado:**

```python
TypeError: 'tuple' object does not support item assignment
```

📌 **Explicación:**

4. Se define una **tupla** `tuplas = ("jeremy", 21, "informatico")`.
5. Se intenta cambiar el segundo elemento `tuplas[1] = 5`.
6. **Error:** Las tuplas son **inmutables**, lo que significa que **no se pueden modificar sus elementos** después de la creación.

✅ **Solución para modificar un valor en una tupla**  
La única forma de "modificar" una tupla es crear una nueva con los valores deseados:

```python
tuplas = ("jeremy", 21, "informatico")
tuplas = (tuplas[0], 5, tuplas[2])  # Crear una nueva tupla con el valor modificado
print(tuplas)  # ('jeremy', 5, 'informatico')
```

---

## **Resumen de los errores y soluciones**

|Código|Error|Explicación|Solución|
|---|---|---|---|
|`tuplas.append(6)` (tupla)|`AttributeError`|No se pueden modificar las tuplas|Crear una nueva tupla con `+ (6,)`|
|`tuplas.append(6)` (lista)|✅ Ninguno|`.append()` solo funciona con listas|Funciona correctamente|
|`tuplas[1] = 5`|`TypeError`|No se pueden modificar elementos de una tupla|Crear una nueva tupla con los valores deseados|

📌 **Conclusión:**

- 🚀 **Las listas son mutables**, lo que permite modificarlas con `.append()`, `.remove()`, etc.
- 🔒 **Las tuplas son inmutables**, por lo que no pueden modificarse después de ser creadas.
- 🛠 **Para modificar o agregar elementos en una tupla, hay que crear una nueva tupla con los cambios deseados.**
- ✅ **Las tuplas son estructuras de datos ordenadas e inmutables.**
- ✅ **No se pueden modificar después de su creación (no se pueden agregar, eliminar o cambiar elementos).**
- ✅ **Se accede a los elementos igual que en las listas (por índices y con índices negativos).**
- 🚨 **Intentar modificar una tupla provoca errores.**

---





[[2- Las Listas]]
[[5- Entrada de Información por parte del Usuario (Argumentos)]]
[[6- Los Diccionarios]]

---

## Navegación

- ⬆️ Carpeta: [[_1- Conceptos Básicos de Python|1- Conceptos Básicos de Python]]
- ⬅️ Anterior: [[2- Las Listas]]
- ➡️ Siguiente: [[4- Entrada de Información por parte del Usuario]]
