
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

---


# Módulo 12: Códigos de Estado HTTP y Manejo Profesional de Errores

## Lección 12.1: El Semáforo del Protocolo HTTP

El protocolo HTTP tiene un sistema universal de comunicación mediante números de tres dígitos. No importa si el cliente habla inglés, español o binario; todos entienden estos números.

Según las imágenes que has subido, debemos clasificar estos códigos en 5 familias:

1. **1xx (Informativos):** "Estoy pensando, espera".
2. **2xx (Éxito):** "¡Lo logré!". La petición fue recibida y procesada correctamente.
3. **3xx (Redirecciones):** "Lo que buscas se mudó a otro lado".
4. **4xx (Errores del Cliente):** "Tú (cliente) te equivocaste". (Ej: Pediste un ID que no existe o enviaste datos mal formados).
5. **5xx (Errores del Servidor):** "Yo (servidor) fallé". (Ej: Se cayó la base de datos o hay un bug en el código Python).

---

## Repaso 12.2: Definiendo el Éxito (Status Code 2xx)

No todos los éxitos son iguales. FastAPI nos permite ser específicos usando el parámetro `status_code` en el decorador.

### A. 200 OK

* **Significado:** La operación fue exitosa. Es el estándar para GET, PUT y respuestas genéricas.
* **Uso:** FastAPI lo usa por defecto si no especificas nada.

### B. 201 Created

* **Significado:** El recurso fue creado correctamente.
* **Uso:** Obligatorio en operaciones **POST** donde se genera un nuevo registro.
* **Implementación:**
```python
@app.post("/user/", status_code=201)  # <--- Aquí se define
async def create_user(user: User):
    ...

```



### C. 204 No Content

* **Significado:** La operación fue exitosa, pero **no hay contenido para devolver**.
* **Uso:** Ideal para **DELETE**. Cuando borras algo, no necesitas devolver el objeto borrado, solo confirmar que ya no existe.

---

## Lección 12.3: Gestión de Errores (4xx y HTTPException)

Aquí es donde elevamos la calidad del código. En lugar de devolver diccionarios con mensajes de error (`return {"error": ...}`), debemos **lanzar excepciones HTTP**.

FastAPI utiliza la clase `HTTPException` para detener la ejecución y enviar el código de error adecuado al cliente.

### A. 404 Not Found

* **Significado:** El recurso solicitado no existe en el servidor.
* **Uso:** Cuando buscas un usuario por ID y no está en la lista.

### B. 409 Conflict

* **Significado:** Hay un conflicto con el estado actual del recurso, como **duplicidad**.
* **Uso:** Cuando intentas crear un usuario con un ID o email que ya existe.

---

## Lección 12.4: Documentación de Respuesta (`response_model`)

Una pregunta clave que subiste menciona `response_model`.

* **Función:** Documenta el tipo de respuesta esperada y filtra los datos de salida.
* **Ventaja:** Si tu base de datos tiene un campo `password`, pero tu `response_model` no lo incluye, FastAPI lo quitará automáticamente antes de enviarlo al cliente. ¡Seguridad gratis!

---

## Lección 12.5: Práctica - Refactorización Profesional

Vamos a reescribir tu código anterior aplicando todo lo aprendido en estas imágenes. Observa cómo manejamos el `HTTPException` y los `status_code`.

```python
from fastapi import FastAPI, HTTPException, status
from pydantic import BaseModel

app = FastAPI()

# ... (Definición de clase User y users_list igual que antes) ...

# 1. GET: Usando status 200 (por defecto) y 404 si falla
@app.get("/user/{id}", status_code=status.HTTP_200_OK)
async def user(id: int):
    user_found = search_user(id)
    if not user_found:
        # LANZAMOS EXCEPCIÓN, NO RETORNAMOS UN JSON
        raise HTTPException(
            status_code=status.HTTP_404_NOT_FOUND, 
            detail="No se ha encontrado el usuario"
        )
    return user_found

# 2. POST: Usando status 201 (Created) y 409 (Conflict)
@app.post("/user/", response_model=User, status_code=status.HTTP_201_CREATED)
async def create_user(user: User):
    if search_user(user.id):
        # Usamos 409 para duplicados
        raise HTTPException(
            status_code=status.HTTP_409_CONFLICT,
            detail="El usuario ya existe"
        )
    
    users_list.append(user)
    return user

# 3. DELETE: Usando status 204 (No Content) o 404
@app.delete("/user/{id}", status_code=status.HTTP_204_NO_CONTENT)
async def delete_user(id: int):
    found = False
    for index, saved_user in enumerate(users_list):
        if saved_user.id == id:
            del users_list[index]
            found = True
            return # En 204 no se devuelve nada
            
    if not found:
        raise HTTPException(
            status_code=status.HTTP_404_NOT_FOUND,
            detail="No se ha eliminado el usuario"
        )

# Función auxiliar ajustada para devolver None si no encuentra
def search_user(id: int):
    users = filter(lambda user: user.id == id, users_list)
    try:
        return list(users)[0]
    except:
        return None

```

### Resumen de Estudio para Certificación

| Concepto | Código HTTP | Decorador / Herramienta |
| --- | --- | --- |
| **Éxito Genérico** | 200 OK | `@app.get("/", status_code=200)` |
| **Creación** | 201 Created | `@app.post("/", status_code=201)` |
| **Borrado (Sin datos)** | 204 No Content | `@app.delete("/", status_code=204)` |
| **No Encontrado** | 404 Not Found | `raise HTTPException(status_code=404)` |
| **Duplicado** | 409 Conflict | `raise HTTPException(status_code=409)` |
| **Filtrar Respuesta** | N/A | `response_model=User` en el decorador |

