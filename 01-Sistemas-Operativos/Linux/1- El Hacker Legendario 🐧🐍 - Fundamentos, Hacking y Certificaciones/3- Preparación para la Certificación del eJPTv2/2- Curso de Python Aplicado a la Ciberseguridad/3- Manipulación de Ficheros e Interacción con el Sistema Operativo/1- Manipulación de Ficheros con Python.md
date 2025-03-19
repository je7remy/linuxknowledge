
📜 **La Épica Saga del Archivo "commits de hoy.txt"** 📜

---

💾 #ManejoDeArchivos #Python #LecturaYEscritura #ArchivosTXT 

---

### **Primer Acto: La Revelación del Contenido** 📖

🔹 **Abrimos el archivo en modo lectura (`"r"`)** para leer su contenido completo y mostrarlo en pantalla.

```python
# Abre el archivo en modo lectura
with open("commits de hoy.txt", "r") as archivo:  
    contenido = archivo.read()  # Lee todo el contenido  
    print(contenido)  # Muestra el contenido en pantalla
```

📜 **Explicación**:

- `with open("commits de hoy.txt", "r") as archivo:` → Abre el archivo en **modo lectura (`"r"`)**.
- `contenido = archivo.read()` → **Lee todo el contenido** y lo almacena en la variable `contenido`.
- `print(contenido)` → Muestra el contenido en pantalla.

💡 **En este momento, el código revela lo que hay dentro del archivo, como si descifraras un pergamino antiguo.**

---

### **Segundo Acto: La Gran Purga** 🔥

🔹 **Abrimos el archivo en modo escritura (`"w"`)**, eliminando todo su contenido y escribiendo un nuevo mensaje.

```python
# Abre el archivo en modo escritura, borrando su contenido
with open("commits de hoy.txt", "w") as archivo:  
    archivo.write("no hay commits que subir")  # Escribe el nuevo mensaje
```

📜 **Explicación**:

- `with open("commits de hoy.txt", "w") as archivo:` → Abre el archivo en **modo escritura (`"w"`)**, **eliminando** todo su contenido anterior.
- `archivo.write("no hay commits que subir")` → Escribe un nuevo mensaje en el archivo.

🔥 **Aquí, el pasado es borrado sin piedad, y un nuevo mensaje ocupa su lugar.**

---

### **Tercer Acto: La Inscripción de un Nuevo Mensaje** 🏛️

🔹 **Abrimos el archivo en modo apéndice (`"a"`)** para agregar una línea sin borrar lo anterior.

```python
# Abre el archivo en modo apéndice, manteniendo el contenido previo
with open("commits de hoy.txt", "a") as archivo:  
    archivo.write("\nno hay commits que subir (sin sustituir el contenido)")  # Agrega una nueva línea
```

📜 **Explicación**:

- `with open("commits de hoy.txt", "a") as archivo:` → Abre el archivo en **modo apéndice (`"a"`)**, **sin eliminar** su contenido.
- `archivo.write("\nno hay commits que subir (sin sustituir el contenido)")` → Agrega una nueva línea con `\n`.

📌 **Ahora, en vez de borrar lo anterior, agregamos un mensaje más. La historia del archivo se expande.**

---

### **Cuarto Acto: La Recitación del Texto Sagrado** 🎤

🔹 **Leemos el archivo línea por línea**, imprimiendo cada una.

```python
# Abre el archivo en modo lectura y lee línea por línea
with open("commits de hoy.txt", "r") as archivo:  
    for line in archivo:  # Itera sobre cada línea del archivo
        print(line.strip())  # Imprime la línea sin espacios extra
```

📜 **Explicación**:

- `with open("commits de hoy.txt", "r") as archivo:` → Abre el archivo en **modo lectura (`"r"`)**.
- `for line in archivo:` → Recorre el archivo **línea por línea**.
- `print(line.strip())` → Imprime cada línea sin espacios extra o saltos innecesarios.

📖 _El código ahora recita las palabras inscritas en el archivo, como un bardo compartiendo un relato legendario._

---
