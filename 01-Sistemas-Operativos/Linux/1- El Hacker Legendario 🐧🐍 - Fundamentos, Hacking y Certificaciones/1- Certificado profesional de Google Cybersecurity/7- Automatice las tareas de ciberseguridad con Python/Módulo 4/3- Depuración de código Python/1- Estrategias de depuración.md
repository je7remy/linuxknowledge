
Depurar tu código es una parte fundamental de la programación.

**Depuración** es la práctica de identificar y corregir errores en el código. A veces, corregir errores puede llevar tanto tiempo como escribir el código original.

## 🐛 Tipos de Errores en Python

Hay tres categorías principales de errores que encontrarás:

### 1. Errores de Sintaxis (`SyntaxError`)

- **Qué son:** Ocurren cuando el código viola las reglas gramaticales del lenguaje Python. Son como errores de ortografía o gramática en un texto.
    
- **Ejemplos:** Olvidar los dos puntos (`:`) al final de un `if`, `for`, `def`, `while`; no cerrar comillas o paréntesis; escribir mal una palabra clave (como `whlie` en lugar de `while`).
    
- **Cómo identificarlos:** Python generalmente te **avisará** con un mensaje de error (`SyntaxError`) que indica la línea donde ocurrió el problema. Suelen ser los más **fáciles de corregir**.
    

Python

```
# Error de sintaxis: faltan los dos puntos
def mi_funcion() # Falta ':'
    print("Hola")
```

---

### 2. Errores Lógicos (`Logic Error`)

- **Qué son:** El código es sintácticamente correcto y se ejecuta sin errores, pero **no hace lo que esperabas**. Produce un resultado incorrecto o inesperado.
    
- **Ejemplos:** Usar un operador incorrecto (como `<` en lugar de `<=`); escribir mal el texto en un `print()`; errores en la lógica de un cálculo.
    
- **Cómo identificarlos:** Son los más **difíciles** porque Python no te avisa. El programa funciona, pero mal.
    
    - **Técnicas de depuración:**
        
        - **Sentencias `print()`:** Insertar `print()` en diferentes partes del código (`print("Llegué a la línea 20")`, `print("Valor de x:", x)`) para rastrear el flujo de ejecución y los valores de las variables.
            
        - **Depuradores (Debuggers):** Herramientas que permiten ejecutar el código paso a paso, establecer **puntos de interrupción** (breakpoints) para pausar la ejecución en ciertos puntos e inspeccionar el estado del programa.
            

---

### 3. Excepciones (`Exception`)

- **Qué son:** Ocurren durante la ejecución del programa. La sintaxis es correcta, pero surge una situación que Python no puede manejar.
    
- **Ejemplos:**
    
    - `ZeroDivisionError`: Intentar dividir entre cero.
        
    - `IndexError`: Intentar acceder a un índice que no existe en una lista o cadena (ej., pedir el carácter 100 en una cadena de 8 caracteres).
        
    - `NameError`: Usar una variable o función que no ha sido definida.
        
    - `TypeError`: Intentar realizar una operación con un tipo de dato incorrecto (ej. sumar un número y una cadena).
        
- **Cómo identificarlos:** Python **detendrá la ejecución** y mostrará un mensaje de error (traceback) que indica el tipo de excepción y la línea donde ocurrió.
    
    - **Técnicas de depuración:** Similar a los errores lógicos, puedes usar `print()` o depuradores para entender el estado del programa justo antes de que ocurra la excepción.
        

Python

```
mi_cadena = "Seguridad"
# IndexError: índice fuera de rango
# print(mi_cadena[100])
```

---

Es normal encontrar errores y excepciones al programar. La habilidad clave es aprender a **interpretar los mensajes de error** y usar técnicas de depuración para **localizar y corregir** el problema.


---

### 🧠 Pregunta

¿Cuáles de los siguientes son **errores de sintaxis**? (Seleccione dos respuestas).

- Omisión de los dos puntos al final del encabezado de una Sentencia iterativa
    
- Escribiendo `<` en una condición cuando se necesita `<=`
    
- Escribir mal la palabra clave de Python `elif` escribiendo en su lugar `elsif`
    
- Llamada a una función que no ha sido definida
    

---

### ✅ Respuestas correctas:

- **Omisión de los dos puntos al final del encabezado de una Sentencia iterativa**
    
- **Escribir mal la palabra clave de Python `elif` escribiendo en su lugar `elsif`**
    

---

### 📘 Justificación:

Omitir los dos puntos al final del encabezado de una Sentencia iterativa y escribir mal la palabra clave de Python `elif` escribiendo `elsif` en su lugar son dos ejemplos de **errores de sintaxis**. Los errores de sintaxis implican un uso no válido del lenguaje Python.

_(Las otras opciones son un error lógico (`<` vs. `<=`) y una excepción en tiempo de ejecución (`NameError` por función no definida), respectivamente)._