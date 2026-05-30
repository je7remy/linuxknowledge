---

# 📘 Reference Guide: SQL

_Google Cybersecurity Certificate_

---

## Tabla de contenidos

1. Query a database
    
2. Apply filters to SQL queries
    
3. Join tables
    
4. Perform calculations
    

---

## 1. Query a database

Los comandos **SELECT**, **FROM** y **ORDER BY** se usan para recuperar información de una base de datos.

### FROM

Indica qué tabla consultar; es requerido para ejecutar una query.

```sql
FROM employees
```

Consulta la tabla `employees`.

### ORDER BY

Ordena los registros devueltos según una o más columnas.

```sql
ORDER BY department
```

Ordena en orden ascendente por la columna `department`.

```sql
ORDER BY department ASC
```

Equivalente, ascendente.

```sql
ORDER BY city DESC
```

Ordena en orden descendente por la columna `city`.

```sql
ORDER BY country, city
```

Primero ordena por país, luego por ciudad.

### SELECT

Indica qué columnas devolver; es requerido para ejecutar una query.

```sql
SELECT employee_id
```

Devuelve la columna `employee_id`.

```sql
SELECT *
```

Devuelve todas las columnas de una tabla.

---

## 2. Apply filters to SQL queries

Los filtros se aplican con **WHERE** y otros operadores.

### AND

Ambas condiciones deben cumplirse.

```sql
WHERE region = 5 AND country = 'USA'
```

### BETWEEN

Filtra por rango de números o fechas.

```sql
WHERE hiredate BETWEEN '2002-01-01' AND '2003-01-01'
```

### Operadores de comparación

- `=` igual a
    
- `>` mayor que
    
- `>=` mayor o igual
    
- `<` menor que
    
- `<=` menor o igual
    

Ejemplo:

```sql
WHERE birthdate = '1980-05-15'
WHERE birthdate > '1970-01-01'
WHERE birthdate >= '1965-06-30'
WHERE date < '2023-01-31'
WHERE date <= '2020-12-31'
```

### LIKE

Busca patrones en un campo.

```sql
WHERE title LIKE 'IT%'
WHERE state LIKE 'N_'
```

### NOT

Nega una condición.

```sql
WHERE NOT country = 'Mexico'
```

### Diferente de

`<>` o `!=`

```sql
WHERE date <> '2023-02-28'
WHERE date != '2023-05-14'
```

### OR

Cualquiera de las condiciones puede cumplirse.

```sql
WHERE country = 'Canada' OR country = 'USA'
```

### Wildcards

- `%` sustituye cualquier cantidad de caracteres.
    
    - `'a%'` empieza con "a".
        
    - `'%a'` termina con "a".
        
    - `'%a%'` contiene "a".
        
- `_` sustituye un solo carácter.
    
    - `'a_'` → "a" + 1 caracter.
        
    - `'a__'` → "a" + 2 caracteres.
        
    - `'_a'` → 1 caracter + "a".
        
    - `'_a_'` → 1 caracter + "a" + 1 caracter.
        

### WHERE

Siempre inicia un filtro.

```sql
WHERE title = 'IT Staff'
```

---

## 3. Join tables

### FULL OUTER JOIN

Devuelve todos los registros de ambas tablas.

```sql
SELECT *
FROM employees
FULL OUTER JOIN machines
ON employees.device_id = machines.device_id;
```

### INNER JOIN

Devuelve solo registros coincidentes.

```sql
SELECT *
FROM employees
INNER JOIN machines
ON employees.device_id = machines.device_id;
```

### LEFT JOIN

Devuelve todos los registros de la primera tabla y solo coincidencias de la segunda.

```sql
SELECT *
FROM employees
LEFT JOIN machines
ON employees.device_id = machines.device_id;
```

### RIGHT JOIN

Devuelve todos los registros de la segunda tabla y solo coincidencias de la primera.

```sql
SELECT *
FROM employees
RIGHT JOIN machines
ON employees.device_id = machines.device_id;
```

---

## 4. Perform calculations

Funciones de agregación para cálculos.

### AVG

Promedio de los valores de una columna.

```sql
SELECT AVG(height)
```

### COUNT

Número de registros devueltos.

```sql
SELECT COUNT(firstname)
```

### SUM

Suma de los valores de una columna.

```sql
SELECT SUM(cost)
```

---

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[3- Recapitulación]]
- ➡️ Siguiente: [[5- Términos del glosario del Módulo 4]]
