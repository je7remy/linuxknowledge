---
tipo: indice
seccion: 🚀 Projects
actualizado: 2026-05-30
---

# 🚀 Projects

🏠 [[🔒🐧Hub|Hub Principal]] · [[🔒🐧Hub|Dashboard]]

**Proyectos activos** con objetivo definido y fecha de finalización. A
diferencia de [[_🎯 Areas|Areas]] (continuas), los Projects **terminan**.

## Proyectos activos

```dataviewjs
const projects = dv.pages('"🚀 Projects"')
  .where(p => p.file.name !== "_🚀 Projects" && p.estado !== "completado" && p.estado !== "archivado");

if (projects.length === 0) {
  dv.paragraph("_No hay proyectos activos. Crea uno con la plantilla [[project]]._");
} else {
  dv.table(["Proyecto", "Estado", "Deadline", "Progreso"],
    projects.map(p => [
      p.file.link,
      p.estado || "🟢 activo",
      p.deadline || "—",
      p.progreso !== undefined ? `${p.progreso}%` : "—"
    ])
  );
}
```

## Proyectos completados (este año)

```dataviewjs
const year = moment().year();
const done = dv.pages('"🚀 Projects"')
  .where(p => p.estado === "completado" && p.completado_en?.year === year);

if (done.length === 0) {
  dv.paragraph("_Aún no hay proyectos completados este año._");
} else {
  dv.table(["Proyecto", "Completado"],
    done.map(p => [p.file.link, p.completado_en || "—"])
  );
}
```

## Cómo crear un proyecto

1. Usar plantilla [[project|templates/project.md]].
2. Definir: `objetivo`, `deadline`, `estado: 🟢 activo`, `area_padre`.
3. Romper en tasks (`- [ ]`) que aparecerán en daily/Dashboard.
4. Al completar: cambiar `estado: completado` y mover a
   [[_🗄️ Archives|Archives]].

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[🔒🐧Hub|Dashboard]]

## Relacionadas

- [[_🎯 Areas|Areas]] — responsabilidades continuas (no terminan).
- [[_📥 Inbox|Inbox]] — capture inicial de ideas de proyectos.
- [[_🗄️ Archives|Archives]] — proyectos completados.
