
# 🧠 Variables en Python

En Python, las **variables** funcionan como **recipientes que almacenan datos**.  
Así como en la cocina usamos recipientes que pueden contener arroz o pasta en diferentes momentos, en programación una variable puede almacenar distintos valores y tipos de datos a lo largo del código.

---

## 📦 ¿Qué es una variable?

Una **variable** es un **nombre simbólico que representa un valor almacenado en memoria**.  
Sirve para guardar información que puede ser reutilizada, modificada o analizada posteriormente.

La estructura básica para crear una variable es:

```python
nombre_variable = valor
```

Ejemplo:

```python
ID_dispositivo = "h32rb17"
```

Aquí, `ID_dispositivo` es el **nombre de la variable**, el signo `=` realiza la **asignación**, y `"h32rb17"` es el **valor** que se almacena (una cadena).

---

## 🧱 Asignación y uso de variables

Después de crear una variable, puedes **usarla** escribiendo su nombre en cualquier parte del código.  
Esto se conoce como **“llamar a la variable”**.

```python
# Crear variable
ID_dispositivo = "h32rb17"

# Imprimir valor almacenado
print(ID_dispositivo)
```

🔹 Salida:

```
h32rb17
```

> 📌 Importante:  
> Cuando llamas una variable dentro de `print()`, **no se colocan comillas**, porque las comillas indicarían una cadena literal, no una variable.

---

## 🔍 Diferencia entre imprimir una cadena y una variable

```python
ID_dispositivo = "h32rb17"

print(ID_dispositivo)    # Muestra el valor almacenado
print("m50pi31")         # Muestra la cadena literal
```

📤 **Salida:**

```
h32rb17
m50pi31
```

- La primera línea imprime el contenido de la variable.
    
- La segunda imprime directamente la cadena.
    

---

## ⚙️ ¿Por qué usar variables?

Las variables sirven para:

- Simplificar el código y hacerlo más **legible**.
    
- **Reutilizar** valores sin escribirlos repetidamente.
    
- **Guardar datos dinámicos**, como resultados de operaciones o entradas del usuario.
    
- **Automatizar procesos** sin depender de valores fijos.
    

Ejemplo práctico:

```python
usuario = "admin"
print("El usuario actual es:", usuario)
```

---

## 🔎 Comprobar el tipo de dato de una variable

En Python, puedes usar la función `type()` para conocer el tipo de dato almacenado en una variable:

```python
ID_dispositivo = "h32rb17"
data_type = type(ID_dispositivo)
print(data_type)
```

📤 **Salida:**

```
<class 'str'>
```

✅ Python confirma que el tipo de dato es una **cadena (string)**.

---

## 🚨 Errores de tipo (TypeError)

Un **TypeError** ocurre cuando intentas usar **tipos de datos incompatibles** en una misma operación.  
Por ejemplo, intentar sumar una cadena con un número:

```python
ID_dispositivo = "h32rb17"
numero = 7

print(ID_dispositivo + numero)
```

📤 **Salida:**

```
TypeError: can only concatenate str (not "int") to str
```

👉 Python no puede sumar una cadena (`str`) con un entero (`int`).  
Solo puedes sumar **dos cadenas** o **dos números**.

---

## 🔄 Reasignación de variables

El contenido de una variable **puede cambiar** en cualquier momento.  
Esto se llama **reasignación**.

Ejemplo:

```python
device_ID = "h32rb17"
print(device_ID)

device_ID = "n73ab07"
print(device_ID)
```

📤 **Salida:**

```
h32rb17
n73ab07
```

- La primera impresión muestra el valor original.
    
- La segunda muestra el nuevo valor asignado.
    

---

## 🧮 Cambiar el tipo de dato durante la reasignación

También puedes **reasignar una variable con un tipo de dato diferente**:

```python
ID_dispositivo = "h32rb17"
print(type(ID_dispositivo))  # <class 'str'>

ID_dispositivo = 1507
print(type(ID_dispositivo))  # <class 'int'>
```

Esto es útil cuando los valores deben adaptarse según el contexto del código.

---

## 🧩 Resumen

|Concepto|Descripción|Ejemplo|
|---|---|---|
|**Variable**|Contenedor que almacena datos|`x = 10`|
|**Asignación**|Proceso de dar un valor a una variable|`nombre = "Ana"`|
|**Llamar variable**|Usar su nombre para acceder al valor|`print(nombre)`|
|**Función `type()`**|Muestra el tipo de dato almacenado|`type(x)`|
|**Error de tipo**|Incompatibilidad entre tipos de datos|`"texto" + 3`|
|**Reasignación**|Cambiar el valor o tipo de una variable|`x = 5; x = "cinco"`|

---

## 🧠 Conclusión

- Una **variable** es la base de todo programa: almacena información, la transforma y la reutiliza.
    
- **Comprender los tipos de datos** dentro de las variables evita errores.
    
- Las **reasignaciones** permiten que los programas sean flexibles.
    
- Python es un lenguaje dinámico, lo que significa que el tipo de una variable puede cambiar en tiempo de ejecución.
    

---

## 🧠 Pregunta

**¿Cuál de las siguientes líneas de programación asigna a la variable `username` un valor de `"jrafael"`?**

### ✅ Respuesta correcta:

```python
username = "jrafael"
```

---

### 📘 Explicación:

En Python, la **asignación de una variable** se realiza siguiendo esta estructura:

```python
nombre_variable = valor
```

- **`nombre_variable`** → Es el identificador que almacena el valor.
    
- **`=`** → Es el **operador de asignación**, no de igualdad.
    
- **`valor`** → Es el dato que se guarda dentro de la variable (puede ser una cadena, número, lista, etc.).
    

Por ejemplo:

```python
username = "jrafael"
print(username)
```

📤 **Salida:**

```
jrafael
```

---

### ⚠️ Errores comunes:

|Código incorrecto|Motivo|
|---|---|
|`"jrafael" = username`|❌ No se puede asignar un valor a una cadena literal.|
|`print(username, "jrafael")`|❌ Solo imprime dos valores, no asigna nada.|
|`print("jrafael", username)`|❌ También imprime, pero no realiza asignación.|

---

### 💡 En resumen:

> En Python, **la variable siempre va a la izquierda del signo igual**, y **el valor a la derecha**.  
> Esta sintaxis permite almacenar datos que luego pueden ser reutilizados, modificados o analizados en el programa.

---