
## Flujo de Atención Normal

```mermaid
graph TD
    A[Paciente llega a emergencia o consulta] --> B[Recepcion toma datos y triage 3,4 y 5]
    B --> C[Se registra como paciente admitido]
    C --> D[Creacion de historia clinica]
    D --> E[Medico evalua al paciente]
    E --> F[Orden medica: estudios, medicamentos, insumos]
    F --> G[Enfermeria recibe orden medica]
    G --> H[Enfermeria solicita insumos en sistema]
    H --> I[Farmacia recibe orden e insumos]
    I --> J[Farmacia despacha medicamentos]
    J --> K[Enfermera aplica medicamento]
    K --> L[Nota de enfermeria]
    L --> M[Se refleja evolucion medica y de enfermeria]
    M --> N{Requiere mas evaluacion}
    N -- Si --> O[Medico hace interconsulta o nuevos estudios]
    O --> P[Especialista da diagnostico]
    P --> Q[Se actualiza evolucion y tratamiento]
    N -- No --> R{Paciente mejora}
    R -- Si --> S[Medico emite alta medica]
    S --> T[Se registra alta en sistema]
    T --> U[Admision reclama seguro]
    U --> V[Facturacion de todo lo registrado]
    R -- No --> W[Paciente requiere ingreso]
    W --> X[Transferido a hospitalizacion]
    X --> Y[Continua atencion bajo otro flujo]

    %% Emergencias
    E --> Z{Emergencia inmediata}
    Z -- Si --> ZA[Medico indica verbalmente]
    ZA --> ZB[Enfermera aplica sin registro]
    ZB --> ZC[Registra despues en sistema]
    ZC --> H

    %% Imagenologia
    F --> IA[Orden de imagen]
    IA --> IB[Se realiza estudio]
    IB --> IC[Se marca como tomado]
    IC --> ID[Se carga y se factura]
    ID --> IE[Medico revisa resultado]

    %% Laboratorio
    F --> LA[Orden de laboratorio]
    LA --> LB[Toma de muestra]
    LB --> LC[Resultado disponible para medico]

    %% Error de registro
    ZC --> E1{No se registro correctamente}
    E1 -- Si --> E2[No se puede facturar]
    E2 --> E3[Posible glosa o rechazo de seguro]
```


---

## Flujo de Atención de Emergencia


```mermaid
graph TD
    A[Llega paciente Triage 1 o 2] --> B[Atencion inmediata]
    B --> C[Tratamiento urgente]
    C --> D[Se crea registro en sistema]
    D --> E[Medico emite orden formal]
    E --> F[Farmacia y personal regularizan]
    F --> G[Destino: UCI, cirugia u observacion]
    G --> H[Registro completo]
    H --> I[Facturacion y reclamo de seguro]
```


---

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



