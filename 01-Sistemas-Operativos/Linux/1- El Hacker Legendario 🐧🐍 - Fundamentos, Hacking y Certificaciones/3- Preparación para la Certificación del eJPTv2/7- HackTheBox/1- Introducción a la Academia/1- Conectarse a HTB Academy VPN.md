---
tipo: teoria
tags: [hackthebox, vpn, openvpn, pwnbox]
actualizado: 2026-05-28
---

# Conectarse a HTB Academy VPN

## **Conectarse a la VPN de Hack The Box Academy**

Para atacar objetivos en la Academia y practicar los conocimientos adquiridos, es necesario conectarse a la red VPN de Hack The Box. Esto se puede hacer de dos maneras:

1️⃣ **Usando Pwnbox (Recomendado)**  
2️⃣ **Descargando y conectándose a un archivo VPN en tu máquina virtual**

### **1. Usar Pwnbox**

Pwnbox es una estación de trabajo en la nube completamente equipada con herramientas de ciberseguridad. Se conecta automáticamente a la VPN de la Academia, por lo que no es necesario configurar nada adicional.

🔹 Para acceder a Pwnbox:

- Dentro de la plataforma, desplázate hacia abajo y selecciona un servidor VPN cercano con baja carga.
- Presiona **"Iniciar instancia"** para generar tu entorno.
- Una vez iniciada la instancia, puedes abrirla en pantalla completa, restablecerla o agregar más tiempo.

📌 **Nota**: Si usas la versión gratuita de HTB Academy y nunca has realizado una compra, solo puedes generar Pwnbox una vez al día. Si tienes problemas, intenta restablecerla en lugar de cerrarla.

---

### **2. Conectar tu máquina virtual mediante un archivo VPN**

Si prefieres usar tu propia máquina virtual (VM), puedes conectarte a la VPN de la Academia descargando un archivo de configuración.

🔹 **Pasos para conectarse**:  
1️⃣ Descarga el archivo VPN desde la plataforma y guárdalo en tu máquina virtual.  
2️⃣ Abre una terminal y ejecuta el siguiente comando para conectarte:

```bash
sudo openvpn academy-regular.ovpn
```

3️⃣ Espera hasta que aparezca el mensaje **"Initialization Sequence Completed"**, lo que indica que la conexión ha sido exitosa.  
4️⃣ No cierres la terminal, ya que esto desconectará la VPN. En su lugar, abre una nueva pestaña para seguir trabajando.

---

### **Solución de problemas de conexión VPN**

Si tienes problemas al conectarte, prueba lo siguiente:

🔹 **Cambiar de servidor VPN**

- En la plataforma de HTB, accede a la sección de **Servidores VPN**.
- Elige un servidor con carga media o baja y descarga el nuevo archivo VPN.

🔹 **Cambiar de UDP a TCP**  
Si experimentas inestabilidad en la conexión, puedes cambiar el protocolo de UDP a TCP para mejorar el rendimiento.

✅ **Para el archivo VPN**  
Descarga un nuevo archivo VPN configurado en **TCP 443** desde la plataforma.

✅ **Para Pwnbox**  
Ejecuta el siguiente comando en la terminal de Pwnbox:

```bash
sudo sed -i 's/udp/tcp/g; s/1337/443/g; s/tls-auth/tls-crypt/g' /etc/openvpn/*.conf; sudo systemctl restart openvpn
```

Luego, revisa los registros de la VPN para confirmar que la conexión fue exitosa:

```bash
cat /var/log/openvpn/htb.log
```

---

### **⚠️ Importante**

🔹 **Solo puedes usar Pwnbox o el archivo VPN, pero no ambos al mismo tiempo.**  
🔹 Si cambias de servidor VPN en Pwnbox, todas las instancias anteriores se cerrarán automáticamente.

---

## Navegación

- ⬆️ Carpeta padre: [[_7- HackTheBox|7- HackTheBox]]
- ➡️ Siguiente: [[../2- Introducción a las pruebas de penetración/1- Introducción]] — comenzar el curso teórico.

## Relacionadas

- [[_2- Introducción a las pruebas de penetración|Curso de Introducción al Pentesting]] — siguiente material en la academia.
- [[_1- Uso Básico de Linux|Linux/Bash → Uso básico]] — comandos para operar en la VM una vez conectada.
- [[../../../0- Configuracion inicial/1- Configuración Básica de Máquina Virtual Kali Linux|Configuración Kali VM]] — alternativa a Pwnbox para usar VM propia.
