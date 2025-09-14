
# Operadores lógicos en SQL aplicados a Seguridad

## Contexto

En la lección aprendimos que, al trabajar con **consultas SQL** para Seguridad, muchas veces es necesario **filtrar por varias condiciones**.  
Por ejemplo, una vulnerabilidad puede depender de:

- Un **cliente de correo electrónico específico**
    
- En un **sistema operativo específico**
    

En estos casos, necesitamos usar operadores lógicos: **AND, OR y NOT**.

---

## Operador AND

- **Función:** Requiere que ambas condiciones se cumplan al mismo tiempo.
    
- **Ejemplo (frutas):** Buscar solo manzanas **grandes y frescas**.
    
    - No incluirá manzanas pequeñas aunque estén frescas.
        
    - No incluirá manzanas grandes si están podridas.
        
- **Ejemplo (SQL):**
    
    ```sql
    SELECT * 
    FROM maquinas
    WHERE os = 'OS 1'
      AND email_client = 'Cliente de correo electrónico 1';
    ```
    
- **Resultado:** Lista de máquinas que cumplen ambas condiciones.
    

---

## Operador OR

- **Función:** Es suficiente que se cumpla **una de las condiciones**.
    
- **Ejemplo (diagrama de Venn):** Se seleccionan registros que cumplen una condición u otra, o ambas.
    
- **Ejemplo (SQL):**
    
    ```sql
    SELECT * 
    FROM maquinas
    WHERE os = 'OS 1'
       OR os = 'OS 3';
    ```
    
- **Resultado:** Lista de máquinas que tengan OS 1 o OS 3.
    

📌 **Pregunta de práctica:**  
**¿Por qué podría un analista de Seguridad utilizar el operador OR?**

👉 **Respuesta correcta:**  
Para encontrar los números de identificación de todos los empleados que trabajan en **EE.UU. o Canadá**.

- El operador **OR** especifica que puede cumplirse cualquiera de las dos condiciones.
    

---

## Operador NOT

- **Función:** Excluye una condición específica.
    
- **Ejemplo (frutas):** Buscar cualquier fruta que **no sea manzana**.
    
- **Ejemplo (SQL):**
    
    ```sql
    SELECT * 
    FROM maquinas
    WHERE NOT os = 'OS 3';
    ```
    
- **Resultado:** Lista de máquinas que **no ejecutan OS 3**.
    

---

## Resumen final

- **AND** → Ambas condiciones deben cumplirse.
    
- **OR** → Basta con que se cumpla una condición.
    
- **NOT** → Excluye registros que cumplan una condición.
    

✔️ Estos operadores permiten crear consultas complejas y útiles en el trabajo de un analista de Seguridad.

---

# ¿Por qué podría un analista de Seguridad utilizar el operador OR?

La respuesta correcta es:

**Para encontrar los números de identificación de todos los empleados que trabajan en EE.UU. o Canadá.**

✅ El operador **OR** en SQL se utiliza cuando cualquiera de las condiciones puede cumplirse. En este caso, un analista de Seguridad podría necesitar identificar empleados que trabajen en **EE.UU. o en Canadá**, sin importar si cumplen ambas condiciones al mismo tiempo.

En cambio:

- **AND** se usaría cuando ambas condiciones deben cumplirse juntas.
    
- **NOT** se usaría cuando queremos excluir una condición.
    
