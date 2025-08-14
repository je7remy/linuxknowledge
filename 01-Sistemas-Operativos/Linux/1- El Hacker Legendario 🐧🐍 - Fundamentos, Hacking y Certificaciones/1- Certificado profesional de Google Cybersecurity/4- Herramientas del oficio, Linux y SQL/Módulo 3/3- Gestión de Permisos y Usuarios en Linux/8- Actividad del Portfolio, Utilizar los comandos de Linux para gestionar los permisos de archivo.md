

## **Permisos de archivos en Linux**

### **Descripción del Proyecto**

Como profesional de ciberseguridad en una organización grande, trabajé con el equipo de investigación para verificar y ajustar los permisos de archivos y directorios dentro del directorio `projects`. El objetivo fue asegurar que solo los usuarios autorizados tuvieran los permisos correctos y eliminar cualquier acceso no autorizado. Utilicé comandos de Linux para inspeccionar los permisos actuales y luego los modifiqué para cumplir con las políticas de seguridad de la organización.

---

### **Comprobar detalles de archivos y directorios**

Para revisar los permisos actuales, utilicé el comando:

```bash
ls -la /home/researcher2/projects
```

Este comando lista todos los archivos, incluidos los ocultos, en formato detallado.

**Salida observada (resumen):**

- `project_k.txt` → Usuario: rw, Grupo: rw, Otros: rw
    
- `project_m.txt` → Usuario: rw, Grupo: r, Otros: ninguno
    
- `project_r.txt` → Usuario: rw, Grupo: rw, Otros: r
    
- `project_t.txt` → Usuario: rw, Grupo: rw, Otros: r
    
- `.project_x.txt` (oculto) → Usuario: rw, Grupo: w, Otros: ninguno
    
- Directorio `drafts` → Usuario: rwx, Grupo: x, Otros: ninguno
    

---

### **Describir la cadena de permisos**

Ejemplo: `-rw-rw-r--` para `project_t.txt`

- **1er carácter (`-`)**: Es un archivo regular.
    
- **2-4 (`rw-`)**: Usuario tiene lectura y escritura, sin ejecución.
    
- **5-7 (`rw-`)**: Grupo tiene lectura y escritura, sin ejecución.
    
- **8-10 (`r--`)**: Otros tienen solo lectura.
    

---

### **Cambiar permisos de un archivo**

La política de la organización no permite que “otros” tengan permisos de escritura en ningún archivo.  
`project_k.txt` tenía permisos de escritura para “otros”, así que ejecuté:

```bash
chmod o-w project_k.txt
```

Verifiqué con:

```bash
ls -la
```

Confirmé que el permiso `w` se eliminó de la sección de “otros”.

---

### **Cambiar permisos de un archivo oculto**

`.project_x.txt` debía quedar sin permisos de escritura para nadie, pero usuario y grupo con permiso de lectura.  
Comandos ejecutados:

```bash
chmod u-w .project_x.txt   # Quitar escritura al usuario  
chmod g-w .project_x.txt   # Quitar escritura al grupo  
chmod g+r .project_x.txt   # Asegurar lectura para el grupo  
```

Resultado: Usuario y grupo con solo lectura, otros sin acceso.

---

### **Cambiar permisos de un directorio**

Solo `researcher2` debía tener acceso al directorio `drafts`.  
Comandos ejecutados:

```bash
chmod g-x drafts   # Quitar ejecución al grupo  
chmod o-x drafts   # Quitar ejecución a otros  
```

Verificación con `ls -la` mostró que solo el usuario `researcher2` mantiene permisos de ejecución.

---

### **Resumen**

Se verificaron los permisos de los archivos y directorios del directorio `projects` con `ls -la`, interpretando las cadenas de 10 caracteres para entender su configuración. Se modificaron los permisos usando `chmod` para:

- Eliminar escritura a “otros” en `project_k.txt`.
    
- Configurar `.project_x.txt` como lectura para usuario y grupo, sin escritura para nadie.
    
- Limitar el acceso a `drafts` solo al usuario `researcher2`.
    

Estos cambios aseguran que el sistema cumpla con las políticas de seguridad y que solo los usuarios autorizados tengan el acceso correspondiente.

---
