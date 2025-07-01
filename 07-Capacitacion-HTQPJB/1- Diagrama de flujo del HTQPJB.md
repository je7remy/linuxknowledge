
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
ambulatorio
1recepcion
2consulta o imagen o laboratorio
2autorizacion
tengo seguro pase aqui
no tiene seguro? pase aqui
pase a caja
3crea servicio de sallud solicita test de imagen
servicio de salud abro el seguro me coubre algo y pago lo otro voy a laboratorio
imagenes lo mismo 




---

creamos los servicios de laboratorio y imagen
servicio de salud