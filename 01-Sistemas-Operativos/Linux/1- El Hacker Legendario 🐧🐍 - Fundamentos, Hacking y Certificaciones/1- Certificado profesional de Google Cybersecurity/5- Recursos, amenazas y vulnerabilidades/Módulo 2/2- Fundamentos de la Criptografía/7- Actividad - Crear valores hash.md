---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Actividad - Crear valores hash
# 🧩 Actividad: Generar y comparar valores de hash

## 📂 Situación inicial

En este laboratorio se trabaja con dos archivos:

```
file1.txt  
file2.txt
```

El objetivo es determinar si **son idénticos** o **difieren**, aunque a simple vista parezcan iguales.

---

## 📝 Tarea 1: Generar hashes para archivos

### 🔹 Paso 1: Mostrar los archivos del directorio

```bash
ls
```

**Salida esperada:**

```
file1.txt  file2.txt
```

---

### 🔹 Paso 2: Mostrar el contenido de cada archivo

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

👉 **A simple vista parecen idénticos**, pero `file2.txt` tiene una línea extra.

**Pregunta:** ¿El contenido de los dos archivos parece idéntico cuando usas `cat`?

- ✅ **Sí** — visualmente se parecen, aunque en realidad hay una diferencia.
    

---

### 🔹 Paso 3: Generar los valores hash

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

**Pregunta:** ¿Ambos archivos producen el mismo valor hash?

- ❌ **No**.
    
    - `file1.txt` → `131f95c5...`
        
    - `file2.txt` → `2558ba9a...`
        

👉 Aunque parecen iguales, el **hash revela que son diferentes**.

---

## 📝 Tarea 2: Comparar hashes

### 🔹 Paso 1: Guardar cada hash en un archivo

```bash
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash
```

---

### 🔹 Paso 2: Mostrar el contenido de los archivos de hash

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

👉 Los hashes son completamente distintos.

---

### 🔹 Paso 3: Comparar los hashes byte por byte

```bash
cmp file1hash file2hash
```

**Salida:**

```
file1hash file2hash differ: char 1, line 1
```

👉 Esto confirma que los archivos **no son idénticos**.

---

## 🎯 Conclusión del laboratorio

- ✔️ **`cat` no siempre es suficiente** → los archivos parecían idénticos visualmente.
    
- ✔️ **Los valores hash (`sha256sum`) mostraron diferencias claras**.
    
- ✔️ **Comparar hashes (`cmp`) confirmó la discrepancia**.
    

**Respuesta final:** Sí, el contenido de los dos archivos es diferente porque los valores de hash no coinciden.

---

## ✅ Aprendizajes clave

- Uso de `sha256sum` para generar valores hash.
    
- Validación de integridad de archivos mediante comparación de hashes.
    
- Confirmación byte por byte con `cmp`.
    

👉 Herramientas esenciales para un analista de seguridad en la detección de alteraciones en archivos.

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ⬅️ Anterior: [[6- La evolución de las funciones hash]]
- ➡️ Siguiente: [[8- Actividad - Crear valores hash - Repaso]]
