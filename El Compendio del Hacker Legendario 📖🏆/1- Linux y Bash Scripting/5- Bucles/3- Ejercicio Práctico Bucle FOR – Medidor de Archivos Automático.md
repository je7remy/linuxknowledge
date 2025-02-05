### **Script 1: Mostrar tamaño de archivos**

Este script itera sobre los archivos del directorio actual y muestra cuánto espacio ocupa cada archivo en bytes.

```bash
#!/bin/bash

archivos=$(ls)

for archivo in $archivos
do
    if [ -f "$archivo" ]; then
        espacio=$(du -b "$archivo" | awk '{print $1}')
        echo "El archivo $archivo ocupa más de $espacio bytes"
    fi
done
```

1. `archivos=$(ls)`: Se obtiene una lista de archivos y directorios en el directorio actual.
2. `for archivo in $archivos`: Inicia un bucle que recorre cada elemento de la lista.
3. `if [ -f "$archivo" ]`: Verifica si el elemento actual es un archivo regular.
4. `espacio=$(du -b "$archivo" | awk '{print $1}')`: Obtiene el tamaño del archivo en bytes usando `du` y extrae solo la cantidad.
5. `echo`: Muestra el tamaño del archivo en la terminal.

Problema potencial: Este script puede fallar si los nombres de archivos contienen espacios o caracteres especiales, ya que `ls` no maneja bien estos casos.

---

### **Script 2: Eliminar archivos mayores a 1 MB**

Este script elimina archivos mayores a 1 MB (1,000,000 bytes).

```bash
#!/bin/bash

archivos=$(ls)

for archivo in $archivos
do
    if [ -f "$archivo" ]; then
        espacio=$(du -b "$archivo" | awk '{print $1}')
        if [ "$espacio" -gt 1000000 ]; then
            echo "Eliminamos $archivo, ocupa más de 1MB"
            rm "$archivo"
        fi
    fi
done
```

1. Similar a Script 1, recorre los archivos en el directorio actual.
2. Si el tamaño del archivo supera 1 MB, muestra un mensaje indicando que se elimina el archivo y lo elimina con `rm`.

Problema potencial: Como en el primer script, los nombres de archivos con espacios o caracteres especiales podrían no ser manejados correctamente.

---

### **Errores con nombres largos o con espacios**

El nombre del archivo problemático `'Hacer más cursos de ciberseguridad no te hará conseguir trabajo.mp4'` provoca problemas porque el nombre completo no se maneja correctamente en un bucle basado en `ls`.

---

### **Soluciones y Buenas Prácticas**

#### 1. Uso de `find` en lugar de `ls`

`find` maneja nombres de archivos con espacios y caracteres especiales de forma adecuada. El script modificado sería:

```bash
#!/bin/bash

find . -type f | while read -r archivo; do
    espacio=$(du -b "$archivo" | awk '{print $1}')
    if [ "$espacio" -gt 1000000 ]; then
        echo "Eliminamos $archivo, ocupa más de 1MB."
        rm "$archivo"
    fi
done
```

- **Explicación**:
    - `find . -type f`: Busca todos los archivos regulares en el directorio actual y subdirectorios.
    - `read -r archivo`: Lee cada nombre de archivo correctamente, incluyendo los que tienen espacios.
    - `"$archivo"`: Entrecomillar protege los nombres de archivos con caracteres especiales.

#### 2. Escaneo previo con confirmación

Antes de eliminar un archivo, es recomendable listar los archivos que se van a eliminar y pedir confirmación:

```bash
#!/bin/bash

find . -type f | while read -r archivo; do
    espacio=$(du -b "$archivo" | awk '{print $1}')
    if [ "$espacio" -gt 1000000 ]; then
        echo "El archivo $archivo ocupa más de 1MB. ¿Deseas eliminarlo? (s/n)"
        read -r respuesta
        if [ "$respuesta" = "s" ]; then
            rm "$archivo"
            echo "$archivo eliminado."
        else
            echo "$archivo conservado."
        fi
    fi
done
```

#### 3. Registro de archivos eliminados

Crea un registro de los archivos eliminados para auditorías posteriores:

```bash
#!/bin/bash

log="archivos_eliminados.log"
> "$log"

find . -type f | while read -r archivo; do
    espacio=$(du -b "$archivo" | awk '{print $1}')
    if [ "$espacio" -gt 1000000 ]; then
        echo "Eliminamos $archivo, ocupa más de 1MB."
        echo "$archivo - $espacio bytes" >> "$log"
        rm "$archivo"
    fi
done

echo "Proceso completo. Revisa $log para ver los detalles."
```

---

### **Resumen de Mejores Prácticas**

1. **Usar `find`** en lugar de `ls` para manejar nombres complejos.
2. **Siempre entrecomillar** las variables que representan nombres de archivos.
3. **Confirmar antes de eliminar** archivos críticos.
4. **Mantener un registro** de los archivos eliminados.
5. **Probar el script en un entorno seguro** antes de usarlo en datos importantes.

Con estos ajustes, evitarás errores con nombres de archivos largos y tendrás mayor control sobre el proceso.
