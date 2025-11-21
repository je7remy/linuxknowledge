
# **Módulo 3: Configuración del Entorno y Primer Despliegue**

## **Lección 3.1: Instalación y el Servidor ASGI**

Bienvenidos. Hasta ahora hemos hablado de teoría. En esta lección, prepararemos el "taller" donde construirás tus APIs. No se trata solo de instalar una librería; se trata de orquestar el entorno de ejecución que permitirá a Python hablar el lenguaje de la web moderna.

### **1. La Instalación: Más allá de un simple `pip`**

La diapositiva muestra el comando: `pip install "fastapi[all]"`. Analicemos esto con lupa profesional.

- **El Comando:** `pip install "fastapi[all]"`
    
- **¿Por qué las comillas?** En terminales como ZSH (común en Mac y Linux), los corchetes `[]` tienen significados especiales. Las comillas aseguran que `pip` reciba el texto literal.
    
- **¿Por qué `[all]`?**
    
    - Si solo instalas `fastapi`, obtienes el framework "desnudo".
        
    - Al usar `[all]`, estás instalando **FastAPI** más un conjunto de **dependencias opcionales estándar** recomendadas para producción y desarrollo, que incluyen:
        
        - **`uvicorn`**: El servidor web (vital, hablaremos de él en un segundo).
            
        - **`pydantic-settings`**: Para gestión de configuraciones.
            
        - **`httpx`**: Cliente HTTP para pruebas.
            
        - **`email-validator`**: Para validar correos en tus esquemas Pydantic.
            

> **Nota de Certificación:** En un entorno profesional, SIEMPRE debes trabajar dentro de un **Entorno Virtual** (`python -m venv venv`). Esto aísla las librerías de tu proyecto de las del sistema operativo.

---

### **2. El Motor: ¿Qué es Uvicorn?**

FastAPI no puede funcionar solo. Es solo un framework (un conjunto de reglas y herramientas). Necesita un servidor que exponga estas reglas al mundo.

Aquí entra **Uvicorn**.

- **Definición:** Uvicorn es un servidor **ASGI** (Asynchronous Server Gateway Interface).
    
- **La diferencia clave:** A diferencia de los servidores antiguos (WSGI) que manejaban una petición a la vez (bloqueantes), Uvicorn es **asíncrono**. Puede manejar miles de conexiones simultáneas esperando (awaiting) bases de datos o redes sin detenerse. Es lo que le da a FastAPI su velocidad de "rayo".
    

---

### **3. Anatomía del Comando de Ejecución**

Para encender tu API, utilizas el comando:

uvicorn main:app --reload

Desglosemos cada parte de esta línea, ya que es pregunta fija de examen:

1. **`uvicorn`**: Es el programa servidor que acabamos de instalar.
    
2. **`main`**: Hace referencia al **nombre de tu archivo Python** (el módulo). El servidor buscará un archivo llamado `main.py`. Si tu archivo se llamara `servidor.py`, escribirías `uvicorn servidor:app...`.
    
3. **`:` (dos puntos)**: Es el separador entre el archivo y el objeto dentro del archivo.
    
4. **`app`**: Es el nombre de la **instancia** de FastAPI dentro de tu código.
    
    - _En tu código tendrás:_ `app = FastAPI()`
        
5. **`--reload`**: Esta es la bandera de **"Hot Reload" (Recarga en caliente)**.
    
    - **Función:** Vigila tus archivos de código. Si guardas un cambio (Ctrl+S), el servidor se reinicia automáticamente en milisegundos.
        
    - **⚠️ Advertencia Profesional:** NUNCA uses `--reload` en un servidor de producción. Consume muchos recursos innecesarios. Es exclusivo para desarrollo.
        

---

### **4. Acceso y Verificación (El Dashboard)**

Una vez que el servidor arranca, verás en la terminal que está escuchando en:

http://127.0.0.1:8000

- **127.0.0.1**: Es la dirección "Loopback" o **Localhost**. Significa "esta misma computadora".
    
- **Port 8000**: Es el puerto estándar por defecto para desarrollo en Python/Uvicorn. (NodeJS suele usar 3000, Java 8080).
    

Tu primera prueba:

Si abres esa URL en tu navegador, y tu código base está listo, verás la respuesta JSON de tu API.

---

### **5. Ciclo de Vida: Detener el Servidor**

A veces, los desarrolladores novatos cierran la terminal completa para apagar el servidor. La forma correcta y elegante es:

- **Comando:** `CTRL + C`
    
- **Lo que sucede técnicamente:** Envías una señal `SIGINT` (Signal Interrupt) al proceso de Uvicorn. Esto permite que el servidor cierre las conexiones abiertas y termine los procesos de forma segura (Graceful Shutdown) antes de apagarse.
    

---

### **Resumen Práctico**

|**Acción**|**Comando / Concepto**|**Explicación**|
|---|---|---|
|**Instalar**|`pip install "fastapi[all]"`|Instala Framework + Servidor + Herramientas.|
|**Motor**|`Uvicorn`|Servidor ASGI de alto rendimiento.|
|**Arrancar**|`uvicorn main:app --reload`|Inicia el servidor en modo desarrollo.|
|**Visitar**|`http://127.0.0.1:8000`|Tu API viva en el puerto 8000.|
|**Apagar**|`CTRL+C`|Cierre seguro del proceso.|

---

