
---

#Python #BeautifulSoup #WebScraping #HTML #DataExtraction #Automation #TextProcessing #PythonWebScraping #WebParsing

---
## **1️⃣ Primera versión: Buscar y mostrar los `<div>` con clase `"container"`**

```python
from bs4 import BeautifulSoup

html_content = '''
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Plantilla HTML5</title>
</head>
<body>
    <div class="container">
        <h1>Bienvenido a Mi Sitio Web</h1>
    </div>
</body>
</html>
'''

objecto_beautifulsoup = BeautifulSoup(html_content, 'html.parser')

leer_divs = objecto_beautifulsoup.find_all('div', class_="container")

print(leer_divs)  
```

🔹 **¿Qué hace este código?**

1. Se define un HTML con un solo `div class="container"`.
2. Se analiza el HTML con `BeautifulSoup`.
3. Se buscan **todos los `div` con la clase `"container"`**.
4. Se imprime `leer_divs`, que es una **lista de objetos `BeautifulSoup`**.

🔹 **Salida esperada:**

```html
[<div class="container">
    <h1>Bienvenido a Mi Sitio Web</h1>
</div>]
```

🔹 **Problema:** Se obtiene una lista con etiquetas HTML completas. No se extrae solo el texto.

---

## **2️⃣ Segunda versión: Iterar sobre `leer_divs`, pero con error**

```python
for div in leer_divs:
    print(leer_divs)
```

🔹 **¿Qué cambia aquí?**

- Se intenta iterar sobre `leer_divs`, pero en lugar de imprimir cada `div`, **se imprime la lista completa en cada iteración**.

🔹 **Salida inesperada:**

```html
[<div class="container">
    <h1>Bienvenido a Mi Sitio Web</h1>
</div>]
[<div class="container">
    <h1>Bienvenido a Mi Sitio Web</h1>
</div>]
...
```

🔹 **Problema:** Se imprime la lista **repetidamente** en cada iteración.

---

## **3️⃣ Tercera versión: Imprimir cada `<div>` individualmente**

```python
for div in leer_divs:
    print(div)
```

🔹 **¿Qué cambia aquí?**

- Ahora se imprime cada `div` en la iteración.

🔹 **Salida esperada:**

```html
<div class="container">
    <h1>Bienvenido a Mi Sitio Web</h1>
</div>
```

🔹 **Problema:** Aún se muestran las etiquetas HTML.

---

## **4️⃣ Cuarta versión: Extraer solo el texto dentro de cada `<div>`**

```python
for div in leer_divs:
    print(div.text)
```

🔹 **¿Qué cambia aquí?**

- Se usa `.text`, lo que **extrae solo el contenido textual dentro de los `div`**, eliminando etiquetas HTML.

🔹 **Salida esperada:**

```
Bienvenido a Mi Sitio Web
```

🎯 **¡Este es el resultado deseado!**

---

## **5️⃣ Última versión: Filtrar solo el `<div class="container footer">`**

```python
leer_divs = objecto_beautifulsoup.find_all('div', class_="container footer")

for div in leer_divs:
    print(div.text)
```

🔹 **¿Qué cambia aquí?**

- Se filtra solo el `div` que tiene ambas clases: `"container"` y `"footer"`.

🔹 **Salida esperada:**

```
© 2025 Mi Sitio Web. Todos los derechos reservados.
```

Esto nos permite obtener únicamente el texto dentro del `<div class="container footer">`.

---

### **Código Final Completo**

```python
from bs4 import BeautifulSoup

html_content = '''
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Plantilla HTML5</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        .container {
            max-width: 900px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            border-radius: 8px;
        }
        .header, .main, .aside, .footer {
            padding: 15px;
            margin: 10px 0;
            background: #ddd;
            border-radius: 5px;
        }
        .header {
            text-align: center;
            background-color: #333;
            color: white;
        }
        .main {
            background-color: #e6e6e6;
        }
        .aside {
            background-color: #cfcfcf;
        }
        .footer {
            text-align: center;
            background-color: #444;
            color: white;
        }
    </style>
</head>
<body>
    <div class="container header">
        <h1>Bienvenido a Mi Sitio Web</h1>
    </div>
    <div class="container main">
        <h2>Sección Principal</h2>
        <p>Este es el contenido principal del sitio web.</p>
    </div>
    <div class="container aside">
        <h2>Barra Lateral</h2>
        <p>Aquí puedes colocar enlaces, información adicional o anuncios.</p>
    </div>
    <div class="container footer">
        <p>&copy; 2025 Mi Sitio Web. Todos los derechos reservados.</p>
    </div>
</body>
</html>
'''

objecto_beautifulsoup = BeautifulSoup(html_content, 'html.parser')
leer_divs = objecto_beautifulsoup.find_all('div', class_="container footer")

for div in leer_divs:
    print(div.text)
```

---

## **Progresión Resumida**

1️⃣ Buscar los `div` con la clase `"container"` y mostrarlos como lista.  
➝ `print(leer_divs)`

2️⃣ Intentar iterar sobre `leer_divs`, pero imprimiendo toda la lista en cada iteración.  
➝ `for div in leer_divs: print(leer_divs)`

3️⃣ Iterar correctamente, mostrando cada `div` por separado.  
➝ `for div in leer_divs: print(div)`

4️⃣ Extraer solo el texto dentro de cada `div`.  
➝ `for div in leer_divs: print(div.text)`

5️⃣ Filtrar por una clase específica (`"footer"`) y extraer su texto.  
➝ `leer_divs = objecto_beautifulsoup.find_all('div', class_="container footer")`

---

🎯 **Conclusión:**  
Este análisis muestra cómo se refinó el código para extraer texto de elementos HTML con `BeautifulSoup`. A través de iteraciones, se pasó de imprimir la lista de `div` completos a mostrar cada uno, eliminar etiquetas y filtrar elementos específicos. ¡Este proceso es clave en Web Scraping! 🚀