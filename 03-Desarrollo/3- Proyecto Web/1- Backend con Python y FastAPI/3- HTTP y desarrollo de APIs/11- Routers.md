---
tipo: teoria
tags: [fastapi]
actualizado: 2026-05-28
---

# Routers
# Módulo 13: Arquitectura Modular con APIRouter

## Lección 13.1: ¿Por qué usar Routers?

Imagina que tu aplicación crece y tienes usuarios, productos, pedidos, facturas y envíos. Si metes todo en `main.py`, tendrás un archivo de 5,000 líneas imposible de mantener.

**APIRouter** es la solución de FastAPI para esto. Funciona como una "mini aplicación" independiente que luego conectas a la aplicación principal. Te permite:

1. **Modularidad:** Separar la lógica por dominios (ej: un archivo para usuarios, otro para productos).
    
2. **Organización:** Mantener el código limpio y escalable.
    
3. **Colaboración:** Varios desarrolladores pueden trabajar en archivos distintos sin molestarse.
    

---

## Lección 13.2: Creando un Router (`users.py`)

Analicemos el primer bloque de código que compartiste. Ya no importamos `FastAPI`, sino `APIRouter`.

Python

```
from fastapi import APIRouter # <--- Cambio clave
from pydantic import BaseModel

router = APIRouter() # <--- Instanciamos el router, no la app

# ... (El resto del CRUD es idéntico al módulo anterior) ...

@router.get("/users") # Usamos @router en lugar de @app
async def users():
    return users_list
```

**Lo que debes saber para el examen:**

- Las funciones decoradas con `@router` no hacen nada por sí solas hasta que se conectan al archivo principal.
    
- La lógica interna (modelos Pydantic, listas, excepciones) funciona exactamente igual que antes.
    

---

## Lección 13.3: Prefijos y Etiquetas (`products.py`)

El segundo bloque de código introduce características avanzadas de `APIRouter` que son **pregunta de certificación**.

Python

```
router = APIRouter(
    prefix="/products",                     # 1. Prefijo Global
    tags=["products"],                      # 2. Etiqueta para Swagger
    responses={404: {"message": "No encontrado"}} # 3. Respuestas por defecto
)

@router.get("/") # <--- OJO AQUÍ
async def products():
    return products_list
```

**Desglose Técnico:**

1. **`prefix="/products"`**: Define una ruta base.
    
    - La ruta definida como `@router.get("/")` **se convierte automáticamente** en `GET /products/`.
        
    - La ruta `@router.get("/{id}")` se convierte en `GET /products/{id}`.
        
    - **Ventaja:** No tienes que escribir `/products` una y otra vez en cada endpoint.
        
2. **`tags=["products"]`**:
    
    - En Swagger UI, esto agrupará todos estos endpoints bajo un título bonito llamado "products".
        
3. **`responses={...}`**:
    
    - Define que _todos_ los endpoints de este router pueden devolver un 404 con ese formato. Es útil para estandarizar errores.
        

---

## Lección 13.4: El Ensamblaje (`main.py`)

Finalmente, tenemos el archivo que une todo. Es el punto de entrada de la aplicación.

Python

```
from fastapi import FastAPI
from routers import products, users # Importamos los archivos

app = FastAPI()

# La línea mágica:
app.include_router(products.router)
app.include_router(users.router)
```

**Método `include_router`:**

- Es el comando que "enchufa" las mini-aplicaciones al servidor principal.
    
- Sin esta línea, tus archivos `users.py` y `products.py` nunca serán vistos por el servidor.
    

---

### Resumen Visual de la Arquitectura

Así es como se ve ahora tu proyecto profesional:

Plaintext

```
📂 mi_proyecto
 ├── 📄 main.py          (El jefe: Solo conecta cosas)
 └── 📂 routers          (Carpeta organizada)
      ├── 📄 users.py    (Lógica de usuarios)
      └── 📄 products.py (Lógica de productos)
```

### Práctica Sugerida

Si ejecutas esto (`uvicorn main:app --reload`) y vas a la documentación (`/docs`), verás algo hermoso:

1. Los endpoints de **Users** estarán agrupados (si les agregas el tag).
    
2. Los endpoints de **Products** estarán en su propia sección.
    
3. La URL `/products/` funcionará aunque en el código solo pusiste `/`.

---

## Navegación

- ⬆️ Carpeta: [[_3- Proyecto Web|3- Proyecto Web]]
- ⬅️ Anterior: [[10- Test de conocimientos - HTTP status codes]]
- ➡️ Siguiente: [[12- Test de conocimientos - Routers]]
