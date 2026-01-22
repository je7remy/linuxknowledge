
# Módulo 14: Recursos Estáticos y Protocolo HTTP Avanzado

## Lección 14.1: ¿Qué son los Recursos Estáticos?

Según la teoría de la certificación, los **recursos estáticos** son archivos que no cambian dinámicamente con cada petición.

- **Ejemplos:** Imágenes (`.png`, `.jpg`), hojas de estilo (`.css`), scripts (`.js`), documentos (`.pdf`).
    
- **Uso:** Son esenciales cuando quieres que tu servidor no solo sea una API de datos, sino que también entregue contenido visual o archivos complementarios.
    

---

## Lección 14.2: Implementación con `StaticFiles`

FastAPI no sirve archivos por defecto (por seguridad). Debemos configurarlo explícitamente. Analicemos la línea nueva en tu código `main.py`:

Python

```
from fastapi.staticfiles import StaticFiles # 1. Importación

# ... instanciación de app ...

# 2. La función de montaje
app.mount("/static", StaticFiles(directory="static"), name="static")
```

### Desglose Técnico para el Examen:

1. **`StaticFiles`**: Es la clase que gestiona la lógica de servir archivos de forma eficiente.
    
2. **`app.mount(...)`**: A diferencia de `include_router`, aquí usamos `mount` (montar).
    
    - **Concepto:** "Montar" significa agregar una aplicación completa e independiente (en este caso, una aplicación de archivos estáticos) dentro de una ruta específica de tu API.
        
3. **Parámetros:**
    
    - **`"/static"` (Path):** Es la URL donde estarán disponibles los archivos. Si tienes una imagen `foto.jpg` dentro de la carpeta, accederás a ella vía `http://tu-api/static/foto.jpg`.
        
    - **`directory="static"`**: Es el nombre real de la carpeta física en tu proyecto donde guardarás los archivos.
        
    - **`name="static"`**: Es el nombre interno para uso de FastAPI (útil para generar URLs inversas).
        

> **⚠️ Nota de Arquitectura:** Para que esto funcione, debes crear manualmente una carpeta llamada `static` en la raíz de tu proyecto y poner una imagen dentro.

---

## Lección 14.3: Cookies y Headers (Teoría)

La imagen introductoria también define dos conceptos críticos del protocolo HTTP que suelen caer en el examen teórico:

### A. Headers (Encabezados HTTP)

Son metadatos (campos clave-valor) que viajan en cada petición y respuesta, pero no son parte de los datos visibles (JSON).

- **Para qué sirven:** Contienen información sobre el tipo de contenido (`Content-Type`), autenticación (`Authorization: Bearer...`), idioma preferido, etc..
    

### B. Cookies

Son pequeños fragmentos de datos que el servidor envía al navegador.

- **Ciclo de vida:** El servidor la envía -> El navegador la guarda -> El navegador la reenvía automáticamente en futuras peticiones al mismo servidor.
    
- **Uso principal:** Mantener sesiones de usuario (saber quién eres sin que te loguees en cada clic), carritos de compra o preferencias.
    

---

### Resumen Práctico del Código

Tu archivo `main.py` ahora cumple tres funciones arquitectónicas:

1. **Orquestador:** Une los routers de `users` y `products`.
    
2. **Servidor de Archivos:** Expone la carpeta `/static` al mundo.
    
3. **API:** Tiene sus propios endpoints raíz (`/`) y (`/url`).
    

### Práctica Sugerida:

1. Crea una carpeta llamada `static` en tu proyecto.
    
2. Guarda una imagen dentro (ej. `logo.png`).
    
3. Ejecuta el servidor: `uvicorn main:app --reload`.
    
4. Abre en tu navegador: `http://127.0.0.1:8000/static/logo.png`. ¡Deberías ver la imagen!
    
