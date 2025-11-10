1.  
**Pregunta 1**  
¿Cuáles de las siguientes fuentes de datos se utilizan normalmente para entrenar modelos de lenguaje grande (LLM)? Selecciona tres respuestas.  
  
☐ Imágenes  
☑ Artículos periodísticos  
☑ Artículos científicos  
☑ Libros de texto  

**Explicación:** Los LLM se entrenan principalmente con enormes cantidades de texto (web crawls como Common Crawl, libros, artículos científicos, noticias, foros, etc.). Las imágenes se usan para modelos multimodales, pero no para entrenar LLM puros de lenguaje.  



2.  
**Pregunta 2**  
Un LLM genera un artículo sobre energía renovable. Al llevar a cabo una revisión, resulta que algunas de las estadísticas que se ofrecen en el resultado no son ciertas. ¿Qué posible problema con los resultados de los LLM pone de relieve este escenario?  
  
☐ Gramática incoherente  
☐ Sesgos lingüísticos  
☐ Incongruencias de estilo  
☑ Alucinaciones  

**Explicación:** Las alucinaciones ocurren cuando el modelo inventa información plausible pero falsa (ej. estadísticas incorrectas). No es un problema de gramática, estilo ni sesgo lingüístico.  



3.  
**Pregunta 3**  
¿Cuál de las siguientes afirmaciones es cierta en relación con la instrucción? Selecciona tres respuestas.  
  
☑ La instrucción suele ser un proceso iterativo.  
☑ La especificación de una persona dirige el enfoque de una herramienta de IA.  
☑ Redactar una tarea clara y específica tiende a producir resultados útiles.  
☐ Proporcionar contexto garantiza que un LLM no produzca alucinacion.  

**Explicación:** La última opción es falsa: proporcionar contexto ayuda, pero **no garantiza** eliminar alucinaciones (ningún prompt lo hace al 100 %).  


4.  
**Pregunta 4**  
Un analista de ciberseguridad utiliza una herramienta de IA para preparar una presentación dirigida a un público no técnico. El analista quiere que la herramienta redacte información sobre los riesgos habituales en las redes domésticas y cómo prevenirlos. ¿Cuál es la instrucción que proporciona las indicaciones más claras y con más contexto?  
  
☐ Comenta la historia de la ciberseguridad y asegúrate de incluir las últimas tendencias que la gente debería tener en cuenta.  
☐ ¡Hola! Podrías profundizar en las medidas de seguridad que impiden que se produzcan ciberataques  
☑ Explica los riesgos habituales asociados con las redes domésticas. Enumera las medidas prácticas que pueden adoptarse para mitigar cada una de ellos.  
☐ Analiza las especificaciones técnicas de productos de wifi populares para uso doméstico y resume la información para mi presentación.  

**Explicación:** Es la única instrucción clara, específica, con contexto adecuado (público no técnico, tema exacto, estructura solicitada). Las demás son vagas, demasiado amplias o técnicas.  


5.  
**Pregunta 5**  
Un artista gráfico instruye a una herramienta de IA para que le resuma las últimas tendencias del sector del diseño. Como parte de la instrucción, incluye tres ejemplos para ilustrar el contexto, la formulación y el formato previsto del resultado. ¿Qué describe este escenario?  
  
☐ Instrucciones ocasionales  
☐ Instrucciones de intento cero  
☐ Ejemplo de instrucción  
☑ Algunos ejemplos de instrucciones  

**Explicación:** Cuando se incluyen ejemplos concretos en el prompt para guiar el formato y estilo, se denomina **few-shot prompting** (algunos ejemplos).  
- “Instrucciones de intento cero” = zero-shot (sin ejemplos).  
- “Ejemplo de instrucción” sería one-shot (un solo ejemplo).  
- “Instrucciones ocasionales” no existe como término.  

