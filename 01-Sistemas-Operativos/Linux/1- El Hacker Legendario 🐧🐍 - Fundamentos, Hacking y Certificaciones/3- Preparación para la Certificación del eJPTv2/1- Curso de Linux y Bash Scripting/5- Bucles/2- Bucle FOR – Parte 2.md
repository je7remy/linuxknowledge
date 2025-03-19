
---

#Bash #ShellScripting #ComandosLinux #AutomatizacionDeTareas #ScriptsDeBash #AdministracionDeSistemas #ComandosBash #TrabajoConArchivos #TrabajoConDirectorios #ExtensionesDeArchivos #CompresionDeArchivos #ZippingFiles #ServidorHTTP #PythonHTTPServer #RedLocal #DireccionIP #ComandoHostname #ScriptingLinux #AutomatizacionDeArchivos #ManejoDeArchivosEnLinux #ProgramacionLinux #ScriptsDeAutomatizacion #ScriptingDeArchivos

---
### **Comando inicial**:

```bash
echo 'recorrerlineas.txt' | awk -F '.' '{print $NF}'
```

- **Explicación**: Este comando imprime la extensión de un archivo llamado `recorrerlineas.txt`.
    - `echo 'recorrerlineas.txt'`: Envía el texto como entrada.
    - `awk -F '.' '{print $NF}'`: Usa `.` como delimitador y selecciona el último campo (`$NF`), que es `txt`.

---

### **Primer script**:

```bash
#!/bin/bash

for archivo in *
do 
    extension=$(echo 'recorrerlineas.txt' | awk -F '.' '{print $NF}')
    echo "$extension"
done
```

- **Explicación**:
    1. Itera sobre todos los archivos en el directorio actual (`for archivo in *`).
    2. Asigna la extensión `txt` al usar `awk` sobre un archivo fijo (`recorrerlineas.txt`).
    3. La salida repetirá `txt` tantas veces como archivos haya en el directorio porque el archivo procesado en el `awk` es fijo.

---

### **Segundo script**:

```bash
#!/bin/bash

for archivo in *
do 
    extension=$(echo "$archivo" | awk -F '.' '{print $NF}')
    echo "$extension"
done
```

- **Explicación**:
    1. Itera sobre todos los archivos en el directorio actual.
    2. Usa `awk` para determinar la extensión real de cada archivo en lugar de un nombre fijo.
    3. Imprime la extensión de cada archivo.

---

### **Tercer script con condiciones**:

```bash
#!/bin/bash

for archivo in *
do 
    extension=$(echo "$archivo" | awk -F '.' '{print $NF}')

    case "$extension" in 
        txt)
            zip -r documentos.zip $archivo >/dev/null
            ;;
    esac
done
```

- **Explicación**:
    1. Itera sobre todos los archivos del directorio.
    2. Si la extensión del archivo es `txt`, lo agrega a un archivo ZIP llamado `documentos.zip`.
    3. Usa `case` para ejecutar el comando ZIP solo si se cumple la condición.

---

### **Comando**:

```bash
hostname -I
```

- **Explicación**: Este comando muestra la dirección IP del sistema en la red local.

---

### **Cuarto script** (servidor HTTP):

```bash
#!/bin/bash

for archivo in *
do 
    extension=$(echo "$archivo" | awk -F '.' '{print $NF}')

    case "$extension" in 
        txt)
            zip -r documentos.zip $archivo >/dev/null
            ;;
    esac
done

mkdir -p servidor/ && mv documentos.zip servidor/

ip=$(hostname -I)

echo "Inserte la $ip desde un navegador de otro equipo que tengas en tu red privada : "

cd servidor/ && python3 -m http.server 80
```

- **Explicación**:
    1. Itera sobre los archivos y, si la extensión es `txt`, los agrupa en un archivo ZIP (`documentos.zip`).
    2. Crea una carpeta llamada `servidor/` y mueve el ZIP allí.
    3. Obtiene la IP del equipo con `hostname -I`.
    4. Inicia un servidor HTTP en el puerto 80 usando `python3 -m http.server`, sirviendo el contenido del directorio `servidor/`.

**Resultado**: El archivo ZIP estará disponible para descarga en la red local accediendo a la dirección IP y puerto indicados en el navegador.




[[1- Bucle FOR – Parte 1]]
[[3- Ejercicio Práctico Bucle FOR – Medidor de Archivos Automático]]
[[4- Ejercicio Práctico Bucle FOR – Script para Ordenar Archivos Automáticamente]]