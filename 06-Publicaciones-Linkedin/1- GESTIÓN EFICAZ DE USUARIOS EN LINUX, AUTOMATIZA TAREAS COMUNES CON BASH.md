
## 🖥️ **GUÍA GESTIÓN DE USUARIOS EN LINUX**

### **Introducción**

La gestión de usuarios es una de las tareas fundamentales en la administración de sistemas y la ciberseguridad. Con Bash, podemos automatizar estas tareas de forma eficiente, asegurando que el proceso sea rápido, seguro y sin errores humanos. Esta guía te llevará paso a paso en la creación, modificación y eliminación de usuarios en Linux, utilizando un script Bash. También se explicarán algunos comandos básicos que son esenciales para interactuar con usuarios en el sistema.

---

### **Parte 1: Script Bash para Gestión de Usuarios**

El siguiente script permite realizar las acciones básicas de gestión de usuarios: **crear**, **modificar** y **eliminar** usuarios. Además, es interactivo, lo que facilita su uso en diferentes escenarios.

#### **Script para la Gestión de Usuarios:**

```bash
#!/bin/bash

# Definir colores para mensajes
ROJO="\e[31m"
VERDE="\e[32m"
RESET="\e[0m"

# Verifica que el usuario tenga permisos de sudo
if ! sudo -v &>/dev/null; then
    echo -e "${ROJO}Este script requiere permisos de sudo.${RESET}"
    exit 1
fi

# Verificar si el script tiene permisos para escribir en /var/log
if ! touch /var/log/user_management.log &>/dev/null; then
    echo -e "${ROJO}No se tiene permiso para escribir en /var/log/user_management.log.${RESET}"
    exit 1
fi

# Función para registrar las acciones en el log
log_action() {
    local action=$1
    local user=$2
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $action: $user" >> /var/log/user_management.log
}

# Función para validar el nombre de usuario
validate_username() {
    local username=$1
    if [[ ! "$username" =~ ^[a-zA-Z0-9_-]+$ ]]; then
        echo -e "${ROJO}El nombre de usuario '$username' no es válido. Solo se permiten letras, números, guiones y guiones bajos.${RESET}"
        return 1
    fi
    return 0
}

# Función para crear un usuario sin prompts
create_user() {
    if ! validate_username "$username"; then
        return 1
    fi

    # Verificar si el usuario ya existe
    if id "$username" &>/dev/null; then
        echo -e "${ROJO}El usuario $username ya existe.${RESET}"
        return 1
    fi

    if [ "$test_mode" -eq 1 ]; then
        echo "Simulando creación de usuario: $username"
    else
        sudo adduser --disabled-password --gecos "" "$username"
        if [ $? -eq 0 ]; then
            echo -e "${VERDE}Usuario $username creado correctamente.${RESET}"
            log_action "Crear usuario" "$username"
        else
            echo -e "${ROJO}Error al crear el usuario $username.${RESET}"
        fi
    fi
}

# Función para modificar un usuario (agregar a sudo)
modify_user() {
    if ! validate_username "$username"; then
        return 1
    fi

    if [ "$test_mode" -eq 1 ]; then
        echo "Simulando modificación de usuario: $username (agregar a sudo)"
    else
        sudo usermod -aG sudo "$username"
        if [ $? -eq 0 ]; then
            echo -e "${VERDE}Usuario $username modificado correctamente (agregado a sudo).${RESET}"
            log_action "Modificar usuario" "$username"
        else
            echo -e "${ROJO}Error al modificar el usuario $username.${RESET}"
        fi
    fi
}

# Función para eliminar un usuario con confirmación
delete_user() {
    if ! validate_username "$username"; then
        return 1
    fi

    # Confirmación antes de eliminar
    read -p "¿Estás seguro de que deseas eliminar al usuario $username? (s/n): " confirm
    if [[ ! "$confirm" =~ ^[sS]$ ]]; then
        echo -e "${ROJO}Cancelado. No se eliminará el usuario $username.${RESET}"
        return 1
    fi

    if [ "$test_mode" -eq 1 ]; then
        echo "Simulando eliminación de usuario: $username"
    else
        sudo deluser --remove-home "$username"
        if [ $? -eq 0 ]; then
            echo -e "${VERDE}Usuario $username eliminado correctamente.${RESET}"
            log_action "Eliminar usuario" "$username"
        else
            echo -e "${ROJO}Error al eliminar el usuario $username.${RESET}"
        fi
    fi
}

# Manejo de Ctrl+C (salir limpiamente)
function control_c {
    echo -e "\nSaliendo del script..."
    exit 1
}

# Captura la señal SIGINT (Ctrl+C)
trap control_c SIGINT

# Modo de prueba (simulación sin ejecutar cambios)
test_mode=0
if [[ "$1" == "-t" || "$1" == "--test" ]]; then
    test_mode=1
    echo -e "${VERDE}Modo de prueba activado: Las acciones no se ejecutarán.${RESET}"
fi

# Menú interactivo
while true; do
    echo -e "\n1- Crear un nuevo usuario"
    echo -e "2- Modificar un usuario (agregar a sudo)"
    echo -e "3- Eliminar un usuario"
    echo -e "4- Salir\n"
    
    read -p "Seleccione una opción (1/2/3/4): " opcion

    case $opcion in
        1) 
            read -p "Ingrese el nombre del nuevo usuario: " username
            create_user
            ;;
        2) 
            read -p "Ingrese el nombre del usuario a modificar: " username
            modify_user
            ;;
        3) 
            read -p "Ingrese el nombre del usuario a eliminar: " username
            delete_user
            ;;
        4) 
            control_c
            ;;
        *)
            echo -e "${ROJO}Opción no válida. Selecciona un número entre 1 y 4.${RESET}"
            ;;
    esac
done
```

#### **Pasos para usar el script:**

1. **Guarda el script** como `manage_users.sh`.
    
2. **Dale permisos de ejecución**:
    
    ```bash
    chmod +x manage_users.sh
    ```
    
3. **Ejecuta el script**:
    
    ```bash
    ./manage_users.sh crear nuevo_usuario
    ```
    

#### **Opciones de uso del menú**:

- **Crear un usuario**:
    
    ```bash
    ./manage_users.sh crear usuario1
    ```
    
- **Modificar un usuario** (agregar a sudo):
    
    ```bash
    ./manage_users.sh modificar usuario1
    ```
    
- **Eliminar un usuario**:
    
    ```bash
    ./manage_users.sh eliminar usuario1
    ```
    

#### **Consejos adicionales**:

- **Registro de acciones**: Para hacer un seguimiento de las acciones realizadas, puedes añadir un archivo de log en el script:
    
    ```bash
    echo "Acción: $ACCION - Usuario: $USUARIO" >> log.txt
    ```
    
- **Seguridad**: Asegúrate de proteger el script. Limita el acceso solo a administradores con:
    
    ```bash
    chmod 700 manage_users.sh
    ```
    

---

### **Parte 2: Comandos Básicos para Gestionar Usuarios**

Además de usar scripts, es importante conocer algunos de los comandos fundamentales que puedes ejecutar en la terminal para gestionar usuarios de manera directa.

#### **1️⃣ Comando `su jeremy`**

- **Significado**: Cambia la sesión al usuario `jeremy`.
    
- **Ejecución**:
    
    ```bash
    su jeremy
    ```
    
- **Posibles resultados**:
    
    - **Si tienes permisos y la contraseña es correcta**:
        
        ```bash
        jeremy@hostname:~$
        ```
        
    - **Si la contraseña es incorrecta**:
        
        ```bash
        Password:
        su: Authentication failure
        ```
        

#### **2️⃣ Comando `exit`**

- **Significado**: Cierra la sesión actual y regresa al usuario anterior.
    
- **Ejecución**:
    
    ```bash
    exit
    ```
    
- **Resultado**:
    
    ```bash
    logout
    usuario_anterior@hostname:~$
    ```
    

#### **3️⃣ Comando `cd /home`**

- **Significado**: Cambia al directorio `/home`, donde se almacenan los directorios de los usuarios.
    
- **Ejecución**:
    
    ```bash
    cd /home
    ```
    
- **Resultado**: Al ejecutar `pwd` (print working directory), se mostrará:
    
    ```bash
    /home
    ```
    

---

### **Parte 3: Explicación del Código del Script**

El script está diseñado para ser fácil de usar y para realizar tres tareas fundamentales de gestión de usuarios. Aquí se explica cada una de las funciones y su propósito.

#### **Funciones del Script:**

1. **`create_user()`**:
    
    - **Objetivo**: Crea un nuevo usuario, verificando primero si ya existe.
        
    - **Explicación**:
        
        - Utiliza el comando `adduser` para crear el usuario.
            
        - Verifica si el usuario ya existe con `id "$username"`.
            
2. **`modify_user()`**:
    
    - **Objetivo**: Modifica un usuario, agregándolo al grupo `sudo` para otorgarle privilegios de administrador.
        
    - **Explicación**: Utiliza `usermod -aG sudo` para agregar el usuario al grupo de sudoers.
        
3. **`delete_user()`**:
    
    - **Objetivo**: Elimina un usuario y su directorio home.
        
    - **Explicación**: Usa `deluser --remove-home` para eliminar tanto al usuario como su directorio.
        
4. **`control_c()`**:
    
    - **Objetivo**: Maneja la interrupción del script con `Ctrl+C`, garantizando una salida limpia del script.
        

#### **Menú Interactivo**:

El script utiliza un bucle `while true` para mostrar un menú de opciones y espera la entrada del usuario. Dependiendo de la opción seleccionada, ejecuta una de las funciones anteriores.

---

### **Parte 4: Consideraciones de Seguridad y Buenas Prácticas**

1. **Protege el script**: Usa permisos restringidos para evitar que otros usuarios modifiquen o ejecuten el script:
    
    ```bash
    chmod 700 manage_users.sh
    ```
    
2. **Uso de `sudo`**: Asegúrate de que el usuario que ejecuta el script tenga los permisos adecuados en el archivo `/etc/sudoers`.
    
3. **Verificación de entrada**: Es recomendable añadir más validaciones, como asegurarse de que los nombres de usuario no contengan caracteres especiales o espacios.
    

---

### **Conclusión**

Este script y los comandos básicos proporcionan una forma eficiente y segura de gestionar usuarios en sistemas Linux. Al automatizar estas tareas, puedes reducir errores y ahorrar tiempo, especialmente en entornos de producción o cuando manejas múltiples usuarios. Además, al seguir las mejores prácticas de seguridad, garantizas que las operaciones se realicen de manera controlada y sin comprometer la integridad del sistema.

