
El propósito del script es obtener el tamaño de un archivo o directorio y mostrarlo en un mensaje. A continuación, se describe cada paso:

---

### 1. **Comandos utilizados**

- **`du`**: Utilidad que calcula el espacio en disco que ocupa un archivo o directorio.
- **`-h`**: Muestra el resultado en un formato legible para humanos (por ejemplo, 4.0K, 1.5M, 2.1G).
- **`awk`**: Lenguaje de procesamiento de texto utilizado para extraer columnas específicas. En este caso, obtiene la primera columna (el tamaño).

---

### 2. **Ejecución del script**

#### Paso 1: Comando básico

```bash
du -h carpeta_compartida
```

- Este comando muestra el tamaño de la carpeta `carpeta_compartida`.
- Ejemplo de salida:
    
    ```bash
    4.0K  carpeta_compartida
    ```
    

#### Paso 2: Extracción del tamaño

```bash
du -h carpeta_compartida | awk '{print $1}'
```

- Este comando usa `awk` para capturar solo la primera columna de la salida, que corresponde al tamaño.
- Ejemplo de salida:
    
    ```bash
    4.0K
    ```
    

#### Paso 3: Almacenamiento en una variable

```bash
espacio=$(du -h carpeta_compartida | awk '{print $1}')
```

- El resultado del comando anterior se guarda en la variable `espacio`.

#### Paso 4: Mostrar el resultado

```bash
echo "El peso del archivo es $espacio"
```

- Imprime el mensaje combinado con el valor de la variable `espacio`.
- Ejemplo de salida:
    
    ```bash
    El peso del archivo es 4.0K
    ```
    

---

### Script (`script.sh`)

El script completo que has creado con `nano script.sh` es el siguiente:

```bash
#!/bin/bash
espacio=$(du -h carpeta_compartida | awk '{print $1}')
echo "El peso del archivo es $espacio"
```

---

### Ejecución del script

#### Paso 1: Guardar y salir del editor

1. En el editor `nano`, guarda con `Ctrl+O` y luego sal con `Ctrl+X`.

#### Paso 2: Hacer el script ejecutable

2. Cambia los permisos para que sea ejecutable:
    
    ```bash
    chmod +x script.sh
    ```
    

#### Paso 3: Ejecutar el script

3. Ejecuta el script con:
    
    ```bash
    ./script.sh
    ```
    

---

### Resultado final

El mensaje mostrado en el terminal será:

```bash
El peso del archivo es 4.0K
```


