---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Filtrar fechas y números

# Filtros en SQL con cadenas, números y fechas

En este vídeo, vamos a seguir utilizando las consultas y los filtros de SQL, pero ahora los vamos a aplicar a los nuevos tipos de datos.

## Tipos de datos comunes en bases de datos

1. **Datos de cadena**  
    Son datos que consisten en una secuencia ordenada de caracteres. Estos caracteres pueden ser números, letras o símbolos.
    
    - Ejemplo: un nombre de usuario como `analyst10`.
        
2. **Datos numéricos**  
    Son datos que constan de números, como el recuento de intentos de inicio de sesión.
    
    - A diferencia de las cadenas, en los numéricos se pueden usar operaciones matemáticas como la multiplicación o la suma.
        
3. **Datos de fecha y hora**  
    Representan una fecha u hora.
    
    - Anteriormente aplicábamos filtros mediante cadenas de datos, pero ahora trabajaremos con datos numéricos y de fecha y hora.
        
    - Como analista de seguridad, con frecuencia necesitará consultar números y fechas.
        
    - Ejemplos:
        
        - Filtrar las fechas de parches para encontrar las máquinas que necesitan actualización.
            
        - Filtrar intentos de inicio de sesión para mostrar solo los realizados en un período de tiempo.
            

## Operadores comunes

Al trabajar con números o fechas, los operadores más usados son:

- `=` igual
    
- `>` mayor que
    
- `<` menor que
    
- `!=` no igual a
    
- `>=` mayor o igual que
    
- `<=` menor o igual que
    

### Ejemplo: intentos de inicio de sesión después de las 18:00

Podemos identificar patrones sospechosos con el operador `>`:

```sql
SELECT * 
FROM log_in_attempts
WHERE time > '18:00';
```

Esto devuelve una lista de los intentos de inicio de sesión realizados después de las 6 p. m.

## Operador BETWEEN

`BETWEEN` permite filtrar números o fechas dentro de un rango.

### Ejemplo: parches instalados entre el 1 de marzo y el 1 de septiembre de 2021

```sql
SELECT *
FROM machines
WHERE OS_Patch_Date BETWEEN '2021-03-01' AND '2021-09-01';
```

Esto devuelve una lista de todas las máquinas parcheadas en ese rango de fechas.

## Nota importante

- Al filtrar por **cadenas, fechas y horas**, se utilizan **comillas** para especificar lo que buscamos.
    
- Para los **números**, **no se utilizan comillas**.
    

---

### ❓ Pregunta

¿Qué cláusula de **WHERE** tiene la sintaxis correcta para devolver todos los registros que tengan un valor de **5, 6, 7 o 8** en la columna `event_id`?

- `WHERE event_id BETWEEN 5,8;`
    
- `WHERE event_id BETWEEN 5 AND 8;` ✅
    
- `WHERE event_id BETWEEN 4 AND 9;`
    
- `WHERE event_id BETWEEN 4,9;`
    

---

### ✅ Respuesta Correcta

`WHERE event_id BETWEEN 5 AND 8;`

Devuelve todos los registros que tienen un valor de **5, 6, 7 u 8** en la columna `event_id`.

📌 El operador **BETWEEN** filtra los valores dentro de un rango:

- Se coloca antes del primer valor a incluir.
    
- Luego se usa **AND**.
    
- Finalmente se indica el último valor a incluir en el rango.
    

---

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ➡️ Siguiente: [[2- Operadores para filtrar fechas y números]]
