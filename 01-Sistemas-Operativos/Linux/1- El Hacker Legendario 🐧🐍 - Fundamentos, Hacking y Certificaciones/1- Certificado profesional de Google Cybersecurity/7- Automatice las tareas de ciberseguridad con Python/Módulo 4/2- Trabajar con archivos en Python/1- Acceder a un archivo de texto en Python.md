---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Acceder a un archivo de texto en Python


## 📂 Acceder a un Archivo de Texto en Python

Los profesionales de la seguridad a menudo revisan archivos de registro (`.log`, `.txt`, `.csv`), que pueden ser enormes. Python puede automatizar este proceso. El primer paso es aprender a abrir y leer el contenido de estos archivos.

---

## 🔑 La Sentencia `with open()`

La forma recomendada para trabajar con archivos en Python es usando la sentencia `with open()`.

**¿Por qué `with`?**

- **Gestión de Recursos:** Se encarga automáticamente de **cerrar el archivo** una vez que terminas de trabajar con él (incluso si ocurren errores). Esto libera recursos del sistema.
    
- **Manejo de Errores:** Ayuda a manejar posibles problemas al interactuar con el archivo.
    

**Sintaxis General:**

Python

```
with open("nombre_del_archivo.txt", "modo") as variable_archivo:
    # Código indentado que trabaja con el archivo
    # ...
```

**Desglose:**

1. **`with`**: Palabra clave que inicia el bloque de gestión de contexto.
    
2. **`open()`**: Función integrada para abrir un archivo. Acepta (al menos) dos parámetros:
    
    - **Parámetro 1 (Nombre del archivo):** Una cadena con el nombre del archivo (incluyendo la extensión, ej. `.txt`) y, si es necesario, la ruta completa a su ubicación.
        
    - **Parámetro 2 (Modo):** Una cadena que indica qué quieres hacer con el archivo. Los modos más comunes son:
        
        - `"r"`: **Leer** (Read) - Modo por defecto si no se especifica. Abre el archivo para lectura.
            
        - `"w"`: **Escribir** (Write) - Abre el archivo para escritura. _Si el archivo existe, sobrescribe su contenido. Si no existe, lo crea._
            
        - `"a"`: **Añadir** (Append) - Abre el archivo para añadir contenido al final. Si no existe, lo crea.
            
3. **`as variable_archivo`**: Asigna el objeto archivo abierto a una variable (puedes llamarla como quieras, `file`, `f`, `archivo`, etc.). Esta variable solo está disponible _dentro_ del bloque `with`.
    
4. **`:`**: Indica el final de la sentencia `with` y el inicio del bloque indentado.
    
5. **Bloque Indentado:** Código que opera sobre `variable_archivo`.
    

---

## 📖 Leer el Contenido: El Método `.read()`

Una vez que el archivo está abierto (dentro del bloque `with`), puedes leer su contenido. El método más simple para leer **todo el contenido** como una **única cadena de texto** es `.read()`.

**Ejemplo Completo:**

Python

```
# Asumiendo que existe un archivo llamado "mi_archivo.txt"
# con el texto "Hola Python."

# 1. Abrir el archivo en modo lectura ("r")
with open("mi_archivo.txt", "r") as archivo:
    # 2. Leer todo el contenido y guardarlo en una variable
    contenido_completo = archivo.read()

# 3. El archivo se cierra automáticamente al salir del bloque 'with'.

# 4. Ahora puedes usar la variable 'contenido_completo' fuera del bloque.
print(contenido_completo)
```

📤 **Salida:**

```
Hola Python.
```

---

## 💡 Próximos Pasos

Ahora que sabes cómo leer el contenido de un archivo en una cadena, el siguiente paso es aprender a **analizar sintácticamente (parsear)** esa cadena para extraer la información específica que necesitas, preparándote para manejar registros de seguridad más complejos.


### 🧠 Pregunta

¿Qué le indica a Python la línea de código `with open("ip_addresses.txt", "r") as file:`? (Seleccione dos respuestas).

- Almacene el objeto de archivo en la variable `file` dentro de la sentencia `with`.
    
- Cree un nuevo archivo llamado `"ip_addresses.txt"`.
    
- Escriba la cadena `"r"` en el archivo `"ip_addresses.txt"`.
    
- Abra el archivo `"ip_addresses.txt"` para poder leerlo.
    

---

### ✅ Respuestas correctas:

- **Almacene el objeto de archivo en la variable `file` dentro de la sentencia `with`.**
    
- **Abra el archivo `"ip_addresses.txt"` para poder leerlo.**
    

---

### 📘 Justificación:

La línea de código `with open("ip_addresses.txt", "r") as file:` realiza dos acciones principales:

1. **`open("ip_addresses.txt", "r")`**: Llama a la función `open()` para **abrir** el archivo llamado `"ip_addresses.txt"`. El segundo argumento, `"r"`, especifica el **modo** de apertura, que en este caso es para **leer** (read).
    
2. **`as file`**: Toma el objeto de archivo que `open()` devuelve y lo **asigna** a la variable `file`. Esta variable estará disponible para usar dentro del bloque de código indentado que sigue a la sentencia `with`.
    

Las otras opciones son incorrectas porque:

- `"r"` solo indica el modo de lectura, no que se escriba esa letra en el archivo.
    
- Abrir en modo lectura (`"r"`) no crea un archivo si no existe (eso lo haría el modo escritura `"w"` o añadir `"a"`).

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ➡️ Siguiente: [[2- Importar archivos a Python]]
