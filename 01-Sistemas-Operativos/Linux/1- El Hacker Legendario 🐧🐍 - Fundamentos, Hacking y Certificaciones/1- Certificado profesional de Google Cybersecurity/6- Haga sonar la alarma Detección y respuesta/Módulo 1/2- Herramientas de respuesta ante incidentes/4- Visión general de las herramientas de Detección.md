
Anteriormente, usted exploró las tecnologías **del Sistema de detección de intrusiones** **(IDS**) y del **Sistema de prevención de intrusiones** **(IPS)**. En esta lectura, comparará y contrastará estas herramientas y aprenderá sobre la **Detección y respuesta en el punto final** (**EDR**). Como analista de Seguridad, es probable que trabaje con estas diferentes herramientas, por lo que es importante que comprenda sus funciones.

## Por qué necesita herramientas de Detección

Las herramientas de Detección funcionan de forma similar a los sistemas de Seguridad del hogar. Mientras que los sistemas de seguridad domésticos vigilan y protegen los hogares contra las intrusiones, las herramientas de detección de la ciberseguridad ayudan a las organizaciones a proteger sus redes y sistemas contra los accesos no deseados y no autorizados. Para que las organizaciones protejan sus sistemas de las amenazas o ataques a la Seguridad, deben ser conscientes de cuándo hay algún indicio de intrusión. Las herramientas de Detección hacen que los profesionales de la Seguridad sean conscientes de la actividad que se está produciendo en una red o en un sistema. Las herramientas hacen esto monitorizando continuamente las redes y los sistemas en busca de cualquier actividad sospechosa. Una vez que se detecta algo inusual o sospechoso, la herramienta activa una alerta que notifica al profesional de la Seguridad para que investigue y detenga la posible intrusión.

## Herramientas de Detección

Como analista de Seguridad, es probable que en algún momento se encuentre con herramientas de Detección **IDS**, **IPS** y **EDR**, pero es importante que entienda las diferencias entre ellas. Aquí tiene un Gráfico comparativo para una referencia rápida:

|**Capacidad**|**IDS**|**IPS**|**EDR**|
|---|---|---|---|
|Detecta actividades maliciosas|✓|✓|✓|
|Previene intrusiones|N/A|✓|✓|
|Registra la actividad|✓|✓|✓|
|Genera alertas|✓|✓|✓|
|Realiza análisis de comportamiento|N/A|N/A|✓|

## Visión general de las herramientas IDS

Un **Sistema de detección de intrusiones** **(IDS**) es una aplicación que monitorea la actividad del sistema y alerta sobre posibles intrusiones. Un IDS proporciona un monitoreo continuo de los eventos de red para ayudar a proteger contra amenazas o ataques a la seguridad. El objetivo de un IDS es detectar posibles actividades maliciosas y generar una alerta una vez detectada dicha actividad. Un IDS _no_ detiene ni evita la actividad. En su lugar, los profesionales de la Seguridad investigarán la alerta y actuarán para detenerla, si es necesario.

Por ejemplo, un IDS puede enviar una alerta cuando identifica un registro de usuario sospechoso, como una dirección IP desconocida que inicia sesión en una aplicación o un dispositivo a una hora inusual. Pero, un IDS no detendrá ni impedirá ninguna acción posterior, como bloquear el inicio de sesión del usuario sospechoso.

Algunos ejemplos de herramientas IDS son Zeek, Suricata, Snort® y Sagan.

### **Categorías de Detección**

Como analista de Seguridad, investigará las alertas que genera un IDS. Hay cuatro tipos de categorías de Detección con las que debe estar familiarizado:

1. **Un Positivo** verdadero es una alerta que detecta correctamente la presencia de un ataque.
    
2. Un**negativo** verdadero es un estado en el que no se detecta actividad maliciosa. Es cuando no existe actividad maliciosa y no se activa ninguna alerta.
    
3. Un**Falso** positivo es una alerta que detecta incorrectamente la presencia de una amenaza. Es cuando un IDS identifica una actividad como maliciosa, pero no lo es. Los falsos positivos son un inconveniente para los Equipos de Seguridad porque gastan tiempo y recursos en investigar una alerta ilegítima.
    
4. **Un** falso negativo es un estado en el que no se detecta la presencia de una amenaza. Es cuando se produce una actividad maliciosa pero un IDS no logra detectarla. Los falsos negativos son peligrosos porque los Equipos de Seguridad se quedan sin saber de ataques legítimos a los que pueden ser vulnerables.
    

## Visión general de las herramientas IPS

Un **sistema de prevención de intrusiones** **(IPS**) es una aplicación que monitoriza la actividad del sistema en busca de actividad intrusiva y toma medidas para detenerla. Un IPS funciona de forma similar a un IDS. Pero, el IPS monitoriza la actividad del sistema para detectar y alertar sobre intrusiones, _y_ también toma medidas para _prevenir_ la actividad y minimizar sus efectos. Por ejemplo, un IPS puede enviar una alerta y modificar una Lista de control de acceso en un router para bloquear el tráfico específico en un servidor.

**Nota:** Muchas herramientas IDS también pueden funcionar como un IPS. Herramientas como Suricata, Snort y Sagan tienen capacidades tanto de IDS como de IPS.

## Visión general de las herramientas EDR

**Detección y respuesta en el punto final** **(EDR**) es una aplicación que monitorea un punto final en busca de actividad maliciosa. Las herramientas EDR se instalan en los puntos finales. Recuerde que un punto **final** es cualquier dispositivo conectado en una red. Algunos ejemplos son los dispositivos de usuario final, como computadoras, teléfonos, tabletas, etc.

Las herramientas EDR monitorizan, registran y analizan la actividad del sistema de los puntos finales para identificar, alertar y responder a las actividades sospechosas. A diferencia de las herramientas IDS o IPS, los EDR recopilan datos de la actividad de los puntos finales y realizan _análisis_ de comportamiento para identificar los patrones de amenazas que se producen en un punto final. El análisis de comportamiento utiliza el poder del Aprendizaje automático y la Inteligencia artificial para analizar el comportamiento del sistema e identificar actividades maliciosas o inusuales. Las herramientas EDR también utilizan la _Automatización_ para detener los ataques sin la intervención manual de los profesionales de la Seguridad. Por ejemplo, si un EDR detecta el inicio de un proceso inusual en la estación de trabajo de un usuario que normalmente no se utiliza, puede bloquear automáticamente la ejecución del proceso.

Herramientas como Open EDR®, Bitdefender™ Detección y respuesta en el punto de conexión y FortiEDR™ son ejemplos de herramientas EDR.

**Nota**: Las herramientas de administración de información y eventos de seguridad (SIEM) también tienen capacidades de detección, que explorará más adelante.

## Puntos clave

Las organizaciones implementan herramientas de Detección para tener conocimiento de la actividad que ocurre en sus entornos. IDS, IPS y EDR son diferentes tipos de herramientas de Detección. El valor de las herramientas de Detección reside en su capacidad para detectar, registrar, alertar y detener posibles actividades maliciosas.