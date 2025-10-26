
## 🧠 Pregunta 1

¿Cuál de los siguientes signos potenciales de actividad sospechosa puede rastrear con programas automatizados de Python? (Seleccione todas las que correspondan).

✅ **Respuestas correctas:**

- Si se produjeron **varios intentos fallidos de inicio de sesión** en un breve espacio de tiempo.
    
- Si se produjeron intentos de inicio de sesión desde **direcciones IP que no son zonas de trabajo establecidas**.
    
- Si los intentos de inicio de sesión se produjeron **fuera del horario normal de trabajo**.
    

📘 Justificación:

Python puede analizar archivos de registro para extraer y comparar marcas de tiempo (para verificar horarios y frecuencia de eventos) y direcciones IP (para verificar ubicaciones o listas de permitidos). El phishing en persona es un método de ataque social y no se registra de forma que Python pueda rastrearlo directamente.

---

## 🧠 Pregunta 2

¿Qué componente de Python contribuye a la automatización al permitirle realizar las mismas acciones un número determinado de veces basándose en una secuencia?

✅ Respuesta correcta:

Bucles for

📘 Justificación:

Los bucles for están diseñados específicamente para iterar sobre los elementos de una secuencia (como una lista, una cadena o un range()), ejecutando un bloque de código un número predeterminado de veces (una vez por cada elemento de la secuencia). Los bucles while iteran basados en una condición, no necesariamente un número fijo de veces sobre una secuencia.

---

## 🧠 Pregunta 3

¿Por qué es importante saber trabajar con archivos para la Automatización?

✅ Respuesta correcta:

La información relacionada con la ciberseguridad suele encontrarse en los archivos de registro.

📘 Justificación:

Gran parte de la automatización en ciberseguridad implica leer, procesar y analizar datos contenidos en archivos, especialmente archivos de registro (.log, .txt, .csv, etc.), que registran eventos del sistema, intentos de inicio de sesión, tráfico de red, etc.

---

## 🧠 Pregunta 4

¿Cuál de los siguientes es un formato de archivo común para los registros de Seguridad? (Seleccione todos los que correspondan).

✅ **Respuestas correctas:**

- `.txt`
    
- `.csv`
    

📘 Justificación:

Los registros de seguridad se almacenan comúnmente como archivos de texto plano (.txt) o archivos de valores separados por comas (.csv) porque son formatos legibles por humanos y fáciles de procesar mediante programación. .jpeg y .gif son formatos de imagen.

---

# Justificación oficial


---

### 🧠 Pregunta 1

¿Cuál de los siguientes signos potenciales de actividad sospechosa puede rastrear con programas automatizados de Python? (Seleccione todas las que correspondan).

- Si se produjeron varios intentos fallidos de inicio de sesión en un breve espacio de tiempo
    
- Si se produjeron intentos de inicio de sesión desde direcciones IP que no son zonas de trabajo establecidas
    
- Si los intentos de inicio de sesión se produjeron fuera del horario normal de trabajo
    
- Si los intentos de Phishing se produjeron a través de interacciones en persona
    

✅ **Respuestas correctas:**

- Si se produjeron **varios intentos fallidos de inicio de sesión** en un breve espacio de tiempo.
    
- Si se produjeron intentos de inicio de sesión desde **direcciones IP que no son zonas de trabajo establecidas**.
    
- Si los intentos de inicio de sesión se produjeron **fuera del horario normal de trabajo**.
    

📘 Justificación:

Utilizando programas Python automatizados, puede hacer un seguimiento de si se produjeron varios intentos de inicio de sesión fallidos en un breve espacio de tiempo, si los intentos de inicio de sesión se produjeron fuera de las horas normales de trabajo y si los intentos de inicio de sesión se produjeron desde direcciones IP que no son zonas de trabajo establecidas. En todos estos casos, puede obtener los Datos necesarios (marcas de tiempo, IPs) para la automatización con Python.

---

### 🧠 Pregunta 2

¿Qué componente de Python contribuye a la automatización al permitirle realizar las mismas acciones un número determinado de veces basándose en una secuencia?

- Notación entre corchetes
    
- Bucles `for`
    
- Bucles `while`
    
- Sentencias condicionales
    

✅ Respuesta correcta:

Bucles for

📘 Justificación:

Los bucles for de Python contribuyen a la automatización al permitirle realizar la misma acción un determinado número de veces basándose en una secuencia (como una lista o un range()).

---

### 🧠 Pregunta 3

¿Por qué es importante saber trabajar con archivos para la Automatización?

- Los métodos Cadena y Lista sólo son accesibles a través de archivos.
    
- La información relacionada con la ciberseguridad suele encontrarse en los archivos de registro.
    
- Es necesario guardar un archivo para poder revisar lo que ha automatizado.
    
- Para crear una función, es necesario incorporarle un archivo.
    

✅ Respuesta correcta:

La información relacionada con la ciberseguridad suele encontrarse en los archivos de registro.

📘 Justificación:

Saber trabajar con archivos es importante para la automatización, ya que la información relevante para la ciberseguridad (eventos, logs, etc.) se encuentra a menudo en archivos de registro.

---

### 🧠 Pregunta 4

¿Cuál de los siguientes es un formato de archivo común para los registros de Seguridad? (Seleccione todos los que correspondan).

- `.txt`
    
- `.csv`
    
- `.jpeg`
    
- `.gif`
    

✅ **Respuestas correctas:**

- `.txt`
    
- `.csv`
    

📘 Justificación:

Los formatos de archivo habituales para los registros de Seguridad son .txt (texto plano) y .csv (valores separados por comas). Ambos formatos son tipos de archivos de texto, lo que significa que sólo contienen texto sin formato, facilitando la extracción de datos mediante programación. .jpeg y .gif son formatos de imagen.

