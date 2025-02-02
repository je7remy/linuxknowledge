

---

### **1. `zip -r archivos.zip *.txt`**

- Este comando crea un archivo comprimido llamado `archivos.zip` e incluye en él **todos los archivos con extensión `.txt`** del directorio actual.
- **Resultado:**
    - Si hay archivos `.txt` en el directorio actual, estos serán añadidos al archivo `archivos.zip`.
    - Si no hay archivos `.txt`, el comando no hará nada o mostrará un mensaje indicando que no encontró coincidencias.

---

### **2. `zip -r archivos.zip *`**

- Este comando actualiza el archivo `archivos.zip` e incluye **todo el contenido del directorio actual** (archivos y subdirectorios), **sin eliminar lo que ya estaba dentro del archivo zip**.
- **Resultado:**
    - Ahora, `archivos.zip` contiene los archivos `.txt` del paso anterior **más** todo el resto del contenido del directorio actual, como otros archivos y carpetas.

---

### **3. `unzip archivos.zip`**

- Este comando extrae el contenido del archivo comprimido `archivos.zip` en el directorio actual.
- **Resultado:**
    - Todos los archivos y carpetas dentro de `archivos.zip` se copian al directorio actual.
    - Si ya existen archivos con los mismos nombres, el comando pedirá confirmación para sobrescribirlos (a menos que uses opciones como `-o` para sobrescribir automáticamente).

---

### **4. `zip -r fotos.zip *.jpg`**

- Este comando crea un archivo comprimido llamado `fotos.zip` y agrega a él todos los archivos con la extensión `.jpg` del directorio actual y de cualquier subdirectorio.
- **Resultado:**
    - `fotos.zip` contendrá únicamente los archivos `.jpg`.

---

### Nota importante:

El uso repetido de `zip -r` puede generar archivos duplicados en un mismo `.zip` si ejecutas los comandos varias veces con diferentes opciones. Es recomendable verificar el contenido de los `.zip` con:

```bash
unzip -l archivos.zip
unzip -l fotos.zip
```

Esto te mostrará la lista de archivos comprimidos en cada archivo `.zip`.
