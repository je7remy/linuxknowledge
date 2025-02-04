# **Configuración y Prueba de Seguridad en Apache contra Fuzzing Web**

Hace poco me puse a probar la seguridad de un servidor Apache contra ataques de fuzzing. Aquí te cuento paso a paso cómo lo configuré y los resultados que obtuve.

---

## **1. Identificación de la Red y el Servidor Apache**

Lo primero fue ubicar la IP del servidor. Desde la máquina atacante, ejecuté:

```bash
ip a
```

Luego escaneé la red local para encontrar dispositivos activos:

```bash
sudo arp-scan -I enp0s3 --localnet
```

Ahí vi varias IPs, y algunas MAC comenzaban con `08:00`, lo que me dio la pista de que se trataba de una máquina virtual. Para confirmar que Apache estaba corriendo, pasé un escaneo rápido con `dirb`:

```bash
dirb http://192.168.118.205
```

Esto me mostró que había un directorio `/public`, lo cual indicaba que el servidor estaba funcionando y accesible.

---

## **2. Instalación y Configuración de `mod_evasive` en Apache**

Sabía que `mod_evasive` era una buena opción para bloquear ataques automáticos, así que lo instalé.  
Primero, entré como root:

```bash
sudo su
```

Después, me moví al directorio web (aunque esto no era estrictamente necesario para la instalación):

```bash
cd /var/www/html/public/
```

Luego instalé el módulo:

```bash
apt install libapache2-mod-evasive
```

Para configurarlo, edité su archivo de configuración:

```bash
nano /etc/apache2/mods-available/evasive.conf
```

Ahí descomenté todas las líneas y agregué esta configuración clave:

```bash
DOSSystemCommand    "sudo /sbin/iptables -A INPUT -s  %s -j DROP"
```

Esto le dice a Apache que bloquee automáticamente cualquier IP que intente hacer fuzzing.

---

## **3. Verificación y Aplicación de la Configuración**

Para asegurarme de que `mod_evasive` estaba activado, ejecuté:

```bash
apache2ctl -M
apache2ctl -M | grep evasive
```

Luego reinicié Apache para aplicar los cambios:

```bash
systemctl restart apache2
```

---

## **4. Prueba de Seguridad con `dirb`**

El siguiente paso fue probar si realmente estaba bloqueando ataques. Volví a lanzar `dirb`:

```bash
dirb http://192.168.118.205
```

Como `mod_evasive` estaba activado, después de varias solicitudes, la IP atacante fue bloqueada automáticamente por unos 10 segundos. Se notó porque los intentos posteriores devolvían errores de conexión.

---

## **Resultado Final**

¡Funcionó como esperaba! Apache detectó el comportamiento de fuzzing y bloqueó la IP atacante usando `iptables`. Esto evitó que siguiera enviando más solicitudes por un tiempo determinado.

### **Conclusión y Recomendaciones**

Con esta configuración, logré mejorar la seguridad del servidor contra ataques de enumeración de directorios y fuerza bruta. Sin embargo, recomiendo revisar los logs en:

```bash
/var/log/mod_evasive
```

Para ajustar los parámetros según el tráfico normal del sitio y evitar falsos positivos.

Definitivamente, `mod_evasive` es una herramienta útil para reforzar la seguridad de Apache contra ataques automatizados.