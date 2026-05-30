---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-4]
actualizado: 2026-05-28
---

# Aplicar estrategias de Depuración

## 🐛 Proceso de Depuración del Script de Análisis de Logs

El objetivo del código es analizar una línea de registro (código de estado HTTP, fecha, hora, nombre de aplicación), **excepto** si el código de estado es 200, en cuyo caso debe imprimir un mensaje indicando que no es necesario analizar.

### Paso 1: Identificar y Corregir Error de Sintaxis (`SyntaxError`) ⌨️

1. **Ejecución Inicial:** Al ejecutar el código por primera vez, aparece un `SyntaxError`.
    
2. **Mensaje de Error:** Indica que el error está en la línea de **definición de la función** (`def ...`).
    
3. **Diagnóstico:** Se revisa la línea y se observa que **faltan los dos puntos (`:`)** al final del encabezado de la función.
    
4. **Corrección:** Se añaden los dos puntos (`:`) faltantes.
    

---

### Paso 2: Identificar y Corregir Excepción (`NameError`) 📛

1. **Segunda Ejecución:** Tras corregir la sintaxis, se ejecuta de nuevo. Ahora aparece un `NameError` (un tipo de Excepción).
    
2. **Mensaje de Error:** Indica que la variable `application_name` no se reconoce ("name ... is not defined") en el punto donde se intenta usar (al añadirla a `parsed_line`).
    
3. **Diagnóstico:** Se busca dónde se asignó originalmente la variable y se descubre un **error tipográfico**: se escribió con una sola 'p' (`aplication_name`) en lugar de dos (`application_name`).
    
4. **Corrección:** Se corrige la ortografía de la variable en su asignación inicial.
    

---

### Paso 3: Identificar y Corregir Error Lógico ❓

1. **Tercera Ejecución:** El código se ejecuta sin mensajes de error.
    
2. **Prueba Específica:** Se prueba el código con una línea de registro que tiene el código de estado **200**.
    
3. **Resultado Incorrecto:** El código _analiza_ la línea y devuelve la lista parseada, en lugar de imprimir el mensaje "Evento exitoso, no es necesario analizarlo". Esto es un **error lógico**.
    
4. **Estrategia de Depuración:** Se usan **sentencias `print()`** temporales en puntos clave para rastrear el flujo:
    
    - Antes de la línea `return parsed_list`.
        
    - Justo antes del `if` que comprueba si el código es 200.
        
    - Dentro del bloque `if` para el código 200.
        
5. **Observación:** Solo se ejecuta la primera sentencia `print()`. El programa nunca llega a la comprobación del código 200.
    
6. **Diagnóstico:** La sentencia **`return parsed_list`** se ejecuta _antes_ de la comprobación `if codigo_estado == 200`. Una sentencia `return` hace que la función termine inmediatamente.
    
7. **Corrección:**
    
    - Se eliminan las sentencias `print()` de depuración.
        
    - Se **mueve el bloque `if`** (que comprueba el código 200) para que se ejecute **antes** de la sentencia `return parsed_list`.
        

---

### Paso 4: Verificación Final ✅

1. **Última Ejecución:** Se ejecuta el código corregido de nuevo con la entrada de código de estado 200.
    
2. **Resultado Correcto:** Ahora se imprime el mensaje esperado: "Evento exitoso, no es necesario analizarlo".
    
3. **Conclusión:** Se han corregido los errores de sintaxis, excepción y lógica. El código funciona según lo previsto.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[2- Matt - Aprender de los errores]]
- ➡️ Siguiente: [[4- Explore las técnicas de depuración]]
