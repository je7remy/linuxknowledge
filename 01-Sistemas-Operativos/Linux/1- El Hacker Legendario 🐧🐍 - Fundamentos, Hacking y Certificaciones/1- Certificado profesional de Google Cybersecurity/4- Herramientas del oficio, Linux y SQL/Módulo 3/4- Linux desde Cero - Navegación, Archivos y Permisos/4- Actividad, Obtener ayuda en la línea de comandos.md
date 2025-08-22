
## 🔹 Tarea 1: Obtener más información sobre los comandos

- Para ver descripción breve de `cat`:
    

```bash
whatis cat
```

👉 Respuesta: las dos primeras palabras son **cat is**

- Para ver más detalles sobre `cat`:
    

```bash
man cat
```

👉 Opción para enumerar todas las líneas: **-n, --number**

- Para encontrar el comando que muestra la primera parte de un archivo:
    

```bash
apropos -a "first part file"
```

👉 Respuesta: **head**

---

## 🔹 Tarea 2: Explora el comando useradd

- Para ver todas sus opciones:
    

```bash
man useradd
```

👉 Opción para configurar fecha de vencimiento de cuenta: **-e**

---

## 🔹 Tarea 3: Explora los comandos rm y rmdir

- Para obtener descripción breve de cada uno:
    

```bash
whatis rm
whatis rmdir
```

👉 Respuesta: el que elimina solo directorios vacíos es **rmdir**

---

## 🔹 Tarea 4: Determina qué comando usar

- Para encontrar qué comando crea un grupo:
    

```bash
apropos -a "create new group"
```

👉 Respuesta: **groupadd**

---

✅ **Resumen de respuestas finales:**

- **Tarea 1** → `whatis cat`, `man cat`, `apropos -a "first part file"` → respuestas: _cat is_, `-n`, `head`
    
- **Tarea 2** → `man useradd` → respuesta: `-e`
    
- **Tarea 3** → `whatis rm`, `whatis rmdir` → respuesta: `rmdir`
    
- **Tarea 4** → `apropos -a "create new group"` → respuesta: `groupadd`
    

---
