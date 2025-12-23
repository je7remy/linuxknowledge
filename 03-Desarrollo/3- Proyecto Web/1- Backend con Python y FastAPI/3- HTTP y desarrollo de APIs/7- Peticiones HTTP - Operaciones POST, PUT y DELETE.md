
# Módulo 11: Operaciones de Escritura: POST, PUT y DELETE

## Lección 11.1: Creación de Recursos con POST

El método **POST** se utiliza para enviar datos al servidor y crear un nuevo recurso. En FastAPI, esto implica recibir un objeto Pydantic en el cuerpo de la petición.

### Análisis del Código:

Python

```
@app.post("/user/", response_model=User)
async def user(user: User):
    # 1. Validación de Duplicados
    if type(search_user(user.id)) == User:
        return {"error": "El usuario ya existe"}

    # 2. Persistencia (Guardar)
    users_list.append(user)
    return user
```

**Desglose Técnico:**

1. **`@app.post`**: El decorador indica que esta función solo responderá a peticiones HTTP POST.
    
2. **`user: User`**: Aquí ocurre la magia. FastAPI espera un JSON en el **Body** de la petición que coincida con la estructura de tu clase `User`. Si el JSON es válido, lo convierte automáticamente a un objeto Python `user`.
    
3. **Lógica de Negocio**: Antes de guardar, verificamos si el ID ya existe usando `search_user`. Esto evita duplicados en nuestra "base de datos".
    
4. **`users_list.append(user)`**: Si es nuevo, lo agregamos a la lista.
    

> **Nota de Certificación:** Observa `response_model=User` en el decorador. Esto le dice a FastAPI y a la documentación automática que esta ruta **siempre** devolverá datos que cumplan con el esquema `User`.

---

## Lección 11.2: Actualización Completa con PUT

El método **PUT** se utiliza para actualizar un recurso existente. La característica clave del PUT es que **reemplaza el recurso completo**.

### Análisis del Código:

Python

```
@app.put("/user/")
async def user(user: User):
    found = False

    # 1. Búsqueda del índice
    for index, saved_user in enumerate(users_list):
        if saved_user.id == user.id:
            # 2. Reemplazo TOTAL
            users_list[index] = user
            found = True

    if not found:
        return {"error": "No se ha actualizado el usuario"}

    return user
```

**Desglose Técnico:**

1. **Iteración (`enumerate`)**: Recorremos la lista buscando el usuario que coincida con el ID enviado.
    
2. **Reemplazo (`users_list[index] = user`)**: Al encontrarlo, sobrescribimos el objeto antiguo con el nuevo objeto `user` que llegó en la petición.
    
3. **Idempotencia**: Si envías la misma petición PUT diez veces con los mismos datos, el resultado en el servidor será siempre el mismo (el usuario queda actualizado con esos datos).
    

---

## Lección 11.3: Eliminación de Recursos con DELETE

El método **DELETE** es el encargado de borrar recursos. Generalmente, no necesita un cuerpo (body), solo un identificador en la ruta (Path Parameter).

### Análisis del Código:

Python

```
@app.delete("/user/{id}")
async def user(id: int):
    found = False

    for index, saved_user in enumerate(users_list):
        if saved_user.id == id:
            # 1. Eliminación
            del users_list[index]
            found = True

    if not found:
        return {"error": "No se ha eliminado el usuario"}
```

**Desglose Técnico:**

1. **Path Parameter (`/user/{id}`)**: A diferencia de POST y PUT, aquí necesitamos saber _cuál_ usuario borrar. Usamos `{id}` en la URL (ej: `/user/1`).
    
2. **`del`**: Es la instrucción de Python para eliminar un elemento de una lista por su índice.
    

---

## Lección 11.4: Refactorización y Buenas Prácticas

El código incluye una función auxiliar `search_user`. Esto es excelente para cumplir el principio **DRY (Don't Repeat Yourself)**.

Python

```
def search_user(id: int):
    users = filter(lambda user: user.id == id, users_list)
    try:
        return list(users)[0]
    except:
        return {"error": "No se ha encontrado el usuario"}
```

Limitación Actual (Para examen):

Actualmente, tu código devuelve {"error": "..."} cuando algo falla. Para FastAPI, esto sigue siendo un código de estado 200 OK (éxito), solo que con un mensaje de error dentro.

En una API profesional, deberíamos devolver códigos de estado HTTP reales:

- **404 Not Found** si no existe el usuario.
    
- **400 Bad Request** si el usuario ya existe.
    
- **201 Created** al crear un usuario.
    

---

### Resumen del Módulo

Has implementado un sistema CRUD completo en memoria.

- **POST**: Crea (`append`).
    
- **PUT**: Actualiza (`list[index] = new_value`).
    
- **DELETE**: Borra (`del list[index]`).
    
- **GET**: Lee.
    

