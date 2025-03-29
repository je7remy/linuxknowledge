
---

#Python #Tkinter #GUI #Menús #InterfazGráfica #DesarrolloDeSoftware #Programación

---
### **Paso 1: Importación de Módulos**

Se importan los módulos necesarios para la creación de la interfaz gráfica:

```python
import tkinter as tk
from tkinter import messagebox
```

- `tkinter` es el módulo principal para crear interfaces gráficas en Python.
- `messagebox` es un submódulo de `tkinter` que permite mostrar cuadros de diálogo con mensajes informativos.

---

### **Paso 2: Definición de Funciones**

Se definen funciones que serán llamadas cuando el usuario seleccione una opción del menú.

```python
def nuevo_archivo():
    messagebox.showinfo("Ventana de crear archivo", "Esta es la ventana para crear un archivo")
```

- Muestra un mensaje indicando que se ha activado la opción de **"Nuevo Archivo"**.

```python
def guardar_archivo():
    messagebox.showinfo("Ventana de guardar archivo", "Esta es la ventana para guardar un archivo")
```

- Informa que se activó la opción de **"Guardar Archivo"**.

```python
def salir():
    ventana.quit()
```

- Cierra la aplicación cuando el usuario selecciona la opción **"Salir"**.

```python
def mostrar_ayuda():
    messagebox.showinfo("Ayuda", "Prueba los menús desplegables")
```

- Muestra un cuadro de ayuda con instrucciones básicas.

```python
def acerca_de():
    messagebox.showinfo("Acerca de", "Aplicación creada en el curso de Python")
```

- Muestra información sobre la aplicación.

---

### **Paso 3: Creación de la Ventana Principal**

```python
ventana = tk.Tk()
ventana.title("Menú Principal")
ventana.geometry("300x200")
```

- Se inicializa la ventana principal con `tk.Tk()`.
- Se establece el título de la ventana con `title("Menú Principal")`.
- Se configura el tamaño de la ventana con `geometry("300x200")`.

---

### **Paso 4: Creación de la Barra de Menú**

```python
barra_menus = tk.Menu(ventana)
```

- Se crea una barra de menús utilizando `tk.Menu()`, la cual se asigna a la ventana.

---

### **Paso 5: Creación del Menú "Archivo"**

```python
menu_archivo = tk.Menu(barra_menus, tearoff=0)
menu_archivo.add_command(label="Nuevo", command=nuevo_archivo)
menu_archivo.add_command(label="Guardar", command=guardar_archivo)
menu_archivo.add_separator()
menu_archivo.add_command(label="Salir", command=salir)

barra_menus.add_cascade(label="Archivo", menu=menu_archivo)
```

- Se crea el menú **Archivo** con `tk.Menu(barra_menus, tearoff=0)`.
- Se agregan las opciones:
    - **Nuevo** (`add_command(label="Nuevo", command=nuevo_archivo)`)
    - **Guardar** (`add_command(label="Guardar", command=guardar_archivo)`)
    - Un separador (`add_separator()`)
    - **Salir** (`add_command(label="Salir", command=salir)`)
- Se añade este menú a la barra de menús con `add_cascade(label="Archivo", menu=menu_archivo)`.

---

### **Paso 6: Creación del Menú "Ayuda"**

```python
menu_ayuda = tk.Menu(barra_menus, tearoff=0)
menu_ayuda.add_command(label="Ayuda", command=mostrar_ayuda)
menu_ayuda.add_command(label="Acerca de", command=acerca_de)

barra_menus.add_cascade(label="Ayuda", menu=menu_ayuda)
```

- Se crea el menú **Ayuda** con `tk.Menu(barra_menus, tearoff=0)`.
- Se agregan las opciones:
    - **Ayuda** (`add_command(label="Ayuda", command=mostrar_ayuda)`)
    - **Acerca de** (`add_command(label="Acerca de", command=acerca_de)`)
- Se añade este menú a la barra con `add_cascade(label="Ayuda", menu=menu_ayuda)`.

---

### **Paso 7: Configuración y Ejecución de la Ventana**

```python
ventana.config(menu=barra_menus)
ventana.mainloop()
```

- Se configura la barra de menús en la ventana principal con `config(menu=barra_menus)`.
- Se ejecuta la aplicación con `mainloop()`, permitiendo que la interfaz gráfica se mantenga activa hasta que el usuario la cierre.

---

## **Código Completo**

```python
import tkinter as tk
from tkinter import messagebox

def nuevo_archivo():
    messagebox.showinfo("Ventana de crear archivo", "Esta es la ventana para crear un archivo")

def guardar_archivo():
    messagebox.showinfo("Ventana de guardar archivo", "Esta es la ventana para guardar un archivo")

def salir():
    ventana.quit()

def mostrar_ayuda():
    messagebox.showinfo("Ayuda", "Prueba los menús desplegables")

def acerca_de():
    messagebox.showinfo("Acerca de", "Aplicación creada en el curso de Python")

ventana = tk.Tk()
ventana.title("Menú Principal")
ventana.geometry("300x200")

barra_menus = tk.Menu(ventana)

# Menú Archivo
menu_archivo = tk.Menu(barra_menus, tearoff=0)
menu_archivo.add_command(label="Nuevo", command=nuevo_archivo)
menu_archivo.add_command(label="Guardar", command=guardar_archivo)
menu_archivo.add_separator()
menu_archivo.add_command(label="Salir", command=salir)

barra_menus.add_cascade(label="Archivo", menu=menu_archivo)

# Menú Ayuda
menu_ayuda = tk.Menu(barra_menus, tearoff=0)
menu_ayuda.add_command(label="Ayuda", command=mostrar_ayuda)
menu_ayuda.add_command(label="Acerca de", command=acerca_de)

barra_menus.add_cascade(label="Ayuda", menu=menu_ayuda)

ventana.config(menu=barra_menus)
ventana.mainloop()
```

---
