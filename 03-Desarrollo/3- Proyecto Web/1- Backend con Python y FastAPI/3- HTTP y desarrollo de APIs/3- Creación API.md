
# Módulo 8: Arquitectura REST y Métodos HTTP

## Lección 8.1: El Protocolo y el Formato de Datos

Antes de escribir código, debemos entender las reglas del juego. La web funciona sobre un protocolo llamado **HTTP** y las APIs modernas hablan en **JSON**.

### 1. ¿Qué es HTTP?

Como viste en la pregunta, HTTP significa **Hypertext Transfer Protocol** (Protocolo de Transferencia de Hipertexto).

- **No es solo texto:** Aunque nació para texto, hoy transporta imágenes, videos y, lo más importante para nosotros, datos JSON.
    
- **Cliente-Servidor:** Funciona con un sistema de petición-respuesta. El cliente (navegador/móvil) pide, el servidor (FastAPI) responde.
    

### 2. El Lenguaje de las APIs: JSON vs XML

Antiguamente, las APIs usaban XML, que era pesado y difícil de leer.

Hoy, el estándar es JSON (JavaScript Object Notation).

**¿Por qué JSON ganó la batalla?**

1. **Ligero:** Usa menos caracteres para decir lo mismo (menos ancho de banda).
    
2. **Legible:** Es fácil de entender para humanos.
    
3. **Nativo:** Se mapea perfectamente a objetos de JavaScript (frontend) y Diccionarios de Python (backend).
    

---

## Lección 8.2: Diseño de Rutas (Endpoints)

Una API profesional se distingue por cómo organiza sus URLs.

### 1. Jerarquía de Recursos

Mira la pregunta sobre /usuarios/productos.

En REST, las URLs deben representar recursos (sustantivos), no acciones (verbos).

- **Mal:** `/obtenerProductosDeUsuario` (Esto es una acción).
    
- **Bien:** `/usuarios/{id}/productos` (Esto es una jerarquía).
    

**Significado:** Esto indica que los "productos" son recursos hijos que pertenecen a un "usuario" padre. Ayuda a organizar la lógica y hace la API predecible.

### 2. Paginación

Cuando tienes 1 millón de productos, no puedes devolverlos todos en una sola petición (el servidor explotaría).

La Paginación es la técnica de dividir esos resultados en bloques manejables ("Página 1", "Página 2").

---

## Lección 8.3: Los Verbos HTTP (CRUD)

Aquí es donde definimos la **intención** de nuestra petición. FastAPI utiliza estos métodos para saber qué función ejecutar.

### 1. GET: El Explorador

- **Función:** Recuperar información. **Solo lectura**.
    
- **Comportamiento:** Es el método que usan los navegadores por defecto cuando escribes una URL.
    
- **Seguridad:** No modifica el estado del servidor (no borra ni crea nada). Es "seguro".
    

### 2. POST: El Constructor

- **Función:** Enviar datos para **crear** un recurso nuevo.
    
- **Diferencia con GET:** Los datos viajan ocultos en el "cuerpo" (body) de la petición, no en la URL.
    

### 3. PUT vs PATCH: Los Editores

Ambos sirven para actualizar, pero hay una diferencia clave de examen:

- **PUT:** Reemplaza el recurso **completamente**. Si envías un usuario solo con el "nombre", y el usuario tenía "edad", la edad se borrará (porque reemplazaste todo el objeto).
    
- **PATCH:** Actualización **parcial**. Solo cambia los campos que envíes.
    

### 4. DELETE: El Destructor

- **Función:** Eliminar un recurso del servidor.
    

---

### Resumen Visual: Mapeo CRUD

En el examen y en la vida real, siempre debes tener clara esta tabla:

|**Operación (CRUD)**|**Método HTTP**|**Descripción**|
|---|---|---|
|**C**reate (Crear)|**POST**|Crea un recurso nuevo.|
|**R**ead (Leer)|**GET**|Lee datos sin modificarlos.|
|**U**pdate (Actualizar)|**PUT**|Reemplaza totalmente un recurso.|
|**D**elete (Borrar)|**DELETE**|Elimina el recurso.|

---

### Implementación en FastAPI

Todo esto se traduce en código muy simple gracias a los decoradores que hemos visto:

Python

```
@app.get("/items")        # Leer
@app.post("/items")       # Crear
@app.put("/items/{id}")   # Reemplazar
@app.delete("/items/{id}")# Borrar
```

### Código Práctico: CRUD de Usuarios con Pydantic

Python

```
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

# Instanciamos la aplicación
app = FastAPI()

# --- MODELO DE DATOS (Pydantic) ---
# Define la estructura y tipos de datos para un Usuario
class User(BaseModel):
    id: int
    name: str
    surname: str
    url: str
    age: int

# --- BASE DE DATOS SIMULADA (En memoria) ---
users_list = [
    User(id=1, name="Brais", surname="Moure", url="https://moure.dev", age=35),
    User(id=2, name="Moure", surname="Dev", url="https://mouredev.com", age=35),
    User(id=3, name="Haakon", surname="Dahlberg", url="https://haakon.com", age=33)
]

# --- OPERACIONES DEL CRUD ---

# 1. GET (Read): Obtener todos los usuarios
@app.get("/users")
async def users():
    return users_list

# 2. GET (Read): Obtener un usuario específico por ID (Path Parameter)
@app.get("/user/{id}")
async def user(id: int):
    return search_user(id)
    
# 3. POST (Create): Crear un nuevo usuario
@app.post("/user/", status_code=201)
async def user(user: User):
    # Validamos si el usuario ya existe para no duplicarlo
    if type(search_user(user.id)) == User:
        raise HTTPException(status_code=404, detail="El usuario ya existe")
    
    users_list.append(user)
    return user

# 4. PUT (Update): Actualizar un usuario completo
@app.put("/user/")
async def user(user: User):
    found = False
    
    # Recorremos la lista para encontrar al usuario y reemplazarlo
    for index, saved_user in enumerate(users_list):
        if saved_user.id == user.id:
            users_list[index] = user  # Reemplazo completo
            found = True
            
    if not found:
        return {"error": "No se ha encontrado el usuario para actualizar"}
    
    return user

# 5. DELETE (Delete): Eliminar un usuario por ID
@app.delete("/user/{id}")
async def user(id: int):
    found = False
    
    for index, saved_user in enumerate(users_list):
        if saved_user.id == id:
            del users_list[index]  # Eliminamos de la lista
            found = True
            
    if not found:
        return {"error": "No se ha encontrado el usuario a eliminar"}
    
    return {"message": "Usuario eliminado correctamente"}

# --- FUNCIÓN AUXILIAR ---
def search_user(id: int):
    # Filtramos la lista buscando coincidencias por ID
    users = filter(lambda user: user.id == id, users_list)
    try:
        return list(users)[0]
    except:
        return {"error": "No se ha encontrado el usuario"}
```

---

### Desglose

Aquí está la explicación técnica de lo que acabamos de implementar para tus notas de estudio:

1. **GET con Path Parameter (`/user/{id}`):**
    
    - Permite buscar un recurso específico. FastAPI lee el `{id}` de la URL, lo valida como entero (`id: int`) y se lo pasa a tu función.
        
2. **POST (`/user/`):**
    
    - Recibe un objeto `User` en el cuerpo de la petición (JSON).
        
    - **Validación:** Antes de guardar, usamos la función auxiliar `search_user` para asegurarnos de que no estamos duplicando un ID existente.
        
    - **Status Code 201:** Es buena práctica devolver un código 201 (Created) al crear recursos.
        
3. **PUT (`/user/`):**
    
    - Recibe el objeto con los datos modificados. Busca el usuario original por su ID y lo **sobrescribe** completamente en la lista.
        
4. **DELETE (`/user/{id}`):**
    
    - Solo necesita el ID. Busca en la lista y utiliza `del` para borrar el registro.
        

### Cómo probar esto (Testing)

Como aprendimos en el Módulo 6, no puedes probar POST, PUT o DELETE desde la barra del navegador. Debes usar:

1. **Swagger UI:** Ve a `http://127.0.0.1:8000/docs`. Ahora verás botones verdes (POST), naranjas (PUT) y rojos (DELETE). ¡Pruébalos ahí mismo!
    
2. **Thunder Client / Postman:** Crea una petición POST, selecciona "Body" -> "JSON" y envía los datos de un nuevo usuario.