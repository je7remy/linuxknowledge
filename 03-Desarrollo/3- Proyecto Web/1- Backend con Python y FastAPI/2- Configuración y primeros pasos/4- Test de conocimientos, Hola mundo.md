
### 1. ¿Para qué sirve el comando `pip install "fastapi[all]"`?

- **A. Instala FastAPI y sus dependencias** (Correcta)
    
- B. Crea automáticamente un proyecto base
    
- C. Ejecuta el servidor local
    

> Justificación:
> 
> Instala la librería FastAPI y sus dependencias para comenzar a desarrollar APIs.

---

### 2. ¿Qué archivo se suele crear para iniciar una API con FastAPI?

- A. Un archivo llamado server.json
    
- B. Un archivo llamado index.html
    
- **C. Un archivo llamado main.py** (Correcta)
    

> Justificación:
> 
> Se recomienda crear un archivo main.py como punto de entrada de la aplicación.

---

### 3. ¿Qué permite hacer FastAPI en el entorno local?

- A. Crear bases de datos automáticamente
    
- **B. Levantar un servidor local para desarrollar y probar APIs** (Correcta)
    
- C. Desplegar directamente en producción sin pruebas
    

> Justificación:
> 
> FastAPI permite levantar un servidor local para desarrollar y probar APIs antes de enviarlas a producción.

---

### 4. ¿Qué clase se utiliza para definir el contexto inicial de una aplicación FastAPI?

- A. La clase AppServer
    
- B. La clase BackendAPI
    
- **C. La clase FastAPI** (Correcta)
    

> Justificación:
> 
> Se utiliza la clase FastAPI para crear el contexto inicial de la aplicación.

---

### 5. ¿Qué se recomienda hacer antes de pasar una API a producción?

- A. Instalarla en el servidor remoto sin validación
    
- **B. Probarla localmente antes de enviarla a producción** (Correcta)
    
- C. Subirla directamente sin pruebas
    

> Justificación:
> 
> Probarla localmente levantando el servidor y verificando su funcionamiento.

---

### 6. ¿Dónde se recomienda instalar FastAPI en un proyecto?

- A. En la nube directamente
    
- **B. En una carpeta del backend para organizar el entorno** (Correcta)
    
- C. En la carpeta raíz del sistema operativo
    

> Justificación:
> 
> En una carpeta específica del backend para organizar el entorno de desarrollo.

---

### 7. ¿Qué ocurre si no se instala FastAPI antes de importar la librería?

- A. Se instala automáticamente
    
- **B. El programa lanza error por no encontrar el módulo** (Correcta)
    
- C. Se ejecuta sin problemas
    

> Justificación:
> 
> El programa lanzará un error porque no encuentra el módulo FastAPI.

---

### 8. ¿Qué permite hacer el contexto inicial creado con `app = FastAPI()`?

- **A. Define el comportamiento del servidor ante peticiones** (Correcta)
    
- B. Conecta automáticamente con bases de datos
    
- C. Evita errores de sintaxis
    

> Justificación:
> 
> La instrucción app = FastAPI() crea una instancia de la aplicación FastAPI. Esta instancia actúa como el núcleo del servidor web, permitiendo definir rutas, manejar peticiones HTTP, validar datos y generar documentación automática. Es el punto de partida para construir una API con FastAPI.

---

### 9. ¿Qué es PIP en el contexto de Python?

- A. Un editor de texto especializado para escribir código en Python
    
- B. Un protocolo de red utilizado para transferir archivos entre servidores
    
- **C. Un sistema de gestión de paquetes que permite instalar y administrar librerías en Python** (Correcta)
    

> Justificación:
> 
> PIP (Pip Installs Packages) es la herramienta oficial de Python para instalar, actualizar y gestionar paquetes externos. Permite incorporar librerías al entorno de desarrollo con comandos simples como pip install nombre_del_paquete.

---

### 10. ¿Qué es Uvicorn en el contexto de FastAPI?

- A. Una librería para validar datos
    
- **B. Es el servidor que ejecuta aplicaciones FastAPI** (Correcta)
    
- C. Un sistema de control de versiones
    

> Justificación:
> 
> Uvicorn es el servidor que ejecuta aplicaciones FastAPI, rápido y con recarga automática.