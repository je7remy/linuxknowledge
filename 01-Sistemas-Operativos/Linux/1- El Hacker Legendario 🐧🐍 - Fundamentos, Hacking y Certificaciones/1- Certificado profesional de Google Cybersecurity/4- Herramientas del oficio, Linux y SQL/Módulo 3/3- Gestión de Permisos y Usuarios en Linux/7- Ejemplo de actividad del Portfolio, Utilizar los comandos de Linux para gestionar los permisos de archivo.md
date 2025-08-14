
## **Permisos de Archivos en Linux**

### **Descripción del Proyecto**

El equipo de investigación de mi organización necesitaba actualizar los permisos de ciertos archivos y directorios dentro del directorio `projects`. Los permisos actuales no coincidían con los niveles de autorización requeridos. Revisar y actualizar estos permisos era esencial para mantener la seguridad del sistema.

---

### **1. Verificar Detalles de Archivos y Directorios**

Comencé revisando los permisos actuales del directorio y su contenido.

**Comando Utilizado:**

```bash
ls -la projects
```

**Explicación:**

- `ls -la` lista todos los archivos, incluyendo los ocultos, en formato detallado.
    
- El resultado mostró:
    
    - **1 directorio**: `drafts`
        
    - **1 archivo oculto**: `.project_x.txt`
        
    - **5 archivos regulares**
        
- Cada entrada incluye una **cadena de 10 caracteres** que representa los permisos.
    

**Desglose de la Cadena de Permisos:**

1. **1er carácter**: Tipo de archivo (`d` = directorio, `-` = archivo regular)
    
2. **2do–4to**: Permisos del usuario (lectura `r`, escritura `w`, ejecución `x`)
    
3. **5to–7mo**: Permisos del grupo
    
4. **8vo–10mo**: Permisos de otros usuarios
    

**Ejemplo:**  
`-rw-rw-r--` para `project_t.txt` significa:

- **`-`** → archivo regular
    
- **Usuario**: lectura, escritura
    
- **Grupo**: lectura, escritura
    
- **Otros**: solo lectura
    

---

### **2. Quitar Permisos de Escritura a "Otros"**

**Requisito:** Los demás usuarios no deben tener acceso de escritura a ningún archivo.

**Archivo Objetivo:** `project_k.txt`

**Comando:**

```bash
chmod o-w project_k.txt
```

**Verificación:**

```bash
ls -la
```

Se confirmó que se eliminó `w` para "otros".

---

### **3. Actualizar Permisos de un Archivo Oculto**

**Requisito:** `.project_x.txt` debe ser de solo lectura para usuario y grupo, sin permisos de escritura para nadie.

**Comandos:**

```bash
chmod u-w .project_x.txt   # Quitar escritura al usuario  
chmod g-w .project_x.txt   # Quitar escritura al grupo  
chmod g+r .project_x.txt   # Asegurar que el grupo tenga lectura  
```

---

### **4. Restringir Acceso a un Directorio**

**Requisito:** Solo el usuario `researcher2` debe tener permisos de ejecución en `drafts` y su contenido.

**Comando:**

```bash
chmod g-x drafts   # Quitar ejecución al grupo  
chmod o-x drafts   # Quitar ejecución a otros (si aplica)  
```

---

### **Resumen**

- **Se verificaron los permisos** con `ls -la`.
    
- **Se modificaron los permisos** con `chmod` para cumplir la política de seguridad.
    
- Los cambios garantizaron:
    
    - Ningún archivo con acceso de escritura para "otros".
        
    - `.project_x.txt` de solo lectura para usuario y grupo.
        
    - Solo `researcher2` con acceso al directorio `drafts`.
        

---

