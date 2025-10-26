

## 🐍 Desarrollar un Algoritmo de Análisis Sintáctico en Python

Ahora, uniremos los conceptos aprendidos (lectura de archivos, análisis sintáctico, listas, bucles, condicionales) para crear un algoritmo simple que detecte intentos de inicio de sesión sospechosos.

---

## 🎯 Objetivo del Algoritmo

Crear un programa que se ejecute cuando un usuario inicie sesión y verifique si ese usuario ha tenido **tres o más intentos fallidos** de inicio de sesión registrados en un archivo de registro.

---

## 💾 Entrada y Estrategia

- **Entrada:** Un archivo de registro (`login.txt`) que contiene un nombre de usuario por línea. Cada línea representa un intento fallido de inicio de sesión.
    
- **Estrategia:**
    
    1. Leer el archivo `login.txt` y convertir su contenido en una **lista** de nombres de usuario.
        
    2. Cuando un usuario (`current_user`) intente iniciar sesión:
        
        - Recorrer la lista de nombres de usuario (intentos fallidos).
            
        - Contar cuántas veces aparece `current_user` en la lista.
            
    3. Si el conteo es 3 o más, mostrar una alerta de "Cuenta bloqueada". De lo contrario, permitir el inicio de sesión.
        

---

## ⚙️ Implementación en Python

#### 1. Leer y Preparar el Archivo

Primero, importamos el archivo y lo dividimos en una lista de nombres de usuario.

Python

```
# Asumiendo que "login.txt" existe y tiene nombres de usuario, uno por línea
with open("login.txt", "r") as file:
    text = file.read()

# Dividir el contenido en una lista de nombres de usuario
usernames = text.split()

# (Opcional) Verificar el contenido de la lista
# print(usernames)
```

#### 2. Definir la Función `login_check`

Creamos una función que implementa la lógica de conteo y verificación.

Python

```
def login_check(login_list, current_user):
    # Inicializar un contador para el usuario actual
    counter = 0

    # Recorrer la lista de intentos fallidos (login_list)
    for i in login_list:
        # Si el intento fallido (i) coincide con el usuario actual
        if i == current_user:
            # Incrementar el contador
            counter = counter + 1

    # Verificar el contador final después del bucle
    if counter >= 3:
        print("Account locked:", current_user) # Alerta si hay 3 o más fallos
    else:
        print("Login successful:", current_user) # Permitir si hay menos de 3 fallos
```

#### 3. Probar la Función

Llamamos a la función con la lista de nombres de usuario y diferentes usuarios actuales para probarla.

Python

```
# Probar con un usuario que aparece pocas veces (asumimos 'elarson' aparece < 3 veces)
login_check(usernames, "elarson")

# Probar con un usuario que aparece 3 o más veces (asumimos 'eraab' aparece >= 3 veces)
login_check(usernames, "eraab")
```

📤 **Salida Esperada:**

```
Login successful: elarson
Account locked: eraab
```

---

## ✅ ¡Éxito!

¡Acabas de desarrollar tu primer algoritmo de seguridad que analiza un registro! Aunque esta es una solución básica y se puede hacer más eficiente, demuestra cómo combinar diferentes conceptos de Python (manejo de archivos, listas, bucles `for`, contadores, sentencias `if`) para resolver un problema de seguridad real.