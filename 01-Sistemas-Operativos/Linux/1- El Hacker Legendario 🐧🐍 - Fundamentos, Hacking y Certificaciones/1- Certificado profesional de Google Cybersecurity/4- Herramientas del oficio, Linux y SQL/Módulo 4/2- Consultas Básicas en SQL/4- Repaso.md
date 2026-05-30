---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Repaso
# 📌 Tarea 1: Recupera datos de los dispositivos de los empleados

👉 **Objetivo**: Ver qué dispositivos usan los empleados y cuáles necesitan parches.  
La información está en la tabla **`machines`**.

### 1. Recuperar todos los dispositivos

```sql
SELECT *
FROM machines;
```

🔎 Esto devuelve **todas las columnas y todas las filas** de la tabla:

- `device_id` (identificador único del dispositivo)
    
- `operating_system` (qué SO usa el dispositivo)
    
- `email_client` (cliente de correo configurado)
    
- `OS_patch_date` (fecha de último parche aplicado al SO)
    
- `employee_id` (a qué empleado pertenece el dispositivo)
    

Ejemplo de resultados:

```
device_id     | operating_system | email_client   | OS_patch_date | employee_id
--------------+------------------+----------------+---------------+------------
a184b775c707  | OS 1             | Email Client 1 | 2021-09-01    | 1156
a192b174c940  | OS 2             | Email Client 1 | 2021-06-01    | 1052
a305b818c708  | OS 3             | Email Client 2 | 2021-06-01    | 1182
...
```

---

### 2. Recuperar solo cliente de correo

```sql
SELECT device_id, email_client
FROM machines;
```

🔎 Esto devuelve solo los campos **ID del dispositivo** y **cliente de correo**.  
Se usa para identificar con qué clientes se está trabajando (Email Client 1, 2, etc.).

➡️ En la **tercera fila** el resultado fue: **Email Client 2** ✅.

---

### 3. Recuperar sistema operativo y fecha de parche

```sql
SELECT device_id, operating_system, OS_patch_date
FROM machines;
```

🔎 Aquí obtienes qué **SO usa cada máquina** y cuándo fue el **último parche**.  
Con eso puedes ver si están al día o desactualizados.

➡️ La **primera entrada** tenía como fecha de parche: **2021-09-01** ✅.

---

# 📌 Tarea 2: Investiga la actividad de acceso

👉 **Objetivo**: Revisar si hubo accesos sospechosos en la tabla **`log_in_attempts`**.

### 1. Ver ubicaciones de acceso

```sql
SELECT event_id, country
FROM log_in_attempts;
```

🔎 Devuelve el ID del evento de acceso y el país desde donde se intentó.  
Con esto verificas si los accesos fueron desde **EE.UU., Canadá o México** (esperados).

➡️ Respuesta: **No hubo intentos desde Australia** ✅.

---

### 2. Revisar accesos fuera de horario laboral

```sql
SELECT username, login_date, login_time
FROM log_in_attempts;
```

🔎 Esto devuelve usuario, fecha y hora de acceso.  
Luego puedes compararlo con el horario de trabajo (ej. 08:00–17:00).

➡️ **Usuario en la 5ta fila** → **jrafael** ✅.

(Opcional si quisieras filtrar solo los accesos fuera de horario):

```sql
SELECT username, login_date, login_time
FROM log_in_attempts
WHERE login_time NOT BETWEEN '08:00:00' AND '17:00:00';
```

---

### 3. Ver todos los intentos de acceso

```sql
SELECT *
FROM log_in_attempts;
```

🔎 Muestra todos los datos de intentos de acceso (incluyendo IP, país, estado del intento, etc.).

---

# 📌 Tarea 3: Ordena los datos de intentos de acceso

👉 **Objetivo**: Usar `ORDER BY` para organizar los datos.

### 1. Ordenar por fecha

```sql
SELECT *
FROM log_in_attempts
ORDER BY login_date;
```

🔎 Ordena cronológicamente según la fecha.

➡️ El **primer registro** fue: **ivelasco on 2022-05-08** ✅.

---

### 2. Ordenar por fecha y hora

```sql
SELECT *
FROM log_in_attempts
ORDER BY login_date, login_time;
```

🔎 Ordena primero por fecha y luego por hora dentro de la misma fecha.

➡️ El **primer registro** fue: **bsand at 00:19:11** ✅.

---

# ✅ Conclusión del Lab

Has practicado 3 puntos clave:

1. **SELECT con columnas específicas** → Para extraer solo lo que importa.
    
2. **Análisis de seguridad** → Países de acceso y accesos fuera de horario.
    
3. **Ordenamiento con ORDER BY** → Para analizar datos en secuencia cronológica.

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[3- Actividad - Realizar una consulta SQL]]
- ➡️ Siguiente: [[5- Filtros básicos en consultas SQL]]
