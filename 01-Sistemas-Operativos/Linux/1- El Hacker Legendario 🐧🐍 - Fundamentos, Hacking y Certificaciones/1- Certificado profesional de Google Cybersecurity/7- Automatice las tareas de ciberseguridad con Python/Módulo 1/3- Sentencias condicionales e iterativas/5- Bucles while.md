
# Bucle `while` en Python

## Qué es

Ejecuta un bloque **mientras** una condición sea `True`. Cuando pasa a `False`, se detiene.

## Forma general

```python
# inicializa variables ANTES del while
i = 0

# cabecera: while <condición>:
while i <= 10:
    # cuerpo indentado: acciones por iteración
    print(i)
    # actualización explícita de la variable de control
    i += 1
```

## Puntos clave (lo del video)

- La **cabecera** lleva `while`, una **condición booleana** y `:`.
    
- La **variable de control** (p. ej., `i` o `tiempo`) **se define antes** del `while`.
    
- En el **cuerpo** debes **actualizar** la variable de control (si no, bucle infinito).
    
- Se usa para repetir en función de una **condición**, no de una secuencia (a diferencia de `for`).
    

---

## Ejemplo 1: contar de 0 a 10 de 2 en 2 (números pares ≤ 10)

```python
tiempo = 0                 # inicialización
while tiempo <= 10:        # condición
    print(tiempo)          # acción
    tiempo += 2            # actualización
```

Salida:

```
0
2
4
6
8
10
```

---

## Ejemplo 2: máximo de dispositivos conectados (mensaje al alcanzar el límite)

```python
max_dispositivos = 5
i = 1

while i < max_dispositivos:
    print("El usuario aún puede conectarse a dispositivos adicionales.")
    i += 1                 # incrementa en cada iteración

print("El usuario ha alcanzado el número máximo de dispositivos conectados.")
```

- El primer mensaje aparece 4 veces (para `i = 1,2,3,4`).
    
- Al llegar `i = 5`, la condición `i < 5` es `False` y se imprime el mensaje final (fuera del bucle).
    

---

## Errores comunes que evitar

- ❌ **Olvidar inicializar** la variable antes del `while`.
    
- ❌ **No actualizar** la variable dentro del cuerpo (provoca bucle infinito).
    
- ❌ Condición imposible de cumplir/cambiar.
    

---

## Variantes útiles

### Usar `break` (salir antes si se cumple algo):

```python
intentos = 0
while intentos < 5:
    intentos += 1
    if intentos == 3:
        print("Cortamos en el intento 3.")
        break
```

### Usar `continue` (saltar al siguiente ciclo):

```python
i = 0
while i < 6:
    i += 1
    if i % 2 != 0:
        continue           # salta impares
    print(i)               # imprime 2,4,6
```

---

