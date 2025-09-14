
### Sesión: SQL aplicado a la ciberseguridad

**Coach**  
¡Bienvenido! Durante este diálogo, nos centraremos en cómo SQL se utiliza en el campo de la ciberseguridad.

Esto es lo que cubriremos:

- **Identificar el almacenamiento de datos de seguridad**: Discutiremos dónde una empresa como SecureCorp almacenaría sus datos relacionados con la seguridad.
    
- **Conectar SQL con tareas de seguridad**: Exploraremos por qué SQL es una habilidad valiosa para los profesionales de la seguridad y qué tareas específicas se pueden realizar con él.
    
- **Aplicar SQL a escenarios de seguridad**: Analizaremos cómo se puede usar SQL para investigar situaciones de seguridad específicas.
    
- **Explorar usos más amplios de SQL**: Pensaremos en otras formas en que los profesionales de la seguridad podrían usar SQL en su trabajo diario.
    

¿Necesitas ayuda? Haz clic en _Estoy atascado_ en la parte superior derecha para obtener una pista.

Cuando estés listo, haz clic en **¡Empecemos!**

---

**Jeremy**  
Let's get started

**Coach**  
¡Excelente! Para empezar, piensa en una empresa hipotética como SecureCorp. ¿Dónde crees que una empresa así almacenaría sus datos relacionados con la seguridad, como registros de actividad o información de usuarios? ¿Qué tipos de repositorios de datos se te ocurren?

**Jeremy**  
en una empresa como securecorp los datos de seguridad se guardarían en bases de datos relacionales para la información de usuarios en sistemas centralizados de registros como un siem para los eventos y también en archivos de respaldo como csv o json

**Coach**  
¡Muy bien! Has mencionado bases de datos relacionales, sistemas SIEM (Security Information and Event Management) y archivos de respaldo como CSV o JSON. Esas son excelentes opciones para almacenar datos de seguridad.

Ahora, pasemos a **Conectar SQL con tareas de seguridad**. Considerando estos tipos de repositorios de datos, ¿por qué crees que la capacidad de usar SQL es una habilidad valiosa para un profesional de la seguridad en SecureCorp? ¿Qué tipo de tareas de seguridad específicas podrían realizar de manera eficiente usando consultas SQL?

**Jeremy**  
porque sql permite analizar grandes volúmenes de información de forma rápida y precisa en ciberseguridad es útil para detectar intentos de acceso sospechosos revisar cambios de permisos de usuarios identificar patrones anómalos en los registros y generar reportes de auditoría de manera más eficiente

**Coach**  
¡Exacto! Has captado la esencia de por qué SQL es tan valioso. La capacidad de analizar grandes volúmenes de información de forma rápida y precisa es fundamental en ciberseguridad.

---

### Escenario 1: Intentos fallidos de inicio de sesión

**Coach**  
Imagina el siguiente escenario en SecureCorp: un analista de seguridad necesita investigar repetidos intentos de inicio de sesión fallidos para un usuario específico. ¿Cómo podría usar SQL para investigar este incidente y obtener la información relevante?

**Jeremy**  
usaría sql así de directo

1. **Total de fallos del usuario**
    

```sql
select count(*) as fallidos
from login_attempts
where user_id = 123 and status = 'failed';
```

2. **Línea de tiempo reciente con IP**
    

```sql
select timestamp, ip_address
from login_attempts
where user_id = 123 and status = 'failed'
order by timestamp desc
limit 200;
```

3. **Agrupar por IP para ver focos**
    

```sql
select ip_address, count(*) as intentos
from login_attempts
where user_id = 123 and status = 'failed'
group by ip_address
order by intentos desc;
```

4. **Detectar ráfagas por hora**
    

```sql
select date_trunc('hour', timestamp) as hora, count(*) as intentos
from login_attempts
where user_id = 123 and status = 'failed'
  and timestamp >= now() - interval '24 hours'
group by hora
order by hora;
```

5. **IPs nuevas no vistas antes**
    

```sql
select la.ip_address, count(*) as intentos
from login_attempts la
left join known_user_ips kui
  on kui.user_id = la.user_id and kui.ip_address = la.ip_address
where la.user_id = 123 and la.status = 'failed' and kui.ip_address is null
group by la.ip_address
order by intentos desc;
```

con esto identifico volumen cuándo ocurrió desde dónde y si hay ips desconocidas para decidir bloqueo o multifactor

**Coach**  
¡Excelente! Has proporcionado un conjunto de consultas SQL muy detalladas y bien pensadas para investigar los intentos de inicio de sesión fallidos.

---

### Escenario 2: Parche crítico no instalado

**Coach**  
Imagina que en SecureCorp, un analista necesita identificar sistemas que no tienen un parche de seguridad crítico instalado. ¿Cómo podría usar SQL para encontrar esta información?

**Jeremy**  
podría usar una consulta sql que compare la tabla de sistemas con la tabla de parches críticos y la tabla de parches instalados para encontrar los sistemas sin ese parche por ejemplo

```sql
select s.hostname, p.cve
from systems s
join patches p on p.severity = 'critical' and p.os_name = s.os_name
left join system_patches sp on sp.system_id = s.id and sp.patch_id = p.id
where sp.patch_id is null;
```

esto devuelve los sistemas que no tienen instalado el parche crítico

**Coach**  
¡Impresionante! Has desglosado este escenario de parches de seguridad de una manera muy completa.

---

### Escenario 3: Fuga de datos

**Coach**  
Un analista de SecureCorp está investigando una posible fuga de datos. Necesita analizar la actividad de la base de datos para identificar accesos inusuales o extracciones de datos. ¿Cómo podría usar SQL?

**Jeremy**  
podría consultar directamente la tabla de auditoría para ver accesos fuera de lo normal por ejemplo

```sql
-- accesos fuera de horario laboral
select user_id, timestamp, action, table_name
from db_audit_logs
where extract(hour from timestamp) not between 8 and 18;

-- volumen de datos leídos por usuario
select user_id, count(*) as consultas
from db_audit_logs
where action = 'select'
group by user_id
order by consultas desc;

-- tablas sensibles accedidas
select user_id, timestamp, table_name, action
from db_audit_logs
where table_name in ('customers','payments','employees')
order by timestamp desc;
```

con estas consultas el analista detecta accesos fuera de horario cargas anormales de consultas y si alguien consultó tablas sensibles

**Coach**  
¡Excelente! Has identificado muy bien cómo SQL puede ser crucial para investigar una posible fuga de datos.

---

### Usos más amplios de SQL en ciberseguridad

**Coach**  
Más allá de los escenarios específicos, ¿se te ocurre alguna otra forma en que los profesionales de la seguridad podrían usar SQL en su trabajo diario?

**Jeremy**  
sí claro los profesionales de seguridad también pueden usar sql para tareas más amplias como

- generar informes periódicos de incidentes o actividad de usuarios para la dirección
    
- verificar cumplimiento comparando configuraciones contra estándares por ejemplo sistemas sin multifactor o contraseñas caducadas
    
- analizar inteligencia de amenazas correlando direcciones ip de logs con listas negras externas
    
- medir métricas de seguridad como tiempos de respuesta a incidentes o porcentaje de parches aplicados
    
- dar soporte a auditorías mostrando consultas que validen roles accesos y segregación de funciones
    

en el día a día sql se convierte en una herramienta flexible para extraer evidencia clara y generar reportes de seguridad

**Coach**  
¡Absolutamente! Has capturado perfectamente la amplitud de las aplicaciones de SQL en el ámbito de la seguridad.

---

✅ **Conclusión**  
Jeremy ha demostrado cómo SQL puede aplicarse a:

- el almacenamiento y análisis de datos de seguridad,
    
- tareas forenses y de cumplimiento,
    
- escenarios prácticos de incidentes,
    
- y usos más amplios como reportes, auditorías e inteligencia de amenazas.
    

SQL es sin duda una herramienta indispensable en la caja de herramientas de cualquier profesional de la ciberseguridad.
