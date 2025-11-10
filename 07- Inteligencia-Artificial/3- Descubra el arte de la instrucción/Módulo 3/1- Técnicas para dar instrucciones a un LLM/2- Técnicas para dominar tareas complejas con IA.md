
Desglosar tareas complejas en pasos manejables puede ser todo un reto cuando se trabaja con modelos lingüísticos de gran tamaño (LLM). Afortunadamente, existen técnicas especializadas que pueden ayudarle a guiar a la IA en las tareas más complicadas. Dos métodos eficaces son **las Indicaciones de cadena de pensamiento** y **el encadenamiento de indicaciones**.

![alt=""](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/JSUW1A3SS_eB208x8lyTpA_6a59a66275a443c8af013780386808f1_AD_4nXep3pQJqTP0AKUXZZfqSIsHLB1H8SIDRDeF6qdZqo0HhHi73v0RPj9EAZWW7m5ktLAoIwb6SkBp-BKptcMWU0_nUEkWPRRYrEcm4B0wudejvgCNP8xMgZsL8BzH_b_vlBKKcxjKsOUh5mVoHwyDry2tiVj6?expiry=1762905600000&hmac=Kv8CziKQuosuiGcdbMTUKGeHNV3gIV7FpZ5aKA2mVvg)

## **Indicaciones de cadena de pensamiento**

**Indicaciones de cadena de pensamiento** es una técnica que consiste en pedir a un LLM que explique su proceso de razonamiento paso a paso, desde la entrada hasta la salida final. En esencia, esta técnica pide a la IA responsable que "muestre su trabajo", haciendo que su respuesta sea más transparente y estructurada.

Para utilizar Indicaciones de cadena de pensamiento, simplemente incluya frases clave en su pregunta, como:

- "Explica tu razonamiento"
    
- "Ve paso a paso"
    

Estas adiciones indican que la IA necesita seguir su proceso de pensamiento, lo que a menudo conduce a una salida más informativa y precisa.

Veamos un ejemplo en el que esta técnica puede ser útil:

Pensemos en un director de Recursos Humanos que elabora material de incorporación para un departamento concreto. A continuación se muestra cómo se podrían utilizar las Indicaciones de cadena de pensamiento para identificar los pasos a seguir para llevar a cabo la tarea:

**Indicación**:

_Elabora una lista con viñetas en la que se describan las principales tareas y responsabilidades de un nuevo empleado de diseño en una agencia de diseño. Explique su razonamiento paso a paso._

¿Notas las instrucciones adicionales "explica tu razonamiento paso a paso"? Puedes probar a utilizar esta instrucción con y sin esta frase para ver la diferencia en la respuesta de la IA.

Al pedir a la IA que desglose la lógica y el razonamiento que hay detrás de las tareas que sugiere, la información que obtengas del resultado también tendrá un razonamiento de _por qué_ se sugirió. En este caso, puede ayudar al responsable de RR.HH. a entender cada una de las posibles lagunas y a tomar decisiones informadas sobre cómo mejorar su actual proceso de incorporación.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/_063bf03b01b54768ad8de683d808e0cb_JSUW1A3SS_eB208x8lyTpA_6a59a66275a443c8af013780386808f1_AD_4nXep3pQJqTP0AKUXZZfqSIsHLB1H8SIDRDeF6qdZqo0HhHi73v0RPj9EAZWW7m5ktLAoIwb6SkBp-BKptcMWU0_nUEkWPRRYrEcm4B0wudejvgCNP8xMgZsL8BzH_b_vlBKKcxjKsOUh5mVoHwyDry2tiVj6?expiry=1762905600000&hmac=fkH6iBViatEsGsI_BezbmOJBoAdIV2DiIqK0-gy9TQM)

## **Encadenamiento de sugerencias**

Mientras que las Indicaciones de cadena de pensamiento se centran en el razonamiento _dentro de_ una sola indicación, el **encadenamiento** de **indicaciones** le ayuda a abordar grandes proyectos dividiéndolos en una serie de pasos más pequeños y conectados que están todos en la misma charla. Funciona como la cadena de montaje de una fábrica: el resultado de una pregunta se utiliza como entrada para la siguiente, enlazando todas las tareas como una cadena.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/_f0e7e35bfb704b0293357acccbd532d0_AI-essentials-chain-of-thought-graphic.png?expiry=1762905600000&hmac=D6WSoahmmlsO3JfEANuQt8E6d3bO1Kf1jny5toroXAI)

Esta técnica consta de tres pasos clave:

1. **Análisis de tareas**: Empiece por dividir la tarea compleja en una serie de pasos lógicos más pequeños.
    
2. **Flujo de entrada/salida**: Utilice el resultado de la primera tarea como contexto para la segunda. Continúe con este flujo iterativo hasta completar la tarea.
    
3. **Indicación inicial**: Crear una indicación específica que pida a la IA que complete sólo el primer paso.
    

Veamos un ejemplo de cadena de instrucciones:

Imagina que estás planeando unas cortas vacaciones en París. Quieres asegurarte de crear un itinerario de las cosas que más te gustan en unas vacaciones, mientras maximizas la logística para ser lo más eficiente posible con tu tiempo:

**Prompt 1**: _Voy a ir a [nombre de la ciudad] durante 3 días. Me gusta el arte, los lugares históricos y los parques. Sugiere algunos lugares conocidos que podría visitar en mi viaje._

**Pregunta 2 (encadenada a partir de la Pregunta 1)**: _Utilizando esos lugares, crea un itinerario lógico, día por día, que minimice el tiempo de viaje._

**Pregunta 3 (encadenada a partir de la pregunta 2)**: _Para cada día del itinerario, sugiera algunos restaurantes situados cerca de cada uno de los lugares sugeridos._

Al dividir la tarea en pasos lógicos y digeribles y utilizar el resultado de una pregunta como entrada específica para la siguiente, la IA pasa de ser un simple generador de respuestas a un colaborador estructurado.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/_30c5193b27b4444b969f63ca01a59245__063bf03b01b54768ad8de683d808e0cb_JSUW1A3SS_eB208x8lyTpA_6a59a66275a443c8af013780386808f1_AD_4nXep3pQJqTP0AKUXZZfqSIsHLB1H8SIDRDeF6qdZqo0HhHi73v0RPj9EAZWW7m5ktLAoIwb6SkBp-BKptcMWU0_nUEkWPRRYrEcm4B0wudejvgCNP8xMgZsL8BzH_b_vlBKKcxjKsOUh5mVoHwyDry2tiVj6?expiry=1762905600000&hmac=JJdqDR4FCIfNWzzR9D0DduZB9zXJkeCEFT1J2Zg1XsI)

## **Combinar el encadenamiento de instrucciones con la cadena de pensamiento**

Puede combinar el encadenamiento de instrucciones con la cadena de pensamiento para mejorar la calidad y la precisión del proceso de resolución de problemas en _cualquier_ etapa.

Veamos un ejemplo en el que se combinan las indicaciones de cadena de pensamiento y el encadenamiento de indicaciones:

Imagina que organizas la próxima reunión de tu club de lectura y quieres sugerencias sobre qué libro recomendar. Le gustaría recomendar una novela de fantasía, pero la fantasía no es un género que su club de lectura lea habitualmente. El libro de fantasía que elijas debe ser atractivo sin ser abrumador o demasiado complejo.

**Pregunta 1:** _Estoy organizando un club de lectura y me gustaría que me recomendaran libros de fantasía para las personas que no conocen este género. Sugiere algunos libros que nos puedan servir._

**Consigna 2 (utilizando el encadenamiento de consignas e Indicaciones de cadena de pensamiento):** _FROM that list, can you suggest which book you would recommend if we are looking for a fast-paced read?_ _**Explique su razonamiento**__._

Este proceso iterativo continúa hasta que se selecciona y examina un libro definitivo. Al desglosar la tarea compleja con el encadenamiento de instrucciones y la incorporación de la cadena de pensamiento, puede abordar problemas más difíciles y, al mismo tiempo, garantizar resultados más precisos.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/_964e14d82eb6462f82ed562a4ef56e48_JSUW1A3SS_eB208x8lyTpA_6a59a66275a443c8af013780386808f1_AD_4nXep3pQJqTP0AKUXZZfqSIsHLB1H8SIDRDeF6qdZqo0HhHi73v0RPj9EAZWW7m5ktLAoIwb6SkBp-BKptcMWU0_nUEkWPRRYrEcm4B0wudejvgCNP8xMgZsL8BzH_b_vlBKKcxjKsOUh5mVoHwyDry2tiVj6?expiry=1762905600000&hmac=1XshnMZhS_YBB4uxGrOOwYY7rxFVW68CyAtkyzMQ4us)

## **Limitaciones y buenas prácticas**

Aunque el encadenamiento de instrucciones puede ser una técnica útil, es importante ser consciente de los posibles problemas que pueden surgir, especialmente con cadenas más largas.

Las herramientas de IA pueden tener dificultades para recordar el contexto de partes anteriores de la conversación a medida que la cadena de instrucciones se alarga. Esto puede dar lugar a

- Respuestas incoherentes
    
- Pasar por alto detalles importantes de preguntas anteriores
    
- Dificultad para mantener el objetivo general de la tarea
    

Para superar estos retos y garantizar un encadenamiento eficaz de las instrucciones, considere las siguientes estrategias:

- **Utilizar puntos de control**: Pedir periódicamente a la IA que haga un breve resumen del objetivo general.
    
- **Trabajar en subtareas**: Divida las tareas muy complejas en subtareas aún más pequeñas para que pueda tratar cada una como su propia cadena más corta antes de pasar a la siguiente.
    
- Recapitular**y redirigir**: Si observa que una herramienta de IA se desvía del objetivo original, recapitule la información esencial y rediríjala de nuevo al objetivo principal.
    

Estas estrategias le permitirán obtener resultados más precisos y pertinentes de una herramienta de IA. ASÍ COMO CON CUALQUIER OTRA TÉCNICA DE PREGUNTAS, EL ENCADENAMIENTO DE PREGUNTAS depende de encontrar el equilibrio adecuado entre proporcionar el contexto necesario y evitar la sobrecarga de información.