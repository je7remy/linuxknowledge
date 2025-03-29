
---

#ComandoFind #Xargs #UnixLinux #ComandosLinux #RenombrarArchivos #MoverArchivos #GestiónDeArchivos #Bash #Terminal #AutomatizaciónLinux #ScriptingLinux #AdministraciónDeSistemas #ShellScripting #GestiónDeDirectorios

---

**`xargs`** es un comando que toma la salida de otro comando y la utiliza como entrada para otro comando, permitiendo realizar operaciones sobre cada elemento de esa salida. Es útil cuando el número de elementos encontrados es muy grande, ya que evita los problemas con límites de longitud de comando.

### 1. **`find . -name "*.txt" | xargs rm`**

**Acción:** Encuentra y elimina todos los archivos con extensión `.txt` en el directorio actual y sus subdirectorios.

**Pasos:**

1. `find . -name "*.txt"`: Busca todos los archivos con la extensión `.txt` en el directorio actual (`.`) y sus subdirectorios.
2. El resultado de `find` (la lista de archivos encontrados) se pasa al comando `xargs`.
3. `xargs rm`: Usa la lista de archivos como argumentos para el comando `rm`, eliminándolos.

---

### 2. **`find . -name "*.txt" | xargs -I {} mv {} carpeta`**

**Acción:** Mueve todos los archivos `.txt` encontrados al directorio `carpeta`.

**Pasos:**

1. `find . -name "*.txt"`: Encuentra todos los archivos `.txt` en el directorio actual y sus subdirectorios.
2. El resultado se pasa al comando `xargs` con la opción `-I {}`, que permite sustituir `{}` con cada archivo encontrado.
3. `mv {} carpeta`: Por cada archivo encontrado, el comando `mv` lo mueve al directorio `carpeta`.

---

### 3. **`ls *.txt | xargs -I {} mv {} {}.bak`**

**Acción:** Renombra todos los archivos `.txt` en el directorio actual añadiéndoles la extensión `.bak`.

**Pasos:**

1. `ls *.txt`: Lista todos los archivos con la extensión `.txt` en el directorio actual.
2. El resultado se pasa a `xargs` con la opción `-I {}`.
3. `mv {} {}.bak`: Para cada archivo listado, el comando `mv` lo renombra agregando `.bak` al final del nombre original.

---

### 4. **`ls *.bak | xargs -I {} mv {} {}.txt`**

**Acción:** Cambia la extensión de todos los archivos `.bak` a `.txt`.

**Pasos:**

1. `ls *.bak`: Lista todos los archivos con la extensión `.bak` en el directorio actual.
2. El resultado se pasa a `xargs` con la opción `-I {}`.
3. `mv {} {}.txt`: Para cada archivo listado, el comando `mv` lo renombra cambiando su extensión de `.bak` a `.txt`.

---

### 5. **`ls *.txt | xargs -I {} mv {} backup_{}`**

**Acción:** Renombra todos los archivos `.txt` en el directorio actual, agregando el prefijo `backup_` a sus nombres.

**Pasos:**

1. `ls *.txt`: Lista todos los archivos con la extensión `.txt` en el directorio actual.
2. El resultado se pasa a `xargs` con la opción `-I {}`.
3. `mv {} backup_{}`: Para cada archivo listado, el comando `mv` lo renombra agregando `backup_` al inicio del nombre original.

---


[[5- Comando find y redirección de errores]]
[[3- Ordenar la Información – SORT, HEAD, TAIL, WC y UNIQ]]