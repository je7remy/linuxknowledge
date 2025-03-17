
---

#Python 🐍 #VirtualEnv 🌍 #EntornoVirtual 💻 #Requests 📡 #Linux 🐧 #Ubuntu 🚀 #ArchLinux ⚡ #PythonDev 👨‍💻 #Scripting 📝 #Automatización 🤖 #DesarrolloSoftware 🔥

---

## 🔹 **1. Creación y ejecución del script Python**

📌 **Código (`proyecto.py`)**

```python
import requests

url = "https://www.google.com"
response = requests.get(url)

print(f"Estado de la respuesta: {response.status_code}")
```

### **Lo que sucede aquí:**

1. **Se importa la biblioteca `requests`** para realizar peticiones HTTP.
2. **Se define la URL de Google** y se hace una solicitud `GET`.
3. **Se imprime el estado de la respuesta (`status_code`)**, que debería ser `200` si la conexión es exitosa.

⚠ **Posible problema:** Si `requests` no está instalado en el sistema, obtendrás un error:

```
ModuleNotFoundError: No module named 'requests'
```

Para evitar esto, se crea un entorno virtual.

---

## 🔹 **2. Instalación de `venv` (Ubuntu/Debian)**

```bash
sudo apt install python3-venv
```

### **¿Qué ocurre aquí?**

- Se instala el módulo `venv`, necesario para crear entornos virtuales en Python.
- Si ya estaba instalado, el sistema lo notificará.

---

## 🔹 **3. Creación del Entorno Virtual**

```bash
python3 -m venv librerias_proyecto
```

### **¿Qué sucede aquí?**

- Se crea una carpeta llamada `librerias_proyecto` que contendrá:
    - Un intérprete de Python aislado.
    - Un gestor de paquetes `pip` propio.
    - Un espacio separado para instalar dependencias sin afectar el sistema global.

📌 **Estructura de la carpeta creada:**

```
librerias_proyecto/
│── bin/       # Ejecutables de Python y pip
│── lib/       # Librerías instaladas en este entorno
│── include/   # Archivos de cabecera de Python
│── pyvenv.cfg # Configuración del entorno virtual
```

---

## 🔹 **4. Activación del Entorno Virtual**

```bash
source librerias_proyecto/bin/activate
```

### **¿Qué sucede aquí?**

- El shell cambia al entorno virtual.
- La línea de comandos muestra algo como:
    
    ```
    (librerias_proyecto) usuario@maquina:~$
    ```
    
- Ahora, cualquier paquete instalado con `pip` **solo afectará este entorno**.

⚠ **Si ejecutamos `proyecto.py` en este punto, seguirá fallando si `requests` no está instalado en el entorno virtual.**

💡 **Solución:** Instalar `requests` dentro del entorno virtual:

```bash
pip install requests
```

Ahora, si ejecutamos:

```bash
python3 proyecto.py
```

El código **funcionará correctamente** y mostrará:

```
Estado de la respuesta: 200
```

---

## 🔹 **5. Salir del Entorno Virtual**

```bash
deactivate
```

### **¿Qué sucede aquí?**

- El shell vuelve a su estado normal.
- Se desactiva el entorno virtual y ahora cualquier ejecución de Python usa los paquetes del sistema.

---

## 🔹 **6. Eliminar el Entorno Virtual**

```bash
rm -rf librerias_proyecto
```

### **¿Qué sucede aquí?**

- Se borra toda la carpeta del entorno virtual, eliminando:
    - Python aislado
    - Todas las librerías instaladas en ese entorno
    - La configuración del entorno

Después de esto, si intentas ejecutar `python3 proyecto.py`, fallará con:

```
ModuleNotFoundError: No module named 'requests'
```

porque el entorno virtual que contenía `requests` ya no existe.

---

## ✅ **Resumen Final**

4. Creamos y ejecutamos un script Python (`proyecto.py`).
5. Instalamos `venv` (`sudo apt install python3-venv`).
6. Creamos un entorno virtual (`python3 -m venv librerias_proyecto`).
7. Activamos el entorno (`source librerias_proyecto/bin/activate`).
8. Instalamos `requests` (`pip install requests`) y ejecutamos el script.
9. Desactivamos el entorno (`deactivate`).
10. Eliminamos el entorno (`rm -rf librerias_proyecto`).

Ahora, cada vez que necesites un entorno limpio, simplemente repites este proceso. 🚀