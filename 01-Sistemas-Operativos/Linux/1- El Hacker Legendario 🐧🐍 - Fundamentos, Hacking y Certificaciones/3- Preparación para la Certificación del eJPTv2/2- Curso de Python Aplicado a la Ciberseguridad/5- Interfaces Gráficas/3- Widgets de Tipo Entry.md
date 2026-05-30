---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, python, pentesting]
actualizado: 2026-05-28
---

# Widgets de Tipo Entry

---

#Python #Tkinter #InterfazGrafica #GUI #Entry #Label #Button

---

### Paso a paso del código en Tkinter

1. **Importación de Tkinter**  
    Se importa la librería `tkinter`, la cual permite crear interfaces gráficas en Python.
    
2. **Creación de la ventana principal**  
    Se instancia un objeto `Tk` de `tkinter`, que representa la ventana principal de la aplicación.
    
    ```python
    ventana = tk.Tk()
    ```
    
3. **Configuración de la ventana**  
    Se establecen el título y el tamaño de la ventana usando `title()` y `geometry()`.
    
    ```python
    ventana.title("Mi primera app en Python")
    ventana.geometry("350x150")
    ```
    
4. **Definición de la función `click`**  
    Se define la función `click()`, que se ejecutará cuando se presione el botón.
    
    - La función obtiene el texto ingresado en el `Entry` mediante `.get()`.
    - Luego, actualiza el `Label` con el texto ingresado.
    
    ```python
    def click():
        texto_introducido = entry.get()
        label.config(text=f"El texto introducido es: {texto_introducido}")
    ```
    
5. **Creación de widgets (Label, Entry, Button)**
    
    - Se crea un `Label` inicial con el texto "Introduce algo".
    - Se crea un `Entry` para que el usuario ingrese texto.
    - Se crea un `Button` que llama a la función `click` cuando es presionado.
    
    ```python
    label = tk.Label(ventana, text="Introduce algo", font=("Arial", 10))
    label.pack(pady=10)
    
    entry = tk.Entry(ventana, width=30)
    entry.pack(pady=10)
    
    button = tk.Button(ventana, text="Presioname", font=("Arial", 10), command=click)
    button.pack(pady=15)
    ```
    
6. **Ejecución de la ventana**  
    Se ejecuta el loop principal de la interfaz con `mainloop()`, permitiendo que la ventana permanezca activa.
    

---

### Código completo

```python
import tkinter as tk

ventana = tk.Tk()

ventana.title("Mi primera app en Python")
ventana.geometry("350x150")

def click():
    texto_introducido = entry.get()
    label.config(text=f"El texto introducido es: {texto_introducido}")

label = tk.Label(ventana, text="Introduce algo", font=("Arial", 10))
label.pack(pady=10)

entry = tk.Entry(ventana, width=30)
entry.pack(pady=10)

button = tk.Button(ventana, text="Presioname", font=("Arial", 10), command=click)
button.pack(pady=15)

ventana.mainloop()
```

---

---

## Navegación

- ⬆️ Carpeta: [[_5- Interfaces Gráficas|5- Interfaces Gráficas]]
- ⬅️ Anterior: [[2- Widgets de Tipo Button y Label]]
- ➡️ Siguiente: [[4- Creación de Pop-Ups y sus Distintos Tipos]]
