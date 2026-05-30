---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Expresiones regulares

### 🧠 Pregunta 1

¿Qué símbolo de expresión regular representa **una o más** apariciones de un carácter específico?

- `+`
    
- `*`
    
- `\d`
    
- `\w`
    

✅ Respuesta correcta:

+

📘 Explicación:

El símbolo + representa una o varias apariciones de un carácter específico.

- `*`: Cero o más apariciones.
    
- `\d`: Un dígito.
    
- `\w`: Un carácter alfanumérico.
    

---

### 🧠 Pregunta 2

Como analista de Seguridad, usted es responsable de encontrar los ID de los empleados que terminan con la secuencia `"a6v"`. Dado que los IDs constan de caracteres alfanuméricos y tienen una longitud mínima de cuatro caracteres, ¿qué patrón regex usaría?

- `"\w+a6v"`
    
- `"a6v"`
    
- `"\wa6v"`
    
- `"\w*a6v"`
    

✅ Respuesta correcta:

"\w+a6v"

📘 Explicación:

La expresión regular "\w+a6v" coincide con cadenas que:

1. Contienen **uno o más** (`+`) caracteres **alfanuméricos** (`\w`) al principio. Esto asegura una longitud mínima de 1 + 3 = 4 caracteres.
    
2. Terminan exactamente con la secuencia `"a6v"`.
    

---

### 🧠 Pregunta 3

Ha importado el módulo `re`. Desea usar `findall()` para buscar en la cadena `text` todas las coincidencias con el patrón regex en la variable `pattern`. ¿Cuál es la llamada correcta?

- `re.findall(text, pattern)`
    
- `re.findall(pattern, text)`
    
- `findall(pattern, text)`
    
- `findall(text, pattern)`
    

✅ Respuesta correcta:

re.findall(pattern, text)

📘 Explicación:

La llamada correcta a la función es re.findall(pattern, text). La función re.findall() devuelve una lista de coincidencias.

1. Debe especificar que la función procede del módulo `re` (`re.`).
    
2. El **primer argumento** es el patrón de expresión regular (`pattern`).
    
3. El **segundo argumento** es la cadena donde buscar (`text`).
    

---

### 🧠 Pregunta 4

¿Cuál de las siguientes cadenas devolvería Python como coincidencias con el patrón de expresión regular `"\w+"`? (Seleccione todas las que correspondan).

- `""`
    
- `"3"`
    
- `"FirstName"`
    
- `"#name"`
    

✅ **Respuestas correctas:**

- `"3"`
    
- `"FirstName"`
    

📘 Explicación:

Las cadenas "3" y "FirstName" coinciden con el patrón "\w+".

- El símbolo `\w` coincide con cualquier carácter **alfanumérico** (letras, números, guion bajo).
    
- El símbolo `+` representa **una o más** apariciones de dicho carácter.
    
- `"3"` contiene un carácter alfanumérico.
    
- `"FirstName"` contiene varios caracteres alfanuméricos.
    
- `""` no tiene _uno o más_ caracteres.
    
- `"#name"` contiene `#`, que _no_ es alfanumérico.

---
# Repaso

---

## 🧩 Evaluación: Expresiones Regulares en Python

### **Pregunta 1**

**¿Qué símbolo de expresión regular representa una o más apariciones de un carácter específico?**  
✅ **Respuesta correcta:** `+`  
**Explicación:**  
El símbolo `+` representa **una o más apariciones** de un carácter específico en una cadena.

---

### **Pregunta 2**

**Como analista de Seguridad, usted es responsable de encontrar los ID de empleados que terminan con "a6v". Los ID contienen letras y números y tienen una longitud mínima de cuatro caracteres. ¿Qué patrón usaría?**  
✅ **Respuesta correcta:** `"\w+a6v"`  
**Explicación:**

- `\w+` → uno o más caracteres alfanuméricos
    
- `a6v` → secuencia final requerida  
    El patrón coincide con cualquier cadena alfanumérica que **termine en "a6v"** y tenga **al menos cuatro caracteres**.
    

---

### **Pregunta 3**

**Ha importado el módulo `re` en Python. ¿Qué llamada a la función permite buscar coincidencias en una cadena?**  
✅ **Respuesta correcta:** `re.findall(pattern, text)`  
**Explicación:**

- `re.findall()` devuelve **una lista con todas las coincidencias** del patrón.
    
- El **primer argumento** es el patrón (`pattern`).
    
- El **segundo argumento** es la cadena donde buscar (`text`).
    

---

### **Pregunta 4**

**¿Cuáles de las siguientes cadenas coinciden con el patrón `\w+`?**  
✅ **Respuestas correctas:**

- `"3"`
    
- `"FirstName"`
    

**Explicación:**

- `\w` → cualquier carácter alfanumérico (letra, número o guion bajo).
    
- `+` → una o más apariciones.  
    Por tanto, `"3"` y `"FirstName"` cumplen el patrón, mientras que `""` (vacío) y `"#name"` no.
    

---
## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[3- Actividad - Utilizar expresiones regulares para encontrar patrones]]
