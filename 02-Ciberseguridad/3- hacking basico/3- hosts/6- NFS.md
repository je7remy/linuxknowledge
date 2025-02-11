
---------
#nfs #comando #mount 

---------

`Network File System` (`NFS`) es un sistema de archivos de red desarrollado por Sun Microsystems y tiene el mismo propósito que SMB. Su propósito es acceder a los sistemas de archivos a través de una red como si fueran locales. Sin embargo, utiliza un protocolo completamente diferente. [NFS](https://en.wikipedia.org/wiki/Network_File_System) se utiliza entre sistemas Linux y Unix. Esto significa que los clientes NFS no pueden comunicarse directamente con los servidores SMB. NFS es un estándar de Internet que gobierna los procedimientos en un sistema de archivos distribuido. Mientras que la versión 3.0 del protocolo NFS (), que ha estado en uso durante muchos años, autentica el equipo cliente, esto cambia con . Aquí, al igual que con el protocolo SMB de Windows, el usuario debe autenticarse.`NFSv3``NFSv4`




Al ocupar NFS, los puertos TCP son esenciales. También podemos obtener información sobre el servicio NFS y el host a través de RPC, como se muestra a continuación en el ejemplo.`111``2049`

#### Nmap

  NFS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap 10.129.14.128 -p111,2049 -sV -sC

Starting Nmap 7.80 ( https://nmap.org ) at 2021-09-19 17:12 CEST
Nmap scan report for 10.129.14.128
Host is up (0.00018s latency).

PORT    STATE SERVICE VERSION
111/tcp open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      41982/udp6  mountd
|   100005  1,2,3      45837/tcp   mountd
|   100005  1,2,3      47217/tcp6  mountd
|   100005  1,2,3      58830/udp   mountd
|   100021  1,3,4      39542/udp   nlockmgr
|   100021  1,3,4      44629/tcp   nlockmgr
|   100021  1,3,4      45273/tcp6  nlockmgr
|   100021  1,3,4      47524/udp6  nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp open  nfs_acl 3 (RPC #100227)
MAC Address: 00:00:00:00:00:00 (VMware)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.58 seconds
```

El script NSE recupera una lista de todos los servicios RPC que se están ejecutando actualmente, sus nombres y descripciones, y los puertos que usan. Esto nos permite comprobar si el recurso compartido de destino está conectado a la red en todos los puertos necesarios. Además, para NFS, Nmap tiene algunos scripts NSE que se pueden usar para los escaneos. Estos pueden mostrarnos, por ejemplo, el de la acción y su .`rpcinfo``contents``stats`

  NFS

```shell-session
zunderrubb@htb[/htb]$ sudo nmap --script nfs* 10.129.14.128 -sV -p111,2049

Starting Nmap 7.80 ( https://nmap.org ) at 2021-09-19 17:37 CEST
Nmap scan report for 10.129.14.128
Host is up (0.00021s latency).

PORT     STATE SERVICE VERSION
111/tcp  open  rpcbind 2-4 (RPC #100000)
| nfs-ls: Volume /mnt/nfs
|   access: Read Lookup NoModify NoExtend NoDelete NoExecute
| PERMISSION  UID    GID    SIZE  TIME                 FILENAME
| rwxrwxrwx   65534  65534  4096  2021-09-19T15:28:17  .
| ??????????  ?      ?      ?     ?                    ..
| rw-r--r--   0      0      1872  2021-09-19T15:27:42  id_rsa
| rw-r--r--   0      0      348   2021-09-19T15:28:17  id_rsa.pub
| rw-r--r--   0      0      0     2021-09-19T15:22:30  nfs.share
|_
| nfs-showmount: 
|_  /mnt/nfs 10.129.14.0/24
| nfs-statfs: 
|   Filesystem  1K-blocks   Used       Available   Use%  Maxfilesize  Maxlink
|_  /mnt/nfs    30313412.0  8074868.0  20675664.0  29%   16.0T        32000
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      41982/udp6  mountd
|   100005  1,2,3      45837/tcp   mountd
|   100005  1,2,3      47217/tcp6  mountd
|   100005  1,2,3      58830/udp   mountd
|   100021  1,3,4      39542/udp   nlockmgr
|   100021  1,3,4      44629/tcp   nlockmgr
|   100021  1,3,4      45273/tcp6  nlockmgr
|   100021  1,3,4      47524/udp6  nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp open  nfs_acl 3 (RPC #100227)
MAC Address: 00:00:00:00:00:00 (VMware)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 0.45 seconds
```

Una vez que hemos descubierto un servicio NFS de este tipo, podemos montarlo en nuestra máquina local. Para ello, podemos crear una nueva carpeta vacía en la que se montará el recurso compartido NFS. Una vez montado, podemos navegar por él y ver el contenido al igual que nuestro sistema local.

#### Mostrar recursos compartidos NFS disponibles

  NFS

```shell-session
zunderrubb@htb[/htb]$ showmount -e 10.129.14.128

Export list for 10.129.14.128:
/mnt/nfs 10.129.14.0/24
```

#### Montaje de NFS Share

  NFS

```shell-session
zunderrubb@htb[/htb]$ mkdir target-NFS
zunderrubb@htb[/htb]$ sudo mount -t nfs 10.129.14.128:/ ./target-NFS/ -o nolock
zunderrubb@htb[/htb]$ cd target-NFS
zunderrubb@htb[/htb]$ tree .

.
└── mnt
    └── nfs
        ├── id_rsa
        ├── id_rsa.pub
        └── nfs.share

2 directories, 3 files
```

Allí tendremos la oportunidad de acceder a los derechos y a los nombres de usuario y grupos a los que pertenecen los archivos mostrados y visibles. Porque una vez que tenemos los nombres de usuario, los nombres de grupo, los UID y los GUID, podemos crearlos en nuestro sistema y adaptarlos al recurso compartido NFS para ver y modificar los archivos.

#### Listar contenidos con nombres de usuario y nombres de grupo

  NFS

```shell-session
zunderrubb@htb[/htb]$ ls -l mnt/nfs/

total 16
-rw-r--r-- 1 cry0l1t3 cry0l1t3 1872 Sep 25 00:55 cry0l1t3.priv
-rw-r--r-- 1 cry0l1t3 cry0l1t3  348 Sep 25 00:55 cry0l1t3.pub
-rw-r--r-- 1 root     root     1872 Sep 19 17:27 id_rsa
-rw-r--r-- 1 root     root      348 Sep 19 17:28 id_rsa.pub
-rw-r--r-- 1 root     root        0 Sep 19 17:22 nfs.share
```

#### Contenido de la lista con UID y GUID

  NFS

```shell-session
zunderrubb@htb[/htb]$ ls -n mnt/nfs/

total 16
-rw-r--r-- 1 1000 1000 1872 Sep 25 00:55 cry0l1t3.priv
-rw-r--r-- 1 1000 1000  348 Sep 25 00:55 cry0l1t3.pub
-rw-r--r-- 1    0 1000 1221 Sep 19 18:21 backup.sh
-rw-r--r-- 1    0    0 1872 Sep 19 17:27 id_rsa
-rw-r--r-- 1    0    0  348 Sep 19 17:28 id_rsa.pub
-rw-r--r-- 1    0    0    0 Sep 19 17:22 nfs.share
```

Es importante tener en cuenta que si la opción está configurada, no podemos editar el archivo incluso como .`root_squash``backup.sh``root`

También podemos usar NFS para una mayor escalada. Por ejemplo, si tenemos acceso al sistema a través de SSH y queremos leer archivos de otra carpeta que un usuario específico pueda leer, necesitaríamos cargar un shell en el recurso compartido NFS que tiene el de ese usuario y luego ejecutar el shell a través del usuario SSH.`SUID`

Una vez que hayamos realizado todos los pasos necesarios y obtenido la información que necesitamos, podemos desmontar el recurso compartido NFS.

#### Desmontar

  NFS

```shell-session
zunderrubb@htb[/htb]$ cd ..
zunderrubb@htb[/htb]$ sudo umount ./target-NFS
```