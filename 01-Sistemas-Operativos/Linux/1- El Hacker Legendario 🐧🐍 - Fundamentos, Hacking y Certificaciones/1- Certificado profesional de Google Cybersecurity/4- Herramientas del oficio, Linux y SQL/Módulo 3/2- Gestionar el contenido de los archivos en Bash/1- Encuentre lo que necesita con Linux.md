---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-3]
actualizado: 2026-05-28
---

# Encuentre lo que necesita con Linux

## 🧠 Conceptos Clave

### 1. **Filtrado con `grep`**

- **`grep`** busca líneas en un archivo que contienen una cadena específica.
    
- **Sintaxis:**
    
    ```bash
    grep <cadena> <archivo>
    ```
    
- **Ejemplo:**
    
    ```bash
    grep OS updates.txt
    ```
    
    Este comando devolverá todas las líneas de `updates.txt` que contienen la palabra "OS".
    

---

### 2. **Piping (`|`)**

- El símbolo **`|`** (barra vertical) **envía la salida de un comando como entrada a otro**.
    
- Se utiliza comúnmente para encadenar comandos y aplicar filtros.
    
- **Ejemplo:**
    
    ```bash
    ls reports | grep users
    ```
    
    - `ls reports` lista los archivos del directorio `reports`.
        
    - Esa lista se **filtra** con `grep users`, que solo muestra los elementos que contienen la palabra `users`.
        

---

## 💻 Demostración Práctica

### Ver todo el contenido de un directorio:

```bash
ls reports
```

### Filtrar contenido que contiene una palabra específica:

```bash
ls reports | grep users
```

> Esto es útil para buscar archivos o subdirectorios que coincidan con un patrón sin tener que leer todo el listado.

---

## 🧰 ¿Por qué esto es útil como analista de seguridad?

- Puedes:
    
    - Buscar patrones maliciosos en archivos de registro (`.log`).
        
    - Verificar configuraciones específicas.
        
    - Identificar archivos relacionados con malware.
        
    - Automatizar tareas de análisis en grandes volúmenes de archivos.
        

---

## 🧪 Retos para practicar

1. Crea un archivo de prueba:
    
    ```bash
    echo -e "Linux\nWindows\nmacOS\nUbuntu\nDebian\nArch Linux" > systems.txt
    ```
    
2. Filtra con `grep`:
    
    ```bash
    grep Linux systems.txt
    ```
    
3. Usa `ls` con `grep`:
    
    ```bash
    mkdir testdir && cd testdir
    touch users1.txt admin_users.csv otherfile.txt
    ls | grep users
    ```
    

---
## Navegación

- ⬆️ Carpeta: [[_4- Herramientas del oficio, Linux y SQL|4- Herramientas del oficio, Linux y SQL]]
- ➡️ Siguiente: [[2- Filtrado de contenidos en Linux]]
