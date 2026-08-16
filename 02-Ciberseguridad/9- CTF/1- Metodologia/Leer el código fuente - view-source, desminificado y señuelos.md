---
tipo: cheatsheet
tags: [ctf, web-exploitation, view-source, minificacion, cheatsheet, pentraze]
actualizado: 2026-08-16
---

# Leer el código fuente — view-source, desminificado y señuelos

Detalle del **movimiento 1** del [[Marco de ataque web - tres movimientos]]
(lo que el servidor entrega sin pedirlo), para el caso en que el dato no
está oculto por ninguna lógica sino simplemente escrito de una forma
incómoda de leer.

## Código fuente vs. página renderizada

El navegador **renderiza** el HTML/CSS/JS interpretándolo: solo se ve en
pantalla lo que produce texto o elementos visibles. Un dato guardado en
un atributo (`class`, `data-*`, un comentario, un `<p>` vacío) sigue
estando en el código aunque no aparezca en la página — visible con
"Ver código fuente" (`Ctrl+U`) o las DevTools. Regla práctica: si algo no
aparece en pantalla, no asumir que no está; revisar el código, no solo
la vista renderizada.

## Desminificar / beautify

*Minificar* comprime el código quitando espacios, saltos de línea y todo
lo prescindible; el resultado queda en una sola línea, ilegible para un
humano pero funcionalmente idéntico. *Desminificar* (o *beautify*) es
revertir eso: dar formato para poder leerlo. Las DevTools (pestaña
**Sources**/Depurador) traen un *pretty print* (`{}`) que lo hace
automáticamente. Con un archivo corto puede bastar con leer el código
crudo a ojo; en uno largo, desminificar deja de ser opcional.

## Patrón de descarte de señuelos

Cuando el código está inundado de candidatos idénticos (por ejemplo,
muchos `class="picoctf{}"` vacíos), el dato real suele diferenciarse por
un detalle sutil — capitalización, contenido no vacío, una posición
distinta — y no por destacar a simple vista. Es el mismo instinto que
ordenar por longitud en [[Cookies]] y quedarse con la fila que **rompe
el patrón**, no con la más larga ni la más corta.

Ver [[Unminify]] para un caso aplicado completo.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[SSTI - de la detección al RCE en Jinja2]]
- ➡️ Siguiente: [[Reversing - de leer código fuente a desensamblar binarios]]

## Relacionadas

- [[Unminify]] — el writeup que estrena esta metodología.
- [[Marco de ataque web - tres movimientos]] — movimiento 1, detallado aquí.
- [[Cookies]] — mismo instinto de descarte de señuelos aplicado a otro tipo de dato.
