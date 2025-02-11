
-----------

#sql #servicios #databases

---------

#### Escaneo de MySQL Server

  MySQL

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.14.128 -sV -sC -p3306 --script mysql*

Starting Nmap 7.80 ( https://nmap.org ) at 2021-09-21 00:53 CEST
Nmap scan report for 10.129.14.128
Host is up (0.00021s latency).

PORT     STATE SERVICE     VERSION
3306/tcp open  nagios-nsca Nagios NSCA
| mysql-brute: 
|   Accounts: 
|     root:<empty> - Valid credentials
|_  Statistics: Performed 45010 guesses in 5 seconds, average tps: 9002.0
|_mysql-databases: ERROR: Script execution failed (use -d to debug)
|_mysql-dump-hashes: ERROR: Script execution failed (use -d to debug)
| mysql-empty-password: 
|_  root account has empty password
| mysql-enum: 
|   Valid usernames: 
|     root:<empty> - Valid credentials
|     netadmin:<empty> - Valid credentials
|     guest:<empty> - Valid credentials
|     user:<empty> - Valid credentials
|     web:<empty> - Valid credentials
|     sysadmin:<empty> - Valid credentials
|     administrator:<empty> - Valid credentials
|     webadmin:<empty> - Valid credentials
|     admin:<empty> - Valid credentials
|     test:<empty> - Valid credentials
|_  Statistics: Performed 10 guesses in 1 seconds, average tps: 10.0
| mysql-info: 
|   Protocol: 10
|   Version: 8.0.26-0ubuntu0.20.04.1
|   Thread ID: 13
|   Capabilities flags: 65535
|   Some Capabilities: SupportsLoadDataLocal, SupportsTransactions, Speaks41ProtocolOld, LongPassword, DontAllowDatabaseTableColumn, Support41Auth, IgnoreSigpipes, SwitchToSSLAfterHandshake, FoundRows, InteractiveClient, Speaks41ProtocolNew, ConnectWithDatabase, IgnoreSpaceBeforeParenthesis, LongColumnFlag, SupportsCompression, ODBCClient, SupportsMultipleStatments, SupportsAuthPlugins, SupportsMultipleResults
|   Status: Autocommit
|   Salt: YTSgMfqvx\x0F\x7F\x16\&\x1EAeK>0
|_  Auth Plugin Name: caching_sha2_password
|_mysql-users: ERROR: Script execution failed (use -d to debug)
|_mysql-variables: ERROR: Script execution failed (use -d to debug)
|_mysql-vuln-cve2012-2122: ERROR: Script execution failed (use -d to debug)
MAC Address: 00:00:00:00:00:00 (VMware)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.21 seconds
```

Al igual que con todos nuestros escaneos, debemos tener cuidado con los resultados y confirmar manualmente la información obtenida porque parte de la información podría resultar ser un falso positivo. Este escaneo anterior es un excelente ejemplo de esto, ya que sabemos con certeza que el servidor MySQL de destino no usa una contraseña vacía para el usuario, sino una contraseña fija. Podemos probar esto con el siguiente comando:`root`

#### Interacción con el servidor MySQL

  MySQL

```shell-session
zunderrubb@htb[/htb]$ mysql -u root -h 10.129.14.132

ERROR 1045 (28000): Access denied for user 'root'@'10.129.14.1' (using password: NO)
```

Por ejemplo, si usamos una contraseña que hemos adivinado o encontrado a través de nuestra investigación, podremos iniciar sesión en el servidor MySQL y ejecutar algunos comandos.

  MySQL

```shell-session
zunderrubb@htb[/htb]$ mysql -u root -pP4SSw0rd -h 10.129.14.128

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MySQL connection id is 150165
Server version: 8.0.27-0ubuntu0.20.04.1 (Ubuntu)                                                         
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.                                     
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.                           
      
MySQL [(none)]> show databases;                                                                          
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.006 sec)


MySQL [(none)]> select version();
+-------------------------+
| version()               |
+-------------------------+
| 8.0.27-0ubuntu0.20.04.1 |
+-------------------------+
1 row in set (0.001 sec)


MySQL [(none)]> use mysql;
MySQL [mysql]> show tables;
+------------------------------------------------------+
| Tables_in_mysql                                      |
+------------------------------------------------------+
| columns_priv                                         |
| component                                            |
| db                                                   |
| default_roles                                        |
| engine_cost                                          |
| func                                                 |
| general_log                                          |
| global_grants                                        |
| gtid_executed                                        |
| help_category                                        |
| help_keyword                                         |
| help_relation                                        |
| help_topic                                           |
| innodb_index_stats                                   |
| innodb_table_stats                                   |
| password_history                                     |
...SNIP...
| user                                                 |
+------------------------------------------------------+
37 rows in set (0.002 sec)
```

Si nos fijamos en las bases de datos existentes, veremos que ya existen varias. Las bases de datos más importantes para el servidor MySQL son () y (). El esquema del sistema contiene tablas, información y metadatos necesarios para la administración. Puede encontrar más información sobre esta base de datos en el [manual de referencia](https://dev.mysql.com/doc/refman/8.0/en/system-schema.html#:~:text=The%20mysql%20schema%20is%20the,used%20for%20other%20operational%20purposes) de MySQL.`system schema``sys``information schema``information_schema`

  MySQL

```shell-session
mysql> use sys;
mysql> show tables;  

+-----------------------------------------------+
| Tables_in_sys                                 |
+-----------------------------------------------+
| host_summary                                  |
| host_summary_by_file_io                       |
| host_summary_by_file_io_type                  |
| host_summary_by_stages                        |
| host_summary_by_statement_latency             |
| host_summary_by_statement_type                |
| innodb_buffer_stats_by_schema                 |
| innodb_buffer_stats_by_table                  |
| innodb_lock_waits                             |
| io_by_thread_by_latency                       |
...SNIP...
| x$waits_global_by_latency                     |
+-----------------------------------------------+


mysql> select host, unique_users from host_summary;

+-------------+--------------+                   
| host        | unique_users |                   
+-------------+--------------+                   
| 10.129.14.1 |            1 |                   
| localhost   |            2 |                   
+-------------+--------------+                   
2 rows in set (0,01 sec)  
```

También es una base de datos que contiene metadatos. Sin embargo, estos metadatos se recuperan principalmente de la base de datos. La razón de la existencia de estos dos es el estándar ANSI/ISO que se ha establecido. es un catálogo del sistema de Microsoft para servidores SQL Server y contiene mucha más información que el archivo .`information schema``system schema``System schema``information schema`

Algunos de los comandos que debemos recordar y anotar para trabajar con bases de datos MySQL se describen a continuación en la tabla.

|**Mandar**|**Descripción**|
|---|---|
|`mysql -u <user> -p<password> -h <IP address>`|Conéctese al servidor MySQL. **No** debe haber un espacio entre el indicador '-p' y la contraseña.|
|`show databases;`|Mostrar todas las bases de datos.|
|`use <database>;`|Seleccione una de las bases de datos existentes.|
|`show tables;`|Mostrar todas las tablas disponibles en la base de datos seleccionada.|
|`show columns from <table>;`|Mostrar todas las columnas de la base de datos seleccionada.|
|`select * from <table>;`|Muestre todo en la tabla deseada.|
|`select * from <table> where <column> = "<string>";`|Busque needed en la tabla deseada.`string`|

Debemos saber interactuar con diferentes bases de datos. Por lo tanto, recomendamos instalar y configurar un servidor MySQL en una de nuestras máquinas virtuales para experimentar. También hay una sección de [problemas de seguridad](https://dev.mysql.com/doc/refman/8.0/en/general-security-issues.html) ampliamente cubierta en el manual de referencia que cubre las mejores prácticas para proteger los servidores MySQL. Deberíamos usar esto al configurar nuestro servidor MySQL para comprender mejor por qué algo podría no funcionar.


**[[SQL]]**