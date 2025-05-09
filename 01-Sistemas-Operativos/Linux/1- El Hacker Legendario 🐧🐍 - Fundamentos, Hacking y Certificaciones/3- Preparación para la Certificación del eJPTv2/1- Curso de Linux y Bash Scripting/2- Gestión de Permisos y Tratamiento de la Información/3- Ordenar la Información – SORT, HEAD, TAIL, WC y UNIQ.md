
---

#Linux #ShellCommands #FileManipulation #Sort #Head #Tail #Cat #Uniq #WC #CommandLine #SysAdmin #Scripting

---
Los comandos están relacionados con la manipulación de archivos en Linux utilizando herramientas básicas como `sort`, `head`, `tail`, `cat`, `uniq`, y `wc`.

---

### **Comandos relacionados con `sort`**

1. **`sort nombres.txt`**
    
    - Ordena alfabéticamente las líneas del archivo `nombres.txt`.
2. **`sort -n numeros`**
    
    - Ordena numéricamente las líneas del archivo `numeros`.
3. **`sort -n -r numeros`**
    
    - Ordena numéricamente las líneas del archivo `numeros` en orden inverso (descendente).
4. **`sort -n -u numeros`**
    
    - Ordena numéricamente las líneas del archivo `numeros` y elimina las líneas duplicadas (`-u` para _unique_).

---

### **Comandos relacionados con `head`**

5. **`head nombreshead`**
    
    - Muestra las primeras 10 líneas del archivo `nombreshead`.
6. **`head -n 5 nombreshead`**
    
    - Muestra las primeras 5 líneas del archivo `nombreshead`.
7. **`head -n 50 nombreshead`**
    
    - Muestra las primeras 50 líneas del archivo `nombreshead`.
8. **`head -n 2 nombreshead nombres`**
    
    - Muestra las primeras 2 líneas del archivo `nombreshead` y luego pasa al archivo `nombres`, mostrando también las primeras 2 líneas de este.

---

### **Comandos relacionados con `tail`**

9. **`tail nombreshead`**
    
    - Muestra las últimas 10 líneas del archivo `nombreshead`.
10. **`tail -n 5 nombreshead`**
    
    - Muestra las últimas 5 líneas del archivo `nombreshead`.
11. **`tail -n 50 nombreshead`**
    
    - Muestra las últimas 50 líneas del archivo `nombreshead`.
12. **`tail -n 2 nombreshead nombres`**
    
    - Muestra las últimas 2 líneas del archivo `nombreshead` y luego pasa al archivo `nombres`, mostrando también las últimas 2 líneas de este.

---

### **Comandos relacionados con `cat` y `wc`**

13. **`cat nombres | wc -l`**
    
    - Cuenta la cantidad de líneas en el archivo `nombres`.
14. **`cat nombres | wc -w`**
    
    - Cuenta la cantidad de palabras en el archivo `nombres`.
15. **`cat nombres | wc -c`**
    
    - Cuenta la cantidad de caracteres (bytes) en el archivo `nombres`.
16. **`cat * | wc -c`**
    
    - Cuenta la cantidad de caracteres (bytes) en todos los archivos del directorio actual (`*`).
17. **`cat * | wc -l`**
    
    - Cuenta la cantidad de líneas en todos los archivos del directorio actual.
18. **`cat * | wc -w`**
    
    - Cuenta la cantidad de palabras en todos los archivos del directorio actual.

---

### **Comandos relacionados con `uniq` y `sort`**

19. **`cat nombres | uniq`**
    
    - Muestra las líneas únicas en el archivo `nombres`, eliminando duplicados consecutivos.
20. **`cat nombres | uniq | sort`**
    
    - Primero elimina duplicados consecutivos en el archivo `nombres` y luego ordena las líneas alfabéticamente.
21. **`cat nombres | uniq | sort | wc -l`**
    
    - Elimina duplicados consecutivos en el archivo `nombres`, ordena las líneas alfabéticamente y cuenta el total de líneas únicas resultantes.

---

### **Resumen de lo que ocurre en los comandos**

- **`sort`** organiza el contenido de archivos (alfabéticamente o numéricamente).
- **`head` y `tail`** muestran las primeras o últimas líneas de un archivo.
- **`wc`** se utiliza para contar líneas, palabras y caracteres en archivos.
- **`uniq`** elimina duplicados consecutivos, mientras que **`cat`** concatena y muestra contenido de archivos.

[[9- Uso de Grep]]
[[5- Comando find y redirección de errores]]
[[6- Comando XARGS]]

