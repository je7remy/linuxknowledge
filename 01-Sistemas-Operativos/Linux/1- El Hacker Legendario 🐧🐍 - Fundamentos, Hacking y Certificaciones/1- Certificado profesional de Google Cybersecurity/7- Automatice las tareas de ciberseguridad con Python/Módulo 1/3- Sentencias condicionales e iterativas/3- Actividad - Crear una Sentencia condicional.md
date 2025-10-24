
# Activity: Create a conditional statement (resuelto)

## Task 1

```python
# Assign a variable named `system` to a specific operating system, represented as a string
# This variable indicates which operating system is running
# Feel free to run this cell multiple times; each time try assigning `system` to different values ("OS 1", "OS 2", "OS 3") and observe the result

system = "OS 2"

# If OS 2 is running, then display a "no update needed" message
if system == "OS 2":
    print("no update needed")
```

## Task 2

```python
# Assign `system` to a specific operating system
# Feel free to run multiple times with "OS 1", "OS 2", or "OS 3"
system = "OS 1"

# If OS 2 is running, then display a "no update needed" message
if system == "OS 2":
    print("no update needed")
```

**Question 1 — Respuesta:**

- Con **OS 2**: se imprime `no update needed`.
    
- Con **OS 1** (o **OS 3**): **no** se imprime nada (la condición no se cumple).
    

---

## Task 3

```python
# Assign `system` to a specific operating system
system = "OS 2"   # luego prueba con "OS 1" o "OS 3"

# If OS 2 is running, then display a "no update needed" message
# Otherwise, display an "update needed" message
if system == "OS 2":
    print("no update needed")
else:
    print("update needed")
```

**Question 2 — Respuesta:**

- Con **OS 2**: imprime `no update needed`.
    
- Si **no** es OS 2 (OS 1 u OS 3): imprime `update needed`.
    

---

## Task 4

```python
# Assign `system` to a specific operating system
system = "OS 3"   # prueba también "OS 1", "OS 2" y otros como "OS 4"

# If OS 2 is running, then display a "no update needed" message
# Otherwise if OS 1 is running, display an "update needed" message
# Otherwise if OS 3 is running, display an "update needed" message
if system == "OS 2":
    print("no update needed")
elif system == "OS 1":
    print("update needed")
elif system == "OS 3":
    print("update needed")
```

**Question 3 — Respuesta:**

- **OS 2**: `no update needed`.
    
- **OS 1**: `update needed`.
    
- **OS 3**: `update needed`.
    
- **Otro valor (p. ej., "OS 4")**: no imprime nada (ninguna condición coincide).
    

---

## Task 5

```python
# Assign `system` to a specific operating system
system = "OS 1"

# If OS 2 is running, then display a "no update needed" message
# Otherwise if either OS 1 or OS 3 is running, display an "update needed" message
if system == "OS 2":
    print("no update needed")
elif system == "OS 1" or system == "OS 3":
    print("update needed")
```

**Question 4 — Respuesta:**  
El condicional es más **conciso**: se combinan dos casos (`OS 1` y `OS 3`) con `or`, manteniendo el mismo comportamiento.

---

## Task 6

```python
# Assign `approved_user1` and `approved_user2` to usernames of approved users
approved_user1 = "elarson"
approved_user2 = "bmoreno"

# Assign `username` to the username of a specific user trying to log in
username = "bmoreno"

# If the user trying to log in is among the approved users, then display a message that they are approved to access this device
# Otherwise, display a message that they do not have access to this device
if username == approved_user1 or username == approved_user2:
    print("This user has access to this device.")
else:
    print("This user does not have access to this device.")
```

---

## Task 7

```python
# Assign `approved_list` to a list of approved usernames
approved_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab"]

# Assign `username` to the username of a specific user trying to log in
username = "bmoreno"   # prueba luego con un usuario no aprobado

# If the user trying to log in is among the approved users...
if username in approved_list:
    print("This user has access to this device.")
else:
    print("This user does not have access to this device.")
```

**Question 5 — Respuesta:**

- Usuario **aprobado**: imprime `This user has access to this device.`
    
- Usuario **no aprobado**: imprime `This user does not have access to this device.`
    

---

## Task 8

```python
# Assign `organization_hours` to whether the user is trying to log in during organization hours
organization_hours = True   # prueba también con False

# If True -> during hours; else -> outside hours
if organization_hours:
    print("Login attempt made during organization hours.")
else:
    print("Login attempt made outside of organization hours.")
```

**Question 6 — Respuesta:**

- **Durante** el horario: `Login attempt made during organization hours.`
    
- **Fuera** del horario: `Login attempt made outside of organization hours.`
    

---

## Task 9

```python
# Assign `approved_list` to a list of approved usernames
approved_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab"]

# Assign `username` to the username of a specific user trying to log in
username = "bmoreno"

# Access check
if username in approved_list:
    print("This user has access to this device.")
else:
    print("This user does not have access to this device.")

# Assign `organization_hours`
organization_hours = True

# Hours check
if organization_hours == True:
    print("Login attempt made during organization hours.")
else:
    print("Login attempt made outside of organization hours.")
```

**Question 7 — Respuesta:**

- Usuario **no aprobado**: se imprime que **no tiene acceso**.
    
- Usuario **aprobado**: se imprime que **tiene acceso**.
    
- **Fuera de horario**: se imprime que el intento fue **fuera del horario**.
    

---

## Task 10

```python
# Assign `approved_list` to a list of approved usernames
approved_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab"]

# Assign `username` to the username of a specific user trying to log in
username = "bmoreno"

# Assign `organization_hours` to a Boolean value that represents organization hours
organization_hours = True

# Single-message conditional using a logical operator
if username in approved_list and organization_hours == True:
    print("Login attempt made by an approved user during organization hours.")
else:
    print("Username not approved or login attempt made outside of organization hours.")
```

**Question 8 — Respuesta:**

- Si el usuario está **aprobado** **y** es **horario laboral**: se imprime el mensaje de intento válido durante horario.
    
- Si **no** cumple cualquiera de las dos (no aprobado **o** fuera de horario): se imprime el mensaje alternativo.
    

---

## Conclusion — Key takeaways

- `if / elif / else` permiten **automatizar decisiones** según condiciones.
    
- Operadores lógicos como `or` y `and` hacen el código más **conciso**.
    
- El operador `in` es ideal para verificar pertenencia a **listas** (allow lists).
    
- Comparar booleans directamente (`if organization_hours:`) hace el código más **legible**.
    
- Dividir reglas en pasos y luego combinar condiciones ayuda a construir **validaciones completas** y claras.