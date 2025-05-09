# Creación de un Script en Python para Enumerar Plugins de WordPress: Paso a Paso

En este tutorial, vamos a desarrollar paso a paso un script en Python diseñado para enumerar plugins instalados en un sitio WordPress, utilizando la máquina vulnerable "Azucar" de Docker Labs. Este proceso es útil en el ámbito de la ciberseguridad para identificar plugins que podrían ser vulnerables y, por ende, explotables. A continuación, detallaremos todo el proceso desde el inicio hasta el final, con explicaciones claras y formato Markdown para facilitar la comprensión.

---

## Introducción al Proyecto

El objetivo es crear una herramienta en Python que automatice la enumeración de plugins en un sitio WordPress. En el contexto de la ciberseguridad, esta técnica es valiosa porque muchos plugins obsoletos o con vulnerabilidades conocidas pueden ser puntos de entrada para ataques. Usaremos:

- **Kali Linux**: Como sistema operativo base.
- **Docker Labs**: Plataforma que proporciona máquinas vulnerables para prácticas de ciberseguridad.
- **Máquina "Azucar"**: Una máquina específica de Docker Labs con un WordPress que incluye un plugin vulnerable ("site-editor").
- **Python**: Con la librería `requests` para realizar peticiones HTTP.

---

## Paso 1: Descarga y Despliegue de la Máquina "Azucar"

### 1.1 Descarga de la Máquina
1. **Acceder a Docker Labs**:
   - Visita el sitio oficial de [Docker Labs](https://dockerlabs.es/).
   - Busca la máquina llamada "Azucar" y haz clic en "Descargar".
   - Esto abrirá un enlace en Mega (o similar). Elimina cualquier sufijo como ".LOAD" si aparece en el nombre del archivo.

2. **Tamaño del Archivo**:
   - La máquina ocupa aproximadamente 200 MB, por lo que es relativamente ligera.

3. **Descarga**:
   - Descarga el archivo ZIP al escritorio de tu Kali Linux.

### 1.2 Descompresión
1. **Abrir la Terminal**:
   - Abre una terminal en Kali Linux.

2. **Organizar el Escritorio**:
   - Para mantener el orden, elimina cualquier archivo innecesario del escritorio:
     ```bash
     sudo rm -r /home/user/Desktop/*
     ```
   - Nota: Asegúrate de que no haya archivos importantes antes de ejecutar este comando.

3. **Extraer el ZIP**:
   - Navega al directorio del escritorio:
     ```bash
     cd /home/user/Desktop
     ```
   - Extrae el archivo ZIP descargado:
     ```bash
     unzip azucar.zip
     ```
   - Esto generará una carpeta con los archivos necesarios, incluyendo `azucar.tar` y el script `autodeploy.sh`.

### 1.3 Desplegar la Máquina
1. **Ejecutar el Script de Despliegue**:
   - En la terminal, ejecuta:
     ```bash
     sudo bash autodeploy.sh azucar.tar
     ```
   - Este comando despliega la máquina vulnerable usando Docker.

2. **Obtener la IP**:
   - Una vez desplegada, la terminal mostrará la IP asignada a la máquina (por ejemplo, `172.17.0.2`). Anótala, ya que la usaremos para acceder al WordPress.

---

## Paso 2: Configuración Inicial del Entorno

### 2.1 Acceso al WordPress
1. **Probar la IP en el Navegador**:
   - Abre un navegador (como Firefox) y escribe:
     ```
     http://172.17.0.2/
     ```
   - Verás un sitio WordPress. Puede parecer mal configurado o "raro", pero esto no afecta nuestro propósito.

2. **Identificar el Dominio**:
   - Inspecciona la página (Ctrl+U para ver el código fuente).
   - Busca referencias a un dominio, como `azucar.dl`. Este dominio está asociado a la máquina y lo usaremos para evitar problemas con las peticiones HTTP.

### 2.2 Configurar el Archivo `/etc/hosts`
1. **Editar el Archivo**:
   - En la terminal, abre el archivo `/etc/hosts` con un editor como `nano`:
     ```bash
     sudo nano /etc/hosts
     ```

2. **Añadir el Dominio**:
   - Agrega una línea con la IP de la máquina y el dominio `azucar.dl`:
     ```
     172.17.0.2  azucar.dl
     ```
   - Guarda el archivo (Ctrl+O, Enter, Ctrl+X).

3. **Verificar la Configuración**:
   - Regresa al navegador y accede a:
     ```
     http://azucar.dl/
     ```
   - Ahora las imágenes y otros elementos deberían cargarse correctamente, confirmando que el dominio está bien asociado.

---

## Paso 3: Entendiendo la Enumeración de Plugins en WordPress

### 3.1 Ruta de los Plugins
- En WordPress, los plugins se alojan en la carpeta `wp-content/plugins/`.
- Accede a:
  ```
  http://azucar.dl/wp-content/plugins/
  ```
- Verás una página en blanco, lo cual es normal porque WordPress no lista los plugins directamente.

### 3.2 Archivos `readme.txt`
- Cada plugin suele incluir un archivo `readme.txt` en su directorio.
- Si el plugin existe, puedes acceder a este archivo con la ruta:
  ```
  http://azucar.dl/wp-content/plugins/<nombre-plugin>/readme.txt
  ```
- Ejemplos:
  - **Plugin inexistente**: `http://azucar.dl/wp-content/plugins/fdf/readme.txt` → Error 404.
  - **Plugin existente**: `http://azucar.dl/wp-content/plugins/site-editor/readme.txt` → Muestra el contenido del archivo, incluyendo la versión del plugin (por ejemplo, "Stable tag: 1.1").

### 3.3 Objetivo
- Automatizaremos este proceso con Python para probar una lista de plugins y determinar cuáles están instalados en el WordPress objetivo.

---

## Paso 4: Desarrollo del Script en Python

### 4.1 Preparación del Entorno de Desarrollo
1. **Abrir Visual Studio Code**:
   - En Kali Linux, abre Visual Studio Code (o tu editor preferido):
     ```bash
     code .
     ```

2. **Crear un Nuevo Archivo**:
   - Crea un archivo llamado `enum_plugins.py`.

### 4.2 Código Inicial
Comenzaremos con un script básico que prueba una lista de plugins.

#### Código:
```python
import requests

# Lista de plugins a comprobar
plugins = (
    "jetpack",
    "akismet",
    "contact-form-7",
    "woocommerce",
    "wordfence",
    "yoast-seo",
    "elementor",
    "w3-total-cache",
    "updraftplus",
    "wpforms",
    "site-editor"
    # Puedes añadir más plugins aquí...
)

# URL base
base_url = "http://172.17.0.2/wp-content/plugins/"

def check_plugin(plugin):
    url = f"{base_url}{plugin}/readme.txt"
    response = requests.get(url)
    if response.status_code == 200:
        print(f"[+] Plugin encontrado: {plugin}")
    else:
        pass

# Iterar sobre cada plugin
for plugin in plugins:
    check_plugin(plugin)
```

#### Explicación:
- **Librería `requests`**: Permite hacer peticiones HTTP.
- **Tupla `plugins`**: Contiene nombres de plugins comunes. Para este ejemplo, usamos una lista corta, pero idealmente debería incluir cientos o miles de plugins (puedes obtener listas de internet o bases de datos como la de WPScan).
- **URL Base**: La ruta común donde se alojan los plugins.
- **Función `check_plugin`**: Construye la URL completa y verifica si el `readme.txt` existe (código 200).
- **Bucle**: Itera sobre cada plugin y ejecuta la función.

### 4.3 Ejecución Inicial
1. **Guardar el Archivo**:
   - Guarda el script como `enum_plugins.py`.

2. **Ejecutar**:
   - En la terminal:
     ```bash
     python3 enum_plugins.py
     ```
   - Resultado esperado (si "site-editor" está instalado):
     ```
     [+] Plugin encontrado: site-editor
     ```

### 4.4 Mejora del Script
El script inicial solo indica qué plugins existen, pero no proporciona la URL del `readme.txt` para inspeccionar manualmente. Vamos a mejorarlo.

#### Código Mejorado:
```python
import requests

# Lista de plugins a comprobar
plugins = (
    "jetpack",
    "akismet",
    "contact-form-7",
    "woocommerce",
    "wordfence",
    "yoast-seo",
    "elementor",
    "w3-total-cache",
    "updraftplus",
    "wpforms",
    "site-editor"
    # Puedes añadir más plugins aquí...
)

# URL base
base_url = "http://172.17.0.2/wp-content/plugins/"

def check_plugin(plugin):
    url = f"{base_url}{plugin}/readme.txt"
    response = requests.get(url)
    if response.status_code == 200:
        print(f"[+] Plugin encontrado: {plugin}")
        print(f"Debes insertar esta url: {url}")
    else:
        pass

# Iterar sobre cada plugin
for plugin in plugins:
    check_plugin(plugin)
```

#### Cambios:
- **Mensaje Adicional**: Si se encuentra un plugin, se imprime la URL completa del `readme.txt`.

3. **Ejecutar de Nuevo**:
   - Corre el script:
     ```bash
     python3 enum_plugins.py
     ```
   - Resultado:
     ```
     [+] Plugin encontrado: site-editor
     Debes insertar esta url: http://172.17.0.2/wp-content/plugins/site-editor/readme.txt
     ```

---

## Paso 5: Verificación Manual
1. **Copiar la URL**:
   - Copia la URL proporcionada: `http://172.17.0.2/wp-content/plugins/site-editor/readme.txt`.

2. **Acceder en el Navegador**:
   - Pégala en el navegador y presiona Enter.
   - Verás el contenido del `readme.txt`, que incluye la versión del plugin (por ejemplo, "Stable tag: 1.1").

---

## Paso 6: Investigación de Vulnerabilidades
1. **Buscar Exploits**:
   - Con el nombre y versión del plugin ("site-editor 1.1"), busca en Google:
     ```
     site-editor 1.1 exploit
     ```
   - Encuentras que este plugin es vulnerable a un **Local File Inclusion (LFI)**.

2. **Explotación (Ejemplo)**:
   - Supongamos que el exploit requiere una URL como:
     ```
     http://172.17.0.2/wp-content/plugins/site-editor/editor.php?file=../../../../etc/passwd
     ```
   - Accede a esta URL en el navegador.
   - Si funciona, podrías ver el contenido del archivo `/etc/passwd` de la máquina, demostrando la vulnerabilidad.

**Nota**: La explotación está fuera del alcance de este tutorial y solo debe realizarse en entornos controlados con permiso explícito.

---

## Paso 7: Limpieza
1. **Detener la Máquina**:
   - En la terminal donde desplegaste "Azucar", presiona `Ctrl+C`.
   - Esto detiene y elimina la máquina de Docker, limpiando el entorno.

---

## Conclusión
Hemos creado un script en Python que:
- Enumera plugins instalados en un WordPress comprobando la existencia de archivos `readme.txt`.
- Proporciona las URLs para inspeccionar manualmente los plugins encontrados.
- Facilita la identificación de vulnerabilidades al revelar versiones de plugins.

Este proceso demuestra cómo técnicas simples de automatización con Python pueden ser poderosas en ciberseguridad. Recuerda practicar estas habilidades de manera ética y en entornos autorizados como Docker Labs.

---

## Código Resumido
```python
import requests

# Lista de plugins a comprobar
plugins = (
    "jetpack",
    "akismet",
    "contact-form-7",
    "woocommerce",
    "wordfence",
    "yoast-seo",
    "elementor",
    "w3-total-cache",
    "updraftplus",
    "wpforms",
    "site-editor"
    # Añade más plugins según necesites
)

# URL base (ajusta según la IP de tu máquina)
base_url = "http://172.17.0.2/wp-content/plugins/"

def check_plugin(plugin):
    url = f"{base_url}{plugin}/readme.txt"
    response = requests.get(url)
    if response.status_code == 200:
        print(f"[+] Plugin encontrado: {plugin}")
        print(f"Debes insertar esta url: {url}")
    else:
        pass

# Iterar sobre cada plugin
for plugin in plugins:
    check_plugin(plugin)
```


## Código Completo
````python

import requests
# Incluimos todos los plugins que queramos comprobar (si no está en esta tupla, no lo va a encontrar)

plugins = (

"jetpack",

"akismet",

"contact-form-7",

"woocommerce",

"wordfence",

"yoast-seo",

"elementor",

"w3-total-cache",

"updraftplus",

"wpforms",

"all-in-one-seo-pack",

"google-analytics-for-wordpress",

"really-simple-ssl",

"wordfence-security",

"classic-editor",

"disable-comments",

"smush",

"mailchimp-for-wp",

"redirection",

"shortpixel-image-optimizer",

"duplicate-post",

"monsterinsights",

"tablepress",

"ninja-forms",

"wp-optimize",

"broken-link-checker",

"cookie-notice",

"advanced-custom-fields",

"the-events-calendar",

"easy-wp-smtp",

"seo-press",

"elementor-pro",

"rank-math",

"wp-rocket",

"bbpress",

"buddypress",

"wp-super-cache",

"mailpoet",

"yoast-seo-premium",

"ultimate-member",

"woocommerce-subscriptions",

"wp-job-manager",

"regenerate-thumbnails",

"revslider",

"revive-old-post",

"wp-fastest-cache",

"simple-301-redirects",

"wordfence-login-security",

"wp-smush-pro",

"ithemes-security",

"nextgen-gallery",

"wp-migrate-db",

"duplicator",

"really-simple-captcha",

"autoptimize",

"social-media-widget",

"add-to-any",

"disqus-comment-system",

"broken-link-manager",

"pretty-link",

"simple-tags",

"advanced-excerpt",

"better-click-to-tweet",

"wp-polls",

"wordpress-popular-posts",

"ad-inserter",

"wp-mail-smtp",

"easy-digital-downloads",

"give",

"loco-translate",

"bbpress",

"buddypress",

"sucuri-scanner",

"envira-gallery",

"soliloquy",

"my-calendar",

"wp-google-maps",

"custom-post-type-ui",

"members",

"query-monitor",

"theme-check",

"user-role-editor",

"woocommerce-gateway-stripe",

"woocommerce-services",

"yith-woocommerce-wishlist",

"yith-woocommerce-compare",

"simple-share-buttons-adder",

"the-events-calendar-pro",

"under-construction-page",

"wp-optimize-premium",

"backupbuddy",

"wp-all-import",

"wp-offload-media",

"wp-all-export",

"ultimate-social-media-icons",

"real-cookie-banner",

"litespeed-cache",

"loginizer",

"under-construction",

"wp-maintenance-mode",

"hummingbird-performance",

"push-engage",

"easy-social-share-buttons",

"post-smtp",

"advanced-custom-fields-pro",

"google-site-kit",

"amp",

"autoptimize",

"better-wp-security",

"blubrry-powerpress",

"contact-form-7-datepicker",

"easy-affiliate-links",

"easy-theme-and-plugin-upgrades",

"insert-headers-and-footers",

"mc4wp-mailchimp-for-wordpress",

"post-types-order",

"restrict-content-pro",

"simple-history",

"simple-local-avatars",

"simple-sitemap",

"simple-social-icons",

"smush-pro",

"social-icons-widget-by-wpzoom",

"the-events-calendar-shortcode",

"the-seo-framework",

"updraftplus-premium",

"wp-cfm",

"wp-rollback",

"wp-user-avatar",

"wp-user-frontend",

"yith-woocommerce-ajax-search",

"yith-woocommerce-ajax-product-filter",

"yith-woocommerce-quick-view",

"yith-woocommerce-request-a-quote",

"yith-woocommerce-catalog-mode",

"yith-woocommerce-badge-management",

"yith-woocommerce-compare",

"yith-woocommerce-featured-video",

"yith-woocommerce-questions-and-answers",

"yith-woocommerce-product-bundles",

"yith-woocommerce-product-gallery-magnifier",

"yith-woocommerce-tab-manager",

"yith-woocommerce-wishlist",

"yoast-comment-hacks",

"wordfence-central",

"wp-mail-bank",

"wp-multibyte-patch",

"wp-photo-album-plus",

"wp-postratings",

"wp-recipe-maker",

"wp-review",

"wp-simple-firewall",

"wp-staging",

"wp-statistics",

"wp-super-cache",

"wp-to-buffer",

"wp-to-twitter",

"wp-tune-up",

"wp-ulike",

"wp-useronline",

"wp-webhooks",

"wp-whatsapp-button",

"wp-whatsapp-chat",

"wp-wpbakery-page-builder",

"wpcf7-mailchimp-extension",

"wpcf7-redirect",

"wpcf7-recaptcha",

"wpcf7-submission",

"wpcf7-to-database-extension",

"wpcf7-wpml",

"wpeverest-user-registration",

"wpforms-constant-contact",

"wpforms-drip",

"wpforms-form-abandonment",

"wpforms-mailchimp",

"wpforms-marketing-campaigns",

"wpforms-uploads",

"wpml-translation-management",

"wp-offload-s3",

"wp-offload-ses",

"wpmudev-upfront-builder",

"wpmudev-snapshot",

"wpmudev-smartcrawl",

"wpmudev-marketpress",

"wpmudev-bp-activity",

"wpmudev-bp-group-calendar",

"wpmudev-bp-group-documents",

"wpmudev-bp-group-email",

"wpmudev-bp-group-hierarchy",

"wpmudev-bp-group-organizer",

"wpmudev-bp-groupblog",

"wpmudev-bp-links",

"wpmudev-bp-livestream",

"wpmudev-bp-lockdown",

"wpmudev-bp-mass-messaging",

"wpmudev-bp-polls",

"wpmudev-bp-privacy",

"wpmudev-bp-simple-events",

"wpmudev-bp-social",

"wpmudev-bp-social-media",

"wpmudev-bp-translate",

"wpmudev-bp-twitter",

"wpmudev-bp-user-profile-completion",

"wpmudev-bp-user-profile-fields",

"wpmudev-bp-user-profile-visibility",

"wpmudev-bp-user-status",

"wpmudev-bp-xprofile-custom-fields",

"wpmudev-coursepress",

"wpmudev-dashboard",

"wpmudev-defender",

"wpmudev-domain-mapping",

"wpmudev-edd-pushover",

"wpmudev-e-newsletter",

"wpmudev-events-plus",

"wpmudev-facebook",

"wpmudev-friends",

"wpmudev-gridbuilder",

"wpmudev-hivepress",

"wpmudev-hummingbird",

"wpmudev-infinite-sessions",

"wpmudev-login-safety",

"wpmudev-membership",

"wpmudev-membership-premium",

"wpmudev-membership-ultimate",

"wpmudev-membership2",

"wpmudev-multisite-privacy",

"wpmudev-pro-sites",

"wpmudev-qa",

"wpmudev-qtranslate-x",

"wpmudev-reports",

"wpmudev-saml",

"wpmudev-saml-service-provider",

"wpmudev-simple-css",

"wpmudev-single-sign-on",

"wpmudev-smartsso",

"wpmudev-support",

"wpmudev-support-system",

"wpmudev-tips",

"wpmudev-tutoring",

"wpmudev-unlimited-smtp",

"wpmudev-upfront",

"wpmudev-upfront-contact",

"wpmudev-upfront-media",

"wpmudev-upfront-parallax",

"wpmudev-upfront-portfolio",

"wpmudev-upfront-posts",

"wpmudev-upfront-starter",

"wpmudev-upfront-studio",

"wpmudev-upfront-symbiostock",

"wpmudev-upfront-widgets",

"wpmudev-user-blogs",

"wpmudev-widgets-for-sitebuilder",

"wpmudev-wp-blogandplugin",

"wpmudev-wp-user-control",

"wpmudev-wp-usercontrol",

"wpmudev-wpmudev",

"wpmudev-wunderplugin",

"wp-optimize-premium"

"revslider",

"visual-composer",

"wp-statistics",

"userpro",

"gravityforms",

"all-in-one-wp-migration",

"duplicator",

"wpfastestcache",

"ninja-forms",

"wordfence",

"wp-file-manager",

"file-manager",

"file-manager-advanced",

"download-manager",

"wp-easycart",

"wp-ultimate-csv-importer",

"wp-job-manager",

"wpdiscuz",

"wordfence",

"formidable",

"brizy",

"site-editor",

"wpdatatables",

"members",

"real-estate-7",

"wp-mail-smtp",

"woo-gutenberg-products-block",

"essential-addons-for-elementor-lite",

"paid-memberships-pro",

"wp-customer-area",

"slider-hero",

"simple-301-redirects",

"yith-woocommerce-gift-cards",

"wpmu-dev-facebook",

"wpmu-dev-chat",

"wpmu-dev-defender",

"wpmu-dev-dashboard",

"wpmu-dev-forminator",

"wpmu-dev-membership-2",

"wpmu-dev-hummingbird",

"wpmu-dev-ibbu",

"wpmu-dev-mailchimp",

"wpmu-dev-snapshot",

"wpmu-dev-support",

"wpmu-dev-upfront",

"wpmu-dev-vc-templating",

"wpmu-dev-videopress",

"wpmu-dev-wp-forminator"

)

  

# URL base

base_url = "http://172.17.0.2/wp-content/plugins/"

  

def check_plugin(plugin):

url = f"{base_url}{plugin}/readme.txt"

response = requests.get(url)

if response.status_code == 200:

print(f"[+] Plugin encontrado: {plugin}")

print(f"Debes insertar esta url: {base_url}{plugin}/readme.txt") #lo termino despues...

else:

pass

  

# Iterar sobre cada plugin para ver si existe (Si existe lo envía a la función)

for plugin in plugins:

check_plugin(plugin)
`````



