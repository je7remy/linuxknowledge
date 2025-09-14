
## 🔹 Tarea 1: Recupera datos de los dispositivos

```sql
-- Toda la información de los dispositivos
SELECT *
FROM machines;

-- Solo columnas device_id y email_client
SELECT device_id, email_client
FROM machines;

-- Solo columnas device_id, operating_system y OS_patch_date
SELECT device_id, operating_system, OS_patch_date
FROM machines;
```

✅ Respuestas:

- Cliente en la tercera fila → **Email Client 2**
    
- Fecha del parche de la primera entrada → **2021-09-01**
    

---

## 🔹 Tarea 2: Investiga la actividad de acceso

```sql
-- Seleccionar event_id y country
SELECT event_id, country
FROM log_in_attempts;

-- Seleccionar username, login_date y login_time
SELECT username, login_date, login_time
FROM log_in_attempts;

-- Ver todos los intentos de acceso (todas las columnas)
SELECT *
FROM log_in_attempts;
```

✅ Respuestas:

- ¿Hubo intentos desde Australia? → **Sí**
    
- Usuario en la quinta fila → **mrah**
    

---

## 🔹 Tarea 3: Ordena los datos de intentos de acceso

```sql
-- Ordenar por fecha
SELECT *
FROM log_in_attempts
ORDER BY login_date;

-- Ordenar por fecha y hora
SELECT *
FROM log_in_attempts
ORDER BY login_date, login_time;
```

✅ Respuestas:

- Primer registro ordenado por fecha → **ivelasco on 2022-05-08**
    
- Primer registro ordenado por fecha y hora → **bsand at 00:19:11**
    

---

