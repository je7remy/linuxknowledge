---
tipo: teoria
tags: [osint, ciberseguridad, entity-page, reconocimiento, recon]
actualizado: 2026-05-30
---

# OSINT

🏠 [[🔒🐧Hub|Hub Principal del vault]]

**Entity page** del concepto **Open Source Intelligence** — recolección de
información a partir de fuentes públicas. Componente crítico de la fase de
**Reconocimiento** en [[MOC - Pentesting end-to-end|pentesting]] y también
útil en **forense digital**, **investigaciones de fraude** e
**inteligencia competitiva**.

## Definición

**OSINT** (Open Source Intelligence) es la disciplina de recolectar y
analizar información de **fuentes públicas y accesibles legalmente**, sin
interactuar directamente con el target. La clave es la **pasividad**: el
target no detecta que está siendo investigado.

Fuentes típicas:

- Buscadores (Google, Bing, DuckDuckGo).
- Redes sociales (LinkedIn, Twitter/X, Facebook, Instagram).
- Registros públicos (Whois, certificados SSL, BGP routing).
- Repositorios de código (GitHub, GitLab, Bitbucket).
- Imágenes y metadatos.
- Archivos web históricos (Wayback Machine).
- Bases de breaches públicas (HaveIBeenPwned, Dehashed).

## OSINT en el flujo de pentesting

Es la **fase 2** del PTES (Intelligence Gathering). En esta fase NO se
interactúa con el target, solo se recolecta info pública.

Pivotes típicos desde mínima info inicial:

```
Dominio → Whois (registrante, nameservers)
       → SSL cert transparency (subdominios)
       → Web archive (versiones antiguas)
       → DNS records (MX, TXT, SPF)
       → BGP (ASN, IP ranges)
       
Email → Breach lookups (passwords filtradas)
     → Gravatar / social profiles
     → Google dorks ("email@target.com")
     
Nombre persona → LinkedIn (empresa, rol, colegas)
              → Twitter (intereses, ubicación)
              → Imágenes (geolocalización por metadatos)
              → Whois de dominios registrados a su nombre
```

## Herramientas en el vault

### Para metadatos de archivos

- [[_2- Extraer Metadatos de imagenes|2- Extraer Metadatos de imágenes]] —
  con **ExifTool**: extraer GPS, modelo de cámara, software, fechas.

### Para reconocimiento de red

- [[_2- Shodan|Shodan]] — buscador de dispositivos expuestos a internet
  (cámaras, ICS, bases de datos abiertas).
- [[_1- Nmap|Nmap]] — fase 3 (activa) del pentest, pero NSE scripts también
  hacen OSINT lookups (whois, dns, ssl-cert).

### Para forense digital

- [[_6- Forense Digital|6- Forense Digital]] — casos prácticos donde OSINT
  apoya investigaciones (caso "Spear Phishing JFK Luxury Design").

## Google Dorks (búsqueda avanzada)

Sintaxis útil:

| Operador | Ejemplo | Qué hace |
|---|---|---|
| `site:` | `site:example.com filetype:pdf` | Solo en ese dominio |
| `filetype:` | `filetype:xls password` | Tipo de archivo |
| `inurl:` | `inurl:admin login` | Texto en URL |
| `intitle:` | `intitle:"index of" passwd` | Texto en título |
| `intext:` | `intext:"sql syntax"` | Texto en cuerpo |
| `cache:` | `cache:example.com` | Versión cacheada |
| `-` | `apple -fruit` | Excluir término |
| `OR` / `\|` | `linux OR windows` | Disyunción |

Bases de dorks pre-armados:
- **Google Hacking Database (GHDB)** en exploit-db.com.

## Frameworks y herramientas externas (no en el vault aún)

- **theHarvester** — emails, subdominios, hosts.
- **Maltego** — visualización de relaciones (paid + free).
- **SpiderFoot** — automatización OSINT.
- **recon-ng** — framework modular tipo Metasploit pero para recon.
- **Sherlock** — buscar username en cientos de redes.
- **Amass** — enumeración de subdominios.
- **OSINT Framework** — directorio web de herramientas
  (osintframework.com).

## OSINT vs SOCMINT vs HUMINT

| Disciplina | Fuente |
|---|---|
| **OSINT** | Información pública (web, redes, registros). |
| **SOCMINT** | Subconjunto de OSINT específico a redes sociales. |
| **HUMINT** | Human Intelligence (interacción social directa). |
| **SIGINT** | Signals Intelligence (intercepción de comunicaciones). |
| **GEOINT** | Geospatial Intelligence (mapas, satélite). |

OSINT es **legal** y **pasivo**. HUMINT puede cruzar a social engineering.

## Aplicaciones legítimas

OSINT no es solo ofensivo. Casos legítimos:

- **Investigación periodística** (Bellingcat).
- **Búsqueda de personas desaparecidas**.
- **Due diligence empresarial** (verificar contraparte antes de negocio).
- **Threat intelligence defensivo** (qué hablan de mi empresa los foros).
- **Verificación de credenciales** (LinkedIn vs realidad).

## Privacidad personal — el otro lado de OSINT

Si OSINT puede encontrar todo, ¿cómo te proteges?

- Configurar privacy en cada red social al máximo.
- Limpiar metadatos antes de publicar fotos.
- Usar emails diferentes para cuentas sensibles.
- Revisar tu propia presencia en buscadores periódicamente.
- Consultar HaveIBeenPwned para ver breaches que te afecten.
- Considerar borrar cuentas viejas (justdelete.me como recurso).

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[Pentesting|Pentesting (entity page)]] — OSINT como fase 2 del pentest.
- [[MOC - Pentesting end-to-end|MOC - Pentesting end-to-end]] — flujo
  completo donde OSINT aparece.
- [[_5- Reconocimiento|5- Reconocimiento (carpeta)]] — herramientas
  específicas.
- [[_6- Forense Digital|6- Forense Digital]] — OSINT en investigación
  forense.
