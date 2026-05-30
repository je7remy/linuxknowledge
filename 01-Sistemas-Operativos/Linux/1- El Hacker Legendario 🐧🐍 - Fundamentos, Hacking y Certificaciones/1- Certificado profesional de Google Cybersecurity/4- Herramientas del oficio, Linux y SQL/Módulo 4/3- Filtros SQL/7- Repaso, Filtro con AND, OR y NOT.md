---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Repaso, Filtro con AND, OR y NOT

## 🔹 Tarea 1: Intentos fallidos después del horario laboral

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
```

**Resultado:** 19 intentos de acceso fallidos después de las 6:00 p.m.

---

## 🔹 Tarea 2: Intentos de acceso en fechas específicas

```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**Resultado:** 75 intentos de acceso en esas dos fechas.

---

## 🔹 Tarea 3: Intentos fuera de México

```sql
SELECT * 
FROM log_in_attempts 
WHERE NOT country LIKE 'MEX%';
```

**Resultado:** 144 intentos fuera de México.

---

## 🔹 Tarea 4: Empleados de Marketing en edificio East

```sql
SELECT * 
FROM employees 
WHERE department = 'Marketing' AND office LIKE 'East%';
```

**Resultado:** Primer usuario → **elarson**.

---

## 🔹 Tarea 5: Empleados de Finanzas o Ventas

```sql
SELECT * 
FROM employees 
WHERE department = 'Finance' OR department = 'Sales';
```

**Resultado:** Primer usuario en Sales → **lrodriqu**.

---

## 🔹 Tarea 6: Empleados que **NO** son de TI

```sql
SELECT * 
FROM employees 
WHERE NOT department = 'Information Technology';
```

**Resultado:** 161 empleados no pertenecen al departamento de TI.

---

## ✅ Conclusión

En este lab aplicaste los operadores lógicos en SQL:

- **AND** → Filtrar por múltiples condiciones que deben cumplirse.
    
- **OR** → Mostrar registros si cumplen al menos una condición.
    
- **NOT** → Excluir registros que coincidan con la condición.
    

Esto te permite crear consultas más complejas y útiles en investigación de seguridad y administración de datos.

---


# REPASO


# 📝 Resumen de Actividad – Filtros con AND, OR y NOT en SQL

## 🔹 Escenario

Eres analista de seguridad y debes filtrar información en una base de datos sobre intentos de acceso y empleados de una organización. El objetivo es investigar incidentes y preparar actualizaciones en los equipos.

---

## 🔸 Tarea 1 – Intentos fallidos después del horario laboral

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
```

✅ **Resultado:** 19 intentos fallidos después de las 6:00 p.m.

---

## 🔸 Tarea 2 – Intentos de acceso en fechas específicas

```sql
SELECT * 
FROM log_in_attempts 
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

✅ **Resultado:** 75 intentos en esas dos fechas.

---

## 🔸 Tarea 3 – Intentos fuera de México

```sql
SELECT * 
FROM log_in_attempts 
WHERE NOT country LIKE 'MEX%';
```

✅ **Resultado:** 144 intentos fuera de México.

---

## 🔸 Tarea 4 – Empleados de Marketing en el edificio East

```sql
SELECT * 
FROM employees 
WHERE department = 'Marketing' AND office LIKE 'East%';
```

✅ **Resultado:** Primer usuario → **elarson**.

---

## 🔸 Tarea 5 – Empleados de Finanzas o Ventas

```sql
SELECT * 
FROM employees 
WHERE department = 'Finance' OR department = 'Sales';
```

✅ **Resultado:** Primer usuario en Ventas → **lrodriqu**.

---

## 🔸 Tarea 6 – Empleados que no pertenecen a TI

```sql
SELECT * 
FROM employees 
WHERE NOT department = 'Information Technology';
```

✅ **Resultado:** 161 empleados no pertenecen a TI.

---

## 📌 Conclusión

Con estas consultas practicaste:

- **AND** → combinar condiciones (ej: después de las 18:00 **y** fallidos).
    
- **OR** → incluir múltiples posibilidades (ej: fechas 2022-05-09 **o** 2022-05-08).
    
- **NOT** → excluir registros (ej: accesos que **no** son de México o empleados que **no** son de TI).
    

🔑 Este ejercicio te prepara para consultas SQL más complejas en escenarios de seguridad y gestión de datos.

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[6- Laboratorio Filtrado con AND, OR y NOT]]
- ➡️ Siguiente: [[8- Aplicar filtros a las consultas SQL]]
