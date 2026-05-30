---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Trabajar con cuerdas

### 🧠 Pregunta 1

¿Cuál de las siguientes afirmaciones describe correctamente las cadenas? (Seleccione todas las que correspondan).

- Las cadenas deben colocarse entre corchetes (`[]`).
    
- Las cadenas deben ir entre comillas (`" "`).
    
- Las cadenas son inmutables.
    
- Las cadenas no pueden contener caracteres numéricos.
    

✅ **Respuestas correctas:**

- Las cadenas deben ir entre comillas (`" "`).
    
- Las cadenas son inmutables.
    

📘 **Explicación:** Las cadenas deben ir entre comillas. Las cadenas también son inmutables. Esto significa que no se pueden cambiar después de haberlas creado y asignado un valor.

---

### 🧠 Pregunta 2

¿Qué devuelve el siguiente código?

Python

```
device_id = "uu0ktt0vwugjyf2"
print(device_id[2:5])
```

- `"0ktt"`
    
- `"u0k"`
    
- `"u0kt"`
    
- `"0kt"`
    

✅ **Respuesta correcta:**`"0kt"`

📘 **Explicación:** Este Código devuelve `"0kt"`. Utiliza la notación entre corchetes para tomar una porción del valor contenido en la variable `device_id`. Los índices comienzan en 0 en Python. Extrae los caracteres en los índices 2, 3 y 4. El carácter en el índice 5 se excluye de la rebanada.

---

### 🧠 Pregunta 3

¿Qué muestra el siguiente Código?

Python

```
device_id = "Tj1C58Dakx"
print(device_id.lower())
```

- `"TJ1C58DAKX"`
    
- `"tj1c58dakx"`
    
- `"Tj1C58Dakx"`
    
- `"tj1C58Dakx"`
    

✅ **Respuesta correcta:**`"tj1c58dakx"`

📘 **Explicación:** Este código muestra `"tj1c58dakx"`. El método `.lower()` convierte todos los caracteres en mayúsculas a minúsculas.

---

### 🧠 Pregunta 4

Desea encontrar el índice donde comienza la subcadena `"192.168.243.140"` dentro de la cadena contenida en la variable `ip_addresses`. Complete el código Python para encontrar y mostrar el índice de inicio.

Python

```
ip_addresses = "192.168.140.81, 192.168.109.50, 192.168.243.140"
# YOUR CODE HERE
print(ip_addresses.index("192.168.243.140"))
```

¿En qué índice comienza la subcadena `"192.168.243.140"`?

- `33`
    
- `31`
    
- `34`
    
- `32`
    

✅ **Respuesta correcta:**`32`

📘 **Explicación:** La Subcadena `"192.168.243.140"` comienza en el índice 32. Puede determinarlo utilizando el código `ip_addresses.index("192.168.243.140")`. Tenga en cuenta que los índices de Python comienzan en 0.

---

## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[5- Actividad - Trabajar con cadenas en Python]]
