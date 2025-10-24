
### 🧠 Crear y Llamar a una Función (Definida por el Usuario)

Para usar funciones personalizadas, el proceso siempre consta de dos pasos:

1. **Definir la Función:** Es el proceso de crear la función. Le "dices" a Python que esta función existe y qué instrucciones debe ejecutar.
    
2. **Llamar a la Función:** Es el proceso de ejecutar la función. Le dices a Python: "ejecuta el código que definí antes".
    

Si solo defines una función pero nunca la llamas, su código **nunca se ejecutará**.

---

### 📘 Paso 1: Definir la Función (La Sintaxis)

Para definir una función, se utiliza la palabra clave `def`, seguida de un nombre, paréntesis y dos puntos. El código que pertenece a la función (su "cuerpo") debe estar indentado.

Python

```
# Comentario: Definir una función que saluda al empleado
def greet_employee():
    # Cuerpo de la función (debe estar indentado)
    print("Este es el mensaje de bienvenida al iniciar sesión.")
```

**Desglose de la Sintaxis:**

- `def`: La palabra clave que le indica a Python que estás a punto de **def**inir una función.
    
- `greet_employee`: El nombre que le das a tu función.
    
- `()`: Paréntesis. Más adelante se usarán para pasar información a la función, pero por ahora se dejan vacíos.
    
- `:`: Dos puntos. Indican el final del "encabezado" de la función.
    
- `print(...)`: El **cuerpo** de la función. Es el bloque de código que se ejecutará _cuando_ se llame a la función. Debe tener sangría.
    

---

### ⚙️ Paso 2: Llamar a la Función (La Ejecución)

Una vez definida, puedes "llamar" (ejecutar) la función escribiendo su nombre seguido de los paréntesis. Ya tienes experiencia haciendo esto con funciones integradas como `print()`.

Python

```
# Comentario: Llamar a nuestra función para que se ejecute
greet_employee()
```

---

### 💡 Ejemplo Completo y Resultado

Juntar ambos pasos se ve así:

Python

```
# 1. DEFINICIÓN: Le decimos a Python qué hacer
def greet_employee():
    print("Bienvenido, ha iniciado sesión.")

# Si ejecutáramos solo el código anterior, no pasaría nada.

# 2. LLAMADA: Le decimos a Python que lo haga AHORA
greet_employee()
```

📤 **Salida:**

```
Bienvenido, ha iniciado sesión.
```