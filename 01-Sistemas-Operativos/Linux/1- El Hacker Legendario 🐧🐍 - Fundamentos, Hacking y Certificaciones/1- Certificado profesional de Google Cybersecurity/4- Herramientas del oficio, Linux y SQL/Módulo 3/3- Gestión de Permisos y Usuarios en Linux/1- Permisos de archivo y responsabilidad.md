
# 📂 Permisos de archivo y responsabilidad – Linux

## 📌 Conceptos clave

- **Permisos** → Tipo de acceso concedido a un archivo o directorio.
    
- **Autorización** → Conceder acceso a recursos específicos en un sistema.
    
- Regla general: **dar el acceso mínimo necesario** para reducir riesgos.
    

---

## 🔑 Tipos de permisos

1. **Lectura (r)**
    
    - Archivos → leer su contenido.
        
    - Directorios → listar los archivos que contiene.
        
2. **Escritura (w)**
    
    - Archivos → modificar el contenido.
        
    - Directorios → crear o eliminar archivos dentro.
        
3. **Ejecución (x)**
    
    - Archivos → ejecutarlo (si es ejecutable).
        
    - Directorios → acceder a su contenido.
        

---

## 👥 Tipos de propietarios

- **Usuario (u)** → propietario del archivo.
    
- **Grupo (g)** → conjunto de usuarios con acceso común.
    
- **Otros (o)** → todos los demás usuarios del sistema.
    

---

## 🖋 Representación de permisos

- Cadena de **10 caracteres** → ejemplo:
    
    ```
    drwxrwxrwx
    ```
    
    - **1º caracter** → tipo de archivo (`d` directorio, `-` archivo normal).
        
    - **2º-4º** → permisos del usuario (u).
        
    - **5º-7º** → permisos del grupo (g).
        
    - **8º-10º** → permisos de otros (o).
        
- Guiones (`-`) indican permiso no otorgado.
    

---

## ⚠ Riesgos de seguridad

- **Archivos de nóminas** → no deben ser legibles por otros.
    
- **Archivos escribibles por todos** (`-rw-rw-rw-`) → alto riesgo de manipulación.
    

---

## 🛠 Comandos útiles para ver permisos

- **Listar con detalles:**
    
    ```bash
    ls -l
    ```
    
- **Incluir archivos ocultos:**
    
    ```bash
    ls -a
    ```
    
- **Combinado:**
    
    ```bash
    ls -la
    ```
    

---

## 📌 Ejemplo interpretación

```
-rw-r--r--
```

- Usuario: `rw-` → lectura y escritura.
    
- Grupo: `r--` → sólo lectura.
    
- Otros: `r--` → sólo lectura.
    

---

## 🎯 Importancia en seguridad

- Supervisar y ajustar permisos es esencial para proteger información.
    
- Mantener privilegios mínimos reduce exposición y posibles abusos.
    

---
