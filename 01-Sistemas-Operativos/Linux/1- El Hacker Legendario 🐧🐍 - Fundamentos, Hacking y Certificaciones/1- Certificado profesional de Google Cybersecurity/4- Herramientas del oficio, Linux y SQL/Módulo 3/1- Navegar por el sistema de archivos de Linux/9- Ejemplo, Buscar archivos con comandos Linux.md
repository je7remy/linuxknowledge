
## 🧪 **Resumen de la Actividad - Laboratorio Linux (Qwiklabs)**

### 🎯 **Objetivo General**

Practicar habilidades básicas de uso del shell Bash en Linux para navegar por directorios, listar archivos y leer su contenido sin usar una interfaz gráfica. Estas habilidades son esenciales para un analista de seguridad.

---

## 🧱 **Escenario Práctico**

Trabajar dentro de la ruta `/home/analyst`, realizando varias tareas específicas con archivos y directorios.

---

## 🔹 **Tarea 1: Verificar el directorio actual**

- Comando: `pwd`
    
    - ✅ Salida esperada: `/home/analyst`
        
- Comando: `ls`
    
    - ✅ Salida esperada: `logs projects reports temp`
        
- **Respuestas**:
    
    - Directorio actual: `/home/analyst`
        
    - Contenido: 4 subdirectorios (`logs`, `projects`, `reports`, `temp`)
        

---

## 🔹 **Tarea 2: Navegar y listar subdirectorios**

- Comando para cambiar a reports:
    
    - Relativa: `cd reports`
        
    - Absoluta: `cd /home/analyst/reports`
        
- Comando para listar contenido: `ls`
    
    - ✅ Salida esperada: `users`
        
- **Respuesta**:
    
    - Subdirectorio en `reports`: `users`
        

---

## 🔹 **Tarea 3: Leer contenido de un archivo**

- Comando para acceder: `cd /home/analyst/reports/users`
    
- Comando para listar archivos: `ls`
    
- Comando para leer archivo: `cat Q1_added_users.txt`
    
- **Respuestas**:
    
    - Usuario `aezra`: trabaja en _Recursos Humanos_
        
    - Usuario `mreed`: su `employee_id` es _1104_, trabaja en _TI_
        

---

## 🔹 **Tarea 4: Examinar logs**

- Comando para acceder: `cd /home/analyst/logs`
    
- Comando para listar: `ls`
    
    - ✅ Salida esperada: `server_logs.txt`
        
- Comando para leer primeras 10 líneas: `head server_logs.txt`
    
- **Respuesta**:
    
    - Mensajes de advertencia (`warning`) en las primeras 10 líneas: **3**
        

---

## ✅ **Conclusión**

Aprendiste a utilizar:

- `pwd`: mostrar directorio actual
    
- `cd`: navegar entre directorios
    
- `ls`: listar contenido
    
- `cat`: mostrar contenido completo de un archivo
    
- `head`: mostrar primeras líneas de un archivo
    
- `tail`: mostrar ultimas líneas de un archivo
    

Estas habilidades son clave para administración de sistemas y análisis forense en ciberseguridad.

---
