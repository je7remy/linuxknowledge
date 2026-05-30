---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Operadores para filtrar fechas y números

# Números, Fechas y Horas en Ciberseguridad

Anteriormente, examinó operadores como **menor que (`<`)** o **mayor que (`>`)** y exploró cómo pueden utilizarse en el filtrado de tipos de datos numéricos y de fecha y hora. Esta lectura resume lo aprendido y proporciona **nuevos ejemplos** del uso de operadores en filtros.

## Datos que manejan los analistas de seguridad

Los analistas de seguridad no sólo trabajan con **datos de cadena** (secuencia ordenada de caracteres), sino también con:

- **Datos numéricos**  
    Ejemplos:
    
    - Número de intentos de inicio de sesión
        
    - Recuento de un tipo específico de entrada de registro
        
    - Volumen de datos enviados desde una fuente
        
    - Volumen de datos enviados a un destino
        
- **Datos de fecha y hora**  
    Ejemplos:
    
    - Fechas y horas de inicio de sesión
        
    - Fechas de los parches aplicados
        
    - Duración de una conexión
        
    - Timestamps en registros
        

## Operadores de comparación en SQL

En SQL, el filtrado de datos numéricos y de fecha/hora suele implicar operadores.

|Operador|Uso|
|---|---|
|`<`|Menor que|
|`>`|Mayor que|
|`=`|Igual a|
|`<=`|Menor o igual que|
|`>=`|Mayor o igual que|
|`<>`|No igual a|
|`!=`|Alternativa para no igual a|

### Ejemplo con fechas

```sql
SELECT firstname, lastname, birthdate
FROM employees
WHERE birthdate > '1970-01-01';
```

🔎 Esta consulta devuelve empleados nacidos **después del 1 de enero de 1970**.

- Si usamos `>=`, también incluirá los nacidos **exactamente** en esa fecha.
    
- `>` → Exclusivo (no incluye el valor).
    
- `>=` → Inclusivo (incluye el valor).
    

## Operador BETWEEN

El operador **BETWEEN** permite filtrar dentro de un rango de números o fechas.

### Ejemplo con fechas

```sql
SELECT firstname, lastname, hiredate
FROM employees
WHERE hiredate BETWEEN '2002-01-01' AND '2003-01-01';
```

📌 Esta consulta devuelve empleados contratados **entre el 1 de enero de 2002 y el 1 de enero de 2003, inclusive**.

👉 El operador **BETWEEN es inclusivo**, por lo que incluye ambos extremos del rango.

## Puntos clave

- Los operadores son fundamentales para filtrar datos numéricos y de fecha/hora.
    
- **Exclusivos**: `<`, `>` → no incluyen el valor de comparación.
    
- **Inclusivos**: `<=`, `>=`, `BETWEEN` → sí incluyen el valor de comparación.
    
- `BETWEEN` es ideal para trabajar con rangos definidos de números o fechas.
    

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[1- Filtrar fechas y números]]
- ➡️ Siguiente: [[3- Aplicar más filtros en SQL]]
