---
tipo: hub
tags: [hub, vault-principal, linux, ciberseguridad, dashboard]
actualizado: 2026-05-30
cssclasses:
  - dashboard-home
---

<div class="dashboard-hero">
<img src="assets/wallpaper.svg" alt="hero" class="dashboard-hero-img" />
<div class="dashboard-hero-overlay">
<div class="dashboard-hero-meta">

```dataviewjs
const h = moment().hour();
let greeting = "Buenas noches";
if (h >= 5 && h < 12) greeting = "Buenos días";
else if (h >= 12 && h < 19) greeting = "Buenas tardes";
const fecha = moment().format("dddd, D [de] MMMM YYYY");
const hora = moment().format("h:mm A");   // 12h con AM/PM
dv.el("div", `
  <span class="hero-greeting">${greeting}, je7remy</span>
  <span class="hero-date">${fecha} · ${hora}</span>
`, { cls: "hero-line" });
```

</div>
<h1 class="dashboard-title">linuxknowledge</h1>
<p class="dashboard-subtitle">Linux &amp; Cybersecurity Knowledge Hub</p>
</div>
</div>

## Quick Access

<div class="quick-access-grid">
<a class="internal-link qa-card" data-href="_📥 Inbox" href="_📥 Inbox"><span class="qa-icon">📥</span><span class="qa-label">Inbox</span></a>
<a class="internal-link qa-card" data-href="_📅 Daily Notes" href="_📅 Daily Notes"><span class="qa-icon">📅</span><span class="qa-label">Daily Notes</span></a>
<a class="internal-link qa-card" data-href="_🚀 Projects" href="_🚀 Projects"><span class="qa-icon">🚀</span><span class="qa-label">Projects</span></a>
<a class="internal-link qa-card" data-href="📋 All Tasks" href="📋 All Tasks"><span class="qa-icon">📋</span><span class="qa-label">All Tasks</span></a>
<a class="internal-link qa-card" data-href="📡 RSS Feeds" href="📡 RSS Feeds"><span class="qa-icon">📡</span><span class="qa-label">RSS</span></a>
<a class="internal-link qa-card" data-href="index" href="index"><span class="qa-icon">📚</span><span class="qa-label">Knowledge</span></a>
<a class="internal-link qa-card" data-href="_🎯 Areas" href="_🎯 Areas"><span class="qa-icon">🎯</span><span class="qa-label">Areas</span></a>
<a class="internal-link qa-card" data-href="_05-Recursos" href="_05-Recursos"><span class="qa-icon">💎</span><span class="qa-label">Resources</span></a>
<a class="internal-link qa-card" data-href="_🗄️ Archives" href="_🗄️ Archives"><span class="qa-icon">🗄️</span><span class="qa-label">Archives</span></a>
<a class="internal-link qa-card" data-href="_Vista Curada" href="_Vista Curada"><span class="qa-icon">🧭</span><span class="qa-label">MOCs</span></a>
</div>

<div class="bento-grid">

<div class="bento-card bento-calendar">

<div class="bento-header">
<span class="bento-icon">📅</span>
<span class="bento-title">Calendario</span>
<span class="bento-sub">click → daily note</span>
</div>

```dataviewjs
const today = moment();
const year = today.year();
const month = today.month();
const monthStart = moment([year, month, 1]);
const monthEnd = monthStart.clone().endOf('month');
const firstWeekday = (monthStart.day() + 6) % 7;
const daysInMonth = monthEnd.date();

const dailyNotes = new Set();
for (const p of dv.pages('"📅 Daily Notes"').values) {
  if (p.file.name && p.file.name !== "_📅 Daily Notes") dailyNotes.add(p.file.name);
}

const byDate = {};
for (const p of dv.pages('-"templates"').values) {
  if (!p.file.mtime) continue;
  const key = p.file.mtime.toFormat("yyyy-MM-dd");
  byDate[key] = (byDate[key] || 0) + 1;
}

const monthName = monthStart.format("MMMM YYYY");
const weekdays = ["L", "M", "X", "J", "V", "S", "D"];

let html = `<div class="cal-mensual">
  <div class="cal-header">
    <span class="cal-month-name">${monthName}</span>
    <span class="cal-today-pill">${today.format("D MMM").toUpperCase()}</span>
  </div>
  <div class="cal-weekdays">${weekdays.map(d => `<span>${d}</span>`).join("")}</div>
  <div class="cal-days">`;

for (let i = 0; i < firstWeekday; i++) html += `<span class="cal-day cal-blank"></span>`;

for (let d = 1; d <= daysInMonth; d++) {
  const date = moment([year, month, d]);
  const dateKey = date.format("YYYY-MM-DD");
  const isToday = date.isSame(today, 'day');
  const hasActivity = byDate[dateKey] > 0;
  const hasDailyNote = dailyNotes.has(dateKey);
  const cls = ["cal-day"];
  if (isToday) cls.push("cal-today");
  if (hasActivity) cls.push("cal-active");
  if (hasDailyNote) cls.push("cal-has-note");
  const linkTarget = `📅 Daily Notes/${dateKey}`;
  html += `<a href="${linkTarget}" class="internal-link cal-link"><span class="${cls.join(" ")}">${d}${hasActivity ? '<i class="cal-dot"></i>' : ''}</span></a>`;
}
html += `</div></div>`;
dv.el("div", html, { cls: "cal-wrapper" });
```

</div>

<div class="bento-sidebar">

<div class="bento-card bento-tasks">

<div class="bento-header">
<span class="bento-icon">✅</span>
<span class="bento-title">Daily Tasks</span>
</div>

```dataviewjs
// Solo tasks de carpetas PARA accionables (no quizzes de cursos del Knowledge Base)
const pages = dv.pages('"📅 Daily Notes" or "🚀 Projects" or "📥 Inbox" or "🎯 Areas"');
const tasks = pages.file.tasks
  .where(t => !t.completed)
  .where(t => t.text && t.text.trim().length > 2);  // filtrar placeholders vacíos

if (tasks.length === 0) {
  dv.paragraph("✅ _Sin tasks pendientes_");
} else {
  dv.taskList(tasks.sort(t => t.line, "desc").slice(0, 6), false);
}
```

</div>

<div class="bento-card bento-stats">

<div class="bento-header">
<span class="bento-icon">📊</span>
<span class="bento-title">Quick Stats</span>
</div>

```dataviewjs
const all = dv.pages('-"templates"');
const today = moment();
const startOfToday = today.startOf('day');

const createdToday = all.where(p => p.file.ctime >= startOfToday).length;
const modifiedToday = all.where(p => p.file.mtime >= startOfToday && p.file.ctime < startOfToday).length;
const projects = dv.pages('"🚀 Projects"').where(p =>
  p.file.name !== "_🚀 Projects" && p.estado !== "completado" && p.estado !== "archivado"
).length;

// Tasks completadas hoy: solo de carpetas PARA (no quizzes de cursos)
const actionablePages = dv.pages('"📅 Daily Notes" or "🚀 Projects" or "📥 Inbox" or "🎯 Areas"');
const tasksCompleted = actionablePages.file.tasks
  .where(t => t.completed && t.completion && t.completion >= startOfToday)
  .length;

let streak = 0;
const byDate = {};
for (const p of all.values) {
  if (p.file.mtime) byDate[p.file.mtime.toFormat("yyyy-MM-dd")] = true;
}
for (let i = 0; i < 365; i++) {
  const d = today.clone().subtract(i, 'days').format("YYYY-MM-DD");
  if (byDate[d]) streak++;
  else if (i > 0) break;
}

const html = `<div class="stats-grid">
  <div class="stat"><span class="stat-num">${createdToday}</span><span class="stat-label">Hoy +</span></div>
  <div class="stat"><span class="stat-num">${modifiedToday}</span><span class="stat-label">Modif.</span></div>
  <div class="stat"><span class="stat-num">${tasksCompleted}</span><span class="stat-label">✓ hoy</span></div>
  <div class="stat"><span class="stat-num">${projects}</span><span class="stat-label">Proj</span></div>
  <div class="stat"><span class="stat-num">${all.length}</span><span class="stat-label">Total</span></div>
  <div class="stat"><span class="stat-num">${streak}🔥</span><span class="stat-label">Streak</span></div>
</div>`;
dv.el("div", html, { cls: "stats-wrapper" });
```

</div>

<div class="bento-card bento-projects">

<div class="bento-header">
<span class="bento-icon">🚀</span>
<span class="bento-title">Active Projects</span>
</div>

```dataviewjs
const projects = dv.pages('"🚀 Projects"')
  .where(p => p.file.name !== "_🚀 Projects" && p.estado !== "completado" && p.estado !== "archivado")
  .sort(p => p.deadline || "9999", "asc")
  .limit(3);

if (projects.length === 0) {
  dv.paragraph(`_Sin proyectos activos._
[Crear →](_🚀 Projects)`);
} else {
  const html = `<ul class="proj-list">${projects.map(p => {
    const prog = p.progreso !== undefined ? p.progreso : 0;
    const dl = p.deadline || "—";
    return `<li class="proj-item">
      <a class="internal-link proj-name" href="${p.file.name}">${p.file.name}</a>
      <div class="proj-meta">
        <span class="proj-deadline">${dl}</span>
        <span class="proj-state">${p.estado || "🟢"}</span>
      </div>
      <div class="proj-bar"><div class="proj-fill" style="width:${prog}%"></div></div>
    </li>`;
  }).join("")}</ul>`;
  dv.el("div", html, { cls: "proj-wrapper" });
}
```

</div>

</div>

</div>

<div class="bento-card bento-yeartracker">

<div class="bento-header">
<span class="bento-icon">📈</span>
<span class="bento-title">Year Tracker</span>
<span class="bento-sub">actividad anual del vault</span>
</div>

```dataviewjs
const year = moment().year();
const yearStart = moment([year, 0, 1]);
const yearEnd = moment([year, 11, 31]);

const byDate = {};
for (const p of dv.pages('-"templates"').values) {
  if (!p.file.mtime) continue;
  const key = p.file.mtime.toFormat("yyyy-MM-dd");
  byDate[key] = (byDate[key] || 0) + 1;
}

const counts = Object.values(byDate).filter(v => v > 0);
const maxCount = counts.length ? Math.max(...counts) : 1;
const q = (n) => Math.ceil((n / maxCount) * 4);

const colors = ["#1e2530", "#0e4429", "#006d32", "#26a641", "#39d353"];

let cursor = yearStart.clone();
while (cursor.day() !== 1) cursor.subtract(1, 'day');

const weeks = [];
const monthLabels = [];
let lastMonth = -1;

while (cursor.isBefore(yearEnd) || cursor.isSame(yearEnd, 'week')) {
  const week = [];
  for (let i = 0; i < 7; i++) {
    const day = cursor.clone().add(i, 'days');
    const dateKey = day.format("YYYY-MM-DD");
    const inYear = day.year() === year;
    const count = inYear ? (byDate[dateKey] || 0) : 0;
    const level = count > 0 ? q(count) : 0;
    week.push({ date: dateKey, count, level, inYear, day });
  }
  weeks.push(week);
  const monthOfThisWeek = cursor.month();
  if (monthOfThisWeek !== lastMonth && cursor.year() === year) {
    monthLabels.push({ week: weeks.length - 1, label: cursor.format("MMM") });
    lastMonth = monthOfThisWeek;
  }
  cursor.add(1, 'week');
}

const weekdayLabels = ["", "Mar", "", "Jue", "", "Sáb", ""];
const today = moment();

let html = `<div class="heatmap-custom">
  <div class="heatmap-months">
    <span class="heatmap-corner"></span>
    ${monthLabels.map(m => `<span class="heatmap-month-label" style="grid-column: ${m.week + 2}">${m.label}</span>`).join("")}
  </div>
  <div class="heatmap-body">
    <div class="heatmap-weekdays">${weekdayLabels.map(d => `<span>${d}</span>`).join("")}</div>
    <div class="heatmap-grid" style="grid-template-columns: repeat(${weeks.length}, 14px)">`;

for (const week of weeks) {
  for (const cell of week) {
    if (!cell.inYear) {
      html += `<div class="heatmap-cell" style="background:transparent"></div>`;
    } else {
      const bg = colors[cell.level];
      const border = cell.day.isSame(today, 'day') ? 'box-shadow:0 0 0 2px #fff' : '';
      html += `<div class="heatmap-cell" style="background:${bg};${border}" title="${cell.date} — ${cell.count} nota(s)"></div>`;
    }
  }
}

const totalActive = counts.length;
const totalNotesYear = counts.reduce((a, b) => a + b, 0);

html += `</div></div>
  <div class="heatmap-legend">
    <span>Menos</span>
    ${colors.map(c => `<div class="heatmap-cell" style="background:${c}"></div>`).join("")}
    <span>Más</span>
    <span class="heatmap-total">${totalActive} días · ${totalNotesYear} notas · pico ${maxCount}/día</span>
  </div>
</div>`;
dv.el("div", html, { cls: "heatmap-wrapper" });
```

</div>

<div class="dashboard-footer">

<span class="footer-section">📚 <a class="internal-link" href="index">Index</a></span>
<span class="footer-section">📜 <a class="internal-link" href="schema">Schema</a></span>
<span class="footer-section">🤖 <a class="internal-link" href="CLAUDE">CLAUDE</a></span>
<span class="footer-section">📝 <a class="internal-link" href="log">Log</a></span>
<span class="footer-section">🗺️ <a class="internal-link" href="_roadmap">Roadmap</a></span>
<span class="footer-section">📖 <a class="internal-link" href="00 - Dashboard Guide">Guide</a></span>
<span class="footer-section">📡 <a class="internal-link" href="📡 RSS Feeds">RSS Feeds</a></span>

</div>
