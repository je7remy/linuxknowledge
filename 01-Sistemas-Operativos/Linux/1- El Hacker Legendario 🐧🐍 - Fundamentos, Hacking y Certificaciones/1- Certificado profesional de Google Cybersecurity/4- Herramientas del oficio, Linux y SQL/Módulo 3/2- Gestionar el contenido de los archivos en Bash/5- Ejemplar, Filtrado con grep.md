
**objetivo**  

practicar el uso de `grep` y tuberías en linux para buscar cadenas de texto y filtrar información en archivos y listados

**escenario**

- analizar registros del servidor
    
- encontrar archivos por nombre
    
- buscar contenido específico dentro de archivos de usuarios
    

**tareas**

1. **buscar errores en logs**
    
    - ruta: `/home/analyst/logs`
        
    - comando:
        
        ```bash
        cd logs
        grep error server_logs.txt
        ```
        
    - resultado: 6 líneas con la palabra "error"
        
2. **buscar archivos con cadenas específicas**
    
    - ruta: `/home/analyst/reports/users`
        
    - encontrar archivos con "Q1":
        
        ```bash
        ls | grep Q1
        ```
        
        → 3 archivos
        
    - encontrar archivos con "access":
        
        ```bash
        ls | grep access
        ```
        
        → 4 archivos
        
3. **buscar contenido dentro de archivos**
    
    - verificar si `jhill` está en `Q2_deleted_users.txt`:
        
        ```bash
        grep jhill Q2_deleted_users.txt
        ```
        
        → sí aparece
        
    - listar usuarios añadidos a "Human Resources" en `Q4_added_users.txt`:
        
        ```bash
        grep "Human Resources" Q4_added_users.txt
        ```
        

