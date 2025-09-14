
# 📘 Funciones de agregación en SQL

En SQL, las **funciones de agregación** son funciones que realizan un cálculo sobre varios puntos de datos y devuelven un único valor como resultado.

Los datos reales no se devuelven, sino un resumen de esos datos.

---

## 🔹 Funciones principales:

- **COUNT** → devuelve un único número que representa el número de filas devueltas por la consulta.
    
- **AVG** → devuelve un único número que representa la media de los datos numéricos de una columna.
    
- **SUM** → devuelve un único número que representa la suma de los datos numéricos de una columna.
    

---

## 🔹 Sintaxis básica de funciones de agregación

Para utilizar una función de agregación, se coloca después de la palabra clave `SELECT` y, a continuación, entre paréntesis, la columna sobre la que deseas realizar el cálculo.

---

# 🧩 Ejemplos prácticos

---

### ✅ Ejemplo 1 – Contar todos los clientes

```sql
SELECT COUNT(firstname)
FROM customers;
```

🔸 **Explicación:**  
Se cuenta la cantidad de registros en la tabla `customers`. Aunque uses cualquier columna (`firstname`, `lastname` o incluso `*`), el resultado será el mismo, porque devuelve el número de filas que no son `NULL`.

👉 **Ejecución simulada en base de datos:**

|COUNT(firstname)|
|---|
|100|

_(Imaginemos que hay **100 clientes en total** en la tabla.)_

---

### ✅ Ejemplo 2 – Contar clientes de un país específico

```sql
SELECT COUNT(firstname)
FROM customers
WHERE country = 'USA';
```

🔸 **Explicación:**  
Aquí añadimos un filtro con `WHERE`. Solo se cuentan aquellos clientes que tienen `'USA'` en la columna `country`.

👉 **Ejecución simulada en base de datos:**

|COUNT(firstname)|
|---|
|25|

_(Esto indica que hay **25 clientes en USA**.)_

---

### ✅ Ejemplo 3 – Calcular el promedio de edades de clientes

```sql
SELECT AVG(age)
FROM customers;
```

🔸 **Explicación:**  
La función `AVG()` calcula la media aritmética de los valores numéricos en la columna `age`.

👉 **Ejecución simulada en base de datos:**

|AVG(age)|
|---|
|34.6|

_(Esto significa que la **edad promedio** de los clientes es de 34.6 años.)_

---

### ✅ Ejemplo 4 – Calcular la suma de compras de todos los clientes

```sql
SELECT SUM(purchase_amount)
FROM customers;
```

🔸 **Explicación:**  
`SUM()` agrega todos los valores numéricos de la columna `purchase_amount` (por ejemplo, el monto de compras de los clientes).

👉 **Ejecución simulada en base de datos:**

|SUM(purchase_amount)|
|---|
|152430.50|

_(El total de todas las compras es **152,430.50 dólares**.)_

---

# 🧩 Ejemplo con GROUP BY (más avanzado)

Las funciones de agregación también se combinan con `GROUP BY` para resumir información por grupos (ejemplo: clientes por país).

---

### ✅ Ejemplo 5 – Contar clientes por país

```sql
SELECT country, COUNT(firstname)
FROM customers
GROUP BY country;
```

👉 **Ejecución simulada en base de datos:**

|country|COUNT(firstname)|
|---|---|
|USA|25|
|Canada|15|
|Mexico|20|
|Spain|10|
|Germany|30|

_(Aquí vemos cuántos clientes hay **en cada país**.)_

---

### ✅ Ejemplo 6 – Promedio de edad por país

```sql
SELECT country, AVG(age)
FROM customers
GROUP BY country;
```

👉 **Ejecución simulada en base de datos:**

|country|AVG(age)|
|---|---|
|USA|32.1|
|Canada|30.5|
|Mexico|28.9|
|Spain|35.4|
|Germany|40.2|

_(Esto muestra la **edad promedio de los clientes por país**.)_

---

### ✅ Ejemplo 7 – Total de compras por país

```sql
SELECT country, SUM(purchase_amount)
FROM customers
GROUP BY country;
```

👉 **Ejecución simulada en base de datos:**

|country|SUM(purchase_amount)|
|---|---|
|USA|55430.00|
|Canada|30210.50|
|Mexico|20500.00|
|Spain|10020.00|
|Germany|36430.50|

_(Aquí se muestra el **total de compras acumuladas** en cada país.)_

---

# 📌 Puntos clave para el aprendizaje

1. Las funciones de agregación permiten obtener **estadísticas rápidas** sobre los datos.
    
2. Se pueden combinar con `WHERE` para filtrar.
    
3. Se pueden usar con `GROUP BY` para segmentar los resultados.
    
4. Se aplican en **ciberseguridad** para:
    
    - Contar intentos fallidos de inicio de sesión.
        
    - Calcular promedios de ataques por usuario o por IP.
        
    - Sumar tráfico malicioso detectado en logs.
        

---

