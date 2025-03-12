
---



---

me voy a la pagina oficial de dockerlabs y me descargo la maquina de nivel medio strongjenkins
sudo bash auto_deploy.sh strongjenkins.tar
si tiene dependencias la instalara y al final aparecera un mensaje como este

Estamos desplegando la máquina vulnerable, espere un momento.

Máquina desplegada, su dirección IP es --> 172.17.0.2

Presiona Ctrl+C cuando termines con la máquina para eliminarla

ejecutamos en el navegador 172.17.0.2:8080

![[3.1- Jenkins.png]]


nos descargamos el rockyou de toda la vida en una nueva ventana del navegador
le damos a la opcion de github
ahora nos vamos al visual studio
import requests

  

url = 'http://172.17.0.2:8080/'

en nuestra maquina virtual kali tenemos que configurar firefox para que bursuit escuche las peticiones que se le hacen a jenkins

settings > general > network settings > manual proxy configuration > http proxy172.17.0.2 > port 8080
para que bursuit lo escuche
entramos a bursuit, le damos a proxy > intercept > intercept is off > al hacer click se pone on









[[tools]]
[[0- Comandos de Hacking]]
[[1- FTP]]
[[1- Protección del Protocolo SSH]]
[[1- basic tools]]
[[2- Protección del Protocolo FTP]]
[[2- Bash Scripting Aplicado a Ciberseguridad – Script para Hacer Fuzzing Web]]
[[4- Tiempos de craqueo]]
[[6- Securización de Servidores Web Apache – Evitar Ataques de Fuzzing Web – PARTE 4]]
[[7- Bucle WHILE – Iterar por Líneas]]
[[7- Oracle TNS]]
[[8- RDP]]
[[11- SSH]]
[[12- Herramienta para hacer cracking de contraseñas]]
[[13- Automatización de Cracking de Contraseñas]]



