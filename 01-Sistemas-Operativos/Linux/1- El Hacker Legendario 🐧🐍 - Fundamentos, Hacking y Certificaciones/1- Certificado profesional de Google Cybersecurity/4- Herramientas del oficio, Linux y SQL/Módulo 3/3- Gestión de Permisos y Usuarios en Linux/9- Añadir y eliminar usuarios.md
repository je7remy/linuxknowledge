
## **Gestión de usuarios en Linux: Añadir y eliminar usuarios**

### **1. Autenticación y gestión de accesos**

- **Autenticación**: Proceso por el cual un usuario demuestra que es quien dice ser en el sistema.
    
- No todos los usuarios deben tener acceso; solo quienes lo requieran.
    
- Agregar usuarios:
    
    - Puede deberse a nuevas contrataciones, cambios organizacionales o reubicaciones internas.
        
- Eliminar usuarios:
    
    - Cuando abandonan la organización o cambian de grupo, deben eliminarse del sistema y de los grupos correspondientes.
        

---

### **2. Usuario root (superusuario)**

- **Privilegios**: Puede crear, modificar o eliminar cualquier archivo, y ejecutar cualquier programa.
    
- **Riesgos de iniciar sesión como root**:
    
    1. **Seguridad**: Es un objetivo frecuente para atacantes; se recomienda deshabilitar inicios de sesión directos.
        
    2. **Errores irreversibles**: Un comando mal ejecutado puede eliminar datos permanentemente.
        
    3. **Rendición de cuentas**: No hay trazabilidad de acciones si se comparte la cuenta root.
        

---

### **3. Uso de `sudo` como alternativa**

- `sudo` (super-user do) otorga permisos elevados temporalmente a usuarios específicos.
    
- Ventajas:
    
    - Control más granular que root.
        
    - Solicita la contraseña del usuario actual.
        
    - Requiere configuración en el archivo **sudoers** para otorgar permisos.
        

---

### **4. Añadir un usuario**

- Comando:
    

```bash
sudo useradd <nombre_usuario>
```

- Ejemplo:
    

```bash
sudo useradd salesrep7
```

- Características:
    
    - Solo usuarios root o con privilegios sudo pueden ejecutarlo.
        
    - Si no hay mensaje de error, el comando se ejecutó correctamente.
        

---

### **5. Eliminar un usuario**

- Comando:
    

```bash
sudo userdel <nombre_usuario>
```

- Ejemplo:
    

```bash
sudo userdel salesrep7
```

- Requisitos:
    
    - Privilegios root o sudo.
        
    - Sin mensajes de error → comando ejecutado con éxito.
        

---

### **6. Buenas prácticas**

- Usar privilegios elevados solo cuando sea estrictamente necesario.
    
- Asegurar que los usuarios tengan los permisos mínimos para cumplir sus funciones (principio de privilegio mínimo).
    
- Mantener actualizado el control de accesos para prevenir riesgos de seguridad.
    

---
