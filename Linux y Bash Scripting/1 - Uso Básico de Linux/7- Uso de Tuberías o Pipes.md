Las **tuberías** o **pipes** son una funcionalidad poderosa en sistemas operativos tipo UNIX, como Linux, que permite **conectar la salida de un comando con la entrada de otro**. Esto facilita encadenar múltiples comandos para realizar operaciones complejas de forma sencilla y eficiente.

---

### **1. `cat v.txt | wc -l`**

- **¿Qué hace?**:
    
    - `cat v.txt`: Muestra el contenido del archivo `v.txt`.
    - `|`: Pasa la salida del comando anterior como entrada al siguiente comando.
    - `wc -l`: Cuenta el número de líneas en la entrada proporcionada.
- **Resultado**:
    
    - Devuelve el número total de líneas en el archivo `v.txt`.

---

### **2. `cat v.txt | grep saludo`**

- **¿Qué hace?**:
    
    - `cat v.txt`: Muestra el contenido del archivo `v.txt`.
    - `|`: Pasa la salida del comando anterior como entrada al siguiente comando.
    - `grep saludo`: Busca todas las líneas que contienen la palabra **saludo** (sensible a mayúsculas/minúsculas).
- **Resultado**:
    
    - Devuelve todas las líneas del archivo `v.txt` que contienen la palabra **saludo**.

---

### **3. `cat v.txt | grep saludo | wc -l`**

- **¿Qué hace?**:
    
    - `cat v.txt`: Muestra el contenido del archivo `v.txt`.
    - `| grep saludo`: Filtra las líneas que contienen la palabra **saludo**.
    - `| wc -l`: Cuenta cuántas líneas contienen la palabra **saludo**.
- **Resultado**:
    
    - Devuelve el número total de líneas que contienen la palabra **saludo**.

---

### **4. `cat v.txt | sort | uniq`**

- **¿Qué hace?**:
    
    - `cat v.txt`: Muestra el contenido del archivo `v.txt`.
    - `| sort`: Ordena alfabéticamente las líneas del archivo.
    - `| uniq`: Elimina las líneas duplicadas (en líneas consecutivas).
- **Resultado**:
    
    - Devuelve las líneas únicas de `v.txt`, ordenadas alfabéticamente.

---

### **5. `cat v.txt | sort`**

- **¿Qué hace?**:
    
    - `cat v.txt`: Muestra el contenido del archivo `v.txt`.
    - `| sort`: Ordena alfabéticamente las líneas del archivo.
- **Resultado**:
    
    - Devuelve el contenido de `v.txt` ordenado alfabéticamente.

---

### **Resumen general del flujo**:

1. Los comandos utilizan `cat` para leer el contenido de un archivo llamado `v.txt`.
2. Se aplican filtros (`grep saludo`) para buscar palabras específicas.
3. Se realizan conteos de líneas (`wc -l`) o transformaciones como ordenar (`sort`) y eliminar duplicados (`uniq`).
4. Las tuberías (`|`) conectan los comandos para procesar datos en cadena.

