---
tipo: referencia
tags: [git, github, sync, workspace, deployment]
actualizado: 2026-05-31
---

# 00 — Git & Sync Guide

🏠 [[🔒🐧Hub|Hub Principal]]

Cómo subir tu vault a GitHub manteniendo **idéntico el estado del
dashboard** entre máquinas. Cubre: workspace persistente, `.gitignore`
inteligente, sincronización segura.

## El problema que resuelve

Cuando trabajas con Obsidian + Git:

- Si subes **todo** `.obsidian/` → cada apertura modifica `workspace.json`
  (scroll, tab activo, sidebar redimensionada) → commits sucios constantes.
- Si NO subes `.obsidian/` → en otra máquina pierdes plugins, snippets,
  themes y configuración. Dashboard se rompe.

**Solución**: subir la **CONFIG estable** (plugins activos, snippets,
themes, hotkeys, workspaces guardados) y excluir el **ESTADO VOLÁTIL**
(`workspace.json`, caches, backups).

---

## Parte 1 — Guardar el workspace "Dashboard"

⚠️ **Esto DEBE hacerse desde la UI de Obsidian**, no editando JSON
directamente. Los plugins sobrescriben el JSON al cerrar Obsidian.

### Con plugin Workspaces Plus (recomendado, ya instalado)

1. Asegúrate de tener el layout que quieres:
   - **Hub** abierto en el panel central (pinned).
   - **Sidebars** abiertas o colapsadas según prefieras.
   - Todo lo demás cerrado.

2. **Click en el icono de ribbon "Manage workspaces"** (Workspaces Plus
   añade un icono a la barra lateral izquierda).
   - Alternativa: `Ctrl+P` → `Workspaces Plus: Open workspace switcher`.

3. **Save current as new workspace**.

4. **Nombre**: `Dashboard`.

5. Confirmar.

### Con plugin Workspaces nativo (alternativa)

1. `Settings` → `Core plugins` → habilitar **Workspaces** si no está.
2. `Ctrl+P` → `Workspaces: Save layout`.
3. Nombre: `Dashboard`.

### Verificación

Tras guardar, el archivo `.obsidian/workspaces.json` tendrá el workspace
`Dashboard` con todo el layout serializado. Ese archivo SÍ se sube a Git.

---

## Parte 2 — Configurar Homepage para abrir el workspace

Cambia el plugin Homepage de **archivo** a **workspace**:

1. `Settings` → `Community plugins` → **Homepage** (engranaje).
2. Cambiar:
   - **Type**: de `File` a **`Workspace`**.
   - **Value**: seleccionar **`Dashboard`** del dropdown.
3. Mantener:
   - **Open on startup**: ☑
   - **Refresh Dataview**: ☑
   - **Pin**: ☑

Resultado: al abrir Obsidian, carga el workspace completo con el Hub +
sidebars + todo el layout guardado.

---

## Parte 3 — `.gitignore`

El vault ya tiene `.gitignore` configurado en la raíz. Lo que excluye:

| Excluido | Por qué |
|---|---|
| `.obsidian/workspace.json` | Cambia con cada acción (scroll, tabs) |
| `.obsidian/workspace-mobile.json` | Estado mobile temporal |
| `.obsidian/plugins/*/cache/` | Caches regenerables |
| `.obsidian/plugins/beautitab/data.json` | Tiene wallpapers en base64, archivo enorme |
| `.obsidian/plugins/rss-dashboard/data.json` | Feeds descargados, no la config |
| `.rss-dashboard-data/` | Storage interno del plugin RSS |
| `*.tmp`, `*.bak`, `*.swp` | Temporales |
| `Thumbs.db`, `.DS_Store` | OS basura |
| `node_modules/` | Flowershow plugin |

Lo que **SÍ** se sube (overrides explícitos):

| Incluido | Por qué |
|---|---|
| `.obsidian/app.json` | Settings generales |
| `.obsidian/appearance.json` | Tema + CSS snippets activos |
| `.obsidian/community-plugins.json` | Lista de plugins activos |
| `.obsidian/core-plugins.json` | Core plugins activos |
| `.obsidian/hotkeys.json` | Tus atajos custom |
| `.obsidian/graph.json` | Config del graph view |
| `.obsidian/workspaces.json` | **Tus workspaces guardados** ← clave |
| `.obsidian/snippets/*.css` | dashboard.css, Colored Sidebar Items |
| `.obsidian/themes/**` | GitHub Theme, Hackthebox |
| `.obsidian/plugins/*/manifest.json` | Versión de cada plugin |
| `.obsidian/plugins/*/data.json` | Config de cada plugin (excepto los excluidos) |
| `.obsidian/plugins/rss-dashboard/feeds.opml` | Lista de feeds RSS |

---

## Parte 4 — Inicializar Git y subir a GitHub

### A. Si NO tienes git inicializado

```powershell
cd C:\linuxknowledge

# Inicializar repo
git init
git branch -M main

# Stage + commit inicial
git add .
git commit -m "Initial commit: vault con dashboard premium + PARA + RSS"

# Conectar al repo en GitHub
git remote add origin https://github.com/je7remy/linuxknowledge.git
git push -u origin main
```

### B. Si YA tienes git en otra máquina (sincronizar)

```powershell
cd C:\linuxknowledge

# Pull cambios recientes
git pull origin main

# Subir tus cambios
git add .
git commit -m "Actualización: <descripción>"
git push
```

### C. Clonar el vault en otra máquina (estado idéntico)

```bash
git clone https://github.com/je7remy/linuxknowledge.git
cd linuxknowledge
```

Abre la carpeta como vault en Obsidian (`Open folder as vault`). El
dashboard se cargará idéntico porque:

1. Plugin Homepage abrirá el workspace `Dashboard` guardado.
2. Snippets CSS activos (Workspaces Plus los preserva).
3. Plugins habilitados en `community-plugins.json`.
4. RSS feeds en `feeds.opml` listos para importar.

---

## Parte 5 — Workflow recomendado de commits

### Commits frecuentes (recomendado)

```powershell
# Antes de empezar a trabajar
git pull

# Después de una sesión de notas
git add .
git commit -m "ingest: <título corto>"
git push
```

### Tipos de commit (alineados con CLAUDE.md operations)

| Prefix | Cuándo |
|---|---|
| `ingest:` | Nueva fuente procesada (curso, libro, video) |
| `lint:` | Limpieza, fixes, audit |
| `refactor:` | Reorganización estructural |
| `setup:` | Configuración inicial o nuevos plugins |
| `query:` | Pregunta respondida que generó nota nueva |
| `docs:` | Cambios solo a documentación |

Ejemplo:
```
git commit -m "ingest: Curso CompTIA Security+ módulo 3 (network security)"
git commit -m "lint: bugfix wikilinks rotos + actualización glosario"
git commit -m "refactor: mover MOCs a _Vista Curada"
```

---

## Parte 6 — Recuperarse de un workspace roto

Si al abrir Obsidian el dashboard NO se carga (ves un panel vacío o
beautitab):

### Opción A — Restaurar workspace Dashboard

1. `Ctrl+P` → `Workspaces Plus: Load workspace`.
2. Seleccionar **`Dashboard`**.

### Opción B — Forzar via plugin Homepage

1. `Settings` → `Homepage` → confirmar que `Value: Dashboard` (no
   `Bienvenida` u otro).
2. `Ctrl+P` → `Homepage: Open homepage`.

### Opción C — Reset desde Git

Si todo está perdido:

```powershell
cd C:\linuxknowledge
git checkout .obsidian/workspaces.json
git checkout .obsidian/appearance.json
git checkout .obsidian/community-plugins.json
# Reinicia Obsidian
```

---

## Parte 7 — Cosas que NO subir (incluso si estuviera en .gitignore)

Pensar antes de cada commit:

| ❌ NO subir | Por qué |
|---|---|
| Credenciales reales | API keys, passwords, .env real |
| Datos personales sensibles | Documentos privados que escaneaste |
| Capturas con info privada | Screenshots con datos de cuentas |
| Notas marcadas privadas | `*.private.md` (filtrado en `.gitignore`) |

⚠️ Si accidentalmente subiste un secret:
1. **Asume comprometido** y rota credenciales inmediatamente.
2. Limpia git history: `git filter-repo` o BFG Repo-Cleaner.
3. Force push (peligroso, mejor crear repo nuevo).

---

## Troubleshooting

| Síntoma | Causa | Solución |
|---|---|---|
| Workspace `Dashboard` no aparece tras clonar | Plugin Workspaces Plus no activado en máquina nueva | `Settings → Community plugins → Workspaces Plus → Enable` |
| Dashboard se ve sin CSS al clonar | Snippet `dashboard` no activado | `Settings → Appearance → CSS snippets → dashboard ON` |
| Plugins no funcionan tras clonar | Plugins no descargados (manifest sí, código no) | `Settings → Community plugins → Browse` y reinstalar plugins listados en `community-plugins.json` |
| Dataview queries en blanco | JS no habilitado | `Settings → Dataview → Enable JavaScript Queries` |
| Commits gigantes (>50MB) | `beautitab/data.json` con wallpapers | Verificar que está en `.gitignore` (debe estarlo) |
| `git push` rechazado por tamaño | Hay un archivo grande | `git filter-repo --strip-blobs-bigger-than 50M` |

---

## Resumen ejecutivo

Para que el dashboard se vea igual en cualquier máquina al clonar:

1. ✅ **Workspace `Dashboard` guardado** (desde UI de Workspaces Plus, no JSON).
2. ✅ **Homepage configurado a `Workspace: Dashboard`** (no archivo).
3. ✅ **`.gitignore` configurado** (este archivo en raíz del vault).
4. ✅ **`git push`** con la config estable.
5. ✅ En otra máquina: **`git clone`** + abrir como vault + reinstalar plugins desde lista.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[00 - Dashboard Guide]] — guía del dashboard
- [[📡 RSS Feeds]] — feeds curados
- [[index|Catálogo del vault]]

## Relacionadas

- [[CLAUDE]] — instrucciones operativas LLM.
- [[schema]] — convenciones del vault.
- [[log]] — bitácora de cambios.
