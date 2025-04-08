Hola, bienvenidos nuevamente al curso de Python aplicado a la ciberseguridad. En esta oportunidad, vamos a analizar y desarrollar paso a paso un ejemplo de programación orientada a objetos (POO) que nos permitirá entender cómo funciona este paradigma en Python. El código que vamos a desglosar crea una clase llamada `SistemaOperativo`, la cual simula un sistema básico capaz de crear carpetas, crear documentos y eliminar ambos. A continuación, explicaré cada parte del código con lujo de detalle para que quede claro cómo se construye y cómo funciona.

---

### **Paso 1: Importación del módulo `os`**

```python
import os
```

- **Qué hace**: Este es el primer paso del código. Importamos el módulo `os`, que es una biblioteca estándar de Python diseñada para interactuar con el sistema operativo.
- **Por qué lo usamos**: Nos permite realizar operaciones como crear carpetas (`os.mkdir`), eliminar carpetas (`os.rmdir`) y eliminar archivos (`os.remove`). En este ejemplo, lo necesitamos para que los métodos de nuestra clase puedan manipular el sistema de archivos.
- **Ejemplo práctico**: Si más adelante queremos crear una carpeta llamada "documentos", el módulo `os` nos proporciona las herramientas para hacerlo directamente desde Python.

---

### **Paso 2: Definición de la clase `SistemaOperativo`**

```python
class SistemaOperativo:
```

- **Qué hace**: Aquí definimos una clase llamada `SistemaOperativo`. En POO, una clase es como un molde o plantilla que describe qué atributos (propiedades) y métodos (acciones) tendrán los objetos que creemos a partir de ella.
- **Concepto clave**: La clase no hace nada por sí sola; es solo una definición. Para que "funcione", debemos crear objetos (instancias) basados en esta clase.
- **Ejemplo práctico**: Piensa en la clase como el plano de una casa. El plano no es la casa en sí, pero nos dice cómo construirla.

---

### **Paso 3: Método constructor `__init__`**

```python
def __init__(self, nombre_archivo, nombre_carpeta, dueño):
    self.nombre_archivo = nombre_archivo
    self.nombre_carpeta = nombre_carpeta
    self.dueño = dueño
```

- **Qué hace**: Este es el método constructor de la clase, que se ejecuta automáticamente cada vez que creamos un nuevo objeto de `SistemaOperativo`. Su propósito es inicializar los atributos del objeto con valores específicos.
- **Parámetros**:
  - `self`: Es obligatorio en Python y representa al objeto que se está creando. Nos permite acceder a sus atributos y métodos desde dentro de la clase.
  - `nombre_archivo`: El nombre del archivo que queremos manipular (por ejemplo, "contabilidad.doc").
  - `nombre_carpeta`: El nombre de la carpeta que queremos manipular (por ejemplo, "documentos").
  - `dueño`: El nombre del usuario o propietario que realiza las operaciones (por ejemplo, "Jeremy").
- **Inicialización de atributos**:
  - `self.nombre_archivo = nombre_archivo`: Guarda el valor de `nombre_archivo` como un atributo del objeto.
  - `self.nombre_carpeta = nombre_carpeta`: Guarda el valor de `nombre_carpeta` como un atributo del objeto.
  - `self.dueño = dueño`: Guarda el valor de `dueño` como un atributo del objeto.
- **Ejemplo práctico**: Si creamos un objeto con `SistemaOperativo("contabilidad.doc", "documentos", "Jeremy")`, el objeto tendrá los atributos `nombre_archivo = "contabilidad.doc"`, `nombre_carpeta = "documentos"` y `dueño = "Jeremy"`.

---

### **Paso 4: Método `crear_carpeta`**

```python
def crear_carpeta(self):
    os.mkdir(self.nombre_carpeta)
```

- **Qué hace**: Este método crea una carpeta en el sistema de archivos utilizando el nombre almacenado en el atributo `self.nombre_carpeta`.
- **Cómo funciona**:
  - `self`: Permite acceder a los atributos del objeto, en este caso, `self.nombre_carpeta`.
  - `os.mkdir(self.nombre_carpeta)`: Llama a la función `mkdir` del módulo `os`, que crea una carpeta con el nombre especificado en `self.nombre_carpeta`.
- **Ejemplo práctico**: Si el objeto tiene `self.nombre_carpeta = "documentos"` y ejecutamos `crear_carpeta()`, se creará una carpeta llamada "documentos" en el directorio donde está corriendo el script.
- **Nota**: Si la carpeta ya existe, este método generará un error. Más adelante podríamos mejorarlo con manejo de excepciones.

---

### **Paso 5: Método `crear_documento`**

```python
def crear_documento(self):
    with open(f"{self.nombre_archivo}", 'w') as file:
        file.write(f"Documento {self.nombre_archivo} propiedad de {self.dueño}")
```

- **Qué hace**: Este método crea un archivo con el nombre almacenado en `self.nombre_archivo` y escribe un mensaje en él que incluye el nombre del archivo y el dueño.
- **Cómo funciona**:
  - `with open(f"{self.nombre_archivo}", 'w') as file`: Abre (o crea si no existe) un archivo en modo escritura (`'w'`). El nombre del archivo proviene de `self.nombre_archivo`. El uso de `with` asegura que el archivo se cierre automáticamente después de usarlo.
  - `file.write(...)`: Escribe una cadena en el archivo. La cadena se construye con una f-string que incluye:
    - `"Documento"`: Texto fijo.
    - `self.nombre_archivo`: El nombre del archivo (por ejemplo, "contabilidad.doc").
    - `self.dueño`: El nombre del dueño (por ejemplo, "Jeremy").
- **Ejemplo práctico**: Si `self.nombre_archivo = "contabilidad.doc"` y `self.dueño = "Jeremy"`, este método creará un archivo llamado "contabilidad.doc" con el contenido: `Documento contabilidad.doc propiedad de Jeremy`.
- **Nota**: Si el archivo ya existe, se sobrescribirá.

---

### **Paso 6: Método `borrar_todos`**

```python
def borrar_todos(self):
    os.rmdir(self.nombre_carpeta)
    os.remove(self.nombre_archivo)
    print(f'Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}')
```

- **Qué hace**: Este método elimina tanto la carpeta como el archivo especificados en los atributos del objeto y luego muestra un mensaje de confirmación.
- **Cómo funciona**:
  - `os.rmdir(self.nombre_carpeta)`: Elimina la carpeta cuyo nombre está en `self.nombre_carpeta`. La carpeta debe estar vacía para que esto funcione.
  - `os.remove(self.nombre_archivo)`: Elimina el archivo cuyo nombre está en `self.nombre_archivo`.
  - `print(f'Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}')`: Imprime un mensaje indicando qué se eliminó, usando los valores de los atributos.
- **Ejemplo práctico**: Si `self.nombre_carpeta = "documentos"` y `self.nombre_archivo = "contabilidad.doc"`, este método eliminará la carpeta "documentos" y el archivo "contabilidad.doc", y luego imprimirá: `Se ha eliminado documentos y contabilidad.doc`.
- **Nota**: Si la carpeta no está vacía o alguno de los elementos no existe, este método generará un error. Esto también se puede mejorar con excepciones.

---

### **Paso 7: Creación del objeto `usuario1`**

```python
usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')
```

- **Qué hace**: Creamos un objeto (instancia) de la clase `SistemaOperativo` llamado `usuario1`. Al hacerlo, pasamos tres argumentos al constructor.
- **Cómo funciona**:
  - `'contabilidad.doc'`: Se asigna a `self.nombre_archivo`.
  - `'documentos'`: Se asigna a `self.nombre_carpeta`.
  - `'Jeremy'`: Se asigna a `self.dueño`.
- **Resultado**: El objeto `usuario1` ahora tiene los atributos:
  - `usuario1.nombre_archivo = "contabilidad.doc"`
  - `usuario1.nombre_carpeta = "documentos"`
  - `usuario1.dueño = "Jeremy"`
- **Ejemplo práctico**: Este objeto representa a un usuario (Jeremy) que puede usar las funcionalidades de la clase para crear una carpeta llamada "documentos", un archivo llamado "contabilidad.doc", o eliminar ambos.

---

### **Paso 8: Llamadas a los métodos (comentadas)**

```python
#usuario1.crear_carpeta()
#usuario1.crear_documento()
#usuario1.borrar_todos()
```

- **Qué hace**: Estas líneas están comentadas (no se ejecutan), pero muestran cómo podemos usar el objeto `usuario1` para llamar a los métodos de la clase.
- **Explicación de cada una**:
  - `usuario1.crear_carpeta()`: Si lo descomentamos, creará una carpeta llamada "documentos" en el directorio actual.
  - `usuario1.crear_documento()`: Si lo descomentamos, creará un archivo "contabilidad.doc" con el texto "Documento contabilidad.doc propiedad de Jeremy".
  - `usuario1.borrar_todos()`: Si lo descomentamos, eliminará la carpeta "documentos" y el archivo "contabilidad.doc", mostrando un mensaje de confirmación.
- **Por qué están comentadas**: Probablemente para que el código no modifique el sistema de archivos al ejecutarse directamente, permitiéndonos analizarlo sin efectos secundarios.

---

### **Resumen del funcionamiento general**

- **Clase como molde**: La clase `SistemaOperativo` define un sistema simplificado con tres funcionalidades: crear carpetas, crear documentos y eliminar ambos. Estas funcionalidades están encapsuladas en métodos.
- **Atributos**: Los atributos `nombre_archivo`, `nombre_carpeta` y `dueño` se inicializan al crear un objeto y se usan en los métodos para personalizar las operaciones.
- **Objeto `usuario1`**: Es una instancia concreta de la clase, configurada con valores específicos ("contabilidad.doc", "documentos", "Jeremy"). Podemos usar este objeto para ejecutar las acciones definidas en la clase.
- **Programación orientada a objetos**: Este ejemplo muestra los pilares básicos de POO:
  - **Encapsulación**: Los métodos y atributos están agrupados dentro de la clase.
  - **Instanciación**: Podemos crear múltiples objetos con diferentes valores (por ejemplo, otro usuario con otros nombres).
  - **Reutilización**: El código es modular y se puede usar repetidamente.

---

### **Posibles mejoras (mencionadas en el contexto)**

Aunque el código funciona, tiene limitaciones que podríamos abordar:
1. **Manejo de errores**: Si intentamos eliminar una carpeta o archivo que no existe, o crear algo que ya existe, el código fallará. Podríamos usar bloques `try-except` para manejar estas excepciones.
2. **Interacción con el usuario**: Podríamos agregar un `input()` para que el usuario decida qué método ejecutar (por ejemplo, "1 para crear carpeta, 2 para crear documento, 3 para borrar todo").
3. **Flexibilidad**: Podríamos permitir que los métodos acepten parámetros adicionales en lugar de depender solo de los atributos iniciales.

---

### **Conclusión**

Este código es un excelente punto de partida para entender la programación orientada a objetos en Python. Nos muestra cómo definir una clase, inicializar atributos con un constructor, crear métodos para realizar acciones y usar objetos para ejecutar esas acciones en un contexto específico. Si lo ejecutamos paso a paso (descomentando las líneas una por una), podemos ver cómo interactúa con el sistema de archivos y cómo los atributos personalizan cada operación. Espero que esta explicación detallada te haya aclarado cada parte del código. 


### **Código Completo:

````python
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

        os.rmdir(self.nombre_carpeta)

        os.remove(self.nombre_archivo)

        print(f'Se ha eliminado {self.nombre_carpeta} y {self.nombre_archivo}')

  

usuario1 = SistemaOperativo('contabilidad.doc', 'documentos', 'Jeremy')

  

usuario1.crear_carpeta()

#usuario1.crear_documento()

#usuario1.borrar_todo()

`````
