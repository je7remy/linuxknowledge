
# Módulo 6: Herramientas de Prueba y Consumo de APIs

## Lección 6.1: Postman y Thunder Client

En el desarrollo profesional, no basta con que la API "funcione" en tu navegador. Necesitas simular peticiones complejas, guardar historiales de prueba y, a menudo, probar sin salir de tu entorno de código. En esta lección dominaremos las dos herramientas más utilizadas en la industria.

### 1. ¿Por qué no usar solo el navegador o Swagger?

El navegador (Chrome, Firefox) es excelente para peticiones **GET** (ver información), pero es muy malo para:

- Enviar datos (POST, PUT).
    
- Enviar cabeceras de autenticación (Tokens).
    
- Guardar un historial de pruebas para no escribir la URL cada vez.
    
- Automatizar pruebas.
    

Para esto usamos **Clientes API**.

---

### 2. Postman: El Estándar de la Industria

**Postman** es una aplicación independiente (stand-alone). Es la herramienta más popular del mundo para desarrollo de APIs.

#### **Características Clave:**

- **Colecciones:** Puedes guardar tus peticiones en carpetas (ej: "Usuarios", "Productos", "Auth") para mantener el orden.
    
- **Entornos (Environments):** Puedes definir variables. Por ejemplo, tener un entorno "Local" (`localhost:8000`) y uno "Producción" (`miapi.com`). Cambias de entorno con un clic sin reescribir las URLs.
    
- **Colaboración:** Permite compartir colecciones con tu equipo de trabajo.
    

#### **Flujo de Trabajo Típico:**

1. Abres la aplicación Postman.
    
2. Creas una "Nueva Petición" (New Request).
    
3. Seleccionas el método (GET, POST, etc.).
    
4. Pegas la URL: `http://127.0.0.1:8000/url`.
    
5. Presionas **Send** (Enviar).
    
6. Abajo verás la respuesta formateada (JSON bonito), el código de estado (200 OK) y el tiempo que tardó (ej. 15ms).
    

> **Nota de Certificación:** Postman es ideal para equipos de QA (Calidad) y para documentar APIs complejas externamente.

---

### 3. Thunder Client: Eficiencia dentro de VS Code

**Thunder Client** es una extensión para Visual Studio Code. Su filosofía es: _"¿Por qué salir del editor de código si solo quiero probar una ruta rápida?"_.

#### **Ventajas Principales:**

- **Ligero:** No consume tanta memoria RAM como Postman.
    
- **Integrado:** No tienes que hacer `Alt + Tab` para cambiar de ventana. Ves tu código y la prueba en la misma pantalla.
    
- **Git Friendly:** Puedes guardar tus pruebas dentro del proyecto y subirlas a Git para que tus compañeros las tengan automáticamente.
    

#### **Instalación y Uso:**

1. Ve a la pestaña de **Extensiones** en VS Code (cuadradito a la izquierda).
    
2. Busca "Thunder Client" y dale a Instalar.
    
3. Verás un icono de un **Rayo** ⚡ en tu barra lateral.
    
4. Haz clic en "New Request", escribe `http://127.0.0.1:8000` y dale a enviar.
    

---

### 4. Práctica: Tu primera prueba externa

Vamos a probar la API que creaste en la lección anterior (`/url`) usando Thunder Client (o Postman si prefieres).

**Pasos:**

1. **Asegúrate de que el servidor esté encendido:**
    
    Bash
    
    ```
    uvicorn main:app --reload
    ```
    
2. Abre Thunder Client (el Rayo ⚡).
    
3. Haz clic en **"New Request"**.
    
4. En la barra de direcciones, pon: `http://127.0.0.1:8000/url`
    
5. Asegúrate de que el método a la izquierda sea **GET**.
    
6. Haz clic en **Send**.
    

Análisis de la Respuesta:

A la derecha verás varios datos importantes que como profesional debes saber leer:

- **Status:** `200 OK` (La petición fue exitosa).
    
- **Time:** Ej. `4 ms` (Lo que tardó el servidor en responder. FastAPI es muy rápido).
    
- **Size:** Ej. `35 B` (El tamaño de los datos transferidos).
    
- **JSON:**
    
    JSON
    
    ```
    {
      "url": "https://mouredev.com/python"
    }
    ```
    

---

### Resumen Comparativo

|**Característica**|**Postman**|**Thunder Client**|
|---|---|---|
|**Tipo**|Aplicación Independiente|Extensión de VS Code|
|**Uso Ideal**|Proyectos grandes, Equipos, QA|Desarrollo rápido, Debugging, Solo devs|
|**Consumo**|Alto (es pesado)|Muy bajo (ligero)|
|**Curva de aprendizaje**|Media (muchas funciones)|Baja (muy intuitivo)|

---

