**Microsoft Python + IA: Llamada a Funciones y Salidas Estructuradas**  
*Por Gwyneth Peña-Siguenza, Python Cloud Advocate en Microsoft*  

---

### **Agenda**  
1. **Function Calling**: Integración de LLMs con funciones personalizadas.  
2. **Salidas Estructuradas**: Garantizar respuestas en formato JSON definido por el usuario.  
3. **Escenarios Populares**: Aplicaciones prácticas como RAG, agentes y filtros de búsqueda.  

---

### **1. Function Calling**  
Permite que los LLMs interactúen con funciones definidas por el desarrollador para acceder a datos externos o realizar acciones específicas.  

#### **Flujo Básico**  
1. **Definir herramientas**: Especificar funciones disponibles para el modelo.  
2. **LLM sugiere función y argumentos**: El modelo analiza la consulta y propone qué función usar.  
3. **Ejecutar función localmente**: El desarrollador llama a la función con los parámetros sugeridos.  
4. **Enviar resultados al LLM**: Integrar la respuesta de la función en el historial de mensajes para una respuesta final contextualizada.  

**Ejemplo: Consulta del clima**  
```python
tools = [{
    "type": "function",
    "function": {
        "name": "lookup_weather",
        "description": "Obtener el clima por ciudad o código postal.",
        "parameters": {
            "type": "object",
            "properties": {
                "city_name": {"type": "string"},
                "zip_code": {"type": "string"}
            }
        }
    }
}]

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "¿Qué clima hace en París?"}],
    tools=tools
)

# Respuesta del LLM sugiere llamar a lookup_weather(city_name="París")
# Ejecutar función y enviar resultados al modelo para respuesta final.
```

**Casos de Uso**  
- **RAG (Retrieval Augmented Generation)**: Generar consultas estructuradas para bases de datos (ej: `search_database("climbing_gear", price_filter={"operator": "<", "value": 30}`).  
- **Escalación a humano**: Detectar frustración del usuario y activar `human_escalation(requires_escalation=True)`.  
- **Búsquedas en GitHub**: Extraer issues relevantes con `github_search_issues(search_query="Deployment failure")`.  

---

### **2. Salidas Estructuradas**  
Garantiza que el modelo devuelva respuestas en formato JSON siguiendo un esquema definido.  

#### **Implementación con Pydantic**  
```python
from pydantic import BaseModel

class CalendarEvent(BaseModel):
    name: str
    date: str  # Formato: YYYY-MM-DD
    participants: list[str]

# Especificar el esquema en la llamada al modelo
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Alice y Bob irán a una feria el viernes."}],
    response_format={"type": "json_schema", "schema": CalendarEvent.model_json_schema()}
)

# Respuesta estructurada
print(response.choices[0].message.content)
# Output: {"name": "Feria de Ciencias", "date": "2024-03-28", "participants": ["Alice", "Bob"]}
```

**Casos de Uso**  
- **Extracción de entidades**: De PDFs, imágenes o páginas web (ej: facturas, tablas, gráficos).  
- **OCR con modelos de visión**: Analizar imágenes para obtener datos estructurados (ej: gráficos con título, ejes y leyenda).  
- **Alternativa a Function Calling**: Para respuestas predecibles sin ejecutar código externo.  

---

### **3. Recursos y Próximos Pasos**  
- **Repositorio de Ejemplos**: [github.com/pamelafox/python-openai-demos](https://github.com/pamelafox/python-openai-demos).  
- **Horas de Oficina**: Soporte en Discord: [aka.ms/pythonia/ho](https://aka.ms/pythonia/ho).  
- **Grabaciones y Material**: Disponibles en [aka.ms/PythonIA/grabaciones](https://aka.ms/PythonIA/grabaciones).  
- **Hackathon de Agentes de IA**: Registro en [aka.ms/agentshack/es](https://aka.ms/agentshack/es).  

---

### **Conclusión**  
Las **llamadas a funciones** y **salidas estructuradas** potencian aplicaciones de IA al integrar lógica personalizada y garantizar respuestas consistentes. Para profundizar:  
- Experimente con los ejemplos del repositorio.  
- Participe en las sesiones de calidad y seguridad (27/3) para optimizar sus implementaciones.  
- Únase al hackathon de agentes para aplicar estos conceptos en proyectos reales.  

¡Nos vemos en la próxima sesión! 🚀  
*Gwyneth Peña-Siguenza | [LinkedIn](https://linkedin.com/in/madebygps)*