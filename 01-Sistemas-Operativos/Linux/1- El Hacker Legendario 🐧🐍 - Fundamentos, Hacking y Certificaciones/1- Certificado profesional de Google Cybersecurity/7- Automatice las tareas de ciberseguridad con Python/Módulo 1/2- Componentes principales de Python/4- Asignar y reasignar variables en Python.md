
Anteriormente, has explorado las variables y cómo asignarlas y reasignarlas en Python. En esta lectura, ampliarás tu comprensión de estos temas. También aprenderás sobre la práctica general de nombrar variables para evitar errores de sintaxis y mejorar la legibilidad del código.

## ¿Qué son las variables?

En un lenguaje de programación, una **variable** es un contenedor que almacena datos. Es una ubicación de almacenamiento con nombre en la memoria de un ordenador que puede contener un valor. Almacena los datos en un tipo de datos particular, como entero, cadena o booleano. El valor que se almacena en una variable puede cambiar.

Puedes pensar en las variables como cajas con etiquetas. Aunque cambie el contenido de una caja, la etiqueta de la caja no cambia. Del mismo modo, cuando se cambia el valor almacenado en una variable, el nombre de la variable sigue siendo el mismo.

Los analistas de seguridad que trabajan en Python utilizarán una variedad de variables. Algunos ejemplos incluyen variables para intentos de acceso, listas de permitidos y direcciones.

## Trabajar con variables

En Python, es importante saber cómo asignar variables y cómo reasignarlas.

### **Asignación y reasignación de variables**

Si quieres crear una variable llamada username y asignarle un valor de "nzhao", coloca la variable a la izquierda del signo igual y su valor a la derecha:

# Assign 'username'

username = "nzhao"

Si más tarde reasignas este nombre de usuario a "zhao2", seguirás refiriéndote a ese contenedor de variables como username.

# Reassign 'username'

username = "zhao2"

Aunque el contenido haya cambiado de "nzhao" a "zhao2", la variable username sigue siendo la misma.

**Nota:** Debes poner "nzhao" y "zhao2" entre comillas porque son cadenas. Python asigna automáticamente a una variable su tipo de datos cuando se ejecuta. Por ejemplo, cuando la variable username contiene la cadena "nzhao", se le asigna un tipo de datos cadena.

### **Asignación de variables a variables**

Utilizando un proceso similar, también puedes asignar variables a otras variables. En el siguiente ejemplo, la variable username se asigna a una nueva variable old_username:

# Assign a variable to another variable

username = "nzhao"

old_username = username

Como username contiene el valor de cadena de "nzhao" y old_username contiene el valor de username, old_username contiene ahora un valor de "nzhao".

### **Montaje**

El siguiente código demuestra cómo se puede actualizar un nombre de usuario. A la variable username se le asigna un valor inicial, que se almacena en una segunda variable llamada old_username. A continuación, se reasigna un nuevo valor a la variable username. Puedes ejecutar este código para obtener un mensaje sobre el nombre de usuario anterior y el actual:

username = "nzhao"

old_username = username

username = "zhao2"

print("Previous username:", old_username)

print("Current username:", username)

---
Previous username: nzhao 
Current username: zhao2

## Mejores prácticas para nombrar variables

Puedes nombrar una variable casi como quieras, pero hay algunas pautas que debes seguir para asegurar una sintaxis correcta y prevenir errores:

- Utilice sólo letras, números y guiones bajos en los nombres de las variables. Ejemplos válidos: date_3, username, interval2
    
- Recuerda que los nombres de variables en Python distinguen entre mayúsculas y minúsculas. Estas son variables diferentes: time, Time, TIME, timE.
    
- No uses palabras clave o funciones incorporadas en Python para nombres de variables. Por ejemplo, las variables no deberían llamarse True, False, o if.
    

Además, debes seguir estas pautas de estilo para que tu código sea más fácil de leer y entender para ti y para otros analistas de seguridad:

- Separe dos o más palabras con guiones bajos. Ejemplos válidos: login_attemptsinvalid_user_,_ status_update
    
- Evite variables con nombres similares. Estas variables podrían confundirse fácilmente entre sí: start_time, starting_time, time_starting.
    
- Evita nombres innecesariamente largos para las variables. Por ejemplo, no dé a las variables nombres como variable_that_equals_3.
    
- Los nombres deben describir los datos y no ser palabras al azar. Ejemplos válidos: num_login_attempts, device_id, invalid_usernames
    

**Nota**: Se recomienda utilizar guiones bajos para separar varias palabras en las variables, pero otra convención que puede encontrarse es escribir en mayúscula la primera letra de cada palabra excepto la primera. Ejemplo: loginAttempt

## Puntos clave

Es importante que los analistas de seguridad tengan una comprensión fundamental de las variables. Las variables son contenedores de datos. Se les asignan valores y también se les pueden reasignar otros valores o variables. Es útil recordar las mejores prácticas para nombrar variables con el fin de crear un código más funcional y legible.

