
------------

#MSSQL #Networking #Nmap #Metasploit #SQLInjection #DatabaseSecurity #Pentesting #SQLServer #TSQL #Impacket #MSSQLPing #NamedPipes #MSSQLInfo #Scanning #HuellasDeServicio #VulnerabilidadesSQL #SeguridadInformática #EthicalHacking #RedTeam

---------

## Huella del servicio

Hay muchas maneras en las que podemos abordar la huella del servicio MSSQL, cuanto más específicos podamos ser con nuestros escaneos, más información útil podremos recopilar. NMAP tiene scripts mssql predeterminados que se pueden usar para dirigirse al puerto tcp predeterminado en el que escucha MSSQL.`1433`

El escaneo NMAP con script a continuación nos proporciona información útil. Podemos ver el , , y . Nos beneficiaremos de añadir estos descubrimientos a nuestras notas.`hostname``database instance name``software version of MSSQL``named pipes are enabled`

#### Análisis de scripts NMAP MSSQL

  MSSQL

```shell-session
zunderrubb@htb[/htb]$ sudo nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 10.129.201.248

Starting Nmap 7.91 ( https://nmap.org ) at 2021-11-08 09:40 EST
Nmap scan report for 10.129.201.248
Host is up (0.15s latency).

PORT     STATE SERVICE  VERSION
1433/tcp open  ms-sql-s Microsoft SQL Server 2019 15.00.2000.00; RTM
| ms-sql-ntlm-info: 
|   Target_Name: SQL-01
|   NetBIOS_Domain_Name: SQL-01
|   NetBIOS_Computer_Name: SQL-01
|   DNS_Domain_Name: SQL-01
|   DNS_Computer_Name: SQL-01
|_  Product_Version: 10.0.17763

Host script results:
| ms-sql-dac: 
|_  Instance: MSSQLSERVER; DAC port: 1434 (connection failed)
| ms-sql-info: 
|   Windows server name: SQL-01
|   10.129.201.248\MSSQLSERVER: 
|     Instance name: MSSQLSERVER
|     Version: 
|       name: Microsoft SQL Server 2019 RTM
|       number: 15.00.2000.00
|       Product: Microsoft SQL Server 2019
|       Service pack level: RTM
|       Post-SP patches applied: false
|     TCP port: 1433
|     Named pipe: \\10.129.201.248\pipe\sql\query
|_    Clustered: false

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.52 seconds
```

También podemos usar Metasploit para ejecutar un escáner auxiliar llamado que escaneará el servicio MSSQL y proporcionará información útil en nuestro proceso de huellas.`mssql_ping`

#### Ping de MSSQL en Metasploit

  MSSQL

```shell-session
msf6 auxiliary(scanner/mssql/mssql_ping) > set rhosts 10.129.201.248

rhosts => 10.129.201.248


msf6 auxiliary(scanner/mssql/mssql_ping) > run

[*] 10.129.201.248:       - SQL Server information for 10.129.201.248:
[+] 10.129.201.248:       -    ServerName      = SQL-01
[+] 10.129.201.248:       -    InstanceName    = MSSQLSERVER
[+] 10.129.201.248:       -    IsClustered     = No
[+] 10.129.201.248:       -    Version         = 15.0.2000.5
[+] 10.129.201.248:       -    tcp             = 1433
[+] 10.129.201.248:       -    np              = \\SQL-01\pipe\sql\query
[*] 10.129.201.248:       - Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```

#### Conectando con Mssqlclient.py

Si podemos adivinar u obtener acceso a las credenciales, esto nos permite conectarnos de forma remota al servidor MSSQL y comenzar a interactuar con las bases de datos usando T-SQL (). La autenticación con MSSQL nos permitirá interactuar directamente con las bases de datos a través de SQL Database Engine. Desde Pwnbox o un host de ataque personal, podemos usar el mssqlclient.py de Impacket para conectarnos como se ve en la salida a continuación. Una vez conectado al servidor, puede ser bueno tener una idea del terreno y enumerar las bases de datos presentes en el sistema.`Transact-SQL`

  MSSQL

```shell-session
zunderrubb@htb[/htb]$ python3 mssqlclient.py Administrator@10.129.201.248 -windows-auth

Impacket v0.9.22 - Copyright 2020 SecureAuth Corporation

Password:
[*] Encryption required, switching to TLS
[*] ENVCHANGE(DATABASE): Old Value: master, New Value: master
[*] ENVCHANGE(LANGUAGE): Old Value: , New Value: us_english
[*] ENVCHANGE(PACKETSIZE): Old Value: 4096, New Value: 16192
[*] INFO(SQL-01): Line 1: Changed database context to 'master'.
[*] INFO(SQL-01): Line 1: Changed language setting to us_english.
[*] ACK: Result: 1 - Microsoft SQL Server (150 7208) 
[!] Press help for extra shell commands

SQL> select name from sys.databases

name                                                                                                                               

--------------------------------------------------------------------------------------

master                                                                                                                             

tempdb                                                                                                                             

model                                                                                                                              

msdb                                                                                                                               

Transactions    
```


**[[SQL]]**