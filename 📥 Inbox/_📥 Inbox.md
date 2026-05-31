---
tipo: indice
seccion: 📥 Inbox
actualizado: 2026-05-30
---

# 📥 Inbox

🏠 [[🔒🐧Hub|Hub Principal]] · [[🔒🐧Hub|Dashboard]]

**Capture rápido** de ideas, notas sueltas, links, fragmentos. Toda nota
nueva empieza aquí antes de clasificarse a Projects/Areas/Resources.

**Workflow:** Capture rápido → Procesar (clasificar y mover) → Vaciar
el inbox semanalmente.

## Notas en el Inbox

```dataviewjs
const items = dv.pages('"📥 Inbox"')
  .where(p => p.file.name !== "_📥 Inbox")
  .sort(p => p.file.ctime, "desc");

if (items.length === 0) {
  dv.paragraph("_Inbox vacío. Buen trabajo._ ✅");
} else {
  dv.table(["Nota", "Capturada", "Edad"],
    items.map(p => {
      const age = moment().diff(p.file.ctime.toJSDate(), 'days');
      const ageStr = age === 0 ? "hoy" : `hace ${age}d`;
      return [p.file.link, p.file.ctime.toFormat("dd LLL HH:mm"), ageStr];
    })
  );
}
```

## Cómo procesar el Inbox

1. **¿Es accionable?**
   - Sí, con fecha + esfuerzo → mover a [[_🚀 Projects|Projects]].
   - Sí, sin fecha (mantenimiento continuo) → mover a [[_🎯 Areas|Areas]].
2. **¿Es referencia?** → mover a `[[_05-Recursos|Resources]]` o sección
   temática.
3. **¿Es trash?** → borrar.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[🔒🐧Hub|Dashboard]]

## Relacionadas

- [[_🚀 Projects|Projects]] — proyectos activos.
- [[_🎯 Areas|Areas]] — áreas de responsabilidad continua.
- [[_🗄️ Archives|Archives]] — proyectos terminados.
