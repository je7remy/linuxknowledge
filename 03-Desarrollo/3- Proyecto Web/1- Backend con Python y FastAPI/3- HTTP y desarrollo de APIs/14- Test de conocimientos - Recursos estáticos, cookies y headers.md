
# Módulo 14: Recursos Estáticos, Headers y Cookies

## Lección 14.1: Gestión de Archivos Estáticos

Una API no vive solo de JSON. A menudo necesitas servir imágenes, documentos PDF o los archivos frontend de tu aplicación (HTML/CSS/JS).

### 1. ¿Qué es un recurso estático?

Es un archivo (como una imagen, PDF o documento) que se sirve directamente desde el servidor al cliente sin ser procesado ni modificado dinámicamente por la API.

### 2. Implementación Técnica en FastAPI

Para "abrir" una carpeta al mundo exterior, utilizamos una técnica llamada **Montaje**.

- **La Clase:** Se utiliza `StaticFiles` para exponer directorios con contenido estático.
    
- **El Método:** Se utiliza `mount()` (montar) en la instancia de la app (`app.mount(...)`) para asociar una ruta con un directorio.
    
- **La Ruta Pública:** El primer argumento de `mount()` define el **path público** (la URL) donde se accederá a los archivos.
    

### 3. Ejemplo de Acceso (Pregunta de Examen)

Si tienes una imagen llamada `python.jpg` dentro de la carpeta física `static/images`, y has montado la carpeta en la ruta `/static`, la URL de acceso será:

`/static/images/python.jpg`.

---

## Lección 14.2: Encabezados HTTP (Headers)

El protocolo HTTP transporta "metadatos" invisibles en cada petición que son vitales para la comunicación técnica.

### 1. Propósito

Los headers sirven para transmitir **metainformación** sobre la petición o la respuesta.

- Ejemplos: Token de autorización, tipo de contenido (`application/json`), idioma preferido del usuario.
    

### 2. Captura en FastAPI

Para leer un header específico dentro de tu función (endpoint), debes usar la clase `Header`.

Python

```
from fastapi import Header

@app.get("/items/")
# FastAPI busca automáticamente el header 'User-Agent'
async def read_items(user_agent: str | None = Header(default=None)):
    return {"User-Agent": user_agent}
```

---

## Lección 14.3: Cookies

Las cookies son la memoria del navegador. Sin ellas, el servidor olvidaría quién eres cada vez que recargas la página.

### 1. Uso Principal

Se utilizan principalmente para **mantener el estado** entre peticiones, como recordar sesiones de usuario iniciadas o preferencias de configuración.

### 2. Diferencia Clave vs Headers

Esta es una pregunta clásica de certificación:

- Las **Cookies** se almacenan en el navegador del usuario.
    
- Los **Headers** son parte de la estructura del protocolo de transporte HTTP.
    

### 3. Captura en FastAPI

Al igual que con los headers, para leer una cookie que llega al servidor, utilizas la clase `Cookie`.

Python

```
from fastapi import Cookie

@app.get("/items/")
async def read_items(ads_id: str | None = Cookie(default=None)):
    return {"ads_id": ads_id}
```

---

### Resumen de Clases para el Examen

Aquí tienes la tabla definitiva basada en tus imágenes:

|**Concepto**|**Clase en FastAPI**|**Propósito**|
|---|---|---|
|**Archivos**|`StaticFiles`|Servir carpetas de imágenes/docs.|
|**Headers**|`Header`|Leer metadatos (User-Agent, Auth).|
|**Cookies**|`Cookie`|Leer datos de sesión/estado.|

---


### 1. ¿Qué es un recurso estático en FastAPI?

- **A. Un archivo accesible directamente desde el servidor** (Correcta)
    
- B. Una respuesta JSON generada por la API
    
- C. Un parámetro de consulta
    

> **Justificación:**
> 
> Es un archivo como una imagen, PDF o documento que se sirve directamente desde el servidor sin procesamiento dinámico.

---

### 2. ¿Qué clase se usa para servir archivos estáticos en FastAPI?

- A. FileServer
    
- **B. StaticFiles** (Correcta)
    
- C. StaticRouter
    

> **Justificación:**
> 
> La clase `StaticFiles` es la herramienta específica de FastAPI que permite exponer directorios completos con contenido estático.

---

### 3. ¿Qué método se usa para exponer recursos estáticos en FastAPI?

- A. serve_static()
    
- B. include_router()
    
- **C. mount()** (Correcta)
    

> **Justificación:**
> 
> El método `mount()` permite asociar (montar) una ruta específica de la API con un directorio físico de archivos estáticos.

---

### 4. ¿Qué parámetro define la ruta pública de los recursos estáticos?

- **A. El path público donde se accede a los archivos** (Correcta)
    
- B. El nombre del archivo
    
- C. El tipo MIME del recurso
    

> **Justificación:**
> 
> El primer argumento de la función `mount()` indica el path (URL) bajo el cual se expondrán públicamente los archivos al mundo.

---

### 5. ¿Cómo se accede a una imagen llamada "python.jpg" ubicada en "static/images"?

- **A. /static/images/python.jpg** (Correcta)
    
- B. /images/python.jpg
    
- C. /python.jpg
    

> **Justificación:**
> 
> Si el montaje está correcto, se accede concatenando la ruta de montaje (`/static`) con la ruta interna del archivo (`/images/python.jpg`).

---

### 6. ¿Cuál es el propósito principal de los headers en una petición HTTP?

- A. Definir rutas dinámicas en la API
    
- B. Guardar datos persistentes del usuario
    
- **C. Transmitir metainformación sobre la petición o respuesta** (Correcta)
    

> **Justificación:**
> 
> Los headers (encabezados) transmiten metainformación clave (como tipo de contenido, autorización, idioma) que permite al servidor y al cliente entender cómo manejar la comunicación.

---

### 7. ¿Qué clase se usa para capturar headers en FastAPI?

- A. Meta
    
- B. Cookie
    
- **C. Header** (Correcta)
    

> **Justificación:**
> 
> La clase `Header` permite acceder y validar los valores enviados en las cabeceras HTTP dentro de la función de la ruta.

---

### 8. ¿En qué casos se usan cookies en una API?

- **A. Para mantener estado entre peticiones, como sesiones o preferencias** (Correcta)
    
- B. Para enviar archivos grandes
    
- C. Para definir rutas dinámicas
    

> **Justificación:**
> 
> Las cookies son pequeños datos que permiten "recordar" información entre distintas peticiones, siendo esenciales para mantener sesiones de usuario o preferencias.

---

### 9. ¿Qué diferencia hay entre una cookie y un header?

- **A. Las cookies se guardan en el navegador; los headers son parte del protocolo HTTP** (Correcta)
    
- B. Ambos se usan para enviar archivos
    
- C. Los headers son más seguros que las cookies
    

> **Justificación:**
> 
> La distinción clave es el almacenamiento: las cookies persisten en el navegador del cliente, mientras que los headers son metadatos transitorios del protocolo de transporte.

---

### 10. ¿Qué clase se usa para capturar cookies en FastAPI?

- **A. Cookie** (Correcta)
    
- B. Header
    
- C. Session
    

> **Justificación:**
> 
> La clase `Cookie` se utiliza en los parámetros de la función para leer los valores de las cookies enviadas por el navegador.