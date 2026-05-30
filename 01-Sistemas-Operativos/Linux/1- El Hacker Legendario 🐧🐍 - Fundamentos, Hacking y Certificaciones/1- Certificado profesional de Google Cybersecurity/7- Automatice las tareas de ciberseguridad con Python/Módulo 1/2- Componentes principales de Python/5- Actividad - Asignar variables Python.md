---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-1]
actualizado: 2026-05-28
---

# Actividad - Asignar variables Python

# 🧠 **Activity: Assign Python Variables**

## **Introduction**

Las variables ayudan a los analistas de seguridad a mantener control sobre información importante, como los intentos de inicio de sesión, usuarios autorizados o el estado de conexión. En este laboratorio, se practican las asignaciones de valores a variables y la determinación de sus tipos de datos.

---

## **Task 1**

```python
# Assign the `device_id` variable to the device ID that only specified users can access
device_id = "72e08x0"
print(device_id)
```

📤 **Output:**

```
72e08x0
```

---

## **Task 2**

```python
# Assign `device_id_type` to the data type of `device_id`
device_id_type = type(device_id)

# Display `device_id_type`
print(device_id_type)
```

📤 **Output:**

```
<class 'str'>
```

### **Question 1**

**Observation:**  
El tipo de dato de `device_id` es una **cadena (`str`)**, ya que su valor está entre comillas y contiene caracteres alfanuméricos.

---

## **Task 3**

```python
# Assign `username_list` to the list of usernames who are allowed to access the device
username_list = ["madebowa", "jnguyen", "tbecker", "nhersh", "redwards"]

# Display `username_list`
print(username_list)
```

📤 **Output:**

```
['madebowa', 'jnguyen', 'tbecker', 'nhersh', 'redwards']
```

---

## **Task 4**

```python
# Assign `username_list_type` to the data type of `username_list`
username_list_type = type(username_list)

# Display `username_list_type`
print(username_list_type)
```

📤 **Output:**

```
<class 'list'>
```

### **Question 2**

**Observation:**  
El tipo de dato de `username_list` es una **lista (`list`)**, ya que contiene varios elementos separados por comas dentro de corchetes.

---

## **Task 5**

```python
# Display current list
username_list = ["madebowa", "jnguyen", "tbecker", "nhersh", "redwards"]
print(username_list)

# Update list
username_list = ["madebowa", "jnguyen", "tbecker", "nhersh", "redwards", "lpope"]
print(username_list)
```

📤 **Output:**

```
['madebowa', 'jnguyen', 'tbecker', 'nhersh', 'redwards']
['madebowa', 'jnguyen', 'tbecker', 'nhersh', 'redwards', 'lpope']
```

### **Question 3**

**Observation:**  
El contenido de `username_list` se actualizó correctamente. La nueva lista incluye al usuario **"lpope"**, demostrando que las listas pueden modificarse fácilmente.

---

## **Task 6**

```python
# Assign `max_logins` to the value 3
max_logins = 3

# Assign `max_logins_type` to the data type of `max_logins`
max_logins_type = type(max_logins)

# Display `max_logins_type`
print(max_logins_type)
```

📤 **Output:**

```
<class 'int'>
```

### **Question 4**

**Observation:**  
El tipo de dato de `max_logins` es un **entero (`int`)**, ya que representa un número sin punto decimal.

---

## **Task 7**

```python
# Assign `login_attempts` to the value 2
login_attempts = 2

# Assign `login_attempts_type` to the data type of `login_attempts`
login_attempts_type = type(login_attempts)

# Display `login_attempts_type`
print(login_attempts_type)
```

📤 **Output:**

```
<class 'int'>
```

### **Question 5**

**Observation:**  
El tipo de dato de `login_attempts` también es un **entero (`int`)**, ya que guarda una cantidad numérica de intentos.

---

## **Task 8**

```python
# Assign `max_logins` to the value 3
max_logins = 3

# Assign `login_attempts` to the value 2
login_attempts = 2

# Compare and display Boolean result
print(login_attempts <= max_logins)
```

📤 **Output:**

```
True
```

### **Question 6**

**Observation:**  
El resultado es **True**, lo que significa que el número de intentos actuales (2) **es menor o igual** al máximo permitido (3). El usuario aún puede iniciar sesión.

---

## **Task 9**

```python
# Assign `max_logins` to the value 3
max_logins = 3

# Assign `login_attempts` to a specific value greater than 3
login_attempts = 5

# Compare and display Boolean result
print(login_attempts <= max_logins)
```

📤 **Output:**

```
False
```

### **Question 7**

**Observation:**  
Cuando el valor de `login_attempts` supera el máximo permitido, el resultado es **False**.  
Esto indica que el usuario **ya ha excedido el límite de intentos** y debería ser bloqueado o recibir una alerta.

---

## **Task 10**

```python
# Assign `login_status` to the Boolean value False
login_status = False

# Assign `login_status_type` to the data type of `login_status`
login_status_type = type(login_status)

# Display `login_status_type`
print(login_status_type)
```

📤 **Output:**

```
<class 'bool'>
```

### **Question 8**

**Observation:**  
El tipo de dato de `login_status` es **booleano (`bool`)**, lo que significa que solo puede tener dos valores: **True** o **False**.

---

## **🧩 Conclusion**

**Key takeaways:**

- Las **variables** en Python permiten almacenar datos como texto, números, listas o valores booleanos.
    
- La función **`type()`** es esencial para verificar el tipo de dato y evitar errores de tipo.
    
- Las **listas** pueden modificarse fácilmente, lo que facilita el manejo de usuarios o registros dinámicos.
    
- Los **valores booleanos** son útiles para representar estados lógicos como “permitido/no permitido” o “activo/inactivo”.
    
- En ciberseguridad, estas estructuras son útiles para **automatizar verificaciones de acceso, monitorear intentos de inicio de sesión y gestionar estados de seguridad**.
    

---

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[4- Asignar y reasignar variables en Python]]
- ➡️ Siguiente: [[6- Ponga a prueba sus Conocimientos - Componentes básicos de Python]]
