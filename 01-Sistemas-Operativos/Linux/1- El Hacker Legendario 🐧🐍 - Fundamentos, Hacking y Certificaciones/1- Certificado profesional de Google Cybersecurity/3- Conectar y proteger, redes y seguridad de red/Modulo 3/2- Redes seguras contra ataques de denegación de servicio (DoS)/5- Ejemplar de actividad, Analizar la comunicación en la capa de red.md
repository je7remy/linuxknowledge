
## 📝 **Informe de Incidente de Ciberseguridad**

### 1. **Resumen del incidente**

**Fecha/Hora del incidente:**

- Inició aproximadamente a las 13:24, según el registro `tcpdump`.
    

**Descripción del problema:**  
Usuarios reportaron que no podían acceder al sitio web `www.yummyrecipesforme.com`. Al intentar visitar la página, se muestra el error: **"puerto de destino inalcanzable"**.

**Hallazgos clave del análisis:**

- El navegador del usuario envió solicitudes DNS utilizando **UDP al puerto 53** del servidor DNS `203.0.113.2`.
    
- En lugar de respuestas DNS válidas, el sistema recibió múltiples **mensajes ICMP** con el error:  
    `udp port 53 unreachable`.
    
- Se confirmó el envío repetido de solicitudes DNS y la recepción repetida del mismo mensaje de error, lo que indica que **el servicio DNS no está disponible o inaccesible**.
    

**Protocolos implicados:**

- **UDP** (Puerto 53): Protocolo usado para consultas DNS.
    
- **ICMP**: Utilizado para enviar mensajes de error que indican que el puerto solicitado está inalcanzable.
    

---

### 2. **Análisis y evaluación**

**Motivo del error:**

- La dirección IP `203.0.113.2` no está respondiendo adecuadamente a las solicitudes DNS.
    
- El servicio DNS no parece estar escuchando en el puerto 53 o podría estar apagado o bloqueado.
    

**Impacto del problema:**

- Los usuarios no pueden resolver el dominio `www.yummyrecipesforme.com`, por lo tanto, **el acceso al sitio web está bloqueado**.
    
- Puede afectar la continuidad de las operaciones y causar **pérdida de acceso a servicios en línea** para clientes y empleados.
    

**Posible causa raíz:**

- El **servidor DNS está inactivo**.
    
- **Fallo en el servicio DNS** o enrutamiento incorrecto hacia el puerto 53.
    
- **Política de red o firewall** que bloquea el tráfico entrante en el puerto 53.
    

---

### 3. **Recomendaciones y siguientes pasos**

✅ **Acciones sugeridas:**

- Verificar si el servicio DNS en el servidor `203.0.113.2` está en funcionamiento.
    
- Confirmar que el puerto UDP 53 está abierto y accesible desde dispositivos externos.
    
- Revisar las reglas del firewall y configuración de red.
    
- Cambiar temporalmente a otro servidor DNS funcional si es necesario (como 8.8.8.8 de Google).
    

🔁 **Siguientes pasos:**

- Escalar el incidente al equipo de red para que reinicien o reconfiguren el servidor DNS.
    
- Documentar este incidente y actualizar los registros de cambios.
    
- Implementar un monitoreo más estricto del estado de los servidores DNS en producción.
    

---

