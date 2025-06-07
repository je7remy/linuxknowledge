
### Instalación de Docker en Linux (Distribuciones Basadas en Debian)

**Paso 1: Preparación inicial**

Lo primero que debemos hacer antes de instalar Docker es asegurarnos de que los repositorios de nuestra distribución de Linux estén actualizados. Esto es fundamental, ya que de esta manera garantizamos que estamos instalando la versión más reciente de Docker disponible en los repositorios oficiales. Para hacerlo, vamos a abrir una terminal en nuestra máquina.

- En Ubuntu o cualquier distribución basada en Debian, abre una terminal. Si no sabes cómo, ve a tu cajón de aplicaciones, busca "Terminal" y ábrelo.
    

**Paso 2: Actualizar los repositorios**

Antes de proceder con la instalación de Docker, es recomendable actualizar los repositorios del sistema para obtener los últimos paquetes disponibles. Esto lo hacemos con el siguiente comando:

```bash
sudo apt update
```

- **Explicación:** El comando `sudo apt update` le indica al sistema que actualice la información de los repositorios para obtener la lista más actualizada de los paquetes disponibles. Asegúrate de tener los permisos de administrador para poder ejecutar este comando, por eso se usa `sudo`.
    

**Paso 3: Instalar Docker**

Una vez que hemos actualizado los repositorios, es hora de instalar Docker en el sistema. Para ello, ejecutamos el siguiente comando:

```bash
sudo apt install docker.io
```

- **Explicación:** Este comando le dice al sistema que instale Docker desde los repositorios oficiales. Docker.io es el paquete oficial de Docker para distribuciones basadas en Debian.
    

**Paso 4: Ingresar la contraseña de administrador**

Después de ejecutar el comando, el sistema te pedirá que ingreses tu contraseña de administrador para confirmar que tienes permisos para realizar la instalación. Simplemente ingresa tu contraseña y presiona Enter.

**Paso 5: Verificar la instalación**

Una vez que Docker esté instalado, es importante verificar que se haya instalado correctamente y esté funcionando bien. Para esto, ejecutamos el siguiente comando:

```bash
sudo docker --version
```

- **Explicación:** Este comando nos devolverá la versión instalada de Docker. Si la instalación fue exitosa, deberías ver algo como:
    

```
Docker version 20.10.7, build f0df350
```

- **Comando adicional para comprobar imágenes:** Puedes usar también el siguiente comando para verificar las imágenes que Docker tiene en tu sistema:
    

```bash
sudo docker images
```

Esto debería mostrarte una lista de imágenes Docker disponibles en tu sistema.

**Paso 6: Ejecutar Docker sin `sudo` (opcional)**

Por defecto, para ejecutar comandos de Docker, necesitarás usar `sudo` cada vez. Si quieres ejecutar los comandos de Docker sin tener que escribir `sudo` cada vez, puedes añadir tu usuario al grupo de Docker. Esto lo hacemos con el siguiente comando:

```bash
sudo usermod -aG docker $USER
```

- **Explicación:** Este comando agrega tu usuario al grupo `docker`, lo que te permitirá ejecutar los comandos de Docker sin tener que anteponer `sudo` cada vez. Después de ejecutar este comando, tendrás que cerrar sesión y volver a iniciarla para que los cambios tomen efecto.
    

**Paso 7: Probar comandos sin `sudo`**

Una vez que hayas cerrado y vuelto a iniciar sesión, puedes probar ejecutar un comando de Docker sin `sudo`, como:

```bash
docker images
```

Si todo está configurado correctamente, este comando debería ejecutarse sin pedirte la contraseña de administrador y mostrarte las imágenes disponibles en tu sistema.

---

**Resumen:**

1. **Actualiza los repositorios** de tu sistema con `sudo apt update`.
    
2. **Instala Docker** con `sudo apt install docker.io`.
    
3. **Verifica la instalación** con `sudo docker --version`.
    
4. **Opcionalmente, ejecuta Docker sin `sudo`** añadiendo tu usuario al grupo `docker`.
    

---

Esto es lo básico para instalar y configurar Docker en tu sistema. 