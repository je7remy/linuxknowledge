---
tipo: laboratorio
Plataforma: Pentraze CTF
Ronda: 2
Fuente: '[[assets/PentraZE-2026-ronda-2/ctf.docx]]'
actualizado: 2026-10-18
tags: [ctf, pentraze, ronda-2, web, forensics, volatility, dns]
Categoría: Web / Forensics
Estado: Completado — 4/4 preguntas
Preguntas_completadas: 4
Preguntas_totales: 4
Estado_flag: Pendiente de incorporar
aliases:
- 'Lives: 9, Backups: 0'
---

- **Categoría Principal:** [[CTF - Forensics|Web / Forensics]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Ronda:** [[PentraZE CTF 2026 - Ronda 2|Segunda ronda]]
- **Estado:** Completado — 4/4 preguntas

# Writeup - Lives: 9, Backups: 0

> [!info] Objetivo
> Investigar la captura RAM de RootCorp para identificar el malware, su canal y dominio de exfiltración, y recuperar el secreto del Codex.

## Resumen rápido de la cadena de ataque

1. La evidencia contenía una captura de Windows 10 x64, build 19041.
2. Volatility identificó `SvcHost_Kraken.exe` (PID 392), iniciado por PowerShell.
3. Las consultas DNS del volcado del proceso revelaron `exfil.cthulhu.net`.
4. Se reconstruyeron 83 fragmentos Base32: 2,875 bytes no directamente legibles.
5. El documento original seguía en RAM, en el offset `0x2ca110`.
6. El código hexadecimal del Codex fue aceptado: **4/4 preguntas completadas**.

## Vulnerabilidades y hallazgos

- [[Malware|Ransomware]] con extensión `.catlocked`; la interfaz indicaba AES-256-CTR.
- [[DNS]] como canal de exfiltración con datos codificados en subdominios.
- Recuperación de texto claro desde RAM con [[Volatility 3]] y [[Triaje de archivos - file, strings y exiftool|análisis de cadenas]]. No se documenta un descifrado del ransomware.

## Contexto documentado

- **Competencia:** Pentraze CTF
- **Categoría:** Web / Forensics
- **Herramientas:** Fedora Linux, Volatility 3, Python, GNU Strings
- **Estado:** Completado — 4/4 preguntas

## Paso a paso técnico

### 1. Descripción del desafío

La bóveda de RootCorp fue cifrada por un atacante desconocido. No existían respaldos disponibles y la única evidencia recuperada era una captura de memoria RAM.

El objetivo era investigar el incidente y responder cuatro preguntas relacionadas con el malware, la exfiltración y el secreto perdido del Codex.

La interfaz del desafío mostraba varias pistas:

- AES-256-CTR

- DNS EXFIL

- MEM CAPTURED

- Extensión .catlocked

### 2. Preparación del entorno

Descargamos la evidencia evidence.tar.xz, de aproximadamente 931 MB. Al extraerla encontramos codex_acquisition.MEM, una captura de memoria de aproximadamente 6.1 GB.

Configuramos un entorno virtual de Python e instalamos Volatility 3 para examinar la imagen de memoria.

El análisis con windows.info identificó un sistema Windows 10 x64, build 19041.

### 3. Identificación del ejecutable malicioso

Utilizamos los complementos windows.pslist, windows.cmdline y windows.pstree para enumerar los procesos y reconstruir sus relaciones.

Encontramos un proceso sospechoso con PID 392, cuyo ejecutable se encontraba en:

```text
C:\Users\sus\Downloads\SvcHost_Kraken.exe
```

El proceso había sido iniciado desde powershell.exe, con PID 8744.

Primera respuesta: SvcHost_Kraken.exe

La plataforma la aceptó.

### 4. Identificación del canal de exfiltración

La interfaz mostraba la pista DNS EXFIL. Posteriormente encontramos múltiples consultas DNS que contenían información codificada en los nombres de host.

Esto confirmó que el atacante estaba utilizando consultas DNS para transportar información fuera del sistema comprometido.

Segunda respuesta: DNS

La plataforma la aceptó.

### 5. Identificación del dominio malicioso

Realizamos un volcado de la memoria del proceso 392 mediante windows.memmap --pid 392 --dump.

El archivo resultante, pid.392.dmp, permitió buscar cadenas ASCII y UTF-16.

En la memoria encontramos consultas asociadas con dominios como:

- `lunny-webp.exfil.cthulhu.net`

- `svh-webp.exfil.cthulhu.net`

- `sammy-webp.exfil.cthulhu.net`

- `secret-codex-secret.exfil.cthulhu.net`

El dominio común utilizado para la exfiltración era exfil.cthulhu.net.

Tercera respuesta: exfil.cthulhu.net

La plataforma la aceptó.

### 6. Recuperación del secreto del Codex

La última pregunta solicitaba recuperar el secreto perdido en el Codex.

#### Análisis de los datos exfiltrados

Encontramos referencias al archivo C:\Boveda\secret_codex.SECRET, que había sido cifrado como secret_codex.SECRET.catlocked.

Las consultas DNS del archivo seguían el patrón:

```text
<índice>.<datos-base32>.secret-codex-secret.exfil.cthulhu.net
```

Mediante un script de Python identificamos 83 fragmentos numerados consecutivamente, desde el 1 hasta el 83.

Ordenamos los fragmentos y decodificamos sus datos Base32.

Resultado: recuperamos un archivo binario de 2,875 bytes, pero su contenido no era directamente legible.

#### Recuperación del documento en memoria

Continuamos investigando las cadenas almacenadas en pid.392.dmp.

En el desplazamiento hexadecimal 0x2ca110 encontramos parte del documento original en texto claro.

El documento tenía un apartado titulado:

CÓDIGO DE SEGURIDAD — ARMAS SECRETAS DE ROOTCORP

Su contenido explicaba que el código de acceso a las armas secretas había sido almacenado en formato hexadecimal.

El código recuperado fue:

```text
5351554944534152454e4f54544f424554525553544544
```

Al decodificarlo de hexadecimal a ASCII, obtuvimos:

```text
SQUIDSARENOTTOBETRUSTED
```

Sin embargo, la plataforma rechazó inicialmente la cadena ASCII.

Inspeccionamos entonces la respuesta de /api/state, que indicaba que el formato esperado era «Código Secreto».

Volvimos al documento original y utilizamos directamente el código hexadecimal, sin transformarlo.

Cuarta respuesta aceptada:

```text
5351554944534152454e4f54544f424554525553544544
```

### 7. Resumen de respuestas

| Pregunta | Respuesta |
| --- | --- |
| 01. Ejecutable malicioso | SvcHost_Kraken.exe |
| 02. Canal de exfiltración | DNS |
| 03. Dominio malicioso | exfil.cthulhu.net |
| 04. Secreto del Codex | 5351554944534152454e4f54544f424554525553544544 |

### 8. Conclusión

Este desafío demostró la importancia del análisis forense de memoria en investigaciones de ransomware.

Gracias a Volatility 3 y al análisis de cadenas recuperamos evidencia sobre procesos sospechosos, archivos cifrados, dominios de exfiltración y consultas DNS que transportaban información codificada.

El hallazgo decisivo fue encontrar el documento original del Codex todavía presente en la memoria RAM, lo que permitió recuperar su código de seguridad sin necesidad de descifrar el archivo afectado por el ransomware.

También aprendimos una lección importante: una respuesta puede ser técnicamente correcta y aun así ser rechazada si no respeta el formato esperado por el desafío.

Resultado final: 4/4 preguntas completadas.

Flag final: pendiente de incorporar al write-up cuando se copie de la plataforma.


## Flag

**4/4 preguntas completadas y aceptadas.** La flag final está pendiente de incorporar; no se deduce de las cuatro respuestas.

## Lecciones aprendidas y mitigar

- Correlacionar proceso, ruta, padre y memoria evita depender únicamente del nombre del ejecutable.
- Distinguir datos Base32 recuperados, archivo cifrado y texto claro residual; decodificar no equivale a descifrar.
- Conservar el formato original de las respuestas: la representación hexadecimal fue la aceptada.
- Como mitigaciones derivadas del análisis: mantener copias aisladas y restauraciones probadas, supervisar consultas DNS anómalas y restringir la salida DNS a resolutores controlados.
- Preservar memoria y cadena de custodia durante la respuesta al incidente; las medidas defensivas de esta sección son aprendizaje editorial, no acciones ejecutadas en el reto.

## Evidencia y revisión documental

Falta incorporar la flag final desde la evidencia de la resolución. Las cuatro respuestas ya están aceptadas. El Word no adjunta `evidence.tar.xz`, `codex_acquisition.MEM`, `pid.392.dmp` ni el script de reconstrucción Base32; no se han inventado comandos completos de instalación o extracción.

Fuente conservada: [[assets/PentraZE-2026-ronda-2/ctf.docx|ctf.docx original]]. Las descripciones, pruebas, payloads y salidas anteriores proceden de ese documento; no se han reejecutado. Las relaciones y mitigaciones adicionales son síntesis editorial. El Word no contiene imágenes incrustadas.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🏠 MOC: [[PentraZE CTF 2026 - MOC]]
- 🗂️ Ronda: [[PentraZE CTF 2026 - Ronda 2]]
- 🗂️ Categoría: [[CTF - Forensics]]
- ⬅️ Anterior: [[Writeup - La Receta]]
- ➡️ Siguiente: [[Writeup - Nozama Store]]

## Relacionadas

- [[4- Caso Practico, Un hacker entró a mi equipo]] — mismo recorrido Windows: `windows.info`, árbol de procesos, volcado por PID y búsqueda de secretos; aquí se recuperó el documento, no una clave de descifrado.
- [[Writeup - HooKitty]] — reutiliza el conocimiento de nombres DNS, con objetivos distintos: exfiltración en Lives y cambio de destino entre validación y uso en HooKitty.
- [[Identificar codificaciones, cifrados y hashes]] — separar Base32, hexadecimal y cifrado evita interpretar erróneamente los 2,875 bytes.
- [[MOC - Forense Digital end-to-end]] — encaja la investigación en preservación, análisis y presentación de evidencias.
- [[MOC - Python para Ciberseguridad]] — automatización del ordenado y decodificación de fragmentos; el script concreto no está incluido en la fuente.
