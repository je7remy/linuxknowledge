---
tipo: laboratorio
tags: [ctf, pentraze, crypto, easy]
Plataforma: "Pentraze CTF"
Categoría: "Crypto"
Dificultad: "Easy"
Estado: "Completado"
Puntos: "25"
Flag: "PENTRAZE{dfb982e8552ce170f2227e10bfe46ad0c91e91594b2776f3837b6e8bb3ccd31b}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Crypto|Crypto]]
- **Dificultad:** [[CTF - Easy|Easy]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 25

# Writeup - Xouroboros

> [!info] Objetivo
> Recuperar el token administrativo de un oráculo de cifrado reutilizando el keystream y forjando un ciphertext nuevo.

- **Servicio:** `nc 34.135.253.132 34890`
- **Categoría:** Crypto
- **Dificultad:** Easy
- **Comandos:** `ENCRYPT <plaintext> | ADMIN | REDEEM <hex ciphertext> | QUIT`

## Resumen rápido de la cadena de ataque

1. `ADMIN` entrega un ciphertext de 36 bytes.
2. `ENCRYPT` devuelve un ciphertext de la misma longitud que el plaintext: se identifica un cifrado de flujo.
3. Se obtiene `K = C XOR P` con un plaintext elegido por el atacante.
4. Se descifra el token admin y se obtiene `ROLE:admin;user:admin;flag_gate:true`.
5. El servidor rechaza el ciphertext original por replay, pero acepta un plaintext equivalente con `user:root`.
6. Se forja `C' = P' XOR K` y se canjea con `REDEEM`.

## Vulnerabilidades explotadas

- **[[Keystream Reuse]]:** el keystream global no cambiaba entre peticiones.
- **[[Two-Time Pad]]:** dos textos conocidos permiten recuperar el XOR de sus claves.
- **Ausencia de nonce/IV único** en el servicio de cifrado.
- **Ausencia de autenticación del ciphertext:** no había MAC ni [[AEAD]], por lo que se podía alterar el plaintext válido.
- **Parser de roles demasiado permisivo:** `user:root` conservaba el rol `admin` y generaba un ciphertext distinto.

## Paso a paso técnico

### 1. Obtener el token del administrador

```text
ADMIN
CIPHERTEXT 59b8cd3800337e23cf7018de469f1c385b69043dbebf7a10090dc097fadadc8abaef06c2
```

El token ocupa 36 bytes, representados como 72 caracteres hexadecimales.

### 2. Sondear el oráculo

```text
REDEEM 0000...0000
# ERROR decrypted plaintext is not valid UTF-8

REDEEM 00
# ERROR plaintext does not satisfy the required admin role format

REDEEM <token_admin>
# ERROR replaying the ADMIN ciphertext verbatim is not accepted; recover the keystream and forge your own ciphertext
```

La primera respuesta demuestra que el servicio descifraba datos arbitrarios; la segunda, que validaba el formato después de descifrar. El error del replay fue la pista de [[Cryptography|forja de ciphertext]].

### 3. Identificar `C = P XOR K`

```text
ENCRYPT admin
# CIPHERTEXT 6a93ec1454
```

El resultado tiene 5 bytes, exactamente la longitud de `admin`; no hay bloques AES con padding. Para 80 caracteres `A` se obtuvo una respuesta de 80 bytes, por lo que se podía recuperar el keystream completo:

```text
K = ENCRYPT(b"A" * 80) XOR (b"A" * 80)
```

Para los primeros cinco bytes:

```text
P = 61 64 6d 69 6e
C = 6a 93 ec 14 54
K = 0b f7 81 7d 3a
```

La misma comprobación con `AAAA...` produjo los mismos cinco bytes de keystream.

### 4. Descifrar y forjar

El token administrativo se descifró con:

```text
P_admin = C_admin XOR K[:36]
```

Resultado:

```text
ROLE:admin;user:admin;flag_gate:true
```

El servidor exigía mayúsculas, punto y coma sin `;` final y `flag_gate:true` en minúsculas. Se probaron variantes; la válida fue:

```text
ROLE:admin;user:root;flag_gate:true
```

El campo `user` podía ser `root` sin perder el rol `admin`. Como el texto era distinto, el ciphertext no coincidía con el original y el servidor lo aceptaba.

### 5. Exploit reproducible

```python
#!/usr/bin/env python3
import socket
import time

HOST, PORT = "34.135.253.132", 34890


def conectar():
    s = socket.create_connection((HOST, PORT), timeout=5)
    s.settimeout(2)
    try:
        s.recv(4096)
    except socket.timeout:
        pass
    return s


def enviar(s, cmd, espera=1.5):
    s.sendall((cmd + "\n").encode())
    time.sleep(espera)
    s.settimeout(espera)
    data = b""
    while True:
        try:
            bloque = s.recv(4096)
            if not bloque:
                break
            data += bloque
        except socket.timeout:
            break
    return data.decode(errors="ignore")


def obtener_keystream():
    s = conectar()
    respuesta = enviar(s, "ENCRYPT " + "A" * 80)
    enviar(s, "QUIT", espera=0.5)
    s.close()
    for line in respuesta.splitlines():
        if "CIPHERTEXT" in line:
            ct = bytes.fromhex(line.split("CIPHERTEXT")[1].strip().split()[0])
            return bytes(c ^ 0x41 for c in ct)
    return None


def forjar(plaintext, keystream):
    p = plaintext.encode()
    return bytes(p[i] ^ keystream[i] for i in range(len(p))).hex()


def main():
    ks = obtener_keystream()
    assert ks, "no se pudo obtener el keystream"
    print(f"[+] keystream ({len(ks)} bytes): {ks.hex()}")

    plaintext = "ROLE:admin;user:root;flag_gate:true"
    ciphertext = forjar(plaintext, ks)
    s = conectar()
    respuesta = enviar(s, "REDEEM " + ciphertext).strip()
    enviar(s, "QUIT", espera=0.5)
    s.close()
    print(respuesta)


if __name__ == "__main__":
    main()
```

## Flag

```text
PENTRAZE{dfb982e8552ce170f2227e10bfe46ad0c91e91594b2776f3837b6e8bb3ccd31b}
```

## Lecciones aprendidas y mitigar

- Cada mensaje de un cifrado de flujo debe usar un nonce/IV único y una clave derivada de forma segura.
- No exponer un oráculo que permita cifrar textos elegidos por el atacante si el keystream es reutilizado.
- Usar [[AEAD]] como AES-GCM o ChaCha20-Poly1305: cifra y autentica el mensaje.
- Rechazar la reutilización de nonce, asociar el nonce al contexto y rotar claves después de cualquier uso.
- Validar el formato y la autorización en un parser estricto, pero no confundir validación con integridad criptográfica.
- Registrar intentos de replay y forjado; un check de “ciphertext ya usado” no sustituye un MAC.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Crypto]]
- ⬅️ Anterior: [[Writeup - Eco Persistente|Eco Persistente]]
- ➡️ Siguiente: [[Writeup - MATRIOSKA|MATRIOSKA]]

## Relacionadas

- [[Cryptography]] — principios de cifrado simétrico y autenticación.
- [[Authentication]] — validación de claims y autorización.
- [[Keystream Reuse]] — concepto central reutilizado en otros retos.
