
# Tarea 1 — Fallidos después de las 18:00

```sql
-- Registros
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;

-- ¿Cuántos?
SELECT COUNT(*) AS failed_after_18
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```

> X = `18:00` | Y = `0`

---

# Tarea 2 — Intentos (fallidos) del 2022-05-08 o 2022-05-09

```sql
-- Registros
SELECT *
FROM log_in_attempts
WHERE (login_date = '2022-05-08' OR login_date = '2022-05-09')
  AND success = 0;

-- ¿Cuántos?
SELECT COUNT(*) AS failed_on_0508_or_0509
FROM log_in_attempts
WHERE (login_date = '2022-05-08' OR login_date = '2022-05-09')
  AND success = 0;
```

_(Si tu lab pide “todos los intentos” y no solo los fallidos, quita la línea `AND success = 0`.)_

---

# Tarea 3 — Intentos fuera de México

```sql
-- Registros
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';

-- ¿Cuántos?
SELECT COUNT(*) AS attempts_outside_mexico
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

> X = `NOT` | Y = `MEX%`

---

# Tarea 4 — Empleados de Marketing en edificio East

```sql
-- Registros
SELECT *
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East-%';

-- “Username del primer empleado…”
-- Para que “primero” sea determinista, ordénalo:
SELECT username
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East-%'
ORDER BY username
LIMIT 1;
```

---

# Tarea 5 — Empleados de Finance o Sales

```sql
-- Registros
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';

-- “Username del primer empleado de Sales…”
-- Si solo quieres el primero de Sales (ordenado por username):
SELECT username
FROM employees
WHERE department = 'Sales'
ORDER BY username
LIMIT 1;
```

---

# Tarea 6 — Empleados que NO son de IT

```sql
-- Registros
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';

-- ¿Cuántos?
SELECT COUNT(*) AS non_it_employees
FROM employees
WHERE NOT department = 'Information Technology';
```


