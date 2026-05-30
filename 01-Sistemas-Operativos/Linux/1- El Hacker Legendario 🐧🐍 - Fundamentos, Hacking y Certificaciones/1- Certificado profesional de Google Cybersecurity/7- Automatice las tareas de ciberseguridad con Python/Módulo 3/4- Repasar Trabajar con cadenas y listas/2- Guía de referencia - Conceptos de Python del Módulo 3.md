---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Guía de referencia - Conceptos de Python del Módulo 3

### 🧠 Guía de Referencia: Conceptos de Python (Módulo 3)

Certificado de Ciberseguridad de Google

### Secciones

- Funciones Integradas
    
- Métodos de Cadena
    
- Métodos de Lista
    
- Sintaxis Adicional para Cadenas y Listas
    
- Expresiones Regulares
    

---

### 📘 Funciones Integradas (Built-in)

Las siguientes funciones integradas se usan comúnmente en Python.

|**Función**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`str()`**|Convierte el objeto de entrada en una cadena.|`str(10)` _(Convierte el entero 10 a la cadena `"10"`)_|
|**`len()`**|Devuelve el número de elementos en un objeto.|`print(len("security"))` _(Devuelve y muestra `8`, el número de caracteres en la cadena `"security"`)_|

---

### 📘 Métodos de Cadena (String Methods)

Los siguientes métodos se pueden aplicar a cadenas en Python.

|**Método**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`.upper()`**|Devuelve una copia de la cadena con todas las letras en mayúsculas.|`print("Security".upper())` _(Devuelve y muestra `"SECURITY"`)_|
|**`.lower()`**|Devuelve una copia de la cadena con todas las letras en minúsculas.|`print("Security".lower())` _(Devuelve y muestra `"security"`)_|
|**`.index()`**|Encuentra la primera aparición de la entrada en una cadena y devuelve su ubicación (índice).|`print("Security".index("c"))` _(Encuentra `"c"` y devuelve y muestra su índice `2`)_|

---

### 📘 Métodos de Lista (List Methods)

Los siguientes métodos se pueden aplicar a listas en Python.

|**Método**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`.insert()`**|Añade un elemento en una posición específica dentro de la lista.|`username_list = ["elarson", "fgarcia", "tshah"]` `username_list.insert(2, "wjaffrey")` _(Añade `"wjaffrey"` en el índice 2. La lista se convierte en `["elarson", "fgarcia", "wjaffrey", "tshah"]`)_|
|**`.remove()`**|Elimina la primera aparición de un elemento específico dentro de una lista.|`username_list = ["elarson", "bmoreno", "wjaffrey", "tshah"]` `username_list.remove("elarson")` _(Elimina `"elarson"`. La lista se convierte en `["bmoreno", "wjaffrey", "tshah"]`)_|
|**`.append()`**|Añade la entrada al final de una lista.|`username_list = ["bmoreno", "wjaffrey", "tshah"]` `username_list.append("btang")` _(Añade `"btang"` al final. La lista se convierte en `["bmoreno", "wjaffrey", "tshah", "btang"]`)_|
|**`.index()`**|Encuentra la primera aparición de un elemento en una lista y devuelve su índice.|`username_list = ["bmoreno", "wjaffrey", "tshah", "btang"]` `print(username_list.index("tshah"))` _(Encuentra `"tshah"` y devuelve y muestra su índice `2`)_|

---

### 📘 Sintaxis Adicional para Cadenas y Listas

La siguiente sintaxis es útil cuando se trabaja con cadenas y listas.

|**Sintaxis**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`+`** (concatenación)|Combina dos cadenas o listas juntas.|`device_id = "IT" + "nwp12"` _(Asigna `"ITnwp12"` a `device_id`)_ `users = ["elarson", "bmoreno"] + ["tshah", "btang"]` _(Asigna `["elarson", "bmoreno", "tshah", "btang"]` a `users`)_|
|**`[]`** (notación de corchetes)|Usa índices para extraer partes de una cadena o lista.|`print("h32rb17"[0])` _(Extrae el carácter en el índice 0 (`"h"`))_ `print("h32rb17"[0:3])` _(Extrae la rebanada `[0:3]` (`"h32"`). El índice 0 se incluye, el 3 se excluye.)_ `username_list = ["elarson", "fgarcia", "tshah"]` `print(username_list[2])` _(Extrae el elemento en el índice 2 (`"tshah"`))_|

---

### 📘 Expresiones Regulares (Regex)

La siguiente función del módulo `re` y los símbolos de expresiones regulares son útiles al buscar patrones en cadenas. (_Se asume `import re` antes de usar `re.findall()`_)

|**Función/Símbolo**|**Descripción**|**Ejemplo (cadena = "a53-32c .E")**|**Salida**|
|---|---|---|---|
|**`re.findall()`**|Devuelve una lista de coincidencias con una expresión regular.|`re.findall("a53", cadena)`|`["a53"]`|
|**`\w`**|Coincide con cualquier carácter alfanumérico; también coincide con el guion bajo (`_`).|`re.findall("\w", cadena)`|`["a", "5", "3", "3", "2", "c", "E"]`|
|**`.`**|Coincide con todos los caracteres, incluidos los símbolos (excepto nueva línea).|`re.findall(".", cadena)`|`["a", "5", "3", "-", "3", "2", "c", " ", ".", "E"]`|
|**`\d`**|Coincide con todos los dígitos simples.|`re.findall("\d", cadena)`|`["5", "3", "3", "2"]`|
|**`\s`**|Coincide con todos los espacios simples (espacio, tabulador, nueva línea).|`re.findall("\s", cadena)`|`[" "]`|
|**`\.`**|Coincide con el carácter de punto literal.|`re.findall("\.", cadena)`|`["."]`|
|**`+`**|Representa **una o más** ocurrencias de un carácter específico.|`re.findall("\w+", cadena)`|`["a53", "32c", "E"]`|
|**`*`**|Representa **cero, una o más** ocurrencias de un carácter específico.|`re.findall("\w*", cadena)`|`["a53", "", "32c", "", "", "E", ""]` _(Nota: coincide con cadenas vacías entre no-alfanuméricos)_|
|**`{n}`**|Representa un número **especificado** (`n`) de ocurrencias de un carácter específico.|`re.findall("\w{3}", cadena)`|`["a53", "32c"]`|
|**`{n,m}`**|Representa **entre `n` y `m`** ocurrencias (inclusive) de un carácter específico.|`re.findall("\w{1,2}", cadena)` _(Ejemplo no en la guía)_|`["a5", "3", "32", "c", "E"]`|

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[1- Recapitulación]]
- ➡️ Siguiente: [[3- Términos del glosario del Módulo 3]]
