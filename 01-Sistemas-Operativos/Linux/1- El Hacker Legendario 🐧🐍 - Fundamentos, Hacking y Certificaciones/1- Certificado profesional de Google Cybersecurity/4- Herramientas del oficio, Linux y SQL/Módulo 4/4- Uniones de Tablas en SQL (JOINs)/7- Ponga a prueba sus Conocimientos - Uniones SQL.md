---

# 📌 Evaluación – Uniones SQL

---

## 1. Pregunta 1

**¿Qué tipos de join devuelven todas las filas de una sola de las tablas que se están uniendo?**

- INNER JOIN ❌
    
- FULL OUTER JOIN ❌
    
- RIGHT JOIN ✔️
    
- LEFT JOIN ✔️
    

**Explicación:**

- `LEFT JOIN` devuelve todas las filas de la **tabla izquierda** y solo las coincidentes de la derecha.
    
- `RIGHT JOIN` devuelve todas las filas de la **tabla derecha** y solo las coincidentes de la izquierda.
    

---

## 2. Pregunta 2

**INNER JOIN entre employees (izquierda) y machines (derecha) por employee_id.**

Opciones:

- `INNER JOIN ON employees.employee_id = machines.employee_id;` ❌
    
- `INNER JOIN machines ON employees.employee_id = machines.employee_id SELECT * FROM employees;` ❌
    
- ✅
    

```sql
SELECT * 
FROM employees 
INNER JOIN machines 
    ON employees.employee_id = machines.employee_id;
```

- `INNER JOIN machines WHERE employees.employee_id = machines.employee_id;` ❌
    

---

## 3. Pregunta 3

**Consulta:**

```sql
SELECT * 
FROM employees 
_____ machines ON employees.employee_id = machines.employee_id;
```

Opciones:

- LEFT JOIN ✔️
    
- RIGHT JOIN ❌
    
- INNER JOIN ❌
    
- FULL OUTER JOIN ❌
    

**Explicación:**  
`LEFT JOIN` devuelve todos los registros de la tabla `employees` (izquierda), y solo los que coinciden de `machines`.

---

## 4. Pregunta 4

**INNER JOIN entre invoices e invoice_items por InvoiceId**

Consulta correcta:

```sql
SELECT customerid, trackid
FROM invoices
INNER JOIN invoice_items 
    ON invoices.InvoiceId = invoice_items.InvoiceId;
```

**Valor en la primera fila de la columna `trackid`:**

- 449 ❌
    
- 1 ❌
    
- 2 ✔️
    
- 3 ❌
    

---

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[6- Repaso 2]]
