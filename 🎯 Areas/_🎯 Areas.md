---
tipo: indice
seccion: 🎯 Areas
actualizado: 2026-05-30
---

# 🎯 Areas

🏠 [[🔒🐧Hub|Hub Principal]] · [[🔒🐧Hub|Dashboard]]

**Áreas de responsabilidad continua** (no terminan). Estándares de calidad
que mantienes a lo largo del tiempo. Ejemplos: aprendizaje continuo,
salud, finanzas, carrera profesional.

## Áreas activas

```dataviewjs
const areas = dv.pages('"🎯 Areas"').where(p => p.file.name !== "_🎯 Areas");

if (areas.length === 0) {
  dv.paragraph(`_No hay áreas todavía. Crea una con la plantilla [[area]]._

Ejemplos de áreas para alguien aprendiendo ciberseguridad:

- 🧠 **Aprendizaje continuo** (cursos, certs, lectura).
- 💼 **Carrera profesional** (LinkedIn, networking, portfolio).
- 🏋️ **Salud** (ejercicio, sueño, alimentación).
- 💰 **Finanzas** (presupuesto, ahorro, inversión).
- 👥 **Relaciones** (familia, amigos, mentores).`);
} else {
  dv.table(["Área", "Estado", "Última revisión"],
    areas.map(p => [
      p.file.link,
      p.estado || "🟢 activa",
      p.ultima_revision || p.file.mtime.toFormat("dd LLL yyyy")
    ])
  );
}
```

## Diferencia Areas vs Projects

| Aspecto | Projects | Areas |
|---|---|---|
| Tiene fecha de fin | Sí | No |
| Tiene objetivo concreto | Sí | No (es un estándar) |
| Ejemplo | "Aprobar eJPTv2" | "Mantenerme actualizado en ciber" |

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[🔒🐧Hub|Dashboard]]

## Relacionadas

- [[_🚀 Projects|Projects]] — proyectos activos con deadline.
- [[_05-Recursos|05-Recursos]] — referencias usadas en las áreas.
