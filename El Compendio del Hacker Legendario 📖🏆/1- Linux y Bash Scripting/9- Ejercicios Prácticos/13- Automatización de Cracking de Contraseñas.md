### 1️⃣ **Explicación del Código**

El script recibe dos argumentos:

- **archivo** → el archivo comprimido o base de datos a atacar (.zip, .rar, .kdbx)
- **wordlist** → el diccionario de palabras a utilizar para la fuerza bruta

#### 🔹 **Paso 1: Validación de argumentos**

```bash
if [ $# -ne 2 ]; then
    echo "Uso: <archivo> <wordlist>"
    exit 1
fi
```

Si el usuario no pasa exactamente dos argumentos, se muestra el mensaje de uso y el script se detiene.

#### 🔹 **Paso 2: Definir variables**

```bash
archivo=$1
wordlist=$2
```

Se almacenan los argumentos en variables.

#### 🔹 **Paso 3: Extracción de Hashes**

```bash
case "$archivo" in
    *.kdbx)
        keepass2john "$archivo" > hash
        ;;
    *.zip)
        zip2john "$archivo" > hash
        ;;
    *rar)
        rar2john "$archivo" > hash
        ;;
    *)
        echo "Archivo no compatible, solo .zip, .rar, .kdbx"
        exit 1
        ;;
esac
```

- Dependiendo de la extensión, se ejecuta la herramienta correspondiente:
    - `keepass2john` para archivos KeePass (.kdbx)
    - `zip2john` para archivos ZIP
    - `rar2john` para archivos RAR
- El hash resultante se guarda en un archivo llamado `hash`.

#### 🔹 **Paso 4: Ataque con John the Ripper**

```bash
john --wordlist="$wordlist" hash
john --show hash
```

- Se usa John con el diccionario de palabras para intentar descifrar la contraseña.
- Luego se muestra el resultado con `john --show`.

#### 🔹 **Paso 5: Limpieza**

```bash
rm hash
```

- Se elimina el archivo temporal `hash` al finalizar.

---

### 2️⃣ **Ejemplo de Ejecución**

```bash
./script.sh RDBGIGM.rar rockyou.txt
```

- Se pasa un archivo `.rar` y la lista `rockyou.txt` como diccionario.
- Si el RAR tiene contraseña débil contenida en `rockyou.txt`, se revelará.

---

### 3️⃣ **Posibles Errores y Soluciones**

1️⃣ **Error:** `zip2john: command not found`  
✅ Solución: Instala John the Ripper y sus herramientas auxiliares:

```bash
sudo apt install john
sudo apt install rar2john zip2john keepass2john
```

2️⃣ **Error:** `No password hashes loaded`  
✅ Solución: Asegúrate de que el archivo no está dañado y que realmente tiene contraseña.

3️⃣ **Error:** `Permission denied` al ejecutar el script  
✅ Solución: Dale permisos de ejecución:

```bash
chmod +x script.sh
```

---
