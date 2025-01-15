El **Sticky Bit** es un permiso especial que se aplica a directorios en sistemas tipo Unix/Linux. Cuando se activa, asegura que solo el propietario de un archivo dentro del directorio (o el usuario root) pueda eliminar o modificar ese archivo, incluso si otros usuarios tienen permisos de escritura en el directorio.

---

### **Definición del Sticky Bit**

1. **Uso principal**:
    
    - Es común en directorios como `/tmp`, donde varios usuarios tienen permisos para crear y editar archivos, pero no deberían poder eliminar o modificar archivos de otros.
2. **Configuración**:
    
    - Se activa usando el comando `chmod +t` sobre un directorio.
3. **Indicador**:
    
    - Cuando está activo, en la salida de `ls -l`, aparece una `t` en el lugar de los permisos de ejecución del grupo "otros" (others).

---

### **Ejemplo práctico: Sticky Bit**

#### **Paso 1: Crear un directorio compartido**

```bash
sudo mkdir /carpeta_compartida
```

#### **Paso 2: Asignar permisos para que sea accesible a todos**

```bash
sudo chmod 777 /carpeta_compartida
```

Esto permitirá que todos los usuarios puedan leer, escribir y ejecutar en este directorio.

#### **Paso 3: Activar el Sticky Bit**

```bash
sudo chmod +t /carpeta_compartida
```

#### **Paso 4: Verificar el Sticky Bit**

Usa el comando `ls -ld` para verificar los permisos:

```bash
ls -ld /carpeta_compartida
```

La salida será algo similar a:

```
drwxrwxrwt 2 root root 4096 Jan 15 12:00 /carpeta_compartida
```

El carácter `t` en lugar de `x` al final indica que el Sticky Bit está activado.

---

### **Ejemplo funcional**

1. **Creación de archivos por diferentes usuarios**: Supongamos que hay dos usuarios, `user1` y `user2`.
    
    - `user1` crea un archivo:
        
        ```bash
        su user1
        touch /carpeta_compartida/archivo_user1
        ```
        
    - `user2` intenta eliminar el archivo de `user1`:
        
        ```bash
        su user2
        rm /carpeta_compartida/archivo_user1
        ```
        
        Resultado: **No podrá eliminarlo** debido al Sticky Bit.
        
2. **Solo el propietario del archivo o el administrador (root)** podrá eliminarlo.
    

---

### **Sin el Sticky Bit**

Si el Sticky Bit no estuviera activado, cualquier usuario con permisos de escritura en el directorio podría eliminar o modificar archivos de otros usuarios, lo cual puede ser riesgoso en entornos compartidos.

