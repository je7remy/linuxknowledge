
# 📝 Resumen del Laboratorio de SQL – Filtrado de accesos

## 🔹 Tarea 1: Accesos después de una fecha

**Objetivo:** investigar intentos de acceso ocurridos después de un incidente de seguridad.

- Consulta usada:
    

```sql
SELECT * FROM log_in_attempts WHERE login_date > '2022-05-09';
```

👉 Aquí usamos `>` porque queremos **solo los accesos posteriores** al 9 de mayo de 2022.  
✅ Resultado: **125 intentos de acceso**.

---

**Expansión del período (incluyendo el 9 de mayo):**

```sql
SELECT * FROM log_in_attempts WHERE login_date >= '2022-05-09';
```

👉 Usamos `>=` para incluir tanto el día 9 como los días posteriores.  
✅ Resultado: **165 intentos de acceso**.

---

## 🔹 Tarea 2: Accesos en un rango de fechas

**Objetivo:** limitar la búsqueda a un rango (del 9 al 11 de mayo de 2022).

- Consulta usada:
    

```sql
SELECT * FROM log_in_attempts WHERE login_date BETWEEN '2022-05-09' AND '2022-05-11';
```

👉 `BETWEEN` devuelve todos los registros **desde el 9 hasta el 11, inclusive**.  
✅ Resultado: **123 intentos de acceso**.

---

## 🔹 Tarea 3: Accesos en determinados horarios

**Objetivo:** encontrar accesos fuera del horario laboral (antes de las 07:00 a.m.).

- Consulta inicial:
    

```sql
SELECT * FROM log_in_attempts WHERE login_time < '07:00:00';
```

👉 El filtro `login_time < '07:00:00'` captura accesos **anteriores a las 7:00 a.m.**  
✅ 5.º usuario en la lista: **eraab**.

---

**Afinar el rango (solo entre 06:00 y 07:00):**

```sql
SELECT * FROM log_in_attempts WHERE login_time BETWEEN '06:00:00' AND '07:00:00';
```

👉 `BETWEEN` permite capturar solo ese intervalo de tiempo.  
✅ Primer intento en ese rango: **06:01:31**.

---

## 🔹 Tarea 4: Accesos por ID de evento

**Objetivo:** filtrar accesos según el número de ID del evento.

- Consulta inicial:
    

```sql
SELECT event_id, username, login_date FROM log_in_attempts WHERE event_id >= 100;
```

👉 Usamos `>= 100` porque solo queremos IDs a partir de 100.  
✅ Fecha del 3.º resultado: **2022-05-09**.

---

**Restringiendo el rango (100–150):**

```sql
SELECT event_id, username, login_date FROM log_in_attempts WHERE event_id BETWEEN 100 AND 150;
```

👉 Esto devuelve únicamente los registros **dentro de ese rango numérico**.  
✅ Usuario en el 7.º resultado: **tmitchel**.

---

# ✅ Conclusión

Con este laboratorio aprendiste a:

- Usar `>`, `<`, `>=` para trabajar con fechas y horas.
    
- Usar `BETWEEN … AND …` para restringir períodos de tiempo o rangos de IDs.
    
- Filtrar por fecha (`login_date`), por hora (`login_time`) y por números (`event_id`).
    

Esto es justo lo que se usa en la vida real para **auditar accesos sospechosos** y **detectar patrones fuera de lo normal** (por ejemplo, accesos fuera del horario laboral o después de un incidente de seguridad).

---

