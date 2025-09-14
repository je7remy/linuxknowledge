
Anteriormente, exploró las uniones SQL y cómo utilizarlas para unir datos de varias tablas cuando éstas comparten una columna común. También examinó cómo existen diferentes tipos de uniones y cómo cada una de ellas devuelve filas diferentes de las tablas que se están uniendo. En esta lectura, repasará estos conceptos y analizará más detenidamente la sintaxis necesaria para cada tipo de unión.

## Uniones INNER JOIN

El primer tipo de unión que puede realizar es una unión interna. INNER JOIN devuelve las filas que coinciden en una columna especificada que existe en más de una tabla.

![Diagrama de Venn con dos círculos denominados "mesa izquierda" y "mesa derecha". La intersección está resaltada.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/9y5ZKSySQTuS5RQ-MJLXrA_6b756cb30b9442c8ae576607a6ab3ff1_CS_R-080_Inner-joins.png?expiry=1757894400000&hmac=fA-ZI4xU3m5DpTzLJ8U9ZusPNwKrQxiOIigwI2-d6ic)

Sólo devuelve las filas en las que hay una coincidencia, pero al igual que otros tipos de uniones, devuelve todas las columnas especificadas de todas las tablas unidas. Por ejemplo, si la consulta une dos tablas con SELECT *, se devuelven todas las columnas de ambas tablas.

**Nota:** Si una columna existe en las dos tablas, se devuelve dos veces cuando se utiliza SELECT *.

### La sintaxis de un inner join

Para escribir una consulta utilizando INNER JOIN, puede utilizar la siguiente sintaxis:

SELECT *

FROM employees

INNER JOIN machines ON employees.device_id = machines.device_id;

Debe especificar las dos tablas a unir incluyendo la primera o tabla izquierda después de FROM y la segunda o tabla derecha después de INNER JOIN.

Después del nombre de la tabla derecha, utilice la palabra clave ON y el operador = para indicar la columna sobre la que está uniendo las tablas. Es importante que especifique tanto el nombre de la tabla como el de la columna en esta parte de la unión colocando un punto (.) entre la tabla y la columna.

Además de seleccionar todas las columnas, puede seleccionar sólo determinadas columnas. Por ejemplo, si sólo desea que la unión devuelva las columnas username, operating_system y device_id, puede escribir esta consulta:

SELECT username, operating_system, employees.device_id

FROM  employees

INNER JOIN machines ON employees.device_id = machines.device_id;

**Nota**: En la consulta de ejemplo, username y operating_system sólo aparecen en una de las dos tablas, por lo que se escriben sólo con el nombre de la columna. En cambio, como device_id aparece en las dos tablas, es necesario indicar cuál devolver especificando tanto el nombre de la tabla como el de la columna (employees.device_id).

## Uniones externas

Las uniones externas amplían lo que se devuelve de una unión. Cada tipo de unión externa devuelve todas las filas de una tabla o de ambas.

### LEFT JOIN izquierdas

Al unir dos tablas, LEFT JOIN devuelve todos los registros de la primera tabla, pero sólo devuelve las filas de la segunda tabla que coincidan en una columna especificada.

![Diagrama de Venn con dos círculos denominados "mesa izquierda" y "mesa derecha". El círculo de la izquierda y la intersección están resaltados.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/GsYCwSiOSMmymUqPUAQJ5w_5beed7e470c546fca088a83dfd9465f1_CS_R-080_Left-joins.png?expiry=1757894400000&hmac=2FJcNorG7eukp0uVIn_NsrLjo5qdb5unYBwbhoDPAlk)

La sintaxis para utilizar LEFT JOIN se demuestra en la siguiente consulta:

SELECT *

FROM employees

LEFT JOIN machines ON employees.device_id = machines.device_id;

Como con todas las uniones, debe especificar la primera tabla o tabla izquierda como la tabla que viene después de FROM y la segunda tabla o tabla derecha como la tabla que viene después de LEFT JOIN. En la consulta del ejemplo, como employees es la tabla izquierda, se devuelven todos sus registros. Sólo se devuelven los registros que coinciden en la columna device_id de la tabla derecha, machines.

### RIGHT JOIN

Al unir dos tablas, RIGHT JOIN devuelve todos los registros de la segunda tabla, pero sólo devuelve las filas de la primera tabla que coinciden en una columna especificada.

![Diagrama de Venn con dos círculos denominados "mesa izquierda" y "mesa derecha". El círculo derecho y la intersección están resaltados.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/YHXRMOLiQheppUjthmM5yQ_cfb18a8315e34357bd1299f7eefafcf1_CS_R-080_Right-joins.png?expiry=1757894400000&hmac=SbHBz___TWLc0Db4a0tf54AdGuaMXHZP82D8-ysNIIA)

La siguiente consulta demuestra la sintaxis de RIGHT JOIN:

SELECT *

FROM employees

RIGHT JOIN machines ON employees.device_id = machines.device_id;

RIGHT JOIN tiene la misma sintaxis que LEFT JOIN, con la única diferencia de que la palabra clave RIGHT JOIN indica a SQL que produzca una salida diferente. La consulta devuelve todos los registros de machines, que es la segunda tabla o tabla derecha. Sólo se devuelven los registros coincidentes de employees, que es la primera tabla o izquierda.

**Nota:** Puede utilizar LEFT JOIN y RIGHT JOIN y obtener exactamente los mismos resultados si utiliza las tablas en orden inverso. La siguiente consulta RIGHT JOIN devuelve exactamente el mismo resultado que la consulta LEFT JOIN demostrada en la sección anterior:

SELECT *

FROM machines

RIGHT JOIN employees ON employees.device_id = machines.device_id;

Todo lo que tiene que hacer es cambiar el orden de las tablas que aparecen antes y después de la palabra clave utilizada para la unión, y habrá intercambiado las tablas izquierda y derecha.

### Uniones externas completas

FULL OUTER JOIN devuelve todos los registros de ambas tablas. Puede considerarlo como una forma de unir completamente dos tablas.

![Diagrama de Venn con dos círculos denominados "mesa izquierda" y "mesa derecha". Ambos círculos están resaltados](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/oRzF__GaTqSGMmUqXKbSrQ_92db9841a00244c2aa214e60bb07f1f1_CS_R-080_FULL-OUTER-JOIN.png?expiry=1757894400000&hmac=RdtgP5KTXIXBSWZfi_KlOn6D0UkPcnJvXikilwZxbM8)

Puede revisar la sintaxis para utilizar FULL OUTER JOIN en la siguiente consulta:

SELECT *

FROM employees

FULL OUTER JOIN machines ON employees.device_id = machines.device_id;

Los resultados de una consulta FULL OUTER JOIN incluyen todos los registros de ambas tablas. De forma similar a INNER JOIN, el orden de las tablas no cambia los resultados de la consulta.

## Claves

Cuando se trabaja en SQL, existen múltiples formas de unir tablas. Todas las uniones devuelven los registros que coinciden en una columna especificada. INNER JOIN devolverá sólo estos registros. Las uniones externas también devuelven todos los demás registros de una o ambas tablas. LEFT JOIN devuelve todos los registros de la primera tabla o tabla izquierda, RIGHT JOIN devuelve todos los registros de la segunda tabla o tabla derecha y FULL OUTER JOIN devuelve todos los registros de ambas tablas.