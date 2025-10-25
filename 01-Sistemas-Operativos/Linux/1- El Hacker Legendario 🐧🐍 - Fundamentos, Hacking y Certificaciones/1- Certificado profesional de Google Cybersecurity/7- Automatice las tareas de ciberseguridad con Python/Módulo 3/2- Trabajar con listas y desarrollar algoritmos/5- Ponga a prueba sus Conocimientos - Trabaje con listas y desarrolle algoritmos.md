
## 🧠 Pregunta 1

Revise el siguiente código:

Python

```
my_list = ["a", "b", "c", "d"]
my_list[2] = 4
print(my_list)
```

¿Qué mostrará?

✅ **Respuesta correcta:** `["a", "b", 4, "d"]`

📘 Explicación:

Las listas son mutables. La línea my_list[2] = 4 accede al elemento en el índice 2 (que es "c") y lo reemplaza con el valor entero 4.

---

## 🧠 Pregunta 2

Está trabajando con la lista `["cwvQSQ", "QvPvX5", "ISyT3a", "S7vgN0"]`... ¿Qué línea de código añadirá el ID `"yihhLL"` en el índice 3?

✅ **Respuesta correcta:** `machine_ids.insert(3, "yihhLL")`

📘 Explicación:

El método .insert() se usa para añadir un elemento en un índice específico. Su sintaxis es lista.insert(indice, elemento). Los elementos existentes desde ese índice en adelante se desplazarán a la derecha.

---

## 🧠 Pregunta 3

¿Qué línea de programación eliminará el nombre de usuario "tshah" de la siguiente Lista?

access_list = ["elarson", "bmoreno", "tshah", "sgilmore"]

✅ **Respuesta correcta:** `access_list.remove("tshah")`

📘 Explicación:

El método .remove() elimina la primera aparición del valor especificado dentro de la lista. No utiliza el índice.

---

## 🧠 Pregunta 4

Como analista de Seguridad, usted es responsable de desarrollar un algoritmo que automatice la eliminación de nombres de usuario que coincidan con criterios específicos de una lista de acceso. ¿Qué componentes de Python le ayudarían a implementarlo? (Seleccione tres).

✅ **Respuestas correctas:**

- Un Bucle `for` que itera a través de los nombres de usuario de la Lista de acceso.
    
- Una declaración `if` que compara un nombre de usuario con los criterios de eliminación.
    
- El método `.remove()`.
    

📘 **Explicación:**

1. Necesitas un **bucle `for`** para examinar cada `username` en la `access_list`.
    
2. Dentro del bucle, necesitas una **sentencia `if`** para verificar si el `username` actual cumple los criterios de eliminación.
    
3. Si la condición del if es verdadera, necesitas usar el método .remove() para eliminar ese username de la lista.
    
    (El método .append() se usa para añadir elementos, no para eliminar).


---

# Mejores Justificaciones


---

### 🧠 Pregunta 1

Revise el siguiente código:

Python

```
my_list = ["a", "b", "c", "d"]
my_list[2] = 4
print(my_list)
```

¿Qué mostrará?

- `["a", "b", 4, "d"]`
    
- `["a", 4, "c", "d"]`
    
- `["a", "b", "4", "d"]`
    
- Un mensaje de error
    

✅ Respuesta correcta:

["a", "b", 4, "d"]

📘 Explicación:

El Código mostrará ["a", "b", 4, "d"]. Reasigna el elemento my_list en el índice 2. Se trata del tercer elemento de la lista (recordando que los índices empiezan en 0), por lo que "c" se sustituye por el entero 4.

---

### 🧠 Pregunta 2

Está trabajando con la lista `["cwvQSQ", "QvPvX5", "ISyT3a", "S7vgN0"]`. Sus elementos representan IDs de máquinas, y la lista se almacena en una variable llamada `machine_ids`. ¿Qué línea de código añadirá el ID de `"yihhLL"` en el índice 3?

- `machine_ids.insert(3, "yihhLL")`
    
- `machine_ids.insert("yihhLL", 3)`
    
- `machine_ids.append("yihhLL", 3)`
    
- `machine_ids.append("yihhLL")`
    

✅ Respuesta correcta:

machine_ids.insert(3, "yihhLL")

📘 Explicación:

El Código machine_ids.insert(3, "yihhLL") añadirá el ID "yihhLL" en el índice 3. El método .insert() añade un elemento en una posición específica dentro de una lista. Recibe dos parámetros: el primero indica el índice en el que desea añadir un nuevo elemento (3), y el segundo indica el elemento que desea añadir ("yihhLL").

---

### 🧠 Pregunta 3

¿Qué línea de programación eliminará el nombre de usuario "tshah" de la siguiente Lista?

access_list = ["elarson", "bmoreno", "tshah", "sgilmore"]

- `access_list.remove("tshah")`
    
- `access_list.remove(3)`
    
- `access_list["tshah"].remove()`
    
- `access_list.remove(2)`
    

✅ Respuesta correcta:

access_list.remove("tshah")

📘 Explicación:

El código access_list.remove("tshah") eliminará el nombre de usuario "tshah" de la lista. El método .remove() elimina la primera aparición de un elemento específico (por su valor) en una lista. Toma como argumento el elemento a eliminar, así access_list.remove("tshah") elimina el nombre de usuario "tshah".

---

### 🧠 Pregunta 4

Como analista de Seguridad, usted es responsable de desarrollar un algoritmo que automatice la eliminación de nombres de usuario que coincidan con criterios específicos de una lista de acceso. ¿Qué componentes de Python le ayudarían a implementarlo? (Seleccione tres).

- Un Bucle `for` que itera a través de los nombres de usuario de la Lista de acceso.
    
- Una declaración `if` que compara un nombre de usuario con los criterios de eliminación.
    
- El método `.append()`.
    
- El método `.remove()`.
    

✅ **Respuestas correctas:**

- Un Bucle `for` que itera a través de los nombres de usuario de la Lista de acceso.
    
- Una declaración `if` que compara un nombre de usuario con los criterios de eliminación.
    
- El método `.remove()`.
    

📘 Explicación:

El algoritmo debe iterar a través de los nombres de usuario en una Lista de accesibilidad. En cada iteración, debe comprobar si el nombre de usuario actual coincide con los criterios específicos y eliminarlo cuando así sea.

1. El **Bucle `for`** itera a través de los nombres de usuario de la Lista de acceso.
    
2. La **sentencia `if`** comprueba si el nombre de usuario actual coincide con los criterios específicos.
    
3. El método .remove() elimina la primera aparición de los nombres de usuario que coinciden con los criterios.
    
    (El método .append() se usa para añadir elementos, no para eliminar).