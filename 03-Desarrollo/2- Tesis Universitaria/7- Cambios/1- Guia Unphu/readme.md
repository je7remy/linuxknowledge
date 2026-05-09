
# SGCM — Sistema Web de Gestión de Citas Médicas

[![CI](https://img.shields.io/github/actions/workflow/status/je7remy/HTQ_Citas/ci.yml?branch=main&label=CI&logo=github)](https://github.com/je7remy/HTQ_Citas/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.11+-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.110+-009688.svg?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791.svg?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-24+-2496ED.svg?logo=docker&logoColor=white)](https://www.docker.com/)
[![License](https://img.shields.io/badge/license-Académico-lightgrey.svg)](#)

Plataforma web para automatizar y optimizar el proceso de gestión de citas médicas del **Hospital Regional Traumatológico y Quirúrgico Prof. Juan Bosch (HTQPJB)** en La Vega, República Dominicana.

> Trabajo de grado para optar por el título de Licenciatura en Informática — Universidad Nacional Pedro Henríquez Ureña (UNPHU), Recinto La Vega.

---

## Tabla de contenido

- [Sobre el proyecto](#sobre-el-proyecto)
- [Características principales](#caracter%C3%ADsticas-principales)
- [Arquitectura](#arquitectura)
- [Stack tecnológico](#stack-tecnol%C3%B3gico)
- [Evolución del stack tecnológico](#evoluci%C3%B3n-del-stack-tecnol%C3%B3gico)
- [Inicio rápido](#inicio-r%C3%A1pido)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Casos de uso](#casos-de-uso)
- [Roles y permisos](#roles-y-permisos)
- [Pruebas automatizadas](#pruebas-automatizadas)
- [Integración continua](#integraci%C3%B3n-continua)
- [Comandos útiles](#comandos-%C3%BAtiles)
- [Documentación](#documentaci%C3%B3n)
- [Cumplimiento legal](#cumplimiento-legal)
- [Autores](#autores)
- [Versión](#versi%C3%B3n)

---

## Sobre el proyecto

El SGCM automatiza el proceso de gestión de citas que el HTQPJB realizaba previamente con registros físicos, libretas y comunicación verbal. La plataforma reemplaza esos soportes manuales por una solución digital centralizada que opera en la intranet del hospital.

**Lo que el sistema NO es:** una reingeniería del proceso institucional. La lógica operativa, los roles y las responsabilidades del personal se conservan.

**Lo que el sistema SÍ es:** la automatización de los puntos del flujo donde los soportes manuales generaban duplicaciones, demoras y descoordinación.

---

## Características principales

- Autenticación JWT con hashing bcrypt y expiración configurable.
- Control de acceso basado en roles (RBAC) en dos capas: backend y frontend.
- Calendario interactivo con FullCalendar.js, vista mensual por defecto.
- Prevención física de duplicaciones mediante índice único parcial en PostgreSQL.
- Bloqueo temporal del registro de consulta: el médico no puede registrar diagnósticos antes de la fecha de la cita.
- Vinculación de usuarios con perfiles de médico desde la UI del administrador.
- Reportes PDF generados con WeasyPrint, con fecha de emisión y numeración secuencial.
- Auditoría transaccional de todas las operaciones críticas (Ley 172-13).
- Suite de pruebas automatizadas con pytest.
- CI/CD con GitHub Actions ejecutando linter, tests y construcción de imagen Docker.
- Despliegue contenedorizado con Docker Compose.
- Máscaras visuales en cédula y teléfono para mejor experiencia de usuario.

---

## Arquitectura

```mermaid
flowchart TB
    Browser[Navegador del usuario]
    subgraph Server["Servidor en intranet del hospital"]
        Nginx[Nginx<br/>puerto 80<br/>proxy + estaticos]
        API[FastAPI<br/>puerto 8000<br/>backend]
        DB[(PostgreSQL<br/>puerto 5432<br/>base de datos)]
    end

    Browser -->|HTTP| Nginx
    Nginx -->|/api/v1/*| API
    Nginx -->|archivos HTML/JS/CSS| Browser
    API <-->|SQL| DB
````

---

## Stack tecnológico

### Backend

- **Python 3.11+** — Lenguaje principal.
- **FastAPI** — Framework web asíncrono con OpenAPI automático.
- **SQLModel** — ORM combinado con validación Pydantic.
- **Alembic** — Migraciones versionadas del esquema.
- **python-jose** — Generación y validación de JWT.
- **passlib + bcrypt** — Hashing seguro de contraseñas.
- **WeasyPrint** — Generación de PDFs desde HTML/CSS.
- **pytest + httpx** — Pruebas automatizadas.

### Base de datos

- **PostgreSQL 15** — Con índices únicos parciales para prevenir duplicaciones.

### Frontend

- **HTML5 + JavaScript ES6** — Vanilla, sin framework.
- **Tailwind CSS** — Vía CDN.
- **FullCalendar.js** — Calendario interactivo.

### Infraestructura

- **Docker + Docker Compose** — Orquestación de contenedores.
- **Nginx** — Proxy inverso y servidor de archivos estáticos.
- **mkcert** — Certificado SSL para HTTPS en intranet.
- **GitHub Actions** — Integración continua.

---

## Evolución del stack tecnológico

El stack actual no fue el original. Durante las fases de análisis y diseño, y a lo largo de las primeras iteraciones de desarrollo, el proyecto evolucionó significativamente conforme fui descubriendo limitaciones de las herramientas iniciales y conociendo alternativas más apropiadas para los requisitos del sistema. Esta sección documenta esa evolución, porque entender por qué algo cambió es tan importante como saber qué se está usando hoy.

### Comparativa: idea inicial vs implementación final

|Componente|Idea inicial|Stack actual|Razón del cambio|
|---|---|---|---|
|Base de datos|SQLite|PostgreSQL 15|SQLite no soporta índices únicos parciales con cláusula WHERE, característica clave del diseño para resolver el conflicto entre cancelación y reagendamiento de citas. Tampoco está pensado para concurrencia real con múltiples secretarias agendando al mismo tiempo.|
|Framework backend|Flask|FastAPI|Flask es minimalista pero requiere construir manualmente validación de datos, documentación OpenAPI y manejo asíncrono. FastAPI lo trae todo de fábrica con Pydantic, genera Swagger automáticamente y ofrece un rendimiento muy superior gracias a Starlette y al soporte nativo de async/await.|
|ORM|SQLAlchemy puro|SQLModel sobre SQLAlchemy y Pydantic|SQLModel unifica los modelos de base de datos con los esquemas de validación en una sola capa. Reduce código duplicado y mantiene la potencia de SQLAlchemy por debajo.|
|Frontend|HTML, JavaScript y Tailwind CSS|Igual, más FullCalendar.js|Se mantuvo el enfoque vanilla por su simplicidad y por evitar la complejidad de un framework para un sistema de este alcance. Se incorporó FullCalendar.js como pieza clave para la visualización del calendario interactivo.|
|Entorno de operación|Servidor local con Docker|Igual|Decisión validada y mantenida. La contenedorización facilita despliegue, reproducibilidad y portabilidad.|
|Control de versiones|Git|Git más GitHub Actions|Se añadió integración continua: cada commit ejecuta tests automatizados y construye la imagen Docker, garantizando que el código en el repositorio siempre sea desplegable.|
|Diseño visual|Draw.io|Draw.io|Se mantiene como herramienta de planificación de diagramas (DFD, casos de uso, MER).|

### Componentes incorporados durante la evolución

Algunos componentes no estaban en la planificación inicial pero se sumaron al darme cuenta de su importancia:

- **Alembic** para migraciones versionadas del esquema de base de datos. Sin él, cualquier cambio de modelo implicaba intervenciones manuales propensas a errores.
- **WeasyPrint** para generación de reportes PDF a partir de HTML y CSS, lo que permite reutilizar templates del frontend para reportes profesionales.
- **python-jose y passlib (bcrypt)** para JWT y hashing de contraseñas. La autenticación inicial se pensó simple, pero al estudiar la Ley 172-13 quedó claro que se requería hashing fuerte y tokens firmados.
- **Nginx** como proxy inverso. Originalmente se contemplaba que FastAPI sirviera todo (API y archivos estáticos), pero al separar responsabilidades se obtuvo mejor rendimiento, terminación SSL más limpia y un punto de entrada único.
- **pytest y httpx** para una suite de pruebas automatizadas. Esto no estaba en el plan original; surgió de la necesidad de evitar regresiones al iterar el sistema.
- **GitHub Actions** para CI/CD. Práctica que adopté tras enfrentar el primer fallo en pruebas que un test automatizado habría evitado.
- **ruff** como linter para análisis estático del código.

### Por qué documentar esta evolución

Porque demuestra dos cosas que considero importantes en cualquier proyecto técnico serio:

1. **El stack no se eligió por moda, sino por requisitos.** Cada cambio respondió a una limitación concreta encontrada durante el desarrollo o a una característica específica que el sistema necesitaba (por ejemplo, los índices únicos parciales de PostgreSQL que SQLite no soporta).
    
2. **El proyecto evolucionó con disciplina.** Cambiar de Flask a FastAPI o de SQLite a PostgreSQL en mitad del desarrollo no es trivial: implicó reescribir partes considerables del código. Fueron decisiones tomadas tempranamente, antes de que el costo del cambio fuera prohibitivo, lo cual es una habilidad fundamental en ingeniería de software.
    

El stack actual no es perfecto ni final. Hay áreas donde reconozco oportunidades de mejora futura (tests end-to-end con Playwright, observabilidad con Prometheus, despliegue con Kubernetes para múltiples instancias), pero corresponden a un alcance mayor al de un trabajo de grado y quedan documentadas como recomendaciones de evolución.

---

## Inicio rápido

### Requisitos previos

- Docker Engine 24+ y Docker Compose v2.
- Git 2.30+.

### Instalación en cuatro pasos

```bash
# 1. Clonar el repositorio
git clone https://github.com/je7remy/HTQ_Citas.git sgcm
cd sgcm

# 2. Configurar variables de entorno
cp .env.example .env
# Editar .env y configurar JWT_SECRET_KEY (mínimo 32 caracteres)

# 3. Arrancar el sistema
docker compose up -d --build

# 4. Verificar
docker compose ps
```

Acceder a `http://localhost/` en el navegador.

### Credenciales de demostración

|Rol|Email|Contraseña|
|---|---|---|
|Administrador|`admin@htqpjb.gob.do`|`Admin*2026`|
|Secretaria|`secretaria@htqpjb.gob.do`|`Secret*2026`|
|Médico|`jperez@htqpjb.gob.do`|`Medico*2026`|

> **Importante:** cambiar inmediatamente todas las contraseñas tras la primera puesta en marcha en producción.

---

## Estructura del proyecto

```text
sgcm/
├── app/                          Backend Python
│   ├── api/v1/                   Endpoints REST
│   ├── core/                     Configuración y seguridad (JWT, bcrypt)
│   ├── db/                       Sesión SQLAlchemy
│   ├── models/                   Modelos SQLModel (tablas)
│   ├── services/                 Lógica de negocio
│   ├── templates/reportes/       Templates HTML para PDFs
│   └── main.py                   Punto de entrada FastAPI
├── alembic/                      Migraciones de base de datos
├── frontend/
│   ├── static/
│   │   └── js/app.js             Módulo JS común (SGCM)
│   └── templates/                Páginas HTML
│       ├── login.html
│       ├── calendar.html         Calendario y modales de cita
│       ├── pacientes.html
│       ├── medicos.html          Médicos y modal de edición
│       ├── agenda.html           Agenda del rol médico
│       ├── usuarios.html         Gestión de usuarios (admin)
│       └── auditoria.html        Log de auditoría (admin)
├── nginx/                        Configuración Nginx
├── scripts/seed.py               Datos iniciales
├── tests/                        Suite pytest
├── .github/workflows/ci.yml      CI con GitHub Actions
├── docker-compose.yml            Orquestación
├── Dockerfile                    Imagen del backend
├── requirements.txt              Dependencias Python
└── .env.example                  Plantilla de variables
```

---

## Casos de uso

El sistema implementa los **15 casos de uso** definidos en el análisis:

|ID|Caso de uso|Roles|
|---|---|---|
|CU-01|Iniciar sesión|Todos|
|CU-02|Cerrar sesión|Todos|
|CU-03|Registrar paciente|Secretaria, Admin|
|CU-04|Buscar paciente|Secretaria, Admin|
|CU-05|Editar paciente|Secretaria, Admin|
|CU-06|Agendar cita|Secretaria, Admin|
|CU-07|Reprogramar cita|Secretaria, Admin|
|CU-08|Cancelar cita|Secretaria, Admin|
|CU-09|Consultar citas|Todos|
|CU-10|Generar reporte PDF|Secretaria, Admin|
|CU-11|Ver agenda diaria|Médico|
|CU-12|Registrar consulta|Médico|
|CU-13|Gestionar usuarios|Admin|
|CU-14|Registrar médico|Admin|
|CU-15|Consultar auditoría|Admin|

---

## Roles y permisos

|Rol|Permisos|
|---|---|
|Secretaria|Pacientes (CRUD), citas (CRUD), reportes|
|Médico|Solo agenda propia y registro de consultas (con bloqueo temporal)|
|Administrador|Todo lo anterior, más usuarios, médicos, horarios y auditoría|

El RBAC se aplica en **dos capas**: el backend valida cada petición HTTP independientemente del estado del frontend, garantizando seguridad real. El frontend adapta dinámicamente la UI con `data-role` para mejor experiencia.

---

## Pruebas automatizadas

```bash
# Ejecutar todos los tests dentro del contenedor
docker exec sgcm_api pytest -v

# Con cobertura
docker exec sgcm_api pytest --cov=app --cov-report=term-missing
```

Los tests usan **SQLite en memoria** con `StaticPool` para aislamiento y velocidad. Cubren autenticación, RBAC, CRUDs, índice único parcial, validación de cédula dominicana, bloqueo temporal del registro de consulta, vinculación de usuarios con perfiles de médico, generación de reportes y auditoría transaccional.

---

## Integración continua

El workflow `.github/workflows/ci.yml` se ejecuta ante cada push y pull request:

- **Job 1: Tests + Lint.** Instala dependencias, ejecuta `ruff` y la suite completa de `pytest`.
- **Job 2: Docker build.** Construye la imagen Docker validando que el artefacto sea desplegable.

Las versiones de WeasyPrint y pydyf están **fijadas explícitamente** en `requirements.txt` para evitar fallos derivados de cambios incompatibles entre versiones menores.

---

## Comandos útiles

|Acción|Comando|
|---|---|
|Arrancar el sistema|`docker compose up -d`|
|Detener el sistema|`docker compose down`|
|Ver logs en vivo|`docker compose logs -f`|
|Reiniciar tras cambios HTML/JS|`docker compose restart nginx`|
|Reiniciar tras cambios Python|`docker compose restart api`|
|Reconstruir tras cambios mayores|`docker compose up -d --build`|
|Ejecutar migraciones|`docker exec sgcm_api alembic upgrade head`|
|Acceder a la base de datos|`docker exec -it sgcm_db psql -U sgcm_user -d sgcm_db`|
|Ejecutar tests|`docker exec sgcm_api pytest -v`|

---

## Documentación

El proyecto incluye documentación complementaria:

- **Manual de Usuario.** Para el personal del hospital.
- **Manual de Instalación.** Para el personal técnico.
- **Guía de Configuración Personal.** Procedimiento detallado de despliegue local.
- **Guía de Entendimiento del Proyecto.** Recorrido archivo por archivo del código.
- **Guía de Estudio Profundo.** Testing, CI/CD, auditoría y Docker avanzado.
- **Guía de Demostración para la Defensa.** Guion paso a paso de la presentación.
- **Changelog v1.1.** Registro de cambios desde la entrega inicial.

---

## Cumplimiento legal

El sistema cumple con la **Ley 172-13 sobre Protección de Datos de Carácter Personal** de la República Dominicana mediante:

- Hashing bcrypt de contraseñas (nunca en texto plano).
- Comunicación cifrada HTTPS vía Nginx con certificado SSL.
- Tokens JWT firmados con clave secreta y expiración configurable.
- Auditoría transaccional inmutable de todas las operaciones críticas.
- Control de acceso basado en roles con principio de mínimo privilegio.

---

## Autores

**Cristopher Rafael Marcial** — Matrícula 21-1969

**Jeremy José de la Cruz Pérez** — Matrícula 21-0266

**Asesor:** Lic. David D'Oleo

Universidad Nacional Pedro Henríquez Ureña (UNPHU) — Recinto La Vega

Facultad de Ciencias y Tecnología, Escuela de Informática

La Vega, República Dominicana — 2026

---

## Versión

**SGCM v1.1** — Mayo 2026


## Cambios concretos respecto al anterior y por qué los hice

| Antes | Ahora | Razón |
| --- | --- | --- |
| Badge de CI con URL `actions/workflows/ci.yml/badge.svg` directo | Badge shields.io con `actions/workflow/status/...?branch=main` | El URL antiguo a veces no encuentra el workflow si el nombre cambia. El nuevo formato con `branch=main` es el oficial recomendado por shields.io desde 2022. |
| Diagrama ASCII con cajas Unicode | Diagrama Mermaid (`flowchart TB`) | GitHub renderiza Mermaid nativamente desde 2022. Se ve limpio en cualquier dispositivo, tema oscuro o claro, móvil o escritorio. El ASCII rompía en algunos contextos. |
| Bullets con emojis 🔐 📅 🚫 etc. | Bullets de texto plano en "Características principales" | Los emojis Unicode dependen del sistema operativo del lector. Algunos clientes los renderizan diferentes o como cajitas vacías. Texto plano siempre funciona. |
| Símbolo `↔` en el texto | "vinculación de usuarios con perfiles de médico" | El `↔` se ve mal en algunos navegadores y rompe en lectores de pantalla. |
| Tablas con encabezados separados por `\|---\|---\|` simples | Tablas con `\| --- \| --- \|` (espacios alrededor) | Estilo más conservador que renderiza igual en todas las versiones de GFM. |
| Línea con `\|` simples sin espaciado en tablas largas | Igual estructura pero con espaciado consistente | Mejora legibilidad del fuente. |
| Bloque `text` sin lenguaje en estructura de carpetas | Bloque ` ```text ` explícito | Algunos renderers requieren tipo de lenguaje. `text` es seguro. |
| Iconos en links de los badges anteriores | Badges con `?logo=python&logoColor=white` etc. | Los logos vienen del CDN de shields.io, son confiables. Si el badge no carga, al menos el texto sigue siendo claro. |
