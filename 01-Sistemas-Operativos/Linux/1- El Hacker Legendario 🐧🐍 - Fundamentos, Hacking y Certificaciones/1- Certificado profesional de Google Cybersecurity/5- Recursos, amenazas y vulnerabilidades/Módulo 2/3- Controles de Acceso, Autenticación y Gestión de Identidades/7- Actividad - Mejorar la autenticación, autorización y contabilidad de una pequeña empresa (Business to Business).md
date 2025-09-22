
# 📄 Actividad: Evaluación de controles de acceso

---

## **Resumen de la actividad**

En esta actividad se evaluarán los **controles de acceso** utilizados por una empresa. El objetivo es analizar su proceso actual, identificar los problemas y recomendar mejoras en sus prácticas de seguridad.

Los controles de acceso gestionan la autenticación (verificar quién es un usuario), la autorización (qué puede hacer ese usuario) y la responsabilidad (rastrear sus acciones). Cuando se aplican correctamente, ayudan a **reducir la probabilidad de incidentes de seguridad**.

---

## **Escenario**

Usted es el primer profesional de ciberseguridad contratado por una empresa en expansión.

Recientemente, se detectó un **intento de transferencia de dinero** hacia una cuenta bancaria desconocida. El director financiero asegura que no cometió el error, y afortunadamente el pago pudo detenerse.

El propietario de la empresa le ha pedido que investigue el incidente y proponga soluciones para que no vuelva a ocurrir.

Para ello:

1. Revisará el **registro de accesos**.
    
2. Tomará notas sobre la información relevante.
    
3. Detectará problemas en los controles de acceso.
    
4. Propondrá recomendaciones para mitigar riesgos futuros.
    

---

## **Desarrollo de la actividad**

### **Paso 1: Revisión del registro de incidentes**

En el archivo **“Ejercicio de contabilidad.xlsx”**, en la pestaña _Registro de eventos_, se observan los siguientes datos:

- El evento ocurrió el **03/10/2023**.
    
- El usuario registrado es **Legal/Administrator**.
    
- El intento de acceso provino de la dirección IP **152.207.255.255**.
    

---

### **Paso 2: Comparación con el directorio de empleados**

En la pestaña _Directorio de empleados_, se encuentra que la cuenta **Legal/Administrator** corresponde a **Robert Taylor Jr.**

- Su **contrato finalizó en 2019**.
    
- Sin embargo, su cuenta aún estaba activa y **mantenía privilegios de administrador**.
    
- En 2023, esta misma cuenta accedió a los sistemas de nómina, lo cual constituye una **falla grave de control de acceso**.
    

---

### **Paso 3: Identificación de problemas**

Los problemas detectados son:

1. **Cuentas inactivas sin revocar**: la empresa no elimina ni desactiva las cuentas de empleados o contratistas que ya no laboran allí.
    
2. **Permisos excesivos**: el usuario mantenía privilegios administrativos sin justificación.
    
3. **Falta de revisiones periódicas**: no existían procesos de auditoría para identificar cuentas obsoletas.
    

---

### **Paso 4: Recomendaciones**

Se sugieren las siguientes acciones para fortalecer los controles de acceso:

1. **Expiración automática de cuentas**: configurar políticas para que las cuentas de empleados y contratistas se desactiven automáticamente después de 30 días de inactividad o al término del contrato.
    
2. **Principio de privilegios mínimos (PoLP)**: otorgar solo los permisos estrictamente necesarios según el rol. Los contratistas nunca deben tener acceso de administrador.
    
3. **Autenticación multifactor (MFA)**: implementar MFA en accesos a sistemas críticos (finanzas, nómina, almacenamiento en la nube).
    
4. **Monitoreo y auditoría continua**: revisar trimestralmente la lista de usuarios y permisos, apoyándose en registros centralizados (SIEM).
    
5. **Políticas claras de ciclo de vida de cuentas**: establecer procedimientos para creación, modificación y eliminación inmediata de cuentas al terminar la relación laboral.
    

---

## **Hoja de trabajo de control de acceso (completada)**

|**Authorization / Authentication**|**Note(s)**|**Issue(s)**|**Recommendation(s)**|
|---|---|---|---|
||**Objetivo:** 1–2 notas de información que ayuden a identificar la amenaza: • El evento ocurrió el 03/10/2023. • El usuario registrado fue Legal/Administrator. • La dirección IP usada fue 152.207.255.255. • La cuenta pertenece a Robert Taylor Jr.|**Objetivo:** 1–2 problemas de autorización detectados: • Robert Taylor Jr. seguía siendo administrador a pesar de que su contrato terminó en 2019. • Su cuenta accedió a los sistemas de nómina en 2023, 4 años después de finalizar su relación laboral.|**Objetivo:** Al menos 2–3 recomendaciones que prevengan incidentes: • Implementar expiración automática de cuentas tras 30 días de inactividad. • Aplicar principio de privilegios mínimos: limitar permisos de contratistas y usuarios. • Obligar al uso de MFA en accesos críticos. • Establecer auditorías trimestrales de accesos y permisos.|

---


