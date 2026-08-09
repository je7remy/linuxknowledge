---
tipo: teoria
tags: [ctf, web-exploitation, metodologia, pentesting, pentraze]
actualizado: 2026-08-09
---

# Marco de ataque web — tres movimientos

Marco mental para abordar cualquier reto de [[_9- CTF|CTF]] web desde cero,
sin depender de intuición ni de checklist memorizada. Sirve como punto de
partida antes de recurrir a herramientas específicas.

## Los tres movimientos

### 1. Lo que el servidor te dio sin pedirlo

El código fuente HTML completo, los archivos que carga la página (CSS,
JS), y los comentarios olvidados del desarrollador. Es información que el
servidor entrega por defecto al renderizar la página — no hace falta
manipular nada para verla, solo mirar con atención.

### 2. Lo que el navegador guarda

Cookies, almacenamiento local (`localStorage`, `sessionStorage`), y
cabeceras de respuesta. La pestaña **Red** (Network) del inspector lista
todos los archivos que el navegador descargó para construir la página,
incluidos los que no aparecen enlazados en la navegación visible.

### 3. Lo que puedes manipular

Parámetros de URL, campos de formulario, valores ocultos (`hidden`
inputs). La pregunta que ordena este movimiento: **si el sitio confía en
algo que controla el cliente, ahí está la grieta.**

## Regla anti-rabbit-hole

Más de 30–40 minutos atascado en un reto durante competencia significa
pasar a otro. En la clasificatoria individual de Pentraze 2026,
**amplitud vence a profundidad**: sumar puntos en varios retos fáciles
rinde más que forzar uno solo hasta el final.

Ver [[Archivos y rutas ocultas en retos web]] para el detalle del
movimiento 1 (rutas que no aparecen enlazadas) y
[[Identificar codificaciones, cifrados y hashes]] para cuando el
movimiento 3 revela una cadena que no se lee en claro.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ➡️ Siguiente: [[Archivos y rutas ocultas en retos web]]

## Relacionadas

- [[Archivos y rutas ocultas en retos web]] — rutas concretas para el movimiento 1.
- [[Identificar codificaciones, cifrados y hashes]] — qué hacer con lo que encuentras manipulando el movimiento 3.
- [[Scavenger Hunt]] — aplicación directa de los tres movimientos en un reto real.
- [[MOC - Web Pentesting OWASP]] — marco más amplio de pentesting web profesional.
