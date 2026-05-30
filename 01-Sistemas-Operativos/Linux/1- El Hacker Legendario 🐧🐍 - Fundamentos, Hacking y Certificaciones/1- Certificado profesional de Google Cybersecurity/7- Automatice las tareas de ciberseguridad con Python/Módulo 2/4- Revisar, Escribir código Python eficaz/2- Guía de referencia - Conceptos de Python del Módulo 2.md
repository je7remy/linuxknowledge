---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Guía de referencia - Conceptos de Python del Módulo 2

### 🧠 Guía de Referencia: Conceptos de Python (Módulo 2)

Esta guía resume la sintaxis y los conceptos clave del Módulo 2 del Certificado de Ciberseguridad de Google.

---

## 📘 Funciones Definidas por el Usuario

Las siguientes palabras clave se utilizan al crear funciones personalizadas.

|**Palabra Clave**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`def`**|Se coloca antes del nombre de una función para definirla.|`def greet_employee():` _(Define la función `greet_employee()`.)_ `def calculate_fails(total_attempts, failed_attempts):` _(Define la función `calculate_fails()` con dos parámetros.)_|
|**`return`**|Se utiliza para devolver información desde una función. Cuando Python encuentra esta palabra clave, sale de la función después de devolver la información.|`def calculate_fails(total_attempts, failed_attempts):` `fail_percentage = failed_attempts / total_attempts` `return fail_percentage` _(Devuelve el valor de la variable `fail_percentage` desde la función.)_|

---

## 📘 Funciones Integradas (Built-in)

Las siguientes funciones integradas se usan comúnmente en Python.

|**Función**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`max()`**|Devuelve la entrada numérica más grande que se le haya pasado.|`print(max(10, 15, 5))` _(Devuelve `15` y lo muestra en la pantalla.)_|
|**`min()`**|Devuelve la entrada numérica más pequeña que se le haya pasado.|`print(min(10, 15, 5))` _(Devuelve `5` y lo muestra en la pantalla.)_|
|**`sorted()`**|Ordena los componentes de una lista (u otro iterable).|`print(sorted([10, 15, 5]))` _(Ordena la lista y muestra `[5, 10, 15]`.)_ `print(sorted(["bmoreno", "tshah", "elarson"]))` _(Ordena alfabéticamente y muestra `["bmoreno", "elarson", "tshah"]`.)_|

---

## 📘 Importar Módulos y Bibliotecas

La siguiente palabra clave se utiliza para importar un módulo de la Biblioteca Estándar de Python o una biblioteca externa ya instalada.

|**Palabra Clave**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`import`**|Busca un módulo o biblioteca en un sistema y lo añade al entorno local de Python.|`import statistics` _(Importa el módulo `statistics` completo.)_ `from statistics import mean` _(Importa solo la función `mean()` del módulo.)_ `from statistics import mean, median` _(Importa las funciones `mean()` y `median()`.)_|

---

## 📘 Comentarios

La siguiente sintaxis se utiliza para crear comentarios (notas que los programadores hacen sobre la intención de su código).

|**Sintaxis**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`#`**|Inicia una línea que contiene un comentario de Python.|`# Print approved usernames` _(Indica que el código siguiente imprimirá nombres de usuario aprobados.)_|
|**`"""..."""`** (docstrings)|Inicia y finaliza una cadena de texto multilínea, a menudo usada como un comentario de Python. Se usa cuando un comentario necesita más de 79 caracteres.|`"""` `La función estimate_attempts() toma un total mensual` `de intentos de inicio de sesión y un número de meses` `y devuelve su producto.` `"""`|



---




# Repaso





---

### 🧠 Guía de Referencia: Conceptos de Python (Módulo 2)

Certificado de Ciberseguridad de Google

### Secciones

- Funciones Definidas por el Usuario
    
- Funciones Integradas
    
- Importar Módulos y Bibliotecas
    
- Comentarios
    

---

### 📘 Funciones Definidas por el Usuario

Las siguientes keywords se utilizan al crear funciones definidas por el usuario.

|**Keyword**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`def`**|Se coloca antes del nombre de una función para definirla.|`def greet_employee():` _(Define la función `greet_employee()`.)_ `def calculate_fails(total_attempts, failed_attempts):` _(Define la función `calculate_fails()`, que incluye los dos parámetros `total_attempts` y `failed_attempts`.)_|
|**`return`**|Se utiliza para devolver información desde una función; cuando Python encuentra esta keyword, sale de la función después de devolver la información.|`def calculate_fails(total_attempts, failed_attempts):` `fail_percentage = failed_attempts / total_attempts` `return fail_percentage` _(Devuelve el valor de la variable `fail_percentage` desde la función `calculate_fails()`.)_|

---

### 📘 Funciones Integradas (Built-in)

Las siguientes funciones integradas se usan comúnmente en Python.

|**Función**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`max()`**|Devuelve la entrada numérica más grande que se le haya pasado.|`print(max(10, 15, 5))` _(Devuelve `15` y lo muestra en la pantalla.)_|
|**`min()`**|Devuelve la entrada numérica más pequeña que se le haya pasado.|`print(min(10, 15, 5))` _(Devuelve `5` y lo muestra en la pantalla.)_|
|**`sorted()`**|Ordena los componentes de una lista (u otro iterable).|`print(sorted([10, 15, 5]))` _(Ordena los elementos de la lista de menor a mayor y muestra la lista ordenada `[5, 10, 15]`.)_ `print(sorted(["bmoreno", "tshah", "elarson"]))` _(Ordena los elementos en la lista en orden alfabético y muestra la lista ordenada `["bmoreno", "elarson", "tshah"]`.)_|

---

### 📘 Importar Módulos y Bibliotecas

La siguiente keyword se utiliza para importar un módulo de la Biblioteca Estándar de Python o para importar una biblioteca externa que ya ha sido instalada.

|**Keyword**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`import`**|Busca un módulo o biblioteca en un sistema y lo añade al entorno local de Python.|`import statistics` _(Importa el módulo `statistics` y todas sus funciones desde la Biblioteca Estándar de Python.)_ `from statistics import mean` _(Importa solo la función `mean()` del módulo `statistics` desde la Biblioteca Estándar de Python.)_ `from statistics import mean, median` _(Importa las funciones `mean()` y `median()` del módulo `statistics` desde la Biblioteca Estándar de Python.)_|

---

### 📘 Comentarios

La siguiente sintaxis se utiliza para crear un comentario. (Un comentario es una nota que los programadores hacen sobre la intención detrás de su código.)

|**Sintaxis**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`#`**|Inicia una línea que contiene un comentario de Python.|`# Print approved usernames` _(Contiene un comentario que indica que el propósito del código que sigue es imprimir nombres de usuario aprobados.)_|
|**`"""..."""`** (documentation strings)|Inicia y finaliza una cadena multilínea que a menudo se usa como un comentario de Python; los comentarios multilínea se usan cuando necesitas más de 79 caracteres en un solo comentario.|`"""` `La función estimate_attempts() toma un total` `de intentos de inicio de sesión mensual y un número de meses` `y devuelve su producto.` `"""` _(Contiene un comentario multilínea que indica el propósito de la función `estimate_attempts()`.)_|

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[1- Recapitulación]]
- ➡️ Siguiente: [[3- Términos del glosario del Módulo 2]]
