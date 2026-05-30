---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Actividad - Trabajar con cadenas en Python

### 🧠 Tarea 1

...dado un `employee_id` numérico de cuatro dígitos. Conviértelo a un formato de cadena y almacena el resultado en la misma variable.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `employee_id` to a four digit number as an initial value
employee_id = 4186

# Display the data type of `employee_id`
print(type(employee_id))

# Reassign `employee_id` to the same value but in the form of a string
employee_id = str(employee_id)

# Display the data type of `employee_id` now
print(type(employee_id))
```

---

### 🧠 Pregunta 1

¿Qué observas sobre el tipo de dato de `employee_id` la primera vez que se muestra? ¿Qué observas sobre el tipo de dato de `employee_id` la segunda vez que se muestra (después de reasignar la variable)?

✅ **Respuesta correcta:**

- La primera vez, la salida es `<class 'int'>`, lo que indica que la variable es un **entero** (un número).
    
- La segunda vez, la salida es `<class 'str'>`, lo que indica que la variable es una **cadena** (texto).
    

📘 Explicación:

La función str() se utilizó exitosamente para reasignar la variable, convirtiendo el valor numérico 4186 en el valor de cadena "4186".

---

### 🧠 Tarea 2

...escribe una sentencia condicional que muestre un mensaje si la longitud del `employee_id` es menor de cinco dígitos.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `employee_id` to a four digit number as an initial value
employee_id = 4186

# Reassign `employee_id` to the same value but in the form of a string
employee_id = str(employee_id)

# Conditional statement that displays a message if the length of `employee_id` is less than five digits
if len(employee_id) < 5:
    print("This employee ID has less than five digits. It does not meet length requirements.")
```

---

### 🧠 Tarea 3

...si un ID de empleado tiene solo cuatro dígitos, usa la concatenación para... reasignar `employee_id` concatenando `"E"` al frente... Luego, muestra el `employee_id`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `employee_id` to a four digit number as an initial value
employee_id = 4186

# Reassign `employee_id` to the same value but in the form of a string
employee_id = str(employee_id)

# Display the `employee_id` as it currently stands
print(employee_id)

# Conditional statement that updates the `employee_id` if its length is less than 5 digits
if len(employee_id) < 5:
    employee_id = "E" + employee_id
    
# Display the `employee_id` after the update
print(employee_id)
```

---

### 🧠 Tarea 4

...extrae el cuarto carácter del `device_id` y muéstralo.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `device_id` to a string that contains alphanumeric characters
device_id = "r262c36"

# Extract the fourth character in `device_id` and display it
print(device_id[3])
```

📘 Explicación:

En Python, la indexación comienza en 0. Por lo tanto, el primer carácter está en el índice 0, el segundo en el 1, el tercero en el 2 y el cuarto carácter está en el índice 3.

---

### 🧠 Tarea 5

...extrae los caracteres del primero al tercero en el `device_id`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `device_id` to a string that contains alphanumeric characters
device_id = "r262c36"

# Extract the first through the third characters in `device_id` and display the result
print(device_id[0:3])
```

📘 Explicación:

El corte (slicing) [0:3] funciona así:

- `0`: Inicia en el índice 0 (el primer carácter).
    
- `3`: Termina _antes_ del índice 3 (es decir, incluye los índices 0, 1 y 2).
    

---

### 🧠 Tarea 6

...extrae y muestra el protocolo de la URL y los caracteres `://` que le siguen...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `url` to a specific URL
url = "https://exampleURL1.com"

# Extract the protocol of `url` along with the syntax following it, display the result
print(url[0:8])
```

📘 Explicación:

La subcadena "https://" tiene 8 caracteres. El corte [0:8] extrae desde el índice 0 (el inicio) hasta, pero sin incluir, el índice 8.

---

### 🧠 Tarea 7

...usa el método `.index()` para identificar el índice donde comienza la extensión de dominio `.com`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `url` to a specific URL
url = "https://exampleURL1.com"

# Display the index where the domain extension ".com" is located in `url`
print(url.index(".com"))
```

---

### 🧠 Tarea 8

Almacena el resultado del método `.index()` en una variable llamada `ind`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `url` to a specific URL
url = "https://exampleURL1.com"

# Assign `ind` to the output of applying `.index()` to `url` in order to extract the starting index of ".com" in `url` 
ind = url.index(".com")
```

---

### 🧠 Pregunta 2

¿Qué muestra este código y por qué?

Python

```
# (Código de la Tarea 9)
url = "https://exampleURL1.com"
ind = url.index(".com")
print(url[ind:ind+4])
```

✅ Respuesta correcta:

La salida es .com.

📘 **Explicación:**

1. La variable `ind` almacena el índice inicial de la subcadena `".com"`.
    
2. La sentencia `print` realiza un corte (slice) de la `url`.
    
3. El corte comienza en `ind` (el índice de ".") y termina en `ind+4` (el índice _después_ de la "m").
    
4. Esto extrae exitosamente la subcadena `".com"` de la URL.
    

---

### 🧠 Tarea 10

...extrae el nombre del sitio web ("exampleURL1") de la URL usando el corte (slicing) y la variable `ind`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `url` to a specific URL
url = "https://exampleURL1.com"

# Assign `ind` to the output of applying `.index()` to `url` in order to extract the starting index of ".com" in `url` 
ind = url.index(".com")

# Extract the website name in `url` and display it
print(url[8:ind])
```

📘 Explicación:

El corte [8:ind] funciona así:

- `8`: Inicia en el índice 8, que es el carácter inmediatamente posterior a `"https://"`.
    
- `ind`: Termina _antes_ del índice `ind`, que es donde comienza `".com"`.
    
- Esto aísla perfectamente el nombre del sitio web: `"exampleURL1"`.
    

---

### 🧠 Conclusión

¿Cuáles son tus principales conclusiones de este laboratorio?

✅ **Conclusiones clave:**

- **Conversión de Tipos:** La función `str()` es esencial para convertir otros tipos de datos (como `int`) en cadenas (strings) para poder manipularlos.
    
- **Funciones de Cadena:** `len()` (para obtener la longitud) es crucial para las sentencias condicionales que validan datos.
    
- **Concatenación:** El operador `+` es una forma sencilla de unir cadenas, muy útil para modificar datos (como añadir un prefijo "E" a un ID).
    
- **Indexación (0-based):** Acceder a caracteres individuales se hace con corchetes `[]` (ej. `[3]` para el _cuarto_ carácter).
    
- **Corte (Slicing):** Extraer subcadenas es fácil con la notación de dos puntos `[inicio:fin]`, recordando que el índice `fin` es _exclusivo_ (no se incluye).
    
- **Métodos de Cadena:** El método `.index("subcadena")` es muy potente para encontrar la posición de una subcadena, lo cual es fundamental para extraer datos de formatos estructurados como las URLs.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[4- Cadenas y el analista de Seguridad]]
- ➡️ Siguiente: [[6- Ponga a prueba sus Conocimientos - Trabajar con cuerdas]]
