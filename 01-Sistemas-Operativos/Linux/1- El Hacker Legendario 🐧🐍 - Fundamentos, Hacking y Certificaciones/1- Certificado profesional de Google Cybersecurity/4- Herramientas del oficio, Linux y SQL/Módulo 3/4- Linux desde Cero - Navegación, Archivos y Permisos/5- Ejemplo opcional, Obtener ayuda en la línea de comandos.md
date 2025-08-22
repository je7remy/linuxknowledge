
# 📘 Obtén ayuda en la línea de comandos (Lab)

### 🔹 Tarea 1: Profundiza tus conocimientos sobre los comandos

1. Obtener descripción breve de `cat`
    

```bash
whatis cat
```

➡️ Respuesta: **concatenate files**

2. Ver más detalles sobre `cat` y sus opciones
    

```bash
man cat
```

➡️ Opción para enumerar todas las líneas: **-n, --number**

3. Encontrar el comando que muestra la primera parte de un archivo
    

```bash
apropos -a "first part file"
```

➡️ Respuesta: **head**

---

### 🔹 Tarea 2: Explora el comando useradd

1. Consultar manual completo:
    

```bash
man useradd
```

➡️ Opción para establecer fecha de vencimiento: **-e**

---

### 🔹 Tarea 3: Explora los comandos rm y rmdir

1. Ver descripción breve de `rm`:
    

```bash
whatis rm
```

2. Ver descripción breve de `rmdir`:
    

```bash
whatis rmdir
```

➡️ Respuesta: **rmdir** elimina solo directorios vacíos.

---

### 🔹 Tarea 4: Determina qué comando usar

1. Buscar comando para crear grupos:
    

```bash
apropos -a "create new group"
```

➡️ Respuesta: **groupadd**

---

## ✅ Conclusión

Con este lab practicaste el uso de tres herramientas clave de ayuda en Linux:

- `whatis` → descripción breve de un comando.
    
- `man` → manual completo con opciones y sintaxis.
    
- `apropos` → búsqueda por palabras clave en las páginas de manual.
    

Y además identificaste comandos específicos:

- `head` → mostrar primera parte de un archivo.
    
- `useradd -e` → crear usuario con fecha de vencimiento.
    
- `rmdir` → eliminar directorios vacíos.
    
- `groupadd` → crear un grupo nuevo.
    

---

