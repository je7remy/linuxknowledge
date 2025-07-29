
**En este vídeo, vamos a aprender un poco más sobre el shell y cómo comunicarnos con él.**

Comunicarse con una computadora es como tener una conversación con un amigo. Una persona hace una pregunta y la otra responde con una respuesta. Si no sabe la respuesta, puede simplemente decir que no la sabe.

Cuando se comunica con el shell, los comandos del shell pueden:

- Tomar **entrada**
    
- Dar **salida**
    
- O mostrar **mensajes de error**
    

---

Exploremos la **entrada estándar**, la **salida estándar** y los **mensajes de error** con más detalle.

- La **entrada estándar** consiste en información recibida por el sistema operativo a través de la línea de comandos.
    
- Es como si le hiciera una pregunta a su amigo durante una conversación.
    
- La información se introduce desde su teclado al shell.
    
- Si el shell puede interpretar su petición, le pide al kernel los recursos necesarios para ejecutar la tarea.
    

Veamos esto con `echo`, un comando de Linux que da salida a una cadena de texto especificada.  
Los **datos de cadena** son datos que consisten en una secuencia ordenada de caracteres.

En el ejemplo, solo haremos que `echo` emita la cadena de texto “hola”.  
Entonces, como entrada, escribiremos:

```bash
echo hola
```

Más tarde, cuando pulsemos intro, obtendremos la **salida**.  
Pero antes, discutamos primero el concepto de salida con más detalle.

La **salida estándar** es la información devuelta por el sistema operativo a través del shell.  
De la misma forma que su amigo le da una respuesta a su pregunta, la salida es la **respuesta de la computadora** a la orden que usted introduce.  
La **salida** es lo que usted recibe.

Retomando el ejemplo, escribimos:

```bash
echo hola
```

Y al pulsar enter, la shell devuelve la salida:

```bash
hola
```

---

Por último, el **error estándar** contiene mensajes de error devueltos por el sistema operativo a través del shell.

Al igual que su amigo podría indicar que no puede responder a una pregunta, el sistema responde con un **mensaje de error** si no puede ejecutar su comando.

Esto puede ocurrir:

- Si escribe mal un comando
    
- Si el sistema no conoce el comando
    
- O si no tiene los permisos adecuados para ejecutarlo
    

Ejemplo:

```bash
eco hola
```

Nota que intencionadamente se ha escrito mal `echo` como `eco`.  
Cuando se pulsa intro, aparece un **mensaje de error**.

---

**Para terminar**, hemos cubierto los aspectos básicos de la comunicación con el shell.

La comunicación con el intérprete de comandos puede darse solo de **tres maneras**:

1. El sistema recibe un comando (**entrada**)
    
2. El sistema responde al comando (**salida**)
    
3. El sistema no sabe cómo responder (**error**)
    

Más adelante, te familiarizarás mucho más con esto a medida que explores comandos útiles para los profesionales de la **seguridad informática**.

---

¿Deseas que te lo ponga en formato de resumen tipo ficha o infografía?

**¿Qué puede devolver el shell después de que un usuario escriba un comando?**

- ✅ **Salida estándar o error estándar**
    
- ❌ Sólo salida estándar
    
- ❌ Entrada estándar o error estándar
    
- ❌ Salida estándar o entrada estándar
    

**Correcto**  
Después de que un usuario escriba un comando en el shell, éste puede devolver una **salida estándar** o un **error estándar**.

- La **salida estándar** es la información que el sistema devuelve cuando el comando se ejecuta correctamente.
    
- El **error estándar** aparece cuando hay un problema, como un comando mal escrito o falta de permisos.
    

La **entrada estándar** es lo que el usuario escribe (lo que entra al sistema), por lo tanto **no es una respuesta del shell**.

---