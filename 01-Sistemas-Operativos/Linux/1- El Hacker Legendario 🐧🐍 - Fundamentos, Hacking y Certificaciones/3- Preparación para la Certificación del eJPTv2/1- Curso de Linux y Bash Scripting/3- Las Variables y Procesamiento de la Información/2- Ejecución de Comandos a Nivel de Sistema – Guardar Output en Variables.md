
---

#BashScripting #Linux #Programación #DesarrolloWeb #Automatización #Tecnología #AprenderBash #EvoluciónDeScripts #AutomatizaciónDeTareas #MejoresPrácticasBash #DocumentaciónTécnica #ScriptsDeBash #ComandosLinux #EducaciónTecnológica #CompartirConocimientos #TutorialesDeBash

---
A continuación observaremos una evolución progresiva en el uso de comandos y variables en un script de Bash. Aquí está la explicación y desarrollo de cada etapa:

---

### **1. Primer fragmento:**

```bash
variable=$(ls)
echo $variable
```

- **Descripción:**
    
    - Se usa `ls` para listar el contenido del directorio actual.
    - El resultado de `ls` se almacena en la variable `variable`.
    - Con `echo $variable`, se imprime el contenido de la variable.
- **Comentarios:**
    
    - Este fragmento es básico y funcional, pero no tiene un propósito más allá de demostrar el uso de una variable para almacenar la salida de un comando.

---

### **2. Segundo fragmento:**

```bash
#!/bin/bash

archivos=$(ls)

echo 'vamos a listar todos los archivos del escritorio'

sleep 2

echo $archivos
```

- **Descripción:**
    
    - Añade un encabezado `#!/bin/bash`, necesario para ejecutar el script en Bash.
    - Se declara la variable `archivos` para almacenar el resultado de `ls`.
    - Un mensaje explicativo se muestra antes de listar los archivos.
    - El comando `sleep 2` introduce una pausa de 2 segundos antes de mostrar el contenido de la variable `archivos`.
- **Comentarios:**
    
    - Este script mejora la claridad al incluir una descripción del propósito antes de listar los archivos.
    - Sin embargo, el script sigue limitado al uso del comando `ls` sin especificar un contexto más detallado.

---

### **3. Tercer fragmento:**

```bash
#!/bin/bash

archivos=$(ls)
ruta=$(pwd)

echo "vamos a listar todos los archivos de: $ruta"

sleep 2

echo $archivos
```

- **Descripción:**
    
    - Introduce una nueva variable `ruta`, que almacena la ruta actual obtenida con `pwd` (print working directory).
    - Un mensaje más descriptivo incluye la ruta actual para proporcionar contexto.
    - Después de una pausa de 2 segundos, se listan los archivos.
- **Comentarios:**
    
    - Este script es más completo y proporciona información útil, como la ruta actual.
    - Se orienta hacia la contextualización del contenido listado, pero todavía no filtra archivos específicos.

---

### **4. Cuarto fragmento:**

```bash
#!/bin/bash

archivos=$(ls)
ruta=$(pwd)
scripts=$(ls | grep *.sh)

echo "vamos a listar todos los archivos con extension .sh de la ruta: $ruta"

sleep 2

echo $scripts
```

- **Descripción:**
    
    - Añade una variable `scripts` para almacenar archivos con extensión `.sh` en el directorio actual.
    - Usa `ls | grep *.sh` para filtrar solo archivos con esa extensión.
    - El mensaje ahora indica explícitamente que se listarán solo los archivos `.sh`.
    - Después de la pausa, se imprimen los archivos filtrados.
- **Comentarios:**
    
    - Este script comienza a ser más útil para casos específicos, como trabajar con scripts en Bash.
    - Sin embargo, la combinación `ls | grep` puede fallar en ciertos casos, como nombres de archivos con caracteres especiales o extensiones en mayúsculas.

---

### **5. Quinto fragmento:**

```bash
#!/bin/bash

archivos=$(ls)
ruta=$(pwd)
scripts=$(ls *.sh)

echo "vamos a listar todos los archivos con extension .sh de la ruta: $ruta"

sleep 2

echo $scripts
```

- **Descripción:**
    
    - Optimiza la obtención de archivos `.sh` utilizando directamente `ls *.sh`, lo que es más eficiente y legible.
    - La estructura general del script permanece igual, pero esta versión es menos propensa a errores que la anterior.
- **Comentarios:**
    
    - Este es el más eficiente de los ejemplos. Utiliza buenas prácticas al trabajar con Bash y tiene un propósito claro: listar archivos `.sh` en el directorio actual.

---

### **Evolución resumida:**

1. **Básico:** Guardar y mostrar el resultado de `ls` en una variable.
2. **Claridad:** Introducir mensajes para explicar lo que hace el script.
3. **Contexto:** Mostrar la ruta actual junto con los archivos listados.
4. **Especificidad:** Filtrar archivos `.sh` usando `grep`.
5. **Eficiencia:** Filtrar archivos `.sh` directamente con `ls *.sh`.

Esta progresión muestra una evolución hacia scripts más útiles, claros y eficientes en la automatización de tareas con Bash.



[[10- Creamos un Script que Automatice el Tratamiento de la Información]]
[[11- Creamos un Script para Automatizar Búsquedas en el Sistema]]