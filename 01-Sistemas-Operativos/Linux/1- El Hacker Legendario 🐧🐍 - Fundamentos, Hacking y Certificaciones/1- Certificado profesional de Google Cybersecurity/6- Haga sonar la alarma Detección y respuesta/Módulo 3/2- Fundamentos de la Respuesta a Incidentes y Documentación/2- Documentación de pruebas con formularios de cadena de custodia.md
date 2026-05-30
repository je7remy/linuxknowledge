---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Documentación de pruebas con formularios de cadena de custodia

La **cadena de custodia** es un proceso formal para documentar el manejo, la posesión y el control de las pruebas durante todo el ciclo de vida de un incidente de seguridad. Su principal objetivo es garantizar la **integridad**, **fiabilidad** y **exactitud** de las pruebas, especialmente si se van a utilizar en procedimientos legales.

---

### ¿Cómo Funciona la Cadena de Custodia? ⛓️

El proceso comienza en el momento en que se recolecta una prueba, como un disco duro comprometido. Cada vez que la prueba cambia de manos, se debe registrar en un formulario de cadena de custodia.

Un ejemplo práctico:

1. **Recolección:** Un analista (Aisha) recoge un disco duro. Lo primero que hace es protegerlo contra escritura y calcular un **hash criptográfico** de su contenido. Este hash funciona como una "huella digital" única para los datos en ese momento exacto.
    
2. **Transferencia:** Aisha entrega el disco a un forense (Colin). Ambos firman el formulario, registrando quién entrega, quién recibe, la fecha, la hora y el motivo.
    
3. **Movimiento Continuo:** El proceso se repite cada vez que el disco pasa a otra persona (de Colin a Nav, de Nav a Arman, etc.).
    
4. **Verificación:** En cualquier punto, se puede recalcular el hash del disco. Si coincide con el hash original que calculó Aisha, demuestra que los datos no han sido alterados.
    

Este "rastro de papel" transparente detalla **quién**, **qué**, **cuándo**, **dónde** y **por qué** se manejó la prueba.

---

### Elementos Clave de un Formulario de Cadena de Custodia

Aunque no hay una plantilla universal, todos los formularios deben incluir:

- **Descripción de la Prueba:** Información identificativa como nombre de host, dirección IP/MAC, ubicación, etc.
    
- **Registro de Custodia:** Nombres y firmas de quienes transfieren y reciben la prueba.
    
- **Detalles de la Transferencia:** Fecha, hora y el propósito específico de cada transferencia.
    

---

### ¿Qué es una Ruptura en la Cadena de Custodia? 💥

Una **ruptura en la cadena de custodia** ocurre cuando hay errores, omisiones o inconsistencias en el registro de las pruebas. Por ejemplo, si falta una firma o no se documenta una transferencia.

La consecuencia principal es grave: una ruptura puede **comprometer la integridad de las pruebas**. Esto puede hacer que sean consideradas poco fiables y, por lo tanto, **inadmisibles ante un tribunal**. Sin una cadena de custodia sólida, es mucho más difícil responsabilizar legalmente a los actores malintencionados por sus acciones.

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[1- Beneficios de la documentación]]
- ➡️ Siguiente: [[3- Buenas prácticas para una documentación eficaz]]
