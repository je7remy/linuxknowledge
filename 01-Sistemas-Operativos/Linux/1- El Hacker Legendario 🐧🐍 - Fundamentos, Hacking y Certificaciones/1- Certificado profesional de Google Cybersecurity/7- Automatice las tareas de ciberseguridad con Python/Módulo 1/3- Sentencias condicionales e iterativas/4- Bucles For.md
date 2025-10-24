
## 🧩 **Tema: Sentencias Iterativas (Bucles en Python)**

### 🔹 **Definición**

Una **sentencia iterativa** es una estructura de control que **repite un bloque de código** varias veces.  
También se conoce como **bucle** o **loop**.

📍 **Propósito:**  
Permitir que la computadora ejecute tareas repetitivas sin intervención humana.

---

### 🔹 **Tipos de Bucles**

En Python existen dos tipos principales de bucles:

1. **Bucle `for`** → Repite el código un número específico de veces o por cada elemento de una secuencia.
    
2. **Bucle `while`** → Repite el código mientras una condición sea verdadera.  
    (Se verá en el próximo tema).
    

---

### 🔹 **Estructura de un Bucle `for`**

Un bucle `for` tiene dos partes:

|Parte|Descripción|
|---|---|
|**Cabecera del bucle**|Contiene la palabra clave `for`, la variable de bucle y la secuencia que se recorrerá, terminando con dos puntos `:`|
|**Cuerpo del bucle**|Son las instrucciones indentadas que se ejecutan en cada iteración.|

---

### 🔹 **Ejemplo básico**

```python
for i in [1, 2, 3, 4]:
    print(i)
```

📤 **Salida:**

```
1
2
3
4
```

📘 _Explicación:_  
La variable `i` toma el valor de cada elemento de la lista uno por uno.  
En cada iteración, se ejecuta el bloque indentado (`print(i)`).

---

### 🔹 **Variables de bucle**

- La variable después de `for` (por ejemplo, `i`) se llama **variable de iteración**.
    
- Solo existe **dentro del bucle** y cambia en cada ciclo.
    
- Puedes usar cualquier nombre (no solo `i`).
    

---

### 🔹 **Uso con la función `range()`**

La función **`range()`** genera una secuencia de números.  
Se usa comúnmente para repetir acciones un número determinado de veces.

📘 **Sintaxis:**

```python
range(inicio, fin)
```

- Comienza desde `inicio` (incluido).
    
- Termina en `fin` (excluido).
    

---

### 🔹 **Ejemplo con `range()`**

```python
for i in range(10):
    print("No se puede conectar al destino")
```

📤 **Salida:**

```
No se puede conectar al destino
No se puede conectar al destino
... (repetido 10 veces)
```

📘 _Explicación:_

- `range(10)` genera los números del 0 al 9.
    
- El bucle se repite **10 veces**.
    

---

### 🔹 **Ejemplo con inicio y fin personalizados**

```python
for i in range(3, 8):
    print(i)
```

📤 **Salida:**

```
3
4
5
6
7
```

---

### 🔹 **Resumen General**

|Concepto|Descripción|
|---|---|
|**Bucle for**|Repite acciones una cantidad definida de veces o por cada elemento de una secuencia.|
|**Función range()**|Genera una secuencia numérica (inicio incluido, fin excluido).|
|**Indentación**|Define el bloque de código que se ejecuta en cada iteración.|
|**Ventaja**|Automatiza tareas repetitivas, evitando escribir código redundante.|

---
