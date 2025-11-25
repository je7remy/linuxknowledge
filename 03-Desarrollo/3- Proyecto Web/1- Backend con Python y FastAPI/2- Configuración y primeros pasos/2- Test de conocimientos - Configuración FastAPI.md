
### 1. ¿Qué se recomienda hacer antes de pasar una API a producción?

_Seleccione solamente LA MEJOR respuesta_

- A. Instalarla en el servidor remoto sin validación
    
- **B. Probarla localmente antes de enviarla a producción** (Opción Correcta)
    
- C. Subirla directamente sin pruebas
    

_(Nota: Aunque la imagen cortó la explicación, la práctica estándar de DevOps y desarrollo seguro dicta que siempre se debe validar en un entorno local o de "staging" antes de producción)._

---

### 2. ¿Qué clase se utiliza para definir el contexto inicial de una aplicación FastAPI?

_Seleccione solamente LA MEJOR respuesta_

- A. La clase AppServer
    
- B. La clase BackendAPI
    
- **C. La clase FastAPI** (Seleccionada)
    

> Esta respuesta es correcta.
> 
> Se utiliza la clase FastAPI para crear el contexto inicial de la aplicación.

---

### 3. ¿Qué archivo se suele crear para iniciar una API con FastAPI?

_Seleccione solamente LA MEJOR respuesta_

- A. Un archivo llamado server.json
    
- B. Un archivo llamado index.html
    
- **C. Un archivo llamado main.py** (Seleccionada)
    

> Esta respuesta es correcta.
> 
> Se recomienda crear un archivo main.py como punto de entrada de la aplicación.

---

### 4. ¿Para qué sirve el comando pip install "fastapi[all]"?

_Seleccione solamente LA MEJOR respuesta_

- **A. Instala FastAPI y sus dependencias** (Seleccionada)
    
- B. Crea automáticamente un proyecto base
    
- C. Ejecuta el servidor local
    

> Esta respuesta es correcta.
> 
> Instala la librería FastAPI y sus dependencias para comenzar a desarrollar APIs.

---

### 5. ¿Qué permite hacer FastAPI en el entorno local?

_Seleccione solamente LA MEJOR respuesta_

- A. Crear bases de datos automáticamente
    
- **B. Levantar un servidor local para desarrollar y probar APIs** (Seleccionada)
    
- C. Desplegar directamente en producción sin pruebas
    

> Esta respuesta es correcta.
> 
> FastAPI permite levantar un servidor local para desarrollar y probar APIs antes de enviarlas a producción.

---
### 6. ¿Qué permite hacer el contexto inicial creado con `app = FastAPI()`?

_Seleccione solamente LA MEJOR respuesta_

- **A. Define el comportamiento del servidor ante peticiones** (Seleccionada)
    
- B. Conecta automáticamente con bases de datos
    
- C. Evita errores de sintaxis
    

> Esta respuesta es correcta.
> 
> La instrucción app = FastAPI() crea una instancia de la aplicación FastAPI. Esta instancia actúa como el núcleo del servidor web, permitiendo definir rutas, manejar peticiones HTTP, validar datos y generar documentación automática.

---

### 7. ¿Qué se recomienda hacer antes de pasar una API a producción?

_Seleccione solamente LA MEJOR respuesta_

- A. Instalarla en el servidor remoto sin validación
    
- **B. Probarla localmente antes de enviarla a producción** (Seleccionada)
    
- C. Subirla directamente sin pruebas
    

> Esta respuesta es correcta.
> 
> Probarla localmente levantando el servidor y verificando su funcionamiento.

---

### 8. ¿Dónde se recomienda instalar FastAPI en un proyecto?

_Seleccione solamente LA MEJOR respuesta_

- A. En la nube directamente
    
- **B. En una carpeta del backend para organizar el entorno** (Seleccionada)
    
- C. En la carpeta raíz del sistema operativo
    

> Esta respuesta es correcta.
> 
> En una carpeta específica del backend para organizar el entorno de desarrollo.

---

### 9. ¿Qué ocurre si no se instala FastAPI antes de importar la librería?

_Seleccione solamente LA MEJOR respuesta_

- A. Se instala automáticamente
    
- **B. El programa lanza error por no encontrar el módulo** (Seleccionada)
    
- C. Se ejecuta sin problemas
    

> Esta respuesta es correcta.
> 
> El programa lanzará un error porque no encuentra el módulo FastAPI (Error común: ModuleNotFoundError).

---

### 10. ¿Qué es Uvicorn en el contexto de FastAPI?

_Seleccione solamente LA MEJOR respuesta_

- A. Una librería para validar datos
    
- **B. Es el servidor que ejecuta aplicaciones FastAPI** (Seleccionada)
    
- C. Un sistema de control de versiones
    

> Esta respuesta es correcta.
> 
> Uvicorn es el servidor (ASGI) que ejecuta aplicaciones FastAPI, es rápido y permite recarga automática.

---

### 11. ¿Qué es PIP en el contexto de Python?

_Seleccione solamente LA MEJOR respuesta_

- A. Un editor de texto especializado para escribir código en Python
    
- B. Un protocolo de red utilizado para transferir archivos entre servidores
    
- **C. Un sistema de gestión de paquetes que permite instalar y administrar librerías en Python** (Seleccionada)
    

> Esta respuesta es correcta.
> 
> PIP (Pip Installs Packages) es la herramienta oficial para instalar y gestionar librerías externas (como FastAPI o Uvicorn).