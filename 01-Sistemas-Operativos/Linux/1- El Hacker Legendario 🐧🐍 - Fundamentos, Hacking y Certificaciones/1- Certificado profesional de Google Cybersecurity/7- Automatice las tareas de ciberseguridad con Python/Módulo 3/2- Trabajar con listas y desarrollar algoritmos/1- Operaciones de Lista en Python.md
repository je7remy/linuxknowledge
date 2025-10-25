
### 🧠 Introducción a las Listas en Python

Otro tipo de datos del que hemos hablado anteriormente es la **lista**. Las listas son útiles porque le permiten almacenar múltiples datos en una sola variable.

En la profesión de la seguridad, trabajará con una gran variedad de listas. Por ejemplo, puede tener una lista de direcciones IP que han accedido a una red, y otra lista puede contener información sobre aplicaciones que tienen bloqueada su ejecución en el sistema.

---

### 📘 Repaso: Creación de Listas

Recapitulemos cómo crear una lista en Python.

- **Sintaxis:** Los elementos se separan mediante comas y se rodean de corchetes `[]`.
    
- **Ejemplo:**
    
    Python
    
    ```
    mi_lista = ['a', 'b', 'c', 'd', 'e']
    ```
    
    (Aquí, hemos asignado nuestra lista a una variable para facilitar su uso posterior).
    

---

### ⚙️ Acceso a Elementos (Indexación)

Cuando accedemos a elementos específicos de las listas utilizamos una sintaxis similar a cuando accedemos a los elementos específicos de las cadenas. Colocamos su valor de índice entre corchetes `[]` después de la variable que almacena la lista.

> **Regla Clave:** En Python, empezamos a contar los elementos de la lista en **cero** (0).

Así accederíamos al **segundo** elemento de la lista (que está en el **índice 1**):

Python

```
mi_lista = ['a', 'b', 'c', 'd', 'e']

# Extraeremos el segundo elemento poniendo 1 entre corchetes
print(mi_lista[1])
```

📤 **Salida:**

```
b
```

---

### ⚙️ Concatenación de Listas (`+`)

Al igual que con las cadenas, también podemos **concatenar** listas con el signo más (`+`).

- **Definición:** La **concatenación de listas** consiste en combinar dos listas en una colocando los elementos de la segunda lista directamente después de los elementos de la primera.
    

**Ejemplo:**

Python

```
# Definimos la misma lista que en el ejemplo anterior
mi_lista = ['a', 'b', 'c', 'd', 'e']

# Definimos una lista adicional con números
otra_lista = [1, 2, 3, 4]

# Concatenamos las dos listas con un signo más
lista_concatenada = mi_lista + otra_lista

# Imprimimos el resultado
print(lista_concatenada)
```

📤 **Salida:**

```
['a', 'b', 'c', 'd', 'e', 1, 2, 3, 4]
```

---

### ⚠️ Listas vs. Cadenas: Mutabilidad

Habiendo discutido las similitudes, exploremos ahora las diferencias entre las listas y las cadenas.

- **Cadenas:** Son **inmutables** (no pueden modificarse una vez definidas).
    
- **Listas:** Son **mutables**. Podemos cambiar, añadir y eliminar libremente valores de la lista después de crearla.
    

Así, por ejemplo, si tenemos una lista de direcciones IP maliciosas, cada vez que se identifique una nueva, podemos añadirla fácilmente a la lista.

---

### ⚙️ Modificación de Listas (Mutabilidad en Acción)

#### Cambiar un Elemento Específico (Usando Índice)

Intentemos primero cambiar un elemento específico de una lista en Python. Empezaremos con la lista utilizada en el ejemplo anterior. Para cambiar un elemento, combinamos la notación entre corchetes con la asignación de variables (`=`).

**Ejemplo:** Cambiemos el segundo elemento de `mi_lista` (la cadena `"b"`, en el índice 1) por el número `7`.

Python

```
mi_lista = ['a', 'b', 'c', 'd', 'e']

# Colocamos el objeto que queremos cambiar (mi_lista[1]) a la izquierda
# Colocamos el nuevo valor (7) a la derecha
mi_lista[1] = 7

# Imprimamos la lista para examinar el cambio
print(mi_lista)
```

📤 **Salida:**

```
['a', 7, 'c', 'd', 'e']
```

¡Perfecto! La letra `"b"` se ha cambiado ahora por el número `7`.

---

### 📘 Métodos de Lista (Insertar y Eliminar)

Ahora, echemos un vistazo a los métodos para insertar y eliminar elementos en las listas.

#### El Método `.insert()`

- **Definición:** El método **`.insert()`** añade un elemento en una **posición específica** dentro de una lista.
    
- **Argumentos:** Toma dos argumentos:
    
    1. El **índice** (posición) donde se añadirá el elemento.
        
    2. El **elemento** que queremos añadir.
        
- **Comportamiento:** Los elementos existentes a partir de ese índice se **desplazan** una posición hacia la derecha (no se reemplazan).
    

**Ejemplo:** Insertemos el número entero `7` en el índice `1`.

Python

```
mi_lista = ['a', 'b', 'c', 'd', 'e']

# Pasamos el índice (1) y el elemento (7)
mi_lista.insert(1, 7)

# Imprimamos mi_lista
print(mi_lista)
```

📤 **Salida:**

```
['a', 7, 'b', 'c', 'd', 'e']
```

Nuestra lista sigue empezando con `"a"` (índice 0), y ahora tenemos el entero `7` en la siguiente posición (índice 1). Note que la letra `"b"`, que originalmente estaba en el índice 1, no se sustituye. Con el método `.insert()`, cada elemento más allá del índice 1 simplemente se desplaza una posición hacia abajo (`"b"` está ahora en el índice 2).

#### El Método `.remove()`

A veces puede que queramos eliminar de una lista un elemento que ya no es necesario.

- **Definición:** El método **`.remove()`** elimina la **primera aparición** de un **elemento específico** en la lista.
    
- **Argumento:** A diferencia de `.insert()`, el argumento de `.remove()` **no es un valor de índice**. En su lugar, se escribe directamente el **elemento** que se desea eliminar.
    
- **Comportamiento:** Solo elimina la _primera_ instancia del elemento si este aparece varias veces.
    

**Ejemplo:** Eliminemos la letra `"d"` de nuestra lista.

Python

```
mi_lista = ['a', 'b', 'c', 'd', 'e']

# Añadimos el método remove después de la variable
# Pasamos el elemento a eliminar ("d") como argumento
mi_lista.remove("d")

# Imprimimos mi_lista
print(mi_lista)
```

📤 **Salida:**

```
['a', 'b', 'c', 'e']
```

¡Perfecto! `"d"` ha sido eliminada de la lista.

---

### 💡 Conclusión

Al igual que con las cadenas, ser capaz de buscar y manipular listas es una habilidad necesaria para los analistas de Seguridad. Estoy deseando ampliar nuestros conocimientos a medida que avancemos en este curso.



---


### 🧠 Pregunta

En la Lista `["elarson", "bmoreno", "tshah", "eraab"]`, ¿qué elemento tiene un índice de 3?

- `"eraab"`
    
- `"elarson"`
    
- `"bmoreno"`
    
- `"tshah"`
    

---

### ✅ Respuesta correcta:

`"eraab"`

### 📘 Explicación:

En la Lista `["elarson", "bmoreno", "tshah", "eraab"]`, el elemento `"eraab"` tiene un índice de 3. En Python, los índices comienzan en 0, por lo que el elemento que tiene un índice de 3 es el **cuarto** elemento.

|**Elemento**|**Índice**|
|---|---|
|"elarson"|0|
|"bmoreno"|1|
|"tshah"|2|
|**"eraab"**|**3**|