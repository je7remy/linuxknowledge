
### **Uso de la IA para Identificar Errores en el Código**

En tu trabajo como profesional de la seguridad, escribir código puede ayudarte a completar tareas y procesos repetitivos con precisión y deficiencias. La codificación ayuda a reducir el riesgo de errores humanos y puede ahorrar horas o días en comparación con la realización manual del trabajo.

Pero debo admitir que no soy el mejor programador, e incluso los mejores programadores escriben código que puede contener errores. Tratar de encontrar errores en el código solía ser muy frustrante para mí. A menudo me daba cuenta de que mi código tenía errores porque algo no funcionaba bien, pero para mí, el código parecía perfecto. Estaría mirando la pantalla intentando detectar un error que simplemente no podía encontrar.

Con herramientas de IA de última generación como Gemini ya no tengo que pasar horas buscando errores. Y mejor aún, a veces estas herramientas incluso encuentran errores que no sabía que eran errores.

---

### **Escenario: Revisión de un Script de Python**

Déjeme explicar lo que quiero decir. Supongamos que escribiste código con el lenguaje de programación Python para crear una función que analice los registros. Su intención es utilizar el valor del análisis de inicio de sesión en una declaración condicional. Cuando el valor del análisis de inicio de sesión sea mayor o igual a 3, la actividad de inicio de sesión requerirá una investigación más profunda y se mostrará una alerta.

Por supuesto, existe la posibilidad de que el código contenga errores. Una herramienta de IA generacional como Gemini puede ayudar como revisor de código.

Este es un ejemplo de un mensaje sencillo que puedes introducir:

> ¿Qué errores, si los hay, hay en el código existente?
> 
> _[Aquí copiarías y pegarías tu código]_

---

### **Análisis del Resultado: El Error de "División por Cero"**

Primero las buenas noticias. El código básicamente funciona. Hace lo que se supone que debe hacer. Analiza los inicios de sesión de una persona en la actualidad, los compara con su actividad habitual y alerta si parece inusual.

Sin embargo, se produce un **error de división cero** cuando un programa intenta dividir un número por 0. Matemáticamente, esto es imposible.

Esto es lo que pasó. En el código, estás calculando la proporción de inicios de sesión dividiendo la cantidad de veces que un usuario ha iniciado sesión hoy por la cantidad promedio de inicios de sesión por día. Sin embargo, Gemini señaló correctamente que si un usuario no tiene un número promedio de inicios de sesión por día (lo que puede suceder porque es un empleado nuevo), el programa no funcionaría.

Aún más útil que identificar el error, **Gemini generó una verificación recomendada**, por lo que el código maneja esta situación con elegancia. Propuso agregar una declaración condicional que genere un error cuando el número promedio de inicios de sesión es cero. Esto garantiza que el error se capture sin que el error rompa el código.

---

### **El Valor de la IA: Encontrar "Casos Extremos" Ocultos**

Los errores desconocidos como este de este ejemplo pueden comprometer la **confidencialidad, la integridad y la disponibilidad** de nuestros sistemas. Por eso es tan útil contar con una herramienta de IA de última generación que escanee el código en busca de errores comunes, vulnerabilidades y posibles cuellos de botella en el rendimiento.

Incluso si tu código parece funcionar, como el de nuestro ejemplo, las herramientas de IA de última generación pueden identificar **errores derivados de casos extremos** que quizás no hayas considerado.

- Si no estás seguro de por qué el error es un problema o de cómo puedes evitarlo en el futuro, pide a la herramienta gen IA que te explique las soluciones propuestas.
    
- Y asegúrese de **verificar las recomendaciones** (Human-in-the-Loop), revisar los cambios sugeridos y hacer los ajustes necesarios.
    

---

### **⚠️ Consejo Clave: El Contexto en los Prompts de Código**

Una nota rápida antes de continuar.

Cuando se utilizan herramientas de IA generacional para ayudar a depurar el código, **proporcionar demasiado contexto en el mensaje a veces puede resultar contraproducente.**

Esto se debe a que el código, por naturaleza, es preciso y estructurado, por lo que bombardear a la IA con detalles superfluos puede distraerla del problema central. La clave es lograr un equilibrio y proporcionar suficiente información para que la herramienta de la generación de IA comprenda el problema sin demasiados detalles.

Este no es el caso de muchas otras solicitudes, ya que la adición de contexto adicional a menudo produce resultados mejores y más detallados. La precisión y el nivel correcto de contexto son fundamentales a la hora de solicitar código.