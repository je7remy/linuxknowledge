
### 🧠 Resumen: Funciones Integradas (Built-in) de Python

Además de crear tus propias funciones, Python ofrece una gran cantidad de **funciones integradas** (o _built-in_). Estas son funciones que ya existen en Python y pueden ser llamadas directamente.

Ya conoces algunas de las más comunes:

- **`print()`**: Envía un objeto específico (texto, números, etc.) a la pantalla.
    
- **`type()`**: Devuelve el tipo de dato de su entrada (ej. `str`, `int`, `list`).
    

---

### ⚙️ "Anidación" de Funciones (Usar Funciones Juntas)

A menudo, necesitarás usar múltiples funciones juntas, pasando el resultado de una función como argumento para otra. Esto se conoce como "anidación".

**Ejemplo:**

Python

```
print(type("Hello"))
```

**Orden de Ejecución (de adentro hacia afuera):**

1. **Función Interna:** Primero se ejecuta `type("Hello")`. Esta función _devuelve_ (retorna) un valor: `<class 'str'>`.
    
2. **Función Externa:** El valor devuelto (`<class 'str'>`) se convierte en el argumento para la función `print()`.
    
3. **Resultado:** `print()` muestra ese valor en la pantalla.
    

📤 **Salida:**

```
<class 'str'>
```

---

### 💡 El "Contrato" de la Función: Entradas y Salidas

Antes de usar cualquier función integrada, debes conocer sus "reglas" o su "contrato":

1. **Parámetros Esperados:** ¿Cuántos argumentos acepta?
    
    - `type()`: Acepta **solo un** argumento.
        
    - `print()`: Acepta **cualquier cantidad** de argumentos.
        
2. **Tipos de Datos de Entrada:** ¿Qué tipos de datos espera?
    
    - `print()`: Acepta **cualquier tipo** (cadenas, enteros, flotantes, etc.).
        
    - `max()`: Espera **números**.
        
3. **Salida (Valor de Retorno):** ¿Qué tipo de dato produce (devuelve)?
    
    - `type()`: Devuelve un objeto de tipo `type`.
        
    - `sorted()`: Devuelve una nueva `list`.
        

Usar un tipo de dato incorrecto o un número incorrecto de argumentos resultará en un error (comúnmente un `TypeError`).

---

### 📘 Ejemplos de Nuevas Funciones Integradas

Aquí hay un par de nuevas funciones integradas muy útiles:

|**Función**|**Descripción**|**Ejemplo de Código**|**Salida**|
|---|---|---|---|
|**`max()`**|Devuelve la entrada numérica más grande que se le haya pasado. Acepta múltiples argumentos.|`a = 3` `b = 9` `c = 6` `print(max(a, b, c))`|`9`|
|**`sorted()`**|Ordena los componentes de una lista. Para números, los ordena de menor a mayor. Para cadenas, los ordena **alfabéticamente**.|`usernames = ["bmoreno", "tshah", "elarson"]` `print(sorted(usernames))`|`['bmoreno', 'elarson', 'tshah']`|

Estas son solo algunas de las muchas funciones integradas que Python ofrece. A medida que trabajes más con Python, te familiarizarás con más funciones que pueden ayudarte a simplificar tus programas.