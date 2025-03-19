
---

#Python #FileOrganization #CustomTkinter #GUI #Automation #FileManagement #Coding #Programming #OpenSource #Productivity #OrganizadorDeArchivos #GestiónDeArchivos

---

**Explicación Paso a Paso del Código:**

1. **Importación de Librerías:**
   - `customtkinter`: Para la interfaz gráfica moderna
   - `messagebox`: Para mostrar ventanas emergentes
   - `os`: Manipulación de archivos y directorios
   - `shutil`: Operaciones de movimiento de archivos

2. **Creación de Carpetas:**
   - Verifica y crea las carpetas destino si no existen:
   ```python
   if not os.path.exists(documento_carpeta):
       os.makedirs(documento_carpeta)
   ```

3. **Definición de Extensiones:**
   - Tuplas con extensiones para cada tipo de archivo:
   ```python
   extensiones_documentos = (".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx")
   ```

4. **Listado de Archivos:**
   - Obtiene todos los archivos del directorio actual:
   ```python
   for cada_archivo in os.listdir():
       archivos.append(cada_archivo)
   ```

5. **Función de Movimiento:**
   - Mueve archivos usando `shutil.move`:
   ```python
   def mover_archivo(archivo, destino):
       shutil.move(archivo, destino)
   ```

6. **Funciones de Organización:**
   - Iteran sobre los archivos y los mueven según su extensión:
   ```python
   def organizar_documentos():
       for archivo in archivos:
           if archivo.endswith(extensiones_documentos):
               mover_archivo(archivo, documento_carpeta)
   ```

7. **Interfaz Gráfica (GUI):**
   - Crea ventana principal con botones usando CustomTkinter:
   ```python
   ventana = ctk.CTk()
   boton_documentos = ctk.CTkButton(ventana, text="Organizar Documentos", command=organizar_documentos)
   ```

8. **Manejo de Eventos:**
   - Cada botón ejecuta su función correspondiente y muestra un mensaje de confirmación:
   ```python
   messagebox.showinfo("Informacion", "Documentos ordenados")
   ```

**Consideraciones Importantes:**
- El script debe ejecutarse en el directorio que contiene los archivos a organizar
- Las extensiones son sensibles a mayúsculas/minúsculas
- No mueve el propio script ni las carpetas destino
- Requiere instalación previa de CustomTkinter (`pip install customtkinter`)

**Código Completo:**
```python
import customtkinter as ctk
from tkinter import messagebox
import os
import shutil

# Configuración de carpetas
documento_carpeta = "documentos"
foto_carpeta = "fotos"
video_carpeta = "videos"
musica_carpeta = "musica"

# Crear carpetas si no existen
for carpeta in [documento_carpeta, foto_carpeta, video_carpeta, musica_carpeta]:
    if not os.path.exists(carpeta):
        os.makedirs(carpeta)

# Definición de extensiones
extensiones_documentos = (".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx")
extensiones_fotos = (".jpg", ".jpeg", ".png", ".gif", ".bmp", ".tiff")
extensiones_videos = (".mp4", ".mov", ".avi", ".mkv", ".flv", ".wmv")
extensiones_musica = (".mp3", ".wav", ".aac", ".flac", ".ogg")

# Obtener lista de archivos
archivos = [archivo for archivo in os.listdir() if os.path.isfile(archivo)]

def mover_archivo(archivo, destino):
    shutil.move(archivo, destino)

def organizar_documentos():
    for archivo in archivos:
        if archivo.endswith(extensiones_documentos):
            mover_archivo(archivo, documento_carpeta)
    messagebox.showinfo("Información", "Documentos ordenados")

def organizar_fotos():
    for archivo in archivos:
        if archivo.endswith(extensiones_fotos):
            mover_archivo(archivo, foto_carpeta)
    messagebox.showinfo("Información", "Fotos ordenadas")

def organizar_videos():
    for archivo in archivos:
        if archivo.endswith(extensiones_videos):
            mover_archivo(archivo, video_carpeta)
    messagebox.showinfo("Información", "Videos ordenados")

def organizar_musica():
    for archivo in archivos:
        if archivo.endswith(extensiones_musica):
            mover_archivo(archivo, musica_carpeta)
    messagebox.showinfo("Información", "Música ordenada")

# Configuración de la GUI
ventana = ctk.CTk()
ventana.title("Organizar Archivos")
ventana.geometry("300x200")

# Botones
botones = [
    ("Organizar Documentos", organizar_documentos),
    ("Organizar Fotos", organizar_fotos),
    ("Organizar Videos", organizar_videos),
    ("Organizar Música", organizar_musica)
]

for texto, comando in botones:
    boton = ctk.CTkButton(ventana, text=texto, command=comando)
    boton.pack(pady=5)

ventana.mainloop()
```

---
# Versión mejorada:

#### **1. Importaciones y Configuración Inicial**
```python
import customtkinter as ctk
from tkinter import messagebox
import os
import shutil

documento_carpeta = "documentos"
foto_carpeta = "fotos"
video_carpeta = "videos"
musica_carpeta = "musica"

for carpeta in [documento_carpeta, foto_carpeta, video_carpeta, musica_carpeta]:
    os.makedirs(carpeta, exist_ok=True)
```
- Similar al primer script en importaciones y nombres de carpetas.
- Usa un bucle `for` con `os.makedirs(..., exist_ok=True)` para crear carpetas, lo que es más eficiente y evita errores si las carpetas ya existen.

#### **2. Definición de Extensiones**
```python
extensiones = {
    "documentos": (".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx"),
    "fotos": (".jpg", ".jpeg", ".png", ".gif", ".bmp", ".tiff"),
    "videos": (".mp4", ".mov", ".avi", ".mkv", ".flv", ".wmv"),
    "musica": (".mp3", ".wav", ".aac", ".flac", ".ogg")
}
```
- Usa un diccionario para asociar tipos de archivo con sus extensiones, más organizado que variables separadas.

#### **3. Función para Mover Archivos**
```python
def mover_archivos(tipo, carpeta_destino):
    archivos = [f for f in os.listdir() if f.endswith(extensiones[tipo])]
    for archivo in archivos:
        shutil.move(archivo, carpeta_destino)
    messagebox.showinfo("Información", f"{tipo.capitalize()} organizados correctamente")
```
- Una sola función genérica que:
  - Obtiene la lista de archivos cada vez que se llama, usando una *list comprehension* para filtrar por extensiones.
  - Mueve los archivos coincidentes con `shutil.move()`.
  - Muestra un mensaje con el tipo capitalizado (ej. "Documentos organizados correctamente").
- **Ventaja**: Más flexible y reusable que las funciones separadas del primer script.

#### **4. Interfaz Gráfica**
```python
ctk.set_appearance_mode("dark")  # Modo oscuro
ctk.set_default_color_theme("blue")

ventana = ctk.CTk()
ventana.title("Organizador de Archivos")
ventana.geometry("400x300")

frame = ctk.CTkFrame(ventana)
frame.pack(pady=20, padx=20, fill="both", expand=True)

label = ctk.CTkLabel(frame, text="Organizar Archivos", font=("Arial", 18, "bold"))
label.pack(pady=10)

botones = [
    ("Documentos", "documentos", documento_carpeta),
    ("Fotos", "fotos", foto_carpeta),
    ("Videos", "videos", video_carpeta),
    ("Música", "musica", musica_carpeta)
]

for texto, tipo, carpeta in botones:
    boton = ctk.CTkButton(frame, text=f"Organizar {texto}", command=lambda t=tipo, c=carpeta: mover_archivos(t, c))
    boton.pack(pady=5, padx=20, fill="x")

ventana.mainloop()
```
- Configura un tema oscuro y azul con `set_appearance_mode` y `set_default_color_theme`.
- Crea una ventana de 400x300.
- Usa un `CTkFrame` para organizar los elementos, con un título en `CTkLabel`.
- Define los botones en una lista de tuplas y los crea en un bucle, usando `lambda` para pasar parámetros a `mover_archivos`.
- Los botones se expanden horizontalmente con `fill="x"`.

---

#### **Mejoras Adicionales**
- **Filtrar solo archivos**: Usar `os.path.isfile()` para evitar mover carpetas.
- **Case-insensitive**: Convertir nombres a minúsculas con `f.lower()` para coincidir con extensiones.
- **Mensajes informativos**: Mostrar si no se encuentran archivos.

---
### **Código Completo**
```python
import customtkinter as ctk  # Librería para crear interfaces modernas con Tkinter
from tkinter import messagebox  # Para mostrar mensajes emergentes
import os  # Para operaciones con el sistema de archivos
import shutil  # Para mover archivos entre carpetas

# Definir nombres de carpetas de destino

documento_carpeta = "documentos"
foto_carpeta = "fotos"
video_carpeta = "videos"
musica_carpeta = "musica"

# Crear las carpetas si no existen
for carpeta in [documento_carpeta, foto_carpeta, video_carpeta, musica_carpeta]:
    os.makedirs(carpeta, exist_ok=True)

# Definir las extensiones de archivos para cada tipo de categoría
extensiones = {
    "documentos": (".pdf", ".doc", ".docx", ".txt", ".xls", ".xlsx", ".ppt", ".pptx"),
    "fotos": (".jpg", ".jpeg", ".png", ".gif", ".bmp", ".tiff"),
    "videos": (".mp4", ".mov", ".avi", ".mkv", ".flv", ".wmv"),
    "musica": (".mp3", ".wav", ".aac", ".flac", ".ogg")
}

def mover_archivos(tipo, carpeta_destino):
    """
    Mueve archivos de un tipo específico a la carpeta correspondiente.
    :param tipo: Clave del diccionario de extensiones que indica el tipo de archivo.
    :param carpeta_destino: Nombre de la carpeta de destino donde se moverán los archivos.
    """
    # Filtrar archivos en la carpeta actual que coincidan con las extensiones dadas
    archivos = [f for f in os.listdir() if os.path.isfile(f) and f.lower().endswith(extensiones[tipo])]
    
    # Mover archivos encontrados a la carpeta correspondiente
    for archivo in archivos:
        shutil.move(archivo, carpeta_destino)
    
    # Mostrar mensaje de confirmación o aviso si no hay archivos para mover
    if archivos:
        messagebox.showinfo("Información", f"{tipo.capitalize()} organizados correctamente")
    else:
        messagebox.showinfo("Información", f"No se encontraron {tipo} para organizar")

# Configuración de la interfaz gráfica con CustomTkinter
ctk.set_appearance_mode("dark")  # Modo oscuro
ctk.set_default_color_theme("blue")  # Tema de color azul

# Crear la ventana principal
ventana = ctk.CTk()
ventana.title("Organizador de Archivos")  # Título de la ventana
ventana.geometry("400x300")  # Tamaño de la ventana

# Crear un marco para contener los elementos
frame = ctk.CTkFrame(ventana)
frame.pack(pady=20, padx=20, fill="both", expand=True)

# Etiqueta de título dentro del marco
label = ctk.CTkLabel(frame, text="Organizar Archivos", font=("Arial", 18, "bold"))
label.pack(pady=10)

# Lista de botones con sus respectivos tipos y carpetas de destino
botones = [
    ("Documentos", "documentos", documento_carpeta),
    ("Fotos", "fotos", foto_carpeta),
    ("Videos", "videos", video_carpeta),
    ("Música", "musica", musica_carpeta)
]

# Crear botones dinámicamente para organizar cada tipo de archivo
for texto, tipo, carpeta in botones:
    boton = ctk.CTkButton(frame, text=f"Organizar {texto}", command=lambda t=tipo, c=carpeta: mover_archivos(t, c))
    boton.pack(pady=5, padx=20, fill="x")

# Ejecutar el bucle principal de la interfaz gráfica
ventana.mainloop()

```

---

