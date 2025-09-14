
### Preguntas y Respuestas

**1. ¿Por qué puede utilizar SQL un analista de Seguridad?**  
✔ Para encontrar eficazmente los datos necesarios en los registros de seguridad

---

**2. ¿Qué hay de cierto en los valores de la columna de clave primaria?**  
✔ No pueden ser nulos (o vacíos)  
✔ Cada fila debe tener un valor único

---

**3. ¿Cuál de estas sentencias SQL consulta la tabla `log_in_attempts`?**  
✔

`SELECT * FROM log_in_attempts;`

✔

`SELECT event_id, username FROM log_in_attempts WHERE event_id < 150;`

---

**4. ¿Qué hace INNER JOIN?**  
✔ Compara tablas y devuelve sólo las filas que tienen un valor coincidente en una columna especificada

---

**5. ¿Qué indica `WHERE department = 'Sales'`?**  
✔ Para devolver sólo las filas que coincidan con el filtro

---

**6. ¿Qué consulta devuelve todos los registros que empiezan por `a` en la columna `name`?**  
✔

`SELECT name  FROM employees  WHERE name LIKE 'a%';`

---

**7. ¿Qué devuelve la consulta con `RIGHT JOIN`?**  
✔ Todas las columnas de las tablas `employees` y `machines`, todos los registros de la tabla `machines` y los registros de `employees` que coincidan en `device_id`.

---

**8. Consulta Chinook**

`SELECT employeeid, email FROM employees;`

El empleado con correo `laura@chinookcorp.com` tiene ID: **6**.

---

**9. Filtrar empleados nacidos después del 01-01-1973**

`SELECT firstname, lastname, birthdate FROM employees WHERE birthdate >= '1973-01-01';`

✔ Respuesta: **3 empleados**

---

**10. Filtrar clientes en `Mountain View` y `Google Inc.`**

`SELECT firstname, lastname, city, company FROM customers WHERE city = 'Mountain View'   AND company = 'Google Inc.';`

✔ Respuesta: **1 cliente**