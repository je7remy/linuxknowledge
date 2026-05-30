---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Más sobre filtros con AND, OR y NOT


# Operadores lógicos en SQL

## Introducción

Los operadores **AND**, **OR** y **NOT** permiten filtrar consultas para devolver información específica que ayuda en el trabajo como analista de seguridad.  
Todos ellos se consideran **operadores lógicos**.

---

## Operador AND (Y)

- **Uso:** filtrar a partir de dos condiciones que deben cumplirse simultáneamente.
    
- **Ejemplo de ciberseguridad:**  
    Un problema podría afectar solo a clientes gestionados por un representante con **ID 5** y que además estén en **EE.UU.**
    

```sql
SELECT firstname, lastname, email, country, supportrepid
FROM customers
WHERE supportrepid = 5 AND country = 'USA';
```

📌 **Resultado:** 4 filas con los clientes que cumplen ambas condiciones.  
➡️ Esta información puede usarse para contactarlos respecto al problema de seguridad.

---

## Operador OR (O)

- **Uso:** conecta dos condiciones, devolviendo resultados en los que se cumpla la primera, la segunda o ambas.
    
- **Ejemplo de ciberseguridad:**  
    Necesitamos encontrar a todos los clientes que estén en **EE.UU. o Canadá** para comunicar una actualización de seguridad.
    

```sql
SELECT firstname, lastname, email, country
FROM customers
WHERE country = 'Canada' OR country = 'USA';
```

📌 **Resultado:** Devuelve todos los clientes de EE.UU. o Canadá.

⚠️ **Nota:** aunque ambas condiciones se basen en la misma columna, deben escribirse completas:

```sql
WHERE country = 'Canada' OR country = 'USA';
```

---

## Operador NOT (NO)

- **Uso:** niega una condición, devolviendo registros que **no coincidan** con ella.
    
- **Ejemplo de ciberseguridad:**  
    Un problema **no afecta a clientes de EE.UU.**, pero sí podría afectar a otros países.
    

```sql
SELECT firstname, lastname, email, country
FROM customers
WHERE NOT country = 'USA';
```

📌 **Resultado:** Devuelve todos los clientes que **no son de EE.UU.**

💡 **Consejo profesional:**  
Existen otras formas equivalentes para negar una condición:

```sql
WHERE country <> 'USA';
WHERE country != 'USA';
```

---

## Combinación de operadores lógicos

Los operadores se pueden **combinar** para crear filtros más específicos.

**Ejemplo:** excluir tanto a EE.UU. como a Canadá porque no están afectados.

```sql
SELECT firstname, lastname, email, country
FROM customers
WHERE NOT country = 'Canada' AND NOT country = 'USA';
```

📌 **Resultado:** Devuelve todos los clientes de países distintos a EE.UU. y Canadá.

---

## Claves principales

- **AND** → ambas condiciones deben cumplirse.
    
- **OR** → una o ambas condiciones pueden cumplirse.
    
- **NOT** → niega una condición (excluye registros).
    
- Se pueden **combinar** para crear filtros más avanzados y enfocados a las necesidades de seguridad.
    

---

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[4- Filtrados con AND, OR y NOT]]
- ➡️ Siguiente: [[6- Laboratorio Filtrado con AND, OR y NOT]]
