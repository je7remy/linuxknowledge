
# Módulo 5: Documentación Automática e Interactiva

## Lección 5.1: Swagger UI, Redoc y el Estándar OpenAPI

En el desarrollo tradicional, mantener la documentación sincronizada con el código es una pesadilla. Cambias un parámetro en el código, pero olvidas actualizar el PDF o la Wiki. **FastAPI elimina este problema**. Al definir tus tipos de datos (Type Hints) y tus rutas, FastAPI genera la documentación por ti en tiempo real.

### 1. El Motor Secreto: OpenAPI

Antes de ver las interfaces gráficas, debes entender qué ocurre "bajo el capó".

FastAPI inspecciona tu código y genera automáticamente un **Esquema API** siguiendo el estándar **OpenAPI** (antes conocido como Swagger).

- **¿Qué es?** Es un archivo JSON enorme que describe tu API al detalle: rutas, parámetros, tipos de datos, seguridad, etc.
    
- **¿Dónde está?** Puedes verlo si vas a `http://127.0.0.1:8000/openapi.json`.
    

Las dos herramientas que veremos a continuación (Swagger UI y Redoc) no son más que programas que leen ese archivo JSON y lo convierten en una página web bonita.

---

### 2. Swagger UI: Tu Laboratorio de Pruebas (`/docs`)

Esta es la herramienta que utilizarás el 90% del tiempo mientras desarrollas.

- **URL:** `http://127.0.0.1:8000/docs`
    
- **Propósito:** Exploración y **Testing Interactivo**.
    

Cuando entras a esta URL, verás una interfaz interactiva. No es solo texto; es un cliente HTTP completo (como Postman) integrado en tu navegador.

#### **Características Clave:**

1. **Visualización de Endpoints:** Verás tus rutas (`/` y `/url`) codificadas por colores (Azul para GET, Verde para POST, etc.).
    
2. **Botón "Try it out" (Pruébalo):** Esta es la funcionalidad estrella.
    
    - Al hacer clic, se abre un formulario.
        
    - Si tu API requiriera parámetros, podrías escribirlos ahí.
        
    - Al dar clic en **Execute**, la página envía la petición real a tu servidor y te muestra la respuesta en vivo (código de estado 200, el JSON de respuesta, etc.).
        

> **Nota de Certificación:** Swagger UI es ideal para **desarrolladores** que necesitan probar y depurar la API mientras la construyen.

---

### 3. Redoc: Documentación Ejecutiva (`/redoc`)

FastAPI incluye una segunda opción por defecto, llamada **Redoc**.

- **URL:** `http://127.0.0.1:8000/redoc`
    
- **Propósito:** Lectura y documentación técnica limpia.
    

A diferencia de Swagger UI, Redoc está diseñado para ser extremadamente legible. Presenta la documentación en un formato de tres columnas o estructurado, ideal para ser entregado a clientes externos o equipos que van a consumir tu API pero no necesariamente probarla ahí mismo.

#### **Diferencias con Swagger:**

- **Estética:** Más moderna y limpia.
    
- **Interactividad:** Redoc es **estático**. No tiene el botón "Try it out". Sirve para leer y entender, no para ejecutar.
    

---

### 4. Práctica: Explorando tu API

Vamos a verificar esto con el código que escribimos en la lección anterior.

1. Asegúrate de que tu servidor esté corriendo:
    
    Bash
    
    ```
    uvicorn main:app --reload
    ```
    
2. Abre tu navegador y ve a `http://127.0.0.1:8000/docs`.
    
3. Verás una barra azul que dice `GET /url`. Haz clic en ella.
    
4. Haz clic en el botón gris **"Try it out"**.
    
5. Haz clic en el botón azul grande **"Execute"**.
    

**Lo que deberías ver:**

- **Code:** `200` (Éxito).
    
- **Response body:**
    
    JSON
    
    ```
    {
      "url": "https://mouredev.com/python"
    }
    ```
    

¡Acabas de hacer una petición a tu propia API sin escribir ni una línea de código en el frontend!

---

### Resumen de la Lección

|**Herramienta**|**URL**|**Uso Principal**|**Características**|
|---|---|---|---|
|**OpenAPI**|`/openapi.json`|Estándar Base|Es el JSON crudo que describe la API.|
|**Swagger UI**|`/docs`|Desarrollo / Test|Interactivo, permite ejecutar peticiones ("Try it out").|
|**Redoc**|`/redoc`|Lectura / Referencia|Diseño limpio, estático, ideal para leer la documentación.|

---
