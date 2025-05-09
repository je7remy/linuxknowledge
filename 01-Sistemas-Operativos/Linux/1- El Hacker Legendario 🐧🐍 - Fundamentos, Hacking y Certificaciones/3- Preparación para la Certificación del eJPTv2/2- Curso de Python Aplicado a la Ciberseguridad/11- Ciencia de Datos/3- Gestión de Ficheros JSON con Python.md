
---

#Python #Ciberseguridad #AnálisisDeDatos #PandasPython #DataScience #Programación #Tech #Informática #SeguridadInformática #Coding #DataAnalysis

---

**Objetivo y utilidad del código**

El **objetivo** de este código es leer datos estructurados en formato JSON y transformarlos en un DataFrame de Pandas. Esto permite organizar la información en una estructura tabular que facilita su análisis y manipulación. 

La **utilidad** principal radica en la eficiencia que ofrece Pandas para trabajar con datos. Al convertir los datos en un DataFrame, se pueden aprovechar herramientas avanzadas para realizar operaciones como filtrado, ordenamiento y cálculos estadísticos de manera rápida y sencilla, optimizando el manejo de la información.

### **Paso 1: Crear el archivo JSON**
Primero, creas un archivo llamado `libros.json` con el siguiente contenido:

```json
{
    "libros": [
        {
            "titulo": "Python for Data Science",
            "autor": "John Smith",
            "año_publicacion": 2019,
            "precio": 29.99
        },
        {
            "titulo": "Machine Learning Basics",
            "autor": "Alice Johnson",
            "año_publicacion": 2020,
            "precio": 45.99
        },
        {
            "titulo": "Data Visualization with Matplotlib",
            "autor": "David Williams",
            "año_publicacion": 2018,
            "precio": 24.99
        }
    ]
}
```

#### **Explicación:**
- **Formato JSON**: Este es un archivo en formato JSON (JavaScript Object Notation), un estándar ligero para almacenar y transferir datos. Está compuesto por pares clave-valor y estructuras como objetos (encerrados en `{}`) y listas (encerradas en `[]`).
- **Estructura**:
  - La clave principal `"libros"` contiene una lista de objetos.
  - Cada objeto dentro de la lista representa un libro y tiene cuatro atributos: `"titulo"`, `"autor"`, `"año_publicacion"` y `"precio"`.
- **Datos**: Hay tres libros en la lista, cada uno con valores específicos para sus atributos. Por ejemplo, el primer libro tiene el título "Python for Data Science", fue escrito por "John Smith", publicado en 2019 y cuesta 29.99.

Este archivo se guarda en tu sistema con el nombre `libros.json` y servirá como la fuente de datos para el código en Python.

---

### **Paso 2: Importar las bibliotecas necesarias**
En el código, comienzas importando dos bibliotecas esenciales:

```python
import pandas as pd
import json
```

#### **Explicación:**
- **`import pandas as pd`**:
  - `pandas` es una biblioteca de Python ampliamente utilizada para el análisis y manipulación de datos.
  - Proporciona estructuras como los **DataFrames**, que son tablas bidimensionales (filas y columnas) similares a una hoja de cálculo o una tabla de base de datos.
  - El alias `pd` es una convención común para referirse a `pandas` de manera más corta en el código.
- **`import json`**:
  - `json` es una biblioteca estándar de Python que permite trabajar con datos en formato JSON.
  - Nos ayudará a leer el archivo `libros.json` y convertirlo en una estructura de datos que Python pueda entender (como un diccionario).

Estas importaciones son el punto de partida para procesar el archivo y trabajar con los datos.

---

### **Paso 3: Definir el nombre del archivo**
A continuación, defines una variable con el nombre del archivo:

```python
archivo = 'libros.json'
```

#### **Explicación:**
- Aquí simplemente asignas el nombre del archivo (`libros.json`) a una variable llamada `archivo`.
- Aunque en este caso usas directamente `'libros.json'` en el siguiente paso, definirlo en una variable mejora la legibilidad y facilita modificaciones futuras (por ejemplo, si el nombre del archivo cambia, solo necesitas actualizarlo en un lugar).

---

### **Paso 4: Leer el archivo JSON**
Utilizas un bloque `with` para abrir y leer el archivo:

```python
with open('libros.json', 'r') as archivo_leido:
    datos_json = json.load(archivo_leido)
```

#### **Explicación:**
- **`with open('libros.json', 'r') as archivo_leido:`**:
  - `open()` es una función de Python que abre un archivo. Toma dos argumentos principales:
    - `'libros.json'`: el nombre del archivo que quieres abrir.
    - `'r'`: el modo de apertura, donde `'r'` significa "lectura" (read). Esto indica que solo leerás el archivo, no lo modificarás.
  - El bloque `with` es una buena práctica porque asegura que el archivo se cierre automáticamente después de terminar de leerlo, evitando problemas de recursos.
  - `archivo_leido` es el nombre que le das al objeto archivo mientras está abierto.
- **`datos_json = json.load(archivo_leido)`**:
  - `json.load()` toma el contenido del archivo JSON y lo convierte en una estructura de datos de Python.
  - En este caso, el archivo `libros.json` se convierte en un **diccionario** de Python. La variable `datos_json` contendrá algo como:
    ```python
    {
        "libros": [
            {"titulo": "Python for Data Science", "autor": "John Smith", "año_publicacion": 2019, "precio": 29.99},
            {"titulo": "Machine Learning Basics", "autor": "Alice Johnson", "año_publicacion": 2020, "precio": 45.99},
            {"titulo": "Data Visualization with Matplotlib", "autor": "David Williams", "año_publicacion": 2018, "precio": 24.99}
        ]
    }
    ```
  - Este diccionario tiene una clave `"libros"` que contiene una lista de diccionarios, donde cada diccionario representa un libro.

---

### **Paso 5: Convertir el JSON en un DataFrame**
Utilizas la función `pd.json_normalize` para transformar los datos en un DataFrame:

```python
dataframe = pd.json_normalize(datos_json, 'libros')
```

#### **Explicación:**
- **`pd.json_normalize`**:
  - Esta función de Pandas convierte datos JSON semi-estructurados (como listas anidadas o diccionarios) en una tabla plana, ideal para un DataFrame.
  - Toma dos argumentos principales aquí:
    - `datos_json`: el diccionario que cargaste en el paso anterior con `json.load()`.
    - `'libros'`: la clave dentro de `datos_json` que contiene la lista de libros.
- **Qué hace**:
  - Extrae la lista asociada a la clave `"libros"`.
  - Convierte cada elemento de la lista (cada diccionario de un libro) en una fila del DataFrame.
  - Usa las claves de los diccionarios (`titulo`, `autor`, `año_publicacion`, `precio`) como nombres de las columnas.
- **Resultado**:
  - Se crea un DataFrame llamado `dataframe` con tres filas (una por cada libro) y cuatro columnas (una por cada atributo del libro).

---

### **Paso 6: Imprimir el DataFrame**
Finalmente, imprimes el DataFrame para ver los datos:

```python
print(dataframe)
```

#### **Explicación:**
- **`print(dataframe)`** muestra el contenido del DataFrame en la consola.
- La salida que obtienes es:

```
                               titulo           autor  año_publicacion  precio
0             Python for Data Science      John Smith             2019   29.99
1             Machine Learning Basics    Alice Johnson            2020   45.99
2  Data Visualization with Matplotlib   David Williams            2018   24.99

[3 rows x 4 columns]
```

- **Interpretación de la salida**:
  - Hay **3 filas**, correspondientes a los tres libros en el archivo JSON.
  - Hay **4 columnas**: `titulo`, `autor`, `año_publicacion` y `precio`, que son los atributos de cada libro.
  - Los datos se presentan en un formato tabular claro, donde cada fila es un libro y cada columna es un atributo.
  - El texto `[3 rows x 4 columns]` es un resumen que Pandas agrega para indicar las dimensiones del DataFrame.

---

### **Resumen del proceso**
1. Creaste un archivo `libros.json` con una lista de libros en formato JSON.
2. Importaste las bibliotecas `pandas` y `json` para trabajar con datos y archivos JSON.
3. Definiste el nombre del archivo en una variable (aunque no la usaste directamente).
4. Leíste el archivo JSON con `json.load()` y lo convertiste en un diccionario de Python.
5. Usaste `pd.json_normalize` para transformar la lista de libros del diccionario en un DataFrame de Pandas.
6. Imprimiste el DataFrame, mostrando los datos en formato tabular.

---

### **Notas adicionales**
- **JSON**: Es un formato universal para datos, comúnmente usado en APIs y almacenamiento. Aquí, lo usaste para estructurar información sobre libros.
- **DataFrame**: Es una herramienta poderosa de Pandas para analizar datos. Una vez que tienes los datos en este formato, puedes realizar operaciones como filtrado, ordenamiento o cálculos estadísticos.
- **Buenas prácticas**: El uso de `with` para abrir archivos y la importación clara de bibliotecas son ejemplos de código bien estructurado.