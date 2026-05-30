---
tipo: schema
actualizado: 2026-05-30
---

# Schema del Vault — linuxknowledge

Convenciones que rigen la estructura, nombrado y enlazado de este vault.
Cualquier nota nueva (o LLM operando sobre el vault) debe respetarlas.

## 1. Organización jerárquica

El vault se divide en **7 secciones de nivel raíz**, numeradas con dos dígitos:

| Prefijo | Sección | Dominio |
|--------|---------|---------|
| `01-` | Sistemas-Operativos | Linux, Windows, administración |
| `02-` | Ciberseguridad | Pentesting, OSINT, forense, cripto |
| `03-` | Desarrollo | BBDD, tesis, proyecto web |
| `04-` | Laboratorios | Ejercicios prácticos por lenguaje/herramienta |
| `05-` | Recursos | Guías rápidas, glosarios, cheatsheets |
| `06-` | Publicaciones-Linkedin | Posts redactados para publicar |
| `07-` | Inteligencia-Artificial | Cursos y técnicas de IA |

Dentro de cada sección, las subcarpetas usan prefijo **`N-`** (un dígito)
para indicar orden de lectura sugerido. Ejemplo: `1- Cracking`, `2- Extraer Metadatos`.

Los archivos dentro de una carpeta también pueden numerarse `N- Título.md`
cuando el orden importa (cursos secuenciales). Para notas de referencia
no secuenciales, no usar prefijo numérico.

## 2. Idioma y tono

- **Español neutro** en cuerpo y encabezados.
- Comandos, flags, identificadores de código, nombres de herramientas: en su idioma original.
- Tono didáctico, primera persona ocasional, sin floritura.

## 3. Tipos de nota

Cada nota cae en uno de estos tipos. Frontmatter `tipo:` obligatorio.

**Tipos de contenido:**

- **`teoria`** — concepto, definición, marco conceptual (mayoría de notas).
- **`cheatsheet`** / **`comando`** — referencia rápida de sintaxis.
- **`laboratorio`** — ejercicio práctico con pasos reproducibles.
- **`herramienta`** — descripción de una utilidad (nmap, wireshark, etc).
- **`publicacion`** — post de LinkedIn u otra red.
- **`tesis`** — documentos del proyecto académico (propuesta, anteproyecto, etc).
- **`referencia`** — guías rápidas externas, documentación de terceros.

**Tipos estructurales (solo archivos sistema):**

- **`indice`** — archivo índice `_NombreCarpeta.md` de una carpeta.
- **`hub`** — único archivo `🔒🐧Hub.md` (entrada principal del vault).
- **`schema`** — único archivo `schema.md` (este documento).
- **`log`** — único archivo `log.md` (bitácora cronológica).

## 4. Cross-references (lo más importante)

Usar **enlaces internos de Obsidian** `[[Nombre de la nota]]` siempre que
se mencione un concepto que tiene (o debería tener) su propia nota.

Reglas:
- Una nota nueva debería tener al menos **3 enlaces salientes** salvo que sea
  un cheatsheet puro.
- Si mencionas una herramienta (`nmap`, `hashcat`), enlaza a su nota principal.
- Si una nota referenciada todavía no existe, deja el `[[...]]` igualmente:
  Obsidian lo marca como pendiente y eso es señal de qué falta escribir.

## 5. Frontmatter mínimo (obligatorio)

```yaml
---
tipo: teoria | cheatsheet | laboratorio | herramienta | publicacion | tesis | referencia
tags: [..., linux, redes]
actualizado: YYYY-MM-DD
---
```

Para índices (`_*.md`) usar `tipo: indice` y añadir `seccion: ruta/carpeta`.

## 6. Índices por carpeta (`_NombreCarpeta.md`)

Cada carpeta con descendientes contiene un archivo índice `_NombreCarpeta.md`
(prefijo `_` + nombre de la carpeta padre, único en todo el vault). Razón:
con múltiples `index.md` Obsidian no resuelve wikilinks sin path explícito.

El índice debe:
- Describir en 2-3 líneas el dominio de la carpeta.
- Listar los archivos hijos con enlaces `[[...]]` y una línea de descripción.
- Enlazar a carpetas hermanas relacionadas en una sección **Relacionadas**.
- Tener `🏠 [[🔒🐧Hub|Hub Principal del vault]]` después del título H1.
- Tener una sección **Navegación** con `⬆️ Carpeta padre: [[_X|nombre]]`.

## 7. Bitácora (`log.md`)

`log.md` en la raíz registra **cambios significativos** del vault en orden
cronológico inverso. No reemplaza a git; sirve para responder "¿qué hay de nuevo?"
sin revisar commits.

Formato de entrada:
```
## YYYY-MM-DD — Título corto
Descripción breve. Enlaces a [[notas afectadas]].
```

## 8. Lo que NO va en el vault

- Credenciales, claves, tokens.
- Información personal identificable de terceros.
- Material con licencia restrictiva sin atribución clara.
