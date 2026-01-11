
### 1. Según su clasificación, ¿para qué se utilizan los códigos de respuesta HTTP 3xx y 5xx?

- A. Éxito y Redirecciones
    
- B. Informativos y Éxito
    
- **C. Redirecciones y Errores del servidor** (Correcta)
    

> Justificación:
> 
> Los códigos 3xx indican Redireccionamiento (el recurso se movió), y los 5xx indican errores que se producen en el lado del servidor (fallo interno).

---

### 2. ¿Qué indica el código HTTP 200?

- **A. La operación fue exitosa** (Correcta)
    
- B. Hubo un error en el servidor
    
- C. Se creó un nuevo recurso
    

> Justificación:
> 
> 200 es el código estándar para indicar que la operación (generalmente una petición GET, PUT o DELETE) se completó con éxito.

---

### 3. ¿Qué hace la clase HTTPException en FastAPI?

- **A. Lanza errores personalizados con código y mensaje** (Correcta)
    
- B. Define modelos de respuesta
    
- C. Valida datos de entrada
    

> Justificación:
> 
> Permite detener la ejecución y lanzar errores controlados al cliente, especificando el código de estado (ej. 404) y el detalle del error.

---

### 4. ¿Qué ventaja tiene usar response_model en FastAPI?

- A. Define el tipo de error
    
- **B. Documenta el tipo de respuesta esperada** (Correcta)
    
- C. Valida los parámetros de entrada
    

> Justificación:
> 
> Permite documentar claramente qué tipo de objeto se devuelve en la respuesta y filtra automáticamente los datos que no pertenezcan al modelo.

---

### 5. ¿Cuándo se debería usar el código 409?

- A. Cuando falta contenido
    
- **B. Cuando hay un conflicto como duplicidad** (Correcta)
    
- C. Cuando el servidor no responde
    

> Justificación:
> 
> El código 409 (Conflict) se utiliza cuando la petición entra en conflicto con el estado actual del servidor, como intentar crear un usuario con un email que ya existe.

---

### 6. ¿Qué código indica que la operación fue exitosa pero no hay contenido para devolver?

- **A. 204 No Content** (Correcta)
    
- B. 200 OK
    
- C. 404 Not Found
    

> Justificación:
> 
> El 204 indica éxito, pero que la respuesta no tiene cuerpo (body). Es el estándar al eliminar recursos (DELETE) donde no hace falta devolver nada.

---

### 7. Según su clasificación, ¿para qué se utilizan los códigos de respuesta HTTP 2xx y 4xx?

- **A. Éxito y Errores del cliente** (Correcta)
    
- B. Informativos y Errores del servidor
    
- C. Redirecciones y Errores del servidor
    

> Justificación:
> 
> Los códigos 2xx indican que todo salió bien (Éxito), mientras que los 4xx indican que el cliente cometió un error (como enviar datos mal formados o pedir algo que no existe).

---

### 8. ¿Cuál es el código HTTP adecuado para indicar que se ha creado un recurso?

- A. 200 OK
    
- **B. 201 Created** (Correcta)
    
- C. 204 No Content
    

> Justificación:
> 
> El código 201 está diseñado específicamente para confirmar que una petición (usualmente POST) ha resultado en la creación exitosa de un nuevo recurso.

---

### 9. ¿Qué parámetro se usa para definir el código de estado por defecto en una operación?

- A. detail
    
- B. response_model
    
- **C. status_code** (Correcta)
    

> Justificación:
> 
> El parámetro status_code dentro del decorador de la ruta permite establecer qué código HTTP devolverá FastAPI si la función se ejecuta sin errores.

---

### 10. ¿Qué significa el código 404?

- A. Recurso creado exitosamente
    
- B. Error interno del servidor
    
- **C. Recurso no encontrado** (Correcta)
    

> Justificación:
> 
> Indica que el recurso solicitado (por ejemplo, un usuario con un ID específico) no fue encontrado en el servidor.