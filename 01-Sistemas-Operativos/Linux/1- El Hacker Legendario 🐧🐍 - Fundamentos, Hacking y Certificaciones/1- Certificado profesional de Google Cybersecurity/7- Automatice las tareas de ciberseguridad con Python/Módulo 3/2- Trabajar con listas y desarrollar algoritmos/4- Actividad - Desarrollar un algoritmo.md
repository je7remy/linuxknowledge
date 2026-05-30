---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Actividad - Desarrollar un algoritmo

### 🧠 Tarea 1

...ejecute la siguiente celda de código tal como está y observe la salida. Luego, reemplace cada `0` con otro índice y ejecute la celda para observar qué sucede.

✅ **Código (Ejecutado tal cual):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "2ye3lzg", "4n482ts", "a307vir"]

# Display the element at the specified index in `approved_users`
print(approved_users[0])

# Display the element at the specified index in `approved_devices`
print(approved_devices[0])
```

📤 **Salida:**

```
elarson
8rp2k75
```

-----

### 🧠 Pregunta 1

¿Qué observó sobre la salida cuando se muestra `approved_users[0]` y cuando se muestra `approved_devices[0]`? ¿Qué sucede cuando reemplaza cada `0` con otro índice?

✅ **Respuesta correcta:**

  * Cuando se usa el índice `0`, la salida muestra el **primer elemento** de cada lista (`"elarson"` y `"8rp2k75"`).
  * Al reemplazar `0` con otro índice (por ejemplo, `2`), la salida muestra los elementos correspondientes en esa posición en ambas listas (ej. `"tshah"` y `"2ye3lzg"`).

📘 **Explicación:**
Esto demuestra que las listas están **sincronizadas por índice**. El usuario en `approved_users[i]` corresponde al dispositivo en `approved_devices[i]`. La indexación en Python comienza en 0.

-----

### 🧠 Tarea 2

...Use el método `.append()` para agregar `new_user` y `new_device` a las listas correspondientes. Después, muestre las variables...

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "2ye3lzg", "4n482ts", "a307vir"]

# Assign `new_user` to the username of a new approved user
new_user = "gesparza"

# Assign `new_device` to the device ID of the new approved user
new_device = "3rcv4w6"

# Add that user's username and device ID to `approved_users` and `approved_devices` respectively
approved_users.append(new_user)
approved_devices.append(new_device)

# Display the contents of `approved_users`
print(approved_users)

# Diplay the contents of `approved_devices`
print(approved_devices)
```

-----

### 🧠 Pregunta 2

Después de agregar el nuevo usuario aprobado, ¿qué observó sobre la salida cuando se muestra `approved_users` y cuando se muestra `approved_devices`?

✅ **Respuesta correcta:**
La salida muestra que el nuevo nombre de usuario (`"gesparza"`) se ha añadido **al final** de la lista `approved_users`, y el nuevo ID de dispositivo (`"3rcv4w6"`) se ha añadido **al final** de la lista `approved_devices`. Ambas listas ahora tienen 6 elementos.

-----

### 🧠 Tarea 3

...Use el método `.remove()` para eliminar `removed_user` y `removed_device` de las listas correspondientes. Después, muestre ambas variables...

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab", "gesparza"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "2ye3lzg", "4n482ts", "a307vir", "3rcv4w6"]

# Assign `removed_user` to the username of the employee who has left the team
removed_user = "tshah"

# Assign `removed_device` to the device ID of the employee who has left the team
removed_device = "2ye3lzg"

# Remove that employee's username and device ID from `approved_users` and `approved_devices` respectively
approved_users.remove(removed_user)
approved_devices.remove(removed_device)

# Display `approved_users`
print(approved_users)

# Diplay `approved_devices`
print(approved_devices)
```

-----

### 🧠 Pregunta 3

Después de eliminar al usuario que dejó el equipo, ¿qué observó sobre la salida cuando se muestra `approved_users` y cuando se muestra `approved_devices`?

✅ **Respuesta correcta:**
La salida muestra que el nombre de usuario `"tshah"` ha sido eliminado de `approved_users`, y el ID de dispositivo `"2ye3lzg"` ha sido eliminado de `approved_devices`. Ambas listas ahora tienen 5 elementos nuevamente, y los elementos posteriores a los eliminados se han desplazado para llenar el espacio.

-----

### 🧠 Tarea 4

...Escriba una sentencia condicional que verifique si un `username` dado es un elemento de la lista `approved_users`. ...Muestre el mensaje apropiado.

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "sgilmore", "eraab", "gesparza"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "4n482ts", "a307vir", "3rcv4w6"]

# Assign `username` to a username
username = "sgilmore"

# Conditional statement
# If `username` belongs to `approved_users`, then display "The user ______ is approved to access the system."
# Otherwise display "The user ______ is not approved to access the system."
if username in approved_users:
    print("The username", username, "is approved to access the system.")
else:
    print("The user", username, "is not approved to access the system.")
```

-----

### 🧠 Pregunta 4

¿Qué mensaje observa en la salida cuando `username` es `"sgilmore"`?

✅ **Respuesta correcta:**
La salida es: `"The username sgilmore is approved to access the system."`

-----

### 🧠 Tarea 5

...use el método `.index()` para encontrar el índice de `username` en `approved_users` y almacénelo en `ind`. ...muestre `ind`.

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "sgilmore", "eraab", "gesparza"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "4n482ts", "a307vir", "3rcv4w6"]

# Assign `username` to a username
username = "sgilmore"

# Assign `ind` to the index of `username` in `approved_users`
ind = approved_users.index(username)

# Display the value of `ind`
print(ind)
```

-----

### 🧠 Pregunta 5

¿Qué observa en la salida cuando `username` es `"sgilmore"`?

✅ **Respuesta correcta:**
La salida es **`2`**.

📘 **Explicación:**
El método `.index()` devuelve la posición (índice) de la primera aparición del elemento especificado en la lista. `"sgilmore"` es el tercer elemento de `approved_users`, y como la indexación comienza en 0, su índice es 2.

-----

### 🧠 Tarea 6

...use `.index()` para encontrar el índice de `username`... almacénelo en `ind`. Luego, conecte `ind` a `approved_devices` y muestre el ID de dispositivo...

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "sgilmore", "eraab", "gesparza"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "4n482ts", "a307vir", "3rcv4w6"]

# Assign `username` to a username
username = "sgilmore"

# Assign `ind` to the index of `username` in `approved_users`
ind = approved_users.index(username)

# Display the device ID at the index that matches the value of `ind` in `approved_devices`
print(approved_devices[ind])
```

-----

### 🧠 Pregunta 6

¿Qué observa en la salida cuando `username` es `"sgilmore"`?

✅ **Respuesta correcta:**
La salida es **`"4n482ts"`**.

📘 **Explicación:**
Primero, `ind` se asigna al índice de `"sgilmore"` en `approved_users`, que es `2`. Luego, `print(approved_devices[ind])` se convierte en `print(approved_devices[2])`. El elemento en el índice 2 de `approved_devices` es `"4n482ts"`.

-----

### 🧠 Tarea 7

...escriba un condicional que verifique si el `username` está en `approved_users` **y** si el `device_id` en el índice correspondiente coincide...

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "sgilmore", "eraab", "gesparza"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "4n482ts", "a307vir", "3rcv4w6"]

# Assign `username` to a username
username = "sgilmore"

# Assign `device_id` to a device ID
device_id = "4n482ts"

# Assign `ind` to the index of `username` in `approved_users`
ind = approved_users.index(username)

# Conditional statement
# If `username` belongs to `approved_users`, and if the device ID at `ind` in `approved_devices` matches `device_id`,
# then display a message that the username is approved,
# followed by a message that the user has the correct device
if username in approved_users and device_id == approved_devices[ind]:
    print("The username", username, "is approved to access the system.")
    print(device_id, "is the assigned device for", username)
```

-----

### 🧠 Pregunta 7

¿Qué observa en la salida cuando `username` es `"sgilmore"` y `device_id` es `"4n482ts"`?

✅ **Respuesta correcta:**
La salida muestra ambos mensajes:

```
The username sgilmore is approved to access the system.
4n482ts is the assigned device for sgilmore
```

📘 **Explicación:**
Ambas condiciones del `if` son verdaderas: `"sgilmore"` está en `approved_users`, y `"4n482ts"` (el `device_id` proporcionado) es igual al elemento en el índice `ind` (que es 2) de `approved_devices`. Por lo tanto, se ejecuta el bloque de código dentro del `if`.

-----

### 🧠 Tarea 8

...agregue una sentencia `elif`. Esta sentencia `elif` debe ejecutarse cuando el `username` está aprobado pero el `device_id` no coincide...

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "sgilmore", "eraab", "gesparza"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "4n482ts", "a307vir", "3rcv4w6"]

# Assign `username` to a username
username = "sgilmore"

# Assign `device_id` to a device ID
# device_id = "4n482ts" # Correcto
device_id = "incorrect_device" # Incorrecto para probar elif

# Assign `ind` to the index of `username` in `approved_users`
# Añadir verificación por si el usuario no está en la lista para evitar error en .index()
if username in approved_users:
    ind = approved_users.index(username)

    # If statement
    if device_id == approved_devices[ind]:
        print("The user", username, "is approved to access the system.")
        print(device_id, "is the assigned device for", username)
    
    # Elif statement
    # Handles the case when `username` belongs to `approved_users` but element at `ind` in `approved_devices` does not match `device_id`,
    # and displays two messages accordingly
    elif device_id != approved_devices[ind]:
        print("The user", username, "is approved to access the system, but", device_id, "is not their assigned device.")
else:
    # Manejar caso si el usuario no está aprobado
    print("The user", username, "is not approved to access the system.")

```

*(Nota: Modifiqué ligeramente la estructura para manejar el caso en que `username` no esté en `approved_users` y evitar un error en `.index()`. La lógica central del `elif` es la solicitada).*

-----

### 🧠 Pregunta 8

¿Qué observa en la salida cuando `username` es `"sgilmore"` y `device_id` es `"4n482ts"`?

✅ **Respuesta correcta:**
La salida es la misma que en la Tarea 7 (ambos mensajes de aprobación). El bloque `elif` **no** se ejecuta porque la condición del `if` principal (`device_id == approved_devices[ind]`) es verdadera. Si `device_id` fuera diferente (p. ej., `"incorrect_device"`), entonces el bloque `elif` se ejecutaría y mostraría el mensaje de dispositivo incorrecto.

-----

### 🧠 Tarea 9

...defina una función llamada `login` que tome dos parámetros, `username` y `device_id`. ...llame a la función...

✅ **Respuesta correcta (Código):**

```python
# Assign `approved_users` to a list of approved usernames
approved_users = ["elarson", "bmoreno", "sgilmore", "eraab", "gesparza"]

# Assign `approved_devices` to a list of device IDs that correspond to the usernames in `approved_users`
approved_devices = ["8rp2k75", "hl0s5o1", "4n482ts", "a307vir", "3rcv4w6"]

# Define a function named `login` that takes in two parameters, `username` and `device_id`
def login(username, device_id):

    # If `username` belongs to `approved_users`,
    if username in approved_users:

        # then display "The user ______ is approved to access the system.",
        print("The user", username, "is approved to access the system.")

        # assign `ind` to the index of `username` in `approved_users`,
        ind = approved_users.index(username)

        # and execute the following conditional
        # If `device_id` matches the element at the index `ind` in `approved_devices`,
        if device_id == approved_devices[ind]:

          # then display "______ is the assigned device for ______"
          print(device_id, "is the assigned device for", username)

        # Otherwise,
        else:

          # display "______ is not their assigned device"
          print(device_id, "is not their assigned device.")

    # Otherwise (part of the outer conditional and handles the case when `username` does not belong to `approved_users`),
    else:

        # Display "The user ______ is not approved to access the system."
        print("The username", username, "is not approved to access the system.")

# Call the function you just defined to experiment with different username and device_id combinations
login("sgilmore", "4n482ts") # Caso: Usuario y dispositivo correctos
login("sgilmore", "wrong_device") # Caso: Usuario correcto, dispositivo incorrecto
login("unknown_user", "any_device") # Caso: Usuario incorrecto
```

-----

### 🧠 Pregunta 9

Después de que Python entra en el condicional interno, ¿qué sucede cuando el `device_id` es correcto y qué sucede cuando el `device_id` es incorrecto?

✅ **Respuesta correcta:**

  * **`device_id` Correcto:** Se cumple la condición `if device_id == approved_devices[ind]`. Python ejecuta el bloque `if` interno y muestra el mensaje: `"[device_id] is the assigned device for [username]"`.
  * **`device_id` Incorrecto:** No se cumple la condición `if`. Python salta ese bloque y ejecuta el bloque `else` interno, mostrando el mensaje: `"[device_id] is not their assigned device."`.

-----

### 🧠 Conclusión

¿Cuáles son sus principales conclusiones de este laboratorio?

✅ **Conclusiones clave:**

  * **Sincronización de Listas:** Se puede mantener información relacionada en listas separadas siempre que estén sincronizadas por índice (el elemento en la posición `i` de una lista corresponde al elemento en la posición `i` de la otra).
  * **Métodos de Lista:** `.append()` es útil para añadir elementos al final (ej. nuevos usuarios), y `.remove()` es útil para eliminar elementos por su valor (ej. usuarios que se van).
  * **Operador `in`:** Es una forma concisa y legible de verificar si un elemento existe dentro de una lista (`if username in approved_users:`).
  * **`.index()` para Conectar Listas:** El método `.index()` es clave para encontrar la posición de un elemento en una lista y luego usar esa misma posición (índice) para acceder a la información correspondiente en otra lista sincronizada.
  * **Algoritmos con Condicionales:** Se pueden construir algoritmos paso a paso usando condicionales (`if`, `elif`, `else`) para manejar diferentes casos (usuario aprobado/no aprobado, dispositivo correcto/incorrecto). Los condicionales anidados permiten refinar aún más la lógica.
  * **Funciones para Algoritmos:** Encapsular la lógica completa del algoritmo dentro de una función (`def login(...)`) la hace reutilizable y fácil de probar con diferentes entradas.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[3- Listas y el analista de Seguridad]]
- ➡️ Siguiente: [[5- Ponga a prueba sus Conocimientos - Trabaje con listas y desarrolle algoritmos]]
