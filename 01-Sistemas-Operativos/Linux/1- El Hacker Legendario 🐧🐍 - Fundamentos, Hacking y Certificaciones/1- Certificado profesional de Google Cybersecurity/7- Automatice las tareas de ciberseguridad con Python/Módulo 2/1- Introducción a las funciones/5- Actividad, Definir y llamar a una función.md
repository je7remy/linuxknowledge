
### 🧠 Pregunta 1

Resuma con sus propias palabras qué hace la función definida por el usuario anterior. Piense cuál sería el resultado si se llamara a esta función.

✅ Respuesta correcta:

La función alert() está definida para realizar una sola acción: imprimir el mensaje de cadena de texto "Potential security issue. Investigate further." en la consola.

📘 Explicación:

El código def alert(): simplemente crea y nombra la función, pero no la ejecuta. Si esta función fuera llamada (usando alert()), la salida en la pantalla sería ese mensaje de advertencia. Por sí sola, la definición no produce ninguna salida.

---

### 🧠 Tarea 2

Llame a la función `alert()` que se definió anteriormente y analice el resultado.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `alert()` 

def alert():
    print("Potential security issue. Investigate further.")

# Call the `alert()` function

alert()
```

---

### 🧠 Pregunta 2

¿Cuáles son las ventajas de colocar este código en una función en lugar de ejecutarlo directamente?

✅ Respuesta correcta:

Las dos ventajas principales son la reutilización y la facilidad de mantenimiento.

📘 **Explicación:**

1. **Reutilización:** En lugar de escribir `print("Potential security issue. Investigate further.")` cada vez que necesites mostrar la alerta, ahora solo tienes que escribir `alert()`. Puedes llamar a la función 100 veces si es necesario.
    
2. **Mantenimiento:** Si el mensaje de alerta necesita cambiar (por ejemplo, a "ALERTA: Problema de seguridad detectado"), solo tienes que cambiarlo _una vez_ dentro de la definición de la función (`def`). El cambio se reflejará automáticamente en las 100 veces que la llamaste.
    

---

### 🧠 Tarea 3

Llame a la nueva función `alert()` y observe el resultado.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `alert()`

def alert(): 
    for i in range(3):
        print("Potential security issue. Investigate further.")

# Call the `alert()` function

alert()
```

---

### 🧠 Pregunta 3

¿Cómo se compara la salida anterior con la salida de llamar a la versión anterior de la función `alert()`? ¿En qué se diferencian las dos definiciones de la función?

✅ **Respuesta correcta:**

- **Comparación de Salida:** La nueva salida imprime el mensaje de alerta **tres veces** (una en cada línea), mientras que la función original solo lo imprimió **una vez**.
    
- **Diferencia en Definición:** La definición de la nueva función es diferente porque su **cuerpo** (el código con sangría) ahora contiene un bucle `for i in range(3):`. Este bucle envuelve la sentencia `print()` y hace que se ejecute 3 veces en lugar de una.
    

---

### 🧠 Tarea 4

...comience a definir una función llamada `list_to_string()`. Escriba el encabezado de la función.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `list_to_string()`

def list_to_string():
```

📘 Explicación:

El "encabezado" (header) de una función es la primera línea que la define. Consiste en tres partes clave:

1. La palabra clave `def`.
    
2. El nombre de la función (`list_to_string`).
    
3. Los paréntesis `()` seguidos de dos puntos `:`.
    

_(Nota: Ejecutar esta celda sola dará un error porque se espera un cuerpo con sangría después de los dos puntos)._

---

### 🧠 Tarea 5

...complete el cuerpo de la función `list_to_string()`... escriba un bucle que itere a través de los elementos de `username_list` y muestre cada elemento. Luego, llame a la función.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `list_to_string()`

def list_to_string():

  # Store the list of approved usernames in a variable named `username_list`

  username_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab", "gesparza", "alevitsk", "wjaffrey"]

  # Write a for loop that iterates through the elements of `username_list` and displays each element

  for i in username_list:
    print(i)

# Call the `list_to_string()` function

list_to_string()
```

---

### 🧠 Pregunta 4

¿Qué observa en la salida anterior?

✅ Respuesta correcta:

La salida muestra cada nombre de usuario de la username_list impreso en su propia línea, uno debajo del otro.

📘 Explicación:

La función list_to_string() fue llamada exitosamente. El bucle for i in username_list: iteró correctamente sobre cada elemento de la lista, y la variable i tomó el valor de cada nombre de usuario secuencialmente. La función print(i) se ejecutó en cada iteración.

---

### 🧠 Tarea 6

...use concatenación de cadenas para combinar los nombres de usuario... y almacene el resultado en `sum_variable`. ...Al final de la definición de la función, escriba una sentencia `print()` para mostrar el valor de `sum_variable`.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `list_to_string()`

def list_to_string():

  # Store the list of approved usernames in a variable named `username_list`

  username_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab", "gesparza", "alevitsk", "wjaffrey"]

  # Assign `sum_variable` to an empty string

  sum_variable = ""

  # Write a for loop that iterates through the elements of `username_list` and displays each element

  for i in username_list:
    sum_variable = sum_variable + i

  # Display the value of `sum_variable`

  print(sum_variable)

# Call the `list_to_string()` function

list_to_string()
```

---

### 🧠 Pregunta 5

¿Qué observa en la salida anterior?

✅ Respuesta correcta:

La salida es una única y larga cadena de texto (string) que contiene todos los nombres de usuario pegados uno tras otro, sin espacios, comas ni ningún otro separador.

📘 Explicación:

Esto ocurre porque el operador + se usó para la concatenación de cadenas. En cada iteración, el nombre de usuario actual se "pegó" al final de la sum_variable. La sentencia print() se colocó fuera del bucle, por lo que solo se ejecutó una vez, mostrando el resultado final acumulado.

---

### 🧠 Tarea 7

...agregue una coma y un espacio (`", "`) después de cada nombre de usuario. ...Luego, llame a la función.

✅ **Respuesta correcta (Código):**

Python

```
# Define a function named `list_to_string()`

def list_to_string():

  # Store the list of approved usernames in a variable named `username_list`

  username_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab", "gesparza", "alevitsk", "wjaffrey"]

  # Assign `sum_variable` to an empty string

  sum_variable = ""

  # Write a for loop that iterates through the elements of `username_list` and displays each element

  for i in username_list:
    sum_variable = sum_variable + i + ", "

  # Display the value of `sum_variable`

  print(sum_variable)

# Call the `list_to_string()` function

list_to_string()
```

---

### 🧠 Pregunta 6

¿Qué nota en la salida de la llamada a la función esta vez?

✅ Respuesta correcta:

La salida sigue siendo una única cadena de texto, pero ahora es mucho más legible. Cada nombre de usuario está claramente separado del siguiente por una coma y un espacio.

📘 Observación Adicional:

También se puede notar que hay una coma y un espacio extra (", ") al final de toda la cadena (después de "wjaffrey"), lo cual es un resultado directo de haber añadido el separador en cada iteración del bucle, incluida la última.

---

### 🧠 Conclusión

¿Cuáles son sus principales conclusiones de este laboratorio?

✅ **Conclusiones clave:**

- **Definir vs. Llamar:** Has practicado la diferencia fundamental entre _definir_ una función (con `def nombre():`) para crearla y _llamarla_ (`nombre()`) para que se ejecute.
    
- **Reutilización:** Las funciones son la herramienta principal en Python para crear bloques de código reutilizables, como la función `alert()`.
    
- **Mantenimiento:** Al agrupar el código en una función, si necesitas cambiar la lógica (como añadir un bucle o cambiar un mensaje), solo lo haces en un lugar.
    
- **Cuerpo de la Función:** El cuerpo de una función (el código con sangría) puede contener cualquier lógica de Python que ya conozcas, incluyendo bucles `for` y sentencias `print`.
    
- **Concatenación de Cadenas:** El operador `+` es muy útil dentro de los bucles para "acumular" o construir una nueva cadena de texto a partir de los elementos de una lista, como hiciste al crear `sum_variable`.