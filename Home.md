---
tipo: hub
tags: [home, dashboard, vault-entrada]
actualizado: 2026-05-30
cssclasses:
  - dashboard-home
---

# 🔒🐧 linuxknowledge — Dashboard

<div class="dashboard-quote">

> _"El conocimiento es libre, compártelo responsablemente"_ — je7remy

</div>

## ⚡ Atajos rápidos

<div class="dashboard-shortcuts">

- 🏠 [[🔒🐧Hub|Hub Principal]]
- 📇 [[index|Catálogo del vault]]
- 🗺️ [[_roadmap|Roadmap — pendientes]]
- 📝 [[log|Bitácora]]
- 📜 [[schema|Schema]] · [[CLAUDE|Instrucciones LLM]]

</div>

## 🎯 MOCs / Entity pages

<div class="dashboard-shortcuts">

- 🧭 [[MOC - Camino al eJPTv2]]
- 🛡️ [[MOC - Pentesting end-to-end]]
- 🐍 [[MOC - Python para Ciberseguridad]]
- 🎯 [[Pentesting]] · [[OSINT]] · [[Hacking Etico]]

</div>

## 📚 Las 7 secciones del vault

<div class="dashboard-shortcuts">

- [[_01-Sistemas-Operativos|01 — Sistemas Operativos]]
- [[_02-Ciberseguridad|02 — Ciberseguridad]]
- [[_03-Desarrollo|03 — Desarrollo]]
- [[_04-Laboratorios|04 — Laboratorios]]
- [[_05-Recursos|05 — Recursos]]
- [[_06-Publicaciones-Linkedin|06 — Publicaciones LinkedIn]]
- [[_07- Inteligencia-Artificial|07 — Inteligencia Artificial]]

</div>

---

<div class="dashboard-calendar">

```dataviewjs
// Calendario compacto — esquina superior derecha
// Renderiza fecha actual usando moment.js (incluido en Obsidian)
const m = moment();
const dayName = m.format("dddd");        // ej: "viernes"
const day = m.format("DD");              // ej: "30"
const monthYear = m.format("MMMM YYYY"); // ej: "mayo 2026"

dv.el("div", `
<div class="cal-widget">
  <div class="cal-dayname">${dayName.toUpperCase()}</div>
  <div class="cal-daynum">${day}</div>
  <div class="cal-monthyear">${monthYear}</div>
</div>
`, { cls: "cal-container" });
```

</div>

<div class="dashboard-heatmap">

```dataviewjs
// Heatmap GitHub-style — esquina inferior derecha
// Datos: notas creadas/modificadas en el último año
const calendarData = {
  year: moment().year(),
  colors: {
    green: ["#9be9a8", "#40c463", "#30a14e", "#216e39"]
  },
  showCurrentDayBorder: true,
  defaultEntryIntensity: 1,
  intensityScaleStart: 1,
  intensityScaleEnd: 5,
  entries: []
};

// Construir entries a partir de file.mtime de todas las notas
const pages = dv.pages('-"templates"').values;
const byDate = {};

for (const p of pages) {
  if (!p.file.mtime) continue;
  const dateKey = p.file.mtime.toFormat("yyyy-MM-dd");
  byDate[dateKey] = (byDate[dateKey] || 0) + 1;
}

for (const [date, count] of Object.entries(byDate)) {
  calendarData.entries.push({
    date: date,
    intensity: Math.min(count, 5),
    content: `📝 ${count} nota(s)`
  });
}

renderHeatmapTracker(this.container, calendarData);
```

</div>

<div class="dashboard-footer">

📊 **Estadísticas del vault** —
notas: `$= dv.pages().length` ·
indexes: `$= dv.pages('"" and #tipo/indice').length`

</div>
