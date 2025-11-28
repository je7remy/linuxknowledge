
### 1. ¿Qué especificación usa FastAPI para generar la documentación de Swagger y ReDoc?

- A. RAML
    
- **B. OpenAPI** (Correcta)
    
- C. GraphQL
    

> Justificación:
> 
> FastAPI genera documentación basada en el estándar OpenAPI, que es el estándar mundialmente aceptado para definir APIs REST.

---

### 2. ¿Qué propósito cumple Swagger UI en FastAPI?

- **A. Generar documentación interactiva para los endpoints** (Correcta)
    
- B. Ejecutar pruebas de rendimiento sobre la API
    
- C. Validar el esquema de la base de datos
    

> Justificación:
> 
> Swagger UI permite visualizar y, lo más importante, probar los endpoints (rutas) de la API directamente desde el navegador web.

---

### 3. ¿Qué endpoint suele mostrar la documentación generada por Swagger en FastAPI?

- **A. /docs** (Correcta)
    
- B. /swagger
    
- C. /documentation
    

> Justificación:
> 
> Por defecto, FastAPI expone la interfaz de Swagger UI en la ruta /docs (ej. http://localhost:8000/docs).

---

### 4. ¿Qué motor de documentación alternativa ofrece FastAPI además de Swagger UI?

- A. Postman
    
- **B. ReDoc** (Correcta)
    
- C. Insomnia
    

> Justificación:
> 
> ReDoc es una alternativa incluida por defecto que ofrece una presentación más estética y estructurada, ideal para la lectura técnica.

---

### 5. ¿Qué endpoint suele mostrar la documentación generada por ReDoc en FastAPI?

- A. /docs
    
- **B. /redoc** (Correcta)
    
- C. /documentation
    

> Justificación:
> 
> FastAPI aloja la interfaz de ReDoc en la ruta /redoc por defecto.

---

### 6. ¿Qué ventaja principal ofrece Swagger UI sobre ReDoc?

- A. Genera documentación en PDF
    
- B. Permite editar el código fuente
    
- **C. Permite probar endpoints** (Correcta)
    

> Justificación:
> 
> La característica clave de Swagger UI es el botón "Try it out", que permite enviar peticiones reales al servidor desde la documentación. ReDoc es estático (solo lectura).

---

### 7. ¿Qué ventaja principal ofrece ReDoc sobre Swagger UI?

- A. Permite ejecutar llamadas directamente desde la interfaz
    
- B. Soporta autenticación OAuth2
    
- **C. Tiene una interfaz más orientada a lectura y navegación** (Correcta)
    

> Justificación:
> 
> ReDoc organiza la documentación en un formato de tres columnas o jerárquico que facilita mucho la lectura y comprensión para desarrolladores externos o clientes.

---

### 8. ¿Qué tipo de información se incluye automáticamente en Swagger UI?

- A. Logs del servidor
    
- B. Métricas de uso de la API
    
- **C. Esquemas de validación, parámetros y respuestas** (Correcta)
    

> Justificación:
> 
> Swagger UI lee automáticamente los modelos de Pydantic y las rutas de FastAPI para mostrar qué datos se requieren (parámetros) y qué datos devuelve el servidor (respuestas).

---

### 9. ¿Qué parámetro permite cambiar la URL de ReDoc en FastAPI?

- A. redoc_path
    
- **B. redoc_url** (Correcta)
    
- C. redoc_endpoint
    

> Justificación:
> 
> Al crear la instancia de la aplicación, puedes personalizar la URL: app = FastAPI(redoc_url="/mi-nueva-ruta").

---

### 10. ¿Cómo se puede desactivar Swagger UI en FastAPI?

- **A. Configurando docs_url=None en el constructor de FastAPI** (Correcta)
    
- B. Usando docs=False en el decorador @app.get()
    
- C. Eliminando el archivo swagger.json
    

> Justificación:
> 
> Para ocultar la documentación (común en entornos de producción por seguridad), se instancia la app así: app = FastAPI(docs_url=None).