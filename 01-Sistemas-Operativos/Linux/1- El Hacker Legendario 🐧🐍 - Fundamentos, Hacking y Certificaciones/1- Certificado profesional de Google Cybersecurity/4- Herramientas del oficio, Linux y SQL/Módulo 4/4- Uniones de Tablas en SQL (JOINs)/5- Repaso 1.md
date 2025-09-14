
# 📌 Consultas y Respuestas del Lab

### 🔹 Tarea 1 — INNER JOIN (machines ↔ employees por `device_id`)

```sql
SELECT * 
FROM machines 
INNER JOIN employees 
  ON machines.device_id = employees.device_id;
```

**Resultado:** la unión interna devolvió **185 filas**.

---

### 🔹 Tarea 2 — LEFT JOIN y RIGHT JOIN

**LEFT JOIN (todas las máquinas):**

```sql
SELECT * 
FROM machines 
LEFT JOIN employees 
  ON machines.device_id = employees.device_id;
```

👉 El último valor en la columna `username` = **NULL**.

**RIGHT JOIN (todos los empleados):**

```sql
SELECT * 
FROM machines 
RIGHT JOIN employees 
  ON machines.device_id = employees.device_id;
```

👉 El último valor en la columna `username` = **areyes**.

---

### 🔹 Tarea 3 — INNER JOIN (employees ↔ log_in_attempts por `username`)

```sql
SELECT * 
FROM employees 
INNER JOIN log_in_attempts 
  ON employees.username = log_in_attempts.username;
```

**Resultado:** la unión interna devolvió **200 registros**.

---

# 🎯 Conclusión

Has practicado con éxito:

- `INNER JOIN` → solo registros coincidentes.
    
- `LEFT JOIN` → todos los registros de la tabla izquierda + coincidencias.
    
- `RIGHT JOIN` → todos los registros de la tabla derecha + coincidencias.
    
