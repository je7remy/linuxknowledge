Hola a todos, bienvenidos a esta sesión de hoy. Soy Larisa, responsable de eventos en Microsoft Reactor, y antes de comenzar, quiero pedirles que lean brevemente el **Código de Conducta de Microsoft**. En resumen, todos aquí somos amigables y respetuosos, incluyendo a los oradores. Microsoft Reactor es un espacio donde todos son bienvenidos. Recuerden que esta sesión será grabada y estará disponible en nuestro canal de YouTube en unas 48 horas. También tenemos un chat para sus preguntas, y contamos con un equipo listo para ayudarles y contestar todas sus dudas. ¡Así que empecemos con la sesión de hoy!

---

### Introducción a la sesión: Modelos de visión con Python y AI

Hola, hola, muchas gracias por la introducción. Aquí estoy, ajustando mi reloj para asegurarme de que nos mantengamos en el tiempo con toda la sesión. Vamos a compartir mi pantalla para que puedan seguir todo lo que voy a explicar. Perfecto, ya está listo. 

Son las **6 de la tarde aquí en Nueva York**, lo que significa que es hora de hablar de **Python y AI**. ¿Qué tal, cracks? ¿Cómo estamos? Me emociona ver cuántos de ustedes han estado en todas las sesiones. Ya estamos en la **cuarta sesión de esta serie**. Hemos cubierto temas como **LLMs**, **vector embeddings**, **RAG** (que lo vimos ayer), y hoy nos toca hablar de **modelos de visión**. El martes que viene veremos **salidas estructuradas**, y el jueves 27 cerraremos con **calidad y seguridad**. 

En el chat veo nombres como Pedro, Eric, Mario, Ángel, John, Francisco… ¡Qué bien, qué genial que estén presentes en todas! Hoy nos enfocaremos en **modelos de visión**, y para quienes quieran registrarse en toda la serie, aquí está el enlace: **[aka.ms/PythonIA/series](https://aka.ms/PythonIA/series)**. Ups, me olvidé de actualizar un enlace en la diapositiva, pero lo cambio ahora en vivo para no confundirlos. También, si quieren ponerse al día con las grabaciones de las sesiones anteriores, las encuentran en **[http://aka.ms/Pythonalgrabacio](http://aka.ms/Pythonalgrabacio)**. Ya lo compartimos en el chat también.

Hoy me toca hacer esta sesión en español antes que la de inglés, lo cual es un cambio porque normalmente hacemos inglés primero y luego español unas horas después. Pero mañana tengo otro evento, así que ajustamos el orden. Pamela, mi compañera, ha estado súper ocupada desplegando todos los demos necesarios para esta sesión. Terminé el último a las **5:44**, así que en el chat, por favor, digan **“Gracias, Pamela”**, porque ella se puso las pilas con baterías extra potentes para que todo estuviera listo. ¡Gracias, Pamela, de verdad!

---

### Contenido de la sesión: Modelos de visión

Hoy vamos a hablar de **modelos de visión**, y les comento que esta sesión reúne muchos temas que ya hemos visto en las anteriores. Si han estado conmigo desde el principio, esto les va a resultar muy familiar, pero ahora lo aplicaremos al contexto de los **modelos de visión**. Algunos de ustedes me han preguntado cómo trabajar con imágenes, así que hoy cubriremos eso en detalle. La agenda incluye:

- **Modelos de lenguaje multimodal**
- **Casos de uso populares**
- **Chat con imágenes**
- **Modelos de embeddings multimodales**
- **RAG con modelos de visión**

Empecemos con los **modelos de lenguaje grande multimodales**, o **LLMs multimodales**, como los llamamos.

#### ¿Qué es un LLM multimodal?

La realidad al **20 de marzo de 2025** es que la mayoría de los modelos multimodales trabajan con **imágenes** y, a veces, con **video o audio**. Los llamamos “multimodales” porque en el futuro podrán manejar más tipos de entradas, o “modales”. Pero por ahora, nos enfocamos principalmente en modelos de visión. 

Para explicarlo, usemos un diagrama que ya vimos en la **primera sesión** y repetimos en la **segunda**. Imaginen que tenemos una entrada de **lenguaje natural**, como una palabra, una oración o un texto (por ejemplo, “Monarch butterflies lay eggs on…”). El modelo no entiende palabras directamente; las convierte en **tokens** y luego en **representaciones numéricas** (o **embeddings**) mediante un proceso llamado **tokenización**. Esos números pasan por el modelo, que predice qué palabra tiene más probabilidad de seguir en el contexto.

Ahora, con una **imagen** como entrada, el proceso es similar. Tomamos la imagen, la codificamos directamente en **embeddings** (números que representan la información visual), y el modelo los procesa de la misma manera. ¿Por qué podemos trabajar con texto, imágenes, video o audio? Porque todo se convierte en **números**. Esto es clave, y por eso en la segunda sesión nos enfocamos tanto en entender los **embeddings**: son la base de cómo los modelos procesan cualquier tipo de información.

#### Modelos multimodales disponibles

¿Qué modelos multimodales existen hoy? Aquí hay una lista que vimos en las diapositivas:

| **Creador**   | **Modelos**                  | **¿Cómo acceder?**           |
|---------------|------------------------------|------------------------------|
| OpenAI        | GPT-4o, GPT-4o-mini          | Azure OpenAI, GitHub Models  |
| Microsoft     | Phi-3.5-vision, Phi-4-multimodal-instruct | Azure AI Services, GitHub Models |
| Meta          | Llama-3.2-Vision-instruct    | Azure AI Services, GitHub Models |

Pueden acceder a estos modelos a través de servicios como **[Azure OpenAI](https://azure.microsoft.com/products/ai-services/openai-service)**, **[GitHub Models](https://github.com/marketplace/models)** o **[Azure AI](https://ai.azure.com/)**. En las diapositivas encontrarán todos estos enlaces y más recursos para explorarlos.

---

### Ejemplo práctico: Chat con imágenes

Para esta sesión, vamos a trabajar con dos repositorios principales. El primero es **[aka.ms/chat-vision-app](https://aka.ms/chat-vision-app)**, donde hay una carpeta llamada **notebooks**. Dentro, está el archivo **chat_vision.ipynb**, que usaremos ahora. Ayer me corrigieron cómo decir las barras en inglés: no es “barrito para adelante” ni “barrito para atrás”, sino **diagonal** y **diagonal invertida**. Me gusta eso, así que lo adoptaré.

Abrí el cuaderno en mi pantalla (lo hago más grande para que lo vean bien). Este ejemplo está en inglés porque creo que ya tienen suficiente contexto de las sesiones anteriores para seguirlo, y les da una chance de practicar un poco el idioma. Si lo abren en un **codespace** (como vimos en la sesión pasada), solo den clic en “Crear codespace”, y se configura automáticamente con el entorno de GitHub Models. No necesitan instalar nada extra, pero revisen el README para más detalles.

Vamos al código. Primero, configuramos el entorno y autenticamos con **OpenAI**. Luego, enviamos un mensaje al modelo. Este es un ejemplo que ya hemos visto varias veces: creamos un mensaje con **rol de usuario**. En el chat les pregunté qué otros tipos de mensajes hemos usado, y algunos respondieron correctamente: **system** y **assistant**, además de **user**. ¡Genial, Denis, perfecto!

El mensaje que enviamos dice: **“Is this a unicorn?”** (¿Es esto un unicornio?), y adjuntamos una URL de una imagen: **[https://i.ytimg.com/vi/toR644E--w8/hq720.jpg](https://i.ytimg.com/vi/toR644E--w8/hq720.jpg)**. La imagen es de un rinoceronte, tomada de Wikipedia, no un unicornio (todos lo sabemos). Ejecutamos el código con:

```python
messages = [
    {
        "role": "user",
        "content": [
            {"type": "text", "text": "Is this a unicorn?"},
            {"type": "image_url", "image_url": {"url": "https://i.ytimg.com/vi/toR644E--w8/hq720.jpg"}}
        ]
    }
]
response = openai_client.chat.completions.create(model="gpt-4o", messages=messages)
```

El modelo responde que no es un unicornio. Así de sencillo: enviamos una URL, hacemos una pregunta, y el modelo procesa la imagen y el texto juntos, como si fuera solo texto. Esto es igual a lo que hemos hecho antes, pero ahora con imágenes.

Hay otra opción: enviar imágenes como **URI codificado en base64**. Aquí hay un ejemplo:

```python
def open_image_as_base64(filename):
    with open(filename, "rb") as image_file:
        image_data = image_file.read()
        image_base64 = base64.b64encode(image_data).decode("utf-8")
        return f"data:image/png;base64,{image_base64}"

messages = [
    {
        "role": "user",
        "content": [
            {"type": "text", "text": "What animal is pictured?"},
            {"type": "image_url", "image_url": {"url": open_image_as_base64("ur.png")}}
        ]
    }
]
```

Ejecutamos esto en el cuaderno (en Jupyter Notebook, cada celda se ejecuta por separado). Preguntamos: **“How could I make this into a unicorn though?”** (¿Cómo podría convertir esto en un unicornio?). El modelo procesa la imagen del rinoceronte y sugiere: quitar un cuerno, centralizar el otro, rediseñarlo, añadir características mágicas, etc. Vemos que puede analizar la imagen y dar ideas basadas en ella, todo porque trabaja con números.

---

### Casos de uso populares

¿Para qué sirve esto? Aquí algunos ejemplos que vimos en las diapositivas:

#### Accesibilidad
- **Sugerir texto alternativo para imágenes**: Por ejemplo, revisar accesibilidad en PowerPoint.
- **Ayuda a usuarios con problemas de visión**: Una app móvil increíble que mencioné es **[Be My Eyes](https://www.bemyeyes.com/)**. Alguien con dificultades visuales toma una foto, y otra persona (o un modelo) describe lo que hay en ella en tiempo real. Usa tecnología de LLMs y OCR por detrás. ¡Es genial!

#### Procesos empresariales más eficientes
- **Reclamos de seguros**: Identificar reclamos sospechosos analizando imágenes.
- **Análisis de datos**: Generar insights a partir de gráficos y tablas en PDFs.
- **Atención al cliente**: Responder preguntas sobre imágenes de productos.

Estos ejemplos están en el cuaderno **[chat_vision.ipynb](https://aka.ms/chat-vision-app)**.

---

### Enviando documentos que no son imágenes

Muchos me han preguntado cómo trabajar con PDFs. La clave está en que la mayoría de los modelos de visión solo manejan **JPEG, PNG y GIF estáticos** (sí, aprendí que existen GIFs que no se mueven, gracias a Pamela). Si tienes un PDF, necesitas convertirlo a imagen. Hay dos enfoques:

1. **Convertir todo el documento en una imagen**.
2. **Identificar y recortar la parte visual** (como una tabla o gráfico) y guardarla como imagen. Para esto, usamos **[Document Intelligence](https://aka.ms/document-intelligence-figure-extraction)**, que extrae figuras automáticamente.

Aquí un ejemplo con el paquete **PyMuPDF** para convertir un PDF a imágenes:

```python
import pymupdf
from PIL import Image

filename = "plants.pdf"
doc = pymupdf.open(filename)
for i in range(doc.page_count):
    page = doc.load_page(i)
    pix = page.get_pixmap()
    original_img = Image.frombytes("RGB", [pix.width, pix.height], pix.samples)
    original_img.save(f"page_{i}.png")
```

Abrimos **plants.pdf**, recorremos cada página, la convertimos a imagen PNG y la guardamos. Luego, en el cuaderno **chat_pdf_images.ipynb** (en el mismo repositorio), preguntamos: **“¿Qué plantas están listadas en estas páginas?”**. Enviamos las imágenes generadas y el modelo responde con un listado (por ejemplo, 10 plantas en una página, 5 en otra). Esto demuestra cómo transformar un PDF en algo que el modelo pueda procesar.

---

### Demo: Aplicación de chat con visión

Vamos a un demo práctico. Abrí la app en **[aka.ms/chat-vision-app/demo](https://aka.ms/chat-vision-app/demo)** (gracias otra vez a Pamela por desplegarlo). Es una aplicación donde cargamos imágenes y hacemos preguntas. Seleccioné una foto de reptiles y pregunté: **“¿Son caimanes o cocodrilos?”**. En el chat, algunos opinaron, pero dejé que la app respondiera.

La respuesta fue: **“En la imagen se observan varios reptiles que parecen ser caimanes. Una forma de diferenciarlos de los cocodrilos es observar ciertas características físicas: los caimanes tienen un hocico más ancho y redondeado, mientras que los cocodrilos suelen tener un hocico más estrecho y en forma de V”**. Procesó la imagen y mi pregunta perfectamente.

#### Arquitectura de la app
- **Frontend**: HTML y JavaScript. Codificamos la imagen a **base64** así:
  ```javascript
  const toBase64 = file => new Promise((resolve, reject) => {
      const reader = new FileReader();
      reader.readAsDataURL(file);
      reader.onload = () => resolve(reader.result);
      reader.onerror = reject;
  });
  form.addEventListener("submit", async function(e) {
      const file = document.getElementById("file").files[0];
      const fileData = file ? await toBase64(file) : null;
      // Enviar al backend
  });
  ```
  Esto está en **[index.html](https://aka.ms/chat-vision-app/src/quartapp/templates/index.html)**.

- **Backend**: Python con **Quart** (versión asíncrona de Flask) y **Uvicorn**. Manejamos la solicitud así:
  ```python
  @bp.post("/chat/stream")
  async def chat_handler():
      request_json = await request.get_json()
      image = request_json["context"]["file"]
      messages = [{"role": "user", "content": [
          {"text": request_json["messages"][-1]["content"], "type": "text"},
          {"image_url": {"url": image, "detail": "auto"}, "type": "image_url"}
      ]}]
      chat_coroutine = bp.openai_client.chat.completions.create(
          model="gpt-4o", messages=messages
      )
  ```
  Esto está en **[chat.py](https://aka.ms/chat-vision-app/src/quartapp/chat.py)**. Envía la imagen y la pregunta al modelo y devuelve una respuesta en **streaming** (vimos esto en la primera sesión: las palabras llegan rápido, no esperamos todo el texto).

#### Otras formas de subir imágenes
- **POST con multipart form data**: Ejemplo en **[aka.ms/chat-vision-multipart](https://aka.ms/chat-vision-multipart)**.
- **Carga separada**: 
  1. Guardar la imagen en **Azure Blob Storage**.
  2. Enviar el ID del archivo al frontend, que lo pasa al backend. Ejemplo:
     ```python
     output = io.BytesIO()
     new_img.save(output, format="PNG")
     output.seek(0)
     container_client.upload_blob(blob_name, output)
     ```
     Esto está en **[blobmanager.py](https://aka.ms/ragchat)**. Hay que estar atentos a la seguridad, especialmente con documentos sensibles.

---

### Modelos de embeddings multimodales

Volvamos a los **embeddings**, que vimos en la segunda sesión. Con modelos multimodales, creamos representaciones numéricas de imágenes y texto. Abrí el cuaderno **multimodal_vectors.ipynb** en el repositorio **[vector-embedding-demos](https://aka.ms/vector-embedding-demos)**, en la carpeta **spanish**.

Ya generé **embeddings** con el modelo **Azure AI Vision** para imágenes de Pamela y una lista de sustantivos (la misma de sesiones pasadas). Los guardé en archivos JSON. Luego, visualicé los embeddings gráficamente (como hicimos antes) y busqué similitudes usando **similitud del coseno** (la más popular, junto con distancia Manhattan y euclidiana).

Por ejemplo, tomé una imagen con el texto “inhale exhale” y busqué las 10 imágenes más similares:
- Resultados: “breath”, “incienso”, “vela”, “aire”… Todas relacionadas con respirar o formas similares. El modelo capta patrones visuales y semánticos.

Luego, busqué imágenes similares a la palabra **“cama”**:
- Resultados: Algunas parecían camas, otras no tanto (como una placa con texto, que me recordó a la de mi abuelita). Esto muestra cómo los embeddings multimodales mezclan texto e imágenes en números.

En el demo **[aka.ms/vector-embedding-demos/demo](https://aka.ms/vector-embedding-demos/demo)**, busqué palabras como:
- **“pájaro”**: Encontró aves.
- **“elefante”**: Imágenes de elefantes.
- **“banco”**: Edificios (banco financiero), bancos de nieve, montañas… Múltiples significados.

Esto es poderoso porque todo se reduce a números, y podemos buscar similitudes entre texto e imágenes. ¡Jueguen con el código y experimenten!

---

### RAG con modelos de visión

Ayer hablamos mucho de **RAG** (Retrieval-Augmented Generation). Hoy lo aplicamos a modelos de visión. Usamos el repositorio **[aka.ms/ragchat](https://aka.ms/ragchat)**, que Pamela desplegó hoy (¡gracias otra vez!). Configuré el demo para usar **GPT-4o Vision** (hay que activarlo en las opciones de desarrollador).

Pregunté: **“¿Hay alguna correlación entre los precios del petróleo y las tendencias del mercado de valores?”**. La respuesta fue:
- **“Sí, hay una correlación positiva entre los precios del petróleo y las tendencias del mercado de valores, específicamente con los índices S&P 500 y Nasdaq…”**, con más detalles.

Lo genial es la transparencia: hice clic en un botón y vi el **proceso de pensamiento**:
- **Prompt de búsqueda**: Cómo reescribió mi pregunta.
- **Búsqueda**: Usó filtros y embeddings de texto e imágenes.
- **Resultados**: Fuentes como “Financial Market Analysis Report 2023-3.png”.
- **Prompt de respuesta**: Cómo generó la respuesta final.

#### Flujo de RAG con visión
1. **Consulta del usuario**: “¿Hay alguna correlación…?”.
2. **Reescritura**: El modelo mejora la consulta.
3. **Embeddings**: Crea representaciones numéricas del texto con un modelo de visión (debe ser el mismo que usamos para las imágenes).
4. **Búsqueda**: En **Azure AI Search**, compara embeddings y recupera documentos relevantes (imágenes y texto).
5. **Respuesta**: GPT-4o genera la respuesta con las fuentes citadas.

#### Ingesta de datos
- **Almacenar imágenes**: En **Azure Blob Storage** (ejemplo en **blobmanager.py**).
- **Vectorizar**: Crear embeddings con **Azure AI Vision**.
- **Indexar**: Guardar en **Azure AI Search** con campos como:
  - **id**: Nombre del archivo.
  - **content**: Texto o descripción.
  - **image_embedding**: Embeddings de la imagen.
  - **source_page**: Origen.

Para citar fuentes, añadimos el nombre del archivo en la imagen (coordenadas 10,10 píxeles) con un paquete como **PyMuPDF**.

#### System prompt
El mensaje del sistema fue:
> Eres un asistente inteligente que ayuda a analizar el Informe Financiero Anual de Contoso Ltd. Los documentos contienen texto, gráficos, tablas e imágenes. Cada fuente de imagen tiene el nombre del archivo en la esquina superior izquierda con coordenadas (10,10) píxeles en el formato SourceFileName:<nombre_de_archivo>. Cada fuente de texto comienza con el nombre del archivo seguido de “:”. Incluye siempre el nombre de la fuente en la respuesta como [nombre_de_archivo]. Responde solo con los datos proporcionados. Sé breve. Si no puedes responder, di que no sabes.

#### Mensaje de usuario
Enviamos mensajes complejos, como:
```json
{
    "role": "user",
    "content": [
        {"type": "text", "text": "How have bitcoin and ethereum been fluctuating?"},
        {"type": "image_url", "image_url": {"url": "data:image/png;base64,..."}}
    ]
}
```

#### Consideraciones
- **Beneficios**: Encuentra coincidencias semánticas y usa detalles de imágenes no descritos en texto.
- **Desventajas**: Mayor latencia, más costo (tokens), limita la elección a modelos multimodales.

Más info en el blog de Pamela: **[aka.ms/ragchat/vision/blog](https://aka.ms/ragchat/vision/blog)** y su charla: **[aka.ms/ragdeepdive/watch](https://aka.ms/ragdeepdive/watch)**.

---

### Próximos pasos

Terminamos casi a tiempo (¡hablo rápido!). Lo que viene:
- **25/3**: Salidas estructuradas (formatos personalizados).
- **27/3**: Calidad y seguridad (mejorar resultados).

Otros eventos:
- **Horas de oficina**: Lunes, misma hora, en Discord (**aka.ms/pythonia/ho**). El lunes pasado éramos 15, resolviendo dudas como problemas con codespaces.
- **AI Agents Hackathon**: **[aka.ms/agentshack/es](https://aka.ms/agentshack/es)**, premios hasta $20,000.
- **Recursos**: **[aka.ms/thesource/Python_AI](https://aka.ms/thesource/Python_AI)**.

La sesión en inglés es mañana; revisenla para practicar y ver la versión de Pamela. Nos vemos el lunes en Discord y el martes en la próxima sesión. ¡Chao, gracias por acompañarme! Ahora, a cenar y a repasar los deberes.