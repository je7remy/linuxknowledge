
# 📌 Resumen de Actividades – Uniones SQL

### 🔹 Contexto

Como **analista de seguridad**, necesitaste consultar datos distribuidos en varias tablas para investigar un incidente. Para ello aplicaste distintos tipos de **JOIN** en SQL:

- **INNER JOIN** → solo coincidencias.
    
- **LEFT JOIN** → todos los registros de la tabla izquierda.
    
- **RIGHT JOIN** → todos los registros de la tabla derecha.
    

---

## 🧩 Tarea 1: Emparejar empleados con sus máquinas

**Objetivo:** Identificar qué empleados usan qué máquinas.  
**Consulta:**

```sql
SELECT * 
FROM machines 
INNER JOIN employees 
  ON machines.device_id = employees.device_id;
```

**Resultado:** La unión interna devolvió **185 filas**.

---

## 🧩 Tarea 2: Devolver más datos

### LEFT JOIN (todas las máquinas)

```sql
SELECT * 
FROM machines 
LEFT JOIN employees 
  ON machines.device_id = employees.device_id;
```

👉 El último valor en la columna `username` = **NULL**.

### RIGHT JOIN (todos los empleados)

```sql
SELECT * 
FROM machines 
RIGHT JOIN employees 
  ON machines.device_id = employees.device_id;
```

👉 El último valor en la columna `username` = **areyes**.

---

## 🧩 Tarea 3: Recuperar intentos de inicio de sesión

**Objetivo:** Ver qué empleados han hecho intentos de acceso.  
**Consulta:**

```sql
SELECT * 
FROM employees 
INNER JOIN log_in_attempts 
  ON employees.username = log_in_attempts.username;
```

**Resultado:** La unión interna devolvió **200 registros**.

---

# 🎯 Conclusión

Has practicado y entendido cómo aplicar:

- `INNER JOIN` → para coincidencias exactas entre tablas.
    
- `LEFT JOIN` → para incluir todos los registros de la tabla izquierda, con NULL si no hay coincidencia.
    
- `RIGHT JOIN` → para incluir todos los registros de la tabla derecha, con NULL si no hay coincidencia.
    
