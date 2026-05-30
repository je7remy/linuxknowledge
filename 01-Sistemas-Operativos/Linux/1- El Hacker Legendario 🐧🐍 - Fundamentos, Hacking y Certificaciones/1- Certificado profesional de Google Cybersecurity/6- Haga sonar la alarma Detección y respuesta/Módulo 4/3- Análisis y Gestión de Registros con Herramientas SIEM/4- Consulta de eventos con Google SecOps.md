---
tipo: teoria
tags: [el-hacker-legendario, google-cybersecurity, modulo-4]
actualizado: 2026-05-28
---

# Consulta de eventos con Google SecOps

# 🔎 Chronicle: buscar y filtrar eventos (UDM & YARA-L)

## 🧠 TL;DR

- **Campo de búsqueda**: puedes buscar por `hostname`, `domain`, `ip`, `url`, `email`, `username`, `file.hash`, etc.
    
- **Modo por defecto**: **UDM Search** (Modelo de Datos Unificado) → busca en **datos normalizados** (más rápido y consistente).
    
- **Alternativa**: **Raw Log Search** → busca en **registros sin normalizar** (útil para campos no mapeados o troubleshooting de ingesta).
    
- **Detección avanzada**: **YARA-L** → lenguaje para **reglas de detección** sobre los datos ingeridos.
    

---

## 🧩 UDM Search (datos normalizados)

### Campos UDM habituales

- `metadata.event_type` → tipo de evento (p. ej., `USER_LOGIN`, `NETWORK_DNS`, `PROCESS_START`).
    
- `security_result.action` → acción de seguridad (p. ej., `ALLOW`, `BLOCK`).
    
- `principal.*` / `target.*` → sujeto y destino (usuario, ip, hostname, etc.).
    
- `network.*`, `http.*`, `file.*` → detalles por tipo de evento.
    

### Ejemplo: inicios de sesión bloqueados

```udm
metadata.event_type = "USER_LOGIN"
AND security_result.action = "BLOCK"
```

### Afinar con filtros rápidos

- Filtrar por IP de destino:
    
    - Selecciona en la UI `target.ip = 203.0.113.25` (o agrega a la consulta).
        
- Acotar por tiempo (selector de rango):
    
    - Últimas 24 h / 7 d / 30 d (cuanto más específico, mejor rendimiento).
        

### Consejos de búsqueda efectiva

- Empieza en **UDM**; cambia a **Raw** sólo si falta un campo.
    
- Añade **rango temporal** y **atributos concretos** (host, usuario, IP) para acelerar y hacer más relevantes los resultados.
    
- Usa la **línea de tiempo** para detectar **picos** y patrones.
    

---

## 🧾 Raw Log Search (registros sin normalizar)

Úsalo cuando:

- Necesitas un **campo** que aún **no está mapeado** a UDM.
    
- Estás **debuggeando la ingesta** o los **parsers**.
    
- Quieres ver **texto exacto** del evento tal como llegó.
    

> Recuerda: al no estar indexados de forma uniforme, las búsquedas **suelen ser más lentas** que en UDM.

---

## 🛡️ YARA-L (reglas de detección en Chronicle)

**Qué es**: lenguaje para **definir reglas** que detectan patrones de seguridad en los datos ingeridos (similar a YARA conceptual, con estructura orientada a eventos/condiciones en Chronicle).

### Esqueleto (simplificado y orientativo)

```yaral
rule Suspicious_Blocked_Login_MultiHost {
  meta:
    product = "Chronicle"
    author = "analyst@example.com"
    description = "Múltiples USER_LOGIN bloqueados para el mismo usuario desde IPs distintas en 10m"

  events:
    $e.metadata.event_type = "USER_LOGIN"
    $e.security_result.action = "BLOCK"

  condition:
    // Al menos 5 eventos para el mismo usuario desde >=3 IPs diferentes en 10 minutos
    count_unique($e.target.ip) >= 3 and
    count($e, window=10m, by=$e.principal.user.user_id) >= 5
}
```

> **Idea clave**: en `events` defines el patrón; en `condition` marcas **umbral/ventana** y agregaciones (conteos únicos, etc.). Los nombres exactos de funciones/atributos pueden variar según versión; la lógica es lo importante.

---

## 📚 Mini-chuleta (cheat sheet)

**Cuándo UDM vs Raw**

- ✔ UDM: la mayoría de casos, rendimiento y consistencia.
    
- ✔ Raw: campo no normalizado / diagnóstico de ingesta.
    

**Campos UDM útiles**

- Autenticación: `metadata.event_type="USER_LOGIN"`, `principal.user.user_id`, `target.ip`
    
- Red: `network.ip`, `network.port`, `domain.name`
    
- Ficheros: `file.hash.sha256`, `file.name`, `file.path`
    
- Resultado: `security_result.action` (ALLOW/BLOCK), `security_result.category`
    

**Patrones típicos**

- Logins bloqueados: `metadata.event_type="USER_LOGIN" AND security_result.action="BLOCK"`
    
- DNS sospechoso: `metadata.event_type="NETWORK_DNS" AND domain.name = "*.weird-tld"`
    
- Descargas: `metadata.event_type="HTTP_REQUEST" AND http.request.method="GET" AND url.url = "..."`
    
- Ficheros: `file.hash.sha256 = "<hash>"`
    

---

## 🧪 Ejercicios de práctica (con soluciones al final)

1. **UDM básico**  
    Devuelve **logins bloqueados** del usuario `alice` en las **últimas 24 h**.
    
2. **Filtrado por IP**  
    Muestra **USER_LOGIN** con `target.ip = 198.51.100.77` y **acción ALLOW**.
    
3. **Pivot rápido**  
    A partir de un evento de `USER_LOGIN` bloqueado, **añade un filtro** para ver solo el **host afectado**.
    
4. **Raw vs UDM**  
    Necesitas el **header HTTP** exacto que no está en UDM.  
    ¿Usas UDM o Raw? ¿Por qué?
    
5. **YARA-L (conceptual)**  
    Diseña una condición que **dispare** cuando haya **≥10** inicios de sesión **BLOCK** del **mismo usuario** en **5 minutos**.
    

---

## ✅ Soluciones (breves)

```udm
metadata.event_type = "USER_LOGIN"
AND security_result.action = "BLOCK"
AND principal.user.user_id = "alice"
```

_(Selecciona rango de tiempo “Últimas 24 h” en la UI)._

```udm
metadata.event_type = "USER_LOGIN"
AND target.ip = "198.51.100.77"
AND security_result.action = "ALLOW"
```

- Haz clic en el evento → usa filtro rápido del campo `target.hostname` (o `asset.host_name`).
    
- Alternativamente agrega: `AND target.hostname = "host123.acme.local"`.
    

**Raw Log Search**. Necesitas el **texto exacto** no mapeado a UDM → busca en **registros sin normalizar**.

5. _(YARA-L idea)_
    

- `events`: USER_LOGIN con action BLOCK para el mismo `principal.user.user_id`.
    
- `condition`: `count($e, window=5m, by=$e.principal.user.user_id) >= 10`.
    

---

## 🧭 Siguientes pasos

- Repite las búsquedas con diferentes **rango de tiempo** y **usuarios**.
    
- Toma un evento interesante y **pivota** por IP/host/dominio.
    
- Intenta traducir una búsqueda UDM a una **regla YARA-L** con ventana temporal.
    

## Pregunta

Rellene el espacio en blanco: Chronicle utiliza _____ para buscar entre datos normalizados.

Modelo unificado de datos (UDM)

Lenguaje de Consulta Estructurado (SQL)

Lenguaje de Procesamiento de Búsqueda (SPL)

Formato de Evento Extensible JavaScript Object Notation (EVE JSON)

Correcto

Chronicle utiliza UDM para buscar entre los Datos normalizados.
**Respuesta:** Modelo unificado de datos (**UDM**).

**Por qué:** En Chronicle, las búsquedas por defecto se hacen sobre **datos normalizados** usando **UDM Search** (campos como `metadata.event_type`, `security_result.action`, `target.ip`, etc.).  
Ejemplo:

```
metadata.event_type="USER_LOGIN" AND security_result.action="BLOCK"
```

---

## Navegación

- ⬆️ Carpeta: [[_6- Haga sonar la alarma Detección y respuesta|6- Haga sonar la alarma Detección y respuesta]]
- ⬅️ Anterior: [[3- Consulta de Eventos con Splunk]]
- ➡️ Siguiente: [[5- Métodos de búsqueda con herramientas SIEM]]
