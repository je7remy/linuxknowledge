---
tipo: referencia
tags: [dashboard, instalacion, obsidian, plugins]
actualizado: 2026-05-30
---

# Instalación del Dashboard — guía paso a paso

🏠 [[🔒🐧Hub|Hub Principal del vault]]

Guía completa para activar el dashboard personalizado con calendario en
esquina superior derecha y heatmap GitHub-style en esquina inferior derecha.

## Paso 1 — Instalar **Dataview** (único plugin faltante)

1. En Obsidian: `Settings` → `Community plugins` → `Browse`.
2. Buscar **"Dataview"** (autor: Michael Brenan / blacksmithgu).
3. `Install` → `Enable`.
4. Confirmar versión ≥ 0.5.x.

> Los demás plugins (`heatmap-tracker`, `homepage`, `templater-obsidian`,
> `beautitab`) ya están instalados.

## Paso 2 — Habilitar **JavaScript** en Dataview

Crítico para que el calendario y el heatmap funcionen:

1. `Settings` → `Community plugins` → `Dataview` (icono engranaje).
2. Sección **"Codeblock Settings"**:
   - ☑ **Enable JavaScript Queries** → ON.
   - ☑ **Enable Inline JavaScript Queries** → ON.
3. Sección **"General"**:
   - ☑ **Enable Inline Queries** → ON.

## Paso 3 — Copiar wallpaper

```powershell
# En PowerShell, crear carpeta assets
mkdir C:\linuxknowledge\assets

# Copiar tu wallpaper actual a esta ruta (cualquier .jpg/.png)
copy "C:\ruta\a\tu\wallpaper.jpg" "C:\linuxknowledge\assets\wallpaper.jpg"
```

> **Alternativa:** Si quieres extraer el wallpaper que ya tiene `beautitab`,
> está en base64 dentro de `.obsidian/plugins/beautitab/data.json`. Es más
> sencillo descargar uno nuevo de [Unsplash](https://unsplash.com) o
> reutilizar un archivo que ya tengas.

## Paso 4 — Activar CSS Snippet

1. `Settings` → `Appearance` → scroll hasta **"CSS snippets"**.
2. Click en el botón 🔄 (refresh) — Obsidian detectará `dashboard.css`.
3. Activar el toggle al lado de **"dashboard"**.

> El archivo `dashboard.css` ya está en `.obsidian/snippets/dashboard.css`.
> Si no aparece, click en la carpeta 📁 para abrir el directorio y verificar.

## Paso 5 — Configurar Homepage Plugin

1. `Settings` → `Community plugins` → `Homepage`.
2. **Homepage** → cambiar de `"Bienvenida"` (workspace) a:
   - Type: **File**.
   - Value: **`Home`** (sin extensión, Obsidian añade `.md`).
3. **Open on startup**: ☑ ON.
4. **Open mode**: `"Replace all open notes"`.
5. **Default view**: `"Reading view"` (para que `dataviewjs` renderice).
6. **Refresh Dataview**: ☑ ON (importante — refresca calendario y heatmap).

## Paso 6 — Mantener beautitab solo para new tab

beautitab seguirá funcionando con `Ctrl+T` (nueva pestaña). Para
configurarlo:

1. `Settings` → `Community plugins` → `Beautitab`.
2. **Replace new tab**: ☑ ON (mantener — sale en cada `Ctrl+T`).
3. **Replace homepage**: ☐ **OFF** (clave — para que NO interfiera con
   Home.md al arrancar).

## Paso 7 — Verificar

1. Cerrar Obsidian completamente.
2. Reabrir.
3. Debe abrir **`Home.md`** con:
   - Fondo de pantalla a pantalla completa.
   - Frase motivacional al inicio.
   - Atajos rápidos en bullets glassmorphism.
   - **Calendario** flotante en esquina superior derecha mostrando fecha de hoy.
   - **Heatmap** flotante en esquina inferior derecha mostrando actividad del año.
   - Stats al pie izquierdo.

## Troubleshooting

| Problema | Solución |
|---|---|
| El calendario no aparece, solo veo el bloque de código | Cambiar a **Reading view** (Ctrl+E). Verificar JavaScript habilitado en Dataview (Paso 2). |
| El heatmap muestra "renderHeatmapTracker is not defined" | Plugin `heatmap-tracker` no está activado. `Settings → Community plugins → Heatmap Tracker → Enable`. |
| El fondo no aparece | Ruta del wallpaper incorrecta. Verificar que existe `C:\linuxknowledge\assets\wallpaper.jpg`. Ajustar la ruta en `dashboard.css` línea ~10. |
| Los widgets están desalineados | El CSS snippet usa `position: fixed`. Si tu tema personalizado ya posiciona elementos similares, podría conflictuar. Probar desactivando temas custom temporalmente. |
| El home abre `beautitab` en lugar de `Home.md` | Paso 6 — desactivar **"Replace homepage"** en beautitab. |

## Personalización rápida

**Cambiar colores del calendario** en `dashboard.css`:

```css
.cal-dayname { color: #7fd1ff; }    /* turquesa → tu color */
.cal-daynum { color: #fff; }
```

**Cambiar paleta del heatmap** en `Home.md` (dentro del dataviewjs):

```js
colors: {
  green: ["#9be9a8", "#40c463", "#30a14e", "#216e39"]   // GitHub clásico
  // morado: ["#d0c5e8", "#9d80c8", "#6e4caa", "#4a2d7e"]
  // azul: ["#9ec5fe", "#5ba1f9", "#2680eb", "#0a58ca"]
}
```

**Cambiar posición del calendario** en `dashboard.css`:

```css
.dashboard-calendar {
  top: 50px;     /* superior */
  right: 30px;   /* derecha */
  /* o usar 'left: 30px;' para esquina superior izquierda */
}
```

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[🔒🐧Hub|Volver al Dashboard]]
- [[CLAUDE|Instrucciones operativas LLM]]

## Relacionadas

- [[schema|Schema del vault]] — convenciones de notas que el dashboard refleja.
- [[_templates|templates/]] — plantillas para nuevas notas.
- [[log|Bitácora]] — el dashboard alimenta el heatmap desde aquí.
