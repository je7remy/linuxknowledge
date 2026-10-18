---
tipo: cheatsheet
tags: [ctf, criptografia, codificacion, hashing, cheatsheet, pentraze]
actualizado: 2026-10-18
---

# Identificar codificaciones, cifrados y hashes

Distinción de base para no perder tiempo intentando "decodificar" algo
que ya está en claro, o tratando como codificación algo que en realidad
es un hash irreversible.

## Distinción de base

- **Codificación** — reversible sin clave. Base64, Base32, Hex, binario,
  URL-encoding, ASCII decimal. La longitud varía con el texto de entrada.
- **Cifrado** — necesita clave. ROT13 y César son cifrado débil, sin
  seguridad real.
- **Hash** — una sola vía, no reversible. Longitud **fija** sin importar
  el tamaño de la entrada.

## Longitudes de hash (caracteres hexadecimales)

| Hash | Longitud |
|---|---|
| MD5 | 32 |
| SHA-1 | 40 |
| SHA-256 | 64 |
| SHA-512 | 128 |
| bcrypt | empieza por `$2b$` |

## Reglas de identificación rápida

- Contar la longitud es el método #1 para distinguir hash de codificación.
- Base64 termina en cero, uno o dos signos `=`, pero la ausencia de `=`
  **no** lo descarta.
- En ROT13 los números no se mueven, solo las letras.
- Contraseñas comunes (`admin123`, `password`) no se "descifran": se
  rompen por diccionario. Ver [[Hoja de Trucos HASHCAT]].
- **Si la cadena ya se lee en texto plano, no hay nada que decodificar.**
  Ver [[Scavenger Hunt]].

<!-- PEGAR AQUÍ TABLAS DE EJEMPLOS -->

## Casos conectados de PentraZE

- [[Writeup - Lives 9, Backups 0]]: Base32 reconstruyó 83 fragmentos de datos DNS, pero no volvió legible el binario recuperado. El secreto se encontró en RAM; la plataforma aceptó el hexadecimal original, no su traducción ASCII. Decodificar no equivale a descifrar ni a respetar el formato de respuesta.
- [[Writeup - Data Del Más Allá]]: XOR con `0x5A` desofuscó una clave; después SHA-256 produjo un digest cuyo hexadecimal se truncó a 16 caracteres. El truncamiento explica por qué un token basado en SHA-256 no tenía 64 caracteres: la longitud es una pista, no una identificación concluyente.
- [[Writeup - Xouroboros]]: XOR permitió recuperar un keystream reutilizado. Comparar ese ataque criptográfico con una ofuscación fija evita atribuir la misma causa raíz a ambas operaciones.

---

## Navegación

- ⬆️ Carpeta padre: [[_1- Metodologia|1- Metodologia]]
- ⬅️ Anterior: [[Archivos y rutas ocultas en retos web]]
- ➡️ Siguiente: [[Barrer un parámetro - bucle, Burp Intruder y Caido]]

## Relacionadas

- [[WebDecode]] — reto donde reconocer Base64 fue el paso decisivo.
- [[Scavenger Hunt]] — caso donde sospechar codificación de más hizo perder tiempo.
- [[Hoja de Trucos HASHCAT]] — qué hacer una vez identificado un hash de contraseña.
- [[Marco de ataque web - tres movimientos]] — dónde encaja esta nota dentro del flujo general.
