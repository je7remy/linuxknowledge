---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# La cláusula WHERE y los operadores básicos

## 🔹 Cómo ayuda el filtrado

En **ciberseguridad**, trabajarás con registros enormes (logs de accesos, dispositivos, etc.).  
El filtrado en SQL permite:

- Encontrar intentos de inicio de sesión de un usuario específico.
    
- Identificar accesos en un momento concreto.
    
- Detectar dispositivos con una versión específica de software.
    

---

## 🔹 La cláusula WHERE

`WHERE` indica la condición que debe cumplir un registro para ser devuelto.

Ejemplo: obtener empleados con el título **IT Staff**:

```sql
SELECT firstname, lastname, title, email
FROM employees
WHERE title = 'IT Staff';
```

➡️ El operador `=` filtra valores exactos.  
👉 Solo devuelve filas donde `title` sea **exactamente igual** a `'IT Staff'`.

---

## 🔹 Filtrado por patrones

A veces no basta con coincidencias exactas.  
Para buscar **patrones**, usamos:

- **Operador**: `LIKE`
    
- **Comodines**: `%` y `_`
    

### Comodines

- `%` → sustituye a **cualquier número de caracteres** (incluido cero).
    
- `_` → sustituye a **un solo carácter**.
    

|Patrón|Devuelve ejemplos|
|---|---|
|`'a%'`|apple123, art, a|
|`'a_'`|as, an, a7|
|`'a__'`|ant, add, a1c|
|`'%a'`|pizza, Z6ra, a|
|`'_a'`|ma, 1a, Ha|
|`'%a%'`|Again, back, a|
|`'_a_'`|Car, ban, ea7|

---

## 🔹 Ejemplos de uso de LIKE

### 1. Títulos que empiecen con "IT"

```sql
SELECT lastname, firstname, title, email
FROM employees
WHERE title LIKE 'IT%';
```

➡️ Devuelve: **IT Manager, IT Staff**, etc.

---

### 2. Estados que empiezan con "N" y tienen 2 letras

```sql
SELECT firstname, lastname, state, country
FROM customers
WHERE state LIKE 'N_';
```

➡️ Devuelve abreviaturas como: **NY, NV, NS, NT**.

---

## 🗝️ Puntos clave

- `WHERE` se usa para filtrar registros.
    
- `=` sirve para coincidencias exactas.
    
- `LIKE` se combina con `%` y `_` para buscar **patrones**.
    
- `%` → cualquier secuencia de caracteres.
    
- `_` → un solo carácter.
    

---

---

## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[5- Filtros básicos en consultas SQL]]
- ➡️ Siguiente: [[7- Filtrar una consulta SQL]]
