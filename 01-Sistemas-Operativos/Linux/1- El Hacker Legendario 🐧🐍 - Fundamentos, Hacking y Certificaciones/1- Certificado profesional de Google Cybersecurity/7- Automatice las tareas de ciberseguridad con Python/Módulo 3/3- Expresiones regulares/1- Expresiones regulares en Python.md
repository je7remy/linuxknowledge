
### 🧠 Introducción a las Expresiones Regulares (Regex)

Ya hemos aprendido a trabajar con cadenas, incluyendo indexación y corte. Sin embargo, a menudo necesitamos buscar **patrones** más complejos, no solo caracteres o subcadenas exactas. Aquí es donde entran las **expresiones regulares**.

Una **expresión regular** (abreviada como **regex**) es una secuencia de caracteres que forma un **patrón de búsqueda**.

**Contexto de Seguridad:**

- Encontrar todas las direcciones IP con un identificador de red específico (ej. que empiecen por "184.").
    
- Localizar nombres de usuario específicos en un registro.
    
- Extraer todas las direcciones de correo electrónico de un archivo de registro, **incluso si no sabes cuáles son de antemano**.
    

---

### ⚙️ ¿Por qué Regex en lugar de `.index()`?

El método `.index()` requiere que conozcas la subcadena exacta que buscas. Como analista de seguridad, rara vez tienes esa información completa.

Con regex, puedes definir la **estructura** de lo que buscas (ej. la estructura de una dirección de correo electrónico) y Python encontrará todas las cadenas que coincidan con esa estructura, sin necesidad de conocer los valores específicos.

---

### 📘 Símbolos Básicos de Regex

|**Símbolo**|**Significado**|**Ejemplo de Patrón**|**Coincide con...**|**No coincide con...**|
|---|---|---|---|---|
|**`+`**|**Una o más** apariciones del carácter _anterior_.|`a+`|`"a"`, `"aaa"`, `"aaaaa"`|`""`, `"b"`, `"aba"`|
|**`\w`**|Cualquier **carácter alfanumérico** (letras a-z, A-Z, números 0-9) y el guion bajo (`_`). **No** coincide con símbolos como `@` o `.`.|`\w`|`"1"`, `"k"`, `"i"`, `"_"`|`"@"`, `"."`, `" "` (espacio)|

---

### ⚙️ Combinando Símbolos: `\w+`

Puedes combinar símbolos para crear patrones más potentes.

- **`\w+`**: Coincide con **una o más** (`+`) apariciones de **cualquier carácter alfanumérico** (`\w`). En esencia, coincide con una **palabra** o secuencia alfanumérica de cualquier longitud.
    
    - Coincide con: `"192"`, `"abc123"`, `"security"`.
        

---

### 📘 Construyendo un Regex para Correos Electrónicos

Pensemos en la estructura de un correo electrónico típico: `usuario@dominio.com`

1. **Parte del Usuario (`usuario`):** Suele ser una secuencia alfanumérica de longitud variable.
    
    - **Regex:** `\w+`
        
2. **Símbolo `@`:** Siempre presente.
    
    - **Regex:** `@` (se escribe literalmente)
        
3. **Nombre del Dominio (`dominio`):** Otra secuencia alfanumérica de longitud variable.
    
    - **Regex:** `\w+`
        
4. **Punto (`.`):** Siempre presente. ¡Pero el punto tiene un significado especial en regex! Para buscar un punto literal, debemos "escaparlo" con una barra invertida (`\`).
    
    - **Regex:** `\.`
        
5. **Extensión del Dominio (`com`):** Otra secuencia alfanumérica (puede ser "com", "net", "org", etc.).
    
    - **Regex:** `\w+`
        

Regex Completo para Correos Electrónicos:

Juntando todas las partes, obtenemos: \w+@\w+\.\w+

Este patrón es específico: buscará secuencias alfanuméricas separadas por `@` y `.`, excluyendo otras cadenas.

---

### ⚙️ Usando Regex en Python: El Módulo `re`

Para usar expresiones regulares en Python, necesitas importar el módulo `re`.

**Función Clave: `re.findall()`**

- **Sintaxis:** `re.findall(patron, cadena_donde_buscar)`
    
- **¿Qué hace?:** Busca **todas** las apariciones del `patron` dentro de la `cadena_donde_buscar`.
    
- **¿Qué devuelve?:** Una **lista** que contiene todas las coincidencias encontradas.
    

**Ejemplo Práctico:**

Python

```
# 1. Importar el módulo re
import re

# 2. Definir la cadena donde buscar (puede ser un registro largo)
#    (Usamos triples comillas para cadenas multilínea)
email_log = """
User elarson logged in from 192.168.1.1 with email elarson@example.com
Failed login for tshah from 10.0.0.5, email tshah@sample.net
Successful login for bmoreno, email bmoreno@example.com
"""

# 3. Definir el patrón regex para correos electrónicos
email_pattern = r"\w+@\w+\.\w+" 
# La 'r' antes de las comillas indica una "raw string", 
# útil para evitar problemas con las barras invertidas en regex.

# 4. Usar re.findall() para encontrar todas las coincidencias
emails_encontrados = re.findall(email_pattern, email_log)

# 5. Imprimir la lista de resultados
print(emails_encontrados)
```

📤 **Salida:**

```
['elarson@example.com', 'tshah@sample.net', 'bmoreno@example.com']
```

¡Obtenemos una lista con todos los correos electrónicos encontrados en la cadena original!

---

### 💡 Conclusión

Esto es solo una introducción al poder de las expresiones regulares. Existen muchos más símbolos y técnicas que puedes usar para crear patrones muy específicos y complejos. Te animo a que explores las expresiones regulares por tu cuenta para aprender más.



---

### 🧠 Pregunta

¿Qué cadena coincide con la expresión regular `"b\wa+b"`?

- `"baaa"`
    
- `"bkaaab"`
    
- `"yaaab"`
    
- `"cba"`
    

---

### ✅ Respuesta correcta:

`"bkaaab"`

---

### 📘 Explicación:

La Cadena `"bkaaab"` coincide con la expresión regular `"b\wa+b"`. Analicemos el patrón paso a paso:

1. **`b`**: El primer carácter debe ser exactamente **"b"**.
    
2. **`\w`**: El siguiente carácter debe ser cualquier carácter **alfanumérico** (letras a-z, A-Z, números 0-9, o guion bajo `_`). En `"bkaaab"`, este es `"k"`.
    
3. **`a+`**: Después, debe haber **una o más** (`+`) apariciones consecutivas del carácter **"a"**. En `"bkaaab"`, esto coincide con `"aaa"`.
    
4. **`b`**: La cadena debe **terminar** exactamente con **"b"**.
    

La cadena `"bkaaab"` cumple todas estas condiciones.

**¿Por qué las otras no coinciden?**

- `"baaa"`: Le falta el carácter alfanumérico (`\w`) después de la primera `"b"`.
    
- `"yaaab"`: No comienza con `"b"`.
    
- `"cba"`: No comienza con `"b"` y no tiene la estructura `\wa+`.