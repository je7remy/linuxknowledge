---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Unir tablas en SQL

# 📌 Unir Tablas en SQL – INNER JOIN

### 🎯 Introducción

- Cuando necesitamos información de **dos tablas diferentes**, SQL permite **unir tablas** (JOIN).
    
- Ejemplo:
    
    - Una tabla con **vulnerabilidades de sistemas operativos**.
        
    - Otra con **máquinas de la empresa y sus sistemas operativos**.
        
    - Al unirlas, podemos obtener una **lista de máquinas vulnerables**.
        

---

### 📝 Sintaxis básica de referencias

- Si ambas tablas tienen una columna con el mismo nombre (`employee_id`), SQL necesita saber **de cuál tabla tomar el dato**.
    
- Se especifica así:
    
    ```
    tabla.columna
    ```
    
    - `employees.employee_id`
        
    - `machines.employee_id`
        

---

### 🔑 Identificación de la clave compartida

- Para unir, se necesita una **columna común** entre las tablas.
    
- En el ejemplo:
    
    - `employees.employee_id` → **clave primaria** (valores únicos, no nulos).
        
    - `machines.employee_id` → **clave foránea** (puede repetirse o estar vacía).
        
- Se utilizará un **INNER JOIN**.
    

---

### 🔎 INNER JOIN explicado

- **INNER JOIN** devuelve solo las filas que **coinciden en ambas tablas**.
    
- Ejemplo:
    
    - `employee_id = 1188` y `1189` aparecen en ambas → se muestran.
        
    - Si no hay coincidencia, no aparece en el resultado.
        

---

### ⚠️ Valores NULL

- `NULL` = valor faltante.
    
- Ejemplo: una máquina sin empleado asignado.
    
- INNER JOIN **ignora filas sin coincidencia** (no mostrará las máquinas con `employee_id = NULL`).
    

---

### 🖥️ Construcción de la consulta

Ejemplo de INNER JOIN:

```sql
SELECT 
    employees.username, 
    employees.office, 
    machines.operating_system
FROM employees
INNER JOIN machines
    ON employees.employee_id = machines.employee_id;
```

- `employees` = tabla izquierda (FROM).
    
- `machines` = tabla derecha (INNER JOIN).
    
- La unión se hace con `employee_id`.
    

---

### ✅ Resultado final

- La consulta devuelve:
    
    - `username`, `office` (tabla empleados).
        
    - `operating_system` (tabla máquinas).
        
- Solo aparecen los registros donde **employee_id coincide en ambas tablas**.
    
- Próximos temas: otros tipos de JOIN (LEFT, RIGHT, FULL).
    

---

# Si ejecuta la siguiente consulta, ¿Qué le devolverá? Seleccione todo lo que corresponda.
## 📌 Consulta en SQL

```sql
SELECT *
FROM log_in_attempts
INNER JOIN employees 
    ON log_in_attempts.username = employees.username;
```

---

## Opciones de respuesta

- ❌ **Sólo columnas de la tabla employees**
    
- ❌ **Sólo columnas de la tabla log_in_attempts**
    
- ✅ **Todas las columnas de las tablas log_in_attempts y employees**
    
- ✅ **Todas las filas de las tablas log_in_attempts y employees que coincidan en username**
    

---

## 📝 Explicación

- `INNER JOIN` devuelve **solo las filas que tienen coincidencia** en la columna `username` de ambas tablas.
    
- `SELECT *` devuelve **todas las columnas** de las tablas incluidas en la unión.
    

Por lo tanto, el resultado será:  
👉 **Todas las columnas** de `log_in_attempts` y `employees`.  
👉 **Solo las filas** donde `username` coincida en ambas tablas.

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ➡️ Siguiente: [[2- Tipos de uniones]]
