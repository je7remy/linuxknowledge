### 1. **Primer Script**

```bash
#!/bin/bash

while read -r linea; do
    echo "$linea"
done < "archivo.txt"
```

#### **Explicación Paso a Paso**:

1. **Shebang (`#!/bin/bash`)**: Indica que este script debe ejecutarse usando Bash.
2. **`while read -r linea`**:
    - Inicia un bucle que lee línea por línea del archivo especificado.
    - `-r`: Evita que el carácter `\` sea interpretado como especial.
    - `linea`: Variable que almacena cada línea leída.
3. **`echo "$linea"`**: Imprime en la terminal el contenido de cada línea.
4. **`done < "archivo.txt"`**: Indica que el archivo **archivo.txt** es la entrada para el bucle.

#### **Resultado**:

El script imprime cada línea del archivo **archivo.txt** en la terminal.

---

### 2. **Segundo Script**

```bash
#!/bin/bash

while read -r linea; do
    echo "Este es el contenido de la linea en esta vuelta: $linea"
done < "archivo.txt"
```

#### **Diferencia con el Primero**:

- Similar al primer script, pero añade un mensaje personalizado antes de mostrar el contenido de cada línea.

#### **Resultado**:

Imprime algo como:

```
Este es el contenido de la linea en esta vuelta: [contenido de la línea]
```

---

### 3. **Tercer Script**

```bash
curl -s -o /dev/null -w "%{http_code}" https://www.google.com/
```

#### **Explicación Paso a Paso**:

1. **`curl`**: Herramienta para hacer solicitudes HTTP desde la terminal.
2. **Opciones usadas**:
    - `-s`: Silencioso, no muestra mensajes de progreso.
    - `-o /dev/null`: Descarta el cuerpo de la respuesta.
    - `-w "%{http_code}"`: Muestra solo el código de estado HTTP.
3. **URL**: La solicitud se hace a `https://www.google.com`.

#### **Resultado**:

Muestra el código de estado HTTP (por ejemplo, `200` si la página está operativa).

---

### 4. **Cuarto Script**

```bash
#!/bin/bash

while read -r url; do
    respuesta=$(curl -s -o /dev/null -w "%{http_code}" "$url")
    if [ "$respuesta" == "200" ]; then
        echo "La url esta operativa, devuelve un $respuesta"
    fi
done < "archivo.txt"
```

#### **Explicación**:

1. Similar al tercer script, pero dentro de un bucle.
2. **`while read -r url`**: Lee líneas (URLs) de **archivo.txt**.
3. **`respuesta=$(...)`**: Almacena el código HTTP devuelto por `curl`.
4. **`if [ "$respuesta" == "200" ]`**:
    - Comprueba si el código es `200` (indica éxito).
    - Si es así, imprime un mensaje indicando que la URL está operativa.

#### **Resultado**:

Para cada URL en **archivo.txt**, imprime si está operativa:

```
La url esta operativa, devuelve un 200
```

---

### 5. **Quinto Script**

```bash
#!/bin/bash

while read -r url; do
    respuesta=$(curl -s -o /dev/null -w "%{http_code}" "$url")
    if [ "$respuesta" == "200" ]; then
        echo "La url $url esta operativa, devuelve un $respuesta"
    fi
done < "texto.txt"
```

#### **Diferencia**:

- Similar al cuarto script, pero incluye el nombre de la URL en el mensaje.

#### **Resultado**:

```
La url https://ejemplo.com esta operativa, devuelve un 200
```

---

### 6. **Sexto Script**

```bash
#!/bin/bash

while read -r url; do
    respuesta=$(curl -s -o /dev/null -w "%{http_code}" "$url")
    if [ "$respuesta" == "200" ]; then
        echo "La url $url esta operativa, devuelve un $respuesta"
    elif [ "$respuesta" != "200" ]; then
        echo "La url $url no esta operativa o no existe, devuelve un $respuesta"
    fi
done < "archivo.txt"
```

#### **Explicación**:

1. Añade una comprobación adicional con `elif` para manejar el caso en que la URL no esté operativa.
2. Si el código HTTP no es `200`, imprime un mensaje indicando que la URL no está operativa.

#### **Resultado**:

Ejemplo de salida:

```
La url https://google.com esta operativa, devuelve un 200
La url https://invalido.com no esta operativa o no existe, devuelve un 404
```

---
