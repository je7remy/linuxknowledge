---
tipo: herramienta
tags: [volatility, forense-digital, memoria, windows, dfir]
actualizado: 2026-10-18
---

# Volatility 3

Framework de análisis forense de imágenes de memoria. Permite reconstruir información del sistema, procesos y regiones de memoria usando estructuras del sistema operativo. Analizar un volcado no equivale a ejecutar el malware que dejó sus rastros.

## Flujo Windows aplicado

| Complemento | Pregunta | Evidencia en Lives |
|---|---|---|
| `windows.info` | ¿Qué sistema y arquitectura contiene la captura? | Windows 10 x64, build 19041 |
| `windows.pslist` | ¿Qué procesos figuran en la lista? | PID 392 sospechoso |
| `windows.cmdline` | ¿Con qué ruta/argumentos se ejecutaron? | `C:\Users\sus\Downloads\SvcHost_Kraken.exe` |
| `windows.pstree` | ¿Qué relación padre-hijo hay? | `powershell.exe`, PID 8744, inició el proceso |
| `windows.memmap --pid 392 --dump` | ¿Qué datos conserva la memoria del proceso? | Archivo `pid.392.dmp` para analizar cadenas |

Los nombres y opciones anteriores proceden de [[Writeup - Lives 9, Backups 0|Lives: 9, Backups: 0]]. El documento no conserva la invocación completa ni las versiones precisas del entorno. No se debe convertir esta tabla en una transcripción ficticia de terminal.

## Cadenas, codificaciones y secretos residuales

Buscar ASCII y UTF-16 permitió localizar dominios DNS, referencias a archivos y el documento original en el offset `0x2ca110` de `pid.392.dmp`. Ese desplazamiento pertenece al archivo de volcado: no se afirma que sea una dirección virtual del proceso.

El camino DNS recuperó 83 fragmentos Base32 y 2,875 bytes binarios no legibles. El resultado decisivo vino del texto claro residual. Recuperar el documento no demuestra haber roto AES-256-CTR ni descifrado todos los archivos `.catlocked`.

## Comparación con el caso forense existente

[[4- Caso Practico, Un hacker entró a mi equipo]] ya utiliza información del sistema, árbol de procesos, volcado por PID y búsqueda de cadenas. El método se reutiliza en Lives; cambia el artefacto decisivo: un código del documento frente a la referencia a una clave de cifrado. Los valores específicos y las inconsistencias de aquel caso no se usan para completar evidencia ausente de Lives.

## Preservación y límites

- Conservar la captura original, registrar hashes y analizar una copia.
- Registrar versión, plugins, contexto del PID y offsets; distinguir observación de hipótesis.
- Correlacionar ruta, padre y comportamiento; un nombre de proceso por sí solo no confirma malware.
- El archivo Word es la fuente de la integración. No contiene la imagen de 6.1 GB ni salidas completas de cada plugin.

## Navegación

- ⬆️ Carpeta: [[_6- Forense Digital]]
- 🏠 [[MOC - Forense Digital end-to-end]]

## Relacionadas

- [[Writeup - Lives 9, Backups 0]] — cuatro respuestas aceptadas y flag documental pendiente.
- [[Triaje de archivos - file, strings y exiftool]] — extracción de texto como apoyo al análisis estructurado.
- [[DNS]] — reconocer un canal de exfiltración en nombres consultados.
- [[Identificar codificaciones, cifrados y hashes]] — Base32 y hexadecimal frente a cifrado.
