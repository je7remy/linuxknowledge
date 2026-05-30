---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Servidores proxy


## 🛡️ Servidores Proxy: Protección para Redes Internas

Un **servidor proxy** actúa como intermediario entre los dispositivos de una red privada e Internet. Su función principal es **reenviar solicitudes** de los clientes a otros servidores, **filtrar el tráfico** y **ocultar las direcciones IP reales** de la red interna.

---

### 📌 Beneficios de Seguridad de un Proxy

- **Oculta la IP real** de la red privada.
    
- **Filtra conexiones inseguras** entrantes y salientes.
    
- **Bloquea el acceso a sitios no seguros.**
    
- **Reduce el contacto con servidores internos** al usar memoria caché.
    
- **Mejora la privacidad y el anonimato.**
    

---

### 💡 Ejemplo práctico

> Cuando un usuario recibe una respuesta HTTPS desde un servidor web protegido por proxy, ve una **IP alterada o anónima**, en lugar de la IP real del servidor de la organización.

---

## 🧰 Tipos de Servidores Proxy

|Tipo de Proxy|Función principal|
|---|---|
|**Proxy directo**|Oculta la IP del **usuario** y regula las solicitudes salientes hacia Internet.|
|**Proxy de reenvío**|Aprueba y reenvía el tráfico saliente de los **empleados** a su destino.|
|**Proxy inverso**|Controla el tráfico **entrante** antes de que llegue a servidores internos.|
|**Proxy de correo electrónico**|Filtra **correo no deseado (spam)** y previene ataques de suplantación.|

---

### ✉️ Caso real: Proxy de correo

> En un ISP de EE.UU., un servidor proxy etiquetó como **spam el 95% del correo** antes de que llegara al sistema interno. Se usaron varios niveles de **filtrado sin afectar la plataforma de correo principal.**

---

### 🔒 Conclusión

Los servidores proxy son esenciales para:

- **Reducir la exposición directa** a Internet.
    
- **Evitar ataques de suplantación.**
    
- **Controlar y filtrar el tráfico** de manera inteligente.
    
- **Proteger servidores internos críticos.**
    

---


### 📝 Pregunta:

**Rellene el espacio en blanco:**  
Un(a) **_____** regula y restringe el acceso de Internet a un servidor interno.

---

### ✅ Respuesta correcta:

**Servidor proxy inverso**

---

📌 **Explicación:**  
Un **servidor proxy inverso** actúa como intermediario entre Internet y un **servidor interno**, controlando el tráfico entrante. Su función es **ocultar la dirección IP del servidor interno**, filtrar solicitudes externas y añadir una capa adicional de seguridad.

---

---

## Navegación

- ⬆️ Carpeta: [[_3- Conectar y proteger, redes y seguridad de red|3- Conectar y proteger, redes y seguridad de red]]
- ⬅️ Anterior: [[4- División en subredes y CIDR]]
- ➡️ Siguiente: [[6- Redes virtuales y privacidad]]
