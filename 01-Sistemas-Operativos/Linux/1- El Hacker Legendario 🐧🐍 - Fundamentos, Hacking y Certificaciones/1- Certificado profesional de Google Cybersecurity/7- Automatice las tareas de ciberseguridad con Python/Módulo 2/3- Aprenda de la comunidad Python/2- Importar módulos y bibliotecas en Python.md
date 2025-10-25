
Anteriormente, usted exploró las bibliotecas y módulos. Aprendió que un Módulo es un archivo Python que contiene funciones adicionales, variables, clases y cualquier tipo de código ejecutable. También aprendió que una biblioteca es una colección de módulos que proporcionan código al que los usuarios pueden acceder en sus programas. Se le presentaron algunos módulos de la Biblioteca estándar de Python y un par de bibliotecas externas. En esta lectura, aprenderá a importar un Módulo que existe en la Biblioteca estándar de Python y a utilizar sus funciones. También ampliará sus conocimientos sobre las bibliotecas externas.

### La Biblioteca estándar de Python

La Biblioteca estándar de Python es una extensa colección de código Python que a menudo viene empaquetada con Python. Incluye una variedad de Módulos, cada uno con código pre-construido centrado en un tipo particular de tarea.

Por ejemplo, anteriormente se le presentaron los siguientes módulos de la Biblioteca estándar de Python:

- El módulo `re`, que proporciona funciones utilizadas para la búsqueda de patrones en archivos de registro
    
- El módulo `csv`, que proporciona funciones utilizadas al trabajar con archivos .csv
    
- Los módulos `glob` y `os`, que proporcionan funciones utilizadas al interactuar con la línea de comandos
    
- Los módulos `time` y `datetime`, que proporcionan funciones utilizadas al trabajar con marcas de tiempo
    

Otro módulo de la Biblioteca estándar de Python es `statistics`. El módulo `statistics` incluye funciones utilizadas al calcular estadísticas relacionadas con datos numéricos. Por ejemplo, `mean()` es una función del módulo `statistics` que toma datos numéricos como entrada y calcula su media (o promedio). Además, `median()` es una función del módulo `statistics` que toma datos numéricos como entrada y calcula su mediana (o valor medio).

### Cómo importar módulos desde la Biblioteca estándar de Python

Para acceder a los módulos de la Biblioteca estándar de Python, debe importarlos. Puede elegir entre importar un módulo completo o sólo importar funciones específicas de un módulo.

#### Importar un módulo completo

Para importar un módulo completo de la Biblioteca estándar de Python, utilice la palabra clave `import`. La palabra clave `import` busca un módulo o biblioteca en un sistema y lo añade al entorno local de Python. Después de `import`, especifique el nombre del módulo a importar. Por ejemplo, puede especificar `import statistics` para importar el módulo `statistics`. Esto importará todas las funciones dentro del módulo `statistics` para su uso posterior en su código.

A modo de ejemplo, puede que desee utilizar la función `mean()` del módulo `statistics` para calcular el número medio de intentos fallidos de inicio de sesión al mes de un usuario concreto. En el siguiente bloque de código, el número total de intentos fallidos de inicio de sesión para cada uno de los doce meses se almacena en una Lista llamada `monthly_failed_attempts`. Ejecute este código y analice cómo puede utilizarse `mean()` para calcular la media de estos totales mensuales de inicios de sesión fallidos y almacenarla en `mean_failed_attempts`:

Python

```
import statistics
monthly_failed_attempts = [12, 15, 19, 14, 11, 20, 18, 22, 17, 178, 13, 14]
mean_failed_attempts = statistics.mean(monthly_failed_attempts)
print(mean_failed_attempts)
```

La salida devuelve una media de 31.083... (El texto del ejemplo usa números ilustrativos; este código es funcional). Puede que note el valor periférico de 178 y quiera encontrar también el valor medio. Para hacerlo a través de la función `median()`, puede utilizar el siguiente código:

Python

```
import statistics
monthly_failed_attempts = [12, 15, 19, 14, 11, 20, 18, 22, 17, 178, 13, 14]
median_failed_attempts = statistics.median(monthly_failed_attempts)
print(median_failed_attempts)
```

Esto le da el valor de 17.5 (el valor medio de 17 y 18), que también podría ser útil para analizar las estadísticas de intentos fallidos de inicio de sesión del usuario.

**Nota:** Cuando importe un módulo completo de la Biblioteca estándar de Python, deberá identificar el nombre del módulo con la función al llamarlo. Puede hacerlo colocando el nombre del Módulo seguido de un punto (`.`) antes del nombre de la función. Por ejemplo, los bloques de código anteriores utilizan `statistics.mean()` y `statistics.median()` para llamar a esas funciones.

#### Importar funciones específicas de un módulo

Para importar una función específica de la Biblioteca estándar de Python, puede utilizar la palabra clave `from`. Por ejemplo, si desea importar sólo la función `median()` del módulo `statistics`, puede escribir `from statistics import median`.

Para importar varias funciones de un módulo, puede separar las funciones que desee importar con una coma. Por ejemplo, `from statistics import mean, median` importa tanto la función `mean()` como la `median()` del módulo `statistics`.

Un detalle importante a tener en cuenta es que si importa funciones específicas de un módulo, ya no tendrá que especificar el nombre del módulo antes de dichas funciones. Puede examinar esto en el código siguiente, que importa específicamente sólo las funciones `median()` y `mean()` del módulo `statistics` y realiza los mismos cálculos que los ejemplos anteriores:

Python

```
from statistics import mean, median

monthly_failed_attempts = [12, 15, 19, 14, 11, 20, 18, 22, 17, 178, 13, 14]

mean_failed_attempts = mean(monthly_failed_attempts)
print(mean_failed_attempts)

median_failed_attempts = median(monthly_failed_attempts)
print(median_failed_attempts)
```

Ya no es necesario especificar `statistics.mean()` o `statistics.median()` y en su lugar el código incorpora estas funciones como `mean()` y `median()`.

### Bibliotecas externas

Además de la Biblioteca estándar de Python, también puede descargar bibliotecas externas e incorporarlas a su código Python. Por ejemplo, anteriormente conoció Beautiful Soup (`bs4`) para analizar archivos HTML y NumPy (`numpy`) para matrices y cálculos matemáticos. Antes de utilizarlas en un Notebook de Jupyter o en un entorno Google Colab, deberá instalarlas.

Para instalar una biblioteca, como `numpy`, en cualquiera de los dos entornos, puede ejecutar la siguiente línea antes de importar la biblioteca:

`%pip install numpy`

Esto instala la biblioteca para que pueda utilizarla en su bloc de notas.

Una vez instalada una biblioteca, puede importarla directamente a Python utilizando la palabra clave `import` de forma similar a como la utilizó para importar módulos de la Biblioteca estándar de Python. Por ejemplo, tras la instalación de `numpy`, puede utilizar este código para importarla:

`import numpy`

### Puntos clave

La Biblioteca estándar de Python contiene muchos módulos que puede importar, entre ellos `re`, `csv`, `os`, `glob`, `time`, `datetime` y `statistics`. Para importar estos módulos, debe utilizar la palabra clave `import`. La Sintaxis varía en función de si desea importar todo el Módulo o sólo funciones específicas del mismo. Las bibliotecas externas también se pueden importar en Python, pero es necesario instalarlas primero.