---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Depuración de código Python

## 🧠 Pregunta 1

¿Qué tipos de errores puede encontrar mientras depura código? (Seleccione tres).

✅ **Respuestas correctas:**

- **Excepciones**
    
- **Errores lógicos**
    
- **Errores de sintaxis**
    

📘 Justificación:

Los tres tipos principales de errores en programación son: errores de sintaxis (infracciones de las reglas del lenguaje), excepciones (errores que ocurren durante la ejecución aunque la sintaxis sea válida) y errores lógicos (el código se ejecuta pero produce un resultado incorrecto). "Iterativos" se refiere a un tipo de sentencia (como bucles), no a un tipo de error.

---

## 🧠 Pregunta 2

La finalidad de este Código es indicar si es necesario actualizar un sistema operativo concreto. Sin embargo, contiene un error de sintaxis. Ejecute este código, analice su resultado y, a continuación, depúrelo. Basándose en lo que descubra, ¿cómo puede solucionar el error?

(Suponiendo que el código contiene elsif)

✅ Respuesta correcta:

Cambie la palabra clave elsif por elif.

📘 Justificación:

Python utiliza la palabra clave elif (contracción de "else if") para las condiciones intermedias en una estructura if/elif/else. Escribir elsif es un error de ortografía y, por lo tanto, un error de sintaxis porque Python no reconoce esa palabra clave.

---

## 🧠 Pregunta 3

Usted ha escrito un código que asigna tickets [...] Si el nivel de prioridad es 2, debería enviarse al Equipo B. Al probar, observa que un incidente con nivel de prioridad 2 se envía al Equipo A. ¿De qué tipo de error se trata?

✅ Respuesta correcta:

Error lógico

📘 Justificación:

El código se ejecuta sin detenerse (no hay error de sintaxis ni excepción), pero el resultado no es el esperado (el ticket va al equipo incorrecto). Esto indica un fallo en la lógica del programa.

---

## 🧠 Pregunta 4

Usted ha escrito un código que utiliza un algoritmo de búsqueda [...] Al probar, un mensaje de error le indica que se está accediendo a un índice desconocido. ¿De qué tipo de error se trata?

✅ Respuesta correcta:

Excepción

📘 Justificación:

Acceder a un índice que no existe (por ejemplo, el índice 5 en una lista de 5 elementos, cuyos índices van del 0 al 4) provoca un error durante la ejecución del programa. Este tipo de error en tiempo de ejecución se clasifica como una excepción, específicamente un IndexError.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[5- Actividad - Depuración de código Python]]
