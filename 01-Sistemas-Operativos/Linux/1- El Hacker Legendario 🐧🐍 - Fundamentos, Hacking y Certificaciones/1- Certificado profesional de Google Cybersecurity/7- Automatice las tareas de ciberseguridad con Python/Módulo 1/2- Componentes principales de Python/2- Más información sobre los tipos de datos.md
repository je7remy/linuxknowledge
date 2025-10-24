
# 🧠 Tipos de Datos en Python (Versión Extendida)

Un **tipo de dato** es una **categoría** para un tipo particular de elemento de datos.  
En Python, cada tipo de dato tiene una **función específica** y una **sintaxis propia**.  
Los tipos de datos principales que se estudian en este curso son:

- **Cadena (String)**
    
- **Lista (List)**
    
- **Entero (Integer)**
    
- **Flotante (Float)**
    
- **Booleana (Boolean)**
    

Además, existen **otros tres tipos adicionales**: **Tupla (Tuple)**, **Diccionario (Dictionary)** y **Conjunto (Set)**.

---

## 📘 Cadena (String)

Los **Datos de cadena** son datos formados por una **secuencia ordenada de caracteres**.  
Los caracteres pueden incluir **letras, números, símbolos y espacios**, y **deben ir entre comillas**.

Ejemplos válidos:

```python
"updates needed"
"20%"
"5.0"
"35"
"**/**/**"
""
```

> 💡 La última, `""`, se llama **cadena vacía** porque no contiene ningún valor.

También se pueden usar comillas simples:

```python
print('updates needed')
```

✅ **Recomendación:**  
Elige un tipo de comillas (simples o dobles) y úsalo de forma coherente para mantener la **legibilidad del código**.

---

## 📋 Lista (List)

Los **Datos de lista** son una **colección secuencial de elementos**.  
Cada elemento puede ser de **cualquier tipo de dato** (cadena, entero, booleano, etc.), y se colocan **entre corchetes** `[ ]`, separados por **comas**.

Ejemplos:

```python
[12, 36, 54, 1, 7]
["eraab", "arusso", "drosas"]
[True, False, True, True]
[15, "approved", True, 45.5, False]
[]
```

> 💡 El último ejemplo (`[]`) se llama **lista vacía**.

Podemos imprimir una lista con `print()`:

```python
print([12, 36, 54, 1, 7])
```

Resultado:

```
[12, 36, 54, 1, 7]
```

---

## 🔢 Entero (Integer)

Los **Datos enteros** son números **sin punto decimal**.  
Pueden ser positivos, negativos o cero.

Ejemplos:

```
-100
-12
-1
0
1
20
500
```

Ejemplo con `print()`:

```python
print(5)      # Muestra 5
print(5 + 2)  # Muestra 7
```

✅ Puedes realizar operaciones como suma, resta, multiplicación o división.

---

## 💧 Flotante (Float)

Los **Datos flotantes** son números **con punto decimal**.  
Se usan para representar valores con fracciones o decimales.

Ejemplos:

```
-2.2
-1.34
0.0
0.34
```

Ejemplo de cálculo:

```python
print(1.2 + 2.8)  # Resultado: 4.0
```

📌 **Importante:**

- La **división normal** (`/`) devuelve un **resultado flotante**:
    
    ```python
    print(1 / 4)     # 0.25
    print(1.0 / 4.0) # 0.25
    ```
    
- La **división entera** (`//`) redondea **hacia abajo**:
    
    ```python
    print(1 // 4)     # 0
    print(1.0 // 4.0) # 0.0
    ```
    

---

## ⚙️ Booleana (Boolean)

Los **Datos booleanos** solo pueden tener **dos valores posibles**:  
`True` (verdadero) o `False` (falso).

Ejemplos:

```python
print(True)
print(False)
print(9 > 10)  # False
print(10 > 5)  # True
```

✅ **No deben ir entre comillas.**

Los booleanos se usan para **comparaciones, condiciones y lógica** dentro de programas.

---

## 🧩 Tipos de Datos Adicionales

Además de los cinco anteriores, Python ofrece otros tres tipos comunes:

---

### 🧱 Tupla (Tuple)

Una **tupla** es una colección **inmutable**, es decir, **no se puede modificar** una vez creada.  
A diferencia de las listas, las tuplas usan **paréntesis `( )`** en lugar de corchetes `[ ]`.

Ejemplos:

```python
("wjaffrey", "arutley", "dkot")
(46, 2, 13, 2, 8, 0, 0)
(True, False, True, True)
("wjaffrey", 13, True)
```

> 💡 Las tuplas son **más eficientes en memoria** que las listas, por lo que se recomiendan cuando los datos **no deben cambiar**, como identificadores o configuraciones fijas.

---

### 🗝️ Diccionario (Dictionary)

Un **diccionario** es una colección de **pares clave-valor**.  
Cada **clave** está asociada a un **valor**, y se separan por **dos puntos `:`**.  
Los pares se encierran entre **llaves `{}`** y se separan con **comas**.

Ejemplo:

```python
{
  1: "East",
  2: "West",
  3: "North",
  4: "South"
}
```

✅ Los diccionarios son útiles para **asociar información de forma predecible**, por ejemplo, asignar nombres, direcciones o identificadores a valores.

---

### 🧮 Conjunto (Set)

Un **conjunto** es una **colección desordenada de valores únicos** (sin duplicados).  
Se define entre **llaves `{}`** y sus elementos se separan por comas.

Ejemplo:

```python
{"jlanksy", "drosas", "nmason"}
```

Los conjuntos son útiles para operaciones como **comparar listas, eliminar duplicados** o verificar pertenencia.

---

## 🧠 Conclusión

|Tipo de dato|Ejemplo|Características principales|
|---|---|---|
|**Cadena (String)**|`"Hola"`|Texto entre comillas|
|**Lista (List)**|`[1, 2, 3]`|Colección ordenada y editable|
|**Entero (Int)**|`5`|Número sin decimales|
|**Flotante (Float)**|`3.14`|Número con punto decimal|
|**Booleano (Bool)**|`True`, `False`|Lógica binaria|
|**Tupla (Tuple)**|`(1, 2, 3)`|Colección ordenada e inmutable|
|**Diccionario (Dict)**|`{"a": 1}`|Pares clave-valor|
|**Conjunto (Set)**|`{"a", "b"}`|Colección única sin orden|

---

### 🔐 Clave profesional

Para un analista de seguridad, **entender los tipos de datos en Python** permite:

- Manipular información con precisión.
    
- Automatizar tareas de análisis y respuesta.
    
- Estructurar datos correctamente para scripts y herramientas.
    

Cada tipo de dato tiene un **propósito** y una **sintaxis específica**.  
Dominar estos fundamentos es esencial para avanzar en ciberseguridad y programación defensiva.

---

