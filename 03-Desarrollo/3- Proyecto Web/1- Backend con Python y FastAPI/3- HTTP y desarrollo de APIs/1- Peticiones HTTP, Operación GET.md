
# Módulo 7: Verbos HTTP y la Operación GET

## Lección 7.1: El Lenguaje de las APIs REST

En el mundo de las APIs REST, la comunicación entre el Cliente (Frontend/Móvil) y el Servidor (Backend) se basa en **intenciones**. No le dices al servidor "haz la función X". Le dices: "Tengo la intención de **obtener** este recurso" o "Tengo la intención de **eliminar** este otro".

Para expresar esa intención, utilizamos los **Verbos o Métodos HTTP**.

### 1. El Ciclo de Vida de un Recurso (CRUD)

Cualquier sistema de información gestiona datos (recursos). En la industria, esto se conoce como **CRUD**:

- **C**reate (Crear)
    
- **R**ead (Leer)
    
- **U**pdate (Actualizar)
    
- **D**elete (Borrar)
    

HTTP nos da un método específico para cada una de estas acciones. Usarlos correctamente es lo que hace que tu API sea "RESTful" (que cumpla con los estándares de REST).

---

### 2. La Operación GET: "Solo Lectura"

La imagen destaca la operación **GET**. Es la más fundamental y la más utilizada en la web (es lo que hacen los navegadores por defecto).

#### **Definición Técnica:**

El método **GET** se utiliza para **solicitar una representación de un recurso específico**.

#### **Características Críticas para la Certificación:**

1. **Solo Lectura:** Una petición GET **NUNCA** debe modificar datos en el servidor. No borra, no crea, no edita. Solo mira.
    
2. **Segura (Safe):** Como no modifica nada, se considera una operación segura. Puedes ejecutarla mil veces sin miedo a romper la base de datos.
    
3. **Idempotente:** Si pides el mismo recurso 10 veces, deberías obtener el mismo resultado (asumiendo que nadie más lo ha cambiado).
    
4. **Cacheable:** Los navegadores y servidores pueden guardar (cachear) la respuesta de un GET para que la próxima vez sea más rápida.
    

> **⚠️ Regla de Oro Profesional:** Jamás envíes información sensible (como contraseñas) en los parámetros de una petición GET, ya que estos quedan registrados en el historial del navegador y en los logs del servidor.

---

### 3. Implementación en FastAPI (`@app.get`)

FastAPI hace que implementar este estándar sea extremadamente intuitivo mediante **decoradores**.

Analicemos la sintaxis:

Python

```
from fastapi import FastAPI

app = FastAPI()

# Decorador que define:
# 1. El método HTTP: .get (Leer)
# 2. La ruta (Path): "/usuarios"
@app.get("/usuarios")
async def obtener_usuarios():
    # Lógica para buscar en base de datos...
    return [{"id": 1, "nombre": "Ana"}, {"id": 2, "nombre": "Carlos"}]
```

Lo que le dice esto al servidor:

"Si alguien viene a la dirección /usuarios con la intención de LEER (GET), ejecuta la función obtener_usuarios y devuélvele la lista".

---

### 4. Diferencia entre Ruta y Método

Es vital entender que puedes tener la **misma ruta** pero con **diferentes métodos**. FastAPI sabrá qué función ejecutar basándose en el verbo HTTP.

Ejemplo conceptual:

- `GET /productos` -> Devuelve la lista de productos.
    
- `POST /productos` -> Crea un producto nuevo.
    

La URL es la misma, pero la **intención** (el método) cambia.

---

### Resumen de la Lección

- **HTTP:** Es el protocolo que define cómo se envían los mensajes en la web.
    
- **Métodos HTTP:** Definen la **intención** de la acción (Crear, Leer, Actualizar, Borrar).
    
- **GET:** Es el método para **obtener datos**.
    
    - No modifica el servidor.
        
    - Es la operación por defecto de los navegadores.
        
- **En FastAPI:** Se utiliza el decorador `@app.get("/ruta")`.
    

---

