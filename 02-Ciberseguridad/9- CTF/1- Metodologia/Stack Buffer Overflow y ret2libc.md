---
tipo: teoria
tags: [ctf, pwn, stack-buffer-overflow, rop, ret2libc, aslr, nx, pwntools]
actualizado: 2026-10-18
---

# Stack Buffer Overflow y ret2libc

Un desbordamiento de búfer en pila escribe fuera de un objeto local. Si alcanza datos de control y las protecciones no lo impiden, puede modificar la dirección de retorno. El caso documentado en [[Writeup - SMBiablo]] combina esta corrupción con una filtración de una dirección de libc.

## Reconocimiento ELF y protecciones

`file` identifica formato y arquitectura. `checksec` resume protecciones; `nm`, `readelf` y `objdump` ayudan a localizar símbolos y leer instrucciones. La interpretación debe relacionarse con el flujo vulnerable, no quedarse en una lista de checks.

| Propiedad | Función | Caso SMBiablo |
|---|---|---|
| Stack canary | Detectar ciertas sobrescrituras antes del retorno | Ausente |
| NX | Evitar ejecución desde páginas de datos no ejecutables | Activado; se reutilizó código existente |
| PIE | Permitir reubicar el ejecutable principal | Desactivado; no implica que libc carezca de ASLR |
| ASLR | Aleatorizar ubicaciones de módulos y regiones | La filtración permitió calcular libc |
| RELRO | Endurecer estructuras de reubicación como GOT | Parcial; el ataque documentado lee GOT, no la sobrescribe |

## GOT, information leak y libc

La GOT contiene punteros utilizados en el enlace dinámico. En el reto, el comando SMB2 `0xFFFF` devolvió el puntero asociado a `printf`. Con el desplazamiento de la libc suministrada:

```text
base_libc = dirección_filtrada_printf - offset_printf
0x722580cd06f0 - 0x606f0 = 0x722580c70000
```

La alineación a página es una comprobación de coherencia, no una prueba suficiente por sí sola. Hay que asociar el offset con la biblioteca correcta y no reutilizar direcciones absolutas de otra ejecución.

## ROP y ret2libc

ROP reutiliza secuencias de instrucciones existentes (*gadgets*). Ret2libc dirige el control hacia funciones de libc; puede construirse mediante ROP. En la ABI System V x86-64, el primer argumento se pasa en RDI.

En SMBiablo se documentó:

```text
56 bytes hasta RIP
ret                 → ajuste de alineación
pop rdi; ret        → cargar el argumento
dirección /bin/sh    → cadena en libc
system              → función de libc
```

El contador de 48 dialectos originaba una copia de 96 bytes. El esquema anterior muestra la cadena descrita en la fuente, pero no reconstruye los bytes adicionales del paquete ausentes en el código conservado.

## pwntools y límites de evidencia

`ELF` permite consultar símbolos, `remote` representa el transporte y `p32`/`u32` empaquetan longitudes. En el fragmento de SMBiablo, el prefijo de longitud usa orden de bytes grande y los campos SMB2 se empaquetan con `struct` en orden pequeño. Son campos distintos y deben respetarse por separado.

El Word solo conserva la conexión, construcción básica de paquetes y lectura de la respuesta del leak. Faltan las etapas Python de ROP y desbordamiento; la shell y la flag constan en las salidas documentadas. La integración no ejecutó el exploit.

## Mitigación

Acotar cada copia al tamaño del destino y a la longitud real recibida; validar multiplicaciones y conteos. Eliminar filtraciones de punteros y habilitar canarios, PIE, NX y RELRO completo como medidas complementarias. Los hardenings no sustituyen la corrección del parser.

## Navegación

- ⬆️ Carpeta: [[_1- Metodologia]]
- ⬅️ Anterior: [[Reversing - de leer código fuente a desensamblar binarios]]

## Relacionadas

- [[Writeup - SMBiablo]] — evidencia, offsets y salidas del caso.
- [[GDB baby step 1]] — registros y lectura de ensamblador como base.
- [[9- SMB]] — contexto del protocolo; el bug pertenece al parser particular del reto.
- [[Writeup - Data Del Más Allá]] — contraste: investigar longitudes no basta para afirmar explotación de heap.
