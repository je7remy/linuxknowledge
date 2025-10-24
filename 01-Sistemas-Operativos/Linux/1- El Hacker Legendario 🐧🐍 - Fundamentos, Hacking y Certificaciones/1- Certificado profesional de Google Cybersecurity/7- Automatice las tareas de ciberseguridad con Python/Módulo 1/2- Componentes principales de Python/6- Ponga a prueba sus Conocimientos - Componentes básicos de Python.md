
### 🧠 Pregunta 1

¿Cuáles de los siguientes elementos de datos son datos flotantes? (Seleccione todos los que correspondan)

- `15.0`
    
- `8`
    
- `"5.2"`
    
- `-2.11`
    

✅ Respuesta correcta:

15.0 y -2.11

📘 Explicación:

Los Datos flotantes (o floats) son datos formados por un número que incluye un punto decimal.

⚠️ **Análisis de las otras opciones:**

- **`8`**: Es un **entero** (integer), ya que no tiene punto decimal.
    
- **`"5.2"`**: Es una **cadena de texto** (string), indicado por las comillas. Aunque su _contenido_ parece un número, su _tipo_ de dato es texto.
    

---

### 🧠 Pregunta 2

¿Qué código muestra el tipo de datos de la variable username?

username = ["elarson", "bmoreno", "tshah"]

✅ **Respuesta correcta:**

Python

```
username = ["elarson", "bmoreno", "tshah"]
data_type = type(username)
print(data_type)
```

📘 Explicación:

La función type() en Python devuelve el tipo de dato del objeto que se le pasa como argumento.

1. `type(username)`: Esta parte obtiene el tipo de la variable `username`, que en este caso es una **lista** (indicada por los corchetes `[]`).
    
2. `data_type = ...`: El tipo de dato obtenido se asigna a la variable `data_type`.
    
3. `print(data_type)`: Se muestra el valor de `data_type`, que sería `<class 'list'>`.
    

---

### 🧠 Pregunta 3

En el código siguiente, ¿cuál es el tipo de datos de login_success?

login_success = ["success", "success", "fail", "success"]

- Booleana
    
- Cadena
    
- Entero
    
- Lista
    

✅ Respuesta correcta:

Lista

📘 Explicación:

El tipo de dato es Lista. Las listas en Python son una estructura de datos que consiste en una colección de elementos en forma secuencial. Se identifican porque los elementos están encerrados entre corchetes [].

---

### 🧠 Pregunta 4

¿Cuál es el resultado del siguiente código?

Python

```
failed_attempts = 3
failed_attempts = 4
print(failed_attempts)
```

- `3`
    
- `7`
    
- `3, 4`
    
- `4`
    

✅ Respuesta correcta:

4

📘 Explicación:

Este código demuestra la reasignación de variables.

1. En la línea 1, la variable `failed_attempts` se crea y se le asigna el valor `3`.
    
2. En la línea 2, la misma variable `failed_attempts` se **reasigna** con un nuevo valor: `4`. El valor anterior (`3`) se descarta.
    
3. En la línea 3, la función `print()` muestra el valor _actual_ de la variable, que es `4`.