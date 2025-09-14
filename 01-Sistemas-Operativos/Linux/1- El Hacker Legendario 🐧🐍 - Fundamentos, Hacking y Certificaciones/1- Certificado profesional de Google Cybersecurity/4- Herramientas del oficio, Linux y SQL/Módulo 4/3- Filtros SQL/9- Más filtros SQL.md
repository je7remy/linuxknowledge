
## **Pregunta 1**

❓ _¿Qué filtro da como resultado todos los registros con valores en la columna `date` entre '01-01-2015' y '01-04-2015'?_

Opciones:

1. `WHERE date BETWEEN '01-01-2015', '01-04-2015';`
    
2. `WHERE date > '01-01-2015';`
    
3. `WHERE date BETWEEN '01-01-2015' AND '01-04-2015';` ✅
    
4. `WHERE date < '01-04-2015';`
    

**Respuesta correcta:** **Opción 3**  
**Explicación:** El operador **BETWEEN … AND …** devuelve los registros que están dentro del rango, incluyendo las fechas límites.

---

## **Pregunta 2**

❓ _¿Qué operador es más eficaz para devolver todos los registros con un `status` distinto de `'successful'`?_

Opciones:

1. `NOT` ✅
    
2. `OR`
    
3. `AND`
    
4. `BETWEEN`
    

**Respuesta correcta:** **Opción 1 (NOT)**  
**Ejemplo:**

```sql
WHERE NOT status = 'successful';
```

**Explicación:** El operador **NOT** niega la condición, devolviendo todos los registros cuyo estado no sea `'successful'`.

---

## **Pregunta 3**

❓ _En la base de datos Chinook, obtener nombres y apellidos de clientes cuyo `country` sea `'Brazil'` o `'Argentina'`._

Consulta correcta:

```sql
SELECT firstname, lastname, country
FROM customers
WHERE country = 'Brazil' OR country = 'Argentina';
```

Opciones de respuesta:

1. 1 cliente
    
2. 5 clientes
    
3. 6 clientes ✅
    
4. 4 clientes
    

**Respuesta correcta:** **Opción 3 (6 clientes)**  
**Explicación:** Con el filtro `WHERE country = 'Brazil' OR country = 'Argentina'`, se obtienen los registros de ambos países y el total es **6 clientes**.

---

## **Pregunta 4**

❓ _Consulta:_

```sql
SELECT *
FROM customers
WHERE country = 'USA' AND state = 'NV';
```

Opciones:

1. Clientes que no tienen `'USA'` en country pero sí `'NV'` en state.
    
2. Clientes que no tienen `'USA'` en country o no tienen `'NV'` en state.
    
3. Clientes que tienen `'USA'` en country **o** `'NV'` en state.
    
4. Clientes que tienen `'USA'` en country **y** `'NV'` en state. ✅
    

**Respuesta correcta:** **Opción 4**  
**Explicación:** El operador **AND** requiere que ambas condiciones se cumplan al mismo tiempo: que el cliente sea de USA **y** que su estado sea Nevada (NV).

---
