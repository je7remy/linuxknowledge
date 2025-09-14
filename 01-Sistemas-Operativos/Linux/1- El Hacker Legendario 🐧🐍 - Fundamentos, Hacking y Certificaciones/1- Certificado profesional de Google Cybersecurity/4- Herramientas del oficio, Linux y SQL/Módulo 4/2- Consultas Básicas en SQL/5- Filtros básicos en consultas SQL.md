

Filtrar es seleccionar datos que cumplan una determinada condición.  
Piense en el filtrado como una forma de elegir sólo los datos que deseamos.

Por ejemplo, si queremos seleccionar manzanas de un carro de fruta, el filtrado nos permite especificar qué tipo de manzanas queremos elegir:  
“**Elija sólo manzanas que sean frescas**”.  
Esto elimina de la selección las manzanas que no son frescas. ¡Eso es un filtro!

Como analista de seguridad, podríamos filtrar una tabla de intentos de registro para encontrar todos los intentos de un país específico. Por ejemplo, podríamos filtrar para que sólo devolviera los registros que contuvieran **Canadá**.

---

### Operadores en SQL

Un operador es un símbolo o palabra clave que representa una operación.  
Un ejemplo de operador sería el **operador igual a (=)**.

Si quisiéramos encontrar todos los registros que tienen **EE.UU.** en la columna de país, usaríamos:

```sql
country = 'EE.UU.'
```

Para aplicar un filtro en SQL, añadimos una línea adicional con la cláusula **WHERE**.  
La palabra clave **WHERE** indica la condición del filtro.  
Después de WHERE se especifica la condición mediante operadores.

---

### Ejemplo de filtro simple

Si quisiéramos encontrar todos los intentos de inicio de sesión realizados en Estados Unidos, usaríamos:

```sql
SELECT *
FROM log_in_attempts
WHERE country = 'EE.UU.';
```

Gracias a este filtro, sólo se devuelven las filas donde el país es **EE.UU.**.

---

### Filtrar por patrones

En el ejemplo anterior, la condición filtraba registros iguales a un valor exacto.  
Pero también podemos filtrar por **patrones** en lugar de una palabra exacta.

Por ejemplo, en una tabla de empleados con la columna **office**, podríamos buscar todas las oficinas del **Edificio Este**.  
Para ello usamos el comodín `%`, que representa cualquier conjunto de caracteres.

```sql
WHERE office LIKE 'Este%'
```

Esto devuelve valores como **Este-120**, **Este-290**, **Este-435**.

---

### Uso de LIKE para casos con variaciones

Supongamos que nuestra base de datos tiene inconsistencias para Estados Unidos:  
algunas entradas dicen **US**, otras **USA**.

Podemos aplicar un filtro con **LIKE**:

```sql
SELECT *
FROM log_in_attempts
WHERE country LIKE 'US%';
```

Esto devuelve registros donde la columna **country** empieza con “US”, incluyendo **US** y **USA**.

---

## Conclusión

Con `WHERE` y operadores como `=` o `LIKE` podemos:

- Seleccionar solo los registros que cumplan condiciones.
    
- Manejar valores exactos o patrones.
    
- Ser mucho más específicos y precisos en nuestras consultas SQL.
    

---

### Pregunta

¿Qué cláusula de **WHERE** contiene la sintaxis correcta para devolver todos los registros que contengan un valor en la columna **username** que empiece por el carácter `'a'`?

1. `WHERE username = 'a';`
    
2. `WHERE username LIKE 'a%';`
    
3. `WHERE username LIKE 'a';`
    
4. `WHERE username = 'a%';`
    

---

### Respuesta Correcta ✅

```sql
WHERE username LIKE 'a%';
```

📌 **Explicación:**

- El operador **LIKE** se utiliza con **WHERE** para buscar patrones en columnas.
    
- El comodín `%` sustituye a cualquier número de caracteres.
    
- `'a%'` significa: _“todos los valores que comienzan con la letra `a` y pueden tener cualquier cosa después”_.
    

Ejemplos que coinciden: `ana`, `andres`, `a123`.  
Ejemplos que **no** coinciden: `maria`, `carlos`.

---


# Repaso:


# 🗂️ Laboratorio: Realizar una consulta SQL


## 📌 Tarea 1: Recuperar datos de los dispositivos

### 1. Obtener toda la información

```sql
SELECT *
FROM machines;
```

👉 Devuelve todas las columnas: `device_id, operating_system, email_client, OS_patch_date, employee_id`.

---

### 2. Ver solo cliente de correo electrónico

```sql
SELECT device_id, email_client
FROM machines;
```

**Pregunta:** ¿Qué cliente de correo aparece en la 3ra fila?  
✅ Respuesta: **Email Client 2**

---

### 3. Ver SO y fecha de parche

```sql
SELECT device_id, operating_system, OS_patch_date
FROM machines;
```

**Pregunta:** ¿Cuál es la fecha del primer parche?  
✅ Respuesta: **2021-09-01**

---

## 📌 Tarea 2: Investigar actividad de inicio de sesión

### 1. Ver ubicaciones de intentos

```sql
SELECT event_id, country
FROM log_in_attempts;
```

**Pregunta:** ¿Hubo intentos desde Australia?  
✅ Respuesta: **No**

---

### 2. Ver accesos fuera de horario

```sql
SELECT username, login_date, login_time
FROM log_in_attempts;
```

**Pregunta:** ¿Qué usuario aparece en la 5ta fila?  
✅ Respuesta: **jrafael**

_(Opcional para horarios)_

```sql
WHERE login_time NOT BETWEEN '08:00:00' AND '17:00:00';
```

---

### 3. Ver todos los intentos

```sql
SELECT *
FROM log_in_attempts;
```

---

## 📌 Tarea 3: Ordenar los intentos de acceso

### 1. Ordenar por fecha

```sql
SELECT *
FROM log_in_attempts
ORDER BY login_date;
```

**Pregunta:** ¿Quién aparece primero?  
✅ Respuesta: **ivelasco on 2022-05-08**

---

### 2. Ordenar por fecha y hora

```sql
SELECT *
FROM log_in_attempts
ORDER BY login_date, login_time;
```

**Pregunta:** ¿Quién aparece primero?  
✅ Respuesta: **bsand at 00:19:11**

---

## 🏁 Conclusión del Lab

Ahora dominas:

- `SELECT columna1, columna2 FROM tabla;` → seleccionar columnas específicas.
    
- `SELECT * FROM tabla;` → seleccionar todas las columnas.
    
- `ORDER BY columna;` → ordenar resultados.
    

Estas son las bases para consultas más avanzadas con **filtros** (`WHERE`, `LIKE`, `AND`, `OR`, etc.).

---
