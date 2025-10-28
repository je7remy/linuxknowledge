
### 🐛 Depuración de Código Python

Anteriormente, usted examinó tres tipos de errores que puede encontrar mientras trabaja en Python y exploró estrategias para depurar estos errores. Esta lectura explora estos conceptos con estrategias adicionales y ejemplos para depurar código Python.

#### Tipos de errores

Es una parte normal del desarrollo de código en Python recibir mensajes de error o descubrir que el código que estás ejecutando no está funcionando como debería. Lo importante es que sepas cómo solucionar los errores cuando se producen. Entender los tres tipos principales de errores puede ayudar. Estos tipos incluyen **errores de sintaxis**, **errores lógicos** y **excepciones**.

#### Errores de sintaxis

Un **error de sintaxis** (`SyntaxError`) es un error que implica un uso no válido de un lenguaje de programación. Ocurre cuando hay un error con la sintaxis de Python en sí. Ejemplos comunes incluyen olvidar un signo de puntuación (como un corchete de cierre `]` para una lista o dos puntos `:` después del encabezado de una función).

Cuando ejecutas código con errores de sintaxis, la salida identificará la localización del error con el número de línea y una porción del código afectado. También describe el error. Los errores de sintaxis suelen comenzar con la etiqueta `"SyntaxError:"`. A continuación, sigue una descripción del error (ej. `"invalid syntax"`). Si olvida un paréntesis de cierre, podría ser `"unexpected EOF while parsing"` ("EOF" significa "fin de archivo").

El siguiente código contiene un error de sintaxis. Ejecútalo y examina su salida:

Python

```
# Error: Falta la comilla de cierre
message = "Iniciando análisis...
print(message)
```

_(Al ejecutar esto, se produciría un `SyntaxError`)_

Aparece el mensaje `"SyntaxError: EOL while scanning string literal"`. "EOL" significa "fin de línea". El mensaje de error también indica que el error se produce en la primera línea. El error se produjo porque faltaba una comilla al final de la cadena de la primera línea. Puede solucionarlo añadiendo esa comilla.

**Nota:** A veces encontrará la etiqueta de error `"IndentationError"` en lugar de `"SyntaxError"`. `"IndentationError"` es una subclase de `"SyntaxError"` que se produce cuando la sangría utilizada con una línea de código no es sintácticamente correcta.

#### Errores lógicos

Un **Error lógico** es un error que se produce cuando la lógica utilizada en el código produce resultados no deseados. Los errores lógicos **pueden no producir mensajes de error**. El código no hará lo que se espera, pero sigue siendo válido para el intérprete.

Por ejemplo, usar el operador incorrecto (`>=` en lugar de `>`) puede resultar en un error lógico. Python no evaluará la condición como usted pretendía, pero el código se ejecutará sin error.

El siguiente ejemplo muestra un mensaje relacionado con si un usuario ha alcanzado o no un número máximo de cinco intentos de inicio de sesión. La condición en la sentencia `if` debería ser `login_attempts < 5`, pero está escrita como `login_attempts >= 5`. Se ha asignado un valor de `5` a `login_attempts` para explorar lo que muestra:

Python

```
login_attempts = 5

# Error lógico: Debería ser < 5 para el mensaje "no alcanzado"
if login_attempts >= 5:
    print("User has reached maximum number of login attempts.")
else:
    print("User has not reached maximum number of login attempts.")
```

📤 **Salida (Incorrecta debido al error lógico):**

```
User has reached maximum number of login attempts.
```

_(El texto original tenía el resultado inverso, este código refleja la condición escrita)_. La lógica es incorrecta si el objetivo era mostrar "no alcanzado" _antes_ de llegar a 5. Si el límite es 5, entonces `login_attempts >= 5` debería indicar "alcanzado". El error está en la intención vs. el código. _Si la intención era mostrar "no alcanzado" cuando es menor que 5, el `if` está mal._

Los errores lógicos también pueden producirse al asignar un valor incorrecto o por errores de sangría que cambian el flujo de ejecución.

#### Excepciones

Una **excepción** es un error que implica que el código no puede ejecutarse aunque sea sintácticamente correcto. Esto ocurre por varias razones durante la _ejecución_.

Una causa común es usar una variable no asignada o una función no definida (`NameError`). Después de ejecutar el siguiente código, utilice el mensaje de error para determinar qué variable no fue asignada:

Python

```
# Asumiendo que `check_logins` está definida
# pero `unusual_logins` no ha sido asignada previamente

approved_logins = ["user1", "user2"]

def check_logins(logins):
    count = 0
    for login in logins:
        if login in unusual_logins: # NameError aquí
            count += 1
    return count

# resultado = check_logins(approved_logins) # Esto causaría NameError
# print(resultado)
```

La salida indicaría un `NameError` involucrando la variable `unusual_logins`. Puede solucionarlo asignando un valor a esta variable antes de usarla (ej. `unusual_logins = ["admin", "root"]`).

Otros tipos de excepciones incluyen:

- `"IndexError"`: Acceder a un índice inexistente (ej. `print(usernames[3])` si `usernames = ["bmoreno", "tshah", "elarson"]`).
    
- `"TypeError"`: Usar un tipo de dato incorrecto (ej. `5 + "a"`).
    
- `"FileNotFoundError"`: Intentar abrir un archivo que no existe.
    

---

### 🛠️ Estrategias de depuración

Ten en cuenta que si tienes varios errores, Python mostrará mensajes de error de uno en uno, empezando por el primero que encuentre.

Para errores de sintaxis, los mensajes suelen ser suficientes. Para errores lógicos y excepciones, pueden ser necesarias estrategias adicionales.

#### Depuradores

Puedes escribir código en un **Entorno de desarrollo integrado (IDE)**, que a menudo incluye un **depurador**. Un depurador ayuda a localizar errores usando **puntos de interrupción** (breakpoints), que pausan la ejecución y te permiten inspeccionar el estado del programa (valores de variables) paso a paso.

Herramientas de IA como **Gemini Code Assist** se integran en IDEs populares y pueden ayudar a analizar código, encontrar errores, sugerir modificaciones y responder preguntas. _Recuerda siempre revisar y validar cualquier resultado generado por IA._

#### Utilice instrucciones `print`

Otra estrategia consiste en incorporar sentencias `print` temporales para rastrear el flujo y los valores.

Por ejemplo, el siguiente código tiene un error lógico: intenta añadir nuevos usuarios a una lista de aprobados, pero añade duplicados.

Python

```
approved_users = ["elarson", "bmoreno", "tshah"]
new_users = ["sgilmore", "bmoreno"]

for user in new_users:
    if user in approved_users:
        print(user, "already in list")
    # Error lógico: El append está fuera del else, siempre se ejecuta
    approved_users.append(user)

print(approved_users)
```

📤 **Salida (Incorrecta):**

```
bmoreno already in list
['elarson', 'bmoreno', 'tshah', 'sgilmore', 'bmoreno']
```

Aunque aparece el mensaje `"bmoreno already in list"`, se añade una segunda instancia de `"bmoreno"`. Añadamos sentencias `print` de depuración:

Python

```
approved_users = ["elarson", "bmoreno", "tshah"]
new_users = ["sgilmore", "bmoreno"]

print("line 1 - before loop")
for user in new_users:
    print("line 5 - inside for loop, user:", user)
    if user in approved_users:
        print("line 7 - inside if statement")
        print(user, "already in list")
    # Error lógico: El append está fuera del else, siempre se ejecuta
    print("line 9 - before .append method")
    approved_users.append(user)

print("line 12 - after loop")
print(approved_users)
```

📤 **Salida (con depuración):**

```
line 1 - before loop
line 5 - inside for loop, user: sgilmore
line 9 - before .append method
line 5 - inside for loop, user: bmoreno
line 7 - inside if statement
bmoreno already in list
line 9 - before .append method
line 12 - after loop
['elarson', 'bmoreno', 'tshah', 'sgilmore', 'bmoreno']
```

La sentencia `print "line 9 - before .append method"` sale dos veces. Esto significa que el código llama al método `.append()` para ambos nombres de usuario aunque uno ya esté en `approved_users`. Esto ayuda a aislar el Error lógico a esta área. Esto puede ayudarte a darte cuenta de que la línea `approved_users.append(user)` debería ser el cuerpo de una sentencia `else` para que sólo se ejecute cuando `user` **no** esté en `approved_users`.

---

### 💡 Puntos Clave

Hay tres tipos principales de errores: **Errores de sintaxis** (uso inválido del lenguaje), **Errores lógicos** (resultados no deseados) y **Excepciones** (errores de ejecución con sintaxis válida). Recibirá mensajes de error para errores de sintaxis y excepciones. El uso de **depuradores** y la inserción de **sentencias `print`** pueden ayudarle a identificar errores lógicos y a depurar más las excepciones.