
### 1. ¿Qué es un router en FastAPI?

- **A. Un objeto que permite organizar y agrupar rutas (endpoints) de forma modular** (Correcta)
    
- B. Una instancia separada de FastAPI
    
- C. Un decorador para definir operaciones
    

> Justificación:
> 
> En FastAPI, un router es un objeto que permite organizar y agrupar rutas (endpoints) de forma modular. Básicamente, funciona como un "mini-API" dentro de tu aplicación principal.

---

### 2. ¿Qué clase se usa para definir un router en FastAPI?

- A. RouterManager
    
- B. FastAPI
    
- **C. APIRouter** (Correcta)
    

> Justificación:
> 
> La clase APIRouter permite crear routers independientes que luego se pueden sumar a la aplicación principal.

---

### 3. ¿Cuál es la ventaja de usar routers en FastAPI?

- A. Evita usar decoradores
    
- **B. Organiza el código y facilita la escalabilidad** (Correcta)
    
- C. Reduce el número de endpoints
    

> Justificación:
> 
> Permite dividir el código en módulos reutilizables (por ejemplo, un archivo para usuarios, otro para productos) y mantener la API escalable y mantenible.

---

### 4. ¿Qué archivo suele encargarse de incluir todos los routers en una app FastAPI?

- A. config.py
    
- B. routers.py
    
- **C. main.py** (Correcta)
    

> Justificación:
> 
> El archivo main.py suele ser el punto de entrada de la aplicación donde se instancia FastAPI() y se incluyen los routers externos.

---

### 5. ¿Qué método se usa para incluir un router en la aplicación principal?

- **A. include_router()** (Correcta)
    
- B. add_route()
    
- C. mount_router()
    

> Justificación:
> 
> El método app.include_router() es el comando que agrega las rutas definidas en el objeto router a la instancia principal de FastAPI.

---

### 6. ¿Por qué es útil separar routers por entidad (users, products, etc.)?

- **A. Mejora organización y mantenimiento** (Correcta)
    
- B. Evita errores de validación
    
- C. Reduce el uso de memoria
    

> Justificación:
> 
> La utilización de routers facilita el mantenimiento, la escalabilidad y la comprensión del código al separar lógicamente las funcionalidades.

---

### 7. ¿Qué efecto tiene el parámetro prefix en un router?

- **A. Agrupa las rutas bajo una misma URL base** (Correcta)
    
- B. Elimina la necesidad de usar decoradores
    
- C. Convierte las rutas en privadas
    

> Justificación:
> 
> Todas las rutas del router se agrupan bajo ese prefijo en la URL (ej. /users). Esto permite que no tengas que repetir el prefijo en cada endpoint individual (/users/create, /users/delete).

---

### 8. ¿Qué parámetro permite agrupar rutas en la documentación?

- A. group
    
- **B. tags** (Correcta)
    
- C. category
    

> Justificación:
> 
> El uso de tags=["nombre"] permite clasificar y agrupar visualmente las rutas en la documentación automática (Swagger UI), dejándola mucho más ordenada.

---

### 9. ¿Qué ocurre si no se incluye un router en la app principal?

- **A. Las rutas no se exponen en la API** (Correcta)
    
- B. Se lanza un error de importación
    
- C. Se duplican las rutas
    

> Justificación:
> 
> Definir el archivo del router no es suficiente; si no usas include_router en el main.py, esas rutas no estarán disponibles en el servidor y darán error 404 al intentar acceder a ellas.
> 
---

### 10. ¿Dónde se suele definir el prefijo de un router?

- A. En el archivo main.py
    
- B. En el decorador de cada ruta
    
- **C. En el parámetro prefix de APIRouter** (Correcta)
    

> Justificación:
> 
> Se define en el parámetro prefix al instanciar la clase APIRouter. De esta forma, todas las rutas que pertenezcan a ese router heredarán automáticamente esa base (ej. /users) sin tener que repetirla.