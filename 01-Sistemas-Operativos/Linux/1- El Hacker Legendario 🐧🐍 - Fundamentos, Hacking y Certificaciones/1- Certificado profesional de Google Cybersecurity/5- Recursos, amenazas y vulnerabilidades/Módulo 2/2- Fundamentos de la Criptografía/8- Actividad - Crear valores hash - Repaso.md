

## 📌 Resumen de actividades

Como analista de seguridad, tendrás que implementar **controles de seguridad** para proteger a las organizaciones contra diversas amenazas.

Aquí es donde entra en juego el **hashing**.

- Una **función hash** es un algoritmo que produce un código que no puede ser descifrado.
    
- Se utiliza para identificar de forma única el contenido de un archivo y comprobar si ha sido modificado.
    
- Este código se conoce como **valor hash** o **resumen**.
    

👉 Por ejemplo:  
Un programa malicioso puede imitar un programa original. Si una sola línea de código cambia, se genera un **hash diferente**, lo que permite a los equipos de seguridad identificarlo y **mitigar el riesgo**.

Aunque existen muchas herramientas para comparar hashes, es importante que un analista de seguridad sepa cómo hacerlo **manualmente**.

En esta actividad de laboratorio:

- Crearás valores hash para dos archivos.
    
- Usarás comandos de Linux para compararlos y analizar diferencias.
    

---

## 🖥️ Escenario

En este laboratorio, deberás investigar si dos archivos (`file1.txt` y `file2.txt`) son **idénticos** o **diferentes**.

### Proceso general:

1. Mostrar el contenido de los dos archivos.
    
2. Generar un valor hash para cada archivo.
    
3. Guardar los hashes en archivos separados.
    
4. Comparar los valores de hash para identificar diferencias.
    

---

## 📝 Tarea 1: Generar hashes para archivos

El laboratorio comienza en el directorio personal:

```
/home/analyst
```

Este directorio contiene los archivos:

```
file1.txt  
file2.txt
```

---

### 🔹 Paso 1: Mostrar archivos del directorio

```bash
ls
```

**Salida esperada:**

```
file1.txt  file2.txt
```

---

### 🔹 Paso 2: Mostrar el contenido de los archivos

```bash
cat file1.txt
```

**Salida:**

```
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
```

```bash
cat file2.txt
```

**Salida:**

```
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
9sxa5Yq20R
```

---

### ❓ Pregunta 1

¿Es idéntico el contenido de los dos archivos cuando se usa el comando `cat`?

✅ **Respuesta:** Sí, parecen idénticos visualmente, aunque `file2.txt` contiene una línea adicional al final.

---

### 🔹 Paso 3: Generar valores hash

```bash
sha256sum file1.txt
```

**Salida:**

```
131f95c51cc819465fa1797f6ccacf9d494aaaff46fa3eac73ae63ffbdfd8267  file1.txt
```

```bash
sha256sum file2.txt
```

**Salida:**

```
2558ba9a4cad1e69804ce03aa2a029526179a91a5e38cb723320e83af9ca017b  file2.txt
```

---

### ❓ Pregunta 2

¿Producen ambos archivos el mismo valor hash?

❌ **Respuesta:** No.

- `file1.txt` → `131f95c5...`
    
- `file2.txt` → `2558ba9a...`
    

Esto indica que **los contenidos no son idénticos**, a pesar de que a simple vista lo parecían.

---

## 📝 Tarea 2: Comparar hashes

### 🔹 Paso 1: Guardar los hashes en archivos nuevos

```bash
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash
```

---

### 🔹 Paso 2: Mostrar los valores guardados

```bash
cat file1hash
```

```
131f95c51cc819465fa1797f6ccacf9d494aaaff46fa3eac73ae63ffbdfd8267  file1.txt
```

```bash
cat file2hash
```

```
2558ba9a4cad1e69804ce03aa2a029526179a91a5e38cb723320e83af9ca017b  file2.txt
```

👉 Aunque los archivos parecían iguales con `cat`, los **hashes son completamente distintos**.

---

### 🔹 Paso 3: Comparar byte por byte

```bash
cmp file1hash file2hash
```

**Salida:**

```
file1hash file2hash differ: char 1, line 1
```

👉 Esto confirma que los archivos **son diferentes**.

---

### ❓ Pregunta 3

Basándose en los valores hash, ¿es `file1.txt` diferente de `file2.txt`?

✅ **Respuesta:** Sí. El contenido de los archivos es diferente porque los **valores hash no coinciden**.

---

## 🎯 Conclusión

En este laboratorio practicaste cómo:

- Calcular hashes con `sha256sum`.
    
- Mostrar valores de hash con `cat`.
    
- Comparar hashes con `cmp`.
    

📌 Estas son herramientas **clave para validar la integridad de los datos** y detectar modificaciones, contribuyendo al control de seguridad en una organización.

---

