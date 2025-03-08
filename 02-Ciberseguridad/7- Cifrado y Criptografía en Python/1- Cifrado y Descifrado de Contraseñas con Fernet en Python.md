
---

#Python #Cifrado #Descifrado #Seguridad #Fernet #Cryptography #ContraseñasSeguras

---
### 📖 **Paso a Paso: Cifrado y Descifrado de Contraseñas con Fernet en Python**

En este tutorial, vamos a explorar cómo cifrar y descifrar contraseñas de manera segura utilizando **Fernet**, un sistema de cifrado simétrico proporcionado por la librería `cryptography`.

Este sistema permite que cualquier dato cifrado pueda ser descifrado con la misma clave, por lo que es fundamental mantener segura la clave generada.

---

## **🔹 PASO 1: Instalación de la Librería Necesaria**

Antes de comenzar, debemos instalar la librería `cryptography`, que contiene Fernet. Si aún no la tienes instalada, usa este comando:

```bash
pip install cryptography
```

---

## **🔹 PASO 2: Explicación del Proceso de Cifrado y Descifrado**

El proceso consta de tres elementos principales:

1️⃣ **Generación de Clave (`clave.key`)**

- Si la clave no existe, la generamos y la guardamos en un archivo.
- Esta clave será usada tanto para cifrar como para descifrar.

2️⃣ **Cifrado de la Contraseña (`encriptador.py`)**

- Se solicita al usuario una contraseña.
- Se usa la clave almacenada para cifrar la contraseña.
- El resultado cifrado se guarda en un archivo (`contraseña_cifrada.txt`).

3️⃣ **Descifrado de la Contraseña (`desencriptador.py`)**

- Se carga la clave almacenada.
- Se recupera la contraseña cifrada desde el archivo.
- Se usa la clave para descifrar y mostrar la contraseña original.

---

## **🔹 PASO 3: Código Explicado de `encriptador.py` (Cifrar Contraseña)**

Este código se encarga de **cifrar** una contraseña y guardarla en un archivo.

```python
from cryptography.fernet import Fernet  # Importamos Fernet para cifrado y descifrado

# Función para generar y guardar una clave en 'clave.key'
def generar_clave():
    key = Fernet.generate_key()  # Generamos una clave segura
    with open("clave.key", "wb") as file:  # Abrimos el archivo en modo escritura binaria
        file.write(key)  # Guardamos la clave en el archivo

# Función para cargar la clave almacenada
def cargar_clave():
    with open("clave.key", "rb") as file:  # Abrimos el archivo en modo lectura binaria
        return file.read()  # Retornamos la clave almacenada

# Función para cifrar una contraseña
def cifrar_contraseña(contraseña: str) -> bytes:
    key = cargar_clave()  # Cargamos la clave existente
    cipher = Fernet(key)  # Creamos el objeto de cifrado con la clave
    return cipher.encrypt(contraseña.encode())  # Ciframos la contraseña y la retornamos

# Si no existe la clave, la generamos
try:
    clave = cargar_clave()  # Intentamos cargar la clave
except FileNotFoundError:
    generar_clave()  # Si no existe, generamos una nueva
    clave = cargar_clave()  # Cargamos la nueva clave

# Solicitamos al usuario una contraseña
contraseña = input("Introduce la contraseña a cifrar: ")
contraseña_cifrada = cifrar_contraseña(contraseña)  # Ciframos la contraseña

# Guardamos la contraseña cifrada en un archivo
with open("contraseña_cifrada.txt", "wb") as file:
    file.write(contraseña_cifrada)  # Guardamos la contraseña cifrada en binario

print(f"Contraseña cifrada y guardada en 'contraseña_cifrada.txt':\n{contraseña_cifrada}")
```

📌 **¿Qué hace este código?**  
✅ Verifica si la clave `clave.key` existe; si no, la crea.  
✅ Pide al usuario una contraseña y la cifra con la clave.  
✅ Guarda la contraseña cifrada en un archivo llamado `contraseña_cifrada.txt`.

---

## **🔹 PASO 4: Código Explicado de `desencriptador.py` (Descifrar Contraseña)**

Este código **descifra** la contraseña guardada previamente.

```python
from cryptography.fernet import Fernet  # Importamos Fernet para descifrado

# Función para cargar la clave almacenada
def cargar_clave():
    with open("clave.key", "rb") as file:  # Abrimos el archivo en modo lectura binaria
        return file.read()  # Retornamos la clave almacenada

# Función para descifrar una contraseña
def descifrar_contraseña(contraseña_cifrada: bytes) -> str:
    key = cargar_clave()  # Cargamos la clave almacenada
    cipher = Fernet(key)  # Creamos el objeto de descifrado con la clave
    return cipher.decrypt(contraseña_cifrada).decode()  # Desciframos y retornamos la contraseña en texto

# Intentamos cargar la contraseña cifrada desde el archivo
try:
    with open("contraseña_cifrada.txt", "rb") as file:
        contraseña_cifrada = file.read()  # Leemos la contraseña cifrada

    contraseña_descifrada = descifrar_contraseña(contraseña_cifrada)  # Desciframos la contraseña
    print(f"Contraseña original: {contraseña_descifrada}")  # Mostramos la contraseña descifrada

except FileNotFoundError:
    print("No se encontró la contraseña cifrada. Asegúrate de haber ejecutado 'encriptador.py' primero.")
```

📌 **¿Qué hace este código?**  
✅ Carga la clave secreta almacenada en `clave.key`.  
✅ Lee la contraseña cifrada desde `contraseña_cifrada.txt`.  
✅ Descifra y muestra la contraseña original.

---

## **🔹 PASO 5: Código Completo en un Solo Archivo**

Si prefieres un solo archivo con ambas funcionalidades, aquí tienes `main.py`:

```python
from cryptography.fernet import Fernet

def generar_clave():
    key = Fernet.generate_key()
    with open("clave.key", "wb") as file:
        file.write(key)

def cargar_clave():
    with open("clave.key", "rb") as file:
        return file.read()

def cifrar_contraseña(contraseña: str) -> bytes:
    key = cargar_clave()
    cipher = Fernet(key)
    return cipher.encrypt(contraseña.encode())

def descifrar_contraseña(contraseña_cifrada: bytes) -> str:
    key = cargar_clave()
    cipher = Fernet(key)
    return cipher.decrypt(contraseña_cifrada).decode()

# Si no existe la clave, la generamos
try:
    clave = cargar_clave()
except FileNotFoundError:
    generar_clave()
    clave = cargar_clave()

opcion = input("¿Quieres cifrar (C) o descifrar (D) una contraseña? ").upper()

if opcion == "C":
    contraseña = input("Introduce la contraseña a cifrar: ")
    contraseña_cifrada = cifrar_contraseña(contraseña)
    with open("contraseña_cifrada.txt", "wb") as file:
        file.write(contraseña_cifrada)
    print(f"Contraseña cifrada y guardada en 'contraseña_cifrada.txt': {contraseña_cifrada}")

elif opcion == "D":
    try:
        with open("contraseña_cifrada.txt", "rb") as file:
            contraseña_cifrada = file.read()
        print(f"Contraseña original: {descifrar_contraseña(contraseña_cifrada)}")
    except FileNotFoundError:
        print("No se encontró la contraseña cifrada.")
```

---

<details>
  <summary>🔒</summary>

gAAAAABnzE_eSYvY2JrDZFb_EBC023c4huAn9Bu27YdqbCSkTzbsqW0F8r_gCBXe6z541aZA3LfCeQXWjt2qNxzaFWLh0f_oJw==

</details>






[[Hoja de Trucos HASHCAT]]
[[Guía rápida de fundamentos en Python]]
[[2- Laboratorios de Python]]
