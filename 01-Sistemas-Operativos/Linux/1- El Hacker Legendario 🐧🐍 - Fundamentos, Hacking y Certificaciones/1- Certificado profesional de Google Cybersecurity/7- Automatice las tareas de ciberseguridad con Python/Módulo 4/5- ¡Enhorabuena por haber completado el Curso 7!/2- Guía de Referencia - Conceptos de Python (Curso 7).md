

## 🧠 Guía de Referencia: Conceptos de Python (Curso 7)

Certificado de Ciberseguridad de Google

### Secciones

- Comentarios
    
- Sentencias Condicionales
    
- Sentencias Iterativas
    
- Funciones Definidas por el Usuario
    
- Funciones Integradas
    
- Importar Módulos y Bibliotecas
    
- Métodos de Cadena
    
- Métodos de Lista
    
- Sintaxis Adicional para Cadenas y Listas
    
- Expresiones Regulares
    
- Operaciones con Archivos
    
- Análisis Sintáctico (Parsing)
    

---

## 💬 Comentarios

La siguiente sintaxis se utiliza para crear un comentario. (Un comentario es una nota que los programadores hacen sobre la intención detrás de su código).

- **`#`**
    
    - Inicia una línea que contiene un comentario de Python.
        
    - **Ejemplo:**
        
        Python
        
        ```
        # Imprimir nombres de usuario aprobados
        ```
        
        _Contiene un comentario que indica que el propósito del código que sigue es imprimir nombres de usuario aprobados._
        
- **`"""`** (cadenas de documentación o docstrings)
    
    - Inicia y finaliza una cadena multilínea que a menudo se usa como un comentario de Python; los comentarios multilínea se usan cuando necesitas más de 79 caracteres en un solo comentario.
        
    - **Ejemplo:**
        
        Python
        
        ```
        """
        La función estimate_attempts() toma un total mensual
        de intentos de inicio de sesión y un número de meses y
        devuelve su producto.
        """
        ```
        
        _Contiene un comentario multilínea que indica el propósito de la función `estimate_attempts()`._
        

---

## 🤔 Sentencias Condicionales

Las siguientes palabras clave y operadores se utilizan en sentencias condicionales.

- **`if`**
    
    - Inicia una sentencia condicional.
        
    - **Ejemplo 1:**
        
        Python
        
        ```
        if device_id != "la858zn":
            # ...
        ```
        
        _Inicia una sentencia condicional que evalúa si la variable `device_id` contiene un valor que **no es igual** a `"la858zn"`._
        
    - **Ejemplo 2:**
        
        Python
        
        ```
        if user in approved_list:
            # ...
        ```
        
        _Inicia una sentencia condicional que evalúa si el valor de la variable `user` también se encuentra en la variable `approved_list`._
        
- **`elif`**
    
    - Precede a una condición que solo se evalúa cuando las condiciones anteriores evalúan a `False`; las condiciones anteriores incluyen la condición en la sentencia `if` y, cuando aplica, condiciones en otras sentencias `elif`.
        
    - **Ejemplo:**
        
        Python
        
        ```
        elif status == 500:
            # ...
        ```
        
        _Cuando las condiciones anteriores evalúan a `False`, evalúa si la variable `status` contiene un valor que es igual a `500`._
        
- **`else`**
    
    - Precede a una sección de código que solo se evalúa cuando todas las condiciones que la preceden dentro de la sentencia condicional evalúan a `False`; esto incluye la condición en la sentencia `if` y, cuando aplica, condiciones en sentencias `elif`.
        
    - **Ejemplo:**
        
        Python
        
        ```
        else:
            # ...
        ```
        
        _Cuando las condiciones anteriores evalúan a `False`, Python evalúa esta sentencia `else`._
        
- **`and`**
    
    - Requiere que **ambas** condiciones a cada lado del operador evalúen a `True`.
        
    - **Ejemplo:**
        
        Python
        
        ```
        if username == "bmoreno" and login_attempts < 5:
            # ...
        ```
        
        _Evalúa a `True` si el valor en la variable `username` es igual a `"bmoreno"` **y** el valor en la variable `login_attempts` es menor que `5`._
        
- **`or`**
    
    - Requiere que **solo una** de las condiciones a cada lado del operador evalúe a `True`.
        
    - **Ejemplo:**
        
        Python
        
        ```
        if status == 100 or status == 102:
            # ...
        ```
        
        _Evalúa a `True` si el valor en la variable `status` es igual a `100` **o** el valor en la variable `status` es igual a `102`._
        
- **`not`**
    
    - Niega una condición dada para que evalúe a `False` si la condición es `True` y a `True` si es `False`.
        
    - **Ejemplo:**
        
        Python
        
        ```
        if not account_status == "removed":
            # ...
        ```
        
        _Evalúa a `False` si el valor en la variable `account_status` es igual a `"removed"` y evalúa a `True` si el valor en la variable `account_status` **no** es igual a `"removed"`._
        

---

## 🔁 Sentencias Iterativas

Las siguientes palabras clave se utilizan en sentencias iterativas.

- **`for`**
    
    - Señala el comienzo de un bucle `for`; usado para iterar a través de una secuencia especificada.
        
    - **Ejemplo 1:**
        
        Python
        
        ```
        for username in ["bmoreno", "tshah", "elarson"]:
            # ...
        ```
        
        _Señala el comienzo de un bucle `for` que itera a través de la secuencia de elementos en la lista `["bmoreno", "tshah", "elarson"]` usando la variable de bucle `username`._
        
    - **Ejemplo 2:**
        
        Python
        
        ```
        for i in range(10):
            # ...
        ```
        
        _Señala el comienzo de un bucle `for` que itera a través de una secuencia de números creada por `range(10)` usando la variable de bucle `i`._
        
- **`while`**
    
    - Señala el comienzo de un bucle `while`; usado para iterar basándose en una condición.
        
    - **Ejemplo:**
        
        Python
        
        ```
        while login_attempts < 5:
            # ...
        ```
        
        _Señala el comienzo de un bucle `while` que iterará mientras la condición de que el valor de `login_attempts` sea menor que `5` evalúe a `True`._
        
- **`break`**
    
    - Se utiliza para salir (romper) de un bucle.
        
- **`continue`**
    
    - Se utiliza para saltar una iteración del bucle y continuar con la siguiente.
        

---

## ‍🧑‍💻 Funciones Definidas por el Usuario

Las siguientes palabras clave se utilizan al crear funciones definidas por el usuario.

- **`def`**
    
    - Se coloca antes del nombre de una función para definirla.
        
    - **Ejemplo 1:**
        
        Python
        
        ```
        def greet_employee():
            # ...
        ```
        
        _Define la función `greet_employee()`._
        
    - **Ejemplo 2:**
        
        Python
        
        ```
        def calculate_fails(total_attempts, failed_attempts):
            # ...
        ```
        
        _Define la función `calculate_fails()`, que incluye los dos parámetros `total_attempts` y `failed_attempts`._
        
- **`return`**
    
    - Se utiliza para devolver información desde una función; cuando Python encuentra esta palabra clave, sale de la función después de devolver la información.
        
    - **Ejemplo:**
        
        Python
        
        ```
        def calculate_fails(total_attempts, failed_attempts):
            fail_percentage = failed_attempts / total_attempts
            return fail_percentage
        ```
        
        _Devuelve el valor de la variable `fail_percentage` desde la función `calculate_fails()`._
        

---

## ✨ Funciones Integradas (Built-in)

Las siguientes funciones integradas se usan comúnmente en Python.

- **`print()`**
    
    - Muestra un objeto especificado en la pantalla.
        
    - **Ejemplo 1:** `print("login success")` _Muestra la cadena `"login success"`._
        
    - **Ejemplo 2:** `print(9 < 7)` _Muestra el valor Booleano `False`._
        
- **`type()`**
    
    - Devuelve el tipo de datos de su entrada.
        
    - **Ejemplo 1:** `print(type(51.1))` _Devuelve el tipo de datos `float`._
        
    - **Ejemplo 2:** `print(type(True))` _Devuelve el tipo de datos `bool`._
        
- **`range()`**
    
    - Genera una secuencia de números.
        
    - **Ejemplo 1:** `range(0, 5, 1)` _Genera la secuencia `0, 1, 2, 3, 4`._
        
    - **Ejemplo 2:** `range(5)` _Genera la secuencia `0, 1, 2, 3, 4` (usando inicio 0 e incremento 1 por defecto)._
        
- **`max()`**
    
    - Devuelve la entrada numérica más grande que se le haya pasado.
        
    - **Ejemplo:** `print(max(10, 15, 5))` _Devuelve `15`._
        
- **`min()`**
    
    - Devuelve la entrada numérica más pequeña que se le haya pasado.
        
    - **Ejemplo:** `print(min(10, 15, 5))` _Devuelve `5`._
        
- **`sorted()`**
    
    - Ordena los componentes de una lista (u otro iterable).
        
    - **Ejemplo 1:** `print(sorted([10, 15, 5]))` _Muestra la lista ordenada `[5, 10, 15]`._
        
    - **Ejemplo 2:** `print(sorted(["bmoreno", "tshah", "elarson"]))` _Muestra la lista ordenada alfabéticamente `["bmoreno", "elarson", "tshah"]`._
        
- **`str()`**
    
    - Convierte el objeto de entrada en una cadena.
        
    - **Ejemplo:** `str(10)` _Convierte el entero `10` a la cadena `"10"`._
        
- **`len()`**
    
    - Devuelve el número de elementos en un objeto.
        
    - **Ejemplo:** `print(len("security"))` _Devuelve y muestra `8`._
        

---

## 📥 Importar Módulos y Bibliotecas

La siguiente palabra clave se utiliza para importar un módulo de la Biblioteca Estándar de Python o para importar una biblioteca externa que ya ha sido instalada.

- **`import`**
    
    - Busca un módulo o biblioteca en un sistema y lo añade al entorno local de Python.
        
    - **Ejemplo 1:** `import statistics` _Importa el módulo `statistics` completo._
        
    - **Ejemplo 2:** `from statistics import mean` _Importa solo la función `mean()` del módulo `statistics`._
        
    - **Ejemplo 3:** `from statistics import mean, median` _Importa las funciones `mean()` y `median()` del módulo `statistics`._
        

---

## ⛓️ Métodos de Cadena (String Methods)

Los siguientes métodos se pueden aplicar a cadenas en Python.

- **`.upper()`**
    
    - Devuelve una copia de la cadena con todas las letras en mayúsculas.
        
    - **Ejemplo:** `print("Security".upper())` _Muestra `"SECURITY"`._
        
- **`.lower()`**
    
    - Devuelve una copia de la cadena con todas las letras en minúsculas.
        
    - **Ejemplo:** `print("Security".lower())` _Muestra `"security"`._
        
- **`.index()`**
    
    - Encuentra la primera aparición de la entrada en una cadena y devuelve su ubicación (índice).
        
    - **Ejemplo:** `print("Security".index("c"))` _Devuelve y muestra el índice `2`._
        

---

## 📜 Métodos de Lista (List Methods)

Los siguientes métodos se pueden aplicar a listas en Python.

- **`.insert()`**
    
    - Añade un elemento en una posición específica dentro de la lista.
        
    - **Ejemplo:**
        
        Python
        
        ```
        username_list = ["elarson", "fgarcia", "tshah"]
        username_list.insert(2,"wjaffrey")
        # username_list ahora es ["elarson", "fgarcia", "wjaffrey", "tshah"]
        ```
        
- **`.remove()`**
    
    - Elimina la primera aparición de un elemento específico dentro de una lista.
        
    - **Ejemplo:**
        
        Python
        
        ```
        username_list = ["elarson", "bmoreno", "wjaffrey", "tshah"]
        username_list.remove("elarson")
        # username_list ahora es ["bmoreno", "wjaffrey", "tshah"]
        ```
        
- **`.append()`**
    
    - Añade la entrada al final de una lista.
        
    - **Ejemplo:**
        
        Python
        
        ```
        username_list = ["bmoreno", "wjaffrey", "tshah"]
        username_list.append("btang")
        # username_list ahora es ["bmoreno", "wjaffrey", "tshah", "btang"]
        ```
        
- **`.index()`**
    
    - Encuentra la primera aparición de un elemento en una lista y devuelve su índice.
        
    - **Ejemplo:**
        
        Python
        
        ```
        username_list = ["bmoreno", "wjaffrey", "tshah", "btang"]
        print(username_list.index("tshah")) # Muestra 2
        ```
        

---

## ✨ Sintaxis Adicional para Cadenas y Listas

La siguiente sintaxis es útil cuando se trabaja con cadenas y listas.

- **`+`** (concatenación)
    
    - Combina dos cadenas o listas juntas.
        
    - **Ejemplo 1 (Cadenas):** `device_id = "IT" + "nwp12"` _Asigna `"ITnwp12"`._
        
    - **Ejemplo 2 (Listas):** `users = ["elarson", "bmoreno"] + ["tshah", "btang"]` _Asigna `["elarson", "bmoreno", "tshah", "btang"]`._
        
- **`[]`** (notación de corchetes)
    
    - Usa índices para extraer partes de una cadena o lista.
        
    - **Ejemplo 1 (Cadena, Índice):** `print("h32rb17"[0])` _Extrae `"h"`._
        
    - **Ejemplo 2 (Cadena, Rebanada):** `print("h32rb17"[0:3])` _Extrae `"h32"` (índice 3 excluido)._
        
    - **Ejemplo 3 (Lista, Índice):**
        
        Python
        
        ```
        username_list = ["elarson", "fgarcia", "tshah"]
        print(username_list[2]) # Extrae "tshah"
        ```
        

---

## 🔍 Expresiones Regulares (Regex)

La siguiente función del módulo `re` y los símbolos de expresiones regulares son útiles al buscar patrones en cadenas. (_Se asume `import re`_).

- **`re.findall()`**
    
    - Devuelve una lista de coincidencias con una expresión regular.
        
    - **Ejemplo:** `re.findall("a53", "a53-32c .E")` _Devuelve `["a53"]`._
        
- **`\w`**
    
    - Coincide con cualquier carácter alfanumérico; también coincide con el guion bajo (`_`).
        
    - **Ejemplo:** `re.findall("\w", "a53-32c .E")` _Devuelve `["a", "5", "3", "3", "2", "c", "E"]`._
        
- **`.`**
    
    - Coincide con todos los caracteres (excepto nueva línea), incluyendo símbolos.
        
    - **Ejemplo:** `re.findall(".", "a53-32c .E")` _Devuelve `["a", "5", "3", "-", "3", "2", "c", " ", ".", "E"]`._
        
- **`\d`**
    
    - Coincide con todos los dígitos simples.
        
    - **Ejemplo:** `re.findall("\d", "a53-32c .E")` _Devuelve `["5", "3", "3", "2"]`._
        
- **`\s`**
    
    - Coincide con todos los espacios simples (espacio, tabulador, nueva línea).
        
    - **Ejemplo:** `re.findall("\s", "a53-32c .E")` _Devuelve `[" "]`._
        
- **`\.`**
    
    - Coincide con el carácter de punto literal (necesita escaparse con `\`).
        
    - **Ejemplo:** `re.findall("\.", "a53-32c .E")` _Devuelve `["."]`._
        
- **`+`**
    
    - Representa **una o más** ocurrencias de un carácter específico (o grupo).
        
    - **Ejemplo:** `re.findall("\w+", "a53-32c .E")` _Devuelve `["a53", "32c", "E"]`._
        
- **`*`**
    
    - Representa **cero, una o más** ocurrencias de un carácter específico (o grupo).
        
    - **Ejemplo:** `re.findall("\w*", "a53-32c .E")` _Devuelve `["a53", "", "32c", "", "", "E", ""]`._
        
- **`{}`**
    
    - Representa un número **especificado** de ocurrencias de un carácter específico (o grupo); el número se especifica dentro de las llaves (ej. `{3}` para exactamente 3, `{2,4}` para entre 2 y 4).
        
    - **Ejemplo:** `re.findall("\w{3}", "a53-32c .E")` _Devuelve `["a53", "32c"]`._
        

---

## 📂 Operaciones con Archivos

Las siguientes funciones, métodos y palabras clave se utilizan con operaciones que involucran archivos.

- **`with`**
    
    - Maneja errores y gestiona recursos externos (como archivos).
        
    - **Ejemplo:** `with open("logs.txt", "r") as file:` _Asegura que `file` se cierre automáticamente._
        
- **`open()`**
    
    - Abre un archivo en Python.
        
    - **Ejemplo 1 (Leer):** `with open("login_attempts.txt", "r") as file:`
        
    - **Ejemplo 2 (Escribir):** `with open("update_log.txt", "w") as file:`
        
    - **Ejemplo 3 (Añadir):** `with open(import_file, "a") as file:`
        
- **`as`**
    
    - Asigna una variable que hace referencia a otro objeto (usualmente el objeto archivo devuelto por `open()`).
        
    - **Ejemplo:** `with open("logs.txt", "r") as file:` _Asigna el archivo abierto a `file`._
        
- **`.read()`**
    
    - Convierte el contenido de un archivo en una cadena.
        
    - **Ejemplo:**
        
        Python
        
        ```
        with open("login_attempts.txt", "r") as file:
            file_text = file.read()
        ```
        
- **`.write()`**
    
    - Escribe datos de cadena en un archivo especificado.
        
    - **Ejemplo:**
        
        Python
        
        ```
        with open("access_log.txt", "a") as file:
            file.write("jrafael")
        ```
        
        _Añade `"jrafael"` al final del archivo._
        

---

## 📄 Análisis Sintáctico (Parsing)

Los siguientes métodos son útiles al analizar datos.

- **`.split()`**
    
    - Convierte una cadena en una lista; separa basándose en un delimitador (o espacios en blanco por defecto).
        
    - **Ejemplo 1 (Coma):** `approved_users = "elarson,bmoreno,tshah".split(",")` _Crea `["elarson", "bmoreno", "tshah"]`._
        
    - **Ejemplo 2 (Espacio):** `removed_users = "wjaffrey jsoto abernard".split()` _Crea `["wjaffrey", "jsoto", "abernard"]`._
        
- **`.join()`**
    
    - Concatena los elementos de un iterable (como una lista) en una cadena, usando la cadena sobre la que se llama como separador. **Sintaxis:** `"separador".join(iterable)`
        
    - **Ejemplo:** `approved_users = ",".join(["elarson", "bmoreno", "tshah"])` _Crea `"elarson,bmoreno,tshah"`._