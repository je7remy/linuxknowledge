
En esta lectura, explorarás más sobre la importancia de la ingestión de logs. Recordará que las herramientas de **administración de información y eventos de seguridad** **(SIEM**) recopilan y analizan los datos de registro para supervisar las actividades críticas de una organización. También ha aprendido sobre **el análisis** de registros, que es el proceso de examinar registros para identificar eventos de interés. Comprender cómo se introducen las fuentes de registro en las herramientas SIEM es importante porque ayuda a los analistas de seguridad a comprender los tipos de datos que se recopilan y puede ayudar a los analistas a identificar y priorizar los incidentes de seguridad.

## Visión general del proceso SIEM

Anteriormente se ha tratado el proceso SIEM. A modo de repaso, el proceso consta de tres pasos:

1. **Recopilar y agregar datos**: Las herramientas SIEM recopilan datos de eventos de varias fuentes de datos.
    
2. **Normalizar datos**: Los datos de eventos recopilados se normalizan. La normalización convierte los datos a un formato estándar para que se estructuren de forma coherente y sean más fáciles de leer y buscar. Aunque la normalización de datos es una característica común en muchas herramientas SIEM, es importante tener en cuenta que las herramientas SIEM varían en sus capacidades de normalización de datos.
    
3. **Analizar los datos**: Una vez recopilados y normalizados los datos, las herramientas SIEM los analizan y correlacionan para identificar patrones comunes que indiquen actividad inusual.
    

Esta lectura se centra en el primer paso de este proceso, la recopilación y agregación de datos.

## Ingesta de registros

![Una herramienta SIEM recopila datos de diversas fuentes.](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/1ZNypyZJSb6t2dDK8jAs5g_f0331b912c2d4f949734e4325c1928f1_0smyScQN7exeZjonfdPMzR89GB4iKifMP0ou7I4vtfCsmAC8R-idy_3aVUbkopt7P918eo8EJ6CpRGT4ta25LYlfh0Rkr6L8bt5OGYuixWDR5Qrsq1oPf9F8Hxq9SoXoTGb-mRQ7mukPY21rLvQXtNa3BkSnQ9TgnPqz5neROFGNrg0GkYvUr_64MLKj?expiry=1761350400000&hmac=9xk7eOBa0U2OM8hDw5hvOD8Ucn4P-vdEE-riYe1NYFM)

Los datos son necesarios para que las herramientas SIEM funcionen eficazmente. Las herramientas SIEM primero deben recopilar datos mediante la ingesta de registros. La ingesta de registros es el proceso de recopilación e importación de datos de fuentes de registros a una herramienta SIEM. Los datos proceden de cualquier fuente que genere datos de registro, como un servidor.

En la ingestión de registros, el SIEM crea una copia de los datos de eventos que recibe y la conserva en su propio almacenamiento. Esta copia permite al SIEM analizar y procesar los datos sin modificar directamente los registros originales. La recopilación de datos de eventos proporciona una plataforma centralizada para que los analistas de seguridad analicen los datos y respondan a los incidentes. Estos datos de eventos incluyen intentos de autenticación, actividad de red, etc.

### Transmisores de registros

Hay muchas formas de que las herramientas SIEM ingieran datos de registro. Por ejemplo, se pueden cargar datos manualmente o utilizar software que ayude a recopilar datos para la ingesta de registros. La carga manual de datos puede resultar ineficaz y llevar mucho tiempo, ya que las redes pueden contener miles de sistemas y dispositivos. Por lo tanto, es más fácil utilizar software que ayude a recopilar datos.

Una forma común de que las organizaciones recopilen datos de registro es utilizar reenviadores de registro. Estos programas automatizan el proceso de recogida y envío de datos de registro. Algunos sistemas operativos tienen reenviadores de registro nativos. Si utiliza un sistema operativo que no dispone de un reenviador de registros nativo, deberá instalar un software de reenvío de registros de terceros en un dispositivo. Después de instalarlo, configure el software para especificar qué registros reenviar y dónde enviarlos. Por ejemplo, puede configurar los registros para que se envíen a una herramienta SIEM. La herramienta SIEM procesaría y normalizaría los datos. Esto permite que los datos se puedan buscar, explorar, correlacionar y analizar fácilmente.

**Nota**: Muchas herramientas SIEM utilizan sus propios reenviadores de registros. Las herramientas SIEM también pueden integrarse con reenviadores de registros de código abierto. La elección del reenviador de registros adecuado depende de muchos factores, como los requisitos específicos de su sistema u organización, la compatibilidad con la infraestructura existente, etc.

## Puntos clave

Las herramientas SIEM necesitan datos para ser eficaces. COMO analista de seguridad, utilizará herramientas SIEM para acceder a eventos y analizar registros cuando esté investigando un incidente. En su carrera de seguridad, puede que incluso se le encargue configurar un SIEM para recopilar datos de registro. Es importante que entienda cómo se introducen los datos en las herramientas SIEM, ya que esto le permitirá comprender de dónde proceden las fuentes de registro, lo que puede ayudarle a identificar el origen de un incidente de seguridad.

## Recursos

Aquí tienes algunos recursos si quieres saber más sobre el proceso de ingestión de logs para Splunk y Google SecOps (Chronicle) :

- [Guía sobre la ingestión de datos en Splunk](https://docs.splunk.com/Documentation/SplunkCloud/9.0.2303/Data/Howdoyouwanttoadddata)
    
- [Guía sobre la ingestión de datos en Google Security Operations](https://cloud.google.com/chronicle/docs/data-ingestion-flow)
    

**Pro tip:** Más adelante en este módulo, utilizará Splunk Cloud para cargar datos, realizar búsquedas básicas en los datos y responder a una serie de preguntas. Siga las instrucciones en la [Guía de seguimiento para Splunk registro](https://www.coursera.org/learn/detection-and-response/supplement/Wg478/follow-along-guide-for-splunk-sign-up) para completar lo siguiente antes de empezar a usar Splunk. Para empezar a utilizar Splunk rápidamente, regístrese ahora. El correo electrónico de verificación puede tardar un poco en llegar.