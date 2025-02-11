pip3 es una herramienta de línea de comandos utilizada para instalar y gestionar paquetes de software escritos en Python. Es una versión específica para Python 3 de pip, que es el instalador de paquetes estándar para Python. Aquí tienes algunas de las funcionalidades y comandos básicos que puedes utilizar con pip3:

1. **Instalar un paquete:**

pip3 install nombre_paquete

Este comando instalará el paquete especificado desde el índice de paquetes de Python (PyPI).

2. **Desinstalar un paquete:**

pip3 uninstall nombre_paquete

Este comando desinstalará el paquete especificado.

3. **Actualizar un paquete:**

pip3 install --upgrade nombre_paquete

Este comando actualizará el paquete especificado a la última versión disponible.

4. **Listar paquetes instalados:**

pip3 list

Este comando mostrará una lista de todos los paquetes instalados en el entorno actual.

5. **Mostrar información sobre un paquete:**

pip3 show nombre_paquete

Este comando mostrará información detallada sobre el paquete especificado, incluyendo su versión, autor, y dependencias.

6. **Guardar los paquetes instalados en un archivo de requisitos:**

pip3 freeze > requirements.txt

Este comando generará un archivo requirements.txt con una lista de todos los paquetes y sus versiones actuales en el entorno.

7. **Instalar paquetes desde un archivo de requisitos:**

pip3 install -r requirements.txt

Este comando instalará todos los paquetes listados en el archivo requirements.txt.

8. **Buscar un paquete:**

pip3 search nombre_paquete

Este comando buscará paquetes que coincidan con el nombre especificado.

Estas son solo algunas de las operaciones básicas que puedes realizar con pip3. Es una herramienta poderosa y esencial para gestionar dependencias en proyectos de Python, especialmente cuando trabajas con Python 3.