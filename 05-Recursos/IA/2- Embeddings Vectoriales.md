
Gwyneth Peña-Siguenza 
Python Cloud Advocate
madebygps.com/about 
@madebygps
Alias (GPS) 😊
## Sesión Completa sobre Embeddings Vectoriales: Detalle Paso a Paso

Buenas tardes a todos y todas. Bienvenidos a esta segunda sesión de nuestra serie sobre Python e Inteligencia Artificial, organizada por Microsoft. Mi nombre es [su nombre, si aplica], y hoy, 13 de marzo, vamos a sumergirnos en un tema esencial y apasionante en el campo de la inteligencia artificial: **los embeddings vectoriales**. Este concepto es un pilar fundamental para muchas aplicaciones de IA, y estoy emocionado de compartirlo con ustedes. Antes de empezar, quiero asegurarme de que todo esté en orden: ¿me escuchan bien? ¿Pueden ver mi pantalla sin problemas? Por favor, confirmen en el chat para que podamos proceder con tranquilidad.

Esta sesión forma parte de una serie más amplia que incluye temas como Modelos de Lenguaje de Gran Escala (LLMs) el 11 de marzo, Recuperación Aumentada con Generación (RAG) el 18 de marzo, modelos de visión el 19 de marzo, salidas estructuradas el 25 de marzo y calidad y seguridad el 27 de marzo. Si aún no se han inscrito, pueden hacerlo en el enlace [aka.ms/PythonIA/series](https://aka.ms/PythonIA/series). Además, todas las diapositivas de esta presentación están disponibles para descargar en [aka.ms/pythonia/embeddings/diapositivas](https://aka.ms/pythonia/embeddings/diapositivas). Les recomiendo tenerlas a la mano para seguir el contenido paso a paso.

### Agenda de la Sesión

Hoy cubriremos los siguientes temas, cada uno explicado en detalle:

1. **¿Qué son los embeddings vectoriales?**
2. **Espacio de similitud vectorial**
3. **Búsqueda vectorial**
4. **Métricas de distancia vectorial**
5. **Cuantización vectorial**
6. **Reducción de dimensionalidad**

Sin más preámbulos, empecemos con el primer punto.

---

### 1. ¿Qué son los Embeddings Vectoriales?

Comencemos por definir qué son los **embeddings vectoriales**. En términos simples, un embedding vectorial es una representación numérica de datos, generalmente texto, en forma de una lista de números de punto flotante. Imaginen que queremos que una máquina entienda el lenguaje humano: palabras como "perro", "gato" o frases como "hola mundo". Las computadoras no pueden procesar palabras directamente, así que las convertimos en vectores, que son listas de números que representan esos datos en un espacio matemático multidimensional.

Por ejemplo, la palabra "perro" podría representarse como:

```
[0.017198, -0.007493, -0.057982, …]
```

Este vector no es aleatorio; cada número captura algún aspecto del significado o contexto de "perro", aprendido por un modelo de inteligencia artificial durante su entrenamiento. La longitud de estos vectores, conocida como su **dimensionalidad**, depende del modelo que los genera. Aquí tienen algunos ejemplos concretos de modelos populares y sus características:

| **Modelo**                | **Qué codifica**          | **Longitud del vector (Dimensiones)** |
|---------------------------|---------------------------|---------------------------------------|
| Word2Vec                 | Palabras individuales     | 300                                   |
| SBERT                    | Texto (~400 palabras)     | 768                                   |
| OpenAI text-embedding-ada-002 | Texto (hasta 8191 tokens) | 1536                            |
| OpenAI text-embedding-3-small | Texto (hasta 8191 tokens) | 512 o 1536                      |
| OpenAI text-embedding-3-large | Texto (hasta 8191 tokens) | 256, 1024 o 3072                |

Cada modelo tiene un propósito. Por ejemplo, Word2Vec es excelente para palabras individuales, mientras que `text-embedding-3-large` de OpenAI, con hasta 3072 dimensiones, captura matices semánticos más complejos en textos largos. La dimensionalidad afecta tanto la precisión como el costo computacional: más dimensiones suelen significar mayor detalle, pero también más recursos.

#### ¿Cómo se generan los embeddings?

Estos vectores no los inventamos nosotros; los genera un modelo de embeddings previamente entrenado. Vamos a ver cómo hacerlo en la práctica usando el SDK de OpenAI. Aquí tienen un ejemplo de código en Python para generar un embedding:

```python
import openai
import os

# Configuramos el cliente de OpenAI
openai_client = openai.OpenAI(
    base_url="https://models.inference.ai.azure.com",  # Endpoint de la API
    api_key=os.environ["GITHUB_TOKEN"]                # Clave de autenticación
)

# Solicitamos el embedding
response = openai_client.embeddings.create(
    model="text-embedding-3-small",  # Modelo elegido
    input="hola mundo",              # Texto a codificar
    dimensions=1536                  # Dimensionalidad deseada
)

# Imprimimos el vector resultante
print(response.data[0].embedding)
```

Paso a paso, este código:
1. Importa las bibliotecas necesarias (`openai` y `os`).
2. Crea un cliente de OpenAI con una URL base y una clave de API (en este caso, un token de GitHub almacenado como variable de entorno).
3. Llama al método `embeddings.create` con tres parámetros:
   - `model`: Especifica el modelo, aquí `text-embedding-3-small`.
   - `input`: El texto que queremos convertir en vector, "hola mundo".
   - `dimensions`: La longitud del vector, 1536 en este caso.
4. El resultado, almacenado en `response.data[0].embedding`, es una lista de 1536 números que representa "hola mundo".

Si quieren probar esto, pueden usar el notebook `generate_embedding.ipynb` disponible en el repositorio de la sesión. El vector resultante será algo como:

```
[0.013245, -0.009876, 0.045632, …]  # 1536 valores
```

#### Diferencias entre modelos

No todos los modelos producen el mismo embedding para una palabra. Por ejemplo, la palabra "queen" tendrá vectores distintos en `word2vec` (300 dimensiones), `text-embedding-ada-002` (1536 dimensiones) o `text-embedding-3-small` (512 o 1536 dimensiones). Esto se debe a que cada modelo fue entrenado con datos y técnicas diferentes, lo que afecta cómo "interpreta" el significado. Estas diferencias son cruciales cuando medimos similitudes, como veremos más adelante.

---

### 2. Espacio de Similitud Vectorial

Ahora que sabemos qué son los embeddings, pasemos al siguiente concepto: el **espacio de similitud vectorial**. Los embeddings no solo representan datos, sino que también nos permiten comparar cuán similares son entre sí. Imaginen un espacio tridimensional (aunque en realidad tiene cientos o miles de dimensiones): cada vector es un punto, y la distancia entre puntos refleja la similitud semántica.

#### Similitud del coseno

La métrica más común para medir esta similitud es la **similitud del coseno**, que calcula el coseno del ángulo entre dos vectores. Aquí está la fórmula matemática:

```math
\text{Similitud del coseno} = \frac{\mathbf{v1} \cdot \mathbf{v2}}{\|\mathbf{v1}\| \|\mathbf{v2}\|}
```

Desglosemos esto:
- **`v1 · v2`**: El producto punto, que es la suma de los productos de cada par de componentes de los vectores.
- **`‖v1‖` y `‖v2‖`**: Las magnitudes (o normas) de los vectores, calculadas como la raíz cuadrada de la suma de los cuadrados de sus componentes.
- El resultado está entre -1 y 1:
  - **1**: Los vectores son idénticos en dirección (máxima similitud).
  - **0**: Son perpendiculares (sin similitud).
  - **-1**: Apuntan en direcciones opuestas (máxima disimilitud).

Implementemos esto en Python:

```python
def cosine_similarity(v1, v2):
    # Calculamos el producto punto
    dot_product = sum(a * b for a, b in zip(v1, v2))
    # Calculamos las magnitudes
    magnitude_v1 = (sum(a**2 for a in v1)) ** 0.5
    magnitude_v2 = (sum(b**2 for b in v2)) ** 0.5
    # Devolvemos la similitud
    return dot_product / (magnitude_v1 * magnitude_v2)

# Ejemplo con vectores pequeños
v1 = [1, 2, 3]
v2 = [2, 4, 6]
print(cosine_similarity(v1, v2))  # Resultado: 1.0 (vectores proporcionales)
```

En la práctica, con embeddings reales, podríamos comparar "perro" y "gato" y obtener una similitud de, digamos, 0.56, mientras que "perro" y "avena" podrían dar 0.12, reflejando que "perro" y "gato" son más similares semánticamente.

#### Variación entre modelos

El rango de similitudes depende del modelo. Por ejemplo:
- En `text-embedding-ada-002`, las similitudes suelen estar entre 0.7 y 0.9.
- En `text-embedding-3-large`, el rango es más amplio, como 0.1 a 0.5.

Esto ocurre porque cada modelo distribuye los vectores de manera diferente en el espacio, influenciado por su entrenamiento y dimensionalidad.

#### Ejemplo práctico: Recomendaciones

Pensemos en un sistema de recomendación de recetas. Si buscamos recetas similares a "Apple Pie", podríamos obtener:

| **Receta**                | **Similitud del coseno** |
|---------------------------|--------------------------|
| Apple Pie by Grandma Ople | 0.000000                |
| Easy Apple Pie            | 0.051372                |
| Grandma's Iron Skillet Apple Pie | 0.054287         |

Aquí, "Apple Pie by Grandma Ople" tiene similitud 0 consigo misma (la consulta), y las otras recetas son cercanas en significado. Esto muestra cómo la similitud vectorial puede impulsar recomendaciones relevantes.

---

### 3. Búsqueda Vectorial

Pasemos ahora a la **búsqueda vectorial**, una técnica que usa embeddings para encontrar los elementos más similares a una consulta en una base de datos. Esto es clave en aplicaciones como motores de búsqueda semántica o sistemas de recomendación.

#### Proceso básico

Supongamos que tenemos una base de datos con embeddings de palabras como "culebra", "serpiente" y "lagarto". El proceso es:
1. Generamos el embedding de la consulta, por ejemplo, "culebra".
2. Comparamos este vector con todos los vectores en la base de datos.
3. Devolvemos los `k` más similares (e.g., los 3 más cercanos).

Hay dos enfoques principales:

##### Búsqueda Exhaustiva

Compara la consulta con cada vector en la base de datos. Aquí un ejemplo en Python:

```python
def exhaustive_search(query_vector, vectors):
    # Calculamos similitudes para cada vector
    similarities = [(title, cosine_similarity(query_vector, vector)) 
                    for title, vector in vectors.items()]
    # Ordenamos de mayor a menor similitud
    similarities.sort(key=lambda x: x[1], reverse=True)
    # Devolvemos la lista ordenada
    return similarities

# Ejemplo
vectors = {
    "culebra": [0.1, 0.2, 0.3],
    "serpiente": [0.12, 0.19, 0.31],
    "lagarto": [0.5, 0.6, 0.7]
}
query = [0.1, 0.2, 0.3]  # Embedding de "culebra"
results = exhaustive_search(query, vectors)
print(results)  # [("culebra", 1.0), ("serpiente", 0.998), ("lagarto", 0.974)]
```

Esto funciona bien con pocos datos, pero con millones de vectores, es demasiado lento.

##### Búsqueda Aproximada (ANN)

Para bases de datos grandes, usamos algoritmos de **búsqueda aproximada de vecinos más cercanos (ANN)**, como HNSW (Hierarchical Navigable Small Worlds). Aquí un ejemplo con la librería `hnswlib`:

```python
import hnswlib
import numpy as np

# Datos de ejemplo
vectors = np.array([[0.1, 0.2, 0.3], [0.12, 0.19, 0.31], [0.5, 0.6, 0.7]])
ids = np.arange(len(vectors))

# Creamos el índice
p = hnswlib.Index(space='cosine', dim=3)  # Espacio de coseno, 3 dimensiones
p.init_index(max_elements=1000, ef_construction=200, M=16)  # Configuración
p.add_items(vectors, ids)  # Añadimos vectores
p.set_ef(50)  # Parámetro de búsqueda

# Buscamos
query = np.array([0.1, 0.2, 0.3])
labels, distances = p.knn_query(query, k=2)  # 2 vecinos más cercanos
print(labels, distances)  # Ejemplo: [0, 1], [0.0, 0.002]
```

HNSW es rápido y eficiente, con un crecimiento logarítmico en tiempo de búsqueda, ideal para índices dinámicos.

#### Algoritmos ANN populares

| **Algoritmo** | **Librería Python** | **Bases de Datos Soportadas**                  |
|---------------|---------------------|-----------------------------------------------|
| HNSW          | hnswlib             | PostgreSQL (pgvector), Azure AI Search, ChromaDB, Weaviate |
| DiskANN       | diskannpy           | Cosmos DB                                     |
| IVFFlat       | faiss               | PostgreSQL (pgvector)                         |
| Faiss         | faiss               | Solo índice en memoria                        |

Cada uno tiene ventajas: HNSW es versátil, mientras que DiskANN optimiza almacenamiento en disco.

#### Aplicaciones

Un caso práctico es la **Recuperación Aumentada con Generación (RAG)**, donde la búsqueda vectorial encuentra documentos relevantes para enriquecer respuestas de modelos de lenguaje. Otro ejemplo es recomendar productos o detectar fraudes comparando patrones.

---

### 4. Métricas de Distancia Vectorial

Para comparar vectores, usamos métricas de distancia o similitud. Revisemos las principales:

1. **Distancia Euclidiana**: La distancia en línea recta entre dos puntos.
   ```math
   \text{Distancia Euclidiana} = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}
   ```
   Ejemplo: Entre `[1, 2]` y `[4, 6]`, es `√((1-4)² + (2-6)²) = √25 = 5`.

2. **Distancia de Manhattan**: Suma de diferencias absolutas.
   ```math
   \text{Distancia de Manhattan} = \sum_{i=1}^n |x_i - y_i|
   ```
   Ejemplo: Entre `[1, 2]` y `[4, 6]`, es `|1-4| + |2-6| = 3 + 4 = 7`.

3. **Producto Punto**: Suma de productos de componentes.
   ```math
   \text{Producto Punto} = \sum_{i=1}^n x_i y_i
   ```
   Ejemplo: Entre `[1, 2]` y `[4, 6]`, es `1*4 + 2*6 = 4 + 12 = 16`.

4. **Distancia del Coseno**: Complemento de la similitud del coseno.
   ```math
   \text{Distancia del Coseno} = 1 - \text{Similitud del Coseno}
   ```

#### Vectores unitarios

Un vector unitario tiene magnitud 1 (normalizado). En estos casos, el producto punto equivale a la similitud del coseno, simplificando cálculos. Los modelos de OpenAI generan vectores unitarios por defecto.

---

### 5. Cuantización Vectorial

La **cuantización vectorial** reduce el tamaño de los embeddings para ahorrar espacio y acelerar búsquedas, sacrificando algo de precisión.

#### Métodos

- **Cuantización Escalar**: Convierte floats (32 bits) a enteros (8 bits).
  - Proceso:
    1. Normalizar valores al rango [0, 1].
    2. Mapear a [-128, 127].
  - Ejemplo: `[0.032651, 0.013703]` → `[53, 40]`.

- **Cuantización Binaria**: Reduce a 1 bit (0 o 1).
  - Proceso: 1 si el valor es mayor al promedio, 0 si es menor.
  - Ejemplo: `[0.032651, 0.013703, -0.01]` → `[1, 1, 0]`.

#### Efectos

- **Similitud**: Con int8, los resultados son casi idénticos a float32; con binario, hay más variación, pero sigue siendo útil.
- **Almacenamiento**: Un índice de 1177 MB (float32) baja a 298 MB (int8) o 41 MB (binario) en Azure AI Search.

Prueben el notebook `quantization.ipynb` para verlo en acción.

---

### 6. Reducción de Dimensionalidad

La **reducción de dimensionalidad** disminuye la longitud de los vectores, preservando información clave. Una técnica moderna es **Matryoshka Representation Learning (MRL)**, soportada por `text-embedding-3-large`.

#### Ejemplo con OpenAI SDK

```python
response = openai_client.embeddings.create(
    model="text-embedding-3-small",
    input="hello world",
    dimensions=256  # Reducimos de 1536 a 256
)
```

#### Efectos

Comparando "Moana":

| **Película**          | **Similitud (1536 dim)** | **Similitud (256 dim)** |
|-----------------------|--------------------------|-------------------------|
| Moana                | 1.0000                  | 1.0000                 |
| Mulan                | 0.5468                  | 0.5834                 |
| Lilo & Stitch        | 0.5021                  | 0.5760                 |

La similitud se mantiene razonable con menos dimensiones.

#### Combinación con cuantización

Para máxima eficiencia:
- Reduzca dimensiones (e.g., a 256).
- Cuantice a int8 o binario.
- Sobremuestree resultados y reevalúe con vectores originales.

---

### Conclusión

Hemos recorrido los embeddings vectoriales desde su definición hasta técnicas avanzadas. Estos conceptos son fundamentales para aplicaciones como RAG, que exploraremos el 18 de marzo. Revisen los notebooks (`similarity.ipynb`, `search.ipynb`, etc.) y únanse a la próxima sesión. ¡Gracias y nos vemos pronto!

--- 

