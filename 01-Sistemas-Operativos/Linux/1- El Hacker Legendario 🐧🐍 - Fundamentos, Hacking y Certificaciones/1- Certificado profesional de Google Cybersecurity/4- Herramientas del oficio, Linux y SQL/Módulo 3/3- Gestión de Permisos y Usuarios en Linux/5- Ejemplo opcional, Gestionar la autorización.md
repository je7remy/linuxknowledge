

````markdown
# Administra Autorizaciones - Guía Didáctica

## Objetivo
Aprender a verificar y modificar permisos de archivos, archivos ocultos y directorios en Linux para reforzar la seguridad.

## Comandos Clave
- `ls -l` → Lista archivos con permisos.
- `ls -la` → Lista incluyendo archivos ocultos.
- `ls -ld <directorio>` → Muestra permisos de un directorio.
- `chmod` → Cambia permisos.

---

## Procedimiento por Tarea

### **Tarea 1: Verificar detalles de archivos y directorios**
1. Ir al directorio:
```bash
cd projects
````

2. Listar permisos:
    

```bash
ls -l
```

3. Verificar archivos ocultos:
    

```bash
ls -la
```

- **Grupo propietario**: `research_team` ✅
    
- **Archivo oculto**: `.project_x.txt` ✅
    

---

### **Tarea 2: Cambiar permisos de archivos**

1. Detectar archivo con escritura para "otros": `project_k.txt` ✅
    
2. Quitar escritura a "otros":
    

```bash
chmod o-w project_k.txt
```

3. Restringir `project_m.txt` para que el grupo no tenga lectura ni escritura:
    

```bash
chmod g-r project_m.txt
```

- **Permisos grupales previos en `project_m.txt`**: Solo lectura ✅
    

---

### **Tarea 3: Cambiar permisos de archivo oculto**

1. Verificar permisos:
    

```bash
ls -la
```

2. Quitar escritura a usuario y grupo, asegurando lectura:
    

```bash
chmod u-w,g-w,g+r .project_x.txt
```

- **Propietario con escritura incorrecta**: Usuario y grupo ✅
    

---

### **Tarea 4: Cambiar permisos de un directorio**

1. Verificar permisos:
    

```bash
ls -ld drafts
```

- **Grupo con acceso**: Sí ✅
    

2. Quitar ejecución al grupo:
    

```bash
chmod g-x drafts
```

---

## Resultado Final

- Permisos ajustados a las políticas de seguridad.
    
- Archivos y directorio `drafts` protegidos contra accesos no autorizados.
    
- Archivos ocultos revisados y configurados correctamente.
    

---
