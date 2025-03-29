
# Python + IA (Español) (Microsoft Reactor)

Gwyneth Peña-Siguenza 
Python Cloud Advocate
madebygps.com/about 
@madebygps
Alias (GPS) 😊

### Cómo Funcionan los LLMs

Empezando: **¿Cómo funcionan los LLMs?** Una cosa que me encanta del español, pero que a la vez llega a ser un poquito confuso cuando estoy creando contenido, es que hay un montón de maneras de decir una palabra. Por ejemplo, yo en Ecuador sé que el "canguil" es popcorn, pero sé que la gente lo dice "palomitas" o no sé, pongan en el chat cómo dicen "canguil" en su país. Es lo mismo con este concepto de LLMs:  

- Grandes modelos de lenguaje.  
- Modelos de gran contexto del lenguaje.  
- Modelos de lenguaje grande.  

Hay un montón de opciones ahí, pero yo los voy a llamar **LLMs** de ahí en adelante, ¿saben a lo que me refiero, no? Lo genial es que a lo mejor ustedes ya han utilizado un LLM, bien sea en algo como **chatgpt.com** o si han utilizado **Copilot**. ¿Qué tal les parece Copilot? Mírenlo en el chat. ¿Han utilizado Copilot? ¿Cosas como Claude, Gemini? Bueno, un montón de cosas ahí, a lo mejor ustedes ya han utilizado, ¿no es cierto? Es importante saber que la tecnología detrás de esas aplicaciones es el modelo en sí, pero hay funcionalidad que estos programas tienen que no necesariamente son parte del LLM.

**¿Qué es un modelo de lenguaje grande?** Es un modelo de **machine learning**, que es un espacio que ya existe por muchos años. No es que ChatGPT empezó y pues ahí empezó esto de inteligencia artificial y machine learning. No, ya lleva décadas siendo una cosa. Un LLM no es nada más que un modelo de machine learning que es tan, pero tan, pero tan grande, que logra entender, comprender y generar lenguaje de uso cotidiano, de manera que nosotros hablamos. Por ejemplo: "Hola, ¿qué tal?" El modelo también puede decir: "Todo bien, ¿y tú?" Algo así, ¿no?

# Ejemplos

1. Tenemos alguna **entrada** (input) en lenguaje natural, que puede ser una oración, un párrafo, lo que sea.  
2. Estos modelos entienden a través de algo que se llama un **token**. Como nosotros los humanos entendemos en palabras, algo equivalente sería un token para el modelo. Eso llegaría a ser una **representación numérica de la palabra**, porque las computadoras entienden números, ¿no es cierto?  
3. Esos tokens se pasan al modelo, y el modelo utiliza esto para devolver la palabra que tiene más sentido o más relación con la palabra anterior o al contexto anterior.  
4. Después, **decodifica** eso (porque obviamente esto estaría en representación numérica), lo post-procesa para crear palabras a través de esos números y devuelve el resultado a ustedes.  

Por ejemplo, cuando ponen "Hola, ¿cómo estás?", el modelo les dice "Bien, ¿y tú?" o algo así. Todo eso que va en la mitad son números, ¿no es cierto? Vemos que, por ejemplo, la entrada "Hablaremos de LLMs" llegaría a ser 1, 2, 3, 4, 5 tokens. En inglés es casi una palabra por token, más o menos por ahí, y para otros lenguajes, en este caso español, vemos que tres palabras se convirtieron en seis tokens. Esto es porque la mayoría de estos modelos, la cantidad de información con la que se entrenan, está en inglés, por lo que les cuesta más computación, más tokens y todo eso entrenarlos en otro lenguaje.

![[1.1- Tokenizacion.png]]

Piensen que el modelo es como un **diccionario**. Este token tiene el ID 39, entonces el modelo sabe: "Oh, tengo que ir a la identificación 39 para encontrar este token". Nuestra entrada se convierte en estos tokens (en este caso serían seis), y el modelo nos devuelve el token que piensa que tiene que ser el siguiente según el contexto. El contexto es todo lo que sabe, ¿no es cierto? Al comienzo, es simplemente "Hablaremos de los LLMs", y después nos devuelve "hoy". Luego, el contexto crece: "Hablaremos de los LLMs hoy", y sigue creciendo hasta terminar y nos devuelve algo como: "Hablaremos de los LLMs hoy en la clase de programación". Esto quiere decir que el trabajo del modelo es devolver la siguiente palabra o token que tiene más sentido, calculado a través de una probabilidad.

![[1.2- Contexto.png]]

Una manera sencilla de describir cómo trabajan estos LLMs es decir que simplemente **predicen el siguiente token**. Es como un **autocompletar**, pero muy, muy, muy sofisticado. De seguro han escrito un mensaje de texto, ponen "Hola, ¿cómo estás?" y les sale una palabrita en gris que pueden darle clic y les completa todo. Eso es casi como el trabajo de un modelo de este tipo, solo que son muy, muy grandes, tienen un entendimiento muy grande y mucha composición detrás de ellos. Pero, en general, en resumen, así es como trabajan, ¿no?

![[1.3- Flujo de LLM.png]]

---

### Opciones de Modelos

Hablemos de **opciones de modelos**:  
1. **Gestionados (Hosted):** Estos están en la infraestructura de otra compañía.  
   - Ejemplos:  
     - **OpenAI** (openai.com): Modelos como GPT-3.5 (que casi ya no se usa, se considera legacy), GPT-4, GPT-4o (lo que se utiliza más ahora).  
     - **Azure AI**: Hay un montón, OpenAI GPT models, modelos de Meta, modelos de Cohere, Mistral, DeepSeek.
     - **GitHub Models**: Vamos a trabajar muchísimo con GitHub Models porque tiene un montón de opciones, una selección del catálogo de modelos que tiene Azure, y es **gratis**. Solo necesitan una cuenta de GitHub, nada más. Por eso, cuando hacemos esta serie, los demos, los ejercicios, nos gusta utilizar lo que es gratis y todos van a tener acceso a eso.  
     - **Google**: Gemini, Claude.
   - Si van a este enlace [Models · GitHub Marketplace](https://github.com/marketplace/models), les da una interfaz donde pueden seleccionar los modelos y trabajar. Por ejemplo, un ejemplo con OpenAI GPT-4o Mini. Obviamente tienen limitaciones grandes y no van a poder desplegar aplicaciones que deban estar en producción o tener escala de producción ahí, pero para experimentar y probar, muy genial.

2. **Modelos Locales:**  
   - Tienen **open weights** y pueden funcionar en máquinas personales o las máquinas que tengan ustedes.  
   - También hay algo que se conoce como **SLMs (Small Language Models)**. No hay una descripción concreta, pero más o menos se podría decir que son modelos más pequeños, menores a 100 billones de parámetros. Lo difícil de distinguir aquí es que, por ejemplo, la máquina que tengo yo puede correr ciertos modelos, y a lo mejor tú tienes una máquina mucho más potente y hay modelos que tú sí puedes correr y yo no. Pero, por lo general, los SLMs los podemos definir así.  
   - Cuando quieres trabajar de manera local, tienes que utilizar algo que se llama un **local model runner**. Los más populares serían:  
     - **Ollama**.  
     - **LLaMA File**.  
     - **LM Studio**.  
   - Ejemplo con Ollama: Si abro mi terminal y pongo `ollama run` y el nombre del modelo, ya puedo mandarle un mensaje como: "Cuéntame un chiste acerca de un gato". En este caso, sería LLaMA 3.2, y me dice: "¿Por qué el gato fue al veterinario? Porque tenía un problema de pelo en la cabeza". No entendí eso.  
   - ![[1.4- Demo Ollama.png]]
   - SLMs populares: LLaMA, Phi (de Microsoft, son muy buenos), DeepSeek R1, Mistral, LLaVA, Gemma, entre otros.

Hemos cubierto un poquito en cuanto a la fundación de información. Ahora podemos hablar más acerca de ejemplos utilizando **Python**.

---

![[1.5- Librerias.png]]

## Demos y Ejemplos Prácticos 

[pamelafox/python-openai-demos: A series of short examples using the OpenAI SDK](https://github.com/pamelafox/python-openai-demos). Este repositorio incluye todos los ejemplos prácticos que veremos a continuación y está diseñado para que puedan explorarlo después de la sesión a su propio ritmo. También proporcionamos enlaces para configurar un **codespace** a través del host que prefieran, siendo **GitHub Codespaces** nuestra recomendación por ser gratuito y venir preconfigurado. Si optan por usar modelos de **OpenAI**, necesitarán una API key. Para **Azure**, será necesario configurar una cuenta, mientras que con **Ollama**, al ser local, no requiere API key. La grabación de esta sesión también estará disponible en el mismo enlace del repositorio.

---

### Autenticación y Configuración

La autenticación depende del host que elijan para trabajar con los LLMs:  
- **OpenAI (openai.com)**: Requiere una API key que deben configurar como variable de entorno.  
- **Azure OpenAI**: Se recomienda usar **keyless authentication** (autenticación sin claves) con **Azure Default Credentials** por seguridad.  
- **Ollama (local)**: Solo necesitan configurar la URL base, sin API key.  
- **GitHub Models**: Fuera de un codespace, necesitan un **Personal Access Token (PAT)**, pero dentro de GitHub Codespaces, todo está preconfigurado.

OpenAI demos repo: [pamelafox/python-openai-demos: A series of short examples using the OpenAI SDK](https://github.com/pamelafox/python-openai-demos)
- Para acceder gratis: [aka.ms/python-openai-github](https://aka.ms/python-openai-github)
- Para usar el host de OpenAI: [aka.ms/python-openai-openai](https://aka.ms/python-openai-openai)
- Para utilizar Azure como host: [aka.ms/python-openai-azure](https://aka.ms/python-openai-azure)
- Para conectarte con Ollama: [aka.ms/python-openai-ollama](https://aka.ms/python-openai-ollama)

---

### Ejemplos Básicos en Python

A continuación, exploraremos algunos ejemplos básicos de cómo interactuar con LLMs usando Python:

1. **Chat Completion Simple**  
   - Abrimos el archivo `chat.py` del repositorio.  
   - Este ejemplo muestra la forma más sencilla de usar un LLM: creamos un **chat completion**.  
   - Configuramos parámetros como el nombre del modelo (por ejemplo, GPT-4), la **temperatura** (que ajusta la creatividad del modelo), y el número de respuestas (`n=1`).  
   - Enviamos una lista de mensajes:  
     - Un mensaje **system**: "Eres un asistente útil que hace muchas referencias a gatos y usa emojis 😺".  
     - Un mensaje **user**: "Escribe un haiku sobre un gato hambriento que quiere atún".  
   - Al ejecutar `python chat.py`, el modelo responde con algo como:  
     ```
     Gato maúlla fuerte,  
     atún en lata lo llama,  
     hambre lo persigue 😿.
     ```

2. **Streaming de Respuestas**  
   - En el archivo `chat_stream.py`, implementamos **streaming** para recibir respuestas token por token, en lugar de esperar el texto completo.  
   - Esto es ideal para aplicaciones en tiempo real donde la rapidez importa.  
   - Configuramos `stream=True` y ajustamos el código para procesar los fragmentos de respuesta a medida que llegan.

Estos ejemplos básicos están disponibles en el repositorio para que los prueben y modifiquen.
[pamelafox/python-openai-demos: A series of short examples using the OpenAI SDK](https://github.com/pamelafox/python-openai-demos)

---

# Autenticación API para hosts OpenAI

## OpenAI (openai.com)

Para configurar la API key:

```python
client = openai.OpenAI(api_key=os.environ["OPENAI_KEY"])
```

---

## Azure OpenAI (Autenticación sin clave)

Utiliza las credenciales predeterminadas de Azure para autenticación sin API key:

```python
token_provider = azure.identity.get_bearer_token_provider(
    DefaultAzureCredential(), "https://cognitiveservices.azure.com/.default"
)
client = openai.AzureOpenAI(
    api_version=os.environ["AZURE_OPENAI_VERSION"],
    azure_endpoint=os.environ["AZURE_OPENAI_ENDPOINT"],
    azure_ad_token_provider=token_provider,
)
```

Más información: [Keyless Connections](https://learn.microsoft.com/azure/developer/ai/keyless-connections)

---

# Autenticación API para OpenAI-like APIs

## Ollama

Configura la base URL a `localhost` y la key a cualquier valor.

## GitHub Models

Configura la base URL al host de GitHub Models y la API key con tu PAT (Personal Access Token):

```python
client = openai.OpenAI(
    base_url="https://models.inference.ai.azure.com",
    api_key=os.environ["GITHUB_TOKEN"]
)
```

En GitHub Codespaces, el `GITHUB_TOKEN` siempre almacenará tu PAT.  
Si se ejecuta localmente, crea un nuevo PAT:

```python
client = openai.OpenAI(
    base_url="http://localhost:11434/v1",
    api_key="nokeyneeded",
)
```

---

# Llamada a Chat Completion API

### Ejemplo básico

```python
response = client.chat.completions.create(
    model="gpt-4o",
    temperature=0.7,
    max_tokens=30,
    n=1,
    messages=[
        {"role": "system", "content": "Eres un asistente útil que hace muchas referencias a gatos y usa emojis."},
        {"role": "user", "content": "Escribe un haiku sobre un gato hambriento que quiere atún"}
    ]
)
print(response.choices[0].message.content)
```

_Ejemplo completo: `chat.py`_[python-openai-demos/spanish/chat.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/chat.py)

### Ejemplo con transmisión (streaming)

```python
completion = client.chat.completions.create(
    model=MODEL_NAME,
    stream=True,
    messages=[
        {"role": "system", "content": "Eres un asistente útil que hace muchas referencias a gatos y usa emojis."},
        {"role": "user", "content": "Escribe un haiku sobre un gato hambriento que quiere atún"}
    ]
)
for event in completion:
    print(event.choices[0].delta.content, end="", flush=True)
```

_Ejemplo completo: `chat_stream.py`_[python-openai-demos/spanish/chat_async.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/chat_async.py)


---

### Ventajas y Desventajas de los LLMs

#### **Ventajas**  

- **Creatividad**: Generan contenido original y son ideales para brainstorming o redacción creativa.  
- **Reconocimiento de patrones**: Excelentes para identificar estructuras en lenguaje y código.

#### **Desventajas**  

- **Alucinaciones**: Pueden inventar información con aparente certeza, lo que requiere verificación.  
- **Ventana de contexto limitada**: Aunque algunos modelos soportan hasta 128,000 tokens, esto puede no ser suficiente para tareas extensas.  
- **Costo y recursos**: Procesar más tokens aumenta el tiempo, el costo y el consumo energético.

Conocer estas características es clave para aprovechar los LLMs de manera efectiva.

---

### Cómo Mejorar los Resultados de los LLMs

Existen varias técnicas para optimizar las respuestas de los LLMs:

1. **Prompt Engineering**  
   - Instrucciones claras y específicas sobre tono, formato o estilo mejoran las respuestas.  
   - Ejemplo: "Responde como un pirata 🏴‍☠️" cambia el estilo drásticamente.

2. **Few-Shot Examples**  
   - Proporcionar ejemplos guía al modelo sobre cómo responder.  
   - Útil para formatos específicos sin reentrenamiento.

3. **Llamadas Encadenadas (Chained Calls)**  
   - Usar la salida de una llamada como entrada para la siguiente, refinando resultados paso a paso.

4. **RAG (Recuperación Aumentada por Generación)**  
   - Combinar generación de texto con búsqueda en bases de datos. (Se explorará el 18).

5. **Llamadas a Funciones y Salidas Estructuradas**  
   - Obtener respuestas en formatos como JSON. (Se cubrirá el 25).

6. **Fine-Tuning**  
   - Entrenar el modelo con datos específicos, aunque es costoso y no siempre necesario.

---

#### Ejemplo de Prompt Engineering

En `prompt_engineering.py`:  [python-openai-demos/spanish/prompt_engineering.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/prompt_engineering.py)
- Mensaje de sistema: "Actúa como Yoda de Star Wars. Responde con su tono y estilo".  
- Mensaje de usuario: "Explícame qué es un gato".  
- Respuesta: "Criatura felina, un gato es. Silencioso y astuto, sus pasos son. Compañero leal, a veces es 😸".

---

#### Ejemplo de Few-Shot Examples

En `few_shot_examples.py`:  [python-openai-demos/spanish/few_shot_examples.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/few_shot_examples.py)
- Mensaje de sistema: "Da pistas en lugar de respuestas completas".  
- Ejemplos:  
  - User: "¿Capital de Brasil?" → Assistant: "Piensa en la ciudad que no es Río".  
- Pregunta: "¿Planeta más grande?" → Respuesta: "Busca el que tiene una gran mancha roja".

---

#### Ejemplo de Llamadas Encadenadas

En `chain_calls.py`:  [python-openai-demos/spanish/chained_calls.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/chained_calls.py)
1. "Explica LLMs en un párrafo".  
2. "Revisa la explicación como editor".  
3. "Reescribe el párrafo con los comentarios". 

Resultado: Una explicación refinada en varias iteraciones.

---

### Librerías Populares para LLMs

Algunas librerías útiles incluyen:  

- [Langchain - Documentación](https://python.langchain.com/)  
    Orquestación
    
- [Llamaindex - Documentación](https://docs.llamaindex.ai/en/stable/)  
    Orquestación para RAG y Agentes
    
- [PydanticAI - Documentación](https://ai.pydantic.dev/)  
    Orquestación para RAG y Agentes
    
- [Semantic Kernel - Documentación]([semantic-kernel · PyPI](https://pypi.org/project/semantic-kernel/))  
    Orquestación
    
- [Autogen - Documentación](https://microsoft.github.io/autogen/)  
    Orquestación para flujos de agentes
    
- [Litellm - Documentación](https://github.com/BerriAI/litellm)  
    Wrapper para varios hosts
    
- ¡...y muchos más!
    

El repositorio incluye ejemplos con LangChain, Llama Index y Pandas AI.

[python-openai-demos/spanish/chat_langchain.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/chat_langchain.py)
[python-openai-demos/spanish/chat_llamaindex.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/chat_llamaindex.py)
[python-openai-demos/spanish/chat_pydanticai.py at main · pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos/blob/main/spanish/chat_pydanticai.py)

---

#### Cómo Elegir una Librería

Consideren:  
- **Compatibilidad** con modelos y hosts.  
- **Funcionalidades** como streaming o herramientas.  
- **Facilidad de uso** y depuración.  
- **Mantenimiento activo**.  
- **Costo-beneficio** para su proyecto.

---

### Creación de Aplicaciones Basadas en LLMs

Para aplicaciones completas:  
- **Frontend**: HTML/JavaScript.  
- **Backend**: Python con **FastAPI**, **Quart**, o **aiohttp** (asíncronos para mayor eficiencia).  
Ejemplo: Una app con chat y visión para describir imágenes o usar voz.
[Azure-Samples/openai-chat-vision-quickstart: A demonstration of chatting with uploaded images using OpenAI vision models like gpt-4o.](https://github.com/Azure-Samples/openai-chat-vision-quickstart)

---
![[1.6- APP Arquitectura.png]]

![[1.7- Quart.png]]

blog.pamelafox.org/2023/09/best-practices-for-openai-chat-apps_16.html

![[1.8- Porque Quart.png]]

[Best practices for OpenAI Chat apps: Concurrency](https://blog.pamelafox.org/2023/09/best-practices-for-openai-chat-apps.html)

![[1.9- Porque Quart 2.png]]

# Async Frameworks para Python

Hay varias opciones populares para trabajar de forma asíncrona en Python. Puedes consultar más detalles en este [blog post](https://blog.pamelafox.org/2024/07/should-you-use-quart-or-fastapi-for-ai.html).

## Frameworks y Ejemplo de Apps para Azure AI

- **Quart**  
    Ejemplo de app: [aka.ms/azai/chat](https://aka.ms/azai/chat)  
    Otros ejemplos:
    
    - [aka.ms/chat-vision-app](https://aka.ms/chat-vision-app)
    - [aka.ms/ragchat](https://aka.ms/ragchat)
- **FastAPI**  
    Ejemplo de app: [aka.ms/azai/fastapi](https://aka.ms/azai/fastapi)  
    Otro ejemplo: [aka.ms/rag-postgres](https://aka.ms/rag-postgres)
    
- **Aiohttp**  
    Ejemplo de app: [aka.ms/voicerag/repo](https://aka.ms/voicerag/repo)
    
- **Django con async**  
    (No se proporciona enlace específico, pero es una opción a considerar)
    

---

# Resumiendo en breves palabras todo lo que hemos visto anteriormente

## **1. Funcionamiento de los LLMs**

Los LLMs son modelos de machine learning de gran escala diseñados para comprender y generar lenguaje natural. La diapositiva explica su operación de forma clara, destacando dos procesos fundamentales:

- **Tokenización**: El texto de entrada (por ejemplo, "Hablaremos de LLMs") se descompone en unidades más pequeñas llamadas tokens. Estos tokens son procesados por el modelo para entender el significado y la estructura del lenguaje.
- **Generación de texto**: Los LLMs predicen la siguiente palabra o token basándose en el contexto previo, expandiendo iterativamente el texto para producir respuestas coherentes. Este proceso se basa en probabilidades calculadas a partir de su entrenamiento masivo con grandes volúmenes de datos.

Esta explicación desmitifica cómo los LLMs logran entender y responder preguntas, haciéndolo accesible incluso para quienes no tienen experiencia previa en IA. Además, se enfatiza que su capacidad para manejar contexto depende de su tamaño y del volumen de datos con los que fueron entrenados.

**Puntos clave:**
- La tokenización es el primer paso para que los LLMs procesen lenguaje natural.
- La generación iterativa basada en contexto permite respuestas fluidas y relevantes.

---

## **2. Opciones de modelos**

La diapositiva presenta una comparación práctica entre dos tipos principales de LLMs según su despliegue:

- **Modelos gestionados (hosted)**: Estos son ofrecidos por plataformas como OpenAI, Azure AI y GitHub Models. Se accede a ellos mediante APIs, lo que elimina la necesidad de infraestructura local. Son ideales para prototipos rápidos o experimentación, aunque pueden implicar costos asociados. Un punto destacado es que GitHub Models ofrece acceso gratuito, lo cual es una ventaja para desarrolladores con recursos limitados.
- **Modelos locales**: Ejemplificados por herramientas como Ollama, estos modelos se ejecutan en hardware propio, ofreciendo mayor control, privacidad y personalización. Sin embargo, requieren más recursos computacionales, como GPUs potentes, lo que puede ser una barrera para algunos usuarios.

Esta sección equilibra las ventajas y desventajas de cada enfoque, ayudando a los usuarios a elegir según sus necesidades específicas, como presupuesto, infraestructura o requisitos de seguridad.

**Puntos clave:**
- Los modelos gestionados son fáciles de usar pero pueden generar costos.
- Los modelos locales ofrecen autonomía a cambio de mayores demandas técnicas.

---

## **3. Uso de LLMs desde Python**

Uno de los aspectos más valiosos de la diapositiva es su enfoque práctico sobre cómo integrar LLMs en Python. Se incluyen ejemplos de código que cubren:

- **Autenticación**: Varía según el proveedor. Por ejemplo, OpenAI requiere una API key, mientras que Azure AI puede usar autenticación sin clave en algunos casos. Se recomienda almacenar credenciales en variables de entorno para mantener la seguridad.
- **Interacción básica**: Se muestra cómo realizar una solicitud simple de "chat completion" para obtener respuestas del modelo.
- **Streaming**: Se explica cómo implementar respuestas en tiempo real, mejorando la experiencia en aplicaciones interactivas.

Los ejemplos son claros y están acompañados de buenas prácticas, como la configuración segura de credenciales y el manejo eficiente de respuestas. Esto hace que la sección sea especialmente útil para desarrolladores que buscan implementar LLMs en sus proyectos.

**Puntos clave:**
- La autenticación depende del proveedor y debe configurarse cuidadosamente.
- El streaming optimiza la interacción en aplicaciones en tiempo real.

---

## **4. Mejora de los resultados del LLM**

Dado que las respuestas de los LLMs pueden ser impredecibles o no alinearse perfectamente con las expectativas, la diapositiva aborda técnicas para optimizarlas:

- **Prompt engineering**: Consiste en diseñar instrucciones claras y específicas para guiar al modelo hacia el tono, estilo o formato deseado. Por ejemplo, un prompt como "Responde como un profesor formal" cambia el estilo de la respuesta.
- **Few-shot examples**: Proporcionar ejemplos dentro del prompt (por ejemplo, "Dado A, responde B") permite al modelo aprender patrones sin necesidad de reentrenamiento.
- **Técnicas avanzadas**: Se mencionan conceptos como **llamadas encadenadas** (combinar múltiples solicitudes) y **RAG** (Recuperación Aumentada por Generación), aunque se indica que se explorarán en detalle más adelante.

Estas estrategias son accesibles y no requieren conocimientos avanzados, lo que las hace ideales para principiantes y expertos por igual. Los ejemplos prácticos refuerzan su utilidad.

**Puntos clave:**
- El prompt engineering es una técnica simple pero efectiva para controlar las respuestas.
- Los few-shot examples ajustan el comportamiento del modelo con mínima intervención.

---

## **5. Librerías LLM**

La diapositiva enumera y describe librerías populares de Python para trabajar con LLMs, facilitando su integración en proyectos más complejos:

- **LangChain**: Ideal para orquestar flujos de trabajo complejos, como combinar LLMs con bases de datos externas.
- **LlamaIndex**: Enfocada en indexar y recuperar información para aplicaciones basadas en búsqueda.
- **Pydantic AI**: Aunque podría ser un error tipográfico (posiblemente refiriéndose a Pandas AI u otra), se asume que ofrece herramientas para estructurar datos en proyectos de IA.

Se proporcionan ejemplos de código para conectar estas librerías a modelos como los de GitHub Models, junto con criterios para elegir la más adecuada según el caso de uso (por ejemplo, compatibilidad, funcionalidades específicas). Esto ayuda a los desarrolladores a tomar decisiones informadas.

**Puntos clave:**
- Cada librería tiene fortalezas únicas, desde orquestación hasta integración de datos.
- La elección depende de los objetivos y la complejidad del proyecto.

---

## **6. Creación de aplicaciones basadas en LLMs**

La diapositiva culmina con un ejemplo práctico: una aplicación de chat con capacidades de visión. Este caso demuestra cómo los LLMs pueden combinarse con otras tecnologías (como el procesamiento de imágenes) para crear soluciones innovadoras. Algunos detalles incluyen:

- **Framework**: Se usa Quart, un framework asíncrono, para manejar múltiples solicitudes eficientemente.
- **Arquitectura**: Se ilustra de forma sencilla, mostrando la interacción entre el frontend, el backend y el modelo.
- **Recursos**: Se proporcionan enlaces a ejemplos adicionales, incentivando la experimentación.

Este enfoque práctico inspira a los desarrolladores a ir más allá de las interacciones básicas y explorar aplicaciones escalables y multifuncionales.

**Puntos clave:**
- Los LLMs pueden integrarse con visión y otros tipos de datos para aplicaciones avanzadas.
- Los frameworks asíncronos mejoran el rendimiento en entornos de alta demanda.

---




[[Guía rápida de fundamentos en Python]]
[[2- Laboratorios de Python]]
[[1- Qué son y cómo Declarar Variables]]
[[2- Las Listas]]
[[3- Las Tuplas]]
[[4- Entrada de Información por parte del Usuario]]
[[5- Entrada de Información por parte del Usuario (Argumentos)]]
[[6- Los Diccionarios]]
[[7- Los Operadores Lógicos]]
[[8- Sentencias Condicionales]]
[[9- Bucle FOR]]
[[10- Bucle WHILE]]
[[11- Las Funciones]]
