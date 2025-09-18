
# 📄 Hoja de trabajo de fuga de datos

## 🔹 Resumen de incidentes

Un gerente de ventas compartió el acceso a una carpeta de documentos internos con su equipo durante una reunión. La carpeta contenía archivos de un nuevo producto no anunciado, análisis de clientes y materiales promocionales. Después de la reunión, no revocó el acceso. Más tarde, un representante compartió por error el enlace completo con un socio comercial, quien lo publicó en redes sociales.

---

## 🔹 Tabla de análisis

|**Sección**|**Respuesta**|
|---|---|
|**Control**|Privilegio mínimo|
|**Problema(s)**|El acceso a la carpeta interna no se limitó al equipo de ventas y al gerente. El socio comercial no debería haber recibido permiso para compartir la información promocional en redes sociales.|
|**Revisión**|NIST SP 800-53: AC-6 aborda cómo una organización puede proteger la privacidad de sus datos mediante la implementación de privilegios mínimos. También sugiere mejoras de control para mejorar la eficacia del privilegio mínimo.|
|**Recomendación(es)**|● Restringir el acceso a recursos confidenciales en función del rol del usuario. ● Auditar regularmente los privilegios de los usuarios.|
|**Justificación**|Las fugas de datos se pueden evitar si los enlaces compartidos a archivos internos están restringidos solo a los empleados. Además, exigir auditorías regulares de privilegios ayuda a limitar la exposición de información confidencial.|

---

## 🔹 Instantánea del plan de seguridad

- **Función:** Proteger
    
- **Categoría:** PR.DS – Seguridad de los datos
    
- **Subcategoría:** PR.DS-5 – Protecciones contra fugas de datos
    
- **Referencia(s):** NIST SP 800-53: AC-6
    

---

## 🔹 NIST SP 800-53: AC-6 – Privilegio mínimo

- **Control:** Solo se debe proporcionar a los usuarios el acceso y la autorización mínimos necesarios para completar una tarea o función.
    
- **Discusión:** Los procesos, cuentas de usuario y roles deben aplicarse según sea necesario para lograr el privilegio mínimo. La intención es evitar accesos más altos de los necesarios para los objetivos empresariales.
    
- **Mejoras de control:**
    
    - Restringir el acceso a recursos confidenciales según el rol.
        
    - Revocar automáticamente el acceso tras un período de tiempo.
        
    - Mantener registros de actividad de cuentas aprovisionadas.
        
    - Auditar regularmente los privilegios de los usuarios.
        

---

