
---

#Python #Ciberseguridad #AnálisisDeDatos #PandasPython #DataScience #Programación #Tech #Informática #SeguridadInformática #Coding #DataAnalysis

---
### **Introducción: ¿Qué se hace, por qué se hace, su importancia y beneficios en la automatización?**

En este ejercicio, estamos utilizando la biblioteca **pandas** en Python para leer, manipular y analizar un archivo CSV llamado `'datos.csv'`, que contiene información sobre personas (nombres, edades y ciudades). El objetivo es explorar diferentes formas de trabajar con estos datos: desde simplemente leerlos y mostrarlos hasta aplicar filtros avanzados basados en condiciones específicas.

- **¿Por qué se hace?**: El análisis de datos es una tarea común en muchos campos (ciencia, negocios, investigación), y hacerlo manualmente es lento y propenso a errores. Usar herramientas como pandas permite procesar datos de manera eficiente y sistemática.
- **Importancia**: Automatizar estas tareas ahorra tiempo, reduce errores humanos y permite manejar grandes volúmenes de datos con facilidad.
- **Beneficios en la automatización**:
  - **Eficiencia**: Procesar miles o millones de filas en segundos.
  - **Reproducibilidad**: El código puede ejecutarse repetidamente con los mismos resultados.
  - **Flexibilidad**: Podemos ajustar los filtros o análisis según las necesidades.
  - **Escalabilidad**: Se integra con otras herramientas para flujos de trabajo más complejos.

Ahora, desglosemos cada fragmento de código paso a paso.

---

### **Paso 1: Leer y mostrar el archivo CSV**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

print(data)
```

**Salida:**
```
   Nombre  Edad         Ciudad
0   Mario    21        La Vega
1  Jeremy    22         Higuey
2    Jose    23  Santo Domingo
```

**Explicación:**
1. **`import pandas as pd`**: Importamos la biblioteca pandas y la renombramos como `pd` (una convención común para abreviar).
2. **`data = pd.read_csv('datos.csv')`**: Leemos el archivo `'datos.csv'` y lo cargamos en un **DataFrame** llamado `data`. Un DataFrame es como una tabla con filas y columnas, ideal para datos tabulares.
3. **`print(data)`**: Mostramos el contenido completo del DataFrame.

**Propósito**: Este es el punto de partida. Sin leer los datos, no podemos analizarlos. Aquí vemos que el archivo contiene tres columnas: `'Nombre'`, `'Edad'` y `'Ciudad'`.

---

### **Paso 2: Filtrar y mostrar una columna específica (Nombre)**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro_nombre = data['Nombre']

print(filtro_nombre)
```

**Salida:**
```
0     Mario
1    Jeremy
2      Jose
Name: Nombre, dtype: object
```

**Explicación:**
1. **`filtro_nombre = data['Nombre']`**: Extraemos la columna `'Nombre'` del DataFrame, que se convierte en una **Serie** (una estructura de datos unidimensional en pandas).
2. **`print(filtro_nombre)`**: Imprimimos solo los valores de la columna `'Nombre'`.

**Propósito**: Nos permite enfocarnos en una parte específica de los datos, útil cuando no necesitamos toda la tabla.

---

### **Paso 3: Filtrar y mostrar otra columna (Edad)**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro_edad = data['Edad']

print(filtro_edad)
```

**Salida:**
```
0    21
1    22
2    23
Name: Edad, dtype: int64
```

**Explicación:**
1. **`filtro_edad = data['Edad']`**: Extraemos la columna `'Edad'` como una Serie.
2. **`print(filtro_edad)`**: Mostramos las edades.

**Propósito**: Similar al paso anterior, pero ahora con la columna `'Edad'`. Notamos que el tipo de datos es `int64` (números enteros), lo cual será relevante más adelante.

---

### **Paso 4: Mostrar múltiples columnas con separación**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro_nombre = data['Nombre']
filtro_edad = data['Edad']

print(filtro_nombre)
print('-------------------------------')
print(filtro_edad)
```

**Salida:**
```
0     Mario
1    Jeremy
2      Jose
Name: Nombre, dtype: object
-------------------------------
0    21
1    22
2    23
Name: Edad, dtype: int64
```

**Explicación:**
1. Extraemos ambas columnas: `'Nombre'` y `'Edad'`.
2. Las imprimimos separadas por una línea de guiones para mayor claridad.

**Propósito**: Esto es más sobre presentación. En análisis reales, podríamos combinar estas columnas o realizar cálculos, pero aquí solo las mostramos juntas.

---

### **Paso 5: Usar `head()` para ver las primeras filas**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

print(data.head())
```

**Salida:** (Asumiendo las primeras 5 filas, aunque el ejemplo inicial solo muestra 3)
```
   Nombre  Edad         Ciudad
0   Mario    21        La Vega
1  Jeremy    22         Higuey
2    Jose    23  Santo Domingo
```

**Explicación:**
1. **`data.head()`**: Devuelve las primeras 5 filas del DataFrame (por defecto).
2. **`print(data.head())`**: Mostramos esas filas.

**Propósito**: Ideal para inspeccionar rápidamente los datos sin abrumarnos con todo el contenido, especialmente en archivos grandes.

---

### **Paso 6: Filtrar nombres que empiecen con 'J'**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro = data['Nombre'].str.startswith('J')

resultado_filtro = data.loc[filtro]
print(resultado_filtro)
```

**Salida:**
```
    Nombre Edad         Ciudad
1   Jeremy   22         Higuey
2     Jose   23  Santo Domingo
...
```

**Explicación:**
1. **`data['Nombre'].str.startswith('J')`**: Crea una Serie booleana (`True`/`False`) indicando si cada nombre comienza con 'J'.
2. **`data.loc[filtro]`**: Usa esa Serie para seleccionar las filas correspondientes del DataFrame.
3. **`print(resultado_filtro)`**: Muestra las filas filtradas.

**Propósito**: Introducimos el filtrado basado en condiciones, una técnica clave para extraer subconjuntos de datos relevantes.

---

### **Paso 7: Filtrar edades que empiecen con '2' (error potencial)**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro = data['Edad'].str.startswith('2')

resultado_filtro = data.loc[filtro]
print(resultado_filtro)
```

**Salida:**
```
   Nombre Edad         Ciudad
0    Mario   21        La Vega
1   Jeremy   22         Higuey
2     Jose   23  Santo Domingo
...
```

**Explicación:**
1. **`data['Edad'].str.startswith('2')`**: Intenta verificar si las edades comienzan con '2', pero `'Edad'` es numérica (`int64`), no una cadena. Esto generará un error (`AttributeError`) a menos que las edades ya estén como texto en el CSV.
2. **Nota**: La salida proporcionada sugiere que el código funcionó, lo cual implica que `'Edad'` podría estar como cadena en este caso específico. Normalmente, deberíamos convertirla con `data['Edad'].astype(str).str.startswith('2')`.

**Propósito**: Resalta la importancia de entender los tipos de datos. Aquí asumimos que `'Edad'` es texto para que el código tenga sentido.

---

### **Paso 8: Filtrar nombres que terminen con 'y'**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro = data['Nombre'].str.endswith('y')

resultado_filtro = data.loc[filtro]
print(resultado_filtro)
```

**Salida:**
```
    Nombre Edad  Ciudad
1   Jeremy   22  Higuey
...
```

**Explicación:**
1. **`data['Nombre'].str.endswith('y')`**: Serie booleana para nombres que terminan en 'y'.
2. **`data.loc[filtro]`**: Selecciona esas filas.

**Propósito**: Otro ejemplo de filtrado de texto, ahora buscando el final de las cadenas.

---

### **Paso 9: Filtrar ciudades que terminen con 'a'**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro = data['Ciudad'].str.endswith('a')

resultado_filtro = data.loc[filtro]
print(resultado_filtro)
```

**Salida:**
```
   Nombre Edad   Ciudad
0   Mario   21  La Vega
...
```

**Explicación:**
1. **`data['Ciudad'].str.endswith('a')`**: Busca ciudades que terminan en 'a'.
2. **`data.loc[filtro]`**: Filtra las filas.

**Propósito**: Extiende el filtrado a otra columna, mostrando la versatilidad de estas técnicas.

---

### **Paso 10: Filtrar nombres que contengan 'o'**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro = data['Nombre'].str.contains('o')

resultado_filtro = data.loc[filtro]
print(resultado_filtro)
```

**Salida:**
```
    Nombre  Edad         Ciudad
0    Mario    21        La Vega
2     Jose    23  Santo Domingo
...
```

**Explicación:**
1. **`data['Nombre'].str.contains('o')`**: Busca la subcadena 'o' en los nombres.
2. **`data.loc[filtro]`**: Selecciona las filas correspondientes.

**Propósito**: Introduce `contains`, útil para buscar patrones dentro de las cadenas.

---

### **Paso 11: Filtrar nombres con 'o' o 'm'**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro1 = data['Nombre'].str.contains('o')
filtro2 = data['Nombre'].str.contains('m')

resultado_filtro = data.loc[filtro1 | filtro2]
print(resultado_filtro)
```

**Salida:**
```
    Nombre  Edad         Ciudad
0    Mario    21        La Vega
1   Jeremy    22         Higuey
2     Jose    23  Santo Domingo
...
```

**Explicación:**
1. **`filtro1` y `filtro2`**: Dos Series booleanas separadas.
2. **`filtro1 | filtro2`**: Operador OR (`|`) combina las condiciones (nombres con 'o' o 'm').
3. **`data.loc[filtro1 | filtro2]`**: Filtra las filas.

**Propósito**: Muestra cómo combinar condiciones lógicas.

---

### **Paso 12: Filtrar nombres con 'r' y 'y'**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro1 = data['Nombre'].str.contains('r')
filtro2 = data['Nombre'].str.contains('y')

resultado_filtro = data.loc[filtro1 & filtro2]
print(resultado_filtro)
```

**Salida:**
```
    Nombre Edad  Ciudad
1   Jeremy   22  Higuey
...
```

**Explicación:**
1. **`filtro1` y `filtro2`**: Condiciones separadas.
2. **`filtro1 & filtro2`**: Operador AND (`&`) requiere que ambas sean ciertas.
3. **`data.loc[filtro1 & filtro2]`**: Filtra las filas.

**Propósito**: Filtrado con múltiples condiciones simultáneas.

---

### **Paso 13: Filtrar edades mayores a '22' (error)**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

filtro = data[data['Edad'] > '22']

print(filtro)
```

**Salida:**
```
    Nombre  Edad         Ciudad
2     Jose    23  Santo Domingo
...
```

**Explicación:**
1. **`data['Edad'] > '22'`**: Intenta comparar la columna `'Edad'` con la cadena `'22'`. Esto es incorrecto porque `'Edad'` es numérica, y la comparación debería ser con un número (`22`), no una cadena (`'22'`).
2. **Nota**: La salida funciona, pero el código tiene un error conceptual. Debería ser `data['Edad'] > 22`.

**Propósito**: Intenta filtrar numéricamente, pero falla en la implementación.

---

### **Paso 14: Filtrar edades mayores a 22 (correcto)**

**Código:**
```python
import pandas as pd

data = pd.read_csv('datos.csv')

data['Edad'] = pd.to_numeric(data['Edad'], errors='coerce')

filtro = data[data['Edad'] > 22]

print(filtro)
```

**Salida:**
```
   Nombre  Edad         Ciudad
2    Jose  23.0  Santo Domingo
...
```

**Explicación:**
1. **`data['Edad'] = pd.to_numeric(data['Edad'], errors='coerce')`**: Convierte `'Edad'` a numérico, manejando valores no válidos (como encabezados) con `NaN`.
2. **`data['Edad'] > 22`**: Comparación numérica correcta.
3. **`data[data['Edad'] > 22]`**: Filtra las filas directamente (alternativa a `loc`).

**Propósito**: Corrige el filtrado numérico, mostrando cómo manejar tipos de datos adecuadamente.

---

### **Evolución del código**

El código evoluciona desde tareas básicas hasta análisis más complejos:
1. **Lectura y visualización**: `print(data)`, `data.head()`.
2. **Selección de columnas**: `data['Nombre']`, `data['Edad']`.
3. **Filtrado de texto**: `startswith`, `endswith`, `contains`.
4. **Condiciones combinadas**: Uso de `|` (OR) y `&` (AND).
5. **Filtrado numérico**: Conversión de tipos y comparaciones (`> 22`).

Cada paso agrega sofisticación, permitiendo análisis más detallados y específicos.

---

### **Conclusión**

Este ejercicio demuestra cómo pandas facilita la manipulación de datos, desde operaciones simples hasta filtrados complejos. La automatización con pandas es poderosa porque nos permite explorar datos de manera rápida, precisa y adaptable, sentando las bases para análisis más avanzados en ciencia de datos o automatización de procesos.