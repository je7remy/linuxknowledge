---
tipo: teoria
tags: [fastapi]
actualizado: 2026-05-28
---

# Qué es un backend
# 🌐 Lección: Introducción al Frontend, Backend y FastAPI

## 📝 **Descripción ampliada**

En esta lección exploraremos los fundamentos esenciales del desarrollo web moderno. Para entender cómo funciona cualquier aplicación digital —desde una simple página web hasta plataformas complejas como Netflix o Amazon— es necesario comprender dos componentes clave: **el frontend** y **el backend**.

### 🔹 **Frontend**

El frontend es **todo lo que el usuario ve e interactúa**.  
Es la interfaz gráfica: botones, formularios, colores, animaciones, menús, etc.

Ejemplos comunes de frontend:

- Una página web de inicio de sesión
    
- El diseño visual de una tienda online
    
- Los controles de una app móvil
    

El frontend se ejecuta en el dispositivo del usuario (navegador, móvil, etc.) y su objetivo es ofrecer una **experiencia cómoda, intuitiva y atractiva**.

### 🔹 **Backend**

El backend es **el cerebro del sistema**, pero está oculto para el usuario.

Se ejecuta en servidores y se encarga de:

- Procesar datos
    
- Autenticar usuarios
    
- Comunicarse con bases de datos
    
- Ejecutar la lógica de negocio
    
- Enviar respuestas al frontend
    

Ejemplo: cuando envías un formulario para iniciar sesión, el backend verifica el usuario, revisa la base de datos y devuelve una respuesta.

### 🔹 **¿Cómo se comunican?**

A través de **APIs** (Application Programming Interfaces), normalmente usando HTTP o HTTPS.  
El frontend hace **peticiones**, el backend **responde**.

Ejemplo típico:

```
Frontend → (POST /login) → Backend  
Backend → (200 OK + token) → Frontend
```

---

## 🎯 En esta lección aprenderás:

### 1️⃣ **Qué es frontend y backend, y cómo se comunican**

Explicaremos:

- Qué tecnologías se usan en cada lado
    
- Cómo viajan los datos
    
- Qué es un endpoint
    
- Diferencias entre GET, POST, PUT, DELETE
    
- Flujo básico de una API REST:
    

```
Usuario → Frontend → Servidor Backend → Base de Datos → Backend → Frontend → Usuario
```

### 2️⃣ **Por qué Python es clave en el desarrollo moderno**

Python se ha convertido en un estándar global porque:

- Es fácil de aprender
    
- Tiene sintaxis clara
    
- Ofrece enorme cantidad de librerías
    
- Se usa en múltiples áreas:
    
    - Desarrollo web
        
    - Inteligencia artificial
        
    - Machine learning
        
    - Ciberseguridad
        
    - Automatización
        
    - Análisis de datos
        

En el backend es especialmente poderoso gracias a frameworks como:

- **FastAPI**
    
- **Django**
    
- **Flask**
    

### 3️⃣ **Por qué FastAPI es una opción actual y potente**

FastAPI es uno de los frameworks más modernos y eficientes para crear APIs en Python.

#### 🔥 Ventajas clave:

- **Extremadamente rápido** (similar a Node.js y Go)
    
- Basado en async/await (altísimo rendimiento)
    
- Documentación automática integrada con Swagger y ReDoc
    
- Fácil de escribir, fácil de mantener
    
- Validación automática de datos
    
- Ideal para microservicios y proyectos modernos
    

#### 🧩 Ejemplo básico en FastAPI:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"mensaje": "Hola, mundo!"}
```

Al iniciar el servidor, FastAPI genera automáticamente:

- `/docs` → Documentación interactiva estilo Swagger
    
- `/redoc` → Documentación alternativa muy completa
    

---

# 🧠 **Conclusión de la lección**

Al finalizar esta lección deberías comprender:

- La diferencia clara entre frontend y backend
    
- Cómo colaboran para crear aplicaciones completas
    
- El rol de Python en el ecosistema moderno del desarrollo
    
- Por qué FastAPI es considerado uno de los frameworks más sólidos, rápidos y actuales para construir servicios backend de alto nivel
    

---

---

## Navegación

- ⬆️ Carpeta: [[_3- Proyecto Web|3- Proyecto Web]]
- ➡️ Siguiente: [[3- Test de conocimientos, Qué es un backend]]
