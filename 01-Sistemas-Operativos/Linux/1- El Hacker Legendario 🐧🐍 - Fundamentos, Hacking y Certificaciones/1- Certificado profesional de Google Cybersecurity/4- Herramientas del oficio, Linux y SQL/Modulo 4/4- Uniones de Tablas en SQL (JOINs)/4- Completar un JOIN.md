
# Tarea 1 — INNER JOIN `machines` ↔ `employees` por `device_id`

**Consulta:**

```sql
SELECT *
FROM machines
INNER JOIN employees
  ON machines.device_id = employees.device_id;
```

**¿Cuántas filas devolvió?** ➜ **185**

---

# Tarea 2 — LEFT JOIN y RIGHT JOIN

## LEFT JOIN (todas las máquinas)

**Consulta:**

```sql
SELECT *
FROM machines
LEFT JOIN employees
  ON machines.device_id = employees.device_id;
```

**Último `username` devuelto:** ➜ **NULL**

## RIGHT JOIN (todos los empleados)

**Consulta:**

```sql
SELECT *
FROM machines
RIGHT JOIN employees
  ON machines.device_id = employees.device_id;
```

**Último `username` devuelto:** ➜ **areyes**

---

# Tarea 3 — INNER JOIN `employees` ↔ `log_in_attempts` por `username`

**Consulta:**

```sql
SELECT *
FROM employees
INNER JOIN log_in_attempts
  ON employees.username = log_in_attempts.username;
```

**¿Cuántos registros devuelve?** ➜ **200**

---

