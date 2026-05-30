---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Introducción a las funciones

### 🧠 Pregunta 1

En Python, ¿qué es una función?

- Una sección de código que puede reutilizarse en un programa
    
- Una sección de código que existe directamente en Python
    
- Una sección de código que contiene una Sentencia iterativa
    
- Una sección de código que contiene un condicional
    

✅ Respuesta correcta:

Una sección de código que puede reutilizarse en un programa.

📘 Explicación:

Esta es la definición fundamental de una función. Su propósito principal es agrupar un bloque de código para que pueda ser ejecutado (llamado) múltiples veces desde diferentes lugares, promoviendo la reutilización y la eficiencia. Aunque una función puede contener bucles o condicionales, no es lo que la define.

---

### 🧠 Pregunta 2

¿Cuál de las siguientes palabras clave es esencial a la hora de definir una función?

- `def`
    
- `if`
    
- `for`
    
- `while`
    

✅ Respuesta correcta:

def

📘 Explicación:

La palabra clave def (abreviatura de define o definir) es la instrucción que se usa en Python para indicar el comienzo de la definición de una nueva función. Las otras palabras clave (if, for, while) se utilizan para sentencias condicionales y bucles.

---

### 🧠 Pregunta 3

Desea definir una función que realice una comprobación de estado. ¿Cuál de los siguientes es un Encabezado válido para la definición de la función?

- `def status_check()`
    
- `def status_check`
    
- `def status_check:`
    
- `def status_check():`
    

✅ Respuesta correcta:

def status_check():

📘 Explicación:

La sintaxis correcta para el "encabezado" (la primera línea) de una definición de función en Python requiere cuatro componentes:

1. La palabra clave `def`.
    
2. El nombre de la función (ej. `status_check`).
    
3. Paréntesis `()`.
    
4. Dos puntos `:` al final de la línea.
    

---

### 🧠 Pregunta 4

Usted es responsable de definir una función `alert()` que imprima la sentencia "Security issue detected." ¿Cuál de los siguientes bloques de código representa la indentación correcta para definir y luego llamar a la función?

✅ Respuesta correcta:

La indentación correcta es la que sitúa la sentencia print() dentro del bloque de la función, y la llamada a la función fuera de ese bloque.

Python

```
# 1. El encabezado de la función no tiene indentación
def alert():
    # 2. El cuerpo de la función DEBE estar indentado
    print("Security issue detected.")

# 3. La llamada a la función no tiene indentación (está fuera de la definición)
alert()
```

📘 Explicación:

Python utiliza la indentación (sangría) para determinar qué código pertenece a un bloque:

- El **cuerpo** de la función (la acción que realiza, en este caso `print(...)`) debe estar indentado para indicar que forma parte de `def alert():`.
    
- La **llamada** a la función (`alert()`) es una acción separada que se ejecuta _después_ de que la función ha sido definida. Por lo tanto, no debe estar indentada al mismo nivel que el cuerpo de la función.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[5- Actividad, Definir y llamar a una función]]
