
----------

#privilegeescalation #comandos 

--------

|   |   |
|---|---|
|**Escalada de privilegios**||
|`./linpeas.sh`|Ejecutar script para enumerar el servidor remoto`linpeas`|
|`sudo -l`|Enumerar los privilegios disponibles`sudo`|
|`sudo -u user /bin/echo Hello World!`|Ejecute un comando con `sudo`|
|`sudo su -`|Cambiar a usuario root (si tenemos acceso a `sudo su`)|
|`sudo su user -`|Cambiar a un usuario (si tenemos acceso a `sudo su`)|
|`ssh-keygen -f key`|Crear una nueva clave SSH|
|`echo "ssh-rsa AAAAB...SNIP...M= user@parrot" >> /root/.ssh/authorized_keys`|Agregar la clave pública generada al usuario|
|`ssh root@10.10.10.10 -i key`|SSH al servidor con la clave privada generada|

**[[privilege scalation basic]]**
**[[python hijacking]]**
