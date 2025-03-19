
---

#Python #Funciones #Programación #Código #Desarrollo #PythonBasics #Dev #Programador #CodingTips #AprenderPython 🚀

---
### **Definición de Funciones en Python**

En Python, una **función** es un bloque de código reutilizable que realiza una tarea específica. Se define con la palabra clave `def`, seguida del nombre de la función y paréntesis `()`, que pueden contener parámetros opcionales. El código dentro de la función se ejecuta cuando esta es llamada.

---

### **Análisis del Código Proporcionado**

1. **Primera función (`saludar()`)**
    
    ```python
    def saludar():
        print("Hola, te mando saludos, Jeremy!!")
    saludar()
    ```
    
    - Se define una función sin parámetros.
    - Al llamarla, imprime un mensaje fijo.
2. **Función `saludar(nombre)`**
    
    ```python
    def saludar(nombre):
        print("Hola, te mando saludos", nombre)
    saludar("Mario")
    ```
    
    - Se define una función que recibe un parámetro `nombre`.
    - Al llamarla con `"Mario"`, imprime un saludo personalizado.
3. **Función `saludar(nombre, edad)`**
    
    ```python
    def saludar(nombre, edad):
        print(f"Hola, te mando saludos {nombre} con {edad} años")
    saludar("Jeremy", 21)
    ```
    
    - Se define una función con dos parámetros: `nombre` y `edad`.
    - Usa una f-string para imprimir un mensaje con esos valores.
4. **Función `sumar(numero1, numero2)` con `return`**
    
    ```python
    def sumar(numero1, numero2):
        return numero1 + numero2
    resultado = sumar(2, 21)
    print(resultado)
    ```
    
    - Recibe dos números y devuelve su suma con `return`.
    - Se guarda el resultado en una variable y se imprime.
5. **Función `sumar(numero1, numero2)` con `print` dentro**
    
    ```python
    def sumar(numero1, numero2):
        resultado_dentro_funcion = numero1 + numero2
        print(resultado_dentro_funcion)
    resultado = sumar(2, 21)
    ```
    
    - Similar a la anterior, pero en vez de usar `return`, imprime el resultado dentro de la función.
6. **Función `sumar(numero1, numero2)` sin `return` ni `print` correcto**
    
    ```python
    def sumar(numero1, numero2):
        resultado_dentro_funcion = numero1 + numero2
    resultado = sumar(2, 21)
    print(resultado_dentro_funcion)  # ERROR
    ```
    
    - **Error:** `resultado_dentro_funcion` no está definido fuera de la función.
    - Para corregirlo, debería devolver el resultado con `return`.
7. **Función `verificar_edad(nombre, edad)`**
    
    ```python
    def verificar_edad(nombre, edad):
        if edad >= 18:
            print("Eres mayor de edad", nombre)
        else:
            print("Eres menor de edad", nombre)
    verificar_edad("Juan", 14)
    ```
    
    - Evalúa si la persona es mayor de edad.
    - Imprime un mensaje adecuado según la edad.

---

### **Conclusión**

- Las **funciones** permiten organizar el código en bloques reutilizables.
- **Parámetros** permiten personalizar el comportamiento de una función.
- **`return`** devuelve valores de la función, mientras que **`print`** solo los muestra.
- Es importante **definir correctamente las variables** y usarlas dentro del alcance adecuado.🚀