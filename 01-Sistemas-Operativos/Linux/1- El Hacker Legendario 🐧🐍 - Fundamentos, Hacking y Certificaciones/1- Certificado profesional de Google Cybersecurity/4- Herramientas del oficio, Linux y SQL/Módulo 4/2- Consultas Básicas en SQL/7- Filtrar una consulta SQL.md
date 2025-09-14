
## 🔹 Tarea 1: Lista de todas las máquinas

Consulta:

```sql
SELECT device_id, operating_system
FROM machines;
```

📌 **Cantidad de filas devueltas:** `200` ✅

---

## 🔹 Tarea 2: Máquinas con OS/2

Consulta:

```sql
SELECT device_id, operating_system
FROM machines
WHERE operating_system = 'OS 2';
```

📌 **Cantidad de máquinas con OS 2:** `80` ✅

---

## 🔹 Tarea 3: Empleados de Finanzas y Ventas

Consulta para Finanzas:

```sql
SELECT * 
FROM employees
WHERE department = 'Finance';
```

📌 **employee_id de la primera fila devuelta:** `1003` ✅

Consulta para Ventas:

```sql
SELECT * 
FROM employees
WHERE department = 'Sales';
```

📌 **Cantidad de empleados en Sales:** `33` ✅

---

## 🔹 Tarea 4: Máquinas de empleados en South

Consulta para una oficina específica:

```sql
SELECT * 
FROM employees
WHERE office = 'South-109';
```

📌 **Empleado que usa la máquina en South-109:** `jlansky` ✅

Consulta para todas las oficinas del edificio South:

```sql
SELECT * 
FROM employees
WHERE office LIKE 'South-%';
```

📌 **Departamento del primer empleado en South:** `Information Technology` ✅

---

✅ Con esto completaste todas las tareas del lab:

- Practicaste `SELECT` con columnas específicas.
    
- Usaste `WHERE` para filtrar valores exactos.
    
- Usaste `LIKE` con `%` para patrones de texto.
    

# Repaso


## 🔹 Tarea 1 – Listar todas las máquinas

Consulta:

```sql
SELECT device_id, operating_system 
FROM machines;
```

📌 **Resultado:** `200 filas` devueltas.

---

## 🔹 Tarea 2 – Máquinas con OS 2

Consulta:

```sql
SELECT device_id, operating_system
FROM machines 
WHERE operating_system = 'OS 2';
```

📌 **Resultado:** `80 máquinas` con OS 2.

---

## 🔹 Tarea 3 – Empleados de Finanzas y Ventas

Consulta para Finanzas:

```sql
SELECT * 
FROM employees 
WHERE department = 'Finance';
```

📌 **employee_id de la primera fila:** `1003`.

Consulta para Ventas:

```sql
SELECT * 
FROM employees 
WHERE department = 'Sales';
```

📌 **Empleados en Ventas:** `33`.

---

## 🔹 Tarea 4 – Máquinas de empleados en el edificio South

Consulta para oficina específica:

```sql
SELECT * 
FROM employees 
WHERE office = 'South-109';
```

📌 **Empleado en South-109:** `jlansky`.

Consulta para todas las oficinas South:

```sql
SELECT * 
FROM employees 
WHERE office LIKE 'South%';
```

📌 **Departamento del primer empleado en South:** `Finance`.

---

## ✅ Conclusión

Con este laboratorio ya sabes cómo:

- Usar **`SELECT`** para columnas específicas.
    
- Filtrar con **`WHERE`** para valores exactos.
    
- Utilizar **`LIKE` y `%`** para patrones de texto.
    

👉 Esto es clave para un analista de seguridad, porque te permite **aislar rápidamente la información relevante** en bases de datos grandes.

