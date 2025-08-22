
# 📘 Bienvenido

En este vídeo, vamos a discutir algunos recursos que están disponibles directamente a través del **shell** y que pueden ayudarle mientras trabaja en Linux.

Una de las grandes ventajas de Linux es que puede obtener **ayuda directamente a través de la línea de comandos**.

---

## 🔹 Comando `man`

El primer comando que puede ayudarle es:

```bash
man <comando>
```

- `man` muestra información sobre otros comandos y cómo funcionan.
    
- El nombre de este comando proviene de la palabra **manual**.
    

**Ejemplo:**

```bash
man usermod
```

👉 Esto devolverá:

- Una **descripción general** del comando.
    
- Información sobre **cada una de las opciones**.
    
    - Ejemplo: la opción `-d` puede añadirse a `usermod` para cambiar el directorio personal de un usuario.
        

---

## 🔹 Comando `whatis`

`man` puede ser muy detallado, pero a veces solo necesitamos una referencia rápida.  
Para eso existe:

```bash
whatis <comando>
```

- Muestra una **descripción corta en una sola línea**.
    

**Ejemplo:**

```bash
whatis tail
```

👉 Resultado: explica que `tail` muestra la **última parte de los archivos**.

---

## 🔹 Comando `apropos`

¿Qué pasa si ni siquiera sabemos qué comando buscar?  
Aquí entra en juego:

```bash
apropos <cadena>
```

- Busca en las descripciones de las páginas del manual una **palabra clave**.
    

**Ejemplo:**

```bash
apropos contraseña
```

👉 Devuelve muchos comandos relacionados con el término **contraseña**.

---

## 🔹 Filtrar resultados con `apropos -a`

Podemos afinar la búsqueda con la opción `-a` y una cadena adicional:

```bash
apropos -a cambio contraseña
```

👉 Esto mostrará **solo los comandos** que contengan **ambas palabras**:

- `cambio`
    
- `contraseña`
    

---

# ✅ Conclusión

Estos comandos hacen mucho más fácil **navegar y aprender en la línea de comandos de Linux**.  
Como nuevo analista, no tendrá todas las respuestas todo el tiempo, pero puede aprender dónde encontrarlas.

---


**¿Cómo puede utilizar el comando `man`?**

- Para conceder temporalmente permisos elevados a usuarios específicos  
- Para buscar en las descripciones de las páginas del manual una cadena especificada  
- Para mostrar la descripción de un comando en una sola línea  
- ✅ Para mostrar información sobre qué son y cómo funcionan otros comandos  

**Correcto**  
Puede utilizar el comando `man` para mostrar información sobre qué son otros comandos y cómo funcionan.  
Por ejemplo:  

```bash
man chown
````

Este comando mostrará información detallada sobre el comando `chown` y su funcionamiento.

