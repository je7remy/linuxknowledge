
---

#Bash #Linux #ShellScripting #ScriptDeBash #Automatización #BusquedaDeArchivos #ComandosDeSistema #find #tr #awk #LinuxTips #ManejoDeArchivos #ProgramaciónEnLinux #SistemaOperativo #ProcesamientoDeTextos #AutomatizaciónDeTareas #ComandosShell #AdministraciónDeSistemas #ScriptDeBusqueda #TareasAutomatizadas

---
Este script es un ejemplo funcional de cómo automatizar la búsqueda de archivos en un sistema Linux, utilizando herramientas básicas de shell scripting. A continuación, detallo cada parte del proceso y lo que ocurre en cada paso.

---

### Código Original y su Explicación

#### Primera Parte

```bash
#!/bin/bash
read -p "Inserte el nombre del archivo que quieras buscar en el sistema: " archivo
resultado=$(find / -name $archivo 2>/dev/null)
echo $resultado
```

1. **`#!/bin/bash`**:
    
    - Indica que el script se ejecutará con Bash, el intérprete de comandos de Linux.
2. **`read -p`**:
    
    - Solicita al usuario que ingrese el nombre del archivo que desea buscar y guarda la entrada en la variable `archivo`.
3. **`find / -name $archivo`**:
    
    - Realiza una búsqueda recursiva en el sistema de archivos desde la raíz (`/`), buscando coincidencias exactas con el valor de `archivo`.
    - **`2>/dev/null`**: Redirige los errores (como permisos denegados) a `/dev/null` para evitar que se muestren en pantalla.
4. **`echo $resultado`**:
    
    - Muestra en pantalla la ruta completa del archivo encontrado.

---

#### Segunda Parte

```bash
echo '/home/kali/Desktop/dd.jpg' | tr '/' ' '
```

1. **`echo`**:
    
    - Imprime la ruta `/home/kali/Desktop/dd.jpg`.
2. **`tr '/' ' '`**:
    
    - Reemplaza cada barra (`/`) en la ruta con un espacio, transformándola en:
        
        ```
        home kali Desktop dd.jpg
        ```
        

---

#### Tercera Parte

```bash
echo '/home/kali/Desktop/dd.jpg' | tr '/' ' ' | awk '{print $NF}'
```

1. **`echo`**:
    
    - Imprime la ruta `/home/kali/Desktop/dd.jpg`.
2. **`tr '/' ' '`**:
    
    - Sustituye las barras (`/`) por espacios, como en el paso anterior.
3. **`awk '{print $NF}'`**:
    
    - Extrae el último campo (`NF` significa "Número de Campos") de la cadena transformada. En este caso:
        
        ```
        dd.jpg
        ```
        

---

#### Cuarta Parte

```bash
#!/bin/bash
read -p "Inserte el nombre del archivo que quieras buscar en el sistema: " archivo
resultado=$(find / -name $archivo 2>/dev/null)
resultado_final=$(echo $resultado | tr '/' ' ' | awk '{print $NF}')
echo "El archivo encontrado es: ---> $resultado_final "
```

1. **`read -p`**:
    
    - Solicita al usuario el nombre del archivo a buscar y lo guarda en la variable `archivo`.
2. **`find`**:
    
    - Busca el archivo desde la raíz (`/`) y almacena la ruta completa en `resultado`.
3. **`tr '/' ' '`**:
    
    - Transforma las barras de la ruta en espacios.
4. **`awk '{print $NF}'`**:
    
    - Extrae el último campo (nombre del archivo) de la cadena modificada.
5. **`echo`**:
    
    - Muestra al usuario el nombre simplificado del archivo encontrado.

---

### Ejecución del Script

```bash
┌──(kali㉿kali)-[~/Desktop]
└─$ ./scriptbusqueda.sh
Inserte el nombre del archivo que quieras buscar en el sistema: swapfile
El archivo encontrado es: ---> swapfile
```

1. El script solicita el nombre del archivo, en este caso `swapfile`.
2. **`find`** localiza el archivo, por ejemplo: `/var/swapfile`.
3. **`tr`** y **`awk`** procesan la ruta para extraer únicamente `swapfile`.
4. Finalmente, imprime: `El archivo encontrado es: ---> swapfile`.

---

### Observaciones

1. **Uso Limitado**:
    - Si hay múltiples resultados, solo muestra el último archivo encontrado. Esto se debe a que `echo $resultado` procesa todo en una sola línea.
2. **Mejoras Posibles**:
    - **Manejo de múltiples resultados**: Se podría usar un bucle `for` para procesar y mostrar cada resultado.
    - **Validaciones**: Verificar si el archivo existe antes de intentar procesar la ruta.

---

### Conclusión

Este script demuestra cómo usar herramientas básicas de Bash como `find`, `tr` y `awk` para buscar y procesar archivos en un sistema Linux. Aunque funcional, puede mejorarse para manejar escenarios más complejos, como múltiples resultados o la ausencia de archivos coincidentes.




[[2- Ejecución de Comandos a Nivel de Sistema – Guardar Output en Variables]]
[[10- Creamos un Script que Automatice el Tratamiento de la Información]]
