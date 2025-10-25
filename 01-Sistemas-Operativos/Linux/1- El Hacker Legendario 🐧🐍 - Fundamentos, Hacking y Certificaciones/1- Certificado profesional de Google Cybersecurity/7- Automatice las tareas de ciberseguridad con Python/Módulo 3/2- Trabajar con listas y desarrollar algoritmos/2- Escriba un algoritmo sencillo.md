
### 🧠 Introducción a los Algoritmos

En nuestra vida cotidiana, con frecuencia seguimos reglas para resolver problemas. Como ejemplo sencillo, imagine que quiere una taza de café. Si ha hecho café muchas veces, entonces es probable que siga un proceso para prepararlo.

1. Coge su taza favorita.
    
2. Pone agua en la cafetera y añade los posos del café.
    
3. Pulsa el botón de inicio y espera unos minutos.
    
4. Por último, disfruta de su taza de café recién hecho.
    

Incluso si tiene un enfoque diferente o no bebe café, es probable que siga un conjunto de reglas para completar tareas cotidianas similares. Cuando completa estas tareas rutinarias, está siguiendo un **algoritmo**.

---

### 📘 ¿Qué es un Algoritmo?

Un **algoritmo** es un **conjunto de reglas que resuelven un problema**.

Más detalladamente, un algoritmo es un conjunto de pasos que:

1. Toma una **entrada** de un problema.
    
2. Utiliza esta entrada para realizar **tareas**.
    
3. Devuelve una **solución** como salida.
    

---

### ⚙️ Algoritmos en Python: Ejemplo de Seguridad

Exploremos cómo los algoritmos pueden utilizarse para resolver problemas en Python. Imagine que usted, como analista de Seguridad, tiene una lista de direcciones IP. Quiere extraer los tres primeros dígitos de cada dirección IP, lo que le dará información sobre las redes a las que pertenecen.

Para ello, vamos a escribir un algoritmo que involucra múltiples conceptos de Python que hemos cubierto hasta ahora: **bucles**, **listas** y **cadenas**.

Entrada: Una lista con direcciones IP (almacenadas como cadenas).

(Por razones de privacidad, no mostraremos las direcciones IP completas).

Python

```
lista_ip = ["198.567.xxx.xxx", "123.456.xxx.xxx", "200.100.xxx.xxx"] # Ejemplo
```

**Objetivo (Salida):** Extraer los tres primeros números de cada dirección y almacenarlos en una nueva lista.

---

### 💡 Desglose del Problema (El Enfoque Algorítmico)

Antes de escribir código Python, es una buena idea dividir el problema en pasos más pequeños:

1. **Problema Simplificado:** ¿Cómo extraer los tres primeros dígitos de _una sola_ dirección IP?
    
    - **Solución:** Usar el **corte (slicing) de cadenas**.
        
2. **Problema Completo:** ¿Cómo aplicar la solución anterior a _cada_ dirección IP de la lista?
    
    - **Solución:** Usar un **bucle (`for`)**.
        

---

### ⚙️ Paso 1: Resolver el Problema Simplificado (Corte de Cadenas)

Previamente, ha aprendido sobre el corte de cadenas. Escribamos algo de código Python para resolver el problema para una dirección IP.

Python

```
# Empezamos con una dirección IP
address = "198.567.xxx.xxx"

# Usaremos la notación entre corchetes para trocear la cadena
# Recordatorio: Python empieza a contar en 0.
# Para obtener los tres primeros caracteres, empezamos en 0 y terminamos ANTES de 3.
print(address[0:3])
```

📤 **Salida:**

```
198
```

Obtenemos los tres primeros dígitos de la dirección: 198.

---

### ⚙️ Paso 2: Aplicar la Solución a Toda la Lista (Bucles y `append()`)

Ahora que somos capaces de resolver este problema para una dirección IP, podemos poner este código en un bucle y aplicarlo a todas las direcciones IP de la lista original.

Antes de hacerlo, introduzcamos un método más que utilizaremos: el método `.append()`.

- **Método `.append()`:** Añade entradas **al final** de una lista.
    
    - **Ejemplo:**
        
        Python
        
        ```
        mi_lista = [1, 2, 3]
        mi_lista.append(4)
        print(mi_lista) # Salida: [1, 2, 3, 4]
        ```
        

**Código Completo del Algoritmo:**

Python

```
# 1. Entrada: Lista de IPs
lista_ip = ["198.567.xxx.xxx", "123.456.xxx.xxx", "200.100.xxx.xxx"] # Ejemplo

# 2. Preparación: Crear una lista vacía para almacenar los resultados
networks = []

# 3. Proceso (Bucle): Iterar sobre cada dirección en la lista de IPs
for address in lista_ip:
    # 3.1 Tarea: Extraer los 3 primeros caracteres (usando el código del Paso 1)
    primeros_tres_digitos = address[0:3]
    
    # 3.2 Tarea: Añadir el resultado a la nueva lista
    networks.append(primeros_tres_digitos)

# 4. Salida: Imprimir la lista resultante
print(networks)
```

📤 **Salida:**

```
['198', '123', '200']
```

La variable `networks` contiene ahora una lista de los tres primeros dígitos de cada dirección IP de la lista original `lista_ip`.

---

### ⚠️ Conclusión y Consejo

Eso ha sido un montón de Información. Diseñar algoritmos puede ser todo un reto.

> **Es una buena idea dividirlos en problemas más pequeños antes de lanzarse a escribir su código.**

