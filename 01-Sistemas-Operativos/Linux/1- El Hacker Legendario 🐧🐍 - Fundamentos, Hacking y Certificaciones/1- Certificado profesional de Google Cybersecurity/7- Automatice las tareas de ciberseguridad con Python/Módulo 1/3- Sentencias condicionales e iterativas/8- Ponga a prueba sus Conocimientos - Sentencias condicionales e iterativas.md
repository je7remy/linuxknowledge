---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-1]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Sentencias condicionales e iterativas

### 🧠 Pregunta 1

¿Qué mostrará el siguiente Código?

Python

```
ip_address = "192.168.183.51"
if ip_address == "192.168.183.51":
    print("You're logged in.")
else:
    print("Login failed, try again.")
```

- `"You're logged in."`
    
- `"Login failed, try again."`
    
- Nada
    
- Tanto `"You're logged in."` como `"Login failed, try again."`
    

✅ Respuesta correcta:

"You're logged in."

📘 Explicación:

El código primero asigna el valor "192.168.183.51" a la variable ip_address. La sentencia if comprueba si el valor de ip_address es exactamente igual (==) a la cadena "192.168.183.51".

Dado que esta condición se evalúa como `True` (verdadera), Python ejecuta el bloque de código dentro del `if`, que es `print("You're logged in.")`. El bloque `else` solo se ejecuta si la condición del `if` es `False`, por lo que es ignorado.

---

### 🧠 Pregunta 2

¿Qué sentencia condicional imprime el mensaje "account locked" cuando el valor de `failed_logins` es 3 o superior?

- `if failed_login_count == 3: print("account locked")`
    
- `if failed_logins >= 3: print("account locked")`
    
- `if failed_login_count > 3: print("account locked")`
    
- `if failed_login_count != 3: print("account locked")`
    

✅ **Respuesta correcta:**

Python

```
if failed_logins >= 3:
    print("account locked")
```

📘 Explicación:

La frase "3 o superior" significa "mayor o igual que 3".

- El operador de comparación `==` significa "exactamente igual a".
    
- El operador de comparación `>` significa "mayor que".
    
- El operador de comparación `!=` significa "no igual a".
    
- El operador de comparación `>=` significa "mayor o igual que", que es la condición correcta para este escenario.
    

---

### 🧠 Pregunta 3

¿Qué código imprime todos los números de 3 a 7?

- `for i in range(3, 4, 5, 6, 7): print(i)`
    
- `for i in range(3, 8): print(i)`
    
- `for i in range(3, 7): print(i)`
    
- `for i in range(8): print(i)`
    

✅ **Respuesta correcta:**

Python

```
for i in range(3, 8):
    print(i)
```

📘 Explicación:

La función range(inicio, parada) en Python genera una secuencia de números que:

1. **Comienza** en el número `inicio` (este número _sí_ se incluye).
    
2. **Termina** _antes_ de alcanzar el número `parada` (este número _no_ se incluye).
    

Para obtener los números del 3 al 7 (es decir: 3, 4, 5, 6, 7), necesitas:

- Comenzar en **3** (inclusivo).
    
- Detenerte _antes_ de **8** (exclusivo).
    

Por lo tanto, `range(3, 8)` es la sintaxis correcta.

---

### 🧠 Pregunta 4

¿Cuántas veces imprime el siguiente código el mensaje de "alerta de Seguridad"?

Python

```
count = 0
while count < 10:
    print("security alert")
    count = count + 1
```

- `5`
    
- `0`
    
- `10`
    
- `9`
    

✅ Respuesta correcta:

10

📘 Explicación:

Este es un bucle while que se ejecuta basado en el valor de la variable count.

1. `count` se inicializa en `0`.
    
2. El bucle se ejecuta mientras la condición `count < 10` sea `True`.
    
3. Dentro del bucle, se imprime el mensaje y luego `count` se incrementa en 1.
    

El bucle se ejecutará para los siguientes valores de `count`: **0, 1, 2, 3, 4, 5, 6, 7, 8, 9**.

Estos son 10 valores distintos. Cuando `count` se incrementa a `10`, la condición `10 < 10` se evalúa como `False` y el bucle se detiene. Por lo tanto, el mensaje se imprimió **10 veces**.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[7- Actividad - Crear bucles]]
