---
tipo: teoria
tags: [administracion-sistemas, bash, devops, ejptv2, el-hacker-legendario, httpserver, linux, networking, python, python3, servidor-web, web-development]
actualizado: 2026-05-28
---

# Transferencia de Archivos por la Red

---
```python
python3 -m http.server 80
```

El comando `python3 -m http.server 80` se utiliza para iniciar un servidor web HTTP simple en el puerto 80 utilizando Python. A continuación, desgloso cada parte del comando:

### 1. **`python3`**

- Llama al intérprete de Python 3 para ejecutar el comando.
- Asegura que estás utilizando Python versión 3 (no Python 2, que está obsoleto).

### 2. **`-m http.server`**

- `-m`: Ejecuta un módulo como un script.
- `http.server`: Es el módulo estándar de Python que implementa un servidor HTTP básico.
    - Sirve archivos y directorios desde el directorio actual (donde ejecutas el comando) a través de HTTP.

### 3. **`80`**

- Especifica el puerto en el que el servidor escuchará las solicitudes HTTP.
- El puerto 80 es el puerto predeterminado para HTTP.
    - **Nota:** En sistemas operativos basados en Unix/Linux, es posible que necesites permisos de administrador para usar puertos menores a 1024. Puedes usar `sudo` si recibes un error de permiso denegado, así:
    
    -"sudo python3 -m http.server 80"
    
### Resultado del Comando

Cuando ejecutas este comando:

1. **Inicia un servidor web** en el directorio actual.
2. Los archivos y subdirectorios del directorio actual estarán disponibles públicamente a través del navegador web en la dirección `http://<tu-ip-o-hostname>:80/`.


**[[5- Cómo Utilizar WGET]]**
**[[4- Cómo Utilizar CURL con HTTP]]**
**[[3- Securización de Servidores Web Apache – PARTE 1]]**
**[[4- Gestión y Automatización de Servidores FTP – PARTE 2]]**.

---

## Navegación

- ⬆️ Carpeta: [[_1- Uso Básico de Linux|1- Uso Básico de Linux]]
- ⬅️ Anterior: [[2- Gestión de Paquetes – APT y DPKG]]
- ➡️ Siguiente: [[4- Cómo Utilizar CURL con HTTP]]
