### **Definición de `nohup`**

`nohup` significa "no hang up" y permite ejecutar un comando o script de manera que siga funcionando incluso si se cierra la terminal. El comando redirige la salida estándar y el error estándar al archivo `nohup.out` por defecto (o a uno especificado).

---

### **El script `procesoinfinito.sh`**

Este script ejecuta un bucle infinito que imprime un mensaje cada 2 segundos:

```bash
#!/bin/bash

while true
do 
    echo 'esto es un mensaje infinito'
    sleep 2
done
```

1. **`#!/bin/bash`**: Indica que el script debe ejecutarse con Bash.
2. **`while true`**: Comienza un bucle infinito.
3. **`do` y `done`**: Define el cuerpo del bucle.
4. **`echo`**: Imprime el mensaje `'esto es un mensaje infinito'`.
5. **`sleep 2`**: Pausa la ejecución por 2 segundos antes de la siguiente iteración.

---

### **Ejecución del script con `nohup`**

```bash
nohup bash procesoinfinito.sh &
```

1. **`nohup`**: Asegura que el script siga ejecutándose incluso si la terminal se cierra.
2. **`bash procesoinfinito.sh`**: Ejecuta el script utilizando Bash.
3. **`&`**: Coloca el proceso en segundo plano (background), liberando la terminal para otros comandos.

Al ejecutarlo, `nohup` redirige automáticamente la salida del script al archivo `nohup.out`.

---

### **Verificación del proceso**

```bash
ps aux | grep scriptinfinito.sh
```

1. **`ps aux`**: Muestra todos los procesos activos del sistema.
    - **`a`**: Incluye procesos de todos los usuarios.
    - **`u`**: Muestra el usuario que ejecuta cada proceso.
    - **`x`**: Incluye procesos que no tienen una terminal asociada.
2. **`| grep scriptinfinito.sh`**: Filtra la salida para mostrar solo las líneas que contienen `scriptinfinito.sh`.

Esto muestra algo como:

```
usuario   232323  0.0  0.1  12345  6789 ?    S    12:34   0:00 bash procesoinfinito.sh
```

---

### **Terminar el proceso**

```bash
kill -9 232323
```

1. **`kill`**: Envía una señal a un proceso.
2. **`-9`**: Fuerza la terminación del proceso (señal SIGKILL).
3. **`232323`**: Es el ID del proceso (`PID`) que se obtuvo con el comando `ps`.

Después de este comando, el proceso deja de ejecutarse.

---

### **Si el proceso se cierra al cerrar la terminal**

Esto ocurre si no se utiliza `nohup`. Sin `nohup`, el proceso depende de la terminal y se detendrá automáticamente al cerrarla.

Para evitarlo:

- Usa `nohup`.
- O usa `screen` o `tmux`, que permiten sesiones persistentes.


