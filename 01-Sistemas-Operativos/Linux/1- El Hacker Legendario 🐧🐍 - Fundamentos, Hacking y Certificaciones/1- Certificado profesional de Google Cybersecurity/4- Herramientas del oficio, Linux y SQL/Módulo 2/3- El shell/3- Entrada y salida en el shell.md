
Exploremos la **entrada estándar**, la **salida estándar** y los **mensajes de error** con más detalle.

La **entrada estándar** consiste en información recibida por el sistema operativo a través de la línea de comandos. Es como hacerle una pregunta a tu amigo durante una conversación. La información se introduce desde tu teclado al shell. Si el shell puede interpretar tu petición, le pide al kernel los recursos necesarios para ejecutar la tarea relacionada.

Veamos esto con el comando `echo`, un comando de Linux que da salida a una cadena de texto. Las **cadenas de texto** son datos que consisten en una secuencia ordenada de caracteres. En nuestro ejemplo, solo haremos que emita la cadena de texto "hola". Así que como entrada escribiremos:

```
echo hola
```

Cuando presionamos _Enter_, obtenemos la salida.

La **salida estándar** es la información devuelta por el sistema operativo a través del shell. De la misma forma que tu amigo te da una respuesta a tu pregunta, la salida es la respuesta de la computadora a la orden que introduces. Es lo que recibes como resultado.

Entonces, si escribimos:

```
echo hola
```

y presionamos _Enter_, la shell devuelve la salida:

```
hola
```

Por último, el **error estándar** contiene mensajes de error devueltos por el sistema operativo a través del shell. Al igual que tu amigo podría decir que no puede responder una pregunta, el sistema responde con un mensaje de error si no puede procesar tu comando. Esto puede ocurrir si escribimos mal un comando, si el sistema no lo reconoce o si no tenemos los permisos adecuados.

Por ejemplo, si escribimos:

```
eco hola
```

(con un error tipográfico), y presionamos _Enter_, el sistema devuelve un mensaje de error.

---

**En resumen**, la comunicación con el shell se da de tres maneras:

1. **Entrada:** El sistema recibe un comando.
    
2. **Salida:** El sistema responde con un resultado.
    
3. **Error:** El sistema no puede ejecutar el comando o no lo entiende.
    

A medida que avances, te familiarizarás más con estos conceptos explorando comandos útiles para profesionales de la seguridad informática.

---

### ❓ **Pregunta:**

**¿Qué puede devolver el shell después de que un usuario escriba un comando?**

**Opciones:**

- A) Salida estándar o entrada estándar
    
- B) ✅ **Salida estándar o error estándar**
    
- C) Sólo salida estándar
    
- D) Entrada estándar o error estándar
    

---

### ✅ **Respuesta correcta:**

**Salida estándar o error estándar**

---

### 💡 **Explicación:**

Después de que un usuario escribe un comando en el shell:

- El sistema puede **responder correctamente**, devolviendo una **salida estándar** (ejemplo: `echo hola` → devuelve `hola`).
    
- O puede **fallar**, devolviendo un **mensaje de error estándar** (por ejemplo: comando mal escrito o sin permisos).
    

La **entrada estándar** es lo que el usuario proporciona, **no lo que devuelve el shell**.
