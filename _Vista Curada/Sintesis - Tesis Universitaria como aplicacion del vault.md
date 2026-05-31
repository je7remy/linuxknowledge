---
tipo: tesis
tags: [sintesis, tesis, sgcm, fastapi, aplicacion-practica]
actualizado: 2026-05-30
---

# Síntesis — La tesis universitaria como aplicación del vault

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Nota de síntesis cross-dominio** que conecta la tesis universitaria
**Sistema de Gestión de Citas Médicas (SGCM)** con el resto del vault.
La tesis no está aislada: es la **aplicación práctica** de los
fundamentos de desarrollo y la mentalidad de seguridad aprendidos en el
resto del vault.

## El proyecto SGCM

Sistema web para gestionar citas médicas en un hospital. Stack técnico
(según se ve en el vault):

- **Backend**: Python + FastAPI.
- **Base de datos**: MySQL (con MySQL Workbench para modelado).
- **Frontend**: por definir / pendiente.
- **Despliegue**: pendiente (probablemente cloud).

Cobertura en el vault:

- [[_2- Tesis Universitaria|2- Tesis Universitaria (carpeta)]]
- [[_1- Bases de Datos|1- Bases de Datos]]
- [[_3- Proyecto Web|3- Proyecto Web (FastAPI)]]

## Cómo el vault apoya cada capa de la tesis

### Capa 1 — Bases de datos

Conocimiento aplicado:

- **Modelado relacional** — Curso Google Cybersecurity Curso 4 cubre
  SQL fundamentos.
- **MySQL Workbench** — herramienta para diseñar el esquema visualmente.
- **SQL desde Python** — [[_4- Gestión de Bases de Datos desde Python|módulo del curso de Python]].

Tablas típicas en SGCM:

```sql
Pacientes (id, nombre, apellido, cedula, telefono, ...)
Medicos (id, nombre, especialidad, ...)
Citas (id, paciente_id, medico_id, fecha, hora, estado, ...)
Historiales (id, paciente_id, diagnostico, tratamiento, ...)
Usuarios (id, username, password_hash, rol, ...)
```

### Capa 2 — Backend con FastAPI

Conocimiento aplicado:

- [[_1- Backend con Python y FastAPI|1- Backend con Python y FastAPI]] —
  curso completo en el vault con 3 módulos:
  - Introducción a FastAPI.
  - Configuración del entorno.
  - HTTP y APIs.
- [[_Fundamentos de Python|Fundamentos de Python]] — sintaxis base.
- [[MOC - Python para Ciberseguridad|MOC Python para Ciberseguridad]] —
  bibliotecas relevantes (requests, sockets) — aunque la tesis no es
  ofensiva, conocer estas bibliotecas amplía la perspectiva.

Endpoints típicos:

```python
@app.post("/citas")
def crear_cita(cita: CitaSchema, current_user: User = Depends(get_user)):
    """Crear nueva cita (requiere autenticación)."""

@app.get("/citas/{paciente_id}")
def listar_citas(paciente_id: int):
    """Listar citas de un paciente."""
```

### Capa 3 — Seguridad (lo que distingue tu tesis)

Aquí es donde el conocimiento de **ciberseguridad** del vault eleva la
tesis del nivel "proyecto académico" a "sistema profesional".

#### Autenticación y autorización

Aprendizajes aplicables desde el vault:

- **Hashing de contraseñas** — usar `bcrypt`/`argon2`, NUNCA SHA-256
  directo. [[Cryptography|Ver entity page]].
- **JWT vs sessions** — JWT con `RS256` para APIs REST.
- **Roles**: paciente, médico, admin — least privilege.
- **MFA** opcional para roles privilegiados.

#### OWASP Top 10 aplicado

[[MOC - Web Pentesting OWASP|MOC OWASP]] enumera vulns que tu sistema
DEBE prevenir:

| Vuln OWASP | Cómo prevenirla en SGCM |
|---|---|
| **A01 Broken Access Control** | Verificar `current_user.id == paciente_id` o rol admin en cada endpoint. |
| **A02 Cryptographic Failures** | HTTPS, hashes bcrypt, secretos en env vars. |
| **A03 Injection** | SQLAlchemy ORM con parámetros (NO concatenar strings). |
| **A05 Misconfiguration** | Disable docs en producción, debug=False, headers seguros. |
| **A07 Auth Failures** | bcrypt, rate limit en login, password policy. |
| **A09 Logging** | Logger en cada endpoint, no log passwords. |
| **A10 SSRF** | Validar URLs si aceptas inputs URL. |

#### Privacidad médica

Datos de salud son **especialmente sensibles** (HIPAA en USA, GDPR en EU,
similares en otros países):

- **Cifrado en reposo** de DB (MySQL TDE o cifrado a nivel de aplicación).
- **Cifrado en tránsito** (HTTPS obligatorio).
- **Logs de auditoría** (quién accedió a qué historial médico cuándo).
- **Right to be forgotten** (capacidad de borrar datos del paciente).
- **Consentimiento explícito** para procesamiento de datos.

### Capa 4 — Documentación de la tesis

La metodología académica también se beneficia del patrón Karpathy:

- [[_5- Guia Completa de Tesis|5- Guía completa de tesis (pendiente)]] —
  estructura formal del documento.
- [[_8- Tesis Definitiva|8- Tesis definitiva]] — PDF final entregado.

## Mapa de dependencias

```
Tesis SGCM
├── Bases de Datos
│   └── _1- Bases de Datos
│       └── SQL fundamentos (Google Cyber Curso 4)
│
├── Backend
│   ├── _1- Backend con Python y FastAPI
│   ├── _Fundamentos de Python
│   └── _2- Curso de Python Aplicado a la Ciberseguridad
│       └── Módulo BD desde Python
│
└── Seguridad
    ├── Cryptography (entity page)
    ├── MOC - Web Pentesting OWASP
    ├── Pentesting (entity page)
    └── _0- Cómo PREPARAR ENTREVISTA TÉCNICA (conceptos generales)
```

## Por qué esta tesis es relevante para tu perfil

Como **estudiante de Linux/Ciberseguridad** que también desarrolla:

1. **Demuestra integración**: no eres solo pentester ni solo developer.
   Construyes Y rompes (mentalidad red+blue).
2. **Mostrable en entrevistas**: un sistema con autenticación real,
   manejo de datos sensibles, código en GitHub es portfolio fuerte.
3. **Aplicable post-grad**: muchos roles entry-level en empresas piden
   "desarrollo + algo de seguridad" — esta tesis es ese perfil.
4. **Conecta dominios**: la tesis aplica programación + bases de datos +
   redes (HTTPS) + criptografía + Linux (despliegue) — casi todo el vault.

## Pendientes del proyecto (ver [[_roadmap]])

- [ ] Guía completa de tesis ([[_5- Guia Completa de Tesis]] vacío).
- [ ] Tesis definitiva final (PDF en [[_8- Tesis Definitiva]] ya existe).
- [ ] Documentos Word originales ([[_3- Documentos de Word]] solo placeholder).
- [ ] Frontend del sistema (no aparece en el vault).
- [ ] Despliegue y CI/CD.
- [ ] Documentación de seguridad aplicada (threat model).
- [ ] Tests automatizados (unit + integration).

## Próximos pasos sugeridos

1. **Documentar threat model** de SGCM en una nota dentro de la tesis.
2. **Aplicar OWASP Top 10** explícitamente — sección de la tesis.
3. **Conectar las notas FastAPI** con wikilinks a la tesis (cross-ref bidireccional).
4. **Crear ADR (Architecture Decision Records)** dentro de la tesis para
   decisiones clave (¿por qué FastAPI? ¿por qué MySQL?).

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[_2- Tesis Universitaria|Carpeta de la tesis]]
- [[_3- Proyecto Web|Proyecto Web (FastAPI)]]
- [[_1- Bases de Datos|Bases de Datos]]
- [[Cryptography|Cryptography (entity page)]]
- [[MOC - Web Pentesting OWASP|MOC - OWASP]]
- [[MOC - Python para Ciberseguridad|MOC - Python para Ciberseguridad]]
- [[_roadmap|Roadmap del vault]]
