
# Aplicar filtros a consultas SQL

## Instrucciones para incluir consultas SQL

Se recomienda incluir **capturas de pantalla** de tus consultas SQL en la terminal. Si no es posible, también puedes **escribir** las consultas en el documento.

- No captures las instrucciones del laboratorio en el lado derecho de la pantalla.
    
- Para consultas escritas, usa fuente **monoespaciada** y un bloque de código (fondo gris), por ejemplo:
    

```sql
SELECT employee_id, device_id
FROM employees;
```

---

## Descripción del proyecto

Como analista de seguridad, utilicé SQL para investigar incidentes de seguridad y preparar actualizaciones de dispositivos. Apliqué filtros con **AND**, **OR**, **NOT** y **LIKE**, además de condiciones de fechas y horas, para recuperar subconjuntos de datos específicos de `log_in_attempts` y `employees`. Este documento resume las consultas, cómo funcionan y qué información brindan.

---

## Recuperar intentos fallidos de inicio de sesión fuera de horario

**Objetivo:** Identificar inicios de sesión fallidos que ocurrieron **después de las 18:00** (fuera del horario laboral).

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;  -- FALSE es equivalente a 0
```

**Cómo funciona:**

- `login_time > '18:00'` limita los resultados a intentos después de las 6:00 p. m.
    
- `AND success = FALSE` devuelve solo intentos fallidos.
    

> **Resultado del lab:** 19 intentos fallidos después de las 18:00.

---

## Recuperar intentos de inicio de sesión en fechas específicas

**Objetivo:** Devolver todos los intentos realizados el **2022-05-09** o el **2022-05-08**.

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**Alternativa (más clara con IN):**

```sql
SELECT *
FROM log_in_attempts
WHERE login_date IN ('2022-05-09', '2022-05-08');
```

**Cómo funciona:**

- Usa **OR** (o `IN`) para coincidir con cualquiera de las dos fechas.
    

> **Resultado del lab:** 75 intentos en esas dos fechas.

---

## Recuperar intentos de inicio de sesión fuera de México

**Objetivo:** Excluir intentos originados en México, donde los valores del país aparecen como `MEX` **o** `MEXICO`.

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

**Cómo funciona:**

- `LIKE 'MEX%'` coincide con `MEX` y `MEXICO` (prefijo MEX).
    
- `NOT` excluye esos registros; solo se muestran los de otros países.
    

> **Resultado del lab:** 144 intentos fuera de México.

---

## Recuperar empleados en Marketing

**Objetivo:** Obtener empleados de **Marketing** cuya oficina esté en el edificio **East** (por ejemplo, `East-170`, `East-320`).

```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

**Cómo funciona:**

- `department = 'Marketing'` filtra por departamento.
    
- `office LIKE 'East%'` selecciona cualquier oficina que comience con “East”.
    

> **Resultado del lab:** Primer usuario devuelto: `elarson`.

---

## Recuperar empleados en Finanzas o Ventas

**Objetivo:** Listar empleados en **Finance** o **Sales**.

```sql
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```

**Alternativa (IN):**

```sql
SELECT *
FROM employees
WHERE department IN ('Finance','Sales');
```

**Cómo funciona:**

- Usa **OR** (o `IN`) para devolver registros de cualquiera de los dos departamentos.
    

> **Resultado del lab:** Primer usuario en Ventas: `lrodriqu`.

---

## Recuperar todos los empleados que no están en TI

**Objetivo:** Devolver empleados que **no** pertenecen a **Information Technology**.

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

**Alternativa (distinto de):**

```sql
SELECT *
FROM employees
WHERE department <> 'Information Technology';
```

**Cómo funciona:**

- Usa **NOT** (o `<>`) para excluir al departamento de TI.
    
- Nota: si `department` puede ser `NULL`, considerar `OR department IS NULL`.
    

> **Resultado del lab:** 161 empleados no pertenecen a TI.

---

## Resumen

Mediante **AND**, **OR**, **NOT** y **LIKE**, además de comparaciones de fecha/hora, extraje conjuntos de datos específicos para apoyar la investigación de incidentes y planificar actualizaciones de seguridad. Las consultas muestran técnicas prácticas de filtrado para el análisis de seguridad y la gestión de activos.


# Formatos de Tablas – Actividad de Portafolio

Este documento describe cómo están organizadas las tablas utilizadas en la actividad de portafolio. La base de datos **organization** contiene las siguientes dos tablas principales:

- **log_in_attempts**
    
- **employees**
    

---

## Tabla: log_in_attempts

Contiene los registros de cada intento de inicio de sesión.

**Columnas:**

- **event_id**: Número de identificación asignado a cada evento de inicio de sesión.
    
- **username**: Nombre de usuario del empleado.
    
- **login_date**: Fecha en la que se registró el intento de inicio de sesión.
    
- **login_time**: Hora en la que se registró el intento de inicio de sesión.
    
- **country**: País donde ocurrió el intento de inicio de sesión.
    
- **ip_address**: Dirección IP de la máquina del empleado.
    
- **success**: Indica si el inicio de sesión fue exitoso. `FALSE` (0) indica intento fallido, `TRUE` (1) indica éxito.
    

**Ejemplo en la shell de MariaDB:**

```sql
+----------+----------+------------+------------+---------+-------------+---------+
| event_id | username | login_date | login_time | country | ip_address  | success |
+----------+----------+------------+------------+---------+-------------+---------+
|   10001  | jsmith   | 2022-05-08 | 19:30:00   | MEXICO  | 192.168.1.1 |       0 |
|   10002  | elarson  | 2022-05-09 | 09:15:00   | USA     | 10.0.0.25   |       1 |
+----------+----------+------------+------------+---------+-------------+---------+
```

---

## Tabla: employees

Contiene los datos de los empleados y sus dispositivos.

**Columnas:**

- **employee_id**: Número de identificación asignado a cada empleado.
    
- **device_id**: Número de identificación de cada dispositivo usado por el empleado.
    
- **username**: Nombre de usuario del empleado.
    
- **department**: Departamento al que pertenece el empleado (ejemplo: `Marketing`, `Finance`, `Information Technology`).
    
- **office**: Oficina donde se ubica el empleado (ejemplo: `East-170`, `North-434`).
    

**Ejemplo en la shell de MariaDB:**

```sql
+-------------+-----------+----------+----------------------+----------+
| employee_id | device_id | username | department           | office   |
+-------------+-----------+----------+----------------------+----------+
|        2001 |     D1001 | elarson  | Marketing            | East-170 |
|        2002 |     D1002 | lrodriqu | Sales                | West-205 |
|        2003 |     D1003 | jsmith   | Information Technology| North-434|
+-------------+-----------+----------+----------------------+----------+
```