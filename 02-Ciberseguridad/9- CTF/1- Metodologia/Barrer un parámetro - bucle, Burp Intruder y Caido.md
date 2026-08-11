---
tipo: teoria
tags: [ctf, web-exploitation, metodologia, herramientas, burp-suite, caido, pentraze]
actualizado: 2026-08-11
---

# Barrer un parámetro — bucle, Burp Intruder y Caido

Comparación de tres formas de barrer un rango de valores sobre un
parámetro o cookie, con foco en cuándo conviene cada una. Surge de
resolver [[Cookies]], donde había que probar un rango numérico de índices
hasta dar con el que rompía el patrón.

## 1. Bucle en terminal o script en Python

La opción más rápida de montar: desechable, sin límite de velocidad
artificial. Ideal cuando ya se está trabajando en consola y solo hace
falta recorrer un rango numérico, enviando el valor en cada petición y
quedándose con la respuesta que rompe el patrón.

Bucle con `curl`:

```bash
for i in $(seq 0 100); do
  curl -s -L -b "name=$i" "$URL" | grep -o 'picoCTF{[^}]*}'
done
```

Equivalente en Python con `requests`:

```python
import requests

for i in range(100):
    r = requests.get(url, cookies={"name": str(i)})
    if "picoCTF{" in r.text:
        print(i, r.text)
        break
```

No incluir en el script ninguna URL de instancia real ni la flag
capturada — ver la nota de restricciones en [[Cookies]].

## 2. Burp Suite — Intruder

El proxy de intercepción clásico. Flujo:

1. **Open Browser** dentro de Burp y navegar hasta la petición relevante.
2. Capturarla en **HTTP history**.
3. **Send to Intruder**.
4. Marcar el valor a barrer como variable (**Clear** + **Add** sobre la
   posición).
5. Configurar el payload tipo **Numbers** (`from` / `to` / `step`).
6. **Start attack** y leer la tabla de resultados por la columna
   **Length**.

**Limitación honesta:** en la versión **Community**, Intruder está
deliberadamente ralentizado ("tight throttled"), lo que lo hace lento
para barridos de rangos amplios.

## 3. Caido — Automate

Proxy más nuevo, escrito en Rust. Su tier gratuito (**Basic**, no expira)
**no ralentiza la automatización**, a diferencia de Burp Community. Está
disponible en los repositorios de Kali: `sudo apt install caido`.

Flujo equivalente:

1. Navegador integrado → capturar la petición en **HTTP History**.
2. **Send to Automate**.
3. Marcar el valor como **placeholder**.
4. Configurar el payload de rango numérico.
5. **Run** y leer los resultados por longitud.

El tier gratuito tiene topes (número limitado de proyectos/plugins, por
ejemplo) que no estorban para un barrido puntual como este.

## Criterio de elección

Para barrer un rango numérico, el script o el bucle ganan por velocidad
e independencia — no dependen de una GUI ni de límites de versión
gratuita. Burp y Caido brillan cuando hace falta **ver, tocar y reenviar**
peticiones complejas a mano (headers, flujos multi-paso, encadenar
hallazgos), no solo iterar un número.

En cualquiera de las tres vías el filtro final es el mismo: la anomalía
buscada puede ser una respuesta **más larga o más corta** que el resto —
lo relevante es la fila que **no encaja en ningún grupo**, como se detalla
en [[Cookies]].

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Identificar codificaciones, cifrados y hashes]]
- ➡️ Siguiente: [[Triaje de archivos - file, strings y exiftool]]

## Relacionadas

- [[Cookies]] — el reto que motivó esta comparación.
- [[Marco de ataque web - tres movimientos]] — marco general en el que
  este barrido cierra el movimiento 3.
- [[Scavenger Hunt]] — otro reto resuelto con barrido manual de
  superficie, antes de automatizar.
