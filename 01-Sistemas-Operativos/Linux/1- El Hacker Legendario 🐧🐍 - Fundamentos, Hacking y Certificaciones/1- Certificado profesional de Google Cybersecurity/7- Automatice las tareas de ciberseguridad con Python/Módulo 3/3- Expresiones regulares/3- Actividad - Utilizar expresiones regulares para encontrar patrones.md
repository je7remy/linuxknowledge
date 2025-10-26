
### 🧠 Tarea 1

Importar el módulo `re`.

✅ **Respuesta correcta (Código):**

Python

```
# Import the `re` module in Python
import re
```

_(Esta celda ya está completa)._

---

### 🧠 Tarea 2

...Muestre el contenido de la variable `devices`...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `devices` to a string containing device IDs, each device ID represented by alphanumeric characters
devices = "r262c36 67bv8fy 41j1u2e r151dm4 1270t3o 42dr56i r15xk9h 2j33krk 253be78 ac742a1 r15u9q5 zh86b2l ii286fq 9x482kt 6oa6m6u x3463ac i4l56nq g07h55q 081qc9t r159r1u"

# Display the contents of `devices`
print(devices)
```

---

### 🧠 Tarea 3

...Escriba un patrón para encontrar dispositivos que comiencen con "r15". Use los símbolos `\w` y `+`... almacénelo en `target_pattern`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `devices` to a string containing device IDs, each device ID represented by alphanumeric characters
devices = "r262c36 67bv8fy 41j1u2e r151dm4 1270t3o 42dr56i r15xk9h 2j33krk 253be78 ac742a1 r15u9q5 zh86b2l ii286fq 9x482kt 6oa6m6u x3463ac i4l56nq g07h55q 081qc9t r159r1u"

# Assign `target_pattern` to a regular expression pattern for finding device IDs that start with "r15"
target_pattern = r"r15\w+"
```

_(Nota: Usar `r""` (raw string) es una buena práctica para patrones regex)._

---

### 🧠 Pregunta 1

¿Qué patrón de expresión regular usó? Para cada componente del patrón, ¿qué pasaría si faltara?

✅ Respuesta correcta:

El patrón utilizado es r"r15\w+".

- **`r15`**: Coincide con los caracteres literales "r15" al principio. Si faltara, coincidiría con _cualquier_ secuencia alfanumérica, no solo las que comienzan con "r15".
    
- **`\w`**: Coincide con cualquier carácter alfanumérico (letra, número o guion bajo). Si faltara (dejando solo `r15+`), el patrón buscaría "r1" seguido de _una o más_ "5", lo cual es incorrecto.
    
- **`+`**: Coincide con _una o más_ ocurrencias del carácter anterior (`\w`). Si faltara (dejando `r15\w`), solo coincidiría con IDs que tuvieran _exactamente un_ carácter después de "r15" (ej. "r15a").
    

---

### 🧠 Tarea 4

Use la función `findall()` del módulo `re` para encontrar los IDs de dispositivo que coincidan con `target_pattern`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `devices` to a string containing device IDs, each device ID represented by alphanumeric characters
devices = "r262c36 67bv8fy 41j1u2e r151dm4 1270t3o 42dr56i r15xk9h 2j33krk 253be78 ac742a1 r15u9q5 zh86b2l ii286fq 9x482kt 6oa6m6u x3463ac i4l56nq g07h55q 081qc9t r159r1u"

# Assign `target_pattern` to a regular expression pattern for finding device IDs that start with "r15"
target_pattern = r"r15\w+"

# Use `re.findall()` to find the device IDs that start with "r15" and display the results
print(re.findall(target_pattern, devices))
```

---

### 🧠 Tarea 5

...Muestre el contenido de `log_file` para examinar los detalles.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `log_file` to a string containing username, date, login time, and IP address for a series of login attempts 
log_file = "eraab 2022-05-10 6:03:41 192.168.152.148 \niuduike 2022-05-09 6:46:40 192.168.22.115 \nsmartell 2022-05-09 19:30:32 192.168.190.178 \narutley 2022-05-12 17:00:59 1923.1689.3.24 \nrjensen 2022-05-11 0:59:26 192.168.213.128 \naestrada 2022-05-09 19:28:12 1924.1680.27.57 \nasundara 2022-05-11 18:38:07 192.168.96.200 \ndkot 2022-05-12 10:52:00 1921.168.1283.75 \nabernard 2022-05-12 23:38:46 19245.168.2345.49 \ncjackson 2022-05-12 19:36:42 192.168.247.153 \njclark 2022-05-10 10:48:02 192.168.174.117 \nalevitsk 2022-05-08 12:09:10 192.16874.1390.176 \njrafael 2022-05-10 22:40:01 192.168.148.115 \nyappiah 2022-05-12 10:37:22 192.168.103.10654 \ndaquino 2022-05-08 7:02:35 192.168.168.144"

# Display contents of `log_file`
print(log_file)
```

---

### 🧠 Tarea 6

...construya un patrón de expresión regular que coincida con direcciones IP de la forma `xxx.xxx.xxx.xxx`... almacénelo en `pattern`. Use `\d` y `\.`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `log_file` to a string containing username, date, login time, and IP address for a series of login attempts 
log_file = "..." # (Omitido por brevedad)

# Assign `pattern` to a regular expression pattern that will match with IP addresses of the form xxx.xxx.xxx.xxx
pattern = r"\d\d\d\.\d\d\d\.\d\d\d\.\d\d\d"
```

---

### 🧠 Tarea 7

...use `re.findall()` con el `pattern` y `log_file` para extraer las direcciones IP...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `log_file` to a string...
log_file = "..." # (Omitido por brevedad)

# Assign `pattern` to a regular expression pattern...
pattern = r"\d\d\d\.\d\d\d\.\d\d\d\.\d\d\d"

# Use the `re.findall()` function on `pattern` and `log_file`...
print(re.findall(pattern, log_file))
```

---

### 🧠 Pregunta 2

¿Cuáles son algunos ejemplos de direcciones IP que fueron extraídas? ¿Cuáles son algunos ejemplos de direcciones IP que no fueron extraídas? ¿Alguna de las que no fueron extraídas parece ser una dirección IP válida?

✅ **Respuesta correcta:**

- **Extraídas:** `"192.168.152.148"`, `"192.168.190.178"`, `"192.168.213.128"`, `"192.168.96.200"`, `"192.168.247.153"`, `"192.168.174.117"`, `"192.168.148.115"`, `"192.168.168.144"`. (Todas tienen exactamente 3 dígitos por segmento).
    
- **No Extraídas:** `"192.168.22.115"`, `"1923.1689.3.24"`, `"1924.1680.27.57"`, `"1921.168.1283.75"`, `"19245.168.2345.49"`, `"192.16874.1390.176"`, `"192.168.103.10654"`.
    
- **Válidas pero no extraídas:** Sí, `"192.168.22.115"` parece válida (tiene segmentos con menos de 3 dígitos). Las otras no extraídas parecen inválidas porque tienen segmentos con más de 3 dígitos o números que exceden 255.
    

---

### 🧠 Tarea 8

...ajuste el `pattern` usando el símbolo `+` después de `\d`... use el `pattern` actualizado para extraer...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `log_file` to a string...
log_file = "..." # (Omitido por brevedad)

# Update `pattern` to a regular expression pattern that will match with IP addresses with any variation in the number of digits per segment
pattern = r"\d+\.\d+\.\d+\.\d+"

# Use the `re.findall()` function on `pattern` and `log_file`...
print(re.findall(pattern, log_file))
```

---

### 🧠 Pregunta 3

¿Qué se extrae aquí? ¿Todas las direcciones IP extraídas tienen entre uno y tres dígitos en cada segmento?

✅ Respuesta correcta:

Se extraen todas las secuencias que tienen el formato de números separados por tres puntos. Esto incluye tanto las IPs válidas ("192.168.22.115") como las inválidas que tienen más de tres dígitos por segmento ("1923.1689.3.24", "192.168.103.10654").

No, no todas las extraídas tienen entre uno y tres dígitos; el patrón `\d+` permite _cualquier_ cantidad de dígitos (mayor que cero).

---

### 🧠 Tarea 9

...actualice el `pattern` usando llaves `{1,3}` en lugar del símbolo `+`. ...llame a `re.findall()`... almacene la salida en `valid_ip_addresses`. Muestre `valid_ip_addresses`.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `log_file` to a string...
log_file = "..." # (Omitido por brevedad)

# Assign `pattern` to a regular expression that matches with all valid IP addresses and only those 
pattern = r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"

# Use `re.findall()` on `pattern` and `log_file` and assign `valid_ip_addresses` to the output 
valid_ip_addresses = re.findall(pattern, log_file)

# Display the contents of `valid_ip_addresses`
print(valid_ip_addresses)
```

---

### 🧠 Pregunta 4

¿Qué nota sobre las direcciones IP extraídas aquí en comparación con las extraídas en las dos tareas anteriores?

✅ Respuesta correcta:

Esta vez, las direcciones IP extraídas son solo aquellas que tienen entre 1 y 3 dígitos en cada uno de los cuatro segmentos. Esto excluye las cadenas que tenían segmentos con 4 o más dígitos (ej. "1923.1689.3.24"), pero incluye las que tienen segmentos con menos de 3 dígitos (ej. "192.168.22.115"). Este patrón es mucho más preciso para identificar IPs sintácticamente válidas.

---

### 🧠 Tarea 10

...Muestre la lista `flagged_addresses`...

✅ **Respuesta correcta (Código):**

Python

```
# Assign `flagged_addresses` to a list of IP addresses that have been previously flagged for unusual activity
flagged_addresses = ["192.168.190.178", "192.168.96.200", "192.168.174.117", "192.168.168.144"]

# Display the contents of `flagged_addresses`
print(flagged_addresses)
```

---

### 🧠 Tarea 11

...escriba una sentencia iterativa que recorra `valid_ip_addresses`... incluya un condicional que verifique si `address` pertenece a `flagged_addresses`... muestre el mensaje apropiado.

✅ **Respuesta correcta (Código):**

Python

```
# Assign `log_file` to a string...
log_file = "..." # (Omitido por brevedad)

# Assign `pattern` to a regular expression...
pattern = r"\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}"

# Use `re.findall()`... assign `valid_ip_addresses`...
valid_ip_addresses = re.findall(pattern, log_file)

# Assign `flagged_addresses` to a list...
flagged_addresses = ["192.168.190.178", "192.168.96.200", "192.168.174.117", "192.168.168.144"]

# Iterative statement begins here
# Loop through `valid_ip_addresses` with `address` as the loop variable
for address in valid_ip_addresses:

    # Conditional begins here
    # If `address` belongs to `flagged_addresses`, display "The IP address ______ has been flagged for further analysis."
    if address in flagged_addresses:
        print("The IP address", address, "has been flagged for further analysis.")

    # Otherwise, display "The IP address ______ does not require further analysis."
    else:
        print("The IP address", address, "does not require further analysis.")
```

---

### 🧠 Conclusión

¿Cuáles son sus principales conclusiones de este laboratorio?

✅ **Conclusiones clave:**

- **Importancia de `re`:** El módulo `re` es fundamental para trabajar con expresiones regulares en Python.
    
- **`re.findall()`:** Esta función es muy útil para extraer _todas_ las subcadenas que coinciden con un patrón específico de una cadena más grande, devolviéndolas en una lista.
    
- **Construcción de Patrones Regex:**
    
    - Los caracteres literales (como `"r15"`) coinciden consigo mismos.
        
    - Los metacaracteres como `\w` (alfanumérico) y `\d` (dígito) permiten coincidencias más flexibles.
        
    - Los cuantificadores como `+` (uno o más) y `{m,n}` (entre m y n repeticiones) controlan cuántas veces debe aparecer el carácter o grupo anterior.
        
    - Es necesario escapar caracteres especiales (como el punto `\.`) si se quiere buscar el carácter literal.
        
- **Refinamiento Iterativo:** A menudo, el primer patrón regex no es perfecto. Es un proceso iterativo refinar el patrón (`\d\d\d` -> `\d+` -> `\d{1,3}`) para obtener exactamente las coincidencias deseadas y excluir las no deseadas.
    
- **Integración con otras estructuras:** Las listas devueltas por `re.findall()` pueden ser procesadas fácilmente con bucles `for` y condicionales `if` (usando el operador `in`) para realizar análisis posteriores (como verificar contra una lista de IPs marcadas).