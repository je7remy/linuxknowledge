
### 🧠 Tarea 1

Escriba una sentencia iterativa que muestre `Connection could not be established` tres veces. Use la palabra clave `for`, la función `range()`, y una variable de bucle `i`.

✅ **Respuesta correcta:**

Python

```
# Iterative statement using `for`, `range()`, and a loop variable of `i`
# Display "Connection could not be established." three times

for i in range(3):
    print("Connection could not be established.")
```

📘 Explicación:

La función range(3) genera una secuencia de números (0, 1, 2). El bucle for se ejecuta una vez por cada número en esa secuencia (tres veces en total), imprimiendo el mensaje en cada iteración.

---

### 🧠 Tarea 2

Incorpore una variable llamada `connection_attempts`... Asigne un entero positivo de su elección... y rellene la variable que falta.

✅ **Respuesta correcta:**

Python

```
# Create a variable called `connection_attempts` that stores the number of times the user has tried to connect to the network

connection_attempts = 5 # Puede usar cualquier número entero, por ejemplo 5

# Iterative statement using `for`, `range()`, a loop variable of `i`, and `connection_attempts`
# Display "Connection could not be established." as many times as specified by `connection_attempts`

for i in range(connection_attempts):
    print("Connection could not be established")
```

📘 Explicación:

Se asigna un valor entero (ej. 5) a la variable connection_attempts. Esta variable se pasa luego a la función range(), que crea una secuencia de esa longitud. El bucle for itera esa cantidad de veces.

---

### 🧠 Tarea 3

Complete el bucle `while` con el código correcto para que muestre `"Connection could not be established."` tres veces.

✅ **Respuesta correcta:**

Python

```
# Assign `connection_attempts` to an initial value of 0, to keep track of how many times the user has tried to connect to the network

connection_attempts = 0

# Iterative statement using `while` and `connection_attempts`
# Display "Connection could not be established." every iteration, until connection_attempts reaches a specified number

while connection_attempts < 3:
    print("Connection could not be established.")

    # Update `connection_attempts` (increment it by 1 at the end of each iteration) 
    connection_attempts = connection_attempts + 1
```

📘 **Explicación:**

1. `connection_attempts` se inicializa en `0`.
    
2. El bucle `while` comprueba la condición `0 < 3` (True) y se ejecuta. Imprime y `connection_attempts` se vuelve `1`.
    
3. Comprueba `1 < 3` (True). Imprime y `connection_attempts` se vuelve `2`.
    
4. Comprueba `2 < 3` (True). Imprime y `connection_attempts` se vuelve `3`.
    
5. Comprueba `3 < 3` (False). El bucle termina.
    

---

### 🧠 Pregunta 1

**¿Qué observa sobre las diferencias entre el bucle `for` y el bucle `while` que escribió?**

✅ **Respuesta correcta:**

- El **bucle `for`** fue más conciso. Usando `range(3)`, el bucle sabía automáticamente que debía ejecutarse 3 veces. La variable de bucle `i` se gestionó internamente.
    
- El **bucle `while`** requirió más configuración manual. Tuvimos que:
    
    1. **Inicializar** un contador (`connection_attempts = 0`) _antes_ del bucle.
        
    2. Definir una **condición** explícita (`while connection_attempts < 3`).
        
    3. **Incrementar** manualmente el contador (`connection_attempts = connection_attempts + 1`) _dentro_ del bucle para evitar un bucle infinito.
        

---

### 🧠 Tarea 4

...Escriba un bucle `for` que muestre los elementos de esta lista (`ip_addresses`) uno a la vez. Use `i` como la variable de bucle.

✅ **Respuesta correcta:**

Python

```
# Assign `ip_addresses` to a list of IP addresses from which users have tried to log in

ip_addresses = ["192.168.142.245", "192.168.109.50", "192.168.86.232", "192.168.131.147",
                "192.168.205.12", "192.168.200.48"]

# For loop that displays the elements of `ip_addresses` one at a time

for i in ip_addresses:
    print(i)
```

📘 Explicación:

Al usar for i in ip_addresses:, la variable i toma el valor de cada elemento de la lista ip_addresses secuencialmente, y print(i) lo muestra en la pantalla.

---

### 🧠 Tarea 5

...Escriba una sentencia `if` dentro del bucle `for`. Para cada IP... muestre `"IP address is allowed"` si está en la lista de permitidos y `"IP address is not allowed"` en caso contrario.

✅ **Respuesta correcta:**

Python

```
# Assign `allow_list` to a list of IP addresses that are allowed to log in

allow_list = ["192.168.243.140", "192.168.205.12", "192.168.151.162", "192.168.178.71", 
              "192.168.86.232", "192.168.3.24", "192.168.170.243", "192.168.119.173"]

# Assign `ip_addresses` to a list of IP addresses from which users have tried to log in

ip_addresses = ["192.168.142.245", "192.168.109.50", "192.168.86.232", "192.168.131.147",
                "192.168.205.12", "192.168.200.48"]

# For each IP address in the list of IP addresses from which users have tried to log in, 
# If it is among the allowed addresses, then display “IP address is allowed”
# Otherwise, display “IP address is not allowed”

for i in ip_addresses:
	if i in allow_list:
		print("IP address is allowed")
	else:
		print("IP address is not allowed")
```

📘 Explicación:

El bucle itera sobre ip_addresses. En cada iteración, la sentencia if i in allow_list: comprueba si el valor actual de i (la IP) existe dentro de la lista allow_list. Se imprime el mensaje correspondiente según el resultado de esa comprobación.

---

### 🧠 Tarea 6

...si una IP no está permitida, el bucle debe terminar. Use la palabra clave `break` y expanda el mensaje de "no permitido".

✅ **Respuesta correcta:**

Python

```
# Assign `allow_list` to a list of IP addresses that are allowed to log in

allow_list = ["192.168.243.140", "192.168.205.12", "192.168.151.162", "192.168.178.71", 
              "192.168.86.232", "192.168.3.24", "192.168.170.243", "192.168.119.173"]

# Assign `ip_addresses` to a list of IP addresses from which users have tried to log in

ip_addresses = ["192.168.142.245", "192.168.109.50", "192.168.86.232", "192.168.131.147",
                "192.168.205.12", "192.168.200.48"]

# For each IP address in the list of IP addresses from which users have tried to log in, 
# If it is among the allowed addresses, then display “IP address is allowed”
# Otherwise, display “IP address is not allowed”
               
for i in ip_addresses:
	if i in allow_list:
		print("IP address is allowed")
	else:
		print("IP address is not allowed. Further investigation of login activity required")
		break 
```

📘 Explicación:

La palabra clave break se añade dentro del bloque else. Cuando el bucle encuentra la primera IP que no está en allow_list (en este caso, "192.168.142.245"), imprime el mensaje de advertencia y break detiene el bucle for inmediatamente.

---

### 🧠 Tarea 7

...escriba un bucle `while` que genere IDs de empleado... divisibles por 5, entre 5000 y 5150 (inclusive).

✅ **Respuesta correcta:**

Python

```
# Assign the loop variable `i` to an initial value of 5000

i = 5000

# While loop that generates unique employee IDs for the Sales department by iterating through numbers
# and displays each ID created

while i <= 5150: 
    print(i)
    i = i + 5
```

📘 **Explicación:**

1. `i` se inicializa en `5000` (el primer ID válido).
    
2. La condición `while i <= 5150:` asegura que el bucle continúe mientras `i` sea menor o igual a 5150.
    
3. `print(i)` muestra el ID actual.
    
4. `i = i + 5` incrementa `i` al siguiente número divisible por 5, listo para la próxima iteración.
    

---

### 🧠 Tarea 8

...incorpore un mensaje que muestre `Only 10 valid employee ids remaining`... una vez que la variable de bucle alcance `5100`.

✅ **Respuesta correcta:**

Python

```
# Assign the loop variable `i` to an initial value of 5000

i = 5000

# While loop that generates unique employee IDs for the Sales department by iterating through numbers
# and displays each ID created
# This loop displays "Only 10 valid employee ids remaining" once `i` reaches 5100

while i <= 5150: 
    print(i)
    if i == 5100:
        print("Only 10 valid employee ids remaining")
    i = i + 5
```

📘 Explicación:

Dentro del bucle while, después de imprimir el número de ID, una sentencia if comprueba si i es exactamente igual a 5100. Cuando esa condición es True, se imprime el mensaje de advertencia. El bucle luego continúa normalmente.

---

### 🧠 Pregunta 2

**¿Por qué cree que la sentencia `print(i)` está escrita antes del condicional en lugar de dentro del condicional?**

✅ Respuesta correcta:

La sentencia print(i) se coloca antes del condicional if porque queremos que se imprima cada ID de empleado generado (5000, 5005, 5010, etc.).

El condicional `if i == 5100:` solo debe ejecutar una acción adicional (imprimir la advertencia) cuando se cumple esa condición específica.

Si `print(i)` estuviera _dentro_ del `if`, el programa solo imprimiría el número `5100` y ningún otro ID, lo cual no cumpliría con el objetivo de generar la lista de IDs.

---

### 🧠 Conclusión

**¿Cuáles son sus conclusiones clave de este laboratorio?**

✅ **Conclusiones clave:**

- **Automatización:** Los bucles (`for` y `while`) son fundamentales para automatizar tareas repetitivas, como verificar múltiples conexiones o generar series de datos.
    
- **`for` vs. `while`:** El bucle `for` es ideal para iterar sobre una secuencia de longitud definida (como una lista de IPs o un `range()`). El bucle `while` es más adecuado cuando el número de iteraciones es desconocido y depende de que se cumpla una condición (ej. `contador < 3` o `i <= 5150`).
    
- **Control de Bucles `while`:** Los bucles `while` requieren una gestión cuidadosa: (1) inicializar la variable condicional antes del bucle, (2) definir la condición de parada y (3) actualizar la variable _dentro_ del bucle para evitar bucles infinitos.
    
- **Lógica Condicional:** Anidar sentencias `if`/`else` dentro de los bucles permite ejecutar acciones específicas para ciertos elementos durante la iteración.
    
- **`break`:** La palabra clave `break` es una herramienta poderosa para detener un bucle prematuramente, lo cual es crucial en escenarios de seguridad cuando se detecta una anomalía (como una IP no autorizada).