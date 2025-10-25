
Anteriormente, se centró en el trabajo con múltiples parámetros y argumentos en las funciones y en la devolución de información desde las funciones. En esta lectura, repasará estos conceptos. También conocerá un nuevo concepto: las variables globales y locales.

## Trabajar con variables en funciones

Trabajar con variables en funciones requiere comprender tanto los parámetros como los argumentos. Los términos parámetros y argumentos tienen usos distintos cuando se refieren a variables en una función. Además, si desea que la función devuelva un resultado, debe estar familiarizado con las sentencias return.

### Parámetros

Un **parámetro** es un objeto que se incluye en la definición de una función para utilizarlo en ella. Cuando define una función, crea variables en la cabecera de la función. A continuación, pueden utilizarse en el cuerpo de la función. En este contexto, estas variables se denominan parámetros. Por ejemplo, considere la siguiente función:

Python

```
def remaining_login_attempts(maximum_attempts, total_attempts):
    print(maximum_attempts - total_attempts)
```

Esta función toma dos variables, `maximum_attempts` y `total_attempts` y las utiliza para realizar un cálculo. En este ejemplo, `maximum_attempts` y `total_attempts` son parámetros.

### Argumentos

En Python, un **argumento** son los datos que se introducen en una función cuando se llama a ella. Al llamar a `remaining_login_attempts` en el siguiente ejemplo, los enteros `3` y `2` se consideran argumentos:

Python

```
remaining_login_attempts(3, 2)
```

Estos enteros pasan a la función a través de los parámetros que se identificaron al definir la función. En este caso, esos parámetros serían `maximum_attempts` y `total_attempts`. `3` está en la primera posición, por lo que pasa a `maximum_attempts`. Del mismo modo, `2` está en la segunda posición y pasa a `total_attempts`.

### Sentencias de retorno

Cuando se definen funciones en Python, se utilizan sentencias de retorno si se desea que la función devuelva una salida. La palabra clave `return` se utiliza para devolver información de una función.

La palabra clave `return` aparece delante de la información que desea devolver. En el siguiente ejemplo, está antes del cálculo de cuántos intentos de inicio de sesión quedan:

Python

```
def remaining_login_attempts(maximum_attempts, total_attempts):
    return maximum_attempts - total_attempts
```

**Nota:** La palabra clave `return` no es una función, por lo que no debe colocar paréntesis después de ella.

Las sentencias de retorno son útiles cuando desea almacenar lo que devuelve una función dentro de una variable para utilizarlo en otra parte del código. Por ejemplo, puede utilizar esta variable para cálculos o dentro de sentencias condicionales. En el siguiente ejemplo, la información devuelta por la llamada a `remaining_login_attempts` se almacena en una variable llamada `remaining_attempts`. A continuación, esta variable se utiliza en una condicional que imprime un mensaje "Your account is locked" cuando `remaining_attempts` es menor o igual que 0. Puede ejecutar este código para explorar su resultado:

Python

```
def remaining_login_attempts(maximum_attempts, total_attempts):
    return maximum_attempts - total_attempts

remaining_attempts = remaining_login_attempts(3, 3)

if remaining_attempts <= 0:
    print("Your account is locked")
```

En este ejemplo, el mensaje se imprime porque el cálculo en la función da como resultado 0.

**Nota:** Cuando Python encuentra una sentencia `return`, ejecuta esta sentencia y luego sale de la función. Si hay líneas de código que siguen a la sentencia `return` dentro de la función, no se ejecutarán. El ejemplo anterior no contenía ninguna línea de código después de la sentencia `return`, pero esto podría aplicarse en otras funciones, como una que contenga una sentencia condicional.

## Variables globales y locales

Para entender mejor cómo interactúan las funciones con las variables, debe conocer la diferencia entre variables globales y locales.

Cuando define y llama a funciones, está trabajando con variables locales, que son diferentes de las variables que define fuera del ámbito de una función.

### Variables globales

Una **variable global** es una variable que está disponible en todo el programa. Las variables globales se asignan fuera de la definición de una función. Siempre que se llame a esa variable, ya sea dentro o fuera de una función, devolverá el valor que se le haya asignado.

Por ejemplo, puede asignar la siguiente variable al principio de su código:

`device_id = "7ad2130bd"`

A lo largo del resto de su código, podrá acceder a la variable `device_id` y modificarla en condicionales, bucles, funciones y otras sintaxis.

### Variables locales

Una **variable local** es una variable asignada dentro de una función. No se puede llamar a estas variables ni acceder a ellas fuera del cuerpo de una función. Las variables locales incluyen parámetros, así como otras variables asignadas dentro de la definición de una función.

En la siguiente definición de función, `total_string` y `name` son variables locales:

Python

```
def greet_employee(name):
    total_string = "Welcome" + name
    return total_string
```

La variable `total_string` es una variable local porque está asignada dentro de la función. El parámetro `name` es una variable local porque también se crea al definir la función.

Cada vez que llama a una función, Python crea estas variables temporalmente mientras la función se está ejecutando y las borra de la memoria después de que la función deja de ejecutarse.

Esto significa que si llama a la función `greet_employee()` con un argumento y luego utiliza la variable `total_string` fuera de esta función, obtendrá un error.

### Mejores prácticas para variables globales y locales

Cuando trabaje con variables y funciones, es muy importante que se asegure de que sólo utiliza un determinado nombre de variable una vez, aunque una esté definida globalmente y la otra localmente.

Al utilizar variables globales dentro de las funciones, éstas pueden acceder a los valores de una variable global. Puede ejecutar el siguiente ejemplo para explorar esto:

Python

```
# Create a global variable `username`
username = "elarson"

def identify_user():
    print(username)

# Call the function `identify_user()`
identify_user()
```

_Salida:_

```
elarson
```

El bloque de código devuelve "elarson" aunque ese nombre no esté definido localmente. La función accede a la variable global. Si quisiera que la función `identify_user()` diera cabida a otros nombres de usuario, tendría que reasignar la variable global de nombre de usuario fuera de la función. Esto no es una buena práctica. Una forma mejor de pasar diferentes valores a una función es utilizar un parámetro en lugar de una variable global.

También hay algo más a tener en cuenta. Si reutiliza el nombre de una variable global dentro de una función, se creará una nueva variable local con ese nombre. En otras palabras, habrá tanto una variable global con ese nombre como una variable local con ese nombre, y tendrán valores diferentes. Puede considerar el siguiente bloque de código:

Python

```
# Create a global variable `username`
username = "elarson"
print(username)

def identify_user():
    # Create a local variable `username`
    username = "bmoreno"
    print(username)

# Call the function `identify_user()`
identify_user()
print(username)
```

_Salida:_

```
elarson
bmoreno
elarson
```

La primera sentencia de impresión se produce antes de la función, y Python devuelve el valor de la variable global `username`, "elarson". La segunda sentencia `print` está dentro de la función, y devuelve el valor de la variable local `username`, que es "bmoreno". Pero esto no cambia el valor de la variable global, y cuando `username` se imprime por tercera vez después de la llamada a la función, sigue siendo "elarson".

Debido a esta complejidad, es mejor evitar combinar variables globales y locales dentro de las funciones.

## Puntos clave

Trabajar con variables en funciones requiere comprender varios conceptos. Un parámetro es un objeto que se incluye en la definición de una función para su uso en esa función, un argumento son los datos que se introducen en una función cuando se llama a ella, y la palabra clave `return` se utiliza para devolver información de una función. Además, las variables globales son variables accesibles en todo el programa, y las variables locales son parámetros y variables asignados dentro de una función que no son utilizables fuera de ella. Es importante asegurarse de que todas sus variables tienen nombres distintos, incluso si una es una variable local y la otra es una variable global.