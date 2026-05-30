---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Ejemplo, Examinar la entrada y la salida en el Shell

# 🧪 Laboratorio Bash Shell: Entrada y Salida en Linux

## 🧭 Objetivo del laboratorio

Aprender cómo comunicarse con el sistema operativo Linux a través del shell Bash usando comandos básicos:

- `echo` para mostrar texto
    
- `expr` para cálculos matemáticos
    
- `clear` para limpiar la pantalla
    

---

## 🧑‍💻 Escenario

Como profesional de ciberseguridad, debes dominar cómo interactuar con el shell para realizar tareas básicas como mostrar información, realizar cálculos rápidos y limpiar el entorno de trabajo.

---

## ✅ Tarea 1: Generar salida con `echo`

### 1. Mostrar una cadena simple:

```bash
echo hello
```

**Salida esperada:**

```
hello
```

### 2. Mostrar la misma cadena con comillas:

```bash
echo "hello"
```

**Salida:**

```
hello
```

> Las comillas son útiles para agrupar cadenas con espacios o caracteres especiales.

### 3. Mostrar tu nombre:

```bash
echo "Tu Nombre"
```

**Ejemplo:**

```bash
echo "Jeremy de la Cruz"
```

**Salida esperada:**

```
Jeremy de la Cruz
```

---

## ✅ Tarea 2: Realizar cálculos con `expr`

### 1. Calcular falsos positivos:

Supón que tienes 32 alertas, y solo 8 requieren acción.

```bash
expr 32 - 8
```

**Salida esperada:**

```
24
```

### 2. Calcular intentos de inicio de sesión anual (3500 por mes):

```bash
expr 3500 \* 12
```

> Usa `\*` para escapar el asterisco, o coloca toda la expresión entre comillas dobles:

```bash
expr "3500 * 12"
```

**Salida esperada:**

```
42000
```

---

## ✅ Tarea 3: Limpiar el intérprete de comandos

### Borrar toda la salida anterior del shell:

```bash
clear
```

> El cursor volverá al inicio de la terminal.

---

## 🧪 Tarea opcional: Experimentar más con `echo` y `expr`

### 1. Mostrar un nuevo mensaje:

```bash
echo "Este es un nuevo mensaje"
```

### 2. Realizar un nuevo cálculo:

```bash
expr 25 + 15
```

**Salida:**

```
40
```

> También puedes probar:

```bash
expr 100 / 4
```

---

## ✅ Conclusión del laboratorio

¡Buen trabajo! Ahora dominas lo esencial del shell Bash:

- `echo` para imprimir texto
    
- `expr` para operaciones aritméticas básicas
    
- `clear` para limpiar la pantalla
    

Estas habilidades son **la base para tareas más avanzadas en ciberseguridad y administración de sistemas Linux**.

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[7- Ejemplo opcional, Examinar la entrada y la salida en el shell]]
- ➡️ Siguiente: [[9- Ponga a prueba sus Conocimientos, El shell]]
