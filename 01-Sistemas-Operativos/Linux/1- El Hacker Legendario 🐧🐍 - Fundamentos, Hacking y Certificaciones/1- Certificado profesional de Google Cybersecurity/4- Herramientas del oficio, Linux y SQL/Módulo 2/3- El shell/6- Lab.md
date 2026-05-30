---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Lab

### 🧪 **Objetivo del lab**

- Aprender a comunicarse con el sistema operativo Linux usando la **shell Bash**.
    
- Entender cómo los comandos reciben **entradas**, generan **resultados** o producen **mensajes de error**.
    

---

### 💻 **Comandos que usarás**

1. `echo` – Para mostrar texto o cadenas en la shell.
    
2. `expr` – Para realizar operaciones matemáticas básicas.
    
3. `clear` – Para limpiar la pantalla de la terminal.
    

---

### 🔐 **Importancia para seguridad**

Como analista de seguridad, debes:

- Saber ingresar comandos correctamente.
    
- Reconocer cuándo los comandos generan **resultados** o **errores**.
    
- Realizar cálculos simples o verificar salidas.
    

---

### 📋 **Pasos del lab**

#### 🟩 **Tarea 1: Usar `echo`**

- Comando básico:
    
    ```bash
    echo hello
    ```
    
- Resultado:
    
    ```
    hello
    ```
    
- Comillas son opcionales pero útiles:
    
    ```bash
    echo "hello"
    ```
    
- Personalización:
    
    ```bash
    echo "Jeremy"
    ```
    

#### 🟦 **Tarea 2: Usar `expr`**

- Restar alertas:
    
    ```bash
    expr 32 - 8
    # Resultado: 24
    ```
    
- Multiplicar intentos de acceso por mes:
    
    ```bash
    expr 3500 * 12
    # Resultado: 42000
    ```
    
- Reglas:
    
    - Usa espacios entre cada número y operador.
        
    - Solo admite **números enteros** (no decimales).
        

#### 🟨 **Tarea 3: Usar `clear`**

- Comando:
    
    ```bash
    clear
    ```
    
- Limpia la pantalla para trabajar en un entorno más ordenado.
    

#### 🟪 **Tarea opcional**

- Experimentar con más comandos `echo` y `expr`.  
    Ejemplos:
    
    ```bash
    echo "Linux rocks"
    expr 25 + 15
    ```
    

---

### ✅ **Conclusión**

Ahora sabes cómo:

- Generar texto con `echo`
    
- Hacer cálculos con `expr`
    
- Limpiar la terminal con `clear`
    
- Diferenciar entre entrada, salida y error
    

Estos comandos son esenciales para tareas básicas en Linux, especialmente en el campo de la **ciberseguridad**.

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ⬅️ Anterior: [[5- Actividad, Examinar la entrada y salida en el shell]]
- ➡️ Siguiente: [[7- Ejemplo opcional, Examinar la entrada y la salida en el shell]]
