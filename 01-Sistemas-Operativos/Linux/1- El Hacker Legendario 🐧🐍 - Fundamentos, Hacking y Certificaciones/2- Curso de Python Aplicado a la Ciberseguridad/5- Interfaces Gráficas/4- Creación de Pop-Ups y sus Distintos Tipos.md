
---

#Python #Tkinter #GUI #Popups #MessageBox #SimpleDialog #InterfacesGrafícas

---
## **Paso 1: Importar las bibliotecas necesarias**

```python
import tkinter as tk
from tkinter import messagebox, simpledialog
```

- `tkinter` es el módulo estándar de Python para la creación de interfaces gráficas.
- `messagebox` permite mostrar mensajes emergentes.
- `simpledialog` proporciona diálogos de entrada para pedir datos al usuario.

---

## **Paso 2: Crear la función para mostrar un mensaje emergente**

```python
def popup_info():
    messagebox.showinfo("Mensaje de información", "Contenido del popup")
```

- Se define la función `popup_info`, que al ejecutarse muestra un cuadro de diálogo con un mensaje de información.

---

## **Paso 3: Crear la función para solicitar un dato al usuario**

```python
def popup_input():
    name = simpledialog.askstring("Input", "¿Cuál es tu nombre?")
    if name:
        label.config(text=f"Tu nombre es: {name}")
```

- Se usa `askstring` de `simpledialog` para pedir un nombre al usuario.
- Si el usuario introduce un nombre, se actualiza el texto de una etiqueta (`label`).

---

## **Paso 4: Configurar la ventana principal**

```python
ventana = tk.Tk()
ventana.title("Ventana de Pop-ups")
ventana.geometry("300x200")
```

- Se crea una ventana principal (`ventana`).
- Se establece un título con `.title()`.
- Se define el tamaño de la ventana con `.geometry()`.

---

## **Paso 5: Agregar widgets (botones y etiquetas)**

```python
label = tk.Label(ventana, text="Aquí aparecerá tu nombre", font=("Arial", 12))
label.pack(pady=10)

boton_info = tk.Button(ventana, text="Mostrar Info", command=popup_info)
boton_info.pack(pady=5)

boton_input = tk.Button(ventana, text="Ingresar Nombre", command=popup_input)
boton_input.pack(pady=5)
```

- Se crea una `Label` que mostrará el nombre introducido.
- Se agregan dos `Button`:
    - Uno que muestra un mensaje de información.
    - Otro que pide un nombre y actualiza la `Label`.

---

## **Paso 6: Ejecutar el bucle principal de la aplicación**

```python
ventana.mainloop()
```

- `mainloop()` mantiene la ventana en ejecución, esperando eventos del usuario.

---

## **Código Final

```python
import tkinter as tk
from tkinter import messagebox, simpledialog

def popup_info():
    messagebox.showinfo("Mensaje de información", "Contenido del popup")

def popup_input():
    name = simpledialog.askstring("Input", "¿Cuál es tu nombre?")
    if name:
        label.config(text=f"Tu nombre es: {name}")

ventana = tk.Tk()
ventana.title("Ventana de Pop-ups")
ventana.geometry("300x200")

label = tk.Label(ventana, text="Aquí aparecerá tu nombre", font=("Arial", 12))
label.pack(pady=10)

boton_info = tk.Button(ventana, text="Mostrar Info", command=popup_info)
boton_info.pack(pady=5)

boton_input = tk.Button(ventana, text="Ingresar Nombre", command=popup_input)
boton_input.pack(pady=5)

ventana.mainloop()
```

---
