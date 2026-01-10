
---

# Módulo 12: Códigos de Estado HTTP y Manejo de Errores

## Lección 12.1: El Semáforo de la Web

Cada vez que haces una petición, el servidor responde con un número de 3 dígitos. Este número le dice al cliente qué pasó sin necesidad de leer el texto de la respuesta.

Según la clasificación general:

- **2xx (Éxito):** Todo salió bien (ej. 200 OK, 201 Created).
    
- **4xx (Error del Cliente):** Tú te equivocaste (ej. 404 No encontrado, 400 Petición incorrecta).
    
- **5xx (Error del Servidor):** Yo (el servidor) fallé (ej. 500 Internal Server Error).
    

---

## Lección 12.2: Definiendo el Éxito (Status Code 201)

Mira tu función POST en el código que subiste:

Python

```
@app.post("/user/", response_model=User, status_code=201)
async def user(user: User):
    ...
```

**Análisis Técnico:**

- Por defecto, FastAPI devuelve **200 OK**.
    
- Sin embargo, el estándar REST dice que cuando **creas** algo nuevo, debes devolver **201 Created**.
    
- **Implementación:** Agregamos el parámetro `status_code=201` dentro del decorador `@app.post`. Ahora, cuando crees un usuario, el semáforo se pondrá en verde específico de "Creado".
    

---

## Lección 12.3: Lanzando Errores Reales (`HTTPException`)

Aquí es donde tu código da un salto de calidad. En lugar de devolver un diccionario manual, usamos la excepción nativa de FastAPI.

### Código proporcionado (POST):

Python

```
if type(search_user(user.id)) == User:
    raise HTTPException(status_code=404, detail="El usuario ya existe")
```

**Desglose:**

1. **`raise`**: En Python, esto detiene la ejecución inmediatamente. Es mejor que `return` porque corta el flujo en caso de error.
    
2. **`HTTPException`**: Es la clase que FastAPI usa para gestionar errores.
    
3. **`status_code`**: Define el número que recibirá el cliente.
    
    - _Nota:_ En tu código usaste 404 (Not Found), aunque para un "usuario que ya existe", lo semánticamente estricto sería un **409 Conflict** o **400 Bad Request**. Pero el mecanismo es el correcto: detener la ejecución y enviar un código de error 4xx.
        
4. **`detail`**: Es el mensaje que leerá el humano (el JSON `{"detail": "El usuario ya existe"}`).
    

---

## Lección 12.4: El Problema Pendiente (Refactorización)

Si observas tus funciones `PUT` y `DELETE` en el código, notarás que **todavía usan la forma antigua**:

Python

```
# En tu PUT actual
if not found:
    return {"error": "No se ha actualizado el usuario"} 
    # ¡CUIDADO! Esto devuelve status 200 OK aunque haya fallado.
```

### El Reto Profesional (Tu siguiente paso):

Para certificar que dominas esto, debes refactorizar `PUT`, `DELETE` y `GET (search_user)` para que dejen de usar `return {"error": ...}` y empiecen a usar `raise HTTPException`.

**Ejemplo de cómo debería quedar tu función `search_user`:**

Python

```
def search_user(id: int):
    users = filter(lambda user: user.id == id, users_list)
    try:
        return list(users)[0]
    except:
        # En lugar de return {"error"...}, lanzamos la excepción
        return {"error": "No se ha encontrado el usuario"} 
        # Esto debería cambiarse en la función que lo llama para lanzar un 404 real.
```

---

### Resumen de Códigos Clave para el Examen:

|**Código**|**Significado**|**Cuándo usarlo**|
|---|---|---|
|**200 OK**|Éxito genérico|Respuesta estándar para GET, PUT, DELETE.|
|**201 Created**|Creado|Solo cuando un POST crea un recurso nuevo con éxito.|
|**400 Bad Request**|Petición Mala|El cliente envió datos incompletos o inválidos.|
|**404 Not Found**|No Encontrado|El ID buscado no existe en la lista.|
|**500 Internal Error**|Error Servidor|Tu código Python falló (bug).|

