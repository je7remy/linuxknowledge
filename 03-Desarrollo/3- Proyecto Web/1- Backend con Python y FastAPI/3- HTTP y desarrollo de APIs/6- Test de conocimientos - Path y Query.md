
# Fundamentos de FastAPI - Path y Query Parameters

### 1. ¿Para qué se usa un parámetro en el path en FastAPI?

- A) Enviar datos en el cuerpo del request.
    
- B) Definir encabezados HTTP.
    
- **C) Capturar valores desde la URL.**
    

> **Respuesta correcta: C.** Se utiliza para capturar valores directamente desde la URL, como por ejemplo, un ID de usuario.

---

### 2. ¿Cuál es la diferencia entre path y query en FastAPI?

- **A) Path es parte fija, query es opcional.**
    
- B) Ambos son obligatorios.
    
- C) Query se usa solo en POST.
    

> **Respuesta correcta: A.** El _path_ identifica un recurso específico en una ruta fija, mientras que los _query parameters_ son parámetros adicionales y generalmente opcionales.

---

### 3. Si la ruta es `/user/{id}`, ¿cómo accederías al usuario con id=3?

- **A) /user/3**
    
- B) /user?id=3
    
- C) /user&id=3
    

> **Respuesta correcta: A.** Al estar definido entre llaves `{id}`, se espera que el valor forme parte de la estructura de la ruta.

---

### 4. ¿Cómo se indica el inicio de los parámetros de query en una URL?

- **A) Con el signo de interrogación (?)**
    
- B) Con el signo de ampersand (&)
    
- C) Con una barra diagonal (/)
    

> **Respuesta correcta: A.** El signo `?` marca el final de la ruta del recurso y el comienzo de los parámetros de consulta.

---

### 5. ¿Qué operador se usa para concatenar múltiples parámetros en una query?

- A) ?
    
- **B) &**
    
- C) =
    

> **Respuesta correcta: B.** El ampersand (`&`) permite unir varios pares de clave=valor en la misma URL.

---

### 6. ¿Es posible combinar parámetros path y query en una misma operación?

- A) No, son excluyentes.
    
- **B) Sí, se pueden combinar.**
    
- C) Solo en peticiones POST.
    

> **Respuesta correcta: B.** FastAPI permite usar ambos simultáneamente para ofrecer mayor flexibilidad en las peticiones.

---

### 7. ¿Se puede usar el mismo nombre de endpoint para path y query?

- A) Solo si se usa POST.
    
- B) No, deben ser únicos.
    
- **C) Sí, si se diferencian por parámetros.**
    

> **Respuesta correcta: C.** Es posible siempre y cuando la estructura de recepción de parámetros permita al framework distinguir la solicitud.

---

### 8. ¿Qué sucede si un parámetro tipado como `int` recibe un valor que no es entero?

- **A) Devuelve error de validación 422.**
    
- B) Convierte automáticamente el valor a entero.
    
- C) Ignora el parámetro y sigue la ejecución.
    

> **Respuesta correcta: A.** FastAPI realiza validación de datos automática; si los tipos no coinciden, devuelve un error `422 Unprocessable Entity`.

---

