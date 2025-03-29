### Comando 1: `fdupes`

```bash
fdupes
```

Este comando ejecuta `fdupes` sin argumentos. No hace nada sin una ruta proporcionada.

---

### Comando 2: `fdupes .`

```bash
fdupes .
```

- **`fdupes .`**: Busca archivos duplicados en el directorio actual (`.`).
- **Salida**: Muestra grupos de archivos duplicados en bloques separados por líneas en blanco. Cada archivo en un grupo tiene contenido idéntico al resto.

---

### Comando 3: `command -v fdupes`

```bash
command -v fdupes
```

- **`command -v`**: Verifica si un comando existe en el sistema.
- **`fdupes`**: Especifica el comando a buscar.
- **Salida**: Si `fdupes` está instalado, devuelve su ruta completa (por ejemplo, `/usr/bin/fdupes`). Si no está instalado, no produce salida y devuelve un código de error.

---

### Comando 4: `fdupes -r .`

```bash
fdupes -r .
```

- **`-r` (recursivo)**: Indica que `fdupes` debe buscar archivos duplicados en el directorio actual y sus subdirectorios.
- **Salida**: Muestra grupos de archivos duplicados en todos los directorios y subdirectorios.

---

### Comando 5: `fdupes -r . | sed 's/^..//'`

```bash
fdupes -r . | sed 's/^..//'
```

- **`fdupes -r .`**: Busca archivos duplicados de forma recursiva.
- **`|`**: Pasa la salida del comando anterior como entrada al siguiente comando.
- **`sed 's/^..//'`**: Usa `sed` para eliminar los dos primeros caracteres de cada línea de salida.

> En este caso, los dos caracteres eliminados suelen ser espacios o caracteres de formato que `fdupes` agrega al inicio de las líneas para marcar grupos de duplicados.

---


### Paso 1: Verificar si `fdupes` está instalado

El script comienza verificando si el comando `fdupes` está disponible en el sistema. Si no está instalado, se informa al usuario y se termina el script.

```bash
if ! command -v fdupes &> /dev/null
then
    echo "fdupes no está instalado. Debes instalarlo mediante 'apt install fdupes' y volver a ejecutar el script."
    exit 1
fi
```

- **`command -v fdupes`**: Comprueba si el comando `fdupes` está en el sistema.
- **`&> /dev/null`**: Redirige la salida estándar y de error para que no se muestre en pantalla.
- **`exit 1`**: Termina el script con un código de error.

---

### Paso 2: Buscar archivos duplicados

Se utiliza el comando `fdupes` con la opción `-r` para buscar archivos duplicados de manera recursiva en el directorio actual (`.`). Luego, `sed` se usa para eliminar los primeros dos caracteres de las líneas que genera `fdupes`.

```bash
archivo=$(fdupes -r . | sed 's/^..//')
```

- **`fdupes -r .`**: Busca archivos duplicados en el directorio actual y sus subdirectorios.
- **`sed 's/^..//'`**: Elimina los dos primeros caracteres de cada línea de salida, que normalmente son espacios o caracteres adicionales.

---

### Paso 3: Leer los archivos duplicados y eliminarlos

El script utiliza un bucle `while` para leer línea por línea cada archivo duplicado encontrado por `fdupes` y los elimina con `rm`.

```bash
echo "$archivo" | while read -r line; do
    rm "$line"
done
```

- **`echo "$archivo"`**: Toma la lista de archivos duplicados generada anteriormente.
- **`while read -r line`**: Lee cada línea de la lista.
- **`rm "$line"`**: Elimina el archivo correspondiente.

---

### Script completo

```bash
#!/bin/bash

if ! command -v fdupes &> /dev/null
then
    echo "fdupes no está instalado. Debes instalarlo mediante 'apt install fdupes' y volver a ejecutar el script."
    exit 1
fi

archivo=$(fdupes -r . | sed 's/^..//')

echo "$archivo" | while read -r line; do
    rm "$line"
done
```

---

Este script se encarga de:

1. Verificar si `fdupes` está instalado.
2. Buscar archivos duplicados recursivamente en el directorio actual.
3. Eliminar los archivos duplicados encontrados.

