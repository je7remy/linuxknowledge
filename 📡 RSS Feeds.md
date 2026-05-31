---
tipo: indice
seccion: vault-root
tags: [rss, feeds, news, threat-intel]
actualizado: 2026-05-31
---

# 📡 RSS Feeds

🏠 [[🔒🐧Hub|Hub Principal]]

Sistema de **threat intel feeds** integrado con el plugin **RSS Dashboard**
(Aditya Amatya, v2.3.0). Capture continuo de noticias, papers, walkthroughs
y podcasts del dominio ciberseguridad. Los items relevantes se pueden
guardar al [[_📥 Inbox|Inbox]] del vault con un click.

## ⚠️ PRIMERA VEZ — Importar el OPML

El plugin **NO carga automáticamente** el `feeds.opml`. Hay que importarlo:

1. **Abrir RSS Dashboard** (ribbon icon o `Ctrl+P` → `RSS Dashboard: Open dashboard`).
2. **Click en el icono ⚙️ Settings** dentro del dashboard del plugin (NO en Settings global de Obsidian).
3. Buscar **"Import OPML"** o ir a la sección **Backup/Restore**.
4. **Click "Import OPML"** y seleccionar uno de estos archivos:
   - `assets/linuxknowledge-feeds.opml` (copia accesible).
   - `.obsidian/plugins/rss-dashboard/feeds.opml` (el primario).
   - `.obsidian/plugins/rss-dashboard/feeds.opml.backup` (idéntico al anterior).
5. Confirmar la importación → los 35 feeds aparecen en la sidebar del plugin.
6. **Refresh manual** la primera vez (icono 🔄): descarga las primeras entradas.

> Si el plugin no tiene "Import OPML" en la UI, ir a `Settings → Add feed`
> y añadir cada URL manualmente (ver lista abajo).

## Cómo abrir el feed reader (después de importar)

- **Ribbon icon** RSS en la barra lateral izquierda de Obsidian.
- **Command palette**: `Ctrl+P` → `RSS Dashboard: Open dashboard`.
- **Hotkey** (recomendado): asignar en Settings → Hotkeys → `Ctrl+Shift+R`.

## Feeds configurados (33)

### 📰 Threat Intel & News (8)

| Feed | URL | Cubre |
|---|---|---|
| **The Hacker News** | thehackernews.com | Breach reports, vulns, news diaria |
| **Bleeping Computer** | bleepingcomputer.com | Malware, ransomware, breaking news |
| **KrebsOnSecurity** | krebsonsecurity.com | Investigaciones profundas (Brian Krebs) |
| **Schneier on Security** | schneier.com | Análisis estratégico de seguridad |
| **Dark Reading** | darkreading.com | Enterprise security news |
| **SecurityWeek** | securityweek.com | News + analysis |
| **CISA Alerts** | cisa.gov | Alertas oficiales gubernamentales USA |
| **Threatpost** | threatpost.com | Vulnerabilidades y exploits |

### 🛡️ Pentesting & Red Team (5)

| Feed | URL | Cubre |
|---|---|---|
| **HackTricks** | book.hacktricks.xyz | Techniques wiki updates |
| **PortSwigger Daily Swig** | portswigger.net/daily-swig | Web security news |
| **Pentester Land** | pentester.land | Curated bug bounty content |
| **Exploit-DB** | exploit-db.com | PoCs y exploits publicados |
| **HackTheBox Blog** | hackthebox.com/blog | Walkthroughs y CTF news |

### 🐧 Linux & Open Source (4)

| Feed | Cubre |
|---|---|
| **LWN.net** | Linux kernel news, deep technical |
| **Phoronix** | Hardware reviews, performance |
| **It's FOSS** | Distros, software FOSS |
| **LinuxSecurity News** | Linux-specific security |

### ☁️ Cloud & DevSecOps (3)

- **AWS Security Blog**
- **Cloud Security Alliance**
- **Microsoft Security Blog**

### 💻 Dev & Tech (2)

- **Hacker News** (Y Combinator)
- **Lobsters** (link aggregator técnico)

### 🇪🇸 Español — Ciberseguridad (4)

- **Una al día** (Hispasec) — clásico español
- **Hackplayers** — pentesting en español
- **Security By Default** — análisis
- **INCIBE-CERT** — alertas gubernamentales España

### 🎥 YouTube — Cybersecurity (6)

Canales seguidos vía RSS (el plugin soporta YouTube nativamente):

- **IppSec** — HackTheBox machine walkthroughs (referencia para eJPTv2).
- **John Hammond** — CTFs, malware analysis, programming.
- **LiveOverflow** — reversing, binary exploitation.
- **The Cyber Mentor (TCM)** — pentest cursos prácticos.
- **NetworkChuck** — networking, IT.
- **DEF CON Conference** — talks oficiales.

### 🎙️ Podcasts (3)

- **Darknet Diaries** (Jack Rhysider) — historias de hacking reales.
- **Risky Business** — semanal de threat intel.
- **Smashing Security** — humor + actualidad.

## Configuración del plugin

| Setting | Valor | Por qué |
|---|---|---|
| **Refresh interval** | 30 min | Equilibrio entre frescura y carga |
| **Max items** | 100 | Mantiene historial razonable |
| **Auto-delete** | 60 días | Limpia automáticamente |
| **View style** | Card | Visual atractivo con thumbnails |
| **Show thumbnails** | ON | UX mejor |
| **Group by** | feed | Agrupa por fuente |
| **Default filter** | unread | Solo ver lo nuevo |
| **Auto mark read on open** | ON | Marca leído al abrir |
| **Sidebar width** | 280px | Suficiente para emoji + nombre |

### Highlights configurados

El plugin resalta automáticamente estas keywords en titles/summaries:

- `0day`, `zero-day`, `RCE`, `ransomware`, `CVE-2026`, `APT`, `phishing`,
  `supply chain`, `Kerberos`, `Active Directory`, `exploit`, `PoC`

→ Color: cyan (`#7fd1ff`).

### Badge colors

- All feeds unread badge: cyan `#7fd1ff`.
- Folder badge: púrpura `#b88dff`.
- Feed badge: teal `#5eead4`.

## Workflow PARA con RSS

```
1. Refresh automático cada 30 min → llegan items nuevos
2. Al abrir RSS Dashboard → ver "unread" del día
3. Hojear titulares (5-10 min mañana o noche)
4. Item interesante:
   ├─ Click "Save" → se crea nota en 📥 Inbox/
   │                  con frontmatter + checklist procesamiento
   ├─ Click "Star" → marcar para releer después
   └─ Click "Read" → abrir en split view dentro de Obsidian
5. En el Inbox semanal:
   └─ Procesar items guardados:
      ├─ Si relevante a proyecto → mover a 🚀 Projects/
      ├─ Si es referencia → mover a sección temática (02-Ciberseguridad/, etc.)
      ├─ Si es para tesis → mover a 03-Desarrollo/
      └─ Si no es útil → borrar
```

### Plantilla de captura al Inbox

Cuando guardas un artículo RSS, se crea automáticamente con este formato:

```yaml
---
tipo: inbox
tags: [rss, ...]
fuente: "The Hacker News"
link: "https://..."
autor: "..."
fecha: "..."
capturado: 2026-05-31 10:15
actualizado: 2026-05-31
---

# Título del artículo

> Capturado desde **The Hacker News** · [Source](...)

[Summary del artículo]

---

[Contenido completo si está disponible]

---

## Procesamiento

- [ ] ¿Es accionable? → Projects o Areas
- [ ] ¿Es referencia? → Resources / sección temática
- [ ] ¿Es trash? → borrar
```

## Cómo añadir un nuevo feed

### Vía UI

1. Abrir RSS Dashboard.
2. Click en icono "Add feed" en la sidebar.
3. Pegar URL del RSS/Atom feed.
4. Seleccionar folder (categoría).
5. Save.

### Vía edición manual de OPML

Editar `.obsidian/plugins/rss-dashboard/feeds.opml` añadiendo dentro del
folder apropiado:

```xml
<outline text="Nombre" title="Nombre" type="rss"
         xmlUrl="https://example.com/feed"
         htmlUrl="https://example.com/"/>
```

Reiniciar Obsidian o recargar el plugin.

## Cómo encontrar feeds RSS de un sitio

1. Mirar el footer del sitio (`/rss`, `/feed`, `/atom.xml`).
2. Ver source code: buscar `<link rel="alternate" type="application/rss+xml">`.
3. **YouTube**: `https://www.youtube.com/feeds/videos.xml?channel_id=<CHANNEL_ID>` (CHANNEL_ID se obtiene de View Source de la página del canal).
4. **Substack**: `https://example.substack.com/feed`.
5. **Medium**: `https://medium.com/feed/@username` o `https://medium.com/feed/publication`.
6. **GitHub user activity**: `https://github.com/USERNAME.atom`.

## Feeds que considerar añadir (sugerencias)

- **Atomic Red Team blog** (red canary atomic).
- **SANS Internet Storm Center**: https://isc.sans.edu/rssfeed.xml
- **Mandiant blog** (threat intel premium).
- **Google Project Zero**: https://googleprojectzero.blogspot.com/feeds/posts/default
- **PortSwigger Research**: https://portswigger.net/research/rss
- **NVD CVE feed**: https://services.nvd.nist.gov/feeds/json/cve/1.1/recent.json (no es RSS pero similar).

## Troubleshooting

| Síntoma | Solución |
|---|---|
| Feed no carga | Verificar URL en navegador. Puede haber rate limit o cambio. |
| YouTube feeds no actualizan | CHANNEL_ID puede estar mal. Buscar el nuevo. |
| Imágenes no cargan | Habilitar CORS proxy en settings (algunos sitios bloquean cross-origin). |
| Plugin lento con muchos feeds | Bajar `refreshInterval` a 60 min, o reducir `maxItems`. |
| "Failed to fetch" | El feed puede requerir User-Agent específico (usa CORS proxy). |

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal]]
- [[_📥 Inbox|Inbox]] — donde se guardan los artículos capturados.
- [[index|Index general del vault]]

## Relacionadas

- [[CLAUDE|CLAUDE — Instrucciones operativas]] — workflow de ingest.
- [[_05-Recursos|05-Recursos]] — destino final para artículos de referencia.
- [[Sintesis - IA y Ciberseguridad|Síntesis IA y Ciberseguridad]] — threat
  intel sobre IA en seguridad.
- [[APT|APT (entity page)]] — los feeds reportan actividad de APTs.
