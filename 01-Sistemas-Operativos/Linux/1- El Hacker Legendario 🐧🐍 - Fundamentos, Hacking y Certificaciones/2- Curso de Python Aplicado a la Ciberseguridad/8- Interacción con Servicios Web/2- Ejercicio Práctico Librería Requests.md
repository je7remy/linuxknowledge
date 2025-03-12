
---

#Python #HTTPRequests #ErrorHandling #FileReading #WebScraping #CodingBestPractices

---
### **Análisis del primer bloque de código**


```python
import request

with open('favoritos.txt', 'r') as archivo_lectura:
    urls = archivo_lectura.readline()

for direccion in urls:
    direccion =  direccion.strip()

    try:
        respuesta = request.get(direccion, timeout=5)
        if respuesta.status_code == 200:
            print(f"La url {direccion} existe")
        else:
            print(f"La url {direccion} no esta levantada, pero tiene un codigo de estado")

    except:
        print(f"La url {direccion} no existe")
```

#### **Explicación paso a paso y errores encontrados:**

1. **Importación del módulo:**
   - **Línea:** `import request`
   - **Problema:** En Python, el módulo correcto para hacer solicitudes HTTP es `requests` (en plural), no `request`. Este error hará que el código falle porque `request` no existe como módulo estándar para este propósito.
   - **Corrección:** Cambiar a `import requests`.

2. **Lectura del archivo:**
   - **Línea:** `urls = archivo_lectura.readline()`
   - **Problema:** El método `readline()` (en singular) lee únicamente la primera línea del archivo y devuelve una cadena, no una lista de líneas. Esto significa que `urls` será una sola cadena con la primera línea de `favoritos.txt`.
   - **Impacto:** Al usar `for direccion in urls:`, el bucle no iterará sobre líneas del archivo, sino sobre cada carácter de esa cadena. Por ejemplo, si la primera línea es `"google.com"`, el bucle intentará verificar `"g"`, `"o"`, `"o"`, etc., como URLs, lo cual no tiene sentido.
   - **Corrección:** Usar `readlines()` (en plural) para leer todas las líneas del archivo como una lista: `urls = archivo_lectura.readlines()`.

3. **Uso de la biblioteca para solicitudes HTTP:**
   - **Línea:** `respuesta = request.get(direccion, timeout=5)`
   - **Problema:** Debido al error en la importación, `request.get` no existe. Incluso si se corrige a `requests`, debe usarse como `requests.get`.
   - **Corrección:** Cambiar a `requests.get(direccion, timeout=5)`.

4. **Manejo de excepciones:**
   - **Bloque:** `except:`
   - **Problema:** Este `except` captura todas las excepciones sin especificar cuál, lo que puede ocultar errores inesperados (como problemas de archivo o red). Además, el mensaje `"La url {direccion} no existe"` no siempre es correcto, ya que la excepción podría deberse a un timeout o un error diferente.
   - **Mejora:** Especificar el tipo de excepción, como `requests.exceptions.RequestException`, y dar un mensaje más detallado.

5. **Problema potencial con URLs:**
   - **Observación:** Si las URLs en `favoritos.txt` no incluyen el esquema (por ejemplo, `http://` o `https://`), `requests.get` fallará. Aunque no es un error directo en el código, es algo que podría mejorarse.
   - **Sugerencia:** Añadir un esquema por defecto si no está presente.

---

### **Análisis del segundo bloque de código**


```python
import requests

with open('favoritos.txt', 'r') as archivo_lectura:
    urls = archivo_lectura.readlines()

for direccion in urls:
    direccion =  direccion.strip()

    try:
        respuesta = requests.get(direccion, timeout=5)
        if respuesta.status_code == 200:
            print(f"La url {direccion} existe")
        else:
            print(f"La url {direccion} no esta levantada, pero tiene un codigo de estado")

    except:
        print(f"La url {direccion} no existe")
```

#### **Explicación paso a paso y observaciones:**

1. **Importación del módulo:**
   - **Línea:** `import requests`
   - **Correcto:** Ahora se usa el módulo correcto para solicitudes HTTP.

2. **Lectura del archivo:**
   - **Línea:** `urls = archivo_lectura.readlines()`
   - **Correcto:** El método `readlines()` lee todas las líneas del archivo como una lista, lo que permite iterar correctamente sobre cada URL en el bucle `for`.

3. **Uso de la biblioteca para solicitudes HTTP:**
   - **Línea:** `respuesta = requests.get(direccion, timeout=5)`
   - **Correcto:** Se usa `requests.get` de manera adecuada para hacer la solicitud HTTP con un tiempo de espera de 5 segundos.

4. **Manejo de excepciones:**
   - **Bloque:** `except:`
   - **Problema:** Igual que en el primer bloque, captura todas las excepciones sin especificar, y el mensaje puede ser impreciso.
   - **Mejora:** Especificar la excepción y mejorar el mensaje.

5. **Problema potencial con URLs:**
   - **Observación:** Al igual que en el primer bloque, no se maneja el caso de URLs sin esquema (`http://` o `https://`), lo que podría causar errores.
   - **Sugerencia:** Añadir un esquema por defecto.

---

### **Diferencias clave entre los dos bloques**

- **Importación:** El primer bloque usa `import request` (incorrecto), mientras que el segundo usa `import requests` (correcto).
- **Lectura del archivo:** El primero usa `readline()` (lee una sola línea como cadena), y el segundo usa `readlines()` (lee todas las líneas como lista).
- **Funcionamiento:** El primer bloque no funcionará correctamente debido a los errores mencionados, mientras que el segundo sí funciona, aunque puede mejorarse.

---

### **Código corregido y completo**


```python
import requests

with open('favoritos.txt', 'r') as archivo_lectura:
    urls = archivo_lectura.readlines()

for direccion in urls:
    direccion = direccion.strip()
    # Añadir esquema por defecto si no está presente
    if not direccion.startswith(('http://', 'https://')):
        direccion = 'http://' + direccion
    try:
        respuesta = requests.get(direccion, timeout=5)
        if respuesta.status_code == 200:
            print(f"La url {direccion} existe y está accesible")
        else:
            print(f"La url {direccion} devolvió un código de estado {respuesta.status_code}")
    except requests.exceptions.RequestException as e:
        print(f"No se pudo conectar a la url {direccion}: {e}")
```

#### **Explicación de las mejoras:**

1. **Importación:** Se usa `requests` correctamente.
2. **Lectura del archivo:** `readlines()` asegura que se lean todas las URLs.
3. **Esquemas en URLs:** Se añade `http://` si la URL no tiene esquema, evitando errores.
4. **Excepciones:** Se captura específicamente `requests.exceptions.RequestException` y se muestra el error detallado.
5. **Mensajes:** Los mensajes son más claros y específicos, incluyendo el código de estado cuando aplica.

---

### **Resumen**

- El **primer bloque** tiene errores graves que lo hacen no funcional: importación incorrecta, lectura errónea del archivo y uso incorrecto de la biblioteca.
- El **segundo bloque** funciona mejor, pero puede mejorarse con un manejo más preciso de excepciones y URLs.
- El **código corregido** soluciona todos estos problemas y añade robustez.

---





