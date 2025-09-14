
*En esta lectura, explorarás las diferencias entre las dos herramientas en lo que se refiere al filtrado. También aprenderás que una forma de acceder a SQL es a través de la línea de comandos de Linux.

## **Acceso a SQL**

Existen muchas interfaces para acceder a SQL y muchas versiones diferentes de SQL. Una forma de acceder a SQL es a través de la línea de comandos de Linux.

Para acceder a SQL desde Linux, tienes que escribir un comando para la versión de SQL que quieras utilizar. Por ejemplo, si quieres acceder a SQLite, puedes introducir el comando **sqlite3** en la línea de comandos.

Después de esto, cualquier comando escrito en la línea de comandos será dirigido a SQL en lugar de a los comandos de Linux.

## **Diferencias entre el filtrado de Linux y SQL**

Aunque tanto Linux como SQL permiten filtrar los datos, existen algunas diferencias que afectan a la elección de uno u otro.

### **Propósito**

Linux filtra datos en el contexto de archivos y directorios en un sistema de archivos. Se utiliza para tareas como la búsqueda de archivos específicos, la manipulación de permisos de archivo o la gestión de procesos.

SQL se utiliza para filtrar datos dentro de un sistema de gestión de bases de datos. Sirve para consultar y manipular datos almacenados en tablas y recuperar información específica en función de criterios definidos.

### **Sintaxis**

Linux utiliza varios comandos y opciones de línea de comandos específicos para cada herramienta de filtrado. La sintaxis varía en función de la herramienta y su finalidad. Algunos ejemplos de comandos Linux son find, sed, cut, e grep

SQL utiliza el Lenguaje de Consulta Estructurada (SQL), un lenguaje estandarizado con palabras clave y cláusulas específicas para filtrar datos en distintas bases de datos SQL. Algunos ejemplos de palabras clave y cláusulas SQL son WHERE, SELECT, JOIN

### **Estructura**

SQL ofrece mucha más estructura que Linux, que es más libre y no tan ordenado.

Por ejemplo, si quisieras acceder a un registro de los intentos de inicio de sesión de los empleados, SQL tendría cada registro separado en columnas. Linux imprimiría los datos como una línea de texto sin esta organización. Como resultado, la selección de una columna específica para analizar sería más fácil y más eficiente en SQL.

En términos de estructura, SQL proporciona resultados más legibles y que pueden ajustarse más rápidamente que cuando se utiliza Linux.

### **Unir tablas**

Algunas decisiones relacionadas con la seguridad requieren información procedente de distintas tablas. SQL permite al analista unir varias tablas cuando devuelve datos. Linux no tiene esa misma funcionalidad; no permite que los datos se conecten a otra información del ordenador. Esto es más restrictivo para un analista que revisa los registros de seguridad.

### **Mejores usos**

AS un analista de seguridad, es importante entender cuando puedes usar cada herramienta. Aunque SQL tiene una estructura más organizada y permite unir tablas, esto no significa que no haya situaciones que requieran filtrar datos en Linux.

Muchos de los datos utilizados en ciberseguridad se almacenarán en un formato de base de datos que funcione con SQL. Sin embargo, otros registros pueden estar en un formato que no es compatible con SQL. Por ejemplo, si los datos se almacenan en un archivo de texto, no se puede buscar en ellos con SQL. En esos casos, es útil saber cómo filtrar en Linux.

## **Puntos clave**

El filtrado Linux se centra en la gestión de archivos y directorios en un sistema, mientras que el filtrado SQL se centra en la manipulación de datos estructurados dentro de las bases de datos. Para trabajar con SQL, puedes acceder a él desde múltiples interfaces diferentes, como la línea de comandos de Linux. Tanto SQL como Linux permiten filtrar datos específicos, pero SQL ofrece las ventajas de estructurar los datos y permitir unir datos de varias tablas.*