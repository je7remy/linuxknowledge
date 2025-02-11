### Definiciones

1. **Estándar Input (stdin)**:
    
    - Es el flujo de entrada estándar para un programa. Normalmente se refiere al teclado, pero puede redirigirse desde un archivo o salida de otro comando.
    - Descriptor de archivo: **0**.
2. **Estándar Output (stdout)**:
    
    - Es el flujo de salida estándar donde un programa escribe su información de salida. Por defecto, se muestra en la consola (pantalla).
    - Descriptor de archivo: **1**.
3. **Estándar Error (stderr)**:
    
    - Es el flujo de salida estándar para errores y mensajes diagnósticos generados por un programa. También se muestra en la consola por defecto.
    - Descriptor de archivo: **2**.

---

### Ejemplo con comandos en Bash

Supongamos que ejecutamos un script o comando que genera salida normal y errores. Aquí está un ejemplo práctico:

#### 1. **Crear un script con salida estándar, error y redirección:**

```bash
#!/bin/bash

echo "Esto es stdout" # Salida estándar
echo "Esto es stderr" >&2 # Salida de error estándar
read -p "Introduce tu nombre: " nombre # Entrada estándar
echo "Hola, $nombre"
```

#### 2. **Guardar el script como `example.sh` y darle permisos:**

```bash
chmod +x example.sh
```

#### 3. **Ejecución y redirecciones:**

- **Sin redirecciones:**
    
    ```bash
    ./example.sh
    ```
    
    - Muestra la salida normal y de error en la consola.
- **Redirigir stdout a un archivo (`output.txt`):**
    
    ```bash
    ./example.sh > output.txt
    ```
    
    - Solo guarda la salida estándar en `output.txt`. Los errores se seguirán viendo en la consola.
- **Redirigir stderr a un archivo (`error.txt`):**
    
    ```bash
    ./example.sh 2> error.txt
    ```
    
    - Guarda los mensajes de error en `error.txt`. La salida estándar se muestra en la consola.
- **Redirigir stdout y stderr a archivos diferentes:**
    
    ```bash
    ./example.sh > output.txt 2> error.txt
    ```
    
    - Guarda la salida estándar en `output.txt` y los errores en `error.txt`.
- **Redirigir stdout y stderr al mismo archivo:**
    
    ```bash
    ./example.sh > all_output.txt 2>&1
    ```
    
    - Combina stdout y stderr en `all_output.txt`.

#### 4. **Ejemplo con tuberías (`|`) para stdin:**

Si quieres pasar texto desde otro comando o archivo:

```bash
echo "Juan" | ./example.sh
```

Esto envía "Juan" como entrada estándar al script.