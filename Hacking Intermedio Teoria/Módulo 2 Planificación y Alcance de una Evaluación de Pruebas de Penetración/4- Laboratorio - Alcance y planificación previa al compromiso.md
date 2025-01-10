Antes de ofrecer un contrato a un cliente potencial, debemos aclarar cuáles son las condiciones y requisitos para el posible compromiso de pruebas de penetración. El cliente nos proporciona detalles sobre lo que quiere, lo cual es un buen punto de partida. A continuación, nos reunimos con el cliente para aclarar las necesidades y, en algunos casos, proponerle aspectos adicionales del compromiso en los que el cliente no había pensado.

Necesitamos saber qué sistemas y personal deben ser atacados y cuáles están fuera de los límites. También necesitamos conocer los problemas de cumplimiento que se van a evaluar y qué información se nos proporcionará sobre la red del cliente, las instalaciones y las aplicaciones.

Para ayudarle a comprender este proceso, completará un ejercicio en el que determinará y documentará algunas de las condiciones y requisitos que eventualmente se incluirán en un acuerdo de pruebas de penetración. Esto te ayudará a tener una idea del proceso involucrado. Quién sabe, ¡puede que algún día estés en el equipo que redacte estos acuerdos!

Obtener un acuerdo sobre las reglas de compromiso que se aplican a una prueba de penetración o auditoría de seguridad es el primer paso en cualquier compromiso con un cliente. Es importante dedicar tiempo a asegurarse de que tanto su empresa como el cliente tengan una comprensión clara de los términos y el alcance del compromiso de prueba.

- Cree un documento de plan y alcance de pruebas de penetración que aborde los requisitos para los servicios de pruebas de penetración que se recopilaron del cliente.
- Determine los elementos de las reglas de enfrentamiento.

### **Laboratorio - Alcance y planificación previa al compromiso**

Antes de ofrecer un contrato a un cliente potencial, debemos aclarar cuáles son las condiciones y requisitos para el posible compromiso de pruebas de penetración. El cliente nos proporciona detalles sobre lo que quiere, lo cual es un buen punto de partida. A continuación, nos reunimos con el cliente para aclarar las necesidades y, en algunos casos, proponerle aspectos adicionales del compromiso en los que el cliente no había pensado.

Necesitamos saber qué sistemas y personal deben ser atacados y cuáles están fuera de los límites. También necesitamos conocer los problemas de cumplimiento que se van a evaluar y qué información se nos proporcionará sobre la red del cliente, las instalaciones y las aplicaciones.

Para ayudarle a comprender este proceso, completará un ejercicio en el que determinará y documentará algunas de las condiciones y requisitos que eventualmente se incluirán en un acuerdo de pruebas de penetración. Esto te ayudará a tener una idea del proceso involucrado. Quién sabe, ¡puede que algún día estés en el equipo que redacte estos acuerdos!

Obtener un acuerdo sobre las reglas de compromiso que se aplican a una prueba de penetración o auditoría de seguridad es el primer paso en cualquier compromiso con un cliente. Es importante dedicar tiempo a asegurarse de que tanto su empresa como el cliente tengan una comprensión clara de los términos y el alcance del compromiso de prueba.

- Cree un documento de plan y alcance de pruebas de penetración que aborde los requisitos para los servicios de pruebas de penetración que se recopilaron del cliente.
- Determine los elementos de las reglas de enfrentamiento.

### **Laboratorio - Alcance y planificación previos a la participación**

### **Topología**

![[4.1- Topología.png]]

### **Tabla de direccionamiento – Centro de datos**

![[4.2- Tabla de direccionamiento – Centro de datos.png]]

### **Tabla de direccionamiento – LAN**

![[4.3- Tabla de direccionamiento – LAN.png]]

# Objetivos

Obtener un acuerdo sobre las reglas de compromiso que se aplican a una prueba de penetración o auditoría de seguridad es el primer paso en cualquier compromiso con un cliente. Es importante dedicar tiempo a asegurarse de que tanto su empresa como el cliente tengan una comprensión clara de los términos y el alcance del compromiso de prueba.

- Cree un documento de plan y alcance de pruebas de penetración que aborde los requisitos para los servicios de pruebas de penetración que se recopilaron del cliente.
- Determine los elementos de las reglas de enfrentamiento.

# Antecedentes / Escenario

Se contactó con su empresa para realizar una auditoría de seguridad para Nexus Plaza, una empresa minorista en línea. Se le ha asignado la tarea de ayudar al auditor principal a desarrollar el alcance del encargo de pruebas. Utilice el diagrama de red y la transcripción de la entrevista con el CEO de la empresa y el director de TI para completar la hoja de trabajo de alcance.

**Entrevista con el CEO y el Director de TI**

**CEO:** Bienvenidos a Nexus Plaza. Le hemos invitado aquí para dar inicio a nuestro compromiso y hablar sobre lo que esperamos de esta auditoría de seguridad. Estamos ansiosos por asegurarnos de que nuestra infraestructura de seguridad cumpla o supere las salvaguardas necesarias. Le pasaré esto a nuestro director de TI para que describa nuestro entorno de red.

**Director de TI**: Como saben, somos principalmente una empresa minorista en línea. Nuestros sitios de comercio electrónico orientados al cliente están alojados en Amazon, pero todos nuestros servicios de TI de comunicaciones, almacenamiento y envío se gestionan internamente. Operamos un centro de datos local en Houston que respalda nuestras instalaciones de fabricación y almacenamiento. Actualmente hay 25 servidores segregados en tres grupos: administración, operaciones y logística. Además, operamos un clúster que brinda soporte para nuestra tienda de Amazon. El acceso remoto a estos sistemas se realiza a través de SSL o IPsec VPN. Usamos dos ISP para conectarnos a Internet, pero uno se usa principalmente para las comunicaciones con Amazon para respaldar pedidos en tiempo real, inventario y contacto con el cliente.

**CEO:** Uno de nuestros competidores sufrió recientemente un ataque de ransomware dirigido a su sistema de inventario de producción. Perdieron un número significativo de pedidos de clientes debido a que no pudieron recoger y enviar el inventario de manera oportuna. Nos preocupa que nuestros sistemas de almacenamiento y envío puedan tener vulnerabilidades que podrían cerrarnos de manera similar si se produce una infracción. Cuando se depende de una entrega rápida a los clientes, cualquier retraso es un desastre.

**Director de TI**: Los sistemas que soportan nuestro almacenamiento y envío se encuentran en dos grupos en el centro de datos: operaciones y logística. El acceso interno a estos sistemas está restringido al personal de administración del almacén, al personal de TI y a los empleados de control de inventario. Nuestro sistema de control de inventario está respaldado por una base de datos de Microsoft SQL Server. Como puede ver en el diagrama, la base de datos SQL está alojada en una SAN separada con conexiones tanto al almacén como a los sistemas de producción. Nuestro negocio depende de nuestro acceso a Amazon; por lo tanto, ninguna prueba debe invadir los clústeres del centro de datos que contienen los datos y el inventario de la tienda de Amazon. Estos se identifican en el diagrama.

**CEO:** Queremos que pruebe los controles de seguridad para asegurarse de que un atacante que obtenga con éxito acceso a una cuenta de usuario final y a un equipo dentro del almacén no pueda obtener acceso de administrador a ninguno de los servidores ni tener acceso a la base de datos de inventario de producción. También queremos asegurarnos de que el software y los sistemas operativos estén actualizados y que no haya vulnerabilidades conocidas presentes en nuestras aplicaciones.

**Director de TI**: Le daremos acceso interno a través de una VLAN aislada dentro del departamento de TI desde la cual realizar sus pruebas. Hay un firewall con IDS integrado que separa las redes del centro de datos de la LAN corporativa, incluido el departamento de TI. Dentro del centro de datos, cada servidor tiene habilitado un firewall local. El DNS interno se proporciona a través de los servicios de Microsoft Active Directory, y el DNS externo es un servidor Linux ubicado en una DMZ independiente. El acceso externo a los clústeres de operaciones y logística está limitado a los empleados que se conectan a través de VPN. No se permite el acceso HTTP a estos clústeres. Los servidores de estos dos clústeres no tienen acceso a Internet, excepto para obtener actualizaciones automáticas de software.

**CEO:** Debido a que los sistemas que queremos que prueben son sistemas de producción, esperamos limitar al mínimo las interrupciones causadas por las pruebas. Le daremos acceso a un sistema de desarrollo Microsoft SQL Server que está configurado de forma idéntica al sistema de producción con un espejo de la base de datos.

**Director de TI**: Sí, quiero reforzar la necesidad de mantener las interrupciones al mínimo. Le daremos un intervalo de tiempo durante nuestra ventana de mantenimiento programado normal para realizar pruebas de carga y simulaciones de ataques de denegación de servicio. Nuestra ventana de mantenimiento programado es entre las 2:00 a.m. y las 6:00 a.m. los viernes, sábados y domingos. Otras pruebas no disruptivas se pueden ejecutar durante el horario comercial normal.

**CEO:** Estamos limitando el número de personal de TI que está al tanto de las pruebas. Solo el personal de TI directamente responsable de monitorear las operaciones y los sistemas logísticos será notificado de cuándo se realizarán las pruebas. Proporcionaremos una lista de direcciones de correo electrónico del personal de almacén y operaciones, ya que nos preocupa que la mayoría de los ransomware y las violaciones de datos comiencen con un ataque de ingeniería social exitoso. Los usuarios finales no serán informados de que se están realizando pruebas. Esperamos que el compromiso comience dos semanas después de la firma del contrato y el acuerdo de confidencialidad. Esperamos el informe final dentro de 60 días.

Sus contactos principales para este compromiso son el director de TI, el gerente de almacén y el gerente de operaciones. Programe un informe de actualización semanal y una teleconferencia para informarles sobre el progreso de las pruebas y los hallazgos provisionales.

# Instrucciones

## Parte 1: Determinar el alcance del compromiso

### Paso 1: Analizar la información obtenida del cliente.

1. Revisar la información obtenida en la entrevista con el cliente CEO y el Director de TI.
2. Identificar los puntos que influyen en el alcance del proyecto y las reglas de enfrentamiento.

### Paso 2: Complete la hoja de cálculo de alcance.

Utilice la información que identificó en la transcripción de la entrevista para completar la hoja de trabajo de alcance.

## **Hoja de trabajo de alcance**

Para determinar el alcance y las reglas de participación para el proyecto de pruebas de penetración, responda las preguntas en función de los resultados del análisis de su entrevista.

###### 1. **¿Cuáles son las mayores preocupaciones de seguridad del cliente? (Los ejemplos incluyen la divulgación de información confidencial, la interrupción del procesamiento de producción, la vergüenza debido a la desfiguración del sitio web, etc.)**

**Principales preocupaciones de seguridad**:

- **Prevención de ataques de ransomware**: El CEO está preocupado por los ataques de ransomware, en particular aquellos dirigidos a los sistemas de inventario y producción, como el caso que sufrió su competidor.
- **Disponibilidad de datos y servicios**: El objetivo es asegurar que los sistemas, especialmente los de almacén e inventario, sean seguros y resistentes a cualquier interrupción.
- **Limitación del acceso administrativo**: Se debe garantizar que los atacantes no puedan escalar privilegios para obtener acceso administrativo después de comprometer una cuenta de usuario.
- **Actualización de software y sistemas**: Las pruebas deben confirmar que no existen vulnerabilidades debido a sistemas desactualizados.

**Alcance de las pruebas**:

- **Pruebas de penetración interna**: Se debe centrar en los sistemas internos, específicamente en los sistemas de almacén, inventario y logística (servidores de operaciones, logística y administración).
- **Seguridad de bases de datos**: Se debe probar la seguridad del servidor SQL que aloja la base de datos de inventario.
- **Ingeniería social**: Se podrían incluir ataques por correo electrónico para evaluar la susceptibilidad de los usuarios a técnicas de phishing y ransomware.

**Restricciones**:

- **No se deben realizar pruebas en los clústeres de Amazon**: Es fundamental no interrumpir los sistemas alojados en Amazon, ya que manejan operaciones orientadas al cliente.
- **Mínima Disrupción**: Las pruebas deben evitar causar interrupciones en los sistemas de producción. Las pruebas más intensivas, como las de carga, deben realizarse durante las ventanas de mantenimiento.
- **Acceso proporcionado a través de una VLAN**: El acceso a los sistemas internos se proporcionará a través de una VLAN aislada en el departamento de TI.

###### 2. **¿Qué clústeres de servidores, rangos de direcciones de red o aplicaciones específicos se deben probar?**

- **Clústeres de servidores a probar**:
    
    - **Clúster de Operaciones**: Este clúster soporta los sistemas de almacenamiento y envío, que son críticos para el negocio. Necesita ser probado por posibles vulnerabilidades que puedan afectar la cadena de suministro.
    - **Clúster de Logística**: Este clúster está directamente relacionado con el manejo y envío de inventario. También debe ser examinado, ya que una interrupción o acceso no autorizado podría afectar la capacidad de procesar pedidos.
    - **Clúster de Administración**: Aunque tiene un enfoque más general, este clúster también está dentro del alcance, dado que cualquier escalada de privilegios aquí podría comprometer la seguridad general del sistema.
    - **Base de datos SQL**: Asegurar que la base de datos de inventario SQL, que es crítica para las operaciones de control de inventario, no sea accesible para atacantes sin las debidas credenciales.
- **Rangos de direcciones de red a probar**:
    
    - **Red del clúster de Operaciones**: VLAN 50–55, con la dirección IP **172.26.0.0/21**.
    - **Red del clúster de Logística**: VLAN 80–85, con la dirección IP **172.27.0.0/21**.
    - **Red del clúster de Administración**: VLAN 2–5 y VLAN 100–110, con la dirección IP **172.24.1.0/24** y **172.30.0.0/16**, respectivamente.
    - **Soporte de Amazon (para interacciones)**: VLAN 10–25, con la dirección IP **172.25.0.0/16** (aunque no se realizarán pruebas directas en los sistemas de Amazon, podrían revisarse las interacciones).
- **Aplicaciones específicas a probar**:
    
    - **Sistema de control de inventario**: Especialmente la base de datos SQL que soporta este sistema.
    - **Sistemas de almacenamiento y logística**: Aplicaciones críticas para el manejo de inventario, control y distribución.
    - **Firewalls locales y firewalls en los servidores del centro de datos**: Verificar la configuración y la seguridad de los firewalls para asegurar que estén correctamente configurados y no permitan accesos no autorizados.
    - **VPN y SSL/IPsec**: Evaluar la seguridad del acceso remoto a través de VPN y SSL/IPsec, ya que estos son los métodos de acceso externo a los sistemas internos.

###### 3. **¿Qué clústeres de servidores, rangos de direcciones de red o aplicaciones específicos NO deben probarse explícitamente?**

- **Clústeres de servidores que no deben probarse**:
    
    - **Clúster de Soporte de Amazon**: Los servidores que soportan las interacciones con Amazon (VLAN 10–25) no deben estar dentro del alcance de las pruebas. El CEO y el Director de TI dejaron claro que estos sistemas son críticos para el manejo de pedidos en tiempo real, inventario y contacto con el cliente, por lo que cualquier interferencia podría interrumpir operaciones importantes.
    - **Cualquier otro servidor o sistema relacionado con la tienda de Amazon**: Los datos e inventarios relacionados con Amazon no deben ser perturbados bajo ninguna circunstancia.
- **Rangos de direcciones de red que no deben probarse**:
    
    - **Rango de IP del clúster de Soporte de Amazon**: **172.25.0.0/16**. Este rango de direcciones es exclusivo para las interacciones con Amazon, y no se deben realizar pruebas ni auditorías en esta red.
    - **DMZ independiente**: Aunque se menciona una DMZ para servicios como DNS externo, las pruebas no deben interferir con servicios que puedan afectar la conectividad externa o la estabilidad de la empresa en Internet.
    - **Redes utilizadas para comunicaciones con Amazon**: Todo tráfico y redes conectadas directamente a Amazon para operaciones de pedidos e inventarios deben excluirse del alcance, para evitar cualquier impacto en las actividades de la tienda.
- **Aplicaciones que no deben probarse**:
    
    - **Aplicaciones que soportan directamente las interacciones con Amazon**: Ninguna aplicación que maneje pedidos, inventarios o interacciones de los clientes con la tienda de Amazon debe ser objeto de pruebas de penetración o auditoría.
    - **Acceso HTTP y redes VPN relacionadas con los clústeres de Amazon**: Las VPN o cualquier otro medio de acceso remoto que esté relacionado con Amazon deben quedar fuera del alcance para evitar disrupciones operativas.

###### **4. ¿La prueba se realizará en un entorno de producción en vivo o en un entorno de prueba?**

- **Entorno de producción en vivo**:
    
    - Algunas pruebas **se realizarán directamente en los sistemas de producción**, pero con ciertas limitaciones para evitar interrupciones.
    - El **sistema de producción crítico** que se probará es el de **almacenamiento y logística**, aunque con restricciones para no interrumpir las operaciones.
    - Las pruebas disruptivas, como ataques de denegación de servicio (DoS), se limitarán a la **ventana de mantenimiento programada**, que es entre las **2:00 a.m. y las 6:00 a.m. los viernes, sábados y domingos**.
    - Durante las pruebas en el entorno de producción, se debe priorizar la **continuidad operativa** y minimizar al máximo cualquier tipo de interrupción.
    
- **Entorno de prueba**:
    
    - Para evitar impactos en la producción, se ha proporcionado un **entorno de prueba** que incluye una **base de datos Microsoft SQL Server de desarrollo** que está configurada idénticamente al sistema de producción y contiene un **espejo de la base de datos de inventario**.
    - Este entorno de prueba permitirá realizar evaluaciones más exhaustivas y disruptivas sin poner en riesgo las operaciones comerciales en vivo.

###### 5. **¿La prueba de penetración incluirá pruebas de red interna? En caso afirmativo, ¿Cómo se obtendrá el acceso?**

**Sí**, la prueba de penetración **incluirá pruebas de la red interna**. La empresa ha proporcionado detalles específicos sobre cómo se llevará a cabo este acceso para garantizar que las pruebas se realicen de manera segura y controlada.

### Acceso a la red interna:

1. **Acceso mediante una VLAN aislada**:
    
    - El acceso interno a la red de Nexus Plaza se proporcionará a través de una **VLAN aislada dentro del departamento de TI**. Esta VLAN estará separada del tráfico regular y permitirá realizar pruebas sin comprometer otras áreas operativas de la red.
    - El equipo de auditoría podrá realizar pruebas desde esta VLAN que tiene conectividad controlada a los sistemas que deben evaluarse, como los clústeres de **operaciones** y **logística**, así como a los sistemas de **almacenamiento**.
2. **Firewalls y segmentación de red**:
    
    - Existe un **firewall con IDS (Sistema de Detección de Intrusos) integrado** que separa las redes del **centro de datos** de la **LAN corporativa**. Este firewall ayuda a monitorear las actividades durante la auditoría y a identificar posibles amenazas o actividades anómalas.
    - Además, dentro del **centro de datos**, cada servidor tiene un **firewall local habilitado**, lo que agrega una capa adicional de seguridad y monitoreo durante las pruebas.
3. **Acceso VPN para empleados**:
    
    - Aunque el acceso externo a los clústeres de **operaciones** y **logística** está restringido a los empleados que se conectan a través de **VPN**, este acceso **no se incluye como parte de las pruebas de penetración**. Las pruebas se centrarán en el entorno interno a través de la VLAN proporcionada.
    - Sin embargo, el uso de VPNs en la empresa es un punto importante a evaluar en cuanto a seguridad, por lo que podría ser relevante realizar revisiones sobre su configuración y seguridad en la auditoría general.

### Alcance de las pruebas de red interna:

Las pruebas de red interna incluirán la evaluación de los controles de seguridad, configuraciones de firewall, accesos no autorizados y vulnerabilidades en los sistemas internos, asegurando que un atacante no pueda escalar privilegios o acceder a información crítica como la base de datos de inventario de producción.

###### **6. ¿Los sistemas cliente/usuario final están incluidos en el alcance? Si es así, ¿cómo se aprovecharán los clientes?**

**Sí**, los sistemas cliente/usuario final **están incluidos en el alcance** de la prueba de penetración, ya que una de las preocupaciones principales de Nexus Plaza es la posibilidad de que un atacante obtenga acceso a una cuenta de usuario final y comprometa los sistemas críticos.

### Forma de aprovechar los sistemas cliente:

1. **Simulación de ataques de usuario comprometido**:
    
    - El objetivo es simular un escenario en el que un atacante haya obtenido acceso a un sistema cliente o cuenta de usuario final, especialmente aquellos que pertenecen al **personal del almacén** o de **operaciones**, ya que estos empleados tienen acceso limitado a los sistemas de inventario y producción.
    - El acceso inicial podría ser logrado a través de técnicas de **ingeniería social** o mediante la explotación de vulnerabilidades en los sistemas cliente. La empresa proporcionará una lista de direcciones de correo electrónico del personal de almacén y operaciones para simular estos ataques.
2. **Escenario de prueba**:
    
    - El auditor intentará realizar movimientos laterales desde un sistema cliente comprometido hacia otros recursos más críticos de la red, como los servidores de **almacenamiento** o las bases de datos de **producción**. El objetivo es verificar si un atacante con privilegios de usuario final puede escalar privilegios o acceder a información crítica.
    - Las pruebas se centrarán en asegurar que los **controles de acceso** impidan que un atacante pueda obtener permisos de administrador o acceder a áreas sensibles desde una cuenta de usuario comprometida.
3. **Protecciones específicas a evaluar**:
    
    - **Segmentación de red**: Se evaluará si la segmentación de red impide que un atacante pueda moverse lateralmente desde los sistemas cliente hacia los servidores críticos.
    - **Parcheo y actualizaciones de software**: Se verificarán las configuraciones de los sistemas cliente, asegurando que estén actualizados y libres de vulnerabilidades conocidas que puedan ser explotadas.
    - **Políticas de seguridad**: Se revisarán las políticas de seguridad, tales como la configuración de firewalls locales, el uso de **antivirus** o sistemas de **detección de malware**, y la aplicación de políticas de acceso basadas en roles (RBAC) en los sistemas cliente.
    - **Ingeniería social**: El personal de almacén y operaciones podría ser el objetivo de pruebas de **phishing** o de otro tipo de ataques de ingeniería social, para evaluar si es posible comprometer las credenciales y aprovechar sus cuentas para acceder a recursos críticos.

### Objetivo:

El propósito de incluir los sistemas cliente en el alcance es garantizar que **incluso si un usuario final es comprometido**, los controles internos de seguridad eviten que el atacante escale sus privilegios o comprometa los sistemas críticos de la red.

###### **¿Está permitida la ingeniería social? Si es así, ¿es limitado?**

**Sí**, la **ingeniería social está permitida** como parte de la prueba de penetración, pero está **limitada** a ciertos aspectos y empleados clave, según lo indicado por el CEO y el Director de TI.

### Límites de la ingeniería social:

1. **Objetivo de la ingeniería social**:
    
    - La empresa está preocupada por la posibilidad de que un ataque de ransomware o una violación de datos **comience con un ataque exitoso de ingeniería social**. Por lo tanto, los sistemas de los empleados del **almacén** y **operaciones** son los principales objetivos de estas pruebas.
    - El CEO proporcionará una **lista de direcciones de correo electrónico del personal** de estos departamentos, lo que indica que estos empleados podrían ser el blanco de **ataques de phishing** u otros tipos de ingeniería social.
2. **Limitaciones y alcance**:
    
    - **Usuarios finales no serán informados**: Los empleados objetivo de las pruebas **no sabrán** que se están realizando simulaciones de ataques de ingeniería social, para garantizar que los resultados reflejen cómo podrían reaccionar en un escenario real.
    - **Restricción a ciertos departamentos**: Solo el personal de **almacén** y **operaciones** está en el alcance para los ataques de ingeniería social. Otros empleados, como los de administración o finanzas, **no serán incluidos** en estas pruebas, a menos que se indique lo contrario.
3. **Métodos permitidos**:
    
    - Se permitirá el uso de **correos electrónicos de phishing**, en los que el auditor intentará obtener credenciales o comprometer sistemas cliente.
    - También se podrían usar tácticas de **spear-phishing** más dirigidas, como correos electrónicos que simulen comunicaciones internas o avisos de IT, para evaluar cómo los empleados responden ante correos maliciosos o engañosos.
    - **No se permite**: La ingeniería social en forma de **interacciones físicas** (como visitas o llamadas telefónicas) **no ha sido mencionada**, por lo que debe asumirse que estas tácticas **no están permitidas** a menos que se solicite una autorización explícita.

### Propósito de la ingeniería social:

El objetivo es evaluar si los empleados pueden ser engañados para entregar sus credenciales o realizar acciones que comprometan la seguridad de los sistemas. Esto ayudará a identificar las debilidades en la capacitación en seguridad y las políticas de concientización, y permitirá a Nexus Plaza reforzar estos puntos.

###### **¿Están permitidos los ataques de denegación de servicio y otros ataques disruptivos? Si es así, ¿hay límites en cuanto a cuándo se pueden realizar las pruebas disruptivas?**

**Sí**, los **ataques de denegación de servicio (DoS)** y otros ataques disruptivos están permitidos en la prueba de penetración, pero con **límites claros** sobre cuándo pueden realizarse y bajo qué condiciones, para minimizar el impacto en los sistemas de producción.

### Límites y condiciones de los ataques disruptivos:

1. **Permitidos, pero solo en momentos específicos**:
    
    - Los ataques disruptivos, como los ataques de **denegación de servicio** o **simulaciones de carga**, se permiten solo durante las **ventanas de mantenimiento programado** de Nexus Plaza.
    - La ventana de mantenimiento definida es entre las **2:00 a.m. y las 6:00 a.m.**, los días **viernes, sábado y domingo**. Estas son las horas durante las cuales se pueden realizar pruebas que podrían interrumpir el servicio.
2. **Producción en vivo restringida**:
    
    - Debido a que las pruebas se realizarán en un entorno de **producción en vivo**, es fundamental limitar cualquier actividad que pudiera causar interrupciones durante las horas de operación normales. Por lo tanto, cualquier ataque que cause una interrupción visible en el servicio o la red no debe realizarse fuera de la ventana de mantenimiento.
    - En horario comercial normal, solo se permiten **pruebas no disruptivas**, como la exploración de vulnerabilidades o pruebas que no afecten directamente la operación continua de los servicios de producción.
3. **Pruebas DoS específicas**:
    
    - El auditor podrá simular ataques de **denegación de servicio (DoS)** o **denegación de servicio distribuida (DDoS)** durante las ventanas de mantenimiento para evaluar la capacidad de la empresa para manejar sobrecargas y ataques de saturación.
    - También se permitirá probar el **rendimiento del firewall** y el sistema de **detección de intrusiones (IDS)** durante estos momentos, para asegurarse de que puedan mitigar estos ataques sin causar una interrupción significativa en los sistemas críticos.
4. **Monitoreo en tiempo real**:
    
    - Durante los ataques disruptivos, el personal de TI de Nexus Plaza estará **informado** y **monitoreando** los sistemas para asegurarse de que las pruebas no causen daños permanentes ni una interrupción no planificada.

### Propósito de estas pruebas:

El objetivo de los ataques disruptivos es garantizar que los sistemas críticos puedan manejar **picos de tráfico**, **intentos de denegación de servicio**, y que el **firewall** y los mecanismos de **resistencia ante ataques** de Nexus Plaza sean lo suficientemente robustos como para minimizar los daños en caso de un ataque real.

###### **¿Existen dispositivos que puedan afectar los resultados de una prueba de penetración? Si es así, ¿Cuáles son?**

**Sí**, hay dispositivos y sistemas dentro de la infraestructura de Nexus Plaza que podrían afectar los resultados de la prueba de penetración. Estos dispositivos incluyen tanto sistemas de seguridad como restricciones de red que podrían influir en los resultados obtenidos durante la auditoría.

### Dispositivos y sistemas que podrían afectar los resultados:

1. **Firewall con IDS (Sistema de Detección de Intrusos) Integrado**:
    
    - El **firewall** que separa la **LAN corporativa** del **centro de datos** cuenta con un **IDS integrado**. Este sistema monitorea el tráfico en tiempo real y puede bloquear o mitigar ciertos tipos de ataques o comportamientos anómalos. Esto puede afectar los resultados de la prueba de penetración, ya que el **IDS puede detectar y bloquear** ciertas pruebas o intentos de intrusión.
    - El firewall local en cada servidor dentro del centro de datos también puede interferir con las pruebas al limitar o bloquear el acceso a puertos específicos.
2. **Sistemas de Seguridad en la DMZ**:
    
    - Los servidores de la **DMZ (Zona Desmilitarizada)**, que gestionan la conectividad externa, también tienen protecciones que podrían limitar el acceso o generar falsos positivos/negativos durante las pruebas. Estos sistemas están diseñados para limitar el acceso no autorizado y podrían afectar la simulación de ciertos ataques que intenten aprovechar vulnerabilidades en los servicios expuestos.
3. **VPNs SSL e IPsec**:
    
    - El acceso remoto a los sistemas de Nexus Plaza está protegido a través de **VPNs (SSL y IPsec)**. Estas conexiones seguras podrían dificultar la interceptación de tráfico y la simulación de ciertos ataques de red, como el "man-in-the-middle", lo que podría influir en los resultados.
    - Además, las VPNs limitan el acceso remoto solo a usuarios autorizados, lo que restringe la superficie de ataque a solo aquellos usuarios que están conectados.
4. **Segmentación de Redes con VLANs**:
    
    - El uso de **VLANs** para la segmentación de red (tanto en la **LAN corporativa** como en el **centro de datos**) puede restringir la capacidad de realizar ciertos movimientos laterales dentro de la red. Cada departamento tiene su propio rango de IP y **subred**, lo que puede limitar la visibilidad de ciertos sistemas desde otros segmentos de la red durante la prueba.
    - Esto es particularmente relevante en la prueba de penetración interna, donde la **segmentación** por VLAN puede ocultar ciertas partes de la infraestructura o limitar la explotación de vulnerabilidades a nivel de red.
5. **Servidores y sistemas con acceso limitado a Internet**:
    
    - Los **servidores en los clústeres de operaciones y logística** no tienen acceso a Internet, salvo para actualizaciones de software. Esto limita los posibles vectores de ataque desde afuera y podría hacer que algunas pruebas que dependen de la conectividad externa, como la exfiltración de datos a servidores externos, sean más difíciles de realizar o medir.
6. **Sistemas con actualizaciones automáticas**:
    
    - Los sistemas que dependen de actualizaciones automáticas para mantener los parches de seguridad pueden afectar los resultados si los ataques buscan explotar vulnerabilidades en software desactualizado. Si el software está constantemente actualizado, es probable que algunas vulnerabilidades comunes no estén presentes durante las pruebas.
7. **Servidores Microsoft SQL en SAN Separada**:
    
    - El **Microsoft SQL Server**, alojado en una **SAN separada** (Almacenamiento en Red), tiene conexiones directas con los sistemas de almacén y producción. El acceso a este servidor está limitado a empleados específicos, y su ubicación en una SAN puede hacer que los intentos de acceso no autorizado sean más complejos.

###### **7. ¿Probar el acceso inalámbrico es parte de este compromiso?**

No

###### 8. **¿Los servicios web están incluidos en el alcance de las pruebas?**

No

###### 9. **¿Están los empleados al tanto de las pruebas y del plazo en el que se realizarán?**

No

###### 10. **¿Dónde se encuentra físicamente el centro de datos del cliente?**

El centro de datos del cliente se encuentra físicamente en **Houston**, según lo mencionado por el **Director de TI** en la entrevista. Este centro de datos respalda las operaciones de las instalaciones de fabricación y almacenamiento de la empresa.

## Parte 2: Determinar las reglas de enfrentamiento

### Paso 1: Revise la información de la hoja de cálculo de ámbito.

Usar la transcripción de la entrevista y la información de la Hoja de Trabajo de Alcance para completar la tabla de Elementos de las Reglas de Compromiso.

Aquí te ayudo a completar la tabla de **Elementos de las Reglas de Compromiso** basándome en la información proporcionada por la entrevista y el escenario:

| **Elemento de las Reglas de Enfrentamiento**                          | **Valor**                                                                                                                                                                                                                                                                                              |
| --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Cronograma de pruebas**                                             | Las pruebas comenzarán dos semanas después de la firma del contrato y del acuerdo de confidencialidad. Se espera el informe final dentro de los 60 días.                                                                                                                                               |
| **Ubicación de las pruebas**                                          | El acceso será remoto desde una **VLAN aislada** dentro del departamento de TI.                                                                                                                                                                                                                        |
| **Ventanas de tiempo para las pruebas (horas del día)**               | Las pruebas disruptivas, como las pruebas de carga y denegación de servicio (DoS), solo se permitirán en la ventana de mantenimiento: entre las **2:00 a.m. y las 6:00 a.m.**, los **viernes, sábados y domingos**. Las pruebas no disruptivas se pueden ejecutar durante el horario comercial normal. |
| **Método preferido de comunicación**                                  | Actualizaciones semanales por medio de una teleconferencia y reporte de progreso. Se proporcionarán informes preliminares y finales.                                                                                                                                                                   |
| **Controles de seguridad que podrían detectar o impedir las pruebas** | Hay un **firewall con IDS integrado** entre la LAN corporativa y el centro de datos. Cada servidor en el centro de datos tiene habilitado un **firewall local**.                                                                                                                                       |
| **Manejo de datos sensibles**                                         | Las pruebas deben realizarse con mínima interrupción y sin comprometer el entorno de producción. Los datos sensibles deben ser manejados con confidencialidad y se utilizará un entorno de desarrollo espejo para pruebas en los sistemas SQL.                                                         |
| **Direcciones IP o redes desde las que se originarán las pruebas**    | Las pruebas se originarán desde una **VLAN aislada** dentro del departamento de TI.                                                                                                                                                                                                                    |
| **Tipos de pruebas permitidas o no permitidas**                       | No se permitirá ningún tipo de prueba sobre los **clústeres de Amazon** (sistemas relacionados con la tienda en línea). Se permiten pruebas en los sistemas de **almacenamiento** y **logística**, pero limitadas a **no comprometer** los sistemas de producción en horas laborales.                  |
| **Contactos de clientes**                                             | Los contactos principales son el **director de TI**, el **gerente de almacén** y el **gerente de operaciones**.                                                                                                                                                                                        |

![[4.4- Elementos de las Reglas de Compromiso.png]]