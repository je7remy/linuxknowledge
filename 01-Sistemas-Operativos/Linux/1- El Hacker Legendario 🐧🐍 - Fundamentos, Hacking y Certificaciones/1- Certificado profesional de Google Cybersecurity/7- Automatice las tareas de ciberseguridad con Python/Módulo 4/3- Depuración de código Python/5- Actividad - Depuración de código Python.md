---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Actividad - Depuración de código Python

## 📝 Actividad: Depurar Código Python

### **Introducción**

Uno de los mayores desafíos que enfrentan los analistas es asegurar que los procesos automatizados funcionen sin problemas. La depuración es una práctica importante que los analistas de seguridad incorporan en su trabajo para identificar errores en el código y resolverlos, de modo que el código logre el resultado deseado.

A través de una serie de tareas en este laboratorio, desarrollarás y aplicarás tus habilidades de depuración en Python.

### **Consejos para completar este laboratorio**

- `### YOUR CODE HERE ###` indica dónde debes escribir código. Asegúrate de reemplazarlo con tu propio código antes de ejecutar la celda.
    
- Siéntete libre de abrir las pistas para obtener orientación adicional mientras trabajas en cada tarea.
    
- Para ingresar tu respuesta a una pregunta, haz doble clic en la celda de markdown para editarla. Asegúrate de reemplazar el "[Double-click to enter your responses here.]" con tu propia respuesta.
    
- Puedes guardar tu trabajo manualmente haciendo clic en Archivo y luego en Guardar en la barra de menú superior.
    
- Puedes descargar tu trabajo localmente haciendo clic en Archivo, luego en Descargar y especificando tu formato de archivo preferido.
    

### **Escenario**

En tu trabajo como analista de seguridad, necesitas aplicar estrategias de depuración para asegurar que tu código funcione correctamente.

A lo largo de este laboratorio, trabajarás con código similar al que has escrito antes, pero ahora tiene algunos errores que necesitan ser corregidos. Necesitarás leer celdas de código, ejecutarlas, identificar los errores y ajustar el código para resolverlos.

---

### **Tarea 1**

La siguiente celda de código contiene un **error de sintaxis**. En esta tarea, ejecutarás el código, identificarás por qué ocurre el error y modificarás el código para resolverlo. (Para asegurarte de que se ha resuelto, ejecuta el código nuevamente para verificar si ahora funciona correctamente).

Python

```
# Bucle For que itera sobre un rango de números
# y muestra un mensaje en cada iteración
# Corrección: Añadir ':' al final de la línea 'for'
for i in range(10):
    print("La conexión no se puede establecer")
```

#### **Pregunta 1**

¿Qué sucede cuando ejecutas el código antes de modificarlo? ¿Cómo puedes solucionarlo?

> Al ejecutar el código antes de modificarlo, Python genera un **`SyntaxError: invalid syntax`** (Error de Sintaxis: sintaxis inválida). El error generalmente se señala al final de la línea `for i in range(10)`. Esto ocurre porque **falta el dos puntos (`:`)** requerido al final del encabezado de la declaración del bucle `for`. Para solucionarlo, simplemente se deben **añadir los dos puntos (`:`)** al final de esa línea.

---

### **Tarea 2**

En la siguiente celda de código, se te proporciona una lista de nombres de usuario. Hay un **problema con la sintaxis**. En esta tarea, ejecutarás la celda, observarás qué sucede y modificarás el código para solucionar el problema.

Python

```
# Asigna `usernames_list` a una lista de nombres de usuario
# Corrección: Añadir ',' entre "zdutchma" y "esmith", eliminar espacio extra en "zdutchma"
usernames_list = ["djames", "jpark", "tbailey", "zdutchma", "esmith", "srobinso", "dcoleman", "fbautist"]

# Muestra `usernames_list`
print(usernames_list)
```

#### **Pregunta 2**

¿Qué sucede cuando ejecutas el código antes de modificarlo? ¿Cómo puedes solucionarlo?

> Al ejecutar el código antes de modificarlo, Python genera un **`SyntaxError: invalid syntax`**. El error se señala en la cadena `"esmith"`. Esto sucede porque **falta una coma (`,`)** para separar el elemento `"zdutchma "` del elemento `"esmith"` dentro de la definición de la lista. En Python, los elementos de una lista deben estar separados por comas. Para solucionarlo, se debe **añadir la coma faltante** entre `"zdutchma "` y `"esmith"`. Adicionalmente, se puede eliminar el espacio extra al final de `"zdutchma "` para mantener la consistencia.

---

### **Tarea 3**

En la siguiente celda de código, hay un **error de sintaxis**. Tu tarea es ejecutar la celda, identificar qué está causando el error y solucionarlo.

Python

```
# Muestra un mensaje en mayúsculas
# Corrección: Añadir ')' al final para cerrar la llamada a print()
print("update needed".upper())
```

#### **Pregunta 3**

¿Qué sucede cuando ejecutas el código antes de modificarlo? ¿Qué está causando el error de sintaxis? ¿Cómo puedes solucionarlo?

> Al ejecutar el código antes de modificarlo, Python genera un **`SyntaxError`**, a menudo indicando un final de archivo inesperado (`unexpected EOF while parsing`) o un error similar. El error es causado porque **falta el paréntesis de cierre `)`** para la función `print()`. Cada llamada a una función debe tener un par balanceado de paréntesis de apertura y cierre. Para solucionarlo, se debe **añadir el paréntesis `)`** después de `.upper()`.

---

### **Tarea 4**

En la siguiente celda de código, se te proporciona una `usernames_list`, un `username`, y código que determina si el nombre de usuario está aprobado. Hay **dos errores de sintaxis y una excepción**. Tu tarea es encontrarlos y corregir el código. Una estrategia útil de depuración es enfocarse en un error a la vez y ejecutar el código después de corregir cada uno.

Python

```
# Asigna `usernames_list` a una lista de nombres de usuario que representan usuarios aprobados
usernames_list = ["djames", "jpark", "tbailey", "zdutchma", "esmith", "srobinso", "dcoleman", "fbautist"]

# Asigna `username` a un nombre de usuario específico
username = "esmith"

# Bucle For que itera sobre los elementos de `usernames_list` y determina si cada elemento corresponde a un usuario aprobado
# Corrección 3: Usar el nombre de variable correcto 'usernames_list'
for name in usernames_list:

    # Verifica si `name` coincide con `username`
    # Si coincide, muestra un mensaje correspondiente
    # Corrección 1: Usar '==' para comparación
    if name == username:
        # Corrección 2: Añadir indentación
        print("El usuario es un usuario aprobado")
```

#### **Pregunta 4**

¿Qué sucede cuando ejecutas el código antes de modificarlo? ¿Qué está causando los errores? ¿Cómo puedes solucionarlo?

> Al ejecutar el código sin modificar, ocurren varios errores secuencialmente:
> 
> 1. Primero, un **`NameError`** porque la variable `username_list` usada en el `for` no coincide con la definida (`usernames_list`).
>     
> 2. Después de corregir eso, un **`SyntaxError`** en la línea `if name = username:` porque `=` es para asignación, y se necesita `==` para comparación.
>     
> 3. Finalmente, un **`IndentationError`** porque la línea `print(...)` no está indentada correctamente debajo de la declaración `if`.
>     
> 
> **Causas:**
> 
> 4. Error tipográfico en el nombre de la variable dentro del bucle.
>     
> 5. Uso del operador de asignación (`=`) en lugar del de comparación (`==`).
>     
> 6. Falta de indentación requerida para el bloque `if`.
>     
> 
> **Soluciones:**
> 
> 7. Corregir el nombre de la variable en el `for` a `usernames_list`.
>     
> 8. Cambiar `=` por `==` en la condición `if`.
>     
> 9. Indentar la línea `print` para que esté dentro del bloque `if`.
>     

---

### **Tarea 5**

En esta tarea, examinarás el siguiente código e identificarás el tipo de error que ocurre. Luego, ajustarás el código para corregir el error.

Python

```
# Asigna `usernames_list` a una lista de nombres de usuario
usernames_list = ["elarson", "bmoreno", "tshah", "sgilmore", "eraab"]

# Asigna `username` a un nombre de usuario específico
username = "eraab"

# Determina si `username` es el último nombre de usuario en `usernames_list`
# Si lo es, muestra un mensaje correspondiente
# Corrección: El último índice es 4 (o -1), no 5
if username == usernames_list[4]:
    print("Este nombre de usuario es el último en la lista.")
```

#### **Pregunta 5**

¿Qué sucede cuando ejecutas el código antes de modificarlo? ¿Qué tipo de error es este? ¿Cómo puedes solucionarlo?

> Al ejecutar el código antes de modificarlo, Python genera una **excepción** `IndexError: list index out of range` (Índice de lista fuera de rango). Este es un error de **Excepción**, específicamente un `IndexError`. Ocurre durante la ejecución porque el código intenta acceder al índice `5`, pero la lista `usernames_list` solo tiene 5 elementos, por lo que los índices válidos van de `0` a `4`. Para solucionarlo, se debe usar el índice correcto para el último elemento, que es **`4`** (o alternativamente `-1`).

---

### **Tarea 6**

En esta tarea, examinarás el siguiente código. [...] Hay **dos errores** en el código: primero un error de sintaxis y luego una excepción relacionada con un método de cadena. Tu objetivo es encontrar estos errores y corregirlos.

Python

```
# Asigna `import_file` al nombre del archivo de texto
import_file = "allow_list.txt"

# Asigna `remove_list` a una lista de direcciones IP que ya no están permitidas...
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# Declaración With que lee el archivo de texto y almacena su contenido como una lista en `ip_addresses`
# Corrección 1: Añadir ':' al final de la línea 'with'
with open(import_file, "r") as file:
    ip_addresses = file.read()

# Convierte `ip_addresses` de una cadena a una lista
# Corrección 2: Usar la sintaxis correcta 'cadena.split()'
ip_addresses = ip_addresses.split()

# Bucle For que itera sobre los elementos en `remove_list`,
# verifica si cada elemento está en `ip_addresses`,
# y elimina cada elemento que corresponde a una dirección IP que ya no está permitida
# (Iterar sobre una copia si se modifica la lista original)
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)

# Muestra `ip_addresses` después del proceso de eliminación
print(ip_addresses)
```

#### **Pregunta 6**

¿Qué sucede cuando ejecutas el código antes de modificarlo? ¿Qué está causando los errores? ¿Cómo puedes solucionarlos?

> Al ejecutar el código sin modificar, ocurren dos errores secuencialmente:
> 
> 1. Un **`SyntaxError: invalid syntax`** al final de la línea `with open(import_file, "r") as file`.
>     
> 2. Después de corregir eso, un **`NameError: name 'split' is not defined`** (o `AttributeError`) en la línea `ip_addresses = split.ip_addresses()`.
>     
> 
> **Causas:**
> 
> 1. Falta el **dos puntos (`:`)** requerido al final del encabezado de la declaración `with`.
>     
> 2. La sintaxis para llamar al método de cadena **`.split()`** es incorrecta. Debe ser `cadena.split()`.
>     
> 
> **Soluciones:**
> 
> 1. Añadir los **dos puntos (`:`)** al final de la línea `with`.
>     
> 2. Cambiar `ip_addresses = split.ip_addresses()` a **`ip_addresses = ip_addresses.split()`**.
>     

---

### **Tarea 7**

En esta tarea final, hay tres sistemas operativos: OS 1, OS 2 y OS 3. [...] El siguiente código almacena uno de estos sistemas operativos en una variable llamada `system`. Luego, usa condicionales para mostrar la fecha de parche. Sin embargo, este código tiene **errores lógicos**. Tu objetivo es [...] identificar el error y corregirlo.

Python

```
# Asigna `system` a un sistema operativo específico como cadena
system = "OS 2" # Puedes probar con "OS 1", "OS 2", "OS 3"

# Asigna `patch_schedule` a una lista de fechas de parche en orden de sistema operativo
patch_schedule = ["March 1st", "April 1st", "May 1st"] # Índices: 0, 1, 2

# Declaración condicional que verifica qué sistema operativo está almacenado en `system` y muestra un mensaje con la fecha de parche correspondiente
if system == "OS 1":
    # Corrección: Índice 0 para OS 1
    print("Patch date:", patch_schedule[0])
elif system == "OS 2":
    # Corrección: Índice 1 para OS 2
    print("Patch date:", patch_schedule[1])
elif system == "OS 3":
    # Corrección: Índice 2 para OS 3
    print("Patch date:", patch_schedule[2])
```

#### **Pregunta 7**

¿Qué sucede cuando ejecutas el código antes de modificarlo? ¿Qué está causando los errores lógicos? ¿Cómo puedes solucionarlos?

> Al ejecutar el código antes de modificarlo, este se ejecuta sin generar mensajes de error, pero **muestra la fecha de parche incorrecta** para cada sistema operativo (ej., para "OS 2" muestra "March 1st"). Esto es un **Error Lógico**. La causa es que los **índices utilizados** para acceder a la lista `patch_schedule` (`[2]`, `[0]`, `[2]`) no se corresponden con el orden correcto de los sistemas operativos (OS 1 -> índice 0, OS 2 -> índice 1, OS 3 -> índice 2). Para solucionarlo, se deben **corregir los índices** en cada declaración `print` para que coincidan con la posición correcta en la lista: `patch_schedule[0]` para "OS 1", `patch_schedule[1]` para "OS 2", y `patch_schedule[2]` para "OS 3".

---

### **Conclusión**

¿Cuáles son tus conclusiones clave de este laboratorio?

> - La depuración es un proceso esencial en la programación para encontrar y corregir errores.
>     
> - Existen diferentes tipos de errores: **Errores de Sintaxis** (problemas con las reglas del lenguaje, detectados antes de ejecutar), **Excepciones** (errores durante la ejecución con sintaxis válida) y **Errores Lógicos** (el código se ejecuta pero produce resultados incorrectos).
>     
> - Los mensajes de error de Python son herramientas valiosas que a menudo indican la línea y el tipo de error (especialmente para Sintaxis y Excepciones).
>     
> - Es útil abordar los errores **uno por uno**, ejecutando el código después de cada corrección.
>     
> - Errores comunes incluyen la falta de signos de puntuación (`:`, `,`, `()`, `[]`), errores de indentación, errores tipográficos en nombres de variables y el uso incorrecto de operadores (`=` vs `==`) o métodos (`cadena.split()` vs `split.cadena()`).
>     
> - Comprender la **indexación basada en 0** de Python es crucial para evitar errores `IndexError` al trabajar con listas y cadenas.
>     
> - Los errores lógicos requieren **probar el código** con diferentes entradas y comparar los resultados con lo esperado para identificar dónde falla la lógica.
>

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[4- Explore las técnicas de depuración]]
- ➡️ Siguiente: [[6- Ponga a prueba sus Conocimientos - Depuración de código Python]]
