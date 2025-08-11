
# 📂 Lab – Administrar archivos con comandos de Linux

## 📌 Situación

Organizar el directorio `/home/analyst` y sus subdirectorios, moviendo, eliminando y creando archivos, además de editar con **nano**.

---

## 📝 Tareas realizadas

### **Tarea 1 – Crear directorio nuevo**

```bash
mkdir /home/analyst/logs
ls /home/analyst
```

✅ Aparece `logs` junto con los demás directorios.

---

### **Tarea 2 – Quitar un directorio**

```bash
rmdir /home/analyst/temp
ls /home/analyst
```

✅ `temp` ya no está en la lista.

---

### **Tarea 3 – Mover un archivo**

```bash
cd /home/analyst/notes
mv Q3patches.txt /home/analyst/reports/
ls /home/analyst/reports
```

✅ Ahora `Q1patches.txt Q2patches.txt Q3patches.txt` están juntos.

---

### **Tarea 4 – Quitar un archivo**

```bash
rm /home/analyst/notes/tempnotes.txt
ls /home/analyst/notes
```

✅ El directorio `notes` queda vacío.

---

### **Tarea 5 – Crear un archivo nuevo**

```bash
touch /home/analyst/notes/tasks.txt
ls /home/analyst/notes
```

✅ `tasks.txt` creado.

---

### **Tarea 6 – Editar un archivo**

```bash
nano /home/analyst/notes/tasks.txt
```

Contenido añadido:

```
Completed tasks
1. Managed file structure in /home/analyst
```

Guardar → `Ctrl + X` → `Y` → `Enter`  
Limpiar y verificar:

```bash
clear
cat /home/analyst/notes/tasks.txt
```

✅ Contenido confirmado.

---

## 📊 Estructura final

```
/home/analyst
├── logs
├── notes
│   └── tasks.txt
└── reports
    ├── Q1patches.txt
    ├── Q2patches.txt
    └── Q3patches.txt
```



---


# Repaso

# 🐧 Lab – Administrar archivos con comandos de Linux

## 📌 Resumen

Objetivo: Organizar el directorio `/home/analyst` usando comandos básicos de Linux y el editor de texto **nano**.  
Tareas: crear/eliminar directorios, mover/eliminar archivos y editar contenido.

---

## 🗂 Situación inicial

Estructura original:

```
/home/analyst
├── notes
│   ├── Q3patches.txt
│   └── tempnotes.txt
├── reports
│   ├── Q1patches.txt
│   └── Q2patches.txt
└── temp
```

Estructura final deseada:

```
/home/analyst
├── logs
├── notes
│   └── tasks.txt
└── reports
    ├── Q1patches.txt
    ├── Q2patches.txt
    └── Q3patches.txt
```

---

## ✅ Pasos y comandos

### 1️⃣ Crear directorio `logs`

```bash
mkdir /home/analyst/logs
ls /home/analyst
```

Resultado esperado:

```
logs notes reports temp
```

---

### 2️⃣ Eliminar directorio `temp`

```bash
rmdir /home/analyst/temp
ls /home/analyst
```

Resultado esperado:

```
logs notes reports
```

---

### 3️⃣ Mover `Q3patches.txt` a `reports`

```bash
cd /home/analyst/notes
mv Q3patches.txt /home/analyst/reports/
ls /home/analyst/reports
```

Resultado esperado:

```
Q1patches.txt  Q2patches.txt  Q3patches.txt
```

---

### 4️⃣ Eliminar `tempnotes.txt`

```bash
rm /home/analyst/notes/tempnotes.txt
ls /home/analyst/notes
```

Resultado esperado:  
Directorio vacío.

---

### 5️⃣ Crear `tasks.txt`

```bash
touch /home/analyst/notes/tasks.txt
ls /home/analyst/notes
```

Resultado esperado:

```
tasks.txt
```

---

### 6️⃣ Editar `tasks.txt` con **nano**

```bash
nano /home/analyst/notes/tasks.txt
```

Contenido a agregar:

```
Completed tasks
1. Managed file structure in /home/analyst
```

Guardar → `Ctrl + X` → `Y` → `Enter`  
Limpiar y verificar:

```bash
clear
cat /home/analyst/notes/tasks.txt
```

Resultado esperado:

```
Completed tasks
1. Managed file structure in /home/analyst
```

---

## 📊 Resultado final

```
/home/analyst
├── logs
├── notes
│   └── tasks.txt
└── reports
    ├── Q1patches.txt
    ├── Q2patches.txt
    └── Q3patches.txt
```

---

## 📌 Conclusión

En este lab se practicó:

- Crear y eliminar directorios (`mkdir`, `rmdir`)
    
- Mover y eliminar archivos (`mv`, `rm`)
    
- Crear archivos vacíos (`touch`)
    
- Editar con **nano** y guardar cambios
    
- Verificar estructuras y contenidos con `ls` y `cat`
    

---
