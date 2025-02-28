
---

#Python #ManejoDeExcepciones #TryExcept #ErroresPython #Programacion

---
### Explicación paso a paso:

1. **Manejo de error de índice fuera de rango:**
    
    ```python
    lista = [1,2,3]
    
    try:
        elemento = lista[9]
    except:
        print("Error: Numero fuera de rango")
    ```
    
    - Se intenta acceder al índice 9 de una lista que solo tiene 3 elementos.
    - Esto genera un `IndexError`, el cual es capturado por la cláusula `except`.
    - Se imprime `"Error: Numero fuera de rango"`, pero aquí el `except` captura cualquier error, no solo `IndexError`.
2. **Manejo más específico del error de índice:**
    
    ```python
    lista = [1,2,3]
    
    try:
        elemento = lista[9]
    except IndexError as error:
        print(f"Error: Numero fuera de rango, {error}")
    ```
    
    - Similar al caso anterior, pero ahora se maneja específicamente `IndexError`.
    - Se muestra un mensaje más detallado incluyendo la descripción del error.
3. **Manejo de error al convertir una cadena a número entero:**
    
    ```python
    try:
        numero = int('abc')
    except ValueError as error:
        print(f"Error: No se puede convertir a entero: {error}")
    ```
    
    - Se intenta convertir la cadena `'abc'` en un número entero, lo cual genera un `ValueError`.
    - Se captura la excepción y se imprime un mensaje con el error.
4. **Manejo de error con `finally`:**
    
    ```python
    try:
        numero = int('abc')
    except ValueError as error:
        print(f"Error: No se puede convertir a entero: {error}")
    finally:
        print("Este mensaje siempre se ejecutara")
    ```
    
    - Similar al caso anterior, pero ahora se incluye `finally`.
    - La cláusula `finally` asegura que su código se ejecutará siempre, independientemente de si ocurre una excepción o no.
5. **Conversión correcta de un número entero con `finally`:**
    
    ```python
    try:
        numero = int(5)
        print("El numero es un entero, todo correcto")
    except ValueError as error:
        print(f"Error: No se puede convertir a entero: {error}")
    finally:
        print("Este mensaje siempre se ejecutara")
    ```
    
    - `int(5)` es una conversión válida, por lo que el bloque `try` se ejecuta sin problemas.
    - El mensaje `"El numero es un entero, todo correcto"` se muestra.
    - `finally` se ejecuta siempre, por lo que también se imprime `"Este mensaje siempre se ejecutara"`.
6. **Manejo de interrupción del teclado (`KeyboardInterrupt`):**
    
    ```python
    try:
        while True:
            pass
    except KeyboardInterrupt:
        print("Se ha interrumpido la ejecucion del programa con ctrl + c")
    ```
    
    - Se inicia un bucle infinito con `while True: pass`.
    - Si el usuario presiona `Ctrl + C`, se genera un `KeyboardInterrupt`, que es capturado en `except`.
    - Se imprime `"Se ha interrumpido la ejecucion del programa con ctrl + c"`.
7. **Manejo de importación fallida (`ImportError`):**
    
    ```python
    try:
        import requests
    except ImportError:
        print("Error, libreria no instalada, instalala con pip")
    ```
    
    - Se intenta importar la librería `requests`.
    - Si no está instalada, se genera un `ImportError`, capturado en `except`.
    - Se imprime `"Error, libreria no instalada, instalala con pip"`.

---

### Código completo:

```python
# Manejo de error de índice fuera de rango
lista = [1,2,3]

try:
    elemento = lista[9]
except:
    print("Error: Numero fuera de rango")

# Manejo específico del error de índice
lista = [1,2,3]

try:
    elemento = lista[9]
except IndexError as error:
    print(f"Error: Numero fuera de rango, {error}")

# Manejo de error al convertir una cadena en un número
try:
    numero = int('abc')
except ValueError as error:
    print(f"Error: No se puede convertir a entero: {error}")

# Manejo de error con finally
try:
    numero = int('abc')
except ValueError as error:
    print(f"Error: No se puede convertir a entero: {error}")
finally:
    print("Este mensaje siempre se ejecutara")

# Conversión correcta con finally
try:
    numero = int(5)
    print("El numero es un entero, todo correcto")
except ValueError as error:
    print(f"Error: No se puede convertir a entero: {error}")
finally:
    print("Este mensaje siempre se ejecutara")

# Manejo de interrupción del teclado
try:
    while True:
        pass
except KeyboardInterrupt:
    print("Se ha interrumpido la ejecucion del programa con ctrl + c")

# Manejo de ImportError
try:
    import requests
except ImportError:
    print("Error, libreria no instalada, instalala con pip")
```

---
