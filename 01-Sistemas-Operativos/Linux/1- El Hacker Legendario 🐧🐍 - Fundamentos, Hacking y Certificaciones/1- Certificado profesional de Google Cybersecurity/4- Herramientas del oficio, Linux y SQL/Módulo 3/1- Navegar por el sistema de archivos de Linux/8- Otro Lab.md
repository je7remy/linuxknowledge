---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Otro Lab
## ✅ Tarea 1: Obtén información del directorio actual

🔹 **Comandos ejecutados:**

```bash
pwd
ls
```

🔹 **Resultados esperados:**

- Directorio actual: `/home/analyst`
    
- Contenido del directorio: `logs`, `projects`, `reports`, `temp`
    

🔹 **Preguntas:**

- Directorio actual → ✅ `/home/analyst`
    
- ¿Cuántos directorios? → ✅ Cuatro
    

---

## ✅ Tarea 2: Cambia el directorio y obtén una lista de los subdirectorios

🔹 **Comandos ejecutados:**

```bash
cd reports        # o bien:
cd /home/analyst/reports
ls
```

🔹 **Resultado:**

- Subdirectorio contenido: `users`
    

🔹 **Pregunta:**

- ¿Subdirectorio en /home/analyst/reports? → ✅ `users`
    

---

## ✅ Tarea 3: Ubica y lee el contenido de un archivo

🔹 **Comandos ejecutados:**

```bash
cd /home/analyst/reports/users
ls
cat Q1_added_users.txt
```

🔹 **Archivo leído:**

- `Q1_added_users.txt`
    

🔹 **Preguntas:**

- Usuario `aezra` → ✅ Departamento: `Human Resources`
    
- Usuario `mreed` en IT → ✅ `employee_id`: `1104`
    

---

## ✅ Tarea 4: Navega hasta un directorio y ubica un archivo

🔹 **Comandos ejecutados:**

```bash
cd /home/analyst/logs
ls
head server_logs.txt
```

🔹 **Archivo ubicado:**

- `server_logs.txt`
    

🔹 **Pregunta:**

- ¿Cuántos mensajes de advertencia en las primeras 10 líneas? → ✅ **Tres**
    

---

## ✅ Comandos clave del lab

```bash
pwd                       # Muestra el directorio actual
ls                        # Lista archivos/directorios
cd <ruta>                 # Cambia de directorio
cat <archivo>             # Muestra todo el contenido de un archivo
head <archivo>            # Muestra las primeras 10 líneas del archivo
```

---

## 🏁 Conclusión

Has adquirido práctica en:

- Navegación por el sistema de archivos Linux
    
- Visualización de contenido de archivos
    
- Uso correcto de rutas absolutas y relativas
    
- Identificación de información clave en archivos de texto
    

---

## 🔚 Finaliza el lab

1. Haz clic en **“End Lab”**
    
2. Luego haz clic en **“Submit”**
    
3. Cierra la pestaña del lab y vuelve al curso
    
4. **Actualiza** la página del curso para que se marque como completado
    

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[7- Ejemplar opcional, Encontrar archivos con los comandos de Linux]]
- ➡️ Siguiente: [[9- Ejemplo, Buscar archivos con comandos Linux]]
