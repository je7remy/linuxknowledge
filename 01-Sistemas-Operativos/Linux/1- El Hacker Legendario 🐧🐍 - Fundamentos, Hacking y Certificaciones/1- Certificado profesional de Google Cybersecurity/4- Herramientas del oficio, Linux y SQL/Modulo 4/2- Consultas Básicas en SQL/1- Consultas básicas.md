
Las dos palabras clave SQL que necesitamos para las consultas básicas son **SELECT** y **FROM**.

- **SELECT** indica qué columnas queremos devolver.
    
- **FROM** indica de qué tabla obtendremos la información.
    

Podemos entenderlo con un ejemplo cotidiano: pedirle a alguien que _seleccione manzanas y plátanos de la caja grande_ es muy parecido a usar **SELECT** y **FROM** en SQL.

Para nuestra primera consulta, supongamos que tenemos una tabla llamada `empleados`, que contiene varias columnas, entre ellas `employee_id` y `device_id`. Si queremos obtener solo esas dos columnas, la consulta sería:

```sql
SELECT employee_id, device_id
FROM empleados;
```

Las columnas se separan con una coma. Es importante recordar que SQL no distingue entre mayúsculas y minúsculas, por lo que se puede escribir `select` y `from` en minúscula, aunque normalmente se escriben en mayúscula para hacer la consulta más clara y legible.

Otro aspecto de la sintaxis es que las sentencias suelen terminar con un punto y coma `;`. Al ejecutar esta consulta, obtendremos los pares de empleados y las computadoras asignadas.

Si en lugar de obtener solo dos columnas queremos ver toda la información de la tabla, podemos usar un asterisco `*` después de **SELECT**:

```sql
SELECT *
FROM empleados;
```

Esto se conoce como **select all** y devuelve todas las columnas de la tabla `empleados`.

Con esto, hemos realizado nuestra primera consulta SQL básica.

---

**Pregunta:**  
¿Qué columnas devolverá `SELECT *`?

**Opciones:**

- Las cinco primeras columnas de la tabla especificada
    
- La primera columna de la tabla especificada
    
- **Todas las columnas de la tabla especificada** ✅
    
- La última columna de la tabla especificada
    

**Respuesta correcta:**  
`SELECT *` ordena a SQL que devuelva **todas las columnas de la tabla especificada**.