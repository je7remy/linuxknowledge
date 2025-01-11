La **gestión de procesos** es una función del sistema operativo que se encarga de crear, planificar, ejecutar y finalizar los procesos que se ejecutan en un sistema. Implica la asignación de recursos (CPU, memoria, E/S), el manejo de estados de los procesos (nuevo, listo, ejecutando, bloqueado, terminado) y la coordinación entre procesos para garantizar eficiencia y estabilidad en el sistema:

---

### 1. **`firefox`**

- Ejecuta el navegador Firefox en el terminal de forma interactiva. El terminal queda ocupado mientras Firefox está corriendo.

---

### 2. **`firefox &`**

- Ejecuta el navegador Firefox como un proceso en segundo plano.
- El uso del **`&`** al final permite que el terminal quede libre para otros comandos.

---

### 3. **`jobs`**

- Muestra los trabajos actuales en el terminal que están en segundo plano o suspendidos. Cada trabajo tiene un número único asociado (`%n`).

---

### 4. **`fg`**

- Trae un trabajo en segundo plano o suspendido al primer plano. Si hay más de un trabajo, puedes usar **`fg %n`** para especificar cuál trabajo quieres traer al frente.

---

### 5. **`Ctrl + Z`**

- Suspende el proceso actual que está en el primer plano y lo coloca en pausa (estado suspendido). Este proceso puede reanudarse luego con `fg` o enviarse al segundo plano con `bg`.

---

### 6. **`bg`**

- Reanuda un proceso suspendido y lo envía al segundo plano. Similar a `fg`, puedes especificar el trabajo con **`bg %n`**.

---

### 7. **`fg %1`**

- Trae al primer plano el trabajo identificado como `1`. El número `%1` corresponde al trabajo listado por el comando `jobs`.

---

### 8. **`pgrep firefox`**

- Busca el ID del proceso (PID) asociado a Firefox. Si Firefox está corriendo, devuelve su(s) PID(s).

---

### 9. **`kill 4617`**

- Termina el proceso con el PID `4617`. Este número es típicamente obtenido de comandos como `pgrep` o `ps`.

---

### 10. **`ps aux`**

- Muestra una lista de todos los procesos del sistema con información detallada, incluyendo:
    - Usuario propietario del proceso.
    - Uso de CPU y memoria.
    - PID.
    - Estado del proceso.
    - Comando que inició el proceso.

---

### 11. **`ps aux | grep firefox`**

- Este comando utiliza una **tubería (|)** para conectar dos comandos:
    1. `ps aux` lista todos los procesos.
    2. `grep firefox` filtra los procesos que incluyen el término "firefox" en su línea de comando.
- El resultado muestra los procesos relacionados con Firefox. La salida puede incluir:
    - Líneas relevantes del proceso de Firefox.
    - También puede incluir la línea del comando `grep` que buscó "firefox" en sí mismo.

---

### **Ejemplo de desglose:**

- Salida típica del comando `ps aux | grep firefox`:
    
    ```
    user   4617  3.2  1.5 123456 65432 ?  S  12:00   0:02 /usr/lib/firefox/firefox
    user   4625  0.0  0.0   9876   432 ?  S  12:00   0:00 grep --color=auto firefox
    ```
    
- **`user`**: Usuario propietario del proceso.
- **`4617`**: PID del proceso principal de Firefox.
- **`3.2`** y **`1.5`**: Uso de CPU y memoria (%).
- **`123456` y `65432`**: Uso de memoria virtual y residente.
- **`?`**: Terminal asociado al proceso (`?` indica que no tiene un terminal).
- **`S`**: Estado del proceso (`S` = durmiendo).
- **`12:00`**: Hora en que inició el proceso.
- **`0:02`**: Tiempo acumulado en ejecución.
- **`/usr/lib/firefox/firefox`**: Ruta completa del ejecutable.