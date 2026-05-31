---
tipo: indice
seccion: 📅 Daily Notes
actualizado: 2026-05-30
---

# 📅 Daily Notes

🏠 [[🔒🐧Hub|Hub Principal]] · [[🔒🐧Hub|Dashboard]]

Notas diarias del vault. Formato `YYYY-MM-DD.md`. Click en cualquier día
del [[🔒🐧Hub|Dashboard]] (calendario) abre la daily note correspondiente.

## Daily notes recientes

```dataviewjs
const notes = dv.pages('"📅 Daily Notes"')
  .where(p => p.file.name !== "_📅 Daily Notes")
  .sort(p => p.file.name, "desc")
  .limit(14);

if (notes.length === 0) {
  dv.paragraph("_Aún no hay daily notes. Crea la primera desde el calendario del [[🔒🐧Hub|Dashboard]]._");
} else {
  dv.table(["Fecha", "Día semana", "Notas creadas"],
    notes.map(p => {
      const d = moment(p.file.name, "YYYY-MM-DD");
      const dayName = d.isValid() ? d.format("dddd") : "—";
      const wordCount = p.file.size ? `${Math.round(p.file.size/100)/10}k chars` : "—";
      return [p.file.link, dayName, wordCount];
    })
  );
}
```

## Plantilla usada

[[daily-note]] — define la estructura: agenda, tareas, notas, reflexión.

## Workflow recomendado

- **Mañana**: agenda del día + 3 prioridades.
- **Durante el día**: capture rápido en Inbox + tasks en daily.
- **Noche**: reflexión + procesar Inbox.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[🔒🐧Hub|Dashboard]]

## Relacionadas

- [[_📥 Inbox|Inbox]] — capture rápido.
- [[_🚀 Projects|Projects]] — proyectos a los que apuntan tasks.
- [[daily-note|Plantilla daily-note]].
