# CLAUDE.md — Instrucciones operativas del vault

Este archivo le dice al LLM **cómo operar** sobre el vault `linuxknowledge`.
Para las **convenciones de estructura** (frontmatter, indexes, tipos),
ver `schema.md`. Este archivo cubre las **operaciones**.

## Idioma

Responder siempre en **español**. Comandos, identificadores de código,
nombres de herramientas y flags se dejan en su idioma original.

## Las tres operaciones del patrón Karpathy

### 1. Ingest — Procesar una fuente nueva

Disparador: el usuario aporta una fuente (archivo, URL, idea, transcripción).

Flujo:
1. Leer y discutir takeaways clave con el usuario.
2. Crear o actualizar la(s) nota(s) destino aplicando `schema.md`:
   - Frontmatter YAML completo (`tipo`, `tags`, `actualizado`).
   - H1 derivado del título de la fuente.
   - Cuerpo con la síntesis (no copia literal).
   - Sección `## Navegación` con `⬆️ Carpeta`, `⬅️ Anterior`, `➡️ Siguiente`.
   - Sección `## Relacionadas` con 3+ wikilinks cruzados.
3. Actualizar `_NombreCarpeta.md` del padre añadiendo la nueva entrada.
4. Actualizar cross-references en notas afectadas (puede tocar 10-15 archivos).
5. Apendear al `log.md` una entrada `## [YYYY-MM-DD] ingest | Título`.
6. Actualizar `index.md` añadiendo la nueva nota al catálogo.

### 2. Query — Responder con citas

Disparador: el usuario pregunta algo sobre el vault.

Flujo:
1. Leer `index.md` para identificar páginas relevantes.
2. Drill-down a las páginas: leer contenido completo de las 3-5 más relevantes.
3. Sintetizar respuesta citando `[[Nota]]` siempre que se afirme algo concreto.
4. Si la respuesta es valiosa (análisis nuevo, comparación, conexión),
   **proponer filarla como nota nueva** en el lugar apropiado.
5. Apendear al `log.md` `## [YYYY-MM-DD] query | Pregunta resumida`.

### 3. Lint — Health check periódico

Disparador: el usuario pide auditoría / "revisa el vault".

Buscar y reportar:
- **Wikilinks rotos** — `[[X]]` donde `X` no existe como archivo.
- **Notas huérfanas** — archivos sin backlinks entrantes.
- **Frontmatter inválido** — sin `tipo`, sin cerrar, formato no estándar.
- **Indexes incompletos** — carpetas con descendientes pero sin `_NombreCarpeta.md`.
- **Conceptos mencionados sin nota propia** — wikilinks rotos que merezcan crearse.
- **Contradicciones** — afirmaciones que se invalidan entre notas.
- **Notas obsoletas** — fechas viejas en `actualizado` para temas en evolución.
- **H1 ausente, code blocks sin cerrar, tags inline duplicados al frontmatter.**

Apendear al `log.md` `## [YYYY-MM-DD] lint | Resumen del estado`.

## Autonomía

- **Aplicar el patrón Karpathy sin pedir OK por dominio**: frontmatter,
  Navegación, Relacionadas, cross-references curadas → ejecutar directamente.
- **Pedir confirmación** solo para cambios estructurales mayores: renombrar
  carpetas, mover bloques grandes de archivos, refactor de jerarquía.
- **Cambios destructivos**: nunca borrar contenido del usuario sin
  confirmación explícita. Si una nota parece huérfana, **conectarla**, no
  borrarla.

## Archivos sistema (no tocar la estructura sin permiso)

- `CLAUDE.md` — este archivo (instrucciones operativas).
- `schema.md` — convenciones estructurales (frontmatter, tipos, etc.).
- `log.md` — bitácora cronológica greppable.
- `index.md` — catálogo content-oriented de todas las notas.
- `🔒🐧Hub.md` — nodo central del grafo de Obsidian.
- `README.md` — orientado a GitHub (badges, enlaces externos).
- `CODE_OF_CONDUCT.md` — código de conducta del repo.
- `LICENSE` — MIT.

## Comandos útiles

```powershell
# Últimas 5 entradas del log (greppable)
Select-String "^## \[" log.md | Select-Object -Last 5

# Wikilinks rotos
# (ver script de lint en operaciones)

# Total de wikilinks del vault
(Get-ChildItem -Recurse -Filter *.md | ForEach-Object {
  [regex]::Matches((Get-Content $_.FullName -Raw), '\[\[[^\]]+\]\]').Count
} | Measure-Object -Sum).Sum
```

## Workflow recomendado en sesión

1. **Antes de operar**: leer `log.md` últimas entradas para entender el
   estado reciente del vault.
2. **Durante la sesión**: anunciar la operación (`ingest`, `query`, `lint`)
   antes de empezar.
3. **Después de cada operación significativa**: apendear al `log.md`.
4. **Al cerrar**: confirmar con el usuario que no hay cambios pendientes
   y que el vault queda consistente.
