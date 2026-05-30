---
tipo: laboratorio
tags: [ejptv2, el-hacker-legendario, linux, bash]
actualizado: 2026-05-28
---

# Automatizar la Gestión de Usuarios en Linux

---

#Linux #Bash #ShellScripting #SysAdmin #Automatización #ComandosLinux #AdministraciónLinux #SeguridadInformática #DevOps #Scripting #IT #HackingÉtico #GNU #UsuariosLinux

---

### **Parte 1: Comandos Iniciales**

#### **1️⃣ Comando `su jeremy`**

📌 **Significado:**  
El comando `su` (substitute user) permite cambiar a otro usuario en el sistema Linux. En este caso, intentamos cambiar al usuario `jeremy`.

📌 **Ejecución en la terminal:**

```bash
su jeremy
```

📌 **Posibles resultados:**  
✅ **Si tienes permisos y la contraseña de `jeremy` es correcta:**

```bash
jeremy@hostname:~$
```

(La línea de comandos cambia para reflejar que ahora estás en la sesión de `jeremy`.)

❌ **Si introduces una contraseña incorrecta:**

```bash
Password:
su: Authentication failure
```

(Tendrás que volver a intentarlo con la contraseña correcta.)

---

#### **2️⃣ Comando `exit`**

📌 **Significado:**  
Este comando cierra la sesión actual y regresa al usuario anterior.

📌 **Ejecución en la terminal:**

```bash
exit
```

📌 **Resultado:**  
Si estabas en `jeremy`, regresarás al usuario anterior:

```bash
logout
usuario_anterior@hostname:~$
```

---

#### **3️⃣ Comando `cd /home`**

📌 **Significado:**  
`cd` (change directory) cambia el directorio actual. En este caso, vamos a `/home`, donde se almacenan los directorios de los usuarios.

📌 **Ejecución en la terminal:**

```bash
cd /home
```

📌 **Resultado:**  
Si ejecutas `pwd` (print working directory) después, verás:

```bash
/home
```

Significa que ahora estamos en el directorio `/home`.

---

### **Parte 2: Explicación del Código Bash**

#### 📜 **Definición de funciones**

El script define tres funciones:

1️⃣ **`create_user()`**  
📌 **Objetivo:**

- Solicita un nombre de usuario.
- Usa `sudo adduser` para crearlo.
- Muestra un mensaje de confirmación.

📌 **Código explicado línea por línea:**

```bash
create_user() {
    read -p "Ingresa el nombre del nuevo usuario: " username  # Solicita el nombre del usuario
    sudo adduser "$username"  # Crea el usuario con permisos root
    echo "Usuario $username creado correctamente"  # Mensaje de confirmación
}
```

📌 **Ejemplo en la terminal:**

```bash
Seleccione una opción (1/2/3): 1
Ingresa el nombre del nuevo usuario: juanito
Adding user `juanito' ...
Adding new group `juanito' (1001) ...
Adding new user `juanito' (1001) with group `juanito' ...
Creating home directory `/home/juanito' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for juanito
Enter the new value, or press ENTER for the default
	Full Name []:
	Room Number []:
	Work Phone []:
	Home Phone []:
	Other []:
Is the information correct? [Y/n] Y
Usuario juanito creado correctamente
```

---

2️⃣ **`delete_user()`**  
📌 **Objetivo:**

- Solicita un nombre de usuario.
- Usa `sudo deluser --remove-home` para eliminarlo.
- Muestra un mensaje de confirmación.

📌 **Código explicado línea por línea:**

```bash
delete_user() {
    read -p "Ingrese el nombre de usuario que quieras borrar: " username  # Solicita el usuario a eliminar
    sudo deluser --remove-home "$username"  # Elimina el usuario y su directorio home
    echo "Usuario $username ha sido eliminado correctamente"  # Mensaje de confirmación
}
```

📌 **Ejemplo en la terminal:**

```bash
Seleccione una opción (1/2/3): 2
Ingrese el nombre de usuario que quieras borrar: juanito
Looking for files to backup/remove ...
Removing user `juanito' ...
Warning: group `juanito' has no more members.
Done.
Usuario juanito ha sido eliminado correctamente
```

---

3️⃣ **`control_c()`**  
📌 **Objetivo:**

- Manejar la señal `SIGINT` (`Ctrl+C`) para salir del script con un mensaje.

📌 **Código explicado línea por línea:**

```bash
function control_c {
    echo " Saliendo del script"  # Mensaje de salida
    exit 1  # Termina el script con código de error 1
}
```

📌 **Ejemplo en la terminal:**  
Si presionas `Ctrl+C`:

```bash
Saliendo del script
```

---

### **Parte 3: Captura de la Señal SIGINT (`trap`)**

```bash
trap control_c SIGINT
```

📌 **Significado:**

- Captura la señal `SIGINT` cuando el usuario presiona `Ctrl+C`.
- En lugar de cerrar el script abruptamente, ejecuta la función `control_c()`.

📌 **Ejemplo en la terminal:**  
Si intentas detener el script con `Ctrl+C`, verás:

```bash
Saliendo del script
```

---

### **Parte 4: Menú Interactivo con `while true`**

📌 **Código explicado línea por línea:**

```bash
while true; do  # Bucle infinito hasta que el usuario elija salir
    echo -e "\n1- Crear nuevo usuario"
    echo -e "2- Eliminar el usuario"
    echo -e "3- Salir \n"
    read -p "Seleccione una opción (1/2/3): " eleccion
```

- Muestra el menú en cada iteración.
- Espera la entrada del usuario con `read`.

📌 **Estructura `case` para manejar opciones:**

```bash
    case $eleccion in
        1)
            create_user  # Llama a la función para crear usuario
            ;;
        2)
            delete_user  # Llama a la función para eliminar usuario
            ;;
        3)
            control_c  # Llama a la función para salir
            ;;
        *)
            echo "Opción no válida. Inserte un dígito válido (1/2/3)"
            ;;
    esac
done
```

- Si el usuario ingresa `1`, crea un usuario.
- Si ingresa `2`, elimina un usuario.
- Si ingresa `3`, sale del script.
- Si ingresa un número inválido, muestra un mensaje de error.

📌 **Ejemplo en la terminal:**

```bash
1- Crear nuevo usuario
2- Eliminar el usuario
3- Salir

Seleccione una opción (1/2/3): 4
Opción no válida. Inserte un dígito válido (1/2/3)
```

---

### **Parte 5: Código Completo**

```bash
#!/bin/bash

create_user() {
    read -p "Ingresa el nombre del nuevo usuario: " username
    sudo adduser "$username"
    echo "Usuario $username creado correctamente"
}

delete_user() {
    read -p "Ingrese el nombre de usuario que quieras borrar: " username
    sudo deluser --remove-home "$username"
    echo "Usuario $username ha sido eliminado correctamente"
}

function control_c {
    echo " Saliendo del script"
    exit 1
}

trap control_c SIGINT

while true; do
    echo -e "\n1- Crear nuevo usuario"
    echo -e "2- Eliminar el usuario"
    echo -e "3- Salir \n"
    read -p "Seleccione una opción (1/2/3): " eleccion

    case $eleccion in
        1) create_user ;;
        2) delete_user ;;
        3) control_c ;;
        *) echo "Opción no válida. Inserte un dígito válido (1/2/3)" ;;
    esac
done
```

**Flujo:**
1. Configura la trampa para Ctrl + C
2. Bucle infinito con menú:
   - Opción 1: Ejecuta create_user()
   - Opción 2: Ejecuta delete_user()
   - Opción 3: Llama a control_c() (cierra el script)
   - Otras opciones: Mensaje de error

---

**Posibles problemas detectados:**
1. El script no verifica si el usuario ya existe al crear
2. `deluser --remove-home` es específico de Debian/Ubuntu. En otros sistemas se usaría `userdel -r`
3. La opción 3 sale con código de error 1 (lo estándar sería 0 para salida exitosa)
4. No hay validación de entradas (ej. nombres de usuario con espacios)
5. El typo en `elecion` hará que siempre caiga en "*Opción no válida*" a menos que el usuario escriba mal la opción

Este script es un menú interactivo básico para gestión de usuarios, pero necesitaría mejoras para uso en producción.

**[[6- Gestión de Usuarios en Linux]]**
**[[2- Gestión de Grupos]]**
**[[1- Protección del Protocolo SSH]]** 
[[7- Automatización de Copias de Seguridad en Servidor SSH]]
[[6- Acceso Automatizado SSH Importando Clave Pública]]

---

## Navegación

- ⬆️ Carpeta: [[_9- Ejercicios Prácticos|9- Ejercicios Prácticos]]
- ⬅️ Anterior: [[10- Detector de Sistemas Operativos – PARTE 2]]
- ➡️ Siguiente: [[12- Herramienta para hacer cracking de contraseñas]]
