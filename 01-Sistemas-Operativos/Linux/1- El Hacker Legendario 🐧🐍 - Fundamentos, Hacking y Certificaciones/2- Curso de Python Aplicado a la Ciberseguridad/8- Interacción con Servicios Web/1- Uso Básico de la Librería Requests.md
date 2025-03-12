
---

#Python #requests #HTTP #manejo_errores #descarga_archivo #servidor_local

---

#### **1. Importamos el módulo `requests`**

El módulo `requests` nos permite realizar solicitudes HTTP en Python de manera sencilla.

```python
import requests
```

---

#### **2. Realizar una solicitud HTTP a un sitio web**

```python
respuesta = requests.get("https://google.com")
print(respuesta)
```

Aquí:

- `requests.get("https://google.com")` realiza una solicitud HTTP `GET` a Google.
- `respuesta` almacena la respuesta del servidor.
- `print(respuesta)` imprime la respuesta HTTP (como `<Response [200]>` si la solicitud fue exitosa).

---

#### **3. Manejo de Errores con `try-except`**

```python
try:
    respuesta = requests.get("https://google.comm")  # URL incorrecta
    print(respuesta)
except:
    print("La URL no existe")
```

Aquí:

- Se usa `try-except` para manejar errores en caso de que la URL sea incorrecta o no accesible.
- `requests.get("https://google.comm")` intenta hacer la solicitud.
- Si hay un error (como un `requests.exceptions.ConnectionError`), el `except` captura la excepción y muestra `"La URL no existe"`.

---

#### **4. Obtener el Código de Estado de la Respuesta**

```python
try:
    respuesta = requests.get("https://google.com")
    print(respuesta.status_code)
except:
    print("La URL no existe")
```

Aquí:

- `.status_code` devuelve el código HTTP de la respuesta (por ejemplo, `200` si la solicitud fue exitosa, `404` si la página no existe, etc.).

---

#### **5. Descargar un Archivo desde un Servidor HTTP**

```python
try:
    respuesta = requests.get("http://192.168.129.25/compartir_archivo.txt")  # IP de un servidor local
    with open('compartir.txt', 'wb') as archivo_descarga:
        archivo_descarga.write(respuesta.content)
    print(respuesta.status_code)
except:
    print("La URL no existe")
```

Aquí:

- `requests.get("http://192.168.129.25/compartir_archivo.txt")` intenta descargar un archivo desde un servidor local.
- `with open('compartir.txt', 'wb') as archivo_descarga:` abre un archivo en modo escritura binaria (`wb`).
- `archivo_descarga.write(respuesta.content)` guarda el contenido descargado en el archivo local `compartir.txt`.

---

### **Código Completo**

```python
import requests

try:
    respuesta = requests.get("http://192.168.129.25/compartir_archivo.txt")
    with open('compartir.txt', 'wb') as archivo_descarga:
        archivo_descarga.write(respuesta.content)
    print(respuesta.status_code)
except:
    print("La URL no existe")
```

---
