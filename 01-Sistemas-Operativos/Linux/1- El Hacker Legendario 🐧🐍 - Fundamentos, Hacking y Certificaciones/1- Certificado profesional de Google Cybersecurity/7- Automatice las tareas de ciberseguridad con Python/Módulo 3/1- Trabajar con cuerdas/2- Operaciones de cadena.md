
### 🧠 Trabajar con Cadenas (Strings) en Python

Es fundamental saber cómo manejar datos de cadena en ciberseguridad, por ejemplo, al analizar nombres de usuario o patrones en la información de inicio de sesión.

Una **cadena (string)** se define como una **secuencia ordenada de caracteres**. En Python, las cadenas se escriben entre comillas dobles (`"Hola"`) o simples (`'Hola'`).

---

### 📘 Funciones Integradas Clave para Cadenas

Aprendiste sobre dos nuevas funciones integradas que son muy útiles para manejar cadenas.

|**Función**|**Sintaxis**|**Descripción**|**Ejemplo**|
|---|---|---|---|
|**`str()`**|`str(objeto)`|**Convierte** un objeto de otro tipo (como un entero o flotante) en una cadena.|`mi_numero = 123` `mi_cadena = str(mi_numero)` _(Ahora `mi_cadena` es `"123"`)_|
|**`len()`**|`len(cadena)`|**Devuelve la longitud** (un entero) que indica el número de caracteres en la cadena.|`longitud = len("Hola")` _(`longitud` es `5`)_|

**Contexto de Seguridad:** La función `len()` es útil para validar datos. Por ejemplo, una dirección IPv4 no válida puede detectarse si `len(direccion_ip)` es mayor de 15 caracteres.

---

### ⚙️ Operaciones: Concatenación de Cadenas

La **concatenación de cadenas** es el proceso de **unir dos o más cadenas** para formar una sola. Esto se hace usando el operador de suma (`+`).

Python

```
cadena1 = "Hola"
cadena2 = "mundo"
resultado = cadena1 + cadena2

print(resultado)
```

📤 **Salida:**

```
Helloworld
```

⚠️ **Nota Importante:** La concatenación no añade espacios automáticamente. Además, otros operadores matemáticos como la resta (`-`) **no funcionan** con cadenas y causarán un error.

---

### 📘 Métodos de Cadena (Funciones Específicas de Cadenas)

Un **método** es una función que _pertenece_ a un tipo de dato específico (en este caso, a las cadenas). A diferencia de las funciones (como `print()`), los métodos se escriben _después_ de la variable o la cadena, separados por un punto (`.`).

**Sintaxis:** `mi_cadena.metodo()`

|**Método**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`.upper()`**|Devuelve una copia de la cadena con todos los caracteres en **MAYÚSCULAS**.|`print("Hola".upper())` _Salida: `HOLA`_|
|**`.lower()`**|Devuelve una copia de la cadena con todos los caracteres en **minúsculas**.|`print("Hola".lower())` _Salida: `hola`_|

---

### 💡 Próximos Pasos

A continuación, aprenderás conceptos más avanzados sobre cadenas, como la **indexación** (acceder a caracteres individuales) y la **división** (extraer sub-cadenas).

---

# Sin resumir:

### 🧠 Trabajar con Cadenas (Strings) en Python

Es fundamental saber cómo manejar datos de cadena en ciberseguridad, por ejemplo, al analizar nombres de usuario o patrones en la información de inicio de sesión.

Una **cadena (string)** se define como una **secuencia ordenada de caracteres**. En Python, las cadenas se escriben entre comillas dobles (`"Hola"`) o simples (`'Hola'`).

---

### 📘 Funciones Integradas Clave para Cadenas

Aprendiste sobre dos nuevas funciones integradas que son muy útiles para manejar cadenas.

|**Función**|**Sintaxis**|**Descripción**|**Ejemplo**|
|---|---|---|---|
|**`str()`**|`str(objeto)`|**Convierte** un objeto de otro tipo (como un entero o flotante) en una cadena.|`mi_numero = 123` `mi_cadena = str(mi_numero)` _(Ahora `mi_cadena` es `"123"`)_|
|**`len()`**|`len(cadena)`|**Devuelve la longitud** (un entero) que indica el número de caracteres en la cadena.|`longitud = len("Hola")` _(`longitud` es `5`)_|

**Contexto de Seguridad:** La función `len()` es útil para validar datos. Por ejemplo, una dirección IPv4 no válida puede detectarse si `len(direccion_ip)` es mayor de 15 caracteres.

---

### ⚙️ Operaciones: Concatenación de Cadenas

La **concatenación de cadenas** es el proceso de **unir dos o más cadenas** para formar una sola. Esto se hace usando el operador de suma (`+`).

Python

```
cadena1 = "Hola"
cadena2 = "mundo"
resultado = cadena1 + cadena2

print(resultado)
```

📤 **Salida:**

```
Helloworld
```

⚠️ **Nota Importante:** La concatenación no añade espacios automáticamente. Además, otros operadores matemáticos como la resta (`-`) **no funcionan** con cadenas y causarán un error.

---

### 📘 Métodos de Cadena (Funciones Específicas de Cadenas)

Un **método** es una función que _pertenece_ a un tipo de dato específico (en este caso, a las cadenas). A diferencia de las funciones (como `print()`), los métodos se escriben _después_ de la variable o la cadena, separados por un punto (`.`).

**Sintaxis:** `mi_cadena.metodo()`

|**Método**|**Descripción**|**Ejemplo**|
|---|---|---|
|**`.upper()`**|Devuelve una copia de la cadena con todos los caracteres en **MAYÚSCULAS**.|`print("Hola".upper())` _Salida: `HOLA`_|
|**`.lower()`**|Devuelve una copia de la cadena con todos los caracteres en **minúsculas**.|`print("Hola".lower())` _Salida: `hola`_|

---

### 💡 Próximos Pasos

A continuación, aprenderás conceptos más avanzados sobre cadenas, como la **indexación** (acceder a caracteres individuales) y la **división** (extraer sub-cadenas).