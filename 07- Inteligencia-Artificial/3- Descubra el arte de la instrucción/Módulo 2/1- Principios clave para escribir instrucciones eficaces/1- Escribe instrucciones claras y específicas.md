
## 🍽️ El principio de la cocina: Calidad de entrada = Calidad de salida

En general, es cierto que la calidad de lo que se empieza afecta en gran medida a la calidad de lo que produce. Pensemos, por ejemplo, en la cocina. Si tienes **ingredientes frescos de alta calidad**, es más probable que prepares una gran comida. Por el contrario, si falta un ingrediente o los ingredientes no son de alta calidad, la comida resultante puede no ser tan buena.

Del mismo modo, la **calidad de la instrucción** que se pone en una herramienta de IA conversacional puede afectar la calidad de los resultados de la herramienta.

Aquí es donde entra en juego la ingeniería de instrucciones. La ingeniería de instrucciones implica diseñar **la mejor instrucción que puedas** para obtener el resultado deseado de un LLM. Esto incluye escribir **instrucciones claras y específicas** que proporcionen un contexto relevante.

---

## 🤔 ¿Por qué los LLM necesitan tanto contexto?

Para comprender mejor el contexto que necesitan los LLM, compremos cómo una persona y un LLM podrían responder a la misma pregunta.

- **El contexto humano:** Supongamos que un vegetariano pregunta a su amigo a qué restaurante ir en San Francisco. El amigo probablemente sugeriría restaurantes con buenas opciones vegetarianas. Una persona instintivamente consideraría el hecho de que su amigo es vegetariano.
    
- **El contexto del LLM:** Sin embargo, si se le pide eso mismo a un LLM, podría recomendar restaurantes que no son adecuados. **Un LLM no tiene este conocimiento previo.**
    

Entonces, para obtener la información necesaria de un LLM, la instrucción debe ser más específica. En este caso, la instrucción debe mencionar que el restaurante debería tener **buenas opciones vegetarianas**.

---

## 🚀 Ejemplo: De una instrucción vaga a una eficaz

Encarguémonos de la tarea de planificar un evento de empresa. Necesitas encontrar un tema para una próxima conferencia.

### Intento 1: La instrucción vaga

Escribamos una instrucción en Gemini (o ChatGPT, Copilot, etc.):

> "generar una lista de cinco posibles temas para un evento."

**Resultado:** Bueno, esto no es lo que queríamos. Hemos conseguido una lista que parece estar más relacionada con temas de fiestas que con temas para una conferencia profesional.

**El problema:** Nuestra instrucción **no proporcionaba suficiente contexto**. No era lo suficientemente clara ni específica.

### Intento 2: La instrucción específica y con contexto

Intentémoslo de nuevo. Esta vez escribiremos la instrucción:

> "generar una lista de cinco temas potenciales para una conferencia profesional sobre la experiencia del cliente en el sector de la hostelería."

**Resultado:** ¡Esto es mucho mejor! Hemos diseñado nuestra instrucción para incluir contexto específico y pertinente, por lo que se pueden generar resultados útiles.

---

## 🔑 Conclusiones clave

1. **Claridad y contexto son esenciales:** Cuando proporcionas instrucciones claras y específicas que incluyen el contexto, permites que los LLM generen resultados útiles.
    
2. **Conoce las limitaciones:** Ten en cuenta que, debido a las limitaciones del LLM, puede haber algunos casos en los que no se pueda obtener un resultado de calidad. Por ejemplo, si le pides al LLM información sobre un acontecimiento de actualidad al que no tiene acceso, no será capaz de proporcionar el resultado que necesitas.
    
3. **La iteración es la norma:** La ingeniería de instrucciones suele ser un **proceso iterativo**. Cuando nuestra primera instrucción no produjo la respuesta que queríamos, revisamos la instrucción para mejorar el resultado.