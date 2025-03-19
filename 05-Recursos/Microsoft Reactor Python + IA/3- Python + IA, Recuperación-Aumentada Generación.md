Hola a todos, bienvenidos a esta explicación detallada sobre Retrieval-Augmented Generation (RAG), o en español, Generación Aumentada por Recuperación. Hoy voy a darles una visión completa y paso a paso de qué es RAG, cómo funciona, y cómo podemos implementarlo en diferentes contextos usando Python y herramientas de inteligencia artificial. Mi objetivo es que al final de esta explicación, tengan una comprensión profunda del tema, con ejemplos prácticos y detalles técnicos que puedan aplicar en sus propios proyectos. ¡Así que empecemos!

---

### Contexto inicial: La serie Python + IA

Antes de sumergirnos en RAG, quiero darles un poco de contexto. Esta explicación está basada en una sesión que forma parte de una serie más amplia organizada por Microsoft sobre Python e Inteligencia Artificial. Las diapositivas que tengo frente a mí muestran las fechas de las sesiones:

- **3/11**: LLMs (Modelos de Lenguaje Grandes)
- **3/13**: Embeddings vectoriales
- **3/18**: RAG (¡esta es la nuestra!)
- **3/19**: Modelos de Visión
- **3/20**: Salidas Estructuradas
- **3/27**: Calidad y Seguridad

Si quieren registrarse para las próximas sesiones o ver las grabaciones de las anteriores, pueden hacerlo en **aka.ms/PythonIA/series** y **aka.ms/pythonia/grabaciones**. La presentadora de esta sesión sobre RAG es Gwyneth Peña-Siguenza, una Python Cloud Advocate en Microsoft, y pueden encontrar más sobre ella en **aka.ms/madebygps**. Ahora que tenemos el contexto, pasemos al tema principal.

---

### ¿Qué cubriremos hoy?

Las diapositivas indican que hoy vamos a explorar los siguientes puntos:

- Generación Aumentada por Recuperación (RAG)
- Flujos de RAG simples y avanzados
- RAG en bases de datos
- RAG en documentos
- Más formas de construir RAG

Voy a desarrollar cada uno de estos puntos con mucho detalle, paso a paso, integrando ejemplos prácticos y código cuando sea necesario. También les daré instrucciones para que puedan seguir el proceso ustedes mismos si quieren experimentar con el código.

---

### ¿Por qué RAG? Las limitaciones de los LLMs

Primero, dejemos claro por qué necesitamos RAG. Los Modelos de Lenguaje Grandes (LLMs), como los que usamos en ChatGPT o Copilot, son increíblemente poderosos. Han sido entrenados con enormes cantidades de datos públicos y pueden responder a una amplia variedad de preguntas. Sin embargo, tienen dos limitaciones importantes que las diapositivas destacan:

1. **Conocimiento público desactualizado**: Los LLMs están entrenados con datos hasta una fecha específica. Por ejemplo, si el modelo fue entrenado con datos hasta diciembre de 2023, no sabe nada sobre lo que pasó en 2024. Si le pregunto algo sobre un evento reciente, no tendrá la respuesta.

2. **Sin conocimiento interno**: Estos modelos no tienen acceso a información específica de un dominio, como las políticas internas de mi empresa o los datos privados de mi equipo. Por ejemplo, si pregunto: "¿Mis beneficios en la empresa cubren actividades subacuáticas?", el modelo no tiene manera de saberlo porque esa información no está en su entrenamiento.

Entonces, ¿cómo resolvemos esto? Hay dos enfoques principales:

- **Fine-tuning**: Esto implica entrenar el modelo con datos específicos para que aprenda nuevas habilidades permanentemente. Sin embargo, como dicen las diapositivas, esto tiene un **alto costo y toma mucho tiempo**. No es práctico si necesitamos actualizar el modelo frecuentemente o trabajar con datos cambiantes.

- **RAG**: Aquí es donde entra la Generación Aumentada por Recuperación. RAG permite que el modelo acceda a información externa (como bases de datos o documentos) sin necesidad de reentrenarlo. Es más flexible, económico y rápido que el fine-tuning, y hoy vamos a ver cómo funciona en detalle.

---

### RAG 101: ¿Qué es y cómo funciona?

RAG combina dos procesos clave: **recuperación** y **generación**. La idea es simple pero poderosa. Cuando un usuario hace una pregunta, el sistema:

1. **Recupera** información relevante de una fuente externa (como una base de datos o un documento).
2. **Aumenta** el contexto del modelo con esa información.
3. **Genera** una respuesta precisa basada en la pregunta y el contexto recuperado.

Voy a ilustrarlo con un ejemplo práctico que está en las diapositivas.

#### Ejemplo: "¿Qué tan rápido es el Prius V?"

Imagina que tengo un archivo CSV con datos sobre automóviles híbridos. Las diapositivas muestran una tabla como esta:

| Vehicle          | Year | MSRP     | Acceleration | MPG  |
|------------------|------|----------|--------------|------|
| Prius (1st Gen)  | 1997 | 24509.74 | 7.46         | -    |
| Prius (2nd Gen)  | 2000 | 26832.25 | 7.97         | -    |
| Prius (3rd Gen)  | 2009 | 24641.18 | 9.6          | -    |
| Prius V          | 2011 | 27272.28 | 9.51         | -    |
| Prius C          | 2012 | 19006.62 | 9.35         | -    |
| Prius PHV        | 2012 | 32095.61 | 8.82         | -    |
| Prius C          | 2013 | 19080.0  | 8.7          | -    |
| Prius            | 2013 | 24200.0  | 10.2         | -    |
| Prius Plug-in    | 2013 | 32000.0  | 9.17         | -    |

Un usuario me pregunta: "¿Qué tan rápido es el Prius V?". Sin RAG, un LLM podría dar una respuesta vaga basada en su entrenamiento general. Pero con RAG:

1. **Recuperación**: Busco en el CSV y encuentro la fila correspondiente al Prius V de 2011. Veo que su aceleración es de 9.51 segundos de 0 a 60 mph.
2. **Aumento**: Paso esta información al modelo junto con la pregunta.
3. **Generación**: El modelo responde: "El Prius V acelera de 0 a 60 mph en 9.51 segundos."

Este es un ejemplo básico de RAG con datos estructurados. Ahora, veamos cómo implementarlo en código.

#### Código con OpenAI Python SDK

Las diapositivas incluyen un fragmento de código para este ejemplo:

```python
user_query = "How fast is the Prius V?"
retrieved_content = "vehicle | year | msrp | acceleration | Prius V | 2011 | 27272.28 | 9.51 |"
```

Aquí, `retrieved_content` simula lo que recuperaríamos de la base de datos. En la práctica, usaríamos una función de búsqueda (como una consulta SQL o una búsqueda vectorial) para obtener esta información. Luego, pasaríamos `user_query` y `retrieved_content` al modelo de OpenAI para generar la respuesta. Más adelante veremos ejemplos más completos de código, pero esto nos da una idea inicial.

---

### RAG con soporte multiturn

Ahora, supongamos que el usuario quiere continuar la conversación. Después de preguntar por el Prius V, dice: "¿Qué tan rápido es el Insight?". Las diapositivas muestran cómo RAG puede manejar múltiples preguntas en una conversación, manteniendo el contexto.

#### Ejemplo multiturn

1. **Pregunta 1**: "¿Qué tan rápido es el Prius V?"
   - Respuesta: "El Prius V acelera de 0 a 60 mph en 9.51 segundos."
2. **Pregunta 2**: "¿Qué tan rápido es el Insight?"
   - Respuesta: "Aquí están los tiempos de aceleración para los modelos Honda Insight: Insight (2010): 9.17 segundos, Insight (2011): 9.52 segundos, ..."

Para que esto funcione, el sistema necesita almacenar el historial de la conversación y usar RAG en cada turno. Veamos el código.

#### Código multiturn

Las diapositivas proporcionan este ejemplo:

```python
messages = [{"role": "system", "content": SYSTEM_MESSAGE}]
while True:
    question = input("\nYour question: ")
    matches = search(question)
    messages.append({"role": "user", "content": f"{question}\nSources: {matches}"})
    response = client.chat.completions.create(
        model=MODEL_NAME,
        temperature=0.3,
        messages=messages
    )
    bot_response = response.choices[0].message.content
    messages.append({"role": "assistant", "content": bot_response})
```

**Explicación paso a paso**:
1. `messages` es una lista que almacena el historial de la conversación. Comienza con un mensaje del sistema que define el comportamiento del modelo.
2. En un bucle infinito, pedimos al usuario una pregunta con `input`.
3. `search(question)` busca información relevante en la base de datos (en este caso, el CSV de autos).
4. Agregamos la pregunta y los resultados de la búsqueda a `messages`.
5. Llamamos a la API de OpenAI con `client.chat.completions.create` para generar la respuesta.
6. La respuesta del modelo se agrega a `messages` para mantener el contexto.

Este archivo se llama `rag_multiturn.py` según las diapositivas. Si quieren probarlo, pueden encontrarlo en el repositorio de GitHub que mencionaré más adelante.

---

### RAG con multiturn + reescritura de consultas (Query Rewriting)

A veces, las preguntas de los usuarios son ambiguas o tienen errores. Por ejemplo, el usuario podría escribir: "Y el insigt?" en lugar de "Insight". Las diapositivas muestran cómo la reescritura de consultas mejora la precisión.

#### Ejemplo con reescritura

1. **Pregunta 1**: "¿Qué tan rápido es el Prius V?"
   - Respuesta: "El Prius V acelera de 0 a 60 mph en 9.51 segundos."
2. **Pregunta 2**: "Y el insigt?"
   - Sin reescritura, el sistema podría fallar al no reconocer "insigt".
   - Con reescritura, el modelo corrige la consulta a "vehicle: Insight acceleration" y busca en la tabla:

| Vehicle  | Year | MSRP     | Acceleration | MPG  |
|----------|------|----------|--------------|------|
| Insight  | 2010 | 19859.16 | 9.17         | 41.0 |
| Insight  | 2011 | 18254.38 | 9.52         | 41.0 |
| Insight  | 2012 | 18555.28 | 9.42         | 42.0 |

   - Respuesta: "El Insight 2011 tiene un tiempo de aceleración de 9.52 segundos."

#### Código con reescritura

El código es similar al multiturn, pero incluye un paso adicional para reescribir la consulta:

```python
messages = [{"role": "system", "content": SYSTEM_MESSAGE}]
while True:
    question = input("\nYour question: ")
    matches = search(question)  # Aquí se podría incluir la lógica de reescritura
    messages.append({"role": "user", "content": f"{question}\nSources: {matches}"})
    response = client.chat.completions.create(
        model=MODEL_NAME,
        temperature=0.3,
        messages=messages
    )
    bot_response = response.choices[0].message.content
    messages.append({"role": "assistant", "content": bot_response})
```

Este archivo se llama `rag_queryrewrite.py`. En la práctica, la función `search()` podría usar un modelo de lenguaje para reescribir la consulta antes de buscar, como transformar "Y el insigt?" a "What is the acceleration of the Insight?".

---

### RAG en documentos no estructurados

Hasta ahora, hemos trabajado con datos estructurados (CSV). Pero en el mundo real, mucha información está en documentos no estructurados como PDFs. Las diapositivas explican cómo ingerir documentos para usar RAG.

#### Proceso de ingesta de documentos

1. **Extracción de texto**: Usamos herramientas como `PyMuPDF` para extraer texto de un PDF.
2. **División en fragmentos**: Los LLMs tienen una ventana de contexto limitada (por ejemplo, 4096 tokens), así que dividimos el texto en fragmentos más pequeños, como 512 tokens cada uno.
3. **Generación de embeddings**: Convertimos cada fragmento en un vector numérico (embedding) que captura su significado semántico.
4. **Almacenamiento en un índice**: Guardamos los fragmentos y sus embeddings en un índice, que puede ser en memoria o en una base de datos vectorial.

#### Ejemplo práctico

Supongamos que tengo un PDF sobre insectos y alguien pregunta: "¿Dónde vive la abeja solitaria?". El proceso sería:

1. Extraigo el texto del PDF con `PyMuPDF`.
2. Divido el texto en fragmentos de 512 tokens.
3. Genero embeddings para cada fragmento usando un modelo como el de OpenAI.
4. Almaceno los embeddings en un índice.
5. Convierto la pregunta en un embedding y busco los fragmentos más similares en el índice.
6. Paso los fragmentos relevantes al modelo, que responde: "La abeja solitaria gris (Centris pallida) vive en América del Norte, en hábitats desérticos."

#### Código de ingesta

Aunque las diapositivas no dan el código completo, mencionan herramientas como `PyMuPDF` y `LangChain`. Un ejemplo básico sería:

```python
import fitz  # PyMuPDF
from langchain.text_splitter import RecursiveCharacterTextSplitter

# Extraer texto del PDF
doc = fitz.open("insectos.pdf")
text = ""
for page in doc:
    text += page.get_text()

# Dividir en fragmentos
splitter = RecursiveCharacterTextSplitter(chunk_size=512, chunk_overlap=50)
chunks = splitter.split_text(text)

# Generar embeddings y almacenarlos (esto requeriría más código)
```

---

### Optimización: Tamaño de fragmentos y recuperación híbrida

Las diapositivas no lo detallan explícitamente aquí, pero en mi transcripción previa mencioné la importancia del tamaño de los fragmentos y la recuperación híbrida.

- **Tamaño de fragmentos**: Si los fragmentos son muy pequeños, pierden contexto; si son muy grandes, incluyen información irrelevante. Probé con 512 tokens y una superposición del 10-25% para mejorar el recall.
- **Recuperación híbrida**: Combina búsqueda por palabras clave (rápida) y búsqueda vectorial (semántica). Esto mejora la precisión al recuperar información.

---

### Más formas de construir RAG

Las diapositivas listan varias formas avanzadas de implementar RAG:

1. **GraphRAG**: Usa grafos para mejorar la recuperación. Más info en **microsoft.com/research/project/graphrag/**.
2. **RAFT (RAG + Fine-tuning)**: Combina RAG con ajuste fino. Ver ejemplos en **github.com/ShishirPatil/gorilla/** y **github.com/Azure-Samples/raft-distillation-recipe**.
3. **Agentic RAG**: RAG con agentes autónomos. Hay un video en **youtube.com/live/aQ4yQXeB1Ss**.
4. **Bases de datos**: Podemos usar SQL en PostgreSQL o Cosmos DB (ver ejemplo más abajo).
5. **Azure AI Search**: Una solución en la nube para RAG a gran escala.

#### Ejemplo con Cosmos DB

Las diapositivas incluyen un fragmento para buscar vectores en Cosmos DB:

```python
def vector_search(embedding, similarity_score=0.02, num_results=5):
    results = container.query_items(
        query='''
        SELECT TOP @num_results c.overview, VectorDistance(c.vector, @embedding) as SimilarityScore
        FROM c
        WHERE VectorDistance(c.vector, @embedding) > @similarity_score
        ORDER BY VectorDistance(c.vector, @embedding)
        ''',
        parameters=[
            {"name": "@embedding", "value": embedding},
            {"name": "@num_results", "value": num_results},
            {"name": "@similarity_score", "value": similarity_score}
        ],
        enable_cross_partition_query=True
    )
    return list(results)
```

Esto busca documentos similares basados en embeddings vectoriales.

#### Plantillas de código abierto

- **Azure AI Foundry**: Usa Azure AI Search como retriever y OpenAI como LLM. Ver en **github.com**.
- **RAG con LlamaIndex**: Usa un retriever en memoria. Ejemplo en las diapositivas: "¿Cuánto cuesta enviar un paquete grande a Francia?".

---

### Recursos y próximos pasos

Para seguir aprendiendo:

- **RAGHack (Agosto 2024)**: 25+ streams en **aka.ms/raghack/streams**.
- **RAG Deep Dive (Enero 2025)**: 11 streams en **aka.ms/ragdeepdive/watch**.
- **RAG Time (Marzo 2025)**: Temas avanzados en **aka.ms/rag-time**.
- **Repositorio GitHub**: Pueden seguir los ejemplos en **github.com/pamelafox/python-openai-demos**. Abran el repositorio y usen GitHub Codespaces para probar el código.

---

### Conclusión

Hemos cubierto desde los fundamentos de RAG hasta implementaciones avanzadas. Espero que esta explicación detallada les haya dado una visión clara de cómo usar RAG para superar las limitaciones de los LLMs y aplicar estas técnicas en sus proyectos. ¡Gracias por su atención, y nos vemos en la próxima sesión!