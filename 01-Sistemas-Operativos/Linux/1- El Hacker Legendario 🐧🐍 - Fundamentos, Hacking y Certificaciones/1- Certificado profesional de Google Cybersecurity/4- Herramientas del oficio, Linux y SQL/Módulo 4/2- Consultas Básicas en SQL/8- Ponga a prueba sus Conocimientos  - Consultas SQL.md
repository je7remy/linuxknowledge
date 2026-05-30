---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos  - Consultas SQL

### 📌 Pregunta 1

**¿Qué es el filtrado en SQL?**  
👉 Seleccionar datos que coinciden con una determinada condición.

---

### 📌 Pregunta 2

**Consulta para obtener `firstname`, `lastname` y `phone` de employees en Chinook:**

```sql
SELECT firstname, lastname, phone 
FROM employees;
```

👉 Teléfono de Andrew Adams: **+1 (780) 428-9482**

---

### 📌 Pregunta 3

**Filtrar `log_in_attempts` donde country = 'Canada':**

```sql
SELECT * 
FROM log_in_attempts
WHERE country = 'Canada';
```

---

### 📌 Pregunta 4

**Patrón que coincide con cualquier cadena que empiece por 'A':**  
👉 `'A%'`

---

✅ Conclusión:  
Ya dominaste lo esencial:

- `WHERE` para filtrar.
    
- `SELECT` para columnas específicas.
    
- Uso de **comodines** (`%`) en `LIKE`.

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[7- Filtrar una consulta SQL]]
