---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Argumentos, parámetros y sentencias de retorno

### 🧠 Pregunta 1

Rellene el espacio en blanco: En el código siguiente, los enteros 5 y 12 son _____:

Python

```
for i in range(5, 12):
    print(i)
```

- parámetros
    
- argumentos
    
- sentencias de retorno
    
- funciones
    

✅ Respuesta correcta:

argumentos

📘 Explicación:

Los enteros 5 y 12 son argumentos. Un argumento son los Datos que se introducen en una Función cuando es llamada. En este caso, 5 y 12 se introducen en la función range() cuando ésta es invocada.

---

### 🧠 Pregunta 2

¿Cuál es la forma correcta de definir la función `addition()` si requiere los dos parámetros `num1` y `num2`?

- `def addition(num1)(num2):`
    
- `def addition(num1 and num2):`
    
- `def addition(num1 num2):`
    
- `def addition(num1, num2):`
    

✅ Respuesta correcta:

def addition(num1, num2):

📘 Explicación:

La forma correcta es def addition(num1, num2):. Si una función requiere varios parámetros, debe colocarlos entre paréntesis y separarlos con comas al definir la función.

---

### 🧠 Pregunta 3

¿Cuál de las siguientes líneas de código tiene la sintaxis correcta para imprimir el tipo de datos de la cadena "elarson"?

- `print(type, "elarson")`
    
- `print(type("elarson"))`
    
- `print("elarson", type)`
    
- `type(print("elarson"))`
    

✅ Respuesta correcta:

print(type("elarson"))

📘 Explicación:

El código print(type("elarson")) tiene la sintaxis correcta. Primero se procesa la función interna (type("elarson")) y luego se pasa su valor devuelto a la función externa (print()). El argumento "elarson" se pasa primero a la función type(). Ésta devuelve su tipo de datos, y éste se pasa a la función print().

---

### 🧠 Pregunta 4

¿Qué definición de función incluye la sintaxis correcta para devolver el valor de la variable `result` desde la función `doubles()`?

- Python
    
    ```
      def doubles(num):
          result = num * 2
          return "result"
    ```
    
- Python
    
    ```
      def doubles(num):
          result = num * 2
          return result
    ```
    
- Python
    
    ```
      def doubles(num):
          result = num * 2
          result return
    ```
    
- Python
    
    ```
      def doubles(num):
          result = num * 2
          return = result
    ```
    

✅ **Respuesta correcta:**

Python

```
def doubles(num):
    result = num * 2
    return result
```

📘 Explicación:

La palabra clave return se utiliza para devolver información de una función. Se coloca antes de la información que se desea devolver (sin un signo =). En este caso, se devuelve el valor almacenado en la variable result, no la cadena de texto "result".

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[6- Crear más funciones]]
