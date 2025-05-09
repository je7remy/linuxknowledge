
---

#Linux #SysAdmin #Bash #ShellScripting #AdministraciónLinux #PermisosLinux #UsuariosLinux #SeguridadInformática #DevOps #IT #ComandosLinux #HackingÉtico #GNU #GestiónDeGrupos

---

Analicemos paso a paso lo que ocurrió en el flujo de comandos y los posibles problemas que llevaron a la situación actual:

---

### **1. Creación del grupo "profesores"**

```bash
sudo addgroup profesores
```

- Se creó un grupo llamado **profesores**.

---

### **2. Verificación de grupos existentes**

```bash
getent group
```

- Se listaron los grupos del sistema, incluyendo **profesores** si la creación fue exitosa.

---

### **3. Creación del usuario "spider"**

```bash
sudo adduser spider
```

- Se creó un usuario llamado **spider**.

---

### **4. Verificación del archivo `/etc/passwd`**

```bash
cat /etc/passwd
```

- Se revisó la lista de usuarios para confirmar la creación de **spider**.

---

### **5. Adición de usuarios al grupo "profesores"**

```bash
sudo usermod -aG profesores spider
sudo usermod -aG profesores raton
```

- **spider** y **raton** fueron añadidos al grupo **profesores**.
- **Nota:** Estos usuarios deben cerrar y volver a iniciar sesión para que la pertenencia al grupo sea efectiva.

---

### **6. Verificación del grupo "profesores"**

```bash
getent group profesores
```

- Se confirmó que **spider** y **raton** son miembros del grupo.

---

### **7. Modificación de los permisos y propiedad de `examenes.txt`**

```bash
sudo chown kali:profesores examenes.txt
```

- El archivo **examenes.txt** cambió de propietario. Ahora el propietario es **kali**, y el grupo asociado es **profesores**.

```bash
sudo chmod g+w+x examenes.txt
```

- Se otorgaron permisos de escritura (`w`) y ejecución (`x`) al grupo **profesores**.

```bash
sudo chmod o-r examenes.txt
```

- Se eliminó el permiso de lectura (`r`) para **otros** (usuarios que no son propietarios ni miembros del grupo).

---

### **8. Intento de acceso al archivo como "nuevecaras"**

```bash
su nuevecaras
cat examenes.txt
```

- El usuario **nuevecaras** intentó leer el archivo, pero recibió el error `Permission denied`.
- **Razón:** **nuevecaras** no es miembro del grupo **profesores**, y no tiene permiso de lectura sobre el archivo.

---

### **9. Eliminación del grupo "profesores"**

```bash
sudo groupdel profesores
```

- Se eliminó el grupo **profesores** del sistema.

---


**[[11- Automatizar la Gestión de Usuarios en Linux]]**
**[[6- Gestión de Usuarios en Linux]]**
**[[1- Protección del Protocolo SSH]]**

