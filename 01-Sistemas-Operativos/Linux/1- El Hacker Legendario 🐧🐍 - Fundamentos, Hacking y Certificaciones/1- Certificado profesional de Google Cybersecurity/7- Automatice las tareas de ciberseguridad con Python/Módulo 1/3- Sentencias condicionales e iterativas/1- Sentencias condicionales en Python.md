
## 🧠 **Tema: Sentencias Condicionales en Python**

### 🔹 **Concepto de Automatización**

La **automatización** permite reducir el trabajo manual haciendo que las computadoras ejecuten tareas repetitivas.  
En ciberseguridad, esto es útil para:

- Bloquear usuarios tras múltiples intentos fallidos.
    
- Analizar registros automáticamente.
    
- Activar alertas según condiciones específicas.
    

---

### 🔹 **Qué es una Sentencia Condicional**

Una **sentencia condicional** evalúa una condición y ejecuta código dependiendo de si el resultado es **Verdadero (`True`)** o **Falso (`False`)**.

Se construye con la palabra clave **`if`**, seguida de la **condición**, y finalizada con dos puntos `:`.  
La acción que debe ejecutarse se coloca **indentada** (con sangría).

#### 🧩 Ejemplo:

```python
failed_attempts = 6

if failed_attempts > 5:
    print("Cuenta bloqueada")
```

📤 **Salida:**

```
Cuenta bloqueada
```

---

### 🔹 **Partes de una Sentencia If**

- **Cabecera:** contiene la condición (`if failed_attempts > 5:`).
    
- **Cuerpo:** contiene las acciones que se ejecutan si la condición es verdadera.
    

---

### 🔹 **Operadores de Comparación Comunes**

|Operador|Significado|Ejemplo|Resultado|
|---|---|---|---|
|`>`|Mayor que|`5 > 3`|`True`|
|`<`|Menor que|`2 < 1`|`False`|
|`==`|Igual a|`"OS2" == "OS2"`|`True`|
|`!=`|No igual a|`5 != 7`|`True`|
|`>=`|Mayor o igual que|`10 >= 10`|`True`|
|`<=`|Menor o igual que|`4 <= 3`|`False`|

---

### 🔹 **Uso del Doble Igual (`==`)**

El operador **`==`** **no asigna valores**, sino que **compara si dos objetos son iguales**.  
Devuelve un **valor booleano (`True` o `False`)**.

#### Ejemplo:

```python
operating_system = "OS 2"

if operating_system == "OS 2":
    print("Se necesitan actualizaciones")
```

📤 **Salida:**

```
Se necesitan actualizaciones
```

---

### 🔹 **Uso del Operador “No Igual” (`!=`)**

Evalúa si dos valores **son diferentes**.  
Devuelve `True` si **no coinciden**.

#### Ejemplo:

```python
user = "admin"

if user != "root":
    print("Acceso restringido")
```

📤 **Salida:**

```
Acceso restringido
```

---

### 🔹 **La Palabra Clave `else`**

Se usa junto con `if` para ejecutar **una acción alternativa** cuando la condición del `if` es **falsa**.

#### Ejemplo:

```python
operating_system = "OS 3"

if operating_system == "OS 2":
    print("Se necesitan actualizaciones")
else:
    print("No se necesitan actualizaciones")
```

📤 **Salida:**

```
No se necesitan actualizaciones
```

---

### 🔹 **Buenas Prácticas**

- Usa **sangría (indentación)** para indicar qué líneas pertenecen al bloque `if` o `else`.
    
- Coloca **dos puntos (`:`)** al final de la condición.
    
- Nombra las variables de forma **clara y significativa** (por ejemplo, `failed_attempts`, `login_status`).
    

---

### 🧩 **Resumen General**

|Concepto|Descripción|
|---|---|
|**`if`**|Evalúa una condición. Ejecuta código si es verdadera.|
|**`else`**|Se ejecuta solo si el `if` anterior es falso.|
|**`==`**|Compara igualdad entre dos valores.|
|**`!=`**|Evalúa desigualdad entre dos valores.|
|**Indentación**|Indica qué líneas pertenecen al bloque condicional.|

---

## Pregunta

¿Qué operador puede utilizarse en una condición para evaluar si el valor contenido en una variable login_attempts coincide con un valor de 5?

!=

=

>=

==

Correcto

El operador == evalúa si dos objetos coinciden y puede utilizarse en una condición para evaluar si el valor contenido en una variable de login_attempts coincide con un valor de 5. Esta condición puede colocarse en la cabecera de una sentencia if como if login_attempts == 5.

✅ Correcto
El operador **`==`** se usa en Python para **comparar igualdad** entre dos valores.

### 💡 Explicación:

Cuando escribes una condición como:

```python
if login_attempts == 5:
    print("Demasiados intentos")
```

Python evalúa si el valor contenido en la variable `login_attempts` **es igual a** `5`.

- Si **es igual**, devuelve `True` y ejecuta el bloque de código indentado.
    
- Si **no es igual**, devuelve `False` y salta a la siguiente instrucción (por ejemplo, un `else`).
    

---

### ⚠️ Diferencia con otros operadores:

|Operador|Función|Ejemplo|Resultado|
|---|---|---|---|
|`=`|Asigna un valor|`x = 5`|Guarda el valor 5 en `x`|
|`==`|Compara igualdad|`x == 5`|Devuelve `True` si `x` es 5|
|`!=`|Compara desigualdad|`x != 5`|Devuelve `True` si `x` **no** es 5|
|`>=`|Mayor o igual que|`x >= 5`|Devuelve `True` si `x` ≥ 5|

Así que, si en tu programa quieres verificar que un usuario ha alcanzado **exactamente cinco intentos de inicio de sesión**, la forma correcta de hacerlo es:

```python
if login_attempts == 5:
    print("Cuenta bloqueada")
```