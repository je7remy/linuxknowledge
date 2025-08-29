
# Consultas SQL Básicas y ORDER BY

## Palabras clave esenciales

- **SELECT** → Indica qué columnas devolver.
    
- **FROM** → Indica de qué tabla obtener los datos.  
    Estas dos palabras se usan siempre juntas para consultar una base de datos.
    

Ejemplo:

```sql
SELECT employee_id, device_id
FROM employees;
```

## Base de datos Chinook

Durante el curso se utiliza la base de datos **Chinook**, que simula una empresa de medios digitales.  
Incluye tablas como:

- `employees`
    
- `customers`
    
- `invoices`
    

Ejemplo de consulta en `customers`:

```sql
SELECT customerid, city, country
FROM customers;
```

## SELECT

- Puede devolver una sola columna:
    
    ```sql
    SELECT customerid
    FROM customers;
    ```
    
- Puede devolver varias columnas separadas por coma:
    
    ```sql
    SELECT customerid, city
    FROM customers;
    ```
    
- Para obtener todas las columnas se usa `SELECT *`:
    
    ```sql
    SELECT *
    FROM customers;
    ```
    

⚠ Nota: `SELECT *` no es recomendable en tablas muy grandes porque puede generar salidas difíciles de leer y lentas.

## FROM

- Se coloca después de **SELECT** seguido del nombre de la tabla.
    
- Ejemplo en una sola línea:
    
    ```sql
    SELECT * FROM customers;
    ```
    
- El punto y coma `;` indica el final de la consulta.
    
- Los saltos de línea son opcionales, solo mejoran la legibilidad.
    

## ORDER BY

Sirve para **ordenar los resultados** según una o varias columnas.

### Orden ascendente (por defecto)

```sql
SELECT customerid, city, country
FROM customers
ORDER BY city;
```

- Números → de menor a mayor.
    
- Texto → de A a Z.
    

### Orden descendente

```sql
SELECT customerid, city, country
FROM customers
ORDER BY city DESC;
```

- Números → de mayor a menor.
    
- Texto → de Z a A.
    

### Orden por varias columnas

```sql
SELECT customerid, city, country
FROM customers
ORDER BY country, city;
```

- Primero ordena por `country`.
    
- Si hay repetidos, ordena dentro de ellos por `city`.
    

---

## ✅ Puntos clave

1. **SELECT** → qué columnas quieres.
    
2. **FROM** → de qué tabla vienen los datos.
    
3. **ORDER BY** → organiza la salida (ascendente o descendente, incluso por varias columnas).
    

---


