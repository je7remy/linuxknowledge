Hola a todos, en esta vuelta vamos a desarrollar paso a paso el proceso de mejora del código proporcionado en el curso de Python aplicado a la ciberseguridad. Vamos a analizar detalladamente ambas versiones del código: la primera versión inicial y la segunda versión mejorada, explicando cada parte del código, los problemas identificados y cómo se resolvieron con la implementación de sentencias condicionales y excepciones. El objetivo es que quede claro el propósito de cada sección y cómo se logra un código más robusto y eficiente.

---

### **Primera Versión del Código**

Comencemos con la primera versión del código:

```python
import os

class SistemaOperativo:
    def __init__(self, nombre_archivo, nombre_carpeta, dueño):
        self.nombre_archivo = nombre_archivo
        self.nombre_carpeta = nombre_carpeta
        self.dueño = dueño

    def crear_carpeta(self):
        os.mkdir(self.nombre_carpeta)

    def crear_documento(self):
        with open(f"{self.nombre_archivo}", 'w') as file:
            file.write(f"Documento {self.nombre_archivo} propiedad de {self.dueño}")
    
    def borrar_todos(self):
        os.remove(self.nombre_archivo)
        os.rmdir(self.nombre_carpeta)
        print(f'Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}')

# Ejemplo de uso:
usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')

eleccion = input("Escribe 1 si quieres crear los archivos y 2 si los quieres eliminar")

if eleccion == "1":
    usuario1.crear_carpeta()
    usuario1.crear_documento()
elif eleccion == "2":
    usuario1.borrar_todos()
```

#### **Explicación Paso a Paso de la Primera Versión**

1. **Importación del Módulo `os`:**
   - La línea `import os` importa el módulo `os` de Python, que proporciona funciones para interactuar con el sistema operativo, como crear directorios (`os.mkdir`), eliminar archivos (`os.remove`) y eliminar directorios (`os.rmdir`).

2. **Definición de la Clase `SistemaOperativo`:**
   - Se define una clase llamada `SistemaOperativo` que utiliza programación orientada a objetos (POO).
   - El método `__init__` es el constructor de la clase y toma tres parámetros: `nombre_archivo`, `nombre_carpeta` y `dueño`. Estos se almacenan como atributos de la instancia usando `self`:
     - `self.nombre_archivo`: Nombre del archivo a crear (por ejemplo, `'contabilidad.doc'`).
     - `self.nombre_carpeta`: Nombre de la carpeta a crear (por ejemplo, `'documentos'`).
     - `self.dueño`: Nombre del propietario del documento (por ejemplo, `'Jeremy'`).

3. **Métodos de la Clase:**
   - **`crear_carpeta(self)`:**
     - Usa `os.mkdir(self.nombre_carpeta)` para crear un directorio con el nombre almacenado en `self.nombre_carpeta`.
     - Ejemplo: Si `self.nombre_carpeta = 'documentos'`, crea una carpeta llamada `documentos`.
   - **`crear_documento(self)`:**
     - Usa `with open(f"{self.nombre_archivo}", 'w') as file:` para abrir (o crear) un archivo en modo escritura (`'w'`).
     - Escribe en el archivo una línea de texto: `"Documento {self.nombre_archivo} propiedad de {self.dueño}"`.
     - Ejemplo: Si `self.nombre_archivo = 'contabilidad.doc'` y `self.dueño = 'Jeremy'`, el archivo contendrá: `"Documento contabilidad.doc propiedad de Jeremy"`.
   - **`borrar_todos(self)`:**
     - Elimina el archivo con `os.remove(self.nombre_archivo)`.
     - Elimina la carpeta con `os.rmdir(self.nombre_carpeta)`.
     - Imprime un mensaje: `"Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}"`.
     - Ejemplo: `"Se ha eliminado documentos y contabilidad.doc"`.

4. **Ejemplo de Uso:**
   - Se crea una instancia de la clase: `usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')`.
   - Se pide al usuario una entrada con `input("Escribe 1 si quieres crear los archivos y 2 si los quieres eliminar")`, que se almacena en la variable `eleccion`. El valor ingresado es un string (por ejemplo, `"1"` o `"2"`).
   - **Sentencia Condicional:**
     - Si `eleccion == "1"`: Llama a `crear_carpeta()` y `crear_documento()` para crear la carpeta y el archivo.
     - Si `eleccion == "2"`: Llama a `borrar_todos()` para eliminar ambos.

#### **Problemas Identificados**
- **Errores al Crear Archivos Existentes:**
  - Si la carpeta o el archivo ya existen (por ejemplo, si ejecutamos el código con `eleccion = "1"` dos veces), `os.mkdir()` lanza un error `FileExistsError`.
- **Errores al Eliminar Archivos No Existentes:**
  - Si intentamos eliminar archivos o carpetas que no existen (por ejemplo, ejecutando `eleccion = "2"` sin haber creado nada), `os.remove()` y `os.rmdir()` lanzan un error `FileNotFoundError`.
- **Falta de Robustez:**
  - El código no maneja estos errores, lo que provoca que el programa se detenga abruptamente.

---

### **Segunda Versión del Código (Mejorada)**

Ahora veamos la versión mejorada:

```python
import os

class SistemaOperativo:
    def __init__(self, nombre_archivo, nombre_carpeta, dueño):
        self.nombre_archivo = nombre_archivo
        self.nombre_carpeta = nombre_carpeta
        self.dueño = dueño

    def crear_carpeta(self):
        os.mkdir(self.nombre_carpeta)

    def crear_documento(self):
        with open(f"{self.nombre_archivo}", 'w') as file:
            file.write(f"Documento {self.nombre_archivo} propiedad de {self.dueño}")
    
    def borrar_todos(self):
        os.remove(self.nombre_archivo)
        os.rmdir(self.nombre_carpeta)
        print(f'Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}')

# Ejemplo de uso:
usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')

eleccion = input("Escribe 1 si quieres crear los archivos y 2 si los quieres eliminar: ")

if eleccion == "1":
    try:
        usuario1.crear_carpeta()
        usuario1.crear_documento()
    except:
        usuario1.borrar_todos()
        usuario1.crear_carpeta()
        usuario1.crear_documento()
    finally:
        print("El programa ha finalizado")

elif eleccion == "2":
    try:
        usuario1.borrar_todos()
    except:
        print("Hubo un error al eliminar los archivos, o quiza ya estaban eliminados")
```

#### **Explicación Paso a Paso de la Segunda Versión**

1. **Importación del Módulo `os`:**
   - Igual que en la primera versión, se importa `os` para las operaciones con el sistema de archivos.

2. **Definición de la Clase `SistemaOperativo`:**
   - La clase y sus métodos (`__init__`, `crear_carpeta`, `crear_documento`, `borrar_todos`) permanecen idénticos a la primera versión. Las mejoras se implementan en la sección de uso.

3. **Ejemplo de Uso Mejorado:**
   - **Instancia:** `usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')`, igual que antes.
   - **Entrada del Usuario:** 
     - `eleccion = input("Escribe 1 si quieres crear los archivos y 2 si los quieres eliminar: ")`.
     - Se añade un espacio después de los dos puntos (`: `) para mejorar la presentación visual del mensaje.

4. **Sentencia Condicional con Manejo de Excepciones:**
   - **Si `eleccion == "1"` (Crear Archivos):**
     - **Bloque `try`:**
       - Intenta ejecutar `usuario1.crear_carpeta()` y `usuario1.crear_documento()`.
       - Si no hay errores (es decir, la carpeta y el archivo no existen aún), se crean correctamente.
     - **Bloque `except`:**
       - Si ocurre un error (por ejemplo, `FileExistsError` porque la carpeta ya existe), se ejecuta este bloque.
       - Llama a `usuario1.borrar_todos()` para eliminar la carpeta y el archivo existentes.
       - Luego, recrea todo con `crear_carpeta()` y `crear_documento()`.
       - Esto asegura que siempre se creen los archivos, incluso si ya existían.
     - **Bloque `finally`:**
       - Imprime `"El programa ha finalizado"`, ejecutándose siempre, haya error o no. Sirve para confirmar que el proceso terminó.
   - **Si `eleccion == "2"` (Eliminar Archivos):**
     - **Bloque `try`:**
       - Intenta ejecutar `usuario1.borrar_todos()` para eliminar el archivo y la carpeta.
       - Si existen, se eliminan y se imprime el mensaje de confirmación.
     - **Bloque `except`:**
       - Si ocurre un error (por ejemplo, `FileNotFoundError` porque los archivos no existen), imprime: `"Hubo un error al eliminar los archivos, o quiza ya estaban eliminados"`.
       - Esto informa al usuario sin que el programa falle.

#### **Mejoras Implementadas**
- **Manejo de Errores:**
  - **Creación:** Si los archivos ya existen, se eliminan y recrean, evitando el `FileExistsError`.
  - **Eliminación:** Si los archivos no existen, se muestra un mensaje en lugar de fallar con `FileNotFoundError`.
- **Robustez:**
  - El uso de `try-except` hace que el programa sea más tolerante a fallos, manejando escenarios comunes como archivos preexistentes o inexistentes.
- **Retroalimentación:**
  - Los mensajes en `finally` y `except` informan al usuario sobre el resultado, mejorando la experiencia.
- **Presentación:**
  - El espacio en el `input` mejora la legibilidad.

---

### **Comparación y Beneficios**

| Aspecto                | Primera Versión                          | Segunda Versión                          |
|------------------------|------------------------------------------|------------------------------------------|
| **Manejo de Errores**  | No maneja errores, falla abruptamente    | Usa `try-except` para gestionar errores  |
| **Creación**           | Falla si archivos existen                | Elimina y recrea si es necesario         |
| **Eliminación**        | Falla si archivos no existen             | Informa al usuario sin fallar            |
| **Retroalimentación**  | Mensaje solo al eliminar                 | Mensajes en creación y eliminación       |

---

### **Prueba del Código Mejorado**

1. **Ejecutar con `eleccion = "1"`:**
   - Si no hay archivos, se crean la carpeta `documentos` y el archivo `contabilidad.doc`.
   - Si ya existen, se eliminan y recrean.
   - Salida: `"El programa ha finalizado"`.

2. **Ejecutar con `eleccion = "2"`:**
   - Si los archivos existen, se eliminan y se muestra: `"Se ha eliminado documentos y contabilidad.doc"`.
   - Si no existen, se muestra: `"Hubo un error al eliminar los archivos, o quiza ya estaban eliminados"`.

---

### **Conclusión**

Hemos transformado un código básico con problemas de estabilidad en una versión más robusta y amigable mediante:
- **Sentencias Condicionales:** Para elegir entre crear o eliminar según la entrada del usuario.
- **Excepciones:** Para manejar errores como archivos existentes o inexistentes.
- **Programación Orientada a Objetos:** Manteniendo la estructura de la clase `SistemaOperativo`.

Este ejemplo ilustra cómo combinar conceptos fundamentales de Python (POO, condicionales, excepciones) para crear programas más confiables, especialmente en contextos como la ciberseguridad, donde la interacción con el sistema de archivos es común. Espero que esta explicación detallada haya aclarado cada parte del código y su evolución. 