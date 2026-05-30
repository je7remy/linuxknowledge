---
tipo: teoria
tags: [recursos-amenazas-y-vulnerabilidades, seguridad-en-aplicaciones-web, sistemas-operativos]
actualizado: 2026-05-30
---

## Cómo las aplicaciones usan SQL

- Los sitios web no suelen hacer que los usuarios escriban consultas SQL manualmente.
    
- En su lugar, utilizan elementos como **menús, imágenes y botones** para que las acciones del usuario desencadenen consultas en segundo plano.
    
- Por ejemplo, cuando un comprador en línea hace clic en un botón para añadir un jersey a su cesta, se desencadena una consulta SQL que se ejecuta en el backend.
    

A veces esas consultas backend son **vulnerables** a ataques de inyección.

---

## ¿Qué es una inyección de SQL?

Una **inyección de SQL** es un ataque que **ejecuta consultas inesperadas en una base de datos**. Al igual que la XSS, la inyección de SQL se produce debido a una **falta de desinfección (saneamiento) de la entrada**.

Las inyecciones ocurren en áreas del sitio web diseñadas para aceptar entrada del usuario (formularios, campos de búsqueda, parámetros en la URL, etc.). Un ejemplo típico es **el formulario de inicio de sesión**.

---

## Por qué ocurren las inyecciones

- Muchos sitios copian la entrada del usuario **tal cual** en una sentencia SQL backend y la ejecutan.
    
- Esto es un **fallo de diseño**: los desarrolladores a menudo esperan que los usuarios introduzcan datos correctamente y no prevén entradas maliciosas.
    
- Un atacante puede inyectar **código SQL adicional** en esos campos. Si la aplicación no lo maneja, el servidor ejecutará consultas dañinas no previstas.
    

---

## Impacto de una inyección de SQL

Los atacantes pueden, por ejemplo:

- Obtener información sensible (credenciales, datos personales).
    
- Modificar tablas (insertar, actualizar o borrar información).
    
- Obtener **privilegios administrativos** sobre la base de datos.
    

---

## Cómo defenderse: saneamiento de entrada y buenas prácticas

La mejor forma de defenderse contra la inyección de SQL es **escribir código que sanee la entrada** y utilice técnicas seguras:

- **Validar y sanear entradas**: buscar y filtrar caracteres peligrosos o patrones no esperados.
    
- **Sentencias preparadas (prepared statements)**:
    
    - Técnica que separa el código SQL de los datos.
        
    - Se prepara la sentencia con marcadores de posición antes de pasar los datos a la base de datos.
        
    - Permite validar y normalizar la entrada antes de ejecutar la consulta.
        
    - Es la práctica recomendada cuando la entrada del usuario es desconocida.
        

Con unas pocas líneas adicionales, las sentencias preparadas ayudan a evitar que la entrada maliciosa altere la estructura de la consulta SQL.

---

## Trabajo en equipo: seguridad y desarrollo

- Tener **código bien escrito** es clave para prevenir la inyección de SQL.
    
- Los equipos de seguridad deben **trabajar con desarrolladores** para probar las aplicaciones (pentesting, análisis dinámico/estático) y encontrar vulnerabilidades.
    
- La seguridad es **responsabilidad compartida**: desarrolladores, testers y analistas deben coordinarse.
    

---

## Cierre

Los ataques de inyección son solo uno de los muchos tipos de exploits basados en web a los que se enfrentan los equipos de seguridad. Prepararse implica buenas prácticas de desarrollo, pruebas continuas y colaboración estrecha entre equipos.

### ❓ Pregunta

**Rellene el espacio en blanco:**  
A(n) _____ es un ataque que ejecuta consultas inesperadas en una base de datos.

- software malicioso
    
- virus
    
- **inyección de SQL** ✅
    
- CVE
    

---

### ✔️ Respuesta Correcta

**Inyección de SQL**

👉 Una inyección de SQL es un ataque que ejecuta **consultas inesperadas en una base de datos**.

- Suele ocurrir en áreas del sitio web que aceptan **entradas de usuarios** (formularios, campos de búsqueda, URL con parámetros).
    
- Los atacantes aprovechan entradas mal validadas para manipular las consultas SQL y obtener acceso a datos sensibles.
    

---
## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ⬅️ Anterior: [[1- Escritura de secuencias de comandos entre sitios (XSS)]]
- ➡️ Siguiente: [[3- Prevenir ataques de inyección]]
