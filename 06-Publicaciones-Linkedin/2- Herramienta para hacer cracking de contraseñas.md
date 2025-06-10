![[ChatGPT Image 9 jun 2025, 08_59_52 p.m..png]]


# Auditoría Ética de Contraseñas con Herramientas Seguras

## Introducción

Esta guía proporciona un enfoque ético y educativo para recuperar contraseñas de archivos protegidos (ZIP, KeePass, RAR) utilizando herramientas como `John the Ripper` en un entorno Linux. El objetivo es asistir en auditorías de seguridad autorizadas, permitiendo identificar contraseñas débiles y mejorar la protección de datos.

**Advertencia:** Solo realiza estas acciones en archivos de tu propiedad o con permiso explícito. El uso indebido puede violar leyes locales, como la Ley de Fraude y Abuso Informático (CFAA).

## Requisitos Previos

- Sistema operativo Linux (e.g., Ubuntu).
- Herramientas instaladas: `zip2john`, `keepass2john`, `rar2john`, y `john` (instalable con `sudo apt install john`).
- Wordlist (e.g., `rockyou.txt`, disponible en repositorios legales como Kali Linux).

## Procedimiento Paso a Paso

### 1. Recuperación de Contraseñas de Archivos ZIP

#### Generar el hash del archivo ZIP

```bash
zip2john archivo.zip > hash
```

**📌 Explicación:**  
`zip2john` extrae el hash del archivo ZIP protegido por contraseña y lo guarda en el archivo `hash`.

#### Romper la contraseña con John the Ripper

```bash
john --wordlist=rockyou.txt hash
```

**📌 Explicación:**  
`--wordlist=rockyou.txt` especifica la lista de palabras RockYou para intentar descifrar la contraseña. `hash` es el archivo que contiene el hash del ZIP.

#### Mostrar la contraseña encontrada

```bash
john --show hash
```

**📌 Explicación:**  
Muestra la contraseña recuperada si John the Ripper tuvo éxito.

---

### 2. Recuperación de Contraseñas de una Base de Datos KeePass (.kdbx)

#### Generar el hash del archivo KeePass

```bash
keepass2john database.kdbx > hash1
```

**📌 Explicación:**  
`keepass2john` convierte el archivo KeePass en un formato que John the Ripper puede entender.

#### Romper la contraseña con John the Ripper

```bash
john --wordlist=rockyou.txt hash1
```

**📌 Explicación:**  
Intenta descifrar la contraseña con el diccionario RockYou.

#### Mostrar la contraseña encontrada

```bash
john --show hash1
```

**📌 Explicación:**  
Muestra la contraseña de la base de datos KeePass si se encontró con éxito.

---

### 3. Recuperación de Contraseñas de Archivos RAR

#### Generar el hash del archivo RAR

```bash
rar2john "Agregar Microsoft Store Windows (SR. JANCELL).rar" > hash2
```

**📌 Explicación:**  
`rar2john` convierte el archivo RAR protegido en un hash compatible con John the Ripper.

#### Romper la contraseña con John the Ripper

```bash
john --wordlist=rockyou.txt hash2
```

**📌 Explicación:**  
Usa RockYou para tratar de descifrar la contraseña del archivo RAR.

#### Mostrar la contraseña encontrada

```bash
john --show hash2
```

**📌 Explicación:**  
Muestra la contraseña del archivo RAR si se encontró con éxito.

---

## Opciones Avanzadas

- **Fuerza bruta sin diccionario:**
  
  ```bash
  john --incremental hash
  ```

- **Usar múltiples hilos para acelerar el proceso:**
  
  ```bash
  john --fork=4 --wordlist=rockyou.txt hash
  ```

## Conclusión

Este proceso es útil para recuperar contraseñas olvidadas de archivos protegidos o realizar auditorías éticas. Es importante recordar que solo debes realizar este procedimiento en archivos de tu propiedad o con permiso explícito. Considera hacer respaldos antes de cualquier acción.

## Recursos Adicionales

- Repositorio con ejemplos: [github.com/je7remy/linuxknowledge](https://github.com/je7remy/linuxknowledge/blob/main/01-Sistemas-Operativos/Linux/1-%20El%20Hacker%20Legendario%20%F0%9F%90%A7%F0%9F%90%8D%20-%20Fundamentos%2C%20Hacking%20y%20Certificaciones/3-%20Preparaci%C3%B3n%20para%20la%20Certificaci%C3%B3n%20del%20eJPTv2/1-%20Curso%20de%20Linux%20y%20Bash%20Scripting/9-%20Ejercicios%20Pr%C3%A1cticos/12-%20Herramienta%20para%20hacer%20cracking%20de%20contrase%C3%B1as.md)

---
