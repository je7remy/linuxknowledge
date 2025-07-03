
## Flujo de Atención Ambulatoria

## Proceso

### 1. Recepción del Paciente

El paciente llega al centro de salud y es recibido por el personal de admisión. Se verifica su información básica y se identifica el motivo de la visita (laboratorio o imagen diagnóstica).

---

### 2. Autorización del Servicio

Antes de proceder, se evalúa si el paciente cuenta con un seguro médico:

- **Si tiene seguro:**  
    Se remite a la unidad correspondiente para **autorizar el servicio** (laboratorio o imagen).  
    Allí se registra el **número de autorización**.
    
- **Si no tiene seguro:**  
    Se clasifica como **paciente privado** y se remite directamente a **facturación privada**.
    

---

### 3. Solicitud del Servicio de Salud

Una vez gestionada la autorización (o facturación en caso privado), se procede a **iniciar la solicitud de laboratorio o imagen**.

> _Aquí se crea el servicio de salud en el sistema._  
> _Corresponde a las áreas: Salud → Laboratorio → Solicitar test de laboratorio (o imágenes, según sea el caso)._

---

### 4. Caja

El paciente se dirige a **Caja**, donde:

- Si tiene seguro, se verifica la cobertura y se cobra **solo la diferencia**, si la hay.
    
- Si es privado, se realiza el cobro **total** del servicio.
    

---

### 5. Finalización del Proceso Administrativo

Tras el pago, el paciente pasa por la fase de cierre administrativo del servicio, en el que se valida:

- Que los cobros estén correctamente registrados.
    
- Que el servicio solicitado esté listo para ejecutarse.
    

Se considera **finalizado el proceso administrativo del servicio de salud**.

---

### 6. Validación Final de Seguro

Antes de ejecutar el examen, se realiza una **validación final de cobertura**, en caso de seguro:

- **Paciente con seguro contributivo:**  
    Se reconfirma la diferencia a pagar.  
    → El paciente abona el monto correspondiente.  
    → Pasa a laboratorio o imágenes.
    
- **Paciente con seguro subsidiado:**  
    No se requiere pago adicional.  
    → Pasa directamente a laboratorio o imágenes.
    

---

### 7. Ejecución del Servicio

El paciente finalmente se presenta en:

- **Laboratorio clínico**
    
- **Área de imágenes diagnósticas**
    

Allí se ejecuta el procedimiento correspondiente, cerrando así el ciclo del flujo ambulatorio.

---


````mermaid
graph TD
    A[Recepción Paciente] --> B[Autorizar Servicio Laboratorio o Imagen]
    B --> C{¿Tiene seguro?}

    C -- Sí --> D[Seguro]
    D --> E[Número de Autorización]
    E --> F[Iniciar Solicitud Laboratorio o Imagen<br/><small>*Aquí se crea el servicio de salud</small><br/><small>*Salud/Laboratorio/Solicitar Test de Laboratorio</small>]

    C -- No --> G[Privado]
    G --> H[Facturación Privada]
    H --> F

    F --> I[Caja]
    I --> J[Finalizar Servicio de Salud]
    J --> K{¿Tiene seguro?}

    K -- Sí --> L[Paciente Privado Seguro Contributivo]
    L --> M[Pago en efectivo total o diferencia]
    M --> N[Laboratorio o Imagen]

    K -- No --> O[Seguro Subsidiado]
    O --> P[Final con pago 0.00 Seguro]
    P --> N

````



