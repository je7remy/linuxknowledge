
---

#Python 🐍 #shutil 🔄 #GestiónDeArchivos 📂 #CopiarMoverEliminar 🚀 #Automatización 🤖 #Programación 💻 #PythonScripts 📝 #OSModule

---

El código de Python organiza archivos en el directorio actual clasificándolos por tipo y moviéndolos a cuatro carpetas predefinidas: "documentos", "fotos", "videos" y "música". Primero, importa los módulos `os` y `shutil` para gestionar archivos. Luego, crea las carpetas si no existen, define extensiones para cada categoría (e.g., `.pdf` para documentos, `.jpg` para fotos) y lista todos los elementos del directorio. A través de una función, mueve cada archivo a la carpeta correspondiente según su extensión, ignorando aquellos que no coinciden. Finalmente, imprime un mensaje indicando que la operación ha terminado. Es un script simple de automatización para ordenar archivos.

---

### **1. Importación de módulos**

```python
import os
import shutil
```

- **Qué hace:** El código comienza importando dos módulos de la biblioteca estándar de Python:
  - **`os`:** Permite interactuar con el sistema operativo, como listar archivos, verificar si existen directorios o crearlos.
  - **`shutil`:** Proporciona funciones de alto nivel para operaciones con archivos, como moverlos o copiarlos.
- **Propósito:** Estos módulos son esenciales para las tareas de gestión de archivos que el script realizará.

---

### **2. Definición de nombres de carpetas**

```python
documento_carpeta = "documentos"
foto_carpeta = "fotos"
video_carpeta = "videos"
musica_carpeta = "musica"
```

- **Qué hace:** Se definen cuatro variables que representan los nombres de las carpetas donde se organizarán los archivos según su tipo:
  - Documentos (e.g., PDFs, Word).
  - Fotos (e.g., imágenes JPG, PNG).
  - Videos (e.g., MP4, AVI).
  - Música (e.g., MP3, WAV).
- **Propósito:** Estas variables se usarán más adelante como destinos para mover los archivos.

---

### **3. Creación de carpetas si no existen**

```python
if not os.path.exists(documento_carpeta):
    os.makedirs(documento_carpeta)
if not os.path.exists(foto_carpeta):
    os.makedirs(foto_carpeta)
if not os.path.exists(video_carpeta):
    os.makedirs(video_carpeta)
if not os.path.exists(musica_carpeta):
    os.makedirs(musica_carpeta)
```

- **Qué hace:** Para cada una de las carpetas definidas:
  - **`os.path.exists()`:** Verifica si la carpeta ya existe en el directorio actual.
  - **`os.makedirs()`:** Si no existe, la crea.
- **Propósito:** Asegura que las carpetas estén disponibles antes de mover archivos a ellas, evitando errores por destinos inexistentes.

---

### **4. Definición de extensiones de archivos**

```python
extensiones_documentos = (".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx")
extensiones_fotos = (".jpg", "jpeg", ".png", ".gif", ".bmp", ".tiff")
extensiones_videos = (".mp4", ".mov", ".avi", ".mkv", ".flv", ".wmv")
extensiones_musica = (".mp3", ".wav", ".aac", ".flac", ".ogg")
```

- **Qué hace:** Se crean cuatro tuplas que contienen las extensiones de archivo asociadas a cada tipo:
  - Documentos: Archivos de texto y oficina.
  - Fotos: Formatos de imagen comunes.
  - Videos: Formatos de video populares.
  - Música: Formatos de audio.
- **Propósito:** Estas tuplas servirán para clasificar los archivos según su extensión y decidir a qué carpeta moverlos.

---

### **5. Listado de archivos en el directorio actual**

```python
archivos = []
for cada_archivo in os.listdir():
    archivos.append(cada_archivo)
```

- **Qué hace:**
  - **`os.listdir()`:** Devuelve una lista de todos los elementos (archivos y directorios) en el directorio actual donde se ejecuta el script.
  - Se inicializa una lista vacía `archivos` y, mediante un bucle `for`, cada elemento encontrado se agrega a esta lista.
- **Propósito:** Prepara una lista de archivos para procesar en los pasos siguientes.
- **Nota:** Este método no distingue entre archivos y directorios, y no explora subdirectorios (es decir, no es recursivo).

---

### **6. Definición de la función para mover archivos**

```python
def mover_archivo(archivo, destino):
    shutil.move(archivo, destino)
```

- **Qué hace:** Define una función llamada `mover_archivo` que:
  - Toma dos parámetros: `archivo` (el nombre del archivo a mover) y `destino` (la carpeta de destino).
  - Usa **`shutil.move()`** para mover el archivo desde su ubicación actual al directorio especificado.
- **Propósito:** Encapsula la lógica de mover archivos, haciéndola reusable y clara.

---

### **7. Clasificación y movimiento de archivos**

```python
for archivo in archivos:
    if archivo.endswith(extensiones_documentos):
        mover_archivo(archivo, documento_carpeta)
    elif archivo.endswith(extensiones_fotos):
        mover_archivo(archivo, foto_carpeta)
    elif archivo.endswith(extensiones_videos):
        mover_archivo(archivo, video_carpeta)
    elif archivo.endswith(extensiones_musica):
        mover_archivo(archivo, musica_carpeta)
```

- **Qué hace:** Itera sobre cada elemento en la lista `archivos` y:
  - Usa **`endswith()`** para verificar si el nombre del archivo termina con alguna de las extensiones definidas en las tuplas.
  - Si coincide con una extensión (e.g., `.pdf` para documentos), llama a `mover_archivo` para trasladarlo a la carpeta correspondiente.
  - Si no coincide con ninguna extensión, el archivo se ignora.
- **Propósito:** Organiza los archivos moviéndolos a las carpetas según su tipo.
- **Nota:** El código asume que los elementos en `archivos` son archivos y no directorios. Si un elemento es un directorio, `endswith()` no causará un error, pero el archivo no se moverá (ya que no tendrá una extensión típica).

---

### **8. Mensaje de finalización**

```python
print("se ha terminado la openracion")
```

- **Qué hace:** Imprime un mensaje indicando que el proceso ha terminado. (Nota: "openracion" parece un error tipográfico; debería ser "operación").
- **Propósito:** Informa al usuario que el script ha completado su tarea.
- **Nota:** Este mensaje se imprime siempre, incluso si no se movió ningún archivo.

---

### **Resumen del flujo completo**

1. **Importa módulos:** Prepara las herramientas necesarias (`os` y `shutil`).
2. **Define carpetas:** Establece los nombres de las carpetas de destino.
3. **Crea carpetas:** Asegura que existan las carpetas para evitar errores.
4. **Define extensiones:** Asocia extensiones a cada tipo de archivo.
5. **Lista archivos:** Recopila todos los elementos del directorio actual.
6. **Define función:** Crea una función para mover archivos.
7. **Clasifica y mueve:** Itera sobre los archivos y los organiza en las carpetas correspondientes.
8. **Muestra mensaje:** Notifica que la operación ha terminado.

---

### **Observaciones finales**

- **Limitaciones:**
  - Solo procesa archivos en el directorio actual (no subdirectorios).
  - Ignora archivos sin extensiones definidas.
  - No maneja casos como extensiones en mayúsculas (e.g., `.JPG`) o conflictos de nombres en el destino.
- **Resultado:** El script organiza eficientemente archivos en el directorio actual en cuatro carpetas según su tipo, asumiendo que las extensiones coinciden y que no hay errores como permisos denegados o nombres duplicados.



[[4- Ejercicio Práctico Bucle FOR – Script para Ordenar Archivos Automáticamente]]
[[6- Ejercicio Práctico con Interfaces Gráficas]]