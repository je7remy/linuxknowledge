
---

#BitSUID #PermisosLinux #SeguridadLinux #AdministraciónDeSistemas #ComandosLinux #UnixSecurity #Comandochmod #SUID #PermisosElevados #SeguridadInformática #AuditoríaLinux #Linux #AccesoRoot #VulnerabilidadesLinux #RiesgosDeSeguridad #PrivilegiosElevados #LinuxTips #Comandofind #PermisosDeArchivos #AdministraciónDeArchivos

---
El **bit SUID (Set User ID)** es un permiso especial en sistemas Unix/Linux que permite que un archivo se ejecute con los privilegios del propietario del archivo en lugar de con los del usuario que lo ejecuta. Este mecanismo es especialmente útil para ejecutar programas que necesitan permisos elevados en tareas específicas, como cambiar contraseñas o realizar operaciones críticas en el sistema.

---

### **Funcionamiento del bit SUID**

1. **Permiso estándar**: Cuando un usuario ejecuta un archivo sin SUID, este se ejecuta con los privilegios de dicho usuario.
2. **Con SUID activado**: Si un archivo tiene el bit SUID habilitado, este se ejecutará con los privilegios del propietario del archivo, generalmente el superusuario (`root`).

---

### **Representación en Permisos**

El bit SUID se representa en el sistema de archivos de la siguiente manera en los permisos (modo octal `4000`):

- Sin SUID: `-rwxr-xr-x`
- Con SUID: `-rwsr-xr-x`  
    (Nota el cambio de `x` a `s` en el grupo del propietario).

Ejemplo práctico:  
`ls -l /usr/bin/passwd`  
Salida típica:  
`-rwsr-xr-x 1 root root 54232 Jan 15 2025 /usr/bin/passwd`

Aquí:

- El bit `s` en la posición del propietario indica que `passwd` tiene activado el bit SUID.
- Cuando un usuario cambia su contraseña con `passwd`, el comando se ejecuta con privilegios de `root`, lo que le permite modificar archivos del sistema como `/etc/shadow`.

---

### **Habilitación y Deshabilitación del bit SUID**

- **Habilitar SUID**:
    
    ```bash
    sudo chmod u+s archivo
    ```
    
- **Deshabilitar SUID**:
    
    ```bash
    sudo chmod u-s archivo
    ```
    

---

### **Uso Común del Bit SUID**

- **Programas críticos**: Herramientas como `passwd`, `ping`, y `sudo` necesitan permisos elevados para realizar tareas específicas.
- **Propósito controlado**: Permite acceso temporal a funcionalidades que requieren privilegios sin otorgar permisos de administrador permanentes al usuario.

---

### **Riesgos Asociados**

1. **Abusos y Exploits**: Si un archivo con SUID tiene vulnerabilidades, un atacante podría explotarlas para obtener acceso privilegiado.
2. **Errores de configuración**: Configurar SUID en binarios sensibles como `/bin/bash` podría dar acceso `root` a cualquier usuario.
3. **Auditoría necesaria**: Es fundamental monitorear archivos con SUID en un sistema para evitar configuraciones peligrosas.

---

### **Auditoría de Archivos con SUID**

Para listar archivos con SUID activado en el sistema:

```bash
find / -perm -4000 2>/dev/null
```

---

### **Buenas Prácticas**

- Limitar el uso de SUID a programas estrictamente necesarios.
- Monitorizar regularmente los archivos con SUID habilitado.
- Deshabilitar SUID en aplicaciones que no requieren privilegios elevados.

# Ejemplo Practico:

El bit SUID es una herramienta poderosa y debe usarse con responsabilidad para mantener un equilibrio entre funcionalidad y seguridad.

1. **`ls -l /bin/bash`**  
    Este comando lista los permisos y detalles del archivo `/bin/bash`. Normalmente, este archivo tiene el bit SUID desactivado, representado por `-rwxr-xr-x`. Esto significa que los usuarios pueden ejecutar el archivo, pero no con permisos elevados.
    
2. **`/bin/bash -p`**  
    Ejecuta `/bin/bash` con cualquier permiso heredado, como si el bit SUID estuviera activo. Sin embargo, si el bit SUID no está configurado, este comando simplemente se ejecutará con los permisos del usuario que lo ejecuta.
    
3. **`sudo chmod u+s /bin/bash`**  
    Este comando activa el bit SUID en `/bin/bash`. Al hacerlo, cualquier usuario que ejecute `/bin/bash` lo hará con los permisos del propietario del archivo, que en este caso es `root`. Esto cambia los permisos a algo como `-rwsr-xr-x`.
    
4. **`/bin/bash -p`**  
    Ahora, al ejecutar este comando, dado que el bit SUID está activado, el shell de Bash se inicia con privilegios de root. Esto permite al usuario ejecutar comandos como si fuera `root`.
    
5. **`bash-5.2# whoami`**  
    Aquí el comando `whoami` devuelve `root`, confirmando que efectivamente se han adquirido permisos de superusuario.
    
6. **`find / -perm -4000 2>/dev/null`**  
    Este comando busca en todo el sistema archivos que tengan el bit SUID activado (indicado por `-4000`). La redirección `2>/dev/null` oculta mensajes de error relacionados con permisos denegados.
    
7. **`find / -perm -4000 2>/dev/null | xargs ls -l`**  
    Encuentra los archivos con bit SUID activado y luego usa `ls -l` para mostrar sus detalles.
    
8. **`sudo chmod u-s /bin/bash`**  
    Este comando desactiva el bit SUID en `/bin/bash`, restaurando sus permisos normales. Ahora, al ejecutar `/bin/bash`, no se obtendrán privilegios elevados.
    
9. **`find / -perm -4000 2>/dev/null | xargs ls -l`**  
    Este comando se repite para verificar que el bit SUID de `/bin/bash` ha sido eliminado. El archivo `/bin/bash` debería aparecer ahora con permisos normales.
    

### **Conceptos Clave**

- **Bit SUID**: Permite que un archivo se ejecute con los permisos de su propietario en lugar del usuario que lo ejecuta. Es común en programas como `passwd`.
- **Riesgos**: Activar el bit SUID en un archivo como `/bin/bash` es muy peligroso. Permite a cualquier usuario obtener acceso como `root`, lo cual puede comprometer la seguridad del sistema.
- **Uso Ético**: Este tipo de modificaciones solo debe hacerse en entornos de prueba y con fines educativos o de auditoría bajo autorización.




[[8- Permisos Especiales – Sticky Bit]]
[[1- Gestión Básica, Detallada y con números de Permisos – Comando chmod]]
