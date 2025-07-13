
## Resumen de la Actividad

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/wBI365r0TCevN_1iKPj-9A_395ef074f51943288c6b8bdd1ce3eef1_image.png?expiry=1752537600000&hmac=4VYcbINBehuSMnsEX8xejKH1cKOARZlBwv9liGs2P_k)

En esta actividad, crearás un reporte de incidente utilizando el conocimiento que has adquirido sobre redes a lo largo de este curso para analizar un incidente de red. Analizarás la situación utilizando el Marco de Ciberseguridad del Instituto Nacional de Estándares y Tecnología (NIST CSF). El CSF es un marco voluntario que consta de normas, directrices y mejores prácticas para gestionar los riesgos de ciberseguridad. Crear un informe de incidentes de ciberseguridad de calidad y aplicar el CSF puede demostrar un enfoque proactivo de la seguridad, mejorar la comunicación y la transparencia con las partes interesadas y mejorar las prácticas de seguridad dentro de su organización. También puede añadir el informe de incidentes que cree a su cartera de ciberseguridad cuando lo complete.

El CSF es escalable y puede aplicarse en una amplia variedad de contextos. A medida que continúe aprendiendo más y perfeccionando su comprensión de las habilidades clave de ciberseguridad, puede utilizar las plantillas proporcionadas en esta actividad en otras situaciones. Saber identificar qué medidas de seguridad aplicar en respuesta a las necesidades de la empresa le ayudará a determinar cuáles son las mejores opciones disponibles cuando se trata de la seguridad de la red.

Asegúrese de completar esta actividad antes de continuar. En el siguiente punto del curso, podrá autoevaluar su respuesta. Después de eso, habrá un ejemplar completado para comparar con su propio trabajo. También tendrá la oportunidad de responder a las preguntas de la rúbrica que le permitirán reflexionar sobre los elementos clave de su declaración profesional.

## Escenario

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/dDWqzsRPQqeCk0vSaDKmOA_42906106724e4c1d9d53026c020a46f1_image.png?expiry=1752537600000&hmac=l3r1Ygu1PGslcD7wgLCbantVDu7gcQ3_ZQiXqIpFjgI)

Revise el siguiente escenario. A continuación, complete las instrucciones paso a paso.

Usted es un analista de ciberseguridad que trabaja para una empresa multimedia que ofrece servicios de diseño web, diseño gráfico y soluciones de Marketing en redes sociales a pequeñas empresas. Su organización ha sufrido recientemente un ataque DDoS, que ha puesto en peligro la red interna durante dos horas hasta que se ha resuelto.

Durante el ataque, los servicios de red de su organización dejaron de responder repentinamente debido a una avalancha de paquetes ICMP entrantes. El tráfico normal de la red interna no podía acceder a ningún recurso de la red. El equipo de gestión de incidentes respondió bloqueando los paquetes ICMP entrantes, deteniendo todos los servicios de red no críticos fuera de línea y restableciendo los servicios de red críticos.

A continuación, el equipo de ciberseguridad de la empresa investigó el incidente de seguridad. Descubrieron que un actor malicioso había enviado una avalancha de pings ICMP a la red de la empresa a través de un cortafuegos no configurado. Esta vulnerabilidad permitió al agresor abrumar la red de la empresa mediante un ataque de denegación de servicio distribuido (DDoS).

Para hacer frente a este problema de seguridad, el equipo de Seguridad de red implementó:

- Una nueva regla de cortafuegos para limitar la tasa de paquetes ICMP entrantes
    
- Verificación de la dirección IP de origen en el cortafuegos para comprobar si hay direcciones IP falsificadas en los paquetes ICMP entrantes
    
- Software de Monitoreo de red para detectar patrones de tráfico anormales
    
- Un sistema IDS/IPS para filtrar parte del tráfico ICMP basado en características sospechosas
    

Como analista de ciberseguridad, se le ha encomendado la tarea de utilizar este evento de seguridad para crear un plan que mejore la seguridad de la red de su empresa, siguiendo el Marco de Ciberseguridad (CSF) del Instituto Nacional de Estándares y Tecnología (NIST). Utilizarás el CSF para ayudarte a navegar a través de los diferentes pasos del análisis de este evento de ciberseguridad e integrar tu análisis en una estrategia de seguridad general. Hemos dividido el análisis en diferentes partes en la plantilla que figura a continuación. Puede explorarlas aquí:

- **Identificar** los riesgos de seguridad mediante auditorías periódicas de las redes internas, los sistemas, los dispositivos y los privilegios de acceso para identificar posibles brechas en la seguridad.
    
- **Proteger** los activos internos mediante la aplicación de políticas, procedimientos, formación y herramientas que ayuden a mitigar las amenazas a la ciberseguridad.
    
- **Detectar** posibles incidentes de seguridad y mejorar las capacidades de supervisión para aumentar la rapidez y eficacia de las detecciones.
    
- **Responder** para contener, neutralizar y analizar incidentes de seguridad; implantar mejoras en el proceso de seguridad.
    

**Recuperar** el funcionamiento normal de los sistemas afectados y restaurar los datos y/o activos de los sistemas que se hayan visto afectados por un incidente.

## Instrucciones paso a paso

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/5hMqfCEPRVutrXU-S4uWWA_bb13bb0ab1d34ad49f708482f695a3f1_image.png?expiry=1752537600000&hmac=pBiuBcyA2xrUVr_QH-SCXAndg4Za6jhzZsf2qb-MRUs)

Siga las instrucciones y rellene las secciones para completar la actividad. A continuación, vaya al siguiente elemento del curso para comparar su trabajo con un ejemplo completado.

### **Paso 1: Acceder a la plantilla de análisis de informes de incidentes**

Para acceder a la plantilla para este tema del curso, haga clic en el siguiente enlace y seleccione _Usar plantilla_.

Enlace a la plantilla:

- [Análisis de informes de incidentes](https://docs.google.com/document/d/1EnieOKYJyKGsVff5Gg-3-dVwrHrZ2m8Hig6tVpfKqyg/template/preview?usp=sharing&resourcekey=0-eb5t-d69zTPLEGthIpVlXw)
    

Enlace a los materiales de apoyo:

- [Aplicación del NIST CSF](https://docs.google.com/document/d/15yCDbDCOAcJw-LTz2DeCA7UeLRfvsf176T6MA6ku6ok/template/preview?usp=sharing)
    
- [Ejemplo de análisis de informe de incidente](https://docs.google.com/document/d/11eTIo1igTRFrY279DG9tHTO3tB3bugSGyknZxsvY5vI/template/preview?usp=sharing&resourcekey=0-97MA-eOwoGtqcfqky0vjmg)
    

Utilizando la plantilla proporcionada, proporcione un resumen del suceso de seguridad ocurrido. Incluye información sobre el suceso de seguridad, su causa, el impacto y la respuesta. También puedes incluir información sobre los sistemas atacados, el origen del ataque y el impacto estimado.

Piensa en todos los conceptos tratados en el curso hasta ahora y reflexiona sobre el escenario y define qué tipo de ataque se produjo y qué sistemas se vieron afectados. Enumera esta información en la hoja de trabajo de análisis de informes de incidentes en la sección titulada "Identificar"."

A continuación, evaluará dónde puede mejorar la organización para proteger aún más sus activos. En este paso, se centrará en crear un plan de acción inmediato para responder al incidente de ciberseguridad. Al crear este plan, reflexione sobre la siguiente pregunta:

- ¿Qué sistemas o procedimientos deben actualizarse o modificarse para proteger mejor los activos de la organización?
    

Escriba su respuesta en la plantilla de análisis de informes de incidentes en la sección "Proteger".

Es importante supervisar continuamente el tráfico de red en los dispositivos de red para comprobar si hay actividad sospechosa, como paquetes ICMP externos entrantes procedentes de direcciones IP no fiables que intentan atravesar el cortafuegos de red de la organización.

Para este paso, considere las formas en que usted y su equipo pueden supervisar y analizar el tráfico de red, las aplicaciones de software, realizar un seguimiento de los usuarios autorizados frente a los no autorizados y detectar cualquier actividad inusual en las cuentas de usuario. Escriba su respuesta en la hoja de trabajo de análisis de respuesta ante incidentes, en la sección "Detectar".

Después de identificar las herramientas y métodos que usted y su organización tienen en marcha para detectar posibles vulnerabilidades y amenazas, cree un plan de respuesta en caso de que se produzca un incidente en el futuro. Esto suele ocurrir después de que se haya producido el incidente y haya sido resuelto por usted y su equipo. En este caso, creará un plan de respuesta para futuros incidentes de ciberseguridad. Algunos puntos a tener en cuenta a la hora de crear un plan de respuesta ante cualquier incidente de ciberseguridad:

- ¿Cómo pueden usted y su equipo contener los incidentes de ciberseguridad y los dispositivos afectados?
    
- ¿Qué procedimientos existen para ayudarle a usted y a su equipo a neutralizar los incidentes de ciberseguridad?
    
- ¿Qué datos o información pueden utilizarse para analizar este incidente?
    
- ¿Cómo puede mejorarse el proceso de recuperación de su organización para gestionar mejor futuros incidentes de ciberseguridad?
    

Escriba su respuesta en la plantilla de análisis de informes de incidentes, en la sección "responder".

Considere qué medidas deben tomarse para ayudar a la organización a recuperarse del incidente de ciberseguridad. Reflexione sobre toda la información que ha recopilado sobre el incidente en los pasos anteriores para considerar qué dispositivos, sistemas y procesos deben restaurarse y recuperarse.

Considere las siguientes preguntas:

- ¿Qué información necesita poder recuperar inmediatamente?
    
- ¿Qué procesos existen para ayudar a la organización a recuperarse del incidente?
    

Escribe tu respuesta en la parte de "recuperación" de la hoja de trabajo.

### **Consejo profesional: Guarde la plantilla de análisis de informes de incidentes**

Por último, asegúrese de guardar una copia de su plantilla de análisis de informes de incidentes en algún lugar accesible para que pueda acceder a ella a medida que avance en el curso y en el campo de la seguridad.


## 📝 **Resumen del incidente**

La empresa multimedia sufrió un ataque de denegación de servicio distribuido (DDoS) que afectó gravemente su red interna durante dos horas. El ataque consistió en una avalancha de paquetes ICMP que saturaron los recursos de red, provocando que los servicios quedaran inaccesibles. Se determinó que la causa fue un cortafuegos mal configurado que no filtraba este tipo de tráfico. El equipo de ciberseguridad respondió bloqueando paquetes ICMP entrantes, desactivando servicios no críticos y aplicando medidas de mitigación. El incidente afectó los servicios ofrecidos a clientes y puso en riesgo la reputación y la disponibilidad de los sistemas.

---

## 🔎 **Identificar**

- **Tipo de ataque**: DDoS (ataque distribuido de denegación de servicio)
    
- **Método usado**: Avalanche de paquetes ICMP (Ping Flood)
    
- **Origen del ataque**: Dirección IP externa no autenticada; posible IP spoofing
    
- **Sistemas afectados**: Red interna, servidores de servicios web, DNS y correo electrónico
    
- **Causa raíz**: Configuración incorrecta del cortafuegos que permitía tráfico ICMP sin restricciones
    
- **Impacto**: Inaccesibilidad a servicios internos y externos por 2 horas; pérdida de productividad; posibles daños a la confianza del cliente
    

---

## 🛡️ **Proteger**

- Configurar adecuadamente el cortafuegos para limitar y filtrar paquetes ICMP.
    
- Implementar reglas de tasa de paquetes para mitigar futuros intentos de DDoS.
    
- Activar verificación de IP de origen para detectar IPs falsificadas.
    
- Proveer formación a los administradores de red sobre configuración segura de cortafuegos.
    
- Revisar políticas de acceso a red y mantener software de red actualizado.
    
- Documentar protocolos de mantenimiento de red y respuestas ante amenazas.
    

---

## 📡 **Detectar**

- Instalar herramientas de monitoreo continuo como un SIEM para registrar y analizar eventos de red.
    
- Usar un sistema IDS/IPS para detectar tráfico ICMP sospechoso.
    
- Configurar alertas en tiempo real para patrones de tráfico anómalos.
    
- Auditar frecuentemente logs de red y firewall.
    
- Realizar pruebas de penetración para detectar debilidades antes de que sean explotadas.
    

---

## 🚨 **Responder**

- Activar plan de respuesta ante incidentes y coordinar con el equipo de TI.
    
- Contener el incidente bloqueando temporalmente el tráfico ICMP.
    
- Aislar sistemas críticos para evitar mayor propagación del impacto.
    
- Analizar los logs y patrones de tráfico para identificar el origen y características del ataque.
    
- Informar a las partes interesadas internas (administración, TI, marketing) sobre la situación.
    
- Documentar todo el proceso y extraer lecciones aprendidas.
    

---

## 🔧 **Recuperar**

- Restaurar los servicios críticos en orden de prioridad, asegurando su integridad.
    
- Verificar el estado de la red, servidores y servicios afectados.
    
- Evaluar los daños y validar la normalidad del tráfico tras la mitigación.
    
- Comunicar a los usuarios el restablecimiento completo de los servicios.
    
- Actualizar el plan de recuperación y reforzar controles preventivos.
    
- Realizar simulacros de recuperación para medir el tiempo de respuesta.
    

---

## 🧠 **Reflexión / Notas**

Este incidente demuestra la importancia de una configuración segura en los dispositivos de red y de la supervisión proactiva. Aplicar el CSF de NIST permite no solo responder, sino mejorar la ciberresiliencia a futuro. La prevención, formación y monitoreo son pilares clave.
