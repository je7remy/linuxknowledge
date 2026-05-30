---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, pentesting, python]
actualizado: 2026-05-28
---

# Uso Básico de SHUTIL

---

#Python 🐍 #shutil 🔄 #GestiónDeArchivos 📂 #CopiarMoverEliminar 🚀 #Automatización 🤖 #Programación 💻 #PythonScripts 📝

---

### **Definición de `shutil`**

`shutil` es un módulo de la biblioteca estándar de Python que proporciona funciones para manejar archivos y directorios, como copiar, mover, renombrar y eliminar. Se usa para manipular archivos y estructuras de carpetas de manera sencilla y eficiente.

### **1. Copiar un archivo con `shutil.copy`**

```python
import shutil
shutil.copy("reporte_grafico.png", "Copia_reporte_grafico.png")
```

**Explicación:**

- La función `shutil.copy(src, dst)` copia el archivo `reporte_grafico.png` y lo guarda con el nombre `Copia_reporte_grafico.png` en el mismo directorio.
- Se copian solo los contenidos del archivo, sin conservar metadatos como la fecha de modificación.

---

### **2. Copiar un archivo con `shutil.copy2`**

```python
import shutil
shutil.copy2("reporte_grafico.png", "Copia_reporte_grafico.png")
```

**Explicación:**

- La función `shutil.copy2(src, dst)` copia el archivo igual que `shutil.copy`, pero también conserva metadatos como la fecha de creación y modificación del archivo original.

✅ **Diferencia principal entre `copy` y `copy2`**:  
`copy2` mantiene metadatos del archivo original, mientras que `copy` solo copia los datos.

---

### **3. Copiar una carpeta con `shutil.copytree`**

```python
import shutil
shutil.copytree("Nueva carpeta", "Copia_Nueva carpeta")
```

**Explicación:**

- La función `shutil.copytree(src, dst)` copia una carpeta completa (con todos sus archivos y subcarpetas) de `Nueva carpeta` a `Copia_Nueva carpeta`.
- Si `Copia_Nueva carpeta` ya existe, se genera un error.
- Se copian todos los archivos dentro de la carpeta, manteniendo su estructura.

---

### **4. Mover una carpeta con `shutil.move`**

```python
import shutil
shutil.move("Nueva carpeta", "Copia_Nueva carpeta")
```

**Explicación:**

- `shutil.move(src, dst)` mueve `Nueva carpeta` a `Copia_Nueva carpeta`.
- Si `Copia_Nueva carpeta` ya existe, la carpeta `Nueva carpeta` se moverá dentro de `Copia_Nueva carpeta`.
- A diferencia de `copytree`, aquí no se hace una copia, sino que se traslada la carpeta de ubicación.

---

### **5. Copiar todos los archivos `.py` a una carpeta**

```python
import shutil
import os
archivos = os.listdir()
for archivo in archivos:
    if archivo.endswith(".py"):
        shutil.copy(archivo, "archivos python")
        print("Se hizo la copia del archivo:", archivo)
```

**Explicación:**

1. `os.listdir()` obtiene la lista de archivos y carpetas en el directorio actual.
2. Se recorre cada archivo en el directorio.
3. Se verifica si el archivo termina en `.py` (es un script de Python).
4. Si es un archivo `.py`, se copia a la carpeta `"archivos python"`.
5. Se imprime un mensaje confirmando la copia.

🔴 **Posibles problemas:**

- `"archivos python"` debe existir antes de ejecutar el código, de lo contrario, generará un error.
- Si hay muchos archivos `.py`, el proceso puede tardar.

---

### **Resumen**

|Código|Acción|Metadatos|Notas|
|---|---|---|---|
|`shutil.copy`|Copia un archivo|❌ No|Solo datos|
|`shutil.copy2`|Copia un archivo|✅ Sí|Mantiene fecha de creación/modificación|
|`shutil.copytree`|Copia una carpeta completa|✅ Sí|Copia archivos y estructura|
|`shutil.move`|Mueve una carpeta|✅ Sí|Cambia ubicación en lugar de copiar|
|`os.listdir() + shutil.copy`|Copia archivos `.py` a una carpeta|✅ Sí|La carpeta destino debe existir|

---

## Navegación

- ⬆️ Carpeta: [[_3- Manipulación de Ficheros e Interacción con el Sistema Operativo|3- Manipulación de Ficheros e Interacción con el Sistema Operativo]]
- ⬅️ Anterior: [[2- Uso Básico del Módulo OS]]
- ➡️ Siguiente: [[4- Ejercicio Práctico con OS y SHUTIL]]
