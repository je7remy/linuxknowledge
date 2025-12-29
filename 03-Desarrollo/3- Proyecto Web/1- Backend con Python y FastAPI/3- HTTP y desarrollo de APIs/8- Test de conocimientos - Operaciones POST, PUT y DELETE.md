
### 1. ¿Qué diferencia principal hay entre PUT y POST en FastAPI?

- **A. PUT actualiza, POST crea** (Correcta)
    
- B. PUT crea, POST actualiza
    
- C. Ambos crean recursos nuevos
    

> Justificación:
> 
> PUT actualiza un recurso existente (lo reemplaza), mientras que POST se utiliza para crear uno nuevo.

---

### 2. En una operación PUT, ¿qué sucede si falta un campo obligatorio en el JSON enviado?

- **A. Error de validación con el campo faltante** (Correcta)
    
- B. Ignora el campo y sigue
    
- C. Completa el campo automáticamente
    

> Justificación:
> 
> FastAPI devuelve automáticamente un error de validación (HTTP 422) indicando cuál es el campo que falta según el modelo Pydantic definido.

---

### 3. ¿Qué decorador se usa al definir una operación para eliminar un recurso en FastAPI?

- **A. @app.delete("/")** (Correcta)
    
- B. @app.post("/")
    
- C. @app.patch("/")
    

> Justificación:
> 
> El decorador @app.delete vincula la función con el método HTTP DELETE, que es el estándar para la eliminación de recursos.

---

### 4. ¿Qué decorador se usa al definir una operación para crear un recurso en FastAPI?

- A. @app.get("/")
    
- **B. @app.post("/")** (Correcta)
    
- C. @app.route("/")
    

> Justificación:
> 
> El decorador @app.post indica que la función responde a una petición POST, utilizada para crear nuevos recursos.

---

### 5. ¿Qué decorador se usa al definir una operación para modificar un recurso completo en FastAPI?

- A. @app.route("/")
    
- B. @app.get("/")
    
- **C. @app.put("/")** (Correcta)
    

> Justificación:
> 
> El decorador @app.put indica que la función responde a una petición PUT, la cual se usa para reemplazar completamente un recurso.

---

### 6. ¿Cómo se pasa el ID del recurso a eliminar en una operación DELETE?

- A. En el cuerpo de la solicitud
    
- B. Como parámetro Query
    
- **C. Como parámetro Path en la URL** (Correcta)
    

> Justificación:
> 
> El estándar es pasar el identificador como parte de la ruta (Path Parameter), por ejemplo: /users/5.

---

### 7. ¿Qué tipo de datos espera FastAPI recibir en el body de una petición POST por defecto?

- **A. JSON con el modelo de datos** (Correcta)
    
- B. Texto plano
    
- C. Datos en formato XML
    

> Justificación:
> 
> FastAPI espera un JSON que cumpla con la estructura del modelo de datos (Pydantic) definido en la función.

---

### 8. ¿Cuál es el método HTTP recomendado para actualizar parcialmente un recurso en FastAPI?

- A. PUT
    
- **B. PATCH** (Correcta)
    
- C. POST
    

> Justificación:
> 
> Se utiliza PATCH cuando solo se quieren modificar algunos campos de un recurso sin enviar el objeto completo.

---

### 9. ¿Cuándo se utiliza una operación POST en una API?

- **A. Para crear o insertar nuevos datos** (Correcta)
    
- B. Para leer datos
    
- C. Para eliminar datos
    

> Justificación:
> 
> Se utiliza cuando la intención del cliente es crear una nueva entrada o insertar datos nuevos en el servidor.

---

### 10. En FastAPI, ¿qué sucede si envías datos en el body de una petición DELETE pero no se definen en la función?

- **A. Se ignoran los datos** (Correcta)
    
- B. Se actualiza el recurso
    
- C. Se devuelve un error
    

> Justificación:
> 
> Si la función de Python no declara un parámetro para recibir el cuerpo, FastAPI simplemente ignora cualquier dato extra enviado en el body de la petición DELETE, sin lanzar error.