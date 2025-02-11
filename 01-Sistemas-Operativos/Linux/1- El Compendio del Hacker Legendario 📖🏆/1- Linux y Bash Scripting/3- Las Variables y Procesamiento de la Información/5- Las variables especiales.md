# Las variables especiales | $?, $# y $@

El tema de esta explicación es comprender y usar las **variables especiales** en bash, como `$?`, `$#` y `$@`. Estas variables proporcionan información clave durante la ejecución de scripts en Bash.

### Paso 1: La variable `$?`

La variable especial `$?` representa el código de retorno del último comando ejecutado. Los códigos de retorno en Linux indican si un comando se ejecutó correctamente o falló.

- **Código de retorno `0`**: El comando se ejecutó correctamente.
- **Códigos diferentes de `0`**: Hubo un error.

#### Ejemplo 1:

```bash
pwd  # Comando para mostrar el directorio actual.
echo $?  # Muestra el código de retorno del comando anterior.
```

**Resultado**:

```
/home/user
0
```

Esto indica que el comando `pwd` fue exitoso.

### Paso 2: La variable `$#`

La variable `$#` contiene el **número de argumentos** pasados a un script o comando. Es útil para verificar cuántos argumentos se proporcionaron al ejecutar un script.

#### Ejemplo 2:

```bash
nano script.sh
```

Contenido del script:

```bash
#!/bin/bash
echo "Número de argumentos: $#"
```

Ejecución:

```bash
./script.sh 1 2 3 4
```

**Resultado**:

```
Número de argumentos: 4
```

El script recibió cuatro argumentos.

### Paso 3: La variable `$@`

La variable `$@` representa **todos los argumentos** pasados a un script o comando, como una lista. Es útil para iterar sobre los argumentos.

#### Ejemplo 3:

```bash
nano script.sh
```

Contenido del script:

```bash
#!/bin/bash
echo "Argumentos: $@"
```

Ejecución:

```bash
./script.sh 1 2 3 4
```

**Resultado**:

```
Argumentos: 1 2 3 4
```

La variable `$@` muestra cada argumento como una cadena separada por espacios.

---

### Aplicación Práctica

Supongamos que queremos verificar el número de argumentos pasados y listar sus valores. Aquí hay un ejemplo más completo:

```bash
#!/bin/bash
if [ $# -eq 0 ]; then
    echo "No se han pasado argumentos."
    exit 1
fi

echo "Número de argumentos: $#"
echo "Lista de argumentos: $@"

for arg in "$@"; do
    echo "Argumento: $arg"
done
```

#### Ejecución:

```bash
./script.sh uno dos tres
```

**Resultado**:

```
Número de argumentos: 3
Lista de argumentos: uno dos tres
Argumento: uno
Argumento: dos
Argumento: tres
```

### Resumen

- `$?`: Código de retorno del último comando.
- `$#`: Número de argumentos pasados al script.
- `$@`: Lista de todos los argumentos.

Estos ejemplos demuestran cómo aprovechar estas variables para scripts dinámicos y adaptables.
