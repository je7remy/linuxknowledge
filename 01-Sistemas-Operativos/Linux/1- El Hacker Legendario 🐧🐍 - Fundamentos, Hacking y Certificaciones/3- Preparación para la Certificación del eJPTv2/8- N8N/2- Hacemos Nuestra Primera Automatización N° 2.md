
# 🧠 Clase 2: Primeros Pasos con N8N y Automatización Básica (Petición HTTP + Procesamiento)

---

## 📌 Objetivo de esta clase

- Crear una cuenta en N8N (en la nube)
    
- Entender el concepto de _workflow_ y _trigger_
    
- Realizar una petición HTTP a una API real (Dockerlabs)
    
- Procesar la información recibida con JavaScript
    
- Obtener el número total de máquinas disponibles
    

---

## 🚀 Paso 1: Crear una cuenta en N8N (nube)

1. Ve a [https://n8n.io](https://n8n.io/)
    
2. Haz clic en **“Start for Free”**
    
3. Llena el formulario:
    
    - Nombre completo
        
    - Correo electrónico
        
    - Contraseña
        
    - Nombre de cuenta (importante, será tu subdominio: `tunombre.n8n.cloud`)
        
4. Accede a tu panel de N8N
    

👉 _Recuerda: tienes 15 días de prueba gratuita en la nube de N8N. Más adelante aprenderemos cómo instalarlo localmente para uso 100% gratuito._

---

## 🧪 Paso 2: Crear tu primer flujo (workflow)

1. Haz clic en **"Create Workflow"**
    
2. Aparecerá el lienzo vacío para comenzar a automatizar
    
3. Haz clic en el botón **“+”** y agrega un nodo de tipo **Manual Trigger**
    

> 🔹 _El trigger es lo que inicia la automatización. En este caso será manual: se activa al hacer clic._

---

## 🌐 Paso 3: Hacer una petición HTTP

1. Agrega un nuevo nodo: busca **HTTP Request**
    
2. Pega esta URL:
    
    ```
    https://dockerlabs.es/api
    ```
    
3. Ejecuta el nodo y verás una respuesta en formato JSON que contiene:
    
    - Nombre de las máquinas
        
    - Categorías
        
    - Enlaces
        
    - Dificultad
        
    - Autores
        
    - Etc.
        

---

## 🧮 Paso 4: Procesar los datos con JavaScript

1. Añade un nodo de tipo **Code**
    
2. En el campo de código, pega lo siguiente:
    

```javascript
// Este código cuenta cuántas máquinas hay
const items = $input.all();
const data = items[0].json;
const total = data.length;

return [
  {
    json: {
      total_maquinas: total,
    }
  }
];
```

3. Ejecuta el nodo y verás el resultado:
    

```
{
  "total_maquinas": 162
}
```

✅ ¡Perfecto! Has hecho tu primer flujo completo: disparador → petición HTTP → procesamiento con código.

---

## ✉️ ¿Qué puedes hacer con ese dato ahora?

Con la variable `total_maquinas`, puedes:

- Enviarte un correo con el número de máquinas
    
- Crear un mensaje automático en Telegram o Discord
    
- Guardarlo en Google Sheets
    
- Usarlo como condición para otras automatizaciones
    

> 📌 En la próxima clase: aprenderás cómo enviar correos electrónicos desde N8N usando Gmail.

---

## 🛠️ Herramientas utilizadas

- [N8N Cloud](https://n8n.io/)
    
- Dockerlabs API: `https://dockerlabs.es/api`
    
- JavaScript básico
    

---

## 🎓 Recapitulación

- Has creado tu cuenta en N8N
    
- Comprendiste el concepto de flujo y trigger
    
- Hiciste una petición HTTP real
    
- Procesaste datos usando código JavaScript dentro de N8N
    

---

## 📩 Ejemplo práctico: Contar flashcards y preguntas de ciberseguridad

1. Creamos un **flujo manual** en n8n.
    
2. Hacemos una **petición HTTP** al archivo JavaScript que contiene las preguntas:
    

👉 [https://flashcardgooglecybersecurity.netlify.app/js/modulo1.js](https://flashcardgooglecybersecurity.netlify.app/js/modulo1.js)

3. Queremos **contar el total de preguntas de ciberseguridad y flashcards** dentro del bloque `window.dataModulo1`.
    

---

### ✅ Código para usar en un nodo `Code` de n8n (JavaScript)

```javascript
// Paso 1: Obtener contenido bruto
let raw = items[0].json.data;

// Paso 2: Desescapar correctamente (muy importante)
raw = raw
  .replace(/\\n/g, '\n')
  .replace(/\\r/g, '\r')
  .replace(/\\"/g, '"')
  .replace(/\\\\/g, '\\');

// Paso 3: Buscar el bloque window.dataModulo1 = {...};
const inicio = raw.indexOf('window.dataModulo1 =');
if (inicio === -1) {
  throw new Error("No se encontró 'window.dataModulo1 =' en el texto.");
}

// Cortamos desde esa posición
const desde = raw.slice(inicio);

// Buscamos las llaves para extraer el bloque completo
const apertura = desde.indexOf('{');
let nivel = 0;
let fin = -1;

for (let i = apertura; i < desde.length; i++) {
  const char = desde[i];
  if (char === '{') nivel++;
  else if (char === '}') nivel--;
  
  if (nivel === 0) {
    fin = i;
    break;
  }
}

if (fin === -1) {
  throw new Error("No se pudo cerrar correctamente el bloque de datos.");
}

const bloqueObjeto = desde.slice(apertura, fin + 1);

// Paso 4: Evaluar el objeto
let data;
try {
  data = eval('(' + bloqueObjeto + ')');
} catch (err) {
  throw new Error("No se pudo evaluar el bloque de datos.");
}

// Paso 5: Contar y devolver
const flashcards = Array.isArray(data.flashcards) ? data.flashcards.length : 0;
const quiz = Array.isArray(data.quiz) ? data.quiz.length : 0;

return [
  {
    json: {
      flashcards,
      quiz_preguntas: quiz,
      total_preguntas_y_flashcards: flashcards + quiz
    }
  }
];
```

---
### 🔄 ¿Y si quieres usar otro módulo?

Si en lugar del módulo 1 usas el archivo:

👉 [https://flashcardgooglecybersecurity.netlify.app/js/modulo2.js](https://flashcardgooglecybersecurity.netlify.app/js/modulo2.js)

Entonces solo tienes que **cambiar esta línea**:

`const modulo = 'dataModulo1';`

`const modulo = 'dataModulo2';`

Y el mensaje de error de la misma manera que lo anterior, se intercambia el 1 por el 2 y así sucesivamente

✅ **Y listo**, ya n8n te devuelve el total automáticamente. ¡Superfácil!


![[2.1- Automatizacion.png]]

![[2.2- Resultado.png]]

---
