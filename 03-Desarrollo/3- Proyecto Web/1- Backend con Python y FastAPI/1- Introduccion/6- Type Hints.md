
---

# Módulo 2: Fundamentos de Python Moderno para Backend

## Lección 2.1: Type Hints (Anotaciones de Tipo) y Tipado Dinámico

Bienvenidos a una de las lecciones más cruciales para entender cómo **FastAPI** logra su magia. Antes de escribir APIs, debemos entender cómo ha evolucionado Python.

### 1. El Pasado y el Presente: Tipado Dinámico

Históricamente, Python es famoso por ser un lenguaje de **tipado dinámico**.

¿Qué significa esto en la práctica?

Significa que Python "adivina" o interpreta el tipo de dato (si es un número, un texto, una lista) en el momento exacto en que se ejecuta la línea de código (tiempo de ejecución o runtime), no antes. Las variables no son "cajas fijas" donde solo caben manzanas; son "etiquetas" que puedes pegar a una manzana hoy y a una naranja mañana.

Analicemos la **primera parte de tu código** para demostrar esto:

Python

```
# --- BLOQUE 1: Tipado Dinámico Puro ---
my_string_variable = "My String variable"
print(my_string_variable)
print(type(my_string_variable)) 
# Salida: <class 'str'>

my_string_variable = 5
print(my_string_variable)
print(type(my_string_variable))
# Salida: <class 'int'>
```

**Explicación Técnica:**

1. Al inicio, `my_string_variable` apunta a un objeto en memoria que es un texto (`str`).
    
2. Sin previo aviso, reasignamos la **misma variable** al valor `5`.
    
3. Python no se queja. Simplemente cambia la etiqueta. Ahora la variable es de tipo entero (`int`).
    

El Problema en Desarrollo Profesional:

En scripts pequeños, esto es cómodo. Pero en una API con miles de líneas de código, si esperas un email (string) y recibes un 5 (int), tu aplicación fallará cuando el usuario la esté usando. No tendrás advertencias previas.

---

### 2. La Revolución: Type Hints (Anotaciones de Tipo)

A partir de Python 3.6+, se introdujeron los **Type Hints**. Esto nos permite "sugerir" de qué tipo debería ser una variable.

Veamos la **segunda parte de tu código**:

Python

```
# --- BLOQUE 2: Uso de Type Hints ---
my_typed_variable: str = "My typed String variable"
print(my_typed_variable)
print(type(my_typed_variable))
# Salida: <class 'str'>

my_typed_variable = 5
print(my_typed_variable)
print(type(my_typed_variable))
# Salida: <class 'int'>
```

#### **🛑 Punto Crítico**

Observa cuidadosamente el código anterior. Definimos `my_typed_variable: str`. Le dijimos explícitamente que es un TEXTO. Sin embargo, después le asignamos un `5`... **¡y el código se ejecutó sin errores!**

¿Por qué?

Esta es una pregunta de examen: Python, por sí mismo, ignora los Type Hints en tiempo de ejecución. El intérprete de Python ve : str, lo toma como una nota informativa y sigue adelante. No te impide cometer el error de asignar un número.

Entonces, ¿para qué sirven?

Si Python los ignora, ¿por qué son fundamentales en FastAPI? Por tres razones que cambian las reglas del juego:

#### A. Soporte del Editor (IntelliSense)

Aunque Python ejecute el código, tu editor (VS Code, PyCharm) **SÍ** lee los Type Hints.

- Si intentas hacer `my_typed_variable.upper()`, el editor te ayudará porque sabe que es un string.
    
- Si le asignas un `5`, el editor subrayará el código en rojo antes de que lo ejecutes, advirtiéndote del error lógico.
    

#### B. Legibilidad y Documentación

El código se vuelve autodocumentado.

- `def procesar_pago(monto)` -> ¿Monto es un `int`, `float`, o `string` con símbolo de moneda?
    
- `def procesar_pago(monto: float)` -> Queda claro instantáneamente.
    

#### C. El Superpoder de FastAPI: Validación de Datos


> **FastAPI no ignora los tipos.**

FastAPI utiliza una librería llamada **Pydantic** que se toma los Type Hints muy en serio.

Si creas una API con FastAPI así:

Python

```
@app.get("/items/{item_id}")
def read_item(item_id: int):
    return {"item_id": item_id}
```

Y un usuario intenta enviar una petición a `/items/foo` (donde "foo" es un texto):

1. Python normal aceptaría "foo".
    
2. **FastAPI leerá el Type Hint (`int`)**.
    
3. Validará el dato entrante.
    
4. Al ver que "foo" no es un entero, **FastAPI detendrá la ejecución y devolverá un error automático al cliente** diciendo: _"El valor no es un número entero válido"_.
    

---

### Resumen de la Lección

En esta lección hemos aprendido que:

1. **Python es dinámico:** Puedes cambiar tipos de variables al vuelo, lo cual es flexible pero riesgoso.
    
2. **Type Hints (`variable: tipo`):** Son anotaciones que introdujo Python moderno.
    
3. **Ejecución vs. Análisis:** Python estándar ignora los hints al ejecutarse (por eso tu código con el `5` funcionó), pero los editores los usan para prevenir errores mientras programas.
    
4. **Rol en FastAPI:** FastAPI utiliza estos Type Hints para realizar **validación de datos**, **conversión de tipos** (serialización) y generar **documentación automática** (Swagger UI). Sin Type Hints, FastAPI no podría hacer su magia.
    

---

