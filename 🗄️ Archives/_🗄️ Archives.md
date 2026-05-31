---
tipo: indice
seccion: 🗄️ Archives
actualizado: 2026-05-30
---

# 🗄️ Archives

🏠 [[🔒🐧Hub|Hub Principal]] · [[🔒🐧Hub|Dashboard]]

**Proyectos terminados** y notas obsoletas que ya no son activas pero
mantenemos por referencia histórica. NO borrar — archivar.

## Archivados

```dataviewjs
const archived = dv.pages('"🗄️ Archives"').where(p => p.file.name !== "_🗄️ Archives");

if (archived.length === 0) {
  dv.paragraph("_Archivo vacío. Aquí irán proyectos completados de [[_🚀 Projects|Projects]]._");
} else {
  dv.table(["Item", "Tipo", "Archivado"],
    archived.map(p => [
      p.file.link,
      p.tipo || "—",
      p.archivado_en || p.file.mtime.toFormat("dd LLL yyyy")
    ])
  );
}
```

## Cuándo archivar

- **Proyecto completado** → cambiar estado a `archivado` y mover desde
  [[_🚀 Projects|Projects]] aquí.
- **Área cerrada** → ya no es relevante (cambio de carrera, etc.).
- **Recurso obsoleto** → tecnología deprecated.

## Por qué NO borrar

- **Búsqueda futura**: a veces necesitas recordar cómo resolviste X.
- **Auditoría**: track de evolución del vault.
- **Reflexión**: revisar archivos completados es motivador.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[🔒🐧Hub|Dashboard]]

## Relacionadas

- [[_🚀 Projects|Projects]] — proyectos activos.
- [[_🎯 Areas|Areas]] — áreas continuas.
- [[log|Bitácora del vault]] — historial cronológico de cambios.
