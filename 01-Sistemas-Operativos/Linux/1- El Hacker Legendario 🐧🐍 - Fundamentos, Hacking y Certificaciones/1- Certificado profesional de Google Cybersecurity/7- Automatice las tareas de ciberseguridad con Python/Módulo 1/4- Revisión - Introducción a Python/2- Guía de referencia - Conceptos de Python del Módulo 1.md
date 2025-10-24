
---

### 🧠 Guía de Referencia: Conceptos de Python (Módulo 1)

Esta guía resume la sintaxis y los conceptos clave del Módulo 1 del Certificado de Ciberseguridad de Google.

---

### 📘 Comentarios

Los comentarios son notas que los programadores dejan en el código para explicar su intención.

|**Sintaxis**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`#`**|Inicia una línea que contiene un comentario de Python.|`# Print approved usernames` _(Indica que el código siguiente imprimirá nombres de usuario aprobados.)_|

---

### 📘 Funciones Comunes

Estas son funciones integradas de uso frecuente en Python.

|**Función**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`print()`**|Muestra un objeto especificado en la pantalla.|`print("login success")` _(Muestra la cadena "login success".)_ `print(9 < 7)` _(Evalúa la expresión y muestra el valor booleano `False`.)_|
|**`type()`**|Devuelve el tipo de dato de su entrada.|`print(type(51.1))` _(Devuelve el tipo de dato `float`.)_ `print(type(True))` _(Devuelve el tipo de dato `Boolean`.)_|
|**`range()`**|Genera una secuencia de números.|`range(0, 5, 1)` _(Genera la secuencia: 0, 1, 2, 3, 4.)_ `range(5)` _(Genera la misma secuencia: 0, 1, 2, 3, 4, usando el inicio por defecto (0) y el incremento por defecto (1).)_|

---

### 📘 Sentencias Condicionales

Se utilizan para ejecutar código basado en si una condición es verdadera o falsa.

|**Palabra Clave / Operador**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`if`**|Inicia una sentencia condicional.|`if device_id != "la858zn":` _(Evalúa si `device_id` **no es igual** a "la858zn".)_ `if user in approved_list:` _(Evalúa si el valor de `user` **se encuentra dentro** de `approved_list`.)_|
|**`elif`**|Precede a una condición que solo se evalúa si las condiciones `if` (y `elif` anteriores) son `False`.|`elif status == 500:` _(Si el `if` fue `False`, evalúa si `status` es igual a 500.)_|
|**`else`**|Precede a un bloque de código que solo se ejecuta si _todas_ las condiciones anteriores (`if`/`elif`) son `False`.|`else:` _(Se ejecuta si todas las condiciones anteriores fueron `False`.)_|
|**`and`**|Requiere que _ambas_ condiciones a cada lado sean `True`.|`if username == "bmoreno" and login_attempts < 5:` _(Evalúa a `True` solo si el usuario es "bmoreno" **Y** los intentos son menores a 5.)_|
|**`or`**|Requiere que _al menos una_ de las condiciones a cada lado sea `True`.|`if status == 100 or status == 102:` _(Evalúa a `True` si el `status` es 100 **O** si es 102.)_|
|**`not`**|Niega (invierte) una condición. `True` se vuelve `False` y `False` se vuelve `True`.|`if not account_status == "removed"` _(Evalúa a `True` si `account_status` **no** es igual a "removed".)_|

---

### 📘 Sentencias Iterativas (Bucles)

Se utilizan para ejecutar un bloque de código repetidamente.

|**Palabra Clave**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`for`**|Señala el inicio de un bucle `for`; usado para iterar a través de una secuencia especificada.|`for username in ["bmoreno", "tshah", "elarson"]:` _(Itera a través de la lista de nombres de usuario.)_ `for i in range(10):` _(Itera a través de la secuencia de números del 0 al 9.)_|
|**`while`**|Señala el inicio de un bucle `while`; usado para iterar basándose en que una condición sea `True`.|`while login_attempts < 5:` _(Se repite mientras el valor de `login_attempts` sea menor que 5.)_|
|**`break`**|Se utiliza para salir (romper) permanentemente de un bucle.|_(Se usa dentro de un `if` en un bucle para detenerlo prematuramente.)_|
|**`continue`**|Se utiliza para saltar la iteración actual del bucle y continuar con la siguiente.|_(Se usa dentro de un `if` en un bucle para omitir el resto del código de esa iteración.)_|