---
tipo: referencia
tags: [dashboard, instalacion, plugins, homepage, para]
actualizado: 2026-05-30
---

# 00 — Dashboard Guide

🏠 [[🔒🐧Hub|Hub Principal]]

Guía completa del **Command Center** del vault. Cubre instalación de
plugins, configuración del **plugin Homepage**, estructura PARA y
operación diaria.

> **Filosofía**: el plugin Homepage abre el archivo Hub como punto de
> entrada. El archivo Hub es un **dashboard real con widgets dinámicos**
> (calendario, tasks, stats, projects, year tracker), no una nota
> decorada. Los datos se calculan en vivo con Dataview.

---

## A. Plugins necesarios

### Esenciales (obligatorios)

| # | Plugin | Función | Estado |
|---|---|---|---|
| 1 | **Dataview** (`dataview`) | Queries dinámicas: tasks, projects, stats, heatmap, calendar — todo el contenido vivo del dashboard | ✅ instalado |
| 2 | **Homepage** (`homepage`) | Abre el archivo Hub al iniciar Obsidian. Maneja view, refresh de Dataview, pin de tab | ✅ instalado |
| 3 | **Templater** (`templater-obsidian`) | Plantillas con `{{date}}`, `{{title}}` para daily notes, projects, areas | ✅ instalado |

### Recomendados (para sidebars y workflow PARA)

| # | Plugin | Función | Recomendación |
|---|---|---|---|
| 4 | **Calendar** (Liam Cain) | Sidebar izq con calendario mensual nativo. Click en día abre/crea daily note. Complementa el calendar widget del Hub | ⏳ instalar |
| 5 | **Periodic Notes** (Liam Cain) | Auto-crear daily/weekly/monthly notes con plantilla específica | ⏳ instalar |
| 6 | **Tasks** (Martin Schenck, `obsidian-tasks-plugin`) | Sidebar der con todas las tasks pendientes del vault. Permite due dates, recurrence, priorities | ⏳ instalar |

### Opcionales (mejoran experiencia)

| Plugin | Función |
|---|---|
| **Style Settings** | UI gráfica para cambiar variables CSS del dashboard sin tocar archivos |
| **Iconize** | Iconos custom en file explorer (los emoji prefix ya funcionan) |
| **Workspaces Plus** | Guardar layouts (sidebars abiertas, plugins activos) ✅ ya instalado |
| **Heatmap Tracker** (Maksim Rubanau) | Heatmap alternativo si quieres feature parity con el clásico | ✅ ya instalado (no se usa, el dashboard tiene heatmap custom) |
| **Beautitab** | Nueva pestaña personalizada (Ctrl+T) ✅ ya instalado |

### Orden recomendado de instalación

1. **Dataview** primero → habilita los widgets del Hub.
2. **Homepage** → conecta el Hub como punto de entrada.
3. **Templater** → permite plantillas dinámicas.
4. **Calendar** + **Periodic Notes** → sidebar izq + daily notes auto.
5. **Tasks** → sidebar der con tasks management.

---

## B. Arquitectura del vault

```
linuxknowledge/
│
├── 🏠 SISTEMA (archivos raíz)
│   ├── 🔒🐧Hub.md                ← ⭐ Dashboard (Homepage apunta aquí)
│   ├── index.md                  ← Catálogo content-oriented
│   ├── schema.md                 ← Convenciones del vault
│   ├── log.md                    ← Bitácora cronológica
│   ├── CLAUDE.md                 ← Instrucciones LLM
│   ├── _roadmap.md               ← Pendientes
│   ├── 00 - Dashboard Guide.md   ← Esta guía
│   ├── 📋 All Tasks.md           ← Vista global de tasks
│   ├── README.md                 ← README de GitHub
│   ├── CODE_OF_CONDUCT.md
│   └── LICENSE
│
├── 📥 Inbox/                     ← Capture rápido (PARA)
├── 📅 Daily Notes/               ← Daily notes YYYY-MM-DD (PARA)
├── 🚀 Projects/                  ← Proyectos activos con deadline (PARA)
├── 🎯 Areas/                     ← Responsabilidades continuas (PARA)
├── 🗄️ Archives/                  ← Proyectos completados (PARA)
│
├── 01-Sistemas-Operativos/       ← Sección temática (no se toca)
├── 02-Ciberseguridad/            ← Sección temática (no se toca)
├── 03-Desarrollo/                ← Sección temática (no se toca)
├── 04-Laboratorios/              ← Sección temática (no se toca)
├── 05-Recursos/                  ← Tu "R" del PARA (existente)
├── 06-Publicaciones-Linkedin/    ← Sección temática (no se toca)
├── 07- Inteligencia-Artificial/  ← Sección temática (no se toca)
│
├── _Vista Curada/                ← MOCs, entity pages, síntesis
│
├── templates/                    ← Plantillas Templater
│   ├── daily-note.md
│   ├── project.md
│   ├── area.md
│   ├── inbox-item.md
│   ├── nota-nueva.md
│   └── indice-carpeta.md
│
├── assets/                       ← Imágenes / SVG hero
│   └── wallpaper.svg
│
└── .obsidian/
    └── snippets/
        └── dashboard.css         ← Estilos del dashboard
```

---

## C. Configuración paso a paso

### Paso 1 — Verificar Dataview

`Settings` → `Community plugins` → engranaje ⚙️ de **Dataview**:

| Setting | Valor obligatorio |
|---|---|
| Enable JavaScript Queries | ☑ ON |
| Enable Inline JavaScript Queries | ☑ ON |
| Enable Inline Queries | ☑ ON |
| Show null values inline | ☐ OFF (estético) |

**Sin esto los widgets del Hub no se renderizan.**

### Paso 2 — Configurar Homepage Plugin (el corazón)

`Settings` → `Community plugins` → engranaje ⚙️ de **Homepage**:

| Campo | Valor | Por qué |
|---|---|---|
| **Homepage Type** | File | abrir un archivo (no workspace) |
| **Homepage Value** | `🔒🐧Hub` | nombre exacto del archivo (sin `.md`) |
| **Open on startup** | ☑ ON | abre al iniciar Obsidian |
| **Open mode** | Replace all open notes | dashboard limpio en cada inicio |
| **Manual open mode** | Keep open notes | si lo abres manual, conserva tabs |
| **Default view** | **Reading view** | OBLIGATORIO para dataviewjs |
| **Revert view** | ☑ ON | vuelve siempre a Reading view |
| **Open when empty** | ☑ ON | si todo está vacío, abre el dashboard |
| **Refresh Dataview** | ☑ ON | refresca queries al abrir |
| **Pin** | ☑ ON | la tab del dashboard no se cierra accidentalmente |
| **Hide release notes** | ☑ ON | sin pop-ups del plugin |

Esto YA está en `.obsidian/plugins/homepage/data.json`. Verificar:

```json
{
  "homepages": {
    "Main Homepage": {
      "value": "🔒🐧Hub",
      "kind": "File",
      "openOnStartup": true,
      "view": "Reading view",
      "refreshDataview": true,
      "pin": true,
      ...
    }
  }
}
```

### Paso 3 — Activar CSS snippet

`Settings` → `Appearance` → scroll a **CSS snippets** → click 🔄
(refresh) → toggle ON al lado de **`dashboard`**.

Sin esto el Hub se ve sin estilos.

### Paso 4 — Configurar Templater

`Settings` → `Community plugins` → engranaje ⚙️ de **Templater**:

| Campo | Valor |
|---|---|
| Template folder location | **`templates`** |
| Trigger Templater on new file creation | ☑ ON (opcional) |

Configurar hotkey: `Settings` → `Hotkeys` → buscar **"Templater: Open
insert template modal"** → asignar `Ctrl+T` (o el que prefieras).

### Paso 5 — Instalar y configurar Calendar plugin (sidebar izq)

1. `Settings` → `Community plugins` → `Browse` → **Calendar** (Liam Cain) → Install + Enable.
2. `Settings` → `Calendar`:

| Campo | Valor |
|---|---|
| Start week on | Monday |
| Confirm before creating new note | OFF |
| Show week number | OFF (opcional) |
| Localization | Español |

3. Abrir sidebar izq → tab Calendar (icono ⊞).

### Paso 6 — Configurar Periodic Notes

1. Install + Enable plugin **Periodic Notes**.
2. `Settings` → `Periodic Notes`:

| Campo | Valor |
|---|---|
| Daily Notes — Enable | ☑ ON |
| Date format | **`YYYY-MM-DD`** |
| New file location | **`📅 Daily Notes`** |
| Template file location | **`templates/daily-note`** |

### Paso 7 — Instalar Tasks plugin (sidebar der)

1. Install + Enable plugin **Tasks** (Martin Schenck).
2. `Settings` → `Tasks`:
   - ☑ Set done date on every completed task.
   - ☑ Auto-suggest task data when typing.
3. Sidebar der → buscar tab Tasks (icono ✓).

### Paso 8 — Cerrar y reabrir Obsidian

Al reabrir, debes ver el dashboard del Hub directamente.

### Paso 9 — Guardar workspace (opcional pero recomendado)

`Settings` → `Workspaces` (core plugin):

1. Abrir sidebars izq + der como las quieras.
2. `Workspaces` → `Save as...` → nombre: **`Dashboard`**.

Para que abra ese workspace al iniciar (en lugar del archivo), cambiar
Homepage:
- `kind: "Workspace"`
- `value: "Dashboard"`

---

## D. Componentes del dashboard (qué hay en el Hub)

```
┌─────────────────────────────────────────────────────────────┐
│  HERO (320px alto)                                          │
│  ┌ greeting + fecha + hora (top)                            │
│  │ "linuxknowledge" gradient title                          │
│  └ subtítulo (bottom)                                       │
├─────────────────────────────────────────────────────────────┤
│  QUICK ACCESS · 9 cards en grid 3x3 (escala según width)    │
│  📥 Inbox  📅 Daily Notes  🚀 Projects  📋 All Tasks  ...   │
├─────────────────────────────────────────────────────────────┤
│  BENTO GRID · 2 columnas                                    │
│  ┌─ Calendario mensual ──┐  ┌─ Sidebar widgets ──┐         │
│  │  [día actual gradient]│  │  ✅ Daily Tasks      │         │
│  │  [dots verdes]        │  │  📊 Quick Stats      │         │
│  │  [click → daily note] │  │  🚀 Active Projects  │         │
│  └───────────────────────┘  └──────────────────────┘         │
├─────────────────────────────────────────────────────────────┤
│  YEAR TRACKER (full width) — heatmap GitHub-style           │
├─────────────────────────────────────────────────────────────┤
│  FOOTER · 📚 Index  📜 Schema  🤖 CLAUDE  📝 Log  🗺️ Roadmap │
└─────────────────────────────────────────────────────────────┘
```

### Widgets en detalle

**Hero**:
- Saludo dinámico (Buenos días/tardes/noches según hora).
- Fecha completa + hora actual con `moment.js`.
- Título "linuxknowledge" con gradient text (blanco → cyan → púrpura).
- Subtítulo descriptivo.
- SVG paisaje japonés de fondo (templo + luna + montañas).

**Quick Access (9 cards)**:
1. 📥 Inbox
2. 📅 Daily Notes
3. 🚀 Projects
4. 📋 All Tasks
5. 📚 Knowledge Base
6. 🎯 Areas
7. 💎 Resources
8. 🗄️ Archives
9. 🧭 MOCs

Cards con hover translateY -3px + glow cyan + barra superior animada.

**Calendar widget**:
- Mes actual completo.
- Pill con fecha de hoy (gradient cyan→púrpura).
- Día actual con scale 1.05 + gradient.
- Dots verdes en días con actividad.
- Outline cyan en días con daily note.
- Click en cualquier día → abre/crea daily note de ese día.

**Daily Tasks**:
- Top 6 tasks pendientes globales del vault.
- Renderizadas con `dv.taskList` → soportan checkboxes editables.
- Border-left amber pendientes, verde completadas.

**Quick Stats** (6 contadores):
- Hoy + (notas creadas hoy).
- Modificadas (notas tocadas hoy).
- ✓ hoy (tasks completadas).
- Proj (proyectos activos).
- Total (notas en el vault).
- Streak 🔥 (días consecutivos con actividad).

**Active Projects**:
- Top 3 proyectos activos sorted por deadline.
- Cada uno con: nombre, deadline, estado, progress bar gradient cyan→púrpura.

**Year Tracker**:
- 53 semanas × 7 días = 371 cells.
- Paleta GitHub clásica (gris vacío → 4 niveles de verde).
- Día actual con outline blanco.
- Hover scale 1.5 + tooltip nativo `fecha — N nota(s)`.
- Leyenda inferior con stats: días activos · total notas · pico/día.

**Footer**:
- Links monospace a archivos sistema: index, schema, CLAUDE, log, roadmap, guide.

---

## E. Operación diaria (workflow PARA)

### Mañana (3-5 min)

1. Abrir Obsidian → **Hub** aparece centrado.
2. Mirar **Quick Stats** → ver estado del día.
3. Click en el día actual del **Calendar widget** → crea/abre daily note.
4. Anotar **Top 3 prioridades** en la daily note (plantilla).
5. Revisar **Daily Tasks** widget para contexto.

### Durante el día (capture rápido)

- Idea suelta → `Ctrl+T` → plantilla `inbox-item` → guardar en `📥 Inbox/`.
- Tarea concreta → añadir `- [ ] descripción 📅 2026-MM-DD` en daily note.
- Trabajo en proyecto → abrir desde **Active Projects** del Hub.

### Noche (5 min)

1. Volver al Hub (Ctrl+E → vuelve al pin).
2. **Quick Stats** muestra: creadas, modificadas, tasks ✓.
3. Reflexión en daily note (al pie de la plantilla).
4. Procesar Inbox si tienes items > 2 días.

### Semanal (15-30 min)

1. **Inbox a cero**: clasificar items a Projects/Areas/Resources/Trash.
2. **Revisar Projects**: actualizar `progreso` y `estado` en frontmatter.
3. **Revisar Areas**: revisión semanal de cada área.
4. **Archivar** proyectos completados → mover a `🗄️ Archives/`.

---

## F. Automatizaciones avanzadas (opcional)

### Resumen semanal automático

Crear nota `Weekly Review YYYY-Www.md` con plantilla que use dataviewjs:

```dataviewjs
const start = moment().startOf('week');
const end = moment().endOf('week');
const week = dv.pages().where(p => p.file.mtime >= start && p.file.mtime <= end);

dv.header(3, "Notas tocadas esta semana: " + week.length);
dv.table(["Día", "Notas"], 
  [...Array(7)].map((_, i) => {
    const day = start.clone().add(i, 'days');
    const dayNotes = week.where(p => p.file.mtime.toFormat("yyyy-MM-dd") === day.format("YYYY-MM-DD"));
    return [day.format("ddd D MMM"), dayNotes.length];
  })
);
```

### Días sin actividad alert

En el Hub, añadir card que avise si lleva >2 días sin escribir:

```dataviewjs
const today = moment();
const byDate = {};
for (const p of dv.pages('-"templates"').values) {
  if (p.file.mtime) byDate[p.file.mtime.toFormat("yyyy-MM-dd")] = true;
}
let daysWithoutActivity = 0;
for (let i = 1; i < 30; i++) {
  const d = today.clone().subtract(i, 'days').format("YYYY-MM-DD");
  if (!byDate[d]) daysWithoutActivity++;
  else break;
}
if (daysWithoutActivity >= 2) {
  dv.paragraph(`⚠️ **${daysWithoutActivity} días** sin escribir en el vault. ¿Crear daily note?`);
}
```

### KPI personal (productividad)

Stats avanzadas: ratio notas creadas/semana, % objetivos completados,
días streak récord. Implementable con queries similares.

### Integración con Tasks plugin

Una vez instalado el plugin Tasks, reemplazar el dataviewjs simple por:

````markdown
```tasks
not done
limit 6
sort by priority
```
````

Esto da filtros más potentes (priority, due, recurrence, tags).

### Progress bars con frontmatter

Para projects, definir `progreso: 0-100` en frontmatter y el dashboard
lo renderiza automáticamente. Ya implementado en el widget Active Projects.

---

## G. Troubleshooting

| Síntoma | Causa | Solución |
|---|---|---|
| Hub se abre sin estilos | CSS snippet OFF | Settings → Appearance → CSS snippets → toggle `dashboard` |
| `Evaluation Error` en widgets | Dataview JS OFF | Settings → Dataview → Enable JavaScript Queries |
| Hub no abre al iniciar | Homepage mal configurado | Verificar `value: 🔒🐧Hub`, `kind: File`, `openOnStartup: true` |
| Calendar widget muestra bloques de código | View es Source/Live | Forzar Reading view en Homepage |
| Tasks widget vacío | Vault sin tasks `- [ ]` | Crear daily note con tasks |
| Active Projects vacío | Sin proyectos en `🚀 Projects/` | Crear uno con plantilla [[project]] |
| Stats: indexes muestra 0 | Bug viejo de query | Ya arreglado (usar `p.tipo` no `#tipo/indice`) |
| SVG hero no carga | Path incorrecto | Verificar `assets/wallpaper.svg` existe |
| Heatmap dice "max=NaN" | Vault sin actividad histórica | Normal, se llena con el uso |

---

## H. Personalización

### Cambiar paleta global

Editar `.obsidian/snippets/dashboard.css`, sección `:root` tokens:

```css
.dashboard-home {
  --accent-cyan: #7fd1ff;     /* color principal */
  --accent-purple: #b88dff;   /* color secundario */
  --bg-0: #0a0e1a;            /* fondo más oscuro */
  /* ... */
}
```

### Cambiar paleta del heatmap

En `🔒🐧Hub.md`, dentro del Year Tracker dataviewjs:

```js
const colors = ["#161b22", "#0e4429", "#006d32", "#26a641", "#39d353"];
// GitHub clásico (default)

// Alternativas:
// Verde mejorado: ["#1e2530", "#0e4429", "#006d32", "#26a641", "#39d353"]
// Verde + rojo:   ["#2a2a3a", "#5a2030", "#a83838", "#3a8a3a", "#3ad05a"]
// Azul:           ["#161b22", "#1e3a5f", "#2563eb", "#3b82f6", "#7fd1ff"]
// Púrpura:        ["#1a1a3e", "#3d2a6e", "#6a4a9e", "#9d6ef0", "#b88dff"]
```

### Quitar widgets

En `🔒🐧Hub.md`, comentar el bloque del widget que no quieras:

```html
<!-- <div class="bento-card bento-stats">...</div> -->
```

### Cambiar quick access cards

Editar lista bajo `## Quick Access` en el Hub.

### Tu propia imagen hero

Reemplazar `assets/wallpaper.svg` con tu imagen y actualizar la línea en el Hub:

```html
<img src="assets/wallpaper.jpg" alt="hero" class="dashboard-hero-img" />
```

---

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[index|Catálogo del vault]]
- [[schema|Schema]]
- [[CLAUDE|Instrucciones LLM]]

## Relacionadas

- [[_roadmap|Roadmap]] — pendientes del vault.
- [[_templates|templates/]] — todas las plantillas.
- [[log|Bitácora]] — historial cronológico.
