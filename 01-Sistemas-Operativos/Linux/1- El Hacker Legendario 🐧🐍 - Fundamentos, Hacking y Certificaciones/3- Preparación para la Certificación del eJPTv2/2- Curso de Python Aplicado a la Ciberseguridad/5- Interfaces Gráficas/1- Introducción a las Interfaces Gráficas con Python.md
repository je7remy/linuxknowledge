
---

#Python #Tkinter #GUI #InterfazGrafica #Programacion #BucleDeEventos #Ventana #AplicacionPython

---
### **Paso 1: Importación del módulo Tkinter**

```python
import tkinter as tk
```

- Se importa el módulo `tkinter`, que es una biblioteca estándar en Python para crear interfaces gráficas de usuario (GUI).
- Se utiliza el alias `tk` para hacer referencia a `tkinter` de manera más compacta.

---

### **Paso 2: Creación de la ventana principal**

```python
ventana = tk.Tk()
```

- Se crea una instancia de la clase `Tk`, que representa la ventana principal de la aplicación.
- Esta ventana es el contenedor principal donde se colocarán los elementos gráficos (widgets) de la interfaz.

---

### **Paso 3: Configuración del título de la ventana**

```python
ventana.title("Mi primera app en Python")
```

- Se establece el título de la ventana con el método `.title()`.
- Este título aparecerá en la barra superior de la ventana.

---

### **Paso 4: Configuración del tamaño de la ventana**

```python
ventana.geometry("350x300")
```

- Se define el tamaño de la ventana en píxeles (ancho x alto).
- En este caso, la ventana tendrá un tamaño de **350 píxeles de ancho** y **300 píxeles de alto**.

---

### **Paso 5: Inicio del bucle principal**

```python
ventana.mainloop()
```

- Se inicia el **bucle de eventos** con `mainloop()`.
- Este bucle mantiene la ventana abierta y responde a eventos como clics o teclas presionadas.
- Sin este bucle, la ventana se cerraría inmediatamente después de abrirse.

---

### **Resumen:**

1. Se importó la biblioteca `tkinter`.
2. Se creó la ventana principal con `tk.Tk()`.
3. Se configuró el título de la ventana.
4. Se estableció un tamaño para la ventana.
5. Se inició el **bucle de eventos**, permitiendo que la interfaz funcione hasta que el usuario la cierre.

Este código es la estructura base de una aplicación gráfica en Python con `tkinter`.

```` python

# Importar la biblioteca tkinter con el alias tk
import tkinter as tk

# Crear una instancia de Tk, que es la ventana principal
ventana = tk.Tk()

# Establecer el título de la ventana
ventana.title("Mi primera app en Python")

# Establecer el tamaño de la ventana a 350x300 píxeles
ventana.geometry("350x300")

# Ejecutar el bucle principal de la ventana
ventana.mainloop()

````



