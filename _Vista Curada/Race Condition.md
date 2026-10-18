---
tipo: teoria
tags: [race-condition, concurrencia, web, logica-de-negocio, entity-page]
aliases: [Condición de carrera]
actualizado: 2026-10-18
---

# Race Condition — Condición de carrera

Una condición de carrera surge cuando el resultado de operaciones que comparten estado depende de su intercalado. En seguridad, importa si ese intercalado permite incumplir una invariante: por ejemplo, que un cupón se consuma una sola vez.

## Comprobación, consumo y atomicidad

Una comprobación correcta en una petición aislada puede ser insuficiente. Si varias solicitudes observan «cupón disponible» antes de registrar su consumo, pueden acreditar varias veces. Esta secuencia explica el resultado de [[Writeup - Nozama Store]], pero el backend no estaba disponible para verificar su implementación exacta.

- **Evidencia secuencial:** primer canje de US$50; siguientes respuestas `409 already_used`.
- **Evidencia concurrente:** 22/25 canjes en la prueba inicial y 30/30 en la ejecución final; saldo final previo a compra de US$1,500.
- **Identidad compartida:** las peticiones reutilizaban la cookie `PHPSESSID`. Su presencia no demuestra qué almacenamiento o bloqueo usaba el servidor PHP.
- **Atomicidad:** comprobar elegibilidad, consumir el cupón y acreditar saldo deben respetar una única transición consistente.

## Concurrencia desde Python

`ThreadPoolExecutor` programa trabajo en varios hilos y permite solapar solicitudes de E/S. Un pool de 30 workers no garantiza que las 30 peticiones lleguen exactamente en el mismo instante; el efecto se demuestra con las respuestas y el estado posterior. Ver [[1- Introducción a la Programación Concurrente]] y el script conservado en [[Writeup - Nozama Store]].

## Comparación con TOCTOU

TOCTOU es el patrón *Time-of-Check to Time-of-Use*: una condición cambia entre comprobarla y utilizarla. [[Writeup - HooKitty]] valida una dirección DNS y usa otra tras resolver de nuevo. El aprendizaje común es fijar el objeto/estado validado durante la operación; no implica que ambos retos tengan la misma implementación ni que HooKitty use el exploit de cupones.

## Mitigación y verificación

- Usar una operación transaccional con control de concurrencia adecuado; una transacción sin aislamiento/bloqueos suficientes puede seguir siendo vulnerable.
- Imponer unicidad del canje por usuario/cupón en el almacén de datos.
- Diseñar operaciones idempotentes cuando corresponda y validar saldo en servidor.
- Verificar invariantes y saldo persistido con pruebas concurrentes, además del código HTTP.

## Navegación

- ⬆️ Carpeta: [[_Vista Curada]]
- 🏠 [[MOC - Web Pentesting OWASP]]

## Relacionadas

- [[Writeup - Nozama Store]] — caso completo y resultados.
- [[Writeup - HooKitty]] — validación y uso separados en DNS.
- [[MOC - Python para Ciberseguridad]] — automatización con sesiones y concurrencia.
- [[PostgreSQL]] — restricciones y permisos como garantías del estado persistente; no es una afirmación sobre el motor de Nozama.
