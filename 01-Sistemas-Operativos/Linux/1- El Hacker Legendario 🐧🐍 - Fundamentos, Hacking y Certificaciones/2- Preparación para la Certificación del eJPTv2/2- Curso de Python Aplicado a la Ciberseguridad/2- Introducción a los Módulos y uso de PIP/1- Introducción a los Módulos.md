
---

#Python #Programación #MódulosPython #ImportPython #CódigoReutilizable #RandomPython #FuncionesPython #Scripting #Automatización #PythonDesdeCero 🚀🐍

---
### 📌 **Introducción a los Módulos en Python**

Un **módulo** en Python es un archivo que contiene código reutilizable, como funciones, clases y variables. Los módulos permiten organizar mejor el código y facilitan la reutilización en diferentes programas.

Existen tres tipos de módulos en Python:

1. **Módulos estándar:** Vienen incluidos con Python, como `random`, `math`, `os`, etc.
2. **Módulos personalizados:** Son archivos `.py` creados por el usuario.
3. **Módulos de terceros:** Deben ser instalados con herramientas como `pip` (ej. `numpy`, `pandas`).

Ahora, veremos un ejemplo de uso de módulos en Python, explicando paso a paso.

---

## 🔹 **Paso 1: Crear el módulo `modulo.py`**

Este archivo contendrá una función llamada `saludar()` que imprimirá un mensaje.

📄 **Contenido de `modulo.py`:**

```python
def saludar():
    print("Hola, mensaje desde modulo.py")
```

---

## 🔹 **Paso 2: Crear `script1.py` y usar el módulo**

Ahora creamos otro archivo llamado `script1.py`, donde importaremos el módulo `modulo` y usaremos la función `saludar()`.

📄 **Contenido de `script1.py`:**

```python
import modulo  # Importamos el módulo

modulo.saludar()  # Llamamos a la función definida en modulo.py
```

---

## 🔹 **Paso 3: Ejecutar `script1.py`**

Para ejecutar el archivo en la terminal, usamos:

```sh
python script1.py
```

### 📌 **Salida esperada:**

```
Hola, mensaje desde modulo.py
```

---

## 🔹 **Paso 4: Crear `script3.py` y usar un módulo estándar**

Ahora crearemos otro script llamado `script3.py`, donde usaremos el módulo `random` de Python para generar un número aleatorio.

📄 **Contenido de `script3.py`:**

```python
import random  # Importamos el módulo estándar random

numero_aleatorio = random.randint(1, 100)  # Generamos un número aleatorio entre 1 y 100

print("Numero aleatorio:", numero_aleatorio)  # Mostramos el número generado
```

---

## 🔹 **Paso 5: Ejecutar `script3.py`**

Para ejecutarlo, usamos:

```sh
python script3.py
```

### 📌 **Salida esperada (puede variar cada vez):**

```
Numero aleatorio: 13
```

_(El número puede cambiar en cada ejecución porque es generado aleatoriamente)._

---

### ✅ **Conclusión**

- Un **módulo** es un archivo `.py` que contiene código reutilizable.
- Se puede importar un módulo con `import nombre_modulo`.
- Se pueden usar tanto módulos creados por el usuario como módulos estándar de Python (`random`, `math`, etc.).
- Ejecutar `python nombre_script.py` en la terminal permite probar los módulos en acción.