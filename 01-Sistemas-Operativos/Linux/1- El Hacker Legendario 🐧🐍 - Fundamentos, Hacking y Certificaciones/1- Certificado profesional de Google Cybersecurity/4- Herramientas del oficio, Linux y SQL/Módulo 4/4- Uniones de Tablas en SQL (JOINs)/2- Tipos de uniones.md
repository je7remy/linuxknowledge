---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Tipos de uniones

# 📌 Uniones Externas en SQL (LEFT, RIGHT y FULL OUTER JOIN)

### 🎯 Diferencia con INNER JOIN

- **INNER JOIN**: Devuelve **solo los registros coincidentes** en la columna especificada.
    
- **OUTER JOIN**: Devuelve también los registros que **no tienen coincidencia**, completando con valores **NULL**.
    

---

### 🔹 LEFT JOIN

- Devuelve:
    
    - ✅ Todas las filas de la **tabla izquierda** (la que aparece después de `FROM`).
        
    - ✅ Coincidencias de la **tabla derecha**.
        
    - ❌ Si no hay coincidencia, las columnas de la tabla derecha serán **NULL**.
        

**Ejemplo:**

```sql
SELECT *
FROM employees
LEFT JOIN machines
    ON employees.employee_id = machines.employee_id;
```

---

### 🔹 RIGHT JOIN

- Devuelve:
    
    - ✅ Todas las filas de la **tabla derecha** (la que aparece después de `JOIN`).
        
    - ✅ Coincidencias de la **tabla izquierda**.
        
    - ❌ Si no hay coincidencia, las columnas de la tabla izquierda serán **NULL**.
        

**Ejemplo:**

```sql
SELECT *
FROM employees
RIGHT JOIN machines
    ON employees.employee_id = machines.employee_id;
```

---

### 🔹 FULL OUTER JOIN

- Devuelve:
    
    - ✅ **Todas las filas de ambas tablas**.
        
    - Coincidencias donde existan.
        
    - ❌ Si no existe coincidencia en una de las tablas, las columnas de esa tabla se completan con **NULL**.
        

**Ejemplo:**

```sql
SELECT *
FROM employees
FULL OUTER JOIN machines
    ON employees.employee_id = machines.employee_id;
```

---

### 📝 Resumen rápido

|Tipo de JOIN|Qué devuelve|
|---|---|
|**INNER JOIN**|Solo filas con coincidencia en ambas tablas|
|**LEFT JOIN**|Todas las filas de la tabla izquierda + coincidencias de la derecha|
|**RIGHT JOIN**|Todas las filas de la tabla derecha + coincidencias de la izquierda|
|**FULL OUTER JOIN**|Todas las filas de ambas tablas; NULL en donde no hay coincidencia|

---

## 📌 Pregunta

**¿Cuál es la diferencia entre un `INNER JOIN` y un `OUTER JOIN`?**

---

## ✅ Respuesta correcta

✔️ **Las uniones internas sólo devuelven filas que coinciden en una columna especificada, pero las uniones externas también devuelven filas que no coinciden en la columna especificada.**

---

## ❌ Respuestas incorrectas

- ❌ _Las uniones internas implican una tabla izquierda y derecha, pero las uniones externas no._
    
- ❌ _Las uniones externas sólo devuelven las filas que coinciden en una columna especificada, pero las uniones internas devuelven todas las filas de ambas tablas._
    
- ❌ _Las uniones internas requieren la palabra clave ON, pero las uniones externas no._
    

---

👉 En resumen:

- **INNER JOIN** → Solo filas coincidentes.
    
- **OUTER JOIN** → Filas coincidentes **y también** las no coincidentes (con `NULL` en las columnas faltantes).

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[1- Unir tablas en SQL]]
- ➡️ Siguiente: [[3- Comparar tipos de uniones]]
