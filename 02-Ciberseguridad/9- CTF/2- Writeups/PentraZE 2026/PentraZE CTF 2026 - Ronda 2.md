---
tipo: indice
tags: [ctf, pentraze, moc, writeups, ronda-2]
Plataforma: "Pentraze CTF"
Ronda: 2
Estado: "4 flags documentadas; Lives 4/4 preguntas, flag por incorporar"
seccion: 02-Ciberseguridad/9- CTF/2- Writeups/PentraZE 2026
actualizado: 2026-10-18
---

# PentraZE CTF 2026 - Ronda 2

🏠 [[🔒🐧Hub|Hub Principal del vault]]

> [!abstract] Segunda ronda
> Cinco write-ups integrados desde [[assets/PentraZE-2026-ronda-2/ctf.docx|ctf.docx]], siguiendo el formato de la [[PentraZE CTF 2026 - MOC#Primera ronda|primera ronda]]. Cuatro tienen flag documentada; **Lives tiene sus cuatro preguntas completadas** y solo falta copiar la flag final a la documentación.

## Retos por categoría y estado

| Reto | Categoría del documento | Dificultad | Puntos | Estado | Conocimiento central |
|---|---|---|---|---|---|
| [[Writeup - La Receta\|01. La Receta]] | Web | Easy (Fácil) | No documentados | Resuelto; flag documentada | [[SQL Injection]], [[PostgreSQL]], [[Authentication]] |
| [[Writeup - Lives 9, Backups 0\|02. Lives: 9, Backups: 0]] | Web / Forensics | No documentada | No documentados | **4/4 preguntas completadas**; flag por incorporar | [[Volatility 3]], [[DNS]], [[Identificar codificaciones, cifrados y hashes\|Base32 y hexadecimal]] |
| [[Writeup - Nozama Store\|03. Nozama Store]] | Web | Medium | 100 | Resuelto; flag documentada | [[Race Condition]], [[MOC - Python para Ciberseguridad\|Python]], atomicidad |
| [[Writeup - SMBiablo\|04. SMBiablo]] | PWN | No especificada | No documentados | Resuelto; flag documentada | [[Stack Buffer Overflow y ret2libc]], [[9- SMB\|SMB2]], libc |
| [[Writeup - Data Del Más Allá\|05. Data Del Más Allá]] | PWN | No documentada | No documentados | Resuelto; flag documentada | [[Reversing - de leer código fuente a desensamblar binarios\|Ingeniería inversa]], [[WebSocket]], SHA-256/XOR |

**Navegación por categoría:** [[CTF - Web|Web]] · [[CTF - Forensics|Forensics]] · [[CTF - Binary Exploitation|PWN / Binary Exploitation]]. Data conserva la categoría PWN del evento, pero su solución confirmada fue reconstruir autenticación; no se clasifica como explotación de heap demostrada.

## Rutas de aprendizaje entre rondas

- **SQL y permisos:** [[Writeup - Factura Fantasma]] → [[SQL Injection]] → [[Writeup - La Receta]]. Reutilizar descubrimiento de columnas y salida visible; después evaluar qué operaciones autoriza la cuenta SQL.
- **Validar y usar el mismo estado:** [[Writeup - HooKitty]] → [[Race Condition]] → [[Writeup - Nozama Store]]. DNS cambiante y saldo concurrente comparten el riesgo de separar comprobación y uso, aunque el mecanismo concreto difiere.
- **Autenticación y secretos del cliente:** [[Writeup - SoftDat Technology]] → [[Authentication]] → [[Writeup - Data Del Más Allá]]. Comparar un JWT publicado con una clave embebida que permite calcular tokens; La Receta contrasta con ambos al obtener un JWT legítimo tras manipular la base de datos.
- **Mensajes sobre WebSocket:** [[Writeup - Eco Persistente]] → [[WebSocket]] → [[Writeup - Data Del Más Allá]]. Descubrir tipos de mensaje y distinguir sesión establecida de autorización del comando.
- **DNS ofensivo y forense:** [[Writeup - HooKitty]] → [[DNS]] → [[Writeup - Lives 9, Backups 0]]. Cambiar el destino de una petición frente a reconocer información transportada en subdominios.
- **Binarios y memoria:** [[GDB baby step 1]] → [[Reversing - de leer código fuente a desensamblar binarios]] → [[Writeup - SMBiablo]]. Para análisis de RAM, seguir [[4- Caso Practico, Un hacker entró a mi equipo]] → [[Volatility 3]] → Lives; son recorridos distintos que comparten lectura rigurosa de evidencia.
- **XOR y confianza:** [[Writeup - Xouroboros]] y Data permiten comparar keystream reutilizado con ofuscación reversible, sin confundir sus causas raíz.

## Evidencia y revisión pendiente

- **Lives:** copiar la flag final cuando esté disponible; no queda pendiente responder las cuatro preguntas.
- **SMBiablo:** el fragmento Python termina tras recibir la respuesta del leak. La cadena ROP se explica y las salidas constan, pero falta el resto del script original.
- **Data Del Más Allá:** saltos de línea restaurados; el fragmento final carece de imports e inicialización. No se añadió código supuesto.
- **Nozama:** script y registro conservados; los rótulos de salida difieren de algunos `print`, por lo que no se afirma que sean una transcripción exacta de esa versión.
- **Adjuntos:** el Word no contiene imágenes ni los binarios/volcados citados. Se conserva el documento original; los detalles están en [[Informe de integración - PentraZE 2026 Ronda 2]].

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🏠 MOC principal: [[PentraZE CTF 2026 - MOC]]
- ⬅️ Primera ronda: [[PentraZE CTF 2026 - MOC#Primera ronda]]
- ➡️ Primer reto: [[Writeup - La Receta]]

## Relacionadas

- [[_1- Metodologia]] — procedimientos reutilizables.
- [[MOC - Python para Ciberseguridad]] — automatización HTTP, WebSocket y binaria.
- [[MOC - Forense Digital end-to-end]] — contexto de investigación de memoria.
- [[Informe de integración - PentraZE 2026 Ronda 2]] — trazabilidad y validación de la incorporación.
