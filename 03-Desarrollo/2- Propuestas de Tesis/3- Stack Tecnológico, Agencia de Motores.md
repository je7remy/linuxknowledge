
---
# Sistema de Gestión de Concesionarias de Vehículos

**Tecnología Utilizada:** El sistema se construirá utilizando **Flask (Python)** como backend para garantizar modularidad y adaptabilidad. La base de datos **PostgreSQL**, alojada en **ElephantSQL**, será la encargada de almacenar y gestionar datos críticos como inventario de vehículos, detalles de ventas y registros de clientes. Para la interfaz de usuario, se empleará **React + Vite**, asegurando rapidez y eficiencia en la experiencia del usuario. Además, se integrará una biblioteca de visualización de inventario o gestión de vehículos según sea necesario. La autenticación se implementará con **JWT + Bcrypt**, proporcionando seguridad en el manejo de credenciales y sesiones. Para las notificaciones, se utilizará **Resend** para el envío de correos electrónicos. El monitoreo de errores en producción podrá ser gestionado con **Sentry** (opcional). Finalmente, todo el sistema será desplegado en **Render.com**, una plataforma que permite gestionar React, Flask y PostgreSQL sin configuraciones complejas, garantizando escalabilidad y facilidad de mantenimiento.

### **Stack Tecnológico Actualizado** 🛠️  

| **Componente**     | **Tecnología**        | **Razón**                                                                      |
|--------------------|-----------------------|--------------------------------------------------------------------------------|
| **Frontend**       | React + Vite          | Ligero y rápido. Posible integración de bibliotecas para gestión de inventario.|
| **Backend**        | Flask (Python)        | Flexible y fácil de aprender. Ideal para APIs REST.                            |
| **Base de Datos**  | **PostgreSQL**        | Escalable desde el inicio. Usa **ElephantSQL** (PostgreSQL gratis en la nube). |
| **Autenticación**  | **JWT + Bcrypt**      | Contraseñas encriptadas y tokens seguros con expiración.                       |
| **Notificaciones** | Resend (Email)        | API fácil y gratuita para emails.                                              |
| **Logs/Errores**   | **Sentry (opcional)** | Monitoreo proactivo de errores en producción.                                  |
| **Despliegue**     | Render.com            | Soporta PostgreSQL, Flask y React sin configuración compleja.                  |

**Flujo de trabajo:**

```mermaid
graph TD
  subgraph Frontend[Frontend - React + Vite]
    A[Interfaz de Usuario] --> B[Gestión de Vehículos]
    A --> C[Gestión de Ventas]
    A --> D[Autenticación]
  end

  subgraph Backend[Backend - Flask]
    E[API REST] -->|CRUD| F[(PostgreSQL)]
    E -->|JWT + Bcrypt| G[Seguridad]
    E --> H[Resend]
    E --> I[Sentry]
  end

  subgraph Despliegue[Despliegue - Render.com]
    J[Frontend] 
    K[Backend]
    L[PostgreSQL]
  end

  A -->|Solicitudes HTTP| E
  J -->|Hosting| A
  K -->|Hosting| E
  L -->|Alojado en ElephantSQL| F
  G -->|Rate Limiting| E
  G -->|CORS| E
  H -->|Notificaciones| M[Cliente/Empleado]
  I -->|Monitoreo| N[Equipo Técnico]

  style A fill:#61dafb,stroke:#333
  style E fill:#FFD43B,stroke:#333
  style F fill:#336791,stroke:#333
  style H fill:#FF6B6B,stroke:#333
  style J fill:#6e6e6e,stroke:#333
  style K fill:#6e6e6e,stroke:#333
  style L fill:#6e6e6e,stroke:#333
```

---
