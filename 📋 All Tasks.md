---
tipo: indice
seccion: vault-root
tags: [tasks, dashboard]
actualizado: 2026-05-30
---

# 📋 All Tasks

🏠 [[🔒🐧Hub|Hub Principal]]

Vista global de **todas las tasks pendientes** del vault. Recolectadas
automáticamente de cualquier `- [ ]` en cualquier nota (excluyendo
`templates` y `🗄️ Archives`).

## Tasks pendientes

```dataviewjs
const pages = dv.pages('-"templates" and -"🗄️ Archives"');
const tasks = pages.file.tasks.where(t => !t.completed);
if (tasks.length === 0) {
  dv.paragraph("✅ _Sin tasks pendientes._");
} else {
  dv.taskList(tasks.sort(t => t.line, "desc"), false);
}
```

## Tasks completadas hoy

```dataviewjs
const today = moment().startOf('day');
const pages = dv.pages('-"templates"');
const done = pages.file.tasks.where(t => t.completed && t.completion && t.completion >= today);
if (done.length === 0) {
  dv.paragraph("_Aún no has completado tasks hoy._");
} else {
  dv.taskList(done, false);
}
```

## Tasks por proyecto

```dataviewjs
const projects = dv.pages('"🚀 Projects"').where(p => p.file.name !== "_🚀 Projects");
if (projects.length === 0) {
  dv.paragraph("_No hay proyectos con tasks aún._");
} else {
  for (const proj of projects) {
    const pTasks = proj.file.tasks.where(t => !t.completed);
    if (pTasks.length > 0) {
      dv.header(3, proj.file.link);
      dv.taskList(pTasks, false);
    }
  }
}
```

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[_🚀 Projects|Projects]]
- [[_📅 Daily Notes|Daily Notes]]

## Relacionadas

- [[_📥 Inbox|Inbox]] — items por procesar (algunos serán tasks).
- [[_🎯 Areas|Areas]] — tasks de hábitos continuos.
