
### 1. ¿Qué significa la sigla HTTP?

- A. Hyperlink Text Transfer Protocol
    
- B. High-Tech Transfer Protocol
    
- **C. Hypertext Transfer Protocol** (Seleccionada)
    

> Justificación:
> 
> HTTP es el protocolo fundamental sobre el que se construyen las comunicaciones en la World Wide Web, permitiendo la transferencia de documentos como HTML.

---

### 2. ¿Qué método HTTP se usa por defecto al introducir una URL en el navegador?

- **A. GET** (Seleccionada)
    
- B. POST
    
- C. PUT
    

> Justificación:
> 
> El navegador realiza una petición GET al cargar una URL para recuperar el contenido de la página.

---

### 3. ¿Cuál es la principal función de una petición GET?

- A. Enviar nuevos datos para crear un recurso
    
- B. Eliminar un recurso del servidor
    
- **C. Recuperar información de un recurso** (Seleccionada)
    

> Justificación:
> 
> El propósito fundamental del método GET es recuperar una representación de un recurso específico sin causar ninguna modificación en el servidor.

---

### 4. ¿Qué método HTTP no modifica el estado del servidor?

- **A. GET** (Seleccionada)
    
- B. POST
    
- C. PUT
    

> Justificación:
> 
> GET es un método "seguro" que solo recupera información sin alterar, borrar o crear datos en el servidor.

---

### 5. ¿Qué método HTTP se usa para enviar datos al servidor?

- A. GET
    
- **B. POST** (Seleccionada)
    
- C. PUT
    

> Justificación:
> 
> POST permite enviar datos al servidor (generalmente en el cuerpo de la petición) para procesarlos o crear nuevos recursos.

---

### 6. ¿Qué método HTTP reemplaza completamente un recurso existente?

- **A. PUT** (Seleccionada)
    
- B. PATCH
    
- C. DELETE
    

> Justificación:
> 
> PUT se utiliza para actualizar un recurso sobrescribiéndolo por completo con los nuevos datos enviados. (A diferencia de PATCH, que sería una actualización parcial).

---

### 7. ¿Qué método HTTP se usa para eliminar un recurso?

- A. GET
    
- B. POST
    
- **C. DELETE** (Seleccionada)
    

> Justificación:
> 
> El método DELETE indica explícitamente que el recurso especificado en la URL debe ser eliminado del servidor.

---

### 8. ¿Qué es la paginación en una API?

- A. Ordenar los resultados alfabéticamente
    
- **B. Dividir una gran cantidad de resultados en bloques o páginas** (Seleccionada)
    
- C. Cifrar el contenido de la respuesta
    

> Justificación:
> 
> Cuando una petición puede devolver demasiados resultados (ej: /productos), la paginación los divide en fragmentos manejables ("página 1", "página 2") para mejorar el rendimiento y la usabilidad.

---

### 9. ¿Cuál es la principal ventaja del formato JSON sobre XML en las APIs?

- A. JSON puede representar datos más complejos
    
- **B. JSON es más ligero y fácil de procesar** (Seleccionada)
    
- C. Solo JSON es compatible con navegadores
    

> Justificación:
> 
> JSON es menos "verboso" (usa menos caracteres para decir lo mismo) que XML y su sintaxis de llave-valor es nativa para JavaScript y muy fácil de leer para humanos y máquinas.

---

### 10. ¿Cuál es el propósito de definir rutas como `/usuarios/productos`?

- **A. Organizar recursos relacionados** (Seleccionada)
    
- B. Evitar colisiones de nombres
    
- C. Mejorar el rendimiento
    

> Justificación:
> 
> Indica una jerarquía lógica: los productos pertenecen al usuario. Representa que los recursos hijos están relacionados directamente con el recurso padre.