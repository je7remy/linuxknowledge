---
tipo: indice
seccion: templates
actualizado: 2026-05-30
---

# Templates — Plantillas del vault

🏠 [[🔒🐧Hub|Hub Principal del vault]]

Plantillas para crear notas siguiendo el patrón Karpathy (frontmatter +
Navegación + Relacionadas). Usar con el plugin **Templater** de Obsidian o
copiando manualmente.

## Plantillas disponibles

- [[nota-nueva|Nota nueva (teoria/comando/lab)]] — Plantilla genérica para
  cualquier nota de contenido. Incluye frontmatter completo, secciones
  Concepto + Ejemplo + Notas, Navegación con anterior/siguiente, y 3
  Relacionadas.
- [[indice-carpeta|Índice de carpeta (`_NombreCarpeta.md`)]] — Plantilla
  para crear índices de carpeta que listan contenido + linkean al padre y
  a carpetas hermanas.

## Cómo configurar Templater

1. Instalar plugin **Templater** desde Settings → Community plugins.
2. Settings → Templater → Template folder location: `templates`.
3. Configurar hotkey (ej. `Ctrl+T`) para "Templater: Insert Template".
4. Al crear nota nueva: aplicar plantilla con hotkey.

## Convenciones aplicadas

Todas las plantillas siguen [[schema]]:

- Frontmatter YAML con `tipo`, `tags`, `actualizado`.
- H1 con título legible.
- Secciones de contenido principal.
- Bloque final `---` + `## Navegación` + `## Relacionadas`.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[schema|Schema del vault]] — Define el patrón que estas plantillas
  instancian.
- [[CLAUDE|Instrucciones operativas LLM]] — Workflow de ingest que usa
  estas plantillas.
