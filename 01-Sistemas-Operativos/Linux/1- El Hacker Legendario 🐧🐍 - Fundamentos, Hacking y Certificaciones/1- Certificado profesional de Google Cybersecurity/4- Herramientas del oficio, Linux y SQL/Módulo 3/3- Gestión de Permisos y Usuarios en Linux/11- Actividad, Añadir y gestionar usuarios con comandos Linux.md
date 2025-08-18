
### **Tarea 1: Agregar un usuario nuevo**

```bash
sudo useradd researcher9
sudo usermod -g research_team researcher9
```

- Crea al usuario `researcher9`.
    
- Establece `research_team` como su grupo primario.
    

---

### **Tarea 2: Asignar la propiedad del archivo**

```bash
sudo chown researcher9 /home/researcher2/projects/project_r.txt
```

- Cambia el propietario de `project_r.txt` a `researcher9`.
    

---

### **Tarea 3: Agregar al usuario a un grupo secundario**

```bash
sudo usermod -a -G sales_team researcher9
```

- Agrega a `researcher9` al grupo `sales_team` como grupo secundario.
    
- Mantiene `research_team` como grupo primario.
    

---

### **Tarea 4: Borrar un usuario**

```bash
sudo userdel researcher9
sudo groupdel researcher9
```

- Elimina al usuario `researcher9`.
    
- Borra el grupo vacío creado automáticamente con el mismo nombre.
    

---

✅ **Conclusión:**  
Ahora sabes cómo:

- Agregar usuarios y asignar grupos primarios y secundarios.
    
- Cambiar la propiedad de archivos a un usuario.
    
- Eliminar usuarios y grupos vacíos.
    

# **Repaso: Administración de usuarios en Linux**

**Comandos esenciales y tareas clave:**

1. **Agregar un usuario y asignar grupo primario**
    

```bash
sudo useradd researcher9
sudo usermod -g research_team researcher9
```

- Crea el usuario y establece su grupo principal.
    

2. **Asignar propiedad de un archivo**
    

```bash
sudo chown researcher9 /home/researcher2/projects/project_r.txt
```

- Cambia el propietario de un archivo al usuario.
    

3. **Agregar usuario a un grupo secundario**
    

```bash
sudo usermod -a -G sales_team researcher9
```

- Mantiene el grupo primario y añade un grupo adicional.
    

4. **Eliminar usuario y limpiar grupo**
    

```bash
sudo userdel researcher9
sudo groupdel researcher9
```

- Borra al usuario y su grupo vacío creado automáticamente.
    

> Todos los comandos requieren `sudo` para permisos de administrador.

Esto resume lo más importante del lab.


# **Repaso: Añadir y gestionar usuarios en Linux**

**Conceptos clave:**

- **Autenticación:** proceso por el cual un usuario demuestra que es quien dice ser.
    
- **Autorización:** acceso a recursos específicos según roles y permisos.
    
- No todos los usuarios deben tener acceso al sistema; los nuevos se agregan y los que cambian de rol o salen, se eliminan.
    
- Comandos principales: `useradd`, `usermod`, `userdel`, `chown`.
    
- Todos requieren `sudo` para permisos de administrador.
    

---

**Tareas y comandos esenciales:**

1. **Agregar un nuevo usuario y asignar grupo primario**
    

```bash
sudo useradd researcher9
sudo usermod -g research_team researcher9
```

- Alternativa combinada:
    

```bash
sudo useradd researcher9 -g research_team
```

2. **Asignar propiedad de un archivo**
    

```bash
sudo chown researcher9 /home/researcher2/projects/project_r.txt
```

3. **Agregar usuario a un grupo secundario**
    

```bash
sudo usermod -a -G sales_team researcher9
```

- Mantiene el grupo primario y añade el grupo adicional.
    

4. **Eliminar usuario y limpiar grupo vacío**
    

```bash
sudo userdel researcher9
sudo groupdel researcher9
```

---

**Resumen:**  
Con estos comandos puedes:

- Añadir usuarios y asignar grupos.
    
- Cambiar la propiedad de archivos.
    
- Agregar usuarios a grupos secundarios.
    
- Eliminar usuarios y limpiar grupos no usados.
    

Esto resume lo más importante para administrar usuarios en Linux.