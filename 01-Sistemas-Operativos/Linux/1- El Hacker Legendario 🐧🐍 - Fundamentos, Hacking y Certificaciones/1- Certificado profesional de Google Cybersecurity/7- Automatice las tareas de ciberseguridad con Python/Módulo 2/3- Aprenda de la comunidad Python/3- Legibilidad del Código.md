---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-2]
actualizado: 2026-05-28
---

# Legibilidad del Código

# 🐍 Guías de Estilo en Python (PEP 8)

Una de las ventajas de programar en **Python** es que es un lenguaje muy legible. También ayuda que la comunidad Python comparta un conjunto de directrices que promueven un código limpio y ordenado.  
Se denominan **guías de estilo**.

---

## 📘 ¿Qué es una Guía de Estilo?

Una guía de estilo es un manual que informa sobre la escritura, el formato y el diseño de los documentos.  
En lo que respecta a la programación, las guías de estilo pretenden ayudar a los programadores a seguir convenciones similares.

La **Guía de estilo PEP 8** es un recurso que proporciona directrices de estilo para programadores que trabajan en Python.

---

## 🧩 Significado de PEP

**PEP** es la abreviatura de **Python Enhancement Proposals** (_Propuestas de mejora de Python_).  
PEP 8 proporciona a los programadores sugerencias relacionadas con la sintaxis. No son obligatorias, pero ayudan a crear coherencia entre los programadores para asegurarnos de que los demás puedan entender fácilmente nuestro código.

Se basa esencialmente en el principio de que **el código se lee mucho más a menudo de lo que se escribe**.  
Es un gran recurso para cualquiera que quiera aprender a dar estilo y formato a su código Python de una manera coherente con otros programadores.

---

## 💬 Comentarios en el Código

Por ejemplo, la PEP 8 habla de los **comentarios**.  
Un comentario es una nota que los programadores hacen sobre la intención que hay detrás de su código.

Se insertan en los programas de ordenador para indicar **qué está haciendo el código y por qué**.

PEP 8 da recomendaciones específicas, como:

- Hacer que los comentarios sean **claros**.
    
- Mantenerlos **actualizados** cuando cambie el código.
    

---

### 🧾 Ejemplo sin comentario

Puede que la persona que lo escribió sepa lo que está pasando,  
pero ¿qué pasa con otras personas que necesiten leerlo?

Puede que no entiendan el contexto detrás de la variable `intentos fallidos` y por qué imprime `"Cuenta bloqueada"` si es mayor de 5.  
Y puede que el escritor original necesite volver a visitar este código en el futuro, por ejemplo, para depurar el programa más grande.  
Sin el comentario, también sería menos eficiente.

---

### 🧾 Ejemplo con comentario

En este ejemplo hemos añadido un comentario.  
Todos los lectores pueden entender rápidamente lo que está haciendo nuestro programa y sus variables.

Los comentarios deben ser **breves** y **directos al grano**.

---

## 🧱 Indentación (Sangría)

A continuación, hablemos de otro aspecto importante de la legibilidad del código: **la indentación**.

La indentación es un espacio que se añade al principio de una línea de código.  
Esto **mejora la legibilidad** y garantiza que el código se ejecute correctamente.

Hay casos en los que se debe indentar líneas de código para establecer conexiones con otras líneas de código.  
Esto agrupa las líneas de código sangradas y establece una conexión con una línea de código anterior que no está sangrada.

---

### 🔄 Ejemplo Práctico

El cuerpo de una **sentencia condicional** es un ejemplo de ello.  
Necesitamos asegurarnos de que esta sentencia impresa se ejecute **solo cuando se cumpla la condición**.  
La indentación aquí proporciona esta instrucción a Python.

Si la sentencia impresa no estuviera indentada, Python ejecutaría esta sentencia impresa fuera de la condicional y **siempre imprimiría**.  
Esto sería problemático porque recibiría un mensaje de que se necesitan actualizaciones aunque no sea así.

---

## ⚙️ Recomendación de Espacios

Para aplicar una sangría, debe añadir **al menos un espacio** antes de una línea de código.  
Típicamente, los programadores utilizan **de dos a cuatro espacios** para una mayor claridad visual.  
La **Guía de estilo PEP 8 recomienda cuatro espacios.**

---

## 💡 Experiencia Personal

> En mi primer trabajo de ingeniería, escribí una secuencia de comandos para ayudar a validar y lanzar reglas de firewall.  
> Inicialmente, mi secuencia de comandos funcionaba bien pero se volvió difícil de leer un año después, cuando intentábamos ampliar su funcionalidad.  
> Mis conocimientos de programación y estilo de codificación habían evolucionado durante ese año, al igual que las prácticas de codificación de mis compañeros de equipo.  
> Nuestra organización no utilizaba una guía de estilo de codificación en ese momento, por lo que nuestros códigos eran muy diferentes, difíciles de leer y no escalaban bien.  
> Esto causó muchos problemas y requirió trabajo adicional para solucionarlo.

---

## 🔐 Importancia de las Guías de Estilo

Asegurarse de que el código es legible y puede modificarse con el tiempo es la razón por la que es importante que los **profesionales de la seguridad** se adhieran a las guías de estilo de codificación y por qué las guías de estilo son tan importantes para que las organizaciones las utilicen.

---

## 🚀 Conclusión

La capacidad de escribir código legible es **clave cuando se trabaja en Python**.  
A medida que nos adentremos en la siguiente parte del curso, continuaremos desarrollando prácticas de código eficaces para una mejor legibilidad.

---
## Navegación

- ⬆️ Carpeta: [[_7- Automatice las tareas de ciberseguridad con Python|7- Automatice las tareas de ciberseguridad con Python]]
- ⬅️ Anterior: [[2- Importar módulos y bibliotecas en Python]]
- ➡️ Siguiente: [[4- Garantizar una sintaxis y legibilidad adecuadas en Python]]
