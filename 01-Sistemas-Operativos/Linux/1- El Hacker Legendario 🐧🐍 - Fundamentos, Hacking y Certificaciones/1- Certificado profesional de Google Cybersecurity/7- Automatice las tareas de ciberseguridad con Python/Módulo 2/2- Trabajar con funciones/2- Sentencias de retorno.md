---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Sentencias de retorno

### 🧠 Introducción a las Sentencias `return`

Anteriormente, aprendimos a _pasar_ información a una función (usando argumentos). Ahora, aprenderemos cómo una función puede _enviar_ información de vuelta.

Las funciones pueden realizar cálculos o comprobaciones y luego "devolver" un resultado al programa principal para que este pueda usarlo y tomar decisiones.

### 📘 ¿Qué es una Sentencia de Retorno?

Una **sentencia de retorno** (`return`) es una palabra clave de Python que se ejecuta _dentro_ de una función para **enviar un valor de vuelta** al lugar desde donde se llamó la función.

- **`print()` vs. `return`:**
    
    - `print()` solo **muestra** un valor en la pantalla para que el usuario lo vea.
        
    - `return` **entrega** un valor al programa para que pueda ser almacenado en una variable y utilizado en lógica futura (como un `if`).
        
- **Contexto de Seguridad:**
    
    - Una función puede verificar si un usuario tiene permisos y `return True` (si tiene permiso) o `return False` (si no lo tiene).
        
    - Una función puede calcular un porcentaje de riesgo y `return` ese número.
        

---

### ⚙️ Ejemplo: Cálculo de Intentos Fallidos

Veamos cómo crear una función que calcula el porcentaje de intentos de inicio de sesión fallidos y devuelve ese valor.

#### Paso 1: Definición de la Función (con `return`)

Definimos la función con parámetros para los datos de entrada. Dentro, calculamos el porcentaje y usamos `return` para devolver el resultado.

Python

```
# 'total_intentos' y 'intentos_fallidos' son PARÁMETROS
def calcular_intentos(total_intentos, intentos_fallidos):
    
    # 'fail_percentage' es una variable que solo existe DENTRO de esta función
    fail_percentage = intentos_fallidos / total_intentos
    
    # La palabra clave 'return' envía el valor de 'fail_percentage'
    # de vuelta al programa principal.
    return fail_percentage
```

#### Paso 2: Llamada y Captura del Valor Devuelto

Cuando llamamos a la función, debemos **asignar su resultado a una nueva variable** para poder "capturar" el valor que `return` nos envía.

Python

```
# Llamamos a la función con los ARGUMENTOS 4 y 2.
# El valor que 'return' envía (0.5) se almacena en la NUEVA variable 'porcentaje'.
porcentaje = calcular_intentos(4, 2)
```

⚠️ **Punto Clave:** La variable interna (`fail_percentage`) no se puede usar fuera de la función. Debemos capturar el valor devuelto en una nueva variable (como `porcentaje`) para usarlo en el resto del programa.

#### Paso 3: Uso del Valor Devuelto

Ahora que el valor `0.5` está almacenado en la variable `porcentaje`, podemos usarlo en otra lógica, como una sentencia condicional.

Python

```
# Usamos la variable 'porcentaje' que contiene el valor devuelto
if porcentaje >= 0.5:
    print("Cuenta bloqueada")
```

---

### 📤 Salida del Ejemplo Completo

El resultado en la pantalla no es `0.5`. Gracias a que capturamos el valor devuelto, la salida es el resultado de nuestra lógica condicional:

```
Cuenta bloqueada
```

### 💡 En Resumen

- Los **Argumentos** (ej. `4`, `2`) son la forma de **introducir** datos en una función.
    
- `return` es la forma de **sacar** datos (un resultado) de una función.
    
- El valor devuelto debe ser **asignado a una variable** para poder ser reutilizado en el programa.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[1- Utilizar parámetros en las funciones]]
- ➡️ Siguiente: [[3- Funciones y variables]]
