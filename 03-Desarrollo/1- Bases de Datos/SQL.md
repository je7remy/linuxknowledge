
---

#bbdd #sql #comandos #tabla #SQL #ComandosSQL #BaseDeDatos #ConsultasSQL #FiltrarDatos #JOIN #GROUPBY #HAVING #ORDERBY #INSERT #UPDATE #DELETE #CREATE #INDEX #DISTINCT #WHERE #AND #OR #LIKE
  
---

| Comando SQL      | Ejemplo                                                                               | Descripción                                                                          |
| ---------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **SELECT**       | `SELECT columna FROM tabla WHERE condición;`                                          | Recupera datos de una tabla en función de una condición.                             |
| **INSERT INTO**  | `INSERT INTO tabla (columna1, columna2) VALUES (valor1, valor2);`                     | Agrega filas a una tabla con valores especificados.                                  |
| **UPDATE**       | `UPDATE tabla SET columna = nuevo_valor WHERE condición;`                             | Modifica registros existentes en una tabla.                                          |
| **DELETE FROM**  | `DELETE FROM tabla WHERE condición;`                                                  | Elimina registros de una tabla en función de una condición.                          |
| **CREATE TABLE** | `CREATE TABLE tabla (columna1 tipo, columna2 tipo);`                                  | Crea una nueva tabla con columnas y tipos de datos especificados.                    |
| **ALTER TABLE**  | `ALTER TABLE tabla ADD columna tipo;`                                                 | Agrega una columna a una tabla existente.                                            |
| **DROP TABLE**   | `DROP TABLE tabla;`                                                                   | Elimina una tabla y todos sus datos.                                                 |
| **CREATE INDEX** | `CREATE INDEX nombre ON tabla (columna);`                                             | Crea un índice en una columna para mejorar el rendimiento de las consultas.          |
| **JOIN**         | `SELECT t1.columna, t2.columna FROM tabla1 t1 INNER JOIN tabla2 t2 ON t1.id = t2.id;` | Combina datos de dos o más tablas en función de una relación.                        |
| **GROUP BY**     | `SELECT columna, COUNT(*) FROM tabla GROUP BY columna;`                               | Agrupa filas en función de una columna y aplica funciones de agregación.             |
| **HAVING**       | `SELECT columna, COUNT(*) FROM tabla GROUP BY columna HAVING COUNT(*) > 1;`           | Filtra resultados de una consulta GROUP BY basándose en una condición de agregación. |
| **ORDER BY**     | `SELECT columna1, columna2 FROM tabla ORDER BY columna1 ASC, columna2 DESC;`          | Ordena los resultados de una consulta en función de una o más columnas.              |
| **DISTINCT**     | `SELECT DISTINCT columna FROM tabla;`                                                 | Retorna valores únicos de una columna.                                               |
| **WHERE**        | `SELECT columna FROM tabla WHERE condición;`                                          | Filtra filas basadas en una condición dada.                                          |
| **AND** / **OR** | `SELECT columna FROM tabla WHERE condición1 AND condición2;`                          | Combina múltiples condiciones en una consulta.                                       |
| **LIKE**         | `SELECT columna FROM tabla WHERE columna LIKE 'patrón%';`                             | Filtra filas basadas en un patrón de texto.                                          |

 **[[5- MySQL]]**
 **[[4- MSSQL]]** 
 **[[7- Oracle TNS]]**
 **[[1- FTP]]**
 **[[9- SMB]]**
 **[[11- SSH]]**
[[1- Instalar Base de datos MySQL]]
[[2- Insertar Información a la Base de Datos desde Python]]
[[3- Consultas a la Base de Datos]]
[[4- Consultar a la Base de Datos + Sentencias Condicionales]]
