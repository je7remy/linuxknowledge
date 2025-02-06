## **Primer Fragmento: Uso de `argparse` para Capturar Argumentos**

Código:

```python
import argparse

parse = argparse.ArgumentParser(description="Suma de dos numeros")

parse.add_argument("numero1", type=int, help="Primer numero")
parse.add_argument("numero2", type=int, help="Segundo numero")

guardar = parse.parse_args()

primer_numero = guardar.numero1
segundo_numero = guardar.numero2

print(f"El primer numero introducido es {primer_numero} y el segundo numero es {segundo_numero}")
```

### **Explicación Paso a Paso:**

1. **Se importa el módulo `argparse`**
    
    - `argparse` permite manejar argumentos desde la línea de comandos.
2. **Se crea un objeto `ArgumentParser` con una descripción**
    
    - `parse = argparse.ArgumentParser(description="Suma de dos numeros")`
    - La descripción se mostrará si el usuario ejecuta el script con `--help`.
3. **Se añaden dos argumentos obligatorios**
    
    - `parse.add_argument("numero1", type=int, help="Primer numero")`
    - `parse.add_argument("numero2", type=int, help="Segundo numero")`
    - Ambos argumentos son requeridos y deben ser enteros (`type=int`).
4. **Se analizan los argumentos proporcionados por el usuario**
    
    - `guardar = parse.parse_args()`
    - `guardar` es un objeto que contiene los valores introducidos en `numero1` y `numero2`.
5. **Se almacenan los valores en variables para su uso posterior**
    
    - `primer_numero = guardar.numero1`
    - `segundo_numero = guardar.numero2`
6. **Se imprimen los valores introducidos**
    
    - `print(f"El primer numero introducido es {primer_numero} y el segundo numero es {segundo_numero}")`
    - Esto permite verificar que los valores han sido ingresados correctamente.

---

## **Segundo Fragmento: Suma de los Números Capturados**

Código:

```python
import argparse

parse = argparse.ArgumentParser(description="Suma de dos numeros")

parse.add_argument("numero1", type=int, help="Primer numero")
parse.add_argument("numero2", type=int, help="Segundo numero")

guardar = parse.parse_args()

primer_numero = guardar.numero1
segundo_numero = guardar.numero2

resultado = primer_numero + segundo_numero

print("El resultado es: ", resultado)
```

### **Explicación Paso a Paso:**

1. **Se repiten los mismos pasos iniciales del primer fragmento**
    
    - Se importa `argparse`.
    - Se crea el objeto `ArgumentParser` con una descripción.
    - Se añaden los dos argumentos requeridos (`numero1` y `numero2`).
    - Se analizan y almacenan los valores en `guardar`.
2. **Se realiza la suma de los números capturados**
    
    - `resultado = primer_numero + segundo_numero`
    - Se suman los valores obtenidos de los argumentos.
3. **Se imprime el resultado de la suma**
    
    - `print("El resultado es: ", resultado)`
    - Muestra en pantalla el resultado de la operación.

---

## **Ejemplo de Ejecución en la Terminal**

Si ejecutamos el script desde la terminal con los argumentos:

```sh
python script.py 5 10
```

La salida del primer fragmento sería:

```
El primer numero introducido es 5 y el segundo numero es 10
```

Y la salida del segundo fragmento sería:

```
El resultado es: 15
```

Este código es útil cuando queremos manejar argumentos desde la terminal en lugar de usar `input()`, permitiendo automatizar procesos y evitar la interacción manual.