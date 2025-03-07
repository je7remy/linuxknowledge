
---

## **1. Caso Práctico: Espionaje Industrial**

En esta sección, se presenta un escenario práctico diseñado para aplicar los conocimientos de informática forense en un caso realista de espionaje industrial. A continuación, desarrollo los detalles paso a paso:

### **Escenario**
El caso práctico gira en torno a un individuo sospechoso de actividades ilícitas relacionadas con el espionaje corporativo:
- **Sospechoso**: Alias "William Super Mlin". Este nombre parece ser un seudónimo utilizado para identificar al perpetrador en el ejercicio.
- **Ubicación**: Metro Manila, Filipinas. Este dato establece el contexto geográfico del caso, lo que podría implicar consideraciones logísticas o legales específicas en una situación real.
- **Contexto**: El sospechoso está involucrado en espionaje corporativo y robo de secretos comerciales de una empresa. Esto sugiere que ha accedido de manera no autorizada a información confidencial (como planos, fórmulas o estrategias) con el fin de beneficiar a un competidor o a sí mismo.

### **Misión**
El objetivo principal del caso práctico es simular una intervención forense en tiempo real. Los pasos específicos son:
- **Interrumpir la operación del sospechoso**: Esto implica detener las actividades ilícitas en curso, lo que podría incluir la transferencia de datos robados o la comunicación con terceros.
- **Asegurar evidencia digital encontrada en**:
  - **Una laptop encendida**: Un dispositivo activo presenta desafíos únicos, ya que contiene datos volátiles (como procesos en ejecución o memoria RAM) que podrían perderse si se apaga incorrectamente.
  - **Un teléfono con una conversación activa**: Esto indica que el sospechoso estaba comunicándose en el momento de la intervención, lo que podría proporcionar pistas sobre cómplices o el destino de la información robada.
  - **Una memoria USB conectada**: Este dispositivo podría contener copias de los secretos comerciales o herramientas utilizadas para el espionaje.

### **Enfoque**
El enfoque para resolver este caso se basa en los principios fundamentales de la informática forense:
- **Adquirir la evidencia sin alterarla**: Es esencial preservar la integridad de los datos para que puedan ser utilizados como prueba en un contexto legal o corporativo.
- **Seguir pasos críticos de informática forense**: Esto incluye:
  1. Asegurar la escena para evitar la contaminación de la evidencia.
  2. Documentar la cadena de custodia, registrando quién manipuló la evidencia y cuándo.
  3. Utilizar técnicas específicas para capturar datos de dispositivos encendidos (adquisición dinámica) y dispositivos de almacenamiento (adquisición estática).

Este caso práctico permite a los participantes aplicar habilidades prácticas en un escenario controlado que simula los retos de una investigación real.

---

## **2. Contenido Técnico**

Esta sección detalla los conceptos fundamentales de informática forense explicados en la clase. Desarrollo cada uno paso a paso:

### **Adquisición de Evidencia**
La adquisición de evidencia es el proceso de recolectar datos digitales de manera que se preserve su estado original. Se divide en dos categorías:
- **Estática**:
  - Se aplica a equipos apagados, como discos duros, pendrives, CDs u otros dispositivos de almacenamiento.
  - El proceso consiste en crear una copia exacta (imagen forense) del dispositivo sin riesgo de modificar los datos, ya que no hay actividad en curso.
- **Dinámica**:
  - Se realiza en equipos encendidos, como la laptop del caso práctico.
  - El objetivo es capturar datos volátiles, como la memoria RAM, conexiones de red activas, procesos en ejecución o registros del sistema, antes de que se pierdan al apagar el dispositivo.

### **Integridad de la Evidencia**
- **Principio clave**: Nunca se debe trabajar directamente con la evidencia original. Esto evita alteraciones accidentales que podrían invalidarla como prueba.
- **Solución**: Crear imágenes forenses, que son copias bit a bit del dispositivo original. Estas imágenes se utilizan para el análisis, mientras que la evidencia original se guarda intacta bajo estrictos controles de custodia.

### **Técnicas Anti-Forenses**
Los atacantes pueden usar técnicas para dificultar o impedir el análisis forense. Estas incluyen:
- **Borrado Seguro**: Herramientas como CCleaner eliminan datos de manera permanente, sobrescribiendo el espacio en disco para evitar su recuperación.
- **Esteganografía**: Ocultamiento de información dentro de otros archivos (por ejemplo, mensajes escondidos en imágenes), lo que requiere herramientas especializadas para detectarla.
- **Sobreescritura de Metadatos**: Alteración de datos como fechas de creación, modificación o autoría de archivos para despistar a los investigadores.
- **Cifrado**: Uso de herramientas como BitLocker para encriptar datos, haciéndolos inaccesibles sin la clave correcta.

### **Dimensionamiento del Esfuerzo**
Antes de iniciar una investigación, es necesario planificar el esfuerzo requerido:
- **Tiempo**: Depende del volumen de datos (e.g., tamaño del disco) y la complejidad del caso.
- **Herramientas**: Seleccionar herramientas adecuadas, ya sean de código abierto (como Autopsy) o comerciales.
- **Hardware**: Considerar equipos como bloqueadores de escritura o estaciones de trabajo forenses.
- **Costos**: Incluir gastos asociados, como desplazamientos, reuniones o licencias de software.

Estos conceptos forman la base teórica para realizar investigaciones forenses efectivas y enfrentar los desafíos técnicos del campo.

---

## **3. Uso de Herramientas**

En esta sección, describo las herramientas mencionadas en el contexto forense, desarrollando su propósito y uso paso a paso:

- **CCleaner**:
  - **Descripción**: Software diseñado para limpiar sistemas eliminando archivos temporales, historiales y otros datos.
  - **Uso por atacantes**: Puede emplearse para borrar evidencia de manera segura, sobrescribiendo datos para dificultar su recuperación.
  - **Relevancia forense**: Los investigadores deben conocer esta herramienta para identificar rastros de su uso (e.g., logs del sistema) y evaluar qué datos pudieron haber sido eliminados.

- **Autopsy**:
  - **Descripción**: Herramienta de código abierto para el análisis forense de discos y dispositivos de almacenamiento.
  - **Funcionalidades**: Permite examinar imágenes de disco, recuperar archivos borrados, analizar metadatos y generar informes.
  - **Uso**: Ideal para procesar la memoria USB o el disco duro de la laptop en el caso práctico.

- **TryHackMe**:
  - **Descripción**: Plataforma en línea que ofrece laboratorios virtuales y retos prácticos de ciberseguridad.
  - **Uso en la clase**: Proporciona el entorno para resolver el caso de espionaje industrial, simulando sistemas reales.
  - **Beneficio**: Permite practicar habilidades forenses en un entorno seguro y controlado.

- **OpenVPN**:
  - **Descripción**: Software para establecer conexiones seguras mediante una VPN (Red Privada Virtual).
  - **Uso**: Conecta el equipo local a los laboratorios de TryHackMe, garantizando acceso seguro a los recursos virtuales.
  - **Pasos**: Configurar el archivo de conexión proporcionado por TryHackMe e iniciarlo desde el sistema operativo.

- **xfreerdp**:
  - **Descripción**: Herramienta de línea de comandos para conexiones de escritorio remoto, comúnmente usada en Kali Linux.
  - **Uso**: Permite acceder a máquinas virtuales en TryHackMe para realizar análisis forenses.
  - **Ejemplo de comando**: `xfreerdp /u:usuario /p:contraseña /v:servidor` (los parámetros específicos dependen del laboratorio).

Estas herramientas son esenciales para llevar a cabo tanto la adquisición como el análisis de evidencia digital en el contexto del caso práctico y más allá.

---

## **4. Metodología Forense**

Aquí detallo el procedimiento estándar para realizar un análisis forense, basado en los pasos críticos y prácticas mencionadas:

### **Pasos Críticos**
1. **Asegurar la Escena**:
   - Proteger el área donde se encuentra la evidencia (e.g., la laptop, el teléfono y la memoria USB) para evitar alteraciones o acceso no autorizado.
   - Documentar la cadena de custodia, registrando cada persona que manipula la evidencia, junto con fechas y horas exactas.

2. **Bloqueadores de Escritura**:
   - Utilizar dispositivos de hardware (como bloqueadores USB) o software para impedir que se escriban datos en los dispositivos de almacenamiento durante la adquisición.
   - Esto es especialmente importante para la memoria USB y el disco duro de la laptop en el caso práctico.

3. **Documentación**:
   - Registrar todos los pasos realizados, herramientas usadas y hallazgos obtenidos.
   - El informe pericial debe ser detallado pero claro, incluyendo conclusiones y recomendaciones comprensibles para audiencias no técnicas (e.g., abogados o gerentes).

### **Análisis de Logs**
- **Importancia**: Los logs son registros de eventos que pueden revelar acciones del sospechoso, como accesos no autorizados o transferencias de datos.
- **Respaldo**: Utilizar herramientas como SIEM (Security Information and Event Management) para centralizar y proteger los logs, evitando su pérdida o manipulación.
- **Aplicación en el caso**: Analizar logs del teléfono (e.g., registros de llamadas) y de la laptop (e.g., conexiones de red) para reconstruir la operación de "William Super Mlin".

Esta metodología asegura que la investigación sea sistemática, reproducible y válida en contextos legales o corporativos.

---

