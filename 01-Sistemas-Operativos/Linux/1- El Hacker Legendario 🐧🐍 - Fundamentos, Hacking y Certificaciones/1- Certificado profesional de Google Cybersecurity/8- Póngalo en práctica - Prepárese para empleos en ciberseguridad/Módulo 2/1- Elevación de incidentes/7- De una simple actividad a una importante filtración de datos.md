---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# De una simple actividad a una importante filtración de datos

### 🎯 El Peligro de No Escalar (El Efecto "Bola de Nieve")

El escenario lo deja muy claro: un incidente que parece menor (actividad inusual en una app prohibida) puede ser la primera señal de un ataque mucho mayor.

- **Incidente inicial:** Actividad sospechosa. (Impacto bajo).
    
- **Resultado por no escalar:** Violación de datos, paralización de una planta de fabricación y pérdida de dinero. (Impacto catastrófico).
    

La lección principal es que **ningún incidente es demasiado pequeño para ser reportado**. Es mejor escalar algo que resulte ser inofensivo, que ignorar algo que resulte ser desastroso.

---

### 📊 La Criticidad y la Urgencia

El texto distingue dos conceptos clave para manejar un incidente:

#### 1. Criticidad del Incidente

Esto se refiere a la **gravedad** del incidente en sí. El video explica que este nivel puede cambiar:

- Un analista puede marcar un incidente como de **criticidad media** si no está seguro del daño total.
    
- Un supervisor o gestor de incidentes, con más experiencia o información, puede luego **aumentarlo a "alto"** o **disminuirlo a "bajo"**.
    

#### 2. Urgencia del Incidente

Esto se refiere a **qué tan rápido** se debe actuar. La urgencia no la define el incidente en sí, sino el **activo** que está siendo afectado.

- **Activo de bajo impacto:** La computadora de un empleado que olvidó su contraseña.
    
    - _Incidente:_ Múltiples inicios de sesión fallidos.
        
    - _Urgencia:_ Baja. Debe atenderse, pero no es una emergencia.
        
- **Activo de alto impacto (Crítico):** Una base de datos con **PII** (Información de Identificación Personal) o el sistema de control de una planta de fabricación.
    
    - _Incidente:_ Un intento de acceso no autorizado.
        
    - _Urgencia:_ ¡Máxima! El impacto de una brecha aquí es severo y detiene el negocio.
        

---

En resumen, la lección fundamental es: **La urgencia de un incidente se mide por la importancia del activo que protege.**


## Pregunta

¿Cuándo debe un gestor de incidentes escalar un incidente de Seguridad de **alto nivel**?

---

### Opciones

- ✅ **Debe escalarse inmediatamente.**
    
- ❌ Debe escalarse después de que se produzca una violación de datos.
    
- ❌ Debe escalarse unos días después de que se produzca el incidente.
    
- ❌ Se debe escalar si el Problema no se resuelve por sí mismo.
    

---

### ✅ Explicación

> **Correcto.** Los incidentes de Seguridad de alto nivel deben ser escalados y tratados **inmediatamente**. Cuanto más tiempo pase antes de que un incidente sea escalado, mayor será el riesgo.

---

## Navegación

- ⬆️ Carpeta: [[_8- Póngalo en práctica - Prepárese para empleos en ciberseguridad|8- Póngalo en práctica - Prepárese para empleos en ciberseguridad]]
- ⬅️ Anterior: [[6- Ponga a prueba sus Conocimientos - Escalar o no escalar]]
- ➡️ Siguiente: [[8- Cuándo y cómo escalar un incidente de Seguridad]]
