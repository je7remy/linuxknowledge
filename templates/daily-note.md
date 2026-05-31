---
tipo: daily
tags: [daily]
fecha: {{date:YYYY-MM-DD}}
actualizado: {{date:YYYY-MM-DD}}
---

# 📅 {{date:dddd D [de] MMMM, YYYY}}

🏠 [[🔒🐧Hub|Hub]] · [[🔒🐧Hub|Dashboard]] · [[_📅 Daily Notes|Daily Notes]]

## 🎯 Top 3 prioridades

- [ ] Prioridad 1
- [ ] Prioridad 2
- [ ] Prioridad 3

## 📋 Tasks

- [ ]

## 📝 Notas del día

> ¿Qué aprendí hoy? ¿Qué descubrí? Capture rápido aquí.

## 💭 Reflexión

- **Energía:** ⚪⚪⚪⚪⚪
- **Foco:** ⚪⚪⚪⚪⚪
- **Mood:** 😐

### Qué funcionó

-

### Qué no funcionó

-

### Mañana

-

## 🔗 Enlaces del día

```dataviewjs
// Notas modificadas hoy (excluyendo esta daily note)
const todayKey = dv.current().file.name;
const today = moment(todayKey, "YYYY-MM-DD");
if (!today.isValid()) {
  dv.paragraph("_Nombre del archivo no es fecha — saltando._");
} else {
  const start = today.startOf('day');
  const end = today.endOf('day');
  const touched = dv.pages('-"templates" and -"📅 Daily Notes"')
    .where(p => p.file.mtime >= start && p.file.mtime <= end)
    .sort(p => p.file.mtime, "desc");
  if (touched.length === 0) {
    dv.paragraph("_Aún no has tocado ninguna nota hoy._");
  } else {
    dv.list(touched.map(p => p.file.link));
  }
}
```

---

## Navegación

- ⬅️ [Ayer](YYYY-MM-DD)
- ➡️ [Mañana](YYYY-MM-DD)
- 📅 [[_📅 Daily Notes|Todas las daily notes]]
