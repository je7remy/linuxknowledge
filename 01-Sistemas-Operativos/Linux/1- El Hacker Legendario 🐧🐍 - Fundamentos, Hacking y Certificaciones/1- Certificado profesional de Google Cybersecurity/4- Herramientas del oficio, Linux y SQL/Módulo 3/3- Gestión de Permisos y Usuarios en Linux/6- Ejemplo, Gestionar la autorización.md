

````markdown
# Administra Autorizaciones - Ejemplo de Solución del Lab

## Escenario
En este laboratorio, se deben examinar y administrar los permisos de los archivos en el directorio `/home/researcher2/projects` para el usuario **researcher2**, miembro del grupo **research_team**.  
El objetivo es verificar y ajustar los permisos para cumplir con las políticas de seguridad, evitando accesos no autorizados tanto en archivos como en directorios, incluyendo archivos ocultos.

---

## **Tarea 1: Comprobar los detalles de archivos y directorios**

1. **Navegar al directorio `projects`:**
```bash
cd projects
````

2. **Listar contenido y permisos:**
    

```bash
ls -l
```

Salida inicial:

```
drwx--x--- 2 researcher2 research_team 4096 Oct 14 18:40 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Oct 14 18:40 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Oct 14 18:40 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 14 18:40 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 14 18:40 project_t.txt
```

- **Grupo propietario:** `research_team` ✅
    

3. **Verificar archivos ocultos:**
    

```bash
ls -la
```

- **Archivo oculto encontrado:** `.project_x.txt` ✅
    

---

## **Tarea 2: Cambiar los permisos de archivos**

1. **Detectar archivo con permisos de escritura para “otros”:**
    

```bash
ls -l
```

- Archivo identificado: `project_k.txt` ✅
    

2. **Quitar permiso de escritura a otros usuarios en `project_k.txt`:**
    

```bash
chmod o-w project_k.txt
```

3. **Restringir acceso al grupo en `project_m.txt`:**
    

- Permisos actuales del grupo: **Solo lectura** ✅
    
- Comando para quitar lectura y escritura:
    

```bash
chmod g-r project_m.txt
```

---

## **Tarea 3: Cambiar permisos de un archivo oculto**

1. **Verificar permisos de `.project_x.txt`:**
    

```bash
ls -la
```

- Propietarios con permisos de escritura incorrectos: **Usuario y grupo** ✅
    

2. **Quitar escritura a usuario y grupo, manteniendo lectura:**
    

```bash
chmod u-w,g-w,g+r .project_x.txt
```

---

## **Tarea 4: Cambiar los permisos de un directorio**

1. **Verificar permisos de `drafts`:**
    

```bash
ls -ld drafts
```

- El grupo tiene permisos de ejecución: **Sí** ✅
    

2. **Quitar ejecución al grupo:**
    

```bash
chmod g-x drafts
```

---

## **Conclusión**

Con estos pasos, se han completado las siguientes acciones:

- Verificar permisos de archivos y directorios.
    
- Quitar accesos no autorizados en archivos.
    
- Ajustar permisos de archivos ocultos.
    
- Restringir acceso a un directorio.
    

**Resultado:** El sistema queda más seguro al limitar el acceso solo a los usuarios y grupos autorizados.

