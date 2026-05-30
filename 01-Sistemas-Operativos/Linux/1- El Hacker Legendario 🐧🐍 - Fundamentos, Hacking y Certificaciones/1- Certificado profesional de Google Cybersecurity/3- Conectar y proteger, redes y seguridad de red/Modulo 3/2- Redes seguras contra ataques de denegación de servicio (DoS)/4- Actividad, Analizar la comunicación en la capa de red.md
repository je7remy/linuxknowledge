---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-3]
actualizado: 2026-05-28
---

# Actividad, Analizar la comunicación en la capa de red
## 🛡️ Informe de Incidente de Ciberseguridad

### 📌 Parte 1: Resumen del análisis del registro `tcpdump`

**Resumen del problema encontrado:**

El sitio web **[www.yummyrecipesforme.com](http://www.yummyrecipesforme.com/)** no está disponible para múltiples usuarios, mostrando el error “**puerto de destino inalcanzable**”. El análisis del tráfico de red capturado con `tcpdump` indica que el cliente realiza correctamente solicitudes DNS usando **UDP al puerto 53**, pero recibe mensajes de error ICMP de tipo “**udp port 53 unreachable**”.

**Protocolos implicados:**

- **UDP**: utilizado para enviar consultas DNS al servidor `203.0.113.2`.
    
- **ICMP**: el servidor responde con errores que indican que el puerto 53 no está disponible.
    

**Fragmento del registro `tcpdump`:**

```
13:24:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable length 254
```

**Interpretación técnica:**

Cada vez que el cliente intenta resolver el dominio mediante DNS (paquetes UDP al puerto 53), el servidor devuelve una respuesta ICMP indicando que **no hay servicio escuchando en el puerto 53**. Esto se repite en diferentes momentos (13:24, 13:26 y 13:28), lo cual confirma que el servicio DNS está inactivo o mal configurado.

---

### 🔍 Parte 2: Análisis del incidente y causa raíz

**Hora del incidente:**  
Primer intento registrado a las **13:24:32**.

**Escenario:**  
Los usuarios no pueden acceder al sitio web. El navegador intenta resolver la dirección IP de `www.yummyrecipesforme.com`, pero falla en la etapa DNS. Esto impide que se inicie la conexión HTTPS.

**Estado actual:**  
El sitio web no puede resolverse por nombre, ya que el **servidor DNS no responde en el puerto 53**.

**Hallazgos clave:**

- El error **“udp port 53 unreachable”** se origina desde `203.0.113.2`.
    
- La dirección `192.51.100.15` (el cliente) envía la solicitud correctamente.
    
- El servicio DNS **no está disponible en el servidor**, ya sea por caída, error de configuración o bloqueo.
    

**Pasos recomendados:**

1. Verificar si el servicio DNS está corriendo en `203.0.113.2`.
    
2. Asegurar que **puerto 53 UDP** esté abierto y accesible.
    
3. Revisar configuraciones de firewall y logs del servidor DNS.
    
4. Reiniciar el servicio DNS si es necesario.
    
5. Monitorear el servidor para asegurar disponibilidad sostenida.
    

**Causa raíz presunta:**  
El **puerto 53 UDP** del servidor DNS `203.0.113.2` **no está disponible** para procesar solicitudes, lo cual impide la resolución de nombres y causa la caída del acceso al sitio.

---

---

## Navegación

- ⬆️ Carpeta: [[_3- Conectar y proteger, redes y seguridad de red|3- Conectar y proteger, redes y seguridad de red]]
- ⬅️ Anterior: [[3- Ataque DDoS en la vida real]]
- ➡️ Siguiente: [[5- Ejemplar de actividad, Analizar la comunicación en la capa de red]]
