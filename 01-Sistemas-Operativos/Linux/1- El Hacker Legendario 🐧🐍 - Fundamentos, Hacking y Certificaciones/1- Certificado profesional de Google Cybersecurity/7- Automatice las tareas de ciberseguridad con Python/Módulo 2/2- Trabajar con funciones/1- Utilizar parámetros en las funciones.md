
### 🧠 Introducción a Parámetros y Argumentos

Mientras que algunas funciones simples se ejecutan sin necesidad de información externa, la mayoría de las funciones requieren datos de entrada para ser útiles. Aquí es donde entran los **parámetros** y **argumentos**.

---

### 📘 Parámetros vs. Argumentos

Es fundamental entender la diferencia entre estos dos términos:

|**Término**|**Definición**|**Ubicación (Sintaxis)**|
|---|---|---|
|**Parámetro**|Es la **variable** (un marcador de posición) que se lista dentro de los paréntesis en la **definición** de la función (`def`).|`def mi_funcion(parametro):`|
|**Argumento**|Es el **valor real** (el dato) que se "pasa" a la función cuando se **llama** (ejecuta).|`mi_funcion(argumento)`|

_Analogía:_ Piensa en un **parámetro** como el campo "Nombre:" en un formulario. El **argumento** es el nombre real que tú escribes en ese campo (ej. "Charley Patel").

---

### ⚙️ Cómo Usar Parámetros (Ejemplos)

#### Ejemplo 1: Un Solo Parámetro

Vamos a modificar nuestra función `greet_employee` para que acepte un nombre.

1. Definición (con Parámetro):

En la línea def, incluimos el parámetro nombre dentro de los paréntesis. Ahora podemos usar nombre como una variable dentro de la función.

Python

```
# 'nombre' es el PARÁMETRO
def greet_employee(nombre):
    # El parámetro 'nombre' se usa como una variable
    print("Ha iniciado sesión,", nombre) 
```

2. Llamada (con Argumento):

Cuando llamamos a la función, debemos proporcionar un valor (el argumento) para ese parámetro.

Python

```
# "Charley Patel" es el ARGUMENTO
greet_employee("Charley Patel")
```

📤 **Salida:**

```
Ha iniciado sesión, Charley Patel
```

---

#### Ejemplo 2: Múltiples Parámetros

Las funciones pueden aceptar tantos parámetros como necesites, simplemente separándolos con comas (`,`).

**1. Definición (con Múltiples Parámetros):**

Python

```
# 'nombre' y 'apellido' son PARÁMETROS
def greet_employee(nombre, apellido):
    print("Ha iniciado sesión,", nombre, apellido)
```

2. Llamada (con Múltiples Argumentos):

Debes pasar los argumentos en el mismo orden en que se definieron los parámetros.

Python

```
# "Kiara" y "Carter" son ARGUMENTOS
greet_employee("Kiara", "Carter")
```

📤 **Salida:**

```
Ha iniciado sesión, Kiara Carter
```

---

### ⚠️ Puntos Clave de Sintaxis

- **En la Definición:** Los múltiples parámetros se separan por comas.
    
    - `def mi_funcion(param1, param2):`
        
- **En la Llamada:** Los múltiples argumentos también se separan por comas.
    
    - `mi_funcion(arg1, arg2)`
        
- **Uso Interno:** Cuando usas el parámetro dentro de la función (ej. `print`), trátalo como una variable. **No** uses comillas alrededor del nombre del parámetro (ej. `print(nombre)` es correcto, `print("nombre")` es incorrecto).
    

---

### 💡 En Resumen

- Los **parámetros** hacen que las funciones sean flexibles y potentes.
    
- Permiten que una misma función (`greet_employee`) produzca resultados diferentes (`"Hola Charley"` o `"Hola Kiara"`) dependiendo de los datos que se le pasen.
    
- Este es un concepto fundamental para escribir código eficiente y reutilizable.



---


### 🧠 Pregunta

El siguiente bloque de código define y llama a una función. ¿Qué componente del código es un **argumento**?

Python

```
def display_username(username):
    print("Username is", username)

display_username("bmoreno")
```

- `username`
    
- `display_username()`
    
- `"bmoreno"`
    
- `print()`
    

---

### ✅ Respuesta correcta:

`"bmoreno"`

### 📘 Explicación:

En este bloque de código, el componente que es un **argumento** es `"bmoreno"`.

- **Parámetro:** `username` (es la variable "marcador de posición" en la _definición_ de la función, `def`).
    
- **Argumento:** `"bmoreno"` (son los datos reales que se introducen en la función cuando esta es _llamada_).