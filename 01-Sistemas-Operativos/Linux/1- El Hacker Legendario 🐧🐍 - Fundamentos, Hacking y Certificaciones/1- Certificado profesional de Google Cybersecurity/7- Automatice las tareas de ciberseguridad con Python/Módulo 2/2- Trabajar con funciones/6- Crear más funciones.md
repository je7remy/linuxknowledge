
### 🧠 Tarea 1

...use una función integrada de Python para ordenar la lista. ...pase la llamada a la función... directamente a la función `print()`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `failed_login_list` to the list of the number of failed login attempts per month
failed_login_list = [119, 101, 99, 91, 92, 105, 108, 85, 88, 90, 264, 223]
# Sort `failed_login_list` in ascending numerical order and display the result
print(sorted(failed_login_list))
```

---

### 🧠 Pregunta 1

¿Qué observa en el resultado anterior? ¿Nota algún número atípico que indique un aumento en el número de intentos fallidos de inicio de sesión?

✅ Respuesta correcta:

La salida muestra la lista de números ordenada de menor a mayor:

[85, 88, 90, 91, 92, 99, 101, 105, 108, 119, 223, 264]

Sí, se observan dos números atípicos (outliers) claros: **223** y **264**. La mayoría de los meses tienen entre 85 y 119 intentos fallidos, pero estos dos valores son significativamente más altos, lo que indica un aumento notable en los intentos fallidos de inicio de sesión para esos meses (noviembre y diciembre).

---

### 🧠 Tarea 2

...use la función que devuelve el elemento numérico más grande de una lista. Luego, pase esta función a la función `print()` para mostrar el resultado.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `failed_login_list` to the list of the number of failed login attempts per month
failed_login_list = [119, 101, 99, 91, 92, 105, 108, 85, 88, 90, 264, 223]
# Determine the highest number of failed login attempts from `failed_login_list` and display the result
print(max(failed_login_list))
```

---

### 🧠 Pregunta 2

¿Qué observa en el resultado anterior?

✅ Respuesta correcta:

La salida es 264. Esta es la cifra más alta en la lista, que corresponde al valor atípico más grande que identificamos en la Tarea 1.

---

### 🧠 Tarea 3

...defina una función llamada `analyze_logins()` que tome dos parámetros, `username` y `current_day_logins`.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `analyze_logins()` that takes in two parameters, `username` and `current_day_logins`
def analyze_logins(username, current_day_logins):
    # Display a message about how many login attempts the user has made that day
    print("Current day login total for", username, "is", current_day_logins)
```

---

### 🧠 Tarea 4

...llame a `analyze_logins()` con los argumentos `"ejones"` y `9`.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `analyze_logins()` that takes in two parameters, `username` and `current_day_logins`
def analyze_logins(username, current_day_logins):
    # Display a message about how many login attempts the user has made that day
    print("Current day login total for", username, "is", current_day_logins)
# Call `analyze_logins()`
analyze_logins("ejones", 9)
```

---

### 🧠 Pregunta 3

¿Qué muestra esta función? ¿Variaría el resultado para diferentes usuarios?

✅ Respuesta correcta:

La función muestra: "Current day login total for ejones is 9".

Sí, el resultado variaría. La función está diseñada para ser flexible. Los **parámetros** (`username` y `current_day_logins`) actúan como marcadores de posición. Si la llamáramos con diferentes **argumentos** (ej. `analyze_logins("asmith", 3)`), la salida cambiaría a `"Current day login total for asmith is 3"`.

---

### 🧠 Tarea 5

...agregue un parámetro llamado `average_day_logins`. ...llame a la función con... un tercer argumento de `3`.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `analyze_logins()` that takes in three parameters, `username`, `current_day_logins`, and `average_day_logins`
def analyze_logins(username, current_day_logins, average_day_logins):
    # Display a message about how many login attempts the user has made that day
    print("Current day login total for", username, "is", current_day_logins)
    # Display a message about average number of login attempts the user has made that day
    print("Average logins per day for", username, "is", average_day_logins)
# Call `analyze_logins()`
analyze_logins("ejones", 9, 3)
```

---

### 🧠 Tarea 6

...calcule la proporción... almacénela en `login_ratio`. ...llame a la función...

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `analyze_logins()` that takes in three parameters, `username`, `current_day_logins`, and `average_day_logins`
def analyze_logins(username, current_day_logins, average_day_logins):
    # Display a message about how many login attempts the user has made that day
    print("Current day login total for", username, "is", current_day_logins)
    # Display a message about average number of login attempts the user has made that day
    print("Average logins per day for", username, "is", average_day_logins)
    # Calculate the ratio of the logins made on the current day to the logins made on an average day, storing in a variable named `login_ratio`
    login_ratio = current_day_logins / average_day_logins
    # Display a message about the ratio
    print(username, "logged in", login_ratio, "times as much as they do on an average day.")
# Call `analyze_logins()`
analyze_logins("ejones", 9, 3)
```

---

### 🧠 Pregunta 4

¿Qué muestra esta versión de la función `analyze_logins()`? ¿Variaría el resultado para diferentes usuarios?

✅ Respuesta correcta:

Muestra tres líneas de texto. Basado en la llamada analyze_logins("ejones", 9, 3), la salida es:

```
Current day login total for ejones is 9
Average logins per day for ejones is 3
ejones logged in 3.0 times as much as they do on an average day.
```

Sí, el resultado variaría. Si los argumentos fueran `("asmith", 10, 2)`, el ratio calculado sería `5.0` y todos los mensajes se actualizarían en consecuencia.

---

### 🧠 Tarea 7

...agregue una sentencia `return`... para devolver el `login_ratio`. ...almacene el resultado en `login_analysis`.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `analyze_logins()` that takes in three parameters, `username`, `current_day_logins`, and `average_day_logins`
def analyze_logins(username, current_day_logins, average_day_logins):
    # Display a message about how many login attempts the user has made that day
    print("Current day login total for", username, "is", current_day_logins)
    # Display a message about average number of login attempts the user has made that day
    print("Average logins per day for", username, "is", average_day_logins)
    # Calculate the ratio of the logins made on the current day to the logins made on an average day, storing in a variable named `login_ratio`
    login_ratio = current_day_logins / average_day_logins
    # Return the ratio
    return login_ratio
# Call `analyze_logins() and store the output in a variable named `login_analysis`
login_analysis = analyze_logins("ejones", 9, 3)
# Display a message about the `login_analysis`
print("ejones", "logged in", login_analysis, "times as much as they do on an average day.")
```

---

### 🧠 Pregunta 5

¿Cómo se compara esta versión de la función `analyze_logins()` con las anteriores?

✅ Respuesta correcta:

Esta versión es más potente. Las versiones anteriores solo podían imprimir información en la pantalla. Esta versión hace lo mismo (imprime los dos primeros mensajes), pero además devuelve (retorna) el valor calculado (login_ratio) usando return.

Esto nos permite capturar ese valor (`3.0`) en una nueva variable (`login_analysis`) fuera de la función. Ahora podemos usar ese valor para tomar decisiones, como en sentencias condicionales.

---

### 🧠 Tarea 8

...use el valor de `login_analysis` en una sentencia condicional... si es mayor o igual a `3`.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `analyze_logins()` that takes in three parameters, `username`, `current_day_logins`, and `average_day_logins`
def analyze_logins(username, current_day_logins, average_day_logins):
    # Display a message about how many login attempts the user has made that day
    print("Current day login total for", username, "is", current_day_logins)
    # Display a message about average number of login attempts the user has made that day
    print("Average logins per day for", username, "is", average_day_logins)
    # Calculate the ratio of the logins made on the current day to the logins made on an average day, storing in a variable named `login_ratio`
    login_ratio = current_day_logins / average_day_logins
    # Return the ratio
    return login_ratio
# Call `analyze_logins() and store the output in a variable named `login_analysis`
login_analysis = analyze_logins("ejones", 9, 3)
# Conditional statement that displays an alert about the login activity if it's more than normal
if login_analysis >= 3:
    print("Alert! This account has more login activity than normal.")
```

---

### 🧠 Conclusión

¿Cuáles son sus principales conclusiones de este laboratorio?

✅ **Conclusiones clave:**

- **Funciones Integradas:** Python ofrece funciones listas para usar que simplifican tareas comunes. `sorted()` es útil para ordenar listas (lo que ayuda a identificar rangos) y `max()` es útil para encontrar valores atípicos.
    
- **Definición de Funciones (`def`):** Las funciones definidas por el usuario (`def`) nos permiten agrupar código reutilizable.
    
- **Parámetros vs. Argumentos:** Los parámetros son los marcadores de posición en la _definición_ de la función (ej. `username`), mientras que los argumentos son los valores reales pasados durante la _llamada_ a la función (ej. `"ejones"`).
    
- **`print` vs. `return`:** `print()` solo muestra información al usuario. `return` **envía un valor** de vuelta desde la función, permitiendo que ese valor sea almacenado en una variable y utilizado para tomar decisiones lógicas (como en una sentencia `if`).