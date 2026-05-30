---
tipo: teoria
tags: [button, ejptv2, el-hacker-legendario, eventos, gui, interfaz-grafica, label, pentesting, python, tkinter]
actualizado: 2026-05-28
---

# Widgets de Tipo Button y Label

---
```` python

import tkinter as tk  # Importamos la librería Tkinter

# Creamos la ventana principal
ventana = tk.Tk()
ventana.title("Mi primera app en Python")  # Asignamos el título de la ventana
ventana.geometry("350x300")  # Definimos el tamaño de la ventana

# Función que se ejecutará al presionar el botón
def click():
    label.config(text="Label actualizado")  # Modifica el texto del label

# Creamos un widget Label para mostrar un mensaje inicial
label = tk.Label(ventana, text="Soy un mensaje que se imprime", font=("Arial", 15))
label.pack(pady=100)  # Agregamos espacio vertical alrededor del label

# Creamos un botón que ejecutará la función 'click' al ser presionado
button = tk.Button(ventana, text="Presioname", font=("Arial", 15), command=click)
button.pack(pady=15)  # Agregamos espacio vertical alrededor del botón

# Ejecutamos el bucle principal de la aplicación
ventana.mainloop()

`````

### Paso a paso de lo ocurrido

1. **Importación de la librería Tkinter**: Se importa `tkinter` para crear la interfaz gráfica.
2. **Creación de la ventana principal**: Se usa `tk.Tk()` para generar la ventana.
3. **Configuración de la ventana**: Se asigna un título con `title()` y se establece el tamaño con `geometry()`.
4. **Creación de un Label**: Se añade una etiqueta (`Label`) con un mensaje y un formato de fuente.
5. **Empaquetado del Label**: Se usa `pack()` para posicionar el label en la ventana.
6. **Ejecución del bucle principal**: Se ejecuta `mainloop()` para mantener la ventana en pantalla.

---

### Modificación con botón interactivo

1. **Definición de la función `click()`**: Cambia el texto del `Label` cuando se presiona un botón.
2. **Creación del botón (`Button`)**: Se añade un botón que ejecuta la función `click()` al ser presionado.
3. **Empaquetado del botón**: Se usa `pack()` para posicionar el botón en la ventana.
4. **Ejecución del bucle principal**: Se mantiene la ventana abierta con `mainloop()`.

---

### Conclusión

Este código introduce los conceptos básicos de **Tkinter**, una librería de Python para crear interfaces gráficas. Aprendimos a:

✅ **Crear una ventana** con `tk.Tk()`, definir su tamaño y título.  
✅ **Agregar un Label** para mostrar texto en la interfaz.  
✅ **Implementar interactividad** con un botón (`Button`) que cambia el texto del Label al ser presionado.  
✅ **Utilizar el loop principal (`mainloop()`)** para mantener la ventana activa.

Este es un ejemplo simple, pero sienta las bases para desarrollar aplicaciones más complejas con eventos, widgets adicionales y lógica personalizada. 🎯🚀

---

## Navegación

- ⬆️ Carpeta: [[_5- Interfaces Gráficas|5- Interfaces Gráficas]]
- ⬅️ Anterior: [[1- Introducción a las Interfaces Gráficas con Python]]
- ➡️ Siguiente: [[3- Widgets de Tipo Entry]]
