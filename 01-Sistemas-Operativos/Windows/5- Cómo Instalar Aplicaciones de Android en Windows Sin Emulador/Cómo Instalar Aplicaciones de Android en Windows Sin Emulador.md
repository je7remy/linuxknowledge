
---

### **Paso 1: Activar la Virtualización en tu PC**

Lo primero que necesitamos es asegurarnos de que la virtualización esté activada en tu computadora. Esto es clave para que todo funcione.

1. **Verifica si la virtualización ya está habilitada:**
   - Haz clic derecho en la **barra de tareas** (esa barra en la parte inferior de tu pantalla) y selecciona **Administrador de Tareas**.
   - En la ventana que aparece, haz clic en la pestaña **Rendimiento** (puede estar arriba o a la izquierda).
   - Busca donde dice **CPU** o **Procesador** y haz clic ahí.
   - Mira en la parte inferior derecha. Verás una línea que dice **Virtualización**. Si dice **Habilitado**, ¡genial! Puedes pasar al Paso 2. Si dice **Deshabilitado**, sigue leyendo.

2. **Activa la virtualización en la BIOS:**
   - Reinicia tu computadora. Mientras se está encendiendo, presiona repetidamente una tecla como **F2**, **F10**, **Delete** o **Esc** (depende de tu marca de PC; prueba con F2 primero).
   - Entrarás a una pantalla rara llamada **BIOS**. Usa las flechas del teclado para buscar algo como **Virtualization Technology (VT-x)** o **AMD-V**.
   - Cámbialo a **Enabled** (habilitado). Usa las instrucciones en pantalla para saber qué tecla presionar (puede ser Enter o F5/F6).
   - Guarda los cambios (busca algo como **Save & Exit**, suele ser F10) y reinicia.
   - **Nota:** Si te pierdes, busca en YouTube “cómo activar virtualización en (marca de tu PC)”.

---

### **Paso 2: Habilitar Características de Windows**

Ahora vamos a activar un par de cosas en Windows para que el sistema de Android funcione.

1. Haz clic en el ícono de la **lupa** en la barra de tareas (o presiona la tecla Windows + S).
2. Escribe **"Activar o desactivar características de Windows"** y haz clic en esa opción cuando aparezca.
3. Se abrirá una ventana con una lista. Desplázate hacia abajo y busca:
   - **Plataforma de máquina virtual** (Virtual Machine Platform).
   - **Subsistema de Windows para Linux**.
4. Marca las casillas de esas dos opciones (haz clic en el cuadrito para que aparezca un check).
5. Haz clic en **Aceptar**. Windows te dirá que necesita reiniciarse.
6. Reinicia tu PC cuando te lo pida.

---

### **Paso 3: Descargar el Subsistema de Android**

Vamos a descargar el archivo que nos permitirá usar Android en tu PC.

1. Abre tu navegador (Chrome, Edge, Firefox, el que uses).
2. [MustardChef/WSABuilds](https://github.com/MustardChef/WSABuilds/releases/tag/Windows_11_2407.40000.4.0)
   - Si tienes **Windows 11**, usa el enlace para Windows 11.
   - Si tienes **Windows 10**, usa el enlace para Windows 10 (64 bits).
   
1. En la página que se abra, busca un botón de **descarga** (normalmente al final de la pagina).
2. Haz clic en descargar y espera a que termine.

---

### **Paso 4: Extraer e Instalar el Subsistema de Android**

Ya tienes el archivo, ahora lo extraemos e instalamos.

1. Busca el archivo que descargaste (probablemente esté en **Descargas**). Muévelo a una carpeta fácil de encontrar, como **Documentos**.
2. Haz clic derecho sobre el archivo y elige **Extraer todo**. Si no ves esa opción, descarga un programa como WinRAR o 7-Zip y úsalo para extraerlo.
3. Abre la carpeta que se creó al extraer.
4. Busca un archivo llamado **run.bat** (o solo **run** si no ves extensiones).
5. Haz clic derecho en ese archivo y selecciona **Ejecutar como administrador** (puede pedirte permiso; di que sí).
6. Se abrirá una ventana negra con letras (la consola). Espera a que termine y se cierre sola.
7. Cuando acabe, la **Play Store** se abrirá automáticamente en tu pantalla.

---

### **Paso 5: Configurar la Play Store**

¡Ya casi estamos! Ahora configuramos la Play Store con tu cuenta de Google.

1. En la Play Store que se abrió, haz clic en **Iniciar sesión**.
2. Escribe tu correo de Google (o número de teléfono) y tu contraseña.
3. Si te pide aceptar términos, hazlo.
4. Puede que la Play Store se cierre sola después de esto. Si pasa, no te preocupes. Ve al menú de **Inicio** (el botón de Windows abajo a la izquierda) y busca **Play Store** para abrirla de nuevo.

---

### **Paso 6: Descargar e Instalar Downloader**

Vamos a instalar una app llamada Downloader, que nos ayudará a poner otras aplicaciones.

1. En la Play Store, haz clic en la **lupa** de búsqueda (arriba).
2. Escribe **"Downloader"** y presiona Enter.
3. Busca la app **Downloader** (suele ser la primera) y haz clic en **Instalar**.
4. Cuando termine, haz clic en **Abrir** (o ciérrala por ahora, la usaremos en el siguiente paso).

---

### **Paso 7: Usar Downloader para Instalar Otras Aplicaciones**

Con Downloader, puedes instalar cualquier app de Android con un código.

1. Abre **Downloader** (búscala en el menú de **Inicio** si la cerraste).
2. Verás un cuadro donde puedes escribir. Pega el código que quieras usar (281518 para magis tv).
3. Haz clic en **Go** o presiona Enter.
4. Espera a que descargue el archivo. Cuando termine, te pedirá permisos para instalar apps de "orígenes desconocidos".
5. Haz clic en **Configuración** y activa la opción para permitir que Downloader instale cosas.
6. Vuelve a Downloader y haz clic en **Instalar**.
7. Espera a que termine la instalación.

---

### **Paso 8: Acceder a las Aplicaciones Instaladas**

¡Ya casi terminamos! Ahora veamos cómo usar lo que instalaste.

1. Ve al menú de **Inicio** (botón de Windows abajo a la izquierda).
2. Haz clic en **Todas las aplicaciones** (puede que tengas que desplazarte).
3. Busca la app que instalaste (como la "magis tv").
4. Si quieres un acceso directo, haz clic derecho en la app y selecciona **Agregar al escritorio** (o arrástrala al escritorio si puedes).
5. ¡Listo! Haz doble clic en el ícono para abrirla.
