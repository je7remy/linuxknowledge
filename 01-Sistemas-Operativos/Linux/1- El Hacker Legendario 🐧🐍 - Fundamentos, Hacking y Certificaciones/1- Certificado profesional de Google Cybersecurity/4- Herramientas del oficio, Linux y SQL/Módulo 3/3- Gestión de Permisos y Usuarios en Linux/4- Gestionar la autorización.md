
````markdown
# Administra Autorizaciones - Guía Didáctica

## Objetivo
Aprender a verificar y modificar permisos de archivos y directorios en Linux para reforzar la seguridad.

## Comandos Clave
- `ls -l` → Lista archivos con permisos.
- `ls -la` → Lista incluyendo archivos ocultos.
- `ls -ld <directorio>` → Muestra permisos de un directorio.
- `chmod` → Cambia permisos.

## Procedimiento

### 1. Verificar permisos
```bash
ls -l
ls -la
````

### 2. Corregir permisos de archivos

- Quitar escritura a “otros” en `project_k.txt`:
    

```bash
chmod o-w project_k.txt
```

- Quitar lectura y escritura al grupo en `project_m.txt`:
    

```bash
chmod g-rw project_m.txt
```

### 3. Ajustar permisos en archivo oculto

- Quitar escritura a usuario y grupo en `.project_x.txt`:
    

```bash
chmod u-w,g-w .project_x.txt
```

### 4. Restringir acceso a un directorio

- Quitar ejecución al grupo en `drafts`:
    

```bash
chmod g-x drafts
```

## Resultado Esperado

- Permisos alineados con políticas de seguridad.
    
- Acceso limitado a quien corresponda.