---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, python, pentesting]
actualizado: 2026-05-28
---

# Ejercicio Práctico con Interfaces Gráficas

---

#Python #Tkinter #Automatización #Organización #GestiónDeArchivos

---
### Explicación Paso a Paso del Código

Este código es una aplicación en **Python** que organiza archivos en carpetas según su tipo, utilizando **Tkinter** para la interfaz gráfica. Aquí está el desglose paso a paso:

---

### 1️⃣ **Importación de Módulos**

```python
import tkinter as tk
from tkinter import messagebox
import os
import shutil
```

- **tkinter**: Se usa para crear la interfaz gráfica.
- **messagebox**: Muestra mensajes emergentes cuando se completan las acciones.
- **os**: Permite interactuar con el sistema operativo (crear carpetas, listar archivos, etc.).
- **shutil**: Se usa para mover archivos de un lugar a otro.

---

### 2️⃣ **Definición de Carpetas Destino**

```python
documento_carpeta = "documentos"
foto_carpeta = "fotos"
video_carpeta = "videos"
musica_carpeta = "musica"
```

Se definen los nombres de las carpetas donde se organizarán los archivos.

---

### 3️⃣ **Creación de Carpetas si No Existen**

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

Aquí se verifica si las carpetas existen y, si no, se crean con `os.makedirs()`.

---

### 4️⃣ **Extensiones de Archivos por Tipo**

```python
extensiones_documentos = (".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx")
extensiones_fotos = (".jpg", ".jpeg", ".png", ".gif", ".bmp", ".tiff")
extensiones_videos = (".mp4", ".mov", ".avi", ".mkv", ".flv", ".wmv")
extensiones_musica = (".mp3", ".wav", ".aac", ".flac", ".ogg")
```

Se definen listas con las extensiones de archivos que se clasificarán en cada categoría.

---

### 5️⃣ **Obtener Lista de Archivos en el Directorio**

```python
archivos = []
for cada_archivo in os.listdir():
    archivos.append(cada_archivo)
```

Se obtiene la lista de todos los archivos en el directorio actual y se almacena en la lista `archivos`.

---

### 6️⃣ **Función para Mover Archivos**

```python
def mover_archivo(archivo, destino):
    shutil.move(archivo, destino)
```

Esta función usa `shutil.move()` para mover archivos a la carpeta de destino correspondiente.

---

### 7️⃣ **Funciones para Organizar Archivos por Tipo**

Cada una de las siguientes funciones revisa los archivos y, si su extensión coincide con las definidas, los mueve a la carpeta correspondiente. Luego muestra un mensaje de confirmación con `messagebox.showinfo()`.

```python
def organizar_documentos():
    for archivo in archivos:
        if archivo.endswith(extensiones_documentos):
            mover_archivo(archivo, documento_carpeta)
    messagebox.showinfo("Informacion", "Documentos ordenados")
```

```python
def organizar_fotos():
    for archivo in archivos:
        if archivo.endswith(extensiones_fotos):
            mover_archivo(archivo, foto_carpeta)
    messagebox.showinfo("Informacion", "Fotos ordenadas")
```

```python
def organizar_videos():
    for archivo in archivos:
        if archivo.endswith(extensiones_videos):
            mover_archivo(archivo, video_carpeta)
    messagebox.showinfo("Informacion", "Videos ordenados")
```

```python
def organizar_musica():
    for archivo in archivos:
        if archivo.endswith(extensiones_musica):
            mover_archivo(archivo, musica_carpeta)
    messagebox.showinfo("Informacion", "Músicas ordenadas")
```

---

### 8️⃣ **Creación de la Interfaz con Tkinter**

```python
ventana = tk.Tk()
ventana.title("Organizar Archivos")
ventana.geometry("300x300")
```

Aquí se inicializa la ventana principal con Tkinter.

---

### 9️⃣ **Botones para Ejecutar la Organización**

Cada botón ejecuta una de las funciones de organización cuando se presiona.

```python
boton_documentos = tk.Button(ventana, text="Organizar Documentos", command=organizar_documentos)
boton_documentos.pack(pady=10)
```

```python
boton_fotos = tk.Button(ventana, text="Organizar Fotos", command=organizar_fotos)
boton_fotos.pack(pady=10)
```

```python
boton_videos = tk.Button(ventana, text="Organizar Videos", command=organizar_videos)
boton_videos.pack(pady=10)
```

```python
boton_musica = tk.Button(ventana, text="Organizar Música", command=organizar_musica)
boton_musica.pack(pady=10)
```

---

### 🔟 **Bucle Principal de la Interfaz**

```python
ventana.mainloop()
```

Esto mantiene la ventana abierta hasta que el usuario la cierre.

---

## 🔥 Código Completo

```python
import tkinter as tk
from tkinter import messagebox
import os
import shutil

documento_carpeta = "documentos"
foto_carpeta = "fotos"
video_carpeta = "videos"
musica_carpeta = "musica"

if not os.path.exists(documento_carpeta):
    os.makedirs(documento_carpeta)
if not os.path.exists(foto_carpeta):
    os.makedirs(foto_carpeta)
if not os.path.exists(video_carpeta):
    os.makedirs(video_carpeta)
if not os.path.exists(musica_carpeta):
    os.makedirs(musica_carpeta)

extensiones_documentos = (".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx")
extensiones_fotos = (".jpg", ".jpeg", ".png", ".gif", ".bmp", ".tiff")
extensiones_videos = (".mp4", ".mov", ".avi", ".mkv", ".flv", ".wmv")
extensiones_musica = (".mp3", ".wav", ".aac", ".flac", ".ogg")

archivos = []
for cada_archivo in os.listdir():
    archivos.append(cada_archivo)

def mover_archivo(archivo, destino):
    shutil.move(archivo, destino)

def organizar_documentos():
    for archivo in archivos:
        if archivo.endswith(extensiones_documentos):
            mover_archivo(archivo, documento_carpeta)
    messagebox.showinfo("Informacion", "Documentos ordenados")

def organizar_fotos():
    for archivo in archivos:
        if archivo.endswith(extensiones_fotos):
            mover_archivo(archivo, foto_carpeta)
    messagebox.showinfo("Informacion", "Fotos ordenadas")

def organizar_videos():
    for archivo in archivos:
        if archivo.endswith(extensiones_videos):
            mover_archivo(archivo, video_carpeta)
    messagebox.showinfo("Informacion", "Videos ordenados")

def organizar_musica():
    for archivo in archivos:
        if archivo.endswith(extensiones_musica):
            mover_archivo(archivo, musica_carpeta)
    messagebox.showinfo("Informacion", "Músicas ordenadas")

ventana = tk.Tk()
ventana.title("Organizar Archivos")
ventana.geometry("300x300")

boton_documentos = tk.Button(ventana, text="Organizar Documentos", command=organizar_documentos)
boton_documentos.pack(pady=10)

boton_fotos = tk.Button(ventana, text="Organizar Fotos", command=organizar_fotos)
boton_fotos.pack(pady=10)

boton_videos = tk.Button(ventana, text="Organizar Videos", command=organizar_videos)
boton_videos.pack(pady=10)

boton_musica = tk.Button(ventana, text="Organizar Música", command=organizar_musica)
boton_musica.pack(pady=10)

ventana.mainloop()
```

---




[[4- Ejercicio Práctico Bucle FOR – Script para Ordenar Archivos Automáticamente]]
[[4- Ejercicio Práctico con OS y SHUTIL]]

---

## Navegación

- ⬆️ Carpeta: [[_5- Interfaces Gráficas|5- Interfaces Gráficas]]
- ⬅️ Anterior: [[5- Creación de Menús Desplegables]]
- ➡️ Siguiente: [[7- Personalización y Estética de nuestras Aplicaciones Gráficas]]
