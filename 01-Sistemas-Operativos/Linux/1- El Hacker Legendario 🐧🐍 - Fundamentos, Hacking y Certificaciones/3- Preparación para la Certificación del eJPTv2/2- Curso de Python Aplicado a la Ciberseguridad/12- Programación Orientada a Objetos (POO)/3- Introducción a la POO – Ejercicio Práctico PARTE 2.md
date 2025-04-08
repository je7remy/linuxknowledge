import os

  

class SistemaOperativo:

    def __init__(self, nombre_archivo, nombre_carpeta, dueño):

        self.nombre_archivo = nombre_archivo

        self.nombre_carpeta = nombre_carpeta

        self.dueño = dueño

  

    def crear_carpeta(self):

        os.mkdir(self.nombre_carpeta)

  

    def crear_documento(self):

        with open(f"{self.nombre_archivo}", 'w') as file:

            file.write(f"Documento {self.nombre_archivo} propiedad de {self.dueño}")

    def borrar_todos(self):

        os.remove(self.nombre_archivo)

        os.rmdir(self.nombre_carpeta)

        print(f'Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}')

  

# Ejemplo de uso:

usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')

  

eleccion =input("Escribe 1 si quieres crear los archivos y 2 si los quieres eliminar")

  

if eleccion == "1":

  

    usuario1.crear_carpeta()

    usuario1.crear_documento()

  

elif eleccion == "2":

    usuario1.borrar_todos()

---

import os

  

class SistemaOperativo:

    def __init__(self, nombre_archivo, nombre_carpeta, dueño):

        self.nombre_archivo = nombre_archivo

        self.nombre_carpeta = nombre_carpeta

        self.dueño = dueño

  

    def crear_carpeta(self):

        os.mkdir(self.nombre_carpeta)

  

    def crear_documento(self):

        with open(f"{self.nombre_archivo}", 'w') as file:

            file.write(f"Documento {self.nombre_archivo} propiedad de {self.dueño}")

    def borrar_todos(self):

        os.remove(self.nombre_archivo)

        os.rmdir(self.nombre_carpeta)

        print(f'Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}')

  

# Ejemplo de uso:

usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')

  

eleccion =input("Escribe 1 si quieres crear los archivos y 2 si los quieres eliminar")

  

if eleccion == "1":

  

    try:

        usuario1.crear_carpeta()

        usuario1.crear_documento()

    except:

        usuario1.borrar_todos()

        usuario1.crear_carpeta()

        usuario1.crear_documento()

    finally:

        print("El programa ha finalizado")

  

elif eleccion == "2":

    try:

        usuario1.borrar_todos()

    except:

        print("Hubo un error al eliminar los archivos, o quiza ya estaban eliminados")

