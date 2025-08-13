
## **Cambiar permisos con `chmod` en Linux**

En el trabajo como analista de seguridad, es común tener que cambiar los permisos de un usuario. Esto puede ser necesario si:

- Cambia de departamento.
    
- Se le asigna a otro grupo de trabajo.
    
- Ya no participa en un proyecto que requiere ciertos permisos.
    

Estos ajustes ayudan a **proteger los archivos del sistema** contra modificaciones accidentales o intencionales.

---

### **Comando `chmod` (modo simbólico)**

`chmod` significa _change mode_ y permite cambiar permisos en archivos y directorios.  
Nos enfocaremos en **modo simbólico**.

#### **Identificadores de propietario**

- **u** → usuario (owner)
    
- **g** → grupo
    
- **o** → otros
    

#### **Operadores**

- **+** → añadir permiso
    
- **-** → quitar permiso
    

#### **Tipos de permisos**

- **r** → lectura (_read_)
    
- **w** → escritura (_write_)
    
- **x** → ejecución (_execute_)
    

---

### **Ejemplo práctico**

Archivo: `access.txt`

1. **Permisos iniciales**
    
    ```
    rw- r-- r--
    ```
    
    - Usuario (u): lectura y escritura (`rw-`)
        
    - Grupo (g): solo lectura (`r--`)
        
    - Otros (o): solo lectura (`r--`)
        
2. **Objetivo**
    
    - Añadir escritura al grupo (`g+w`)
        
    - Quitar lectura a otros (`o-r`)
        
3. **Comando**
    
    ```bash
    chmod g+w,o-r access.txt
    ```
    
4. **Resultado**
    
    ```
    rw- rw- ---
    ```
    
    - Grupo ahora tiene escritura.
        
    - Otros no tienen permisos.
        

---

✅ Con la práctica, estos cambios se vuelven naturales y rápidos de aplicar en Linux.

---

# **Pregunta**  

### Si desea cambiar los permisos de un archivo `approved_users.txt`, ¿qué comando puede utilizar?

- chmod ✅
    
- ls -l
    
- ls -la
    
- head
    

**Correcto**  
Si desea cambiar los permisos de un archivo `approved_users.txt`, puede utilizar **chmod**.  
El comando `chmod` cambia los permisos de archivos y directorios.

---
