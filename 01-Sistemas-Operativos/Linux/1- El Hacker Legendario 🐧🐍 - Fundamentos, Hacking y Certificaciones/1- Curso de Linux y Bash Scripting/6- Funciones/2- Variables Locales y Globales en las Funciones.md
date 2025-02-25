### Script inicial:

```bash
#!/bin/bash

funcion() {
   variable_global="hola soy una variable global"
   local variable_local="soy una variable local, que solo existe >
}

funcion

echo $variable_global
echo $variable_local
```

#### Desglose:

1. **Definición de la función:**
    
    - `variable_global` se declara como una variable global, lo que significa que su valor está disponible fuera del alcance de la función.
    - `local variable_local`: Define `variable_local` como una variable local, limitada al alcance de la función `funcion`.
2. **Llamada a la función:**
    
    - `funcion` asigna valores a las variables `variable_global` y `variable_local`. Sin embargo, `variable_local` es local y no puede ser usada fuera de la función.
3. **Salida:**
    
    - `echo $variable_global`: Muestra el valor asignado a la variable global.
    - `echo $variable_local`: No imprimirá nada porque `variable_local` solo existe dentro de la función. Fuera de ella, no se reconoce.

**Resultado esperado:**

```plaintext
hola soy una variable global

```

(`variable_local` está vacía).

---

### Segundo script:

```bash
#!/bin/bash

funcion() {
   variable_global="hola soy una variable global"
   local variable_local="soy una variable local, que solo existe >
   echo $variable_local
}

funcion

echo $variable_global
```

#### Desglose:

1. **Diferencia clave:** Dentro de la función, se agrega `echo $variable_local`, que imprime el valor de la variable local antes de que la función termine.
    
2. **Salida:**
    
    - `funcion` imprime el valor de `variable_local` dentro de su propio alcance.
    - Después, fuera de la función, se imprime el valor de `variable_global`.

**Resultado esperado:**

```plaintext
soy una variable local, que solo existe dentro de la función
hola soy una variable global
```

---

### Explicación adicional:

- **Variables locales:** Las variables declaradas con `local` solo existen durante la ejecución de la función y no están disponibles fuera de su alcance.
- **Variables globales:** Estas permanecen accesibles en cualquier parte del script después de ser declaradas.

Esto muestra cómo el alcance de las variables afecta el comportamiento y el resultado de un script Bash.

