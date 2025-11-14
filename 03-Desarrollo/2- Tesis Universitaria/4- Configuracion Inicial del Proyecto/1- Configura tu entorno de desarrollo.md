
### 1. Prerrequisitos (Software Esencial)

Antes de empezar, asegúrate de tener instalado este software en tu computadora:

- **Python (3.10 o superior):** El lenguaje de programación base.
    
- **VS Code (o tu editor preferido):** Para escribir el código.
    
- **Node.js y npm:** Necesarios para instalar y correr Tailwind CSS.
    
- **Docker:** Esta es la forma **más fácil y moderna** de correr tu base de datos PostgreSQL. En lugar de instalar PostgreSQL directamente en tu sistema (que puede ser complicado), lo correremos en un contenedor aislado.
    

---

### 2. Base de Datos (PostgreSQL con Docker)

Esta es la forma más rápida de tener una base de datos PostgreSQL limpia para tu proyecto.

1. Abre tu terminal.
    
2. Ejecuta este comando para descargar e iniciar una base de datos PostgreSQL en un contenedor de Docker:
    
    Bash
    
    ```
    docker run --name "citas-db" -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=admin -e POSTGRES_DB=citas_db -p 5432:5432 -d postgres
    ```
    

Este comando crea un contenedor llamado `"citas-db"` que se ejecuta en segundo plano (`-d`). Ya tienes una base de datos PostgreSQL corriendo en tu máquina con los siguientes datos:

- **Usuario:** `admin`
    
- **Contraseña:** `admin`
    
- **Base de Datos:** `citas_db`
    
- **Puerto:** `5432`
    

---

### 3. Estructura del Proyecto

Te recomiendo esta estructura de carpetas. Ve a tu terminal, crea una carpeta para tu proyecto y organízala así:

```
proyecto_citas/
├── .env                  # (Archivo para guardar contraseñas, lo crearemos)
├── main.py               # (Tu aplicación FastAPI principal)
├── database.py           # (Configuración de conexión de SQLAlchemy)
├── models.py             # (Modelos de la base de datos SQLAlchemy)
├── package.json          # (Dependencias de Tailwind)
├── tailwind.config.js    # (Configuración de Tailwind)
├── static/
│   ├── output.css        # (El CSS final que generará Tailwind)
│   └── input.css         # (El CSS de entrada para Tailwind)
└── templates/
    └── index.html        # (Tu archivo HTML principal)
```

---

### 4. Configuración del Backend (FastAPI + SQLAlchemy)

Ahora configuraremos la parte de Python.

1. **Abre la carpeta `proyecto_citas/` en VS Code.**
    
2. Abre una terminal dentro de VS Code (`Ctrl + ñ` o `Cmd + J`).
    
3. **Crea y activa un entorno virtual:**
    
    Bash
    
    ```
    # (Windows)
    python -m venv venv
    .\venv\Scripts\activate
    
    # (macOS/Linux)
    python3 -m venv venv
    source venv/bin/activate
    ```
    
    Verás `(venv)` al lado de tu nombre en la terminal.
    
4. **Instala las librerías de Python:**
    
    Bash
    
    ```
    pip install fastapi uvicorn sqlalchemy psycopg2-binary python-dotenv
    ```
    
    - **fastapi:** El framework.
        
    - **uvicorn:** El servidor que corre tu app.
        
    - **sqlalchemy:** El ORM (nuestro "pegamento" de base de datos).
        
    - **psycopg2-binary:** El "driver" que permite a Python hablar con PostgreSQL.
        
    - **python-dotenv:** Para leer el archivo `.env`.
        
5. Crea el archivo .env:
    
    Crea un nuevo archivo en la raíz llamado .env y pon la línea de conexión a tu base de datos Docker:
    
    ```
    DATABASE_URL="postgresql://admin:admin@localhost/citas_db"
    ```
    
    _Este archivo NUNCA debe subirse a un repositorio (agrégalo a `.gitignore` si usas Git)._
    

---

### 5. Configuración del Frontend (Tailwind CSS)

Finalmente, configuremos el frontend en la misma carpeta.

1. Inicializa Node.js y Tailwind:
    
    En la misma terminal (con venv aún activo), ejecuta:
    
    Bash
    
    ```
    # 1. Crea el archivo package.json
    npm init -y
    
    # 2. Instala Tailwind CSS
    npm install -D tailwindcss
    
    # 3. Crea el archivo de configuración de Tailwind
    npx tailwindcss init
    ```
    
2. Configura tailwind.config.js:
    
    Abre el archivo tailwind.config.js que se acaba de crear y modifícalo para que "observe" tus archivos HTML en la carpeta templates:
    
    JavaScript
    
    ```
    /** @type {import('tailwindcss').Config} */
    module.exports = {
      content: ["./templates/**/*.html"], // <-- ESTA LÍNEA ES CLAVE
      theme: {
        extend: {},
      },
      plugins: [],
    }
    ```
    
3. Configura el CSS de entrada:
    
    Ve a la carpeta static/ y crea el archivo input.css. Pega estas 3 líneas:
    
    CSS
    
    ```
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```
    
    Este es el archivo que Tailwind usará como base.
    
4. Genera el CSS de salida:
    
    Ejecuta este comando en tu terminal. Debes dejar esta terminal abierta mientras desarrollas tu frontend.
    
    Bash
    
    ```
    npx tailwindcss -i ./static/input.css -o ./static/output.css --watch
    ```
    
    - `--watch` le dice a Tailwind que vigile tus archivos `templates/*.html` y `input.css`. Cada vez que guardes un cambio y uses una clase de Tailwind (ej. `bg-blue-500`), ¡se compilará automáticamente en `output.css`!
        




---


### 1. `database.py` (El Conector de Base de Datos)

Este archivo crea la conexión a tu base de datos PostgreSQL y la "sesión" para hablar con ella.

Crea el archivo `database.py` y pega este código:

Python

```
import os
from dotenv import load_dotenv
from sqlalchemy import create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

# Carga la variable DATABASE_URL desde el archivo .env
load_dotenv()
DATABASE_URL = os.getenv("DATABASE_URL")

# Crea el "motor" de SQLAlchemy para conectarse a la base de datos
engine = create_engine(DATABASE_URL)

# Crea una "fábrica" de sesiones para hablar con la base de datos
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)

# Esta es la clase base que usarán tus modelos (Paciente, Medico, Cita)
Base = declarative_base()

# Función de Inyección de Dependencias
# Esto nos dará una sesión de base de datos limpia para cada petición
def get_db():
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()
```

---

### 2. `models.py` (Los Modelos de Datos)

Este archivo definirá cómo se ven tus datos. Por ahora, lo dejaremos simple, pero **es crucial crearlo** para que `main.py` pueda importarlo.

Crea el archivo `models.py` y pega este código (luego agregaremos los pacientes, médicos, etc.):

Python

```
from sqlalchemy import Column, Integer, String, DateTime, ForeignKey
from sqlalchemy.orm import relationship
from .database import Base

# Ejemplo de cómo se verá un modelo.
# Por ahora lo dejamos simple para que la app arranque.
# Más adelante agregaremos aquí las clases Paciente, Medico y Cita.

class Placeholder(Base):
    __tablename__ = "placeholder"
    id = Column(Integer, primary_key=True, index=True)
    name = Column(String, index=True)

# Aquí definirás tus modelos reales, por ejemplo:
# class Paciente(Base):
#     __tablename__ = "pacientes"
#     id = Column(Integer, primary_key=True, index=True)
#     nombre = Column(String)
#     cedula = Column(String, unique=True, index=True)
#     citas = relationship("Cita", back_populates="paciente")
```

---

### 3. `main.py` (Tu Aplicación Principal)

Este es el corazón de tu backend. Aquí crearás la app FastAPI, le dirás que cree las tablas en la base de datos y definirás tu primera ruta para cargar el frontend.

Crea el archivo `main.py` y pega este código:

Python

```
from fastapi import FastAPI, Request, Depends
from fastapi.templating import Jinja2Templates
from fastapi.staticfiles import StaticFiles
from sqlalchemy.orm import Session
from .database import engine, Base, get_db
from . import models

# --- Configuración Inicial ---

# 1. Crea las tablas en la base de datos
#    (basado en los modelos de models.py)
models.Base.metadata.create_all(bind=engine)

# 2. Crea la aplicación FastAPI
app = FastAPI()

# 3. "Monta" la carpeta "static"
#    Esto permite que el HTML cargue archivos como output.css
app.mount("/static", StaticFiles(directory="static"), name="static")

# 4. Configura Jinja2 para leer los archivos HTML de la carpeta "templates"
templates = Jinja2Templates(directory="templates")


# --- Endpoints (Rutas) ---

@app.get("/")
def get_root(request: Request):
    """
    Ruta principal que carga tu archivo index.html.
    """
    # El diccionario {"request": request} es necesario
    # para que Jinja2 funcione correctamente.
    return templates.TemplateResponse("index.html", {"request": request})

# Aquí es donde agregarás tus rutas de API, por ejemplo:
# @app.post("/api/pacientes")
# def crear_paciente(paciente: EsquemaPaciente, db: Session = Depends(get_db)):
#     # ...lógica para guardar en la base de datos...
#     return {"mensaje": "Paciente creado"}
```

---

### 4. `templates/index.html` (Tu Frontend)

Finalmente, vamos a probar que todo funcione. Crea `index.html` dentro de la carpeta `templates/` y pega este código.

Fíjate en dos cosas:

1. Cómo carga la hoja de estilos `/static/output.css`.
    
2. Cómo usa clases de **Tailwind CSS** (`bg-slate-900`, `text-3xl`, `p-10`).
    

HTML

```
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestión de Citas Médicas</title>
    <link href="/static/output.css" rel="stylesheet">
</head>
<body class="bg-slate-100">

    <div class="max-w-4xl mx-auto p-10 my-10 bg-white rounded-lg shadow-xl">
        
        <h1 class="text-3xl font-bold text-blue-700 mb-6">
            Sistema de Gestión de Citas
        </h1>
        
        <p class="text-gray-700">
            ¡Tu entorno de desarrollo está funcionando!
        </p>
        
        <div class="mt-8 p-4 bg-green-100 border border-green-300 rounded-md">
            <p class="font-semibold text-green-800">
                FastAPI, PostgreSQL y Tailwind CSS están conectados.
            </p>
        </div>

    </div>

</body>
</html>
```

### Cómo Ejecutar Todo

Ahora, solo necesitas **dos terminales** abiertas en la carpeta de tu proyecto:

1. **Terminal 1 (Frontend):** Compila tu Tailwind CSS y lo deja vigilando cambios.
    
    Bash
    
    ```
    npx tailwindcss -i ./static/input.css -o ./static/output.css --watch
    ```
    
2. **Terminal 2 (Backend):** Inicia tu servidor FastAPI (con `venv` activado).
    
    Bash
    
    ```
    # (Asegúrate de tener venv activado)
    uvicorn main:app --reload
    ```
    

Abre tu navegador en **`http://127.0.0.1:8000`**.

Si todo salió bien, deberías ver tu página `index.html` con los estilos de Tailwind aplicados, servida por tu backend de FastAPI y conectada a tu base de datos PostgreSQL.