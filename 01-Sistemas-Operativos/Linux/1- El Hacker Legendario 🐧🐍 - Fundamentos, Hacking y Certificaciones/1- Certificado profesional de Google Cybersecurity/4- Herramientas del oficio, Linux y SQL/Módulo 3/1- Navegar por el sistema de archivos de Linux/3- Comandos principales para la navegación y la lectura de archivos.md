---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Comandos principales para la navegación y la lectura de archivos

# 📁 Navegar el sistema de archivos en Linux

## 👋 Bienvenida a la sección

> _"Bienvenido de nuevo. Espero que esté aprendiendo mucho sobre cómo comunicarse con el OS Linux."_

En esta parte del curso, aprenderás a **navegar por el sistema de archivos** mediante comandos en la línea de comandos (Bash), una habilidad fundamental para los analistas de seguridad.

---

## 🌳 Metáfora del árbol

Piensa en el sistema de archivos de Linux como un **árbol**:

- 🌱 **Raíz** (root) = `/`
    
- 🌿 **Subdirectorios** = ramas del árbol
    
- 📁 Todo en Linux es un **archivo**, y se organiza jerárquicamente desde la raíz usando el **FHS (File Hierarchy Standard)**
    

Ejemplo de ruta:

```
/home/analyst
```

- `/` → raíz
    
- `home` → subdirectorio
    
- `analyst` → subdirectorio dentro de `home`
    

---

## 🛡️ Importancia para la ciberseguridad

Como **analista de seguridad**, necesitas:

- Localizar y analizar **archivos de registro**
    
- Verificar accesos, configuraciones y eventos sospechosos
    
- Navegar sin interfaz gráfica (solo con terminal)
    

---

## 🔧 Comandos esenciales para navegar el sistema

|Comando|Función|
|---|---|
|`pwd`|Muestra el directorio actual|
|`ls`|Lista los archivos y carpetas del directorio actual|
|`cd`|Cambia de directorio|

---

## 🧪 Ejemplo práctico (Transcripción desde 2:26)

1. **Mostrar ubicación actual:**
    

```bash
pwd
```

➡️ Muestra: `/home/analyst`

2. **Listar archivos y carpetas:**
    

```bash
ls
```

➡️ Muestra:  
`logs`  
`informes antiguos`  
`proyectos`  
`informes`  
`updates.txt`

3. **Entrar al directorio `logs`:**
    

```bash
cd logs
```

4. **Confirmar nueva ubicación:**
    

```bash
pwd
```

➡️ Resultado: `/home/analyst/logs`

---

## 📖 Lectura de archivos en Linux

### Comandos para ver el contenido:

|Comando|Función|
|---|---|
|`cat archivo.txt`|Muestra el contenido completo del archivo|
|`head archivo.txt`|Muestra solo las primeras 10 líneas del archivo|

---

## 🧪 Ejemplo práctico (Transcripción desde 3:59)

1. **Leer archivo completo:**
    

```bash
cat acceso.txt
```

2. **Leer solo el inicio:**
    

```bash
head acceso.txt
```

---

## 🎉 Cierre de la sección

> _"¡Vaya, esta sección tenía mucha acción, y es solo el principio!"_  
> _"Me alegro de que haya aprendido cómo los analistas de seguridad pueden utilizar comandos esenciales para navegar por el sistema."_

Próximo tema: **Gestión del sistema**.

---

## ❓ **Pregunta:**

**¿Qué hace el comando `ls`?**

### Opciones:

-  Muestra el contenido de un archivo.
    
-  Imprime el directorio de trabajo en la pantalla.
    
- [✅] **Muestra los nombres de los archivos y directorios del directorio de trabajo actual.**
    
-  Muestra sólo el principio de un archivo, por defecto 10 líneas.
    

---

✅ **Respuesta correcta:**  
**Muestra los nombres de los archivos y directorios del directorio de trabajo actual.**

📌 _El comando `ls` (list) se usa para ver qué hay dentro de un directorio en Linux: archivos, carpetas, etc._

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[2- Comandos Linux a través del shell Bash]]
- ➡️ Siguiente: [[4- Navegar por Linux y leer el contenido de los archivos]]
