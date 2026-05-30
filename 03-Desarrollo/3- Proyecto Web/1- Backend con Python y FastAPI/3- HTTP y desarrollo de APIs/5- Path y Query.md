---
tipo: laboratorio
tags: [fastapi, path-parameters, query-parameters, crud]
actualizado: 2026-05-28
---

# Path y Query Parameters

# Módulo 10: Creación de API REST: Modelos, CRUD y Parámetros

## Lección 10.1: Fundamentos del Diseño REST y CRUD

Como vimos en la introducción teórica, una API profesional gestiona recursos (en este caso "Usuarios"). Para ello, mapeamos las operaciones de base de datos (**CRUD**) a los verbos **HTTP**.

- **GET**: Para **leer** recursos (ej. obtener lista de usuarios).
    
- **POST**: Para **crear** nuevos usuarios.
    
- **PUT**: Para **actualizar** un usuario completo.
    
- **PATCH**: Para actualizaciones parciales.
    
- **DELETE**: Para **eliminar** usuarios.
    

---

## Lección 10.2: Modelado de Datos con Pydantic

En lugar de trabajar con diccionarios sueltos, profesionalizamos el código usando `BaseModel` de Pydantic.

### Análisis del Código:

Python

```
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    surname: str
    url: str
    age: int
```

**¿Por qué hacemos esto?**

1. **Validación de Tipos:** Si intentas crear un usuario con `age="veinte"` (texto), Pydantic lanzará un error automático. Garantiza la integridad de los datos.
    
2. **Serialización Automática:** FastAPI convierte automáticamente estos objetos Python a **JSON** (que es más ligero y fácil de procesar que XML).
    

---

## Lección 10.3: Serialización Manual vs Automática

El código muestra dos formas de devolver datos. Esto es pregunta de examen para entender la potencia de FastAPI.

### A. La Forma Manual (No recomendada)

Python

```
@app.get("/usersjson")
async def usersjson():
    return [{"name": "Brais", ...}, ...]
```

- **Desventaja:** Debes escribir las claves manualmente. Si te equivocas en una letra (`"nme": "Brais"`), rompes la API. Es difícil de mantener.
    

### B. La Forma Profesional (Recomendada)

Python

```
@app.get("/users")
async def users():
    return users_list  # Devolvemos una lista de objetos User
```

- **Ventaja:** FastAPI lee la lista de objetos `User`, extrae sus datos y genera el JSON por ti. Es más seguro, limpio y permite autocompletado en el editor.
    

---

## Lección 10.4: Parámetros de Ruta (Path) vs Parámetros de Consulta (Query)

Esta es la parte más técnica del código proporcionado. FastAPI distingue entre estos dos tipos de parámetros basándose _únicamente_ en cómo declaras la ruta.

### 1. Path Parameters (Parámetros de Ruta)

Se usan para identificar un **recurso específico**. Son parte de la ruta.

- **Código:**
    
    Python
    
    ```
    @app.get("/user/{id}")  # Nota el {id} en la URL
    async def user(id: int):
        return search_user(id)
    ```
    
- **Uso:** El cliente llama a `http://127.0.0.1:8000/user/1`.
    
- **Lógica:** FastAPI extrae el `1` de la URL, valida que sea un entero y lo pasa a la función.
    
- **Cuándo usarlo:** Cuando el parámetro es esencial para encontrar el recurso (ej. el ID de un usuario).
    

### 2. Query Parameters (Parámetros de Consulta)

Se usan para **filtrar**, ordenar o paginar resultados.

- **Código:**
    
    Python
    
    ```
    @app.get("/user/")  # ¡No hay {id} en la URL!
    async def user(id: int): # Pero la función pide 'id'
        return search_user(id)
    ```
    
- **Comportamiento Mágico:** Como `id` está en la función pero **NO** en el decorador de ruta (`/user/`), FastAPI asume automáticamente que es un **Query Parameter**.
    
- **Uso:** El cliente llama a `http://127.0.0.1:8000/user/?id=1`.
    
- **Cuándo usarlo:** Para parámetros opcionales, filtros o configuraciones (como paginación).
    

---

## Lección 10.5: Lógica de Negocio (Función de Búsqueda)

Finalmente, el código implementa una función auxiliar para no repetir lógica:

Python

```
def search_user(id: int):
    # Filtra la lista buscando el ID
    users = filter(lambda user: user.id == id, users_list)
    try:
        return list(users)[0]
    except:
        return {"error": "No se ha encontrado el usuario"}
```

Esta función encapsula la búsqueda. Si encuentra al usuario, devuelve el objeto (que FastAPI convertirá a JSON). Si no, devuelve un diccionario con un mensaje de error.

> **Nota Pro:** En el siguiente nivel, reemplazaremos ese `return {"error": ...}` por una `HTTPException` para devolver códigos de estado reales (como 404 Not Found) en lugar de un 200 OK con un mensaje de error.

---

### Resumen de Conceptos Clave para la Certificación:

1. **JSON vs XML:** Usamos JSON porque es más ligero y nativo para la web.
    
2. **Jerarquía:** Rutas como `/usuarios/productos` organizan recursos relacionados.
    
3. **Path Param:** `/user/{id}` -> Identifica recursos únicos.
    
4. **Query Param:** `/user/?id=1` -> Filtra u ordena resultados.
    
5. **Pydantic:** Define la estructura (`BaseModel`) y valida los datos automáticamente.


---

# 📌 **DESGLOSE COMPLETO DEL ARCHIVO**

---

# 1. **Imports**

```python
from fastapi import FastAPI
from pydantic import BaseModel
```

✔ `FastAPI` → sirve para crear la aplicación web, definir rutas, endpoints, etc.  
✔ `BaseModel` → sirve para definir modelos de datos con validación automática.

---

# 2. **Inicializar la aplicación**

```python
app = FastAPI()
```

✔ Crea la instancia principal de FastAPI.  
Aquí es donde se registran todas las rutas/endpoints.

---

# 3. **Modelo de datos User**

```python
class User(BaseModel):
    id: int
    name: str
    surname: str
    url: str
    age: int
```

✔ `BaseModel` convierte datos automáticamente a su tipo correcto.  
✔ Cada campo tiene un tipo: `int`, `str`, etc.  
✔ Permite que FastAPI valide datos automáticamente al recibir peticiones POST o PUT.

---

# 4. **Lista de usuarios simulando una base de datos**

```python
users_list = [
    User(id=1, name="Brais", surname="Moure", url="https://moure.dev", age=35),
    User(id=2, name="Moure", surname="Dev", url="https://mouredev.com", age=35),
    User(id=3, name="Brais", surname="Dahlberg", url="https://haakon.com", age=33)
]
```

✔ `users_list` es una **lista de objetos User**.  
✔ Se usa como "base de datos" en memoria.  
✔ Cada User es un objeto validado por Pydantic.

---

# 5. **Endpoint /usersjson**

```python
@app.get("/usersjson")
async def usersjson():
    return [{"name": "Brais", "surname": "Moure", "url": "https://moure.dev", "age": 35},
            {"name": "Moure", "surname": "Dev", "url": "https://mouredev.com", "age": 35},
            {"name": "Haakon", "surname": "Dahlberg", "url": "https://haakon.com", "age": 33}]
```

✔ Devuelve una **lista de diccionarios**, NO objetos `User`.  
✔ Ejemplo simplificado.  
✔ No usa `User`, pero es válido.

---

# 6. **Endpoint /users**

```python
@app.get("/users")
async def users():
    return users_list
```

✔ Devuelve la lista de `User`.  
✔ FastAPI convierte cada objeto `User` a JSON automáticamente.  
✔ Ideal y correcto.

---

# 7. **Endpoint con parámetro en el PATH**

```python
@app.get("/user/{id}")
async def user(id: int):
    return search_user(id)
```

✔ `/{id}` significa que si llamas a `/user/2`, FastAPI toma `2` como int.  
✔ Llama a `search_user(id)`.

**PROBLEMA IMPORTANTE:**  
La función se llama `user` pero más abajo hay OTRA función con el MISMO NOMBRE.

---

# 8. **Endpoint con parámetro en QUERY**

```python
@app.get("/user/")
async def user(id: int):
    return search_user(id)
```

✔ Aquí el usuario lo pasa así:

```
/user/?id=2
```

**PROBLEMA GRAVE:**  
Esta función **sobrescribe** la función anterior con el mismo nombre `user`.

Esto no quiebra FastAPI porque registró la ruta antes, pero:

⚠ **A nivel de Python, la función anterior queda reemplazada.**  
⚠ Es una muy mala práctica.

---

# 9. **Función search_user**

```python
def search_user(id: int):
    users = filter(lambda user: user.id == id, users_list)
    try:
        return list(users)[0]
    except:
        return {"error": "No se ha encontrado el usuario"}
```

Ahora sí, vamos a desglosarla en detalle:

---

## 🔵 Paso 1 — Filtrado

```python
users = filter(lambda user: user.id == id, users_list)
```

- `filter` recorre `users_list`
    
- Toma **solo** los usuarios donde `user.id == id`
    
- `filter` NO devuelve una lista, sino un **iterador** (lazy)
    

Ejemplo:  
Si `id = 2` → el filtro devuelve un iterador con un solo User.

---

## 🔵 Paso 2 — Convertir iterador a lista

```python
list(users)
```

⚠ Convierte todo el iterador en una lista.

Si hay coincidencia → la lista tiene ese usuario.  
Si NO hay coincidencia → la lista queda vacía `[]`.

---

## 🔵 Paso 3 — Intentar obtener el primer elemento

```python
list(users)[0]
```

Esto puede causar un error:

- si la lista tiene 1 elemento → OK
    
- si la lista está vacía → `IndexError`
    

---

## 🔵 Paso 4 — Manejar errores con `try/except`

```python
try:
    return list(users)[0]
except:
    return {"error": "No se ha encontrado el usuario"}
```

Si ocurre **cualquier error**, devuelve un mensaje:

```json
{"error": "No se ha encontrado el usuario"}
```

⚠ **PROBLEMA:**  
El `except:` es demasiado genérico.  
Podrías ocultar errores reales.

---

# 📌 PROBLEMAS DEL CÓDIGO COMPLETO

1. ❌ Dos funciones con el mismo nombre `user`
    
2. ❌ `except:` demasiado genérico
    
3. ❌ Se convierte el `filter` completo a lista (ineficiente)
    
4. ❌ `search_user` debería devolver un 404 con `HTTPException`
    
5. ❌ No se usa `next()` que es más eficiente
    
6. ❌ No se separan responsabilidades
    
7. ❌ Demasiada lógica dentro del `except`
    

---

# 📌 Versión corregida y profesional

```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

class User(BaseModel):
    id: int
    name: str
    surname: str
    url: str
    age: int

users_list = [
    User(id=1, name="Brais", surname="Moure", url="https://moure.dev", age=35),
    User(id=2, name="Moure", surname="Dev", url="https://mouredev.com", age=35),
    User(id=3, name="Brais", surname="Dahlberg", url="https://haakon.com", age=33)
]

def search_user(id: int):
    user = next((u for u in users_list if u.id == id), None)
    if not user:
        raise HTTPException(status_code=404, detail="Usuario no encontrado")
    return user

@app.get("/user/{id}")
async def get_user_by_path(id: int):
    return search_user(id)

@app.get("/user/")
async def get_user_by_query(id: int):
    return search_user(id)
```

---

## Navegación

- ⬆️ Carpeta: [[_3- Proyecto Web|3- Proyecto Web]]
- ⬅️ Anterior: [[4- Test de conocimientos - Creación API]]
- ➡️ Siguiente: [[6- Test de conocimientos - Path y Query]]
