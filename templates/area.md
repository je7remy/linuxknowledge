---
tipo: area
tags: [area]
estado: 🟢 activa
ultima_revision: {{date:YYYY-MM-DD}}
proxima_revision:
actualizado: {{date:YYYY-MM-DD}}
---

# 🎯 {{title}}

🏠 [[🔒🐧Hub|Hub]] · [[🔒🐧Hub|Dashboard]] · [[_🎯 Areas|Areas]]

## 🎯 Estándar de calidad

Define el estándar que mantienes en esta área. ¿Qué significa que esté
"en buen estado"?

> _Ejemplo (Aprendizaje continuo): "Dedico al menos 5h/semana a estudiar
> ciberseguridad y mantengo el vault actualizado."_

## 📊 Métricas / KPIs

Cómo medir si el área está saludable:

- Métrica 1: target
- Métrica 2: target

## 🔄 Cadencia de revisión

- **Frecuencia**: semanal / quincenal / mensual.
- **Última revisión**: `=this.ultima_revision`
- **Próxima revisión**: `=this.proxima_revision`

## 📋 Hábitos / Rutinas

- [ ] Hábito recurrente 1
- [ ] Hábito recurrente 2

## 📚 Recursos clave

- [[RECURSO_1]] — descripción.
- [[RECURSO_2]] — descripción.

## 🚀 Proyectos asociados

```dataviewjs
const thisArea = dv.current().file.name;
const projects = dv.pages('"🚀 Projects"').where(p => p.area_padre === thisArea);
if (projects.length === 0) {
  dv.paragraph("_No hay proyectos activos en esta área._");
} else {
  dv.list(projects.map(p => p.file.link));
}
```

## 📝 Notas

> Reflexiones sobre el área, retos actuales, ideas a explorar.

## Navegación

- 🏠 [[🔒🐧Hub|Hub]]
- [[_🎯 Areas|Volver a Areas]]
