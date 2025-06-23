
En los primeros días de Internet, toda la comunicación por Internet se realizaba a través de cables físicos. No fue hasta mediados de la década de 1980 que las autoridades de los Estados Unidos designaron un espectro de frecuencias de ondas de radio que podían usarse sin licencia, por lo que hubo más oportunidades para que Internet se expandiera.

A finales de la década de 1990 y principios de la de 2000, se desarrollaron tecnologías para enviar y recibir datos por radio. Hoy en día, los usuarios acceden a Internet inalámbrico a través de computadoras portátiles, teléfonos inteligentes, tabletas y computadoras de escritorio. Los dispositivos inteligentes, como los termostatos, las cerraduras de las puertas y las cámaras de seguridad, también utilizan Internet inalámbrico para comunicarse entre sí y con los servicios de Internet.

![Wireless router with antenna connected to WEP, WPA, WPA2, and WPA3 protocols](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/xRV4czFOTUeQoV2vrMyMeg_d23346290329425da28d901333b11af1_KRMIlg0NE-hyueu8ieJBVc92c_gZAut6oOyRG0iOjP58SBeS6AojyB3piYq3ZOtOCf1kwrG62COp1ei3Uih_CcoNT2_QdtdaHyEchUsGTcmreFbywK_tUWZJGhMD3Tji9hxIUjH-yQAD8RSKpTbtJDHXD88IOpsqzlu8MCJotlno6JixxiW8pmiYFuzqHZ1bZhfT3cMFIZxI3sPnCh_BnizMW3y21VJuVZcX?expiry=1750809600000&hmac=lRfd8DY8tmJSz_wMIz8sNPHmSvylTY7wEH5XQdcHuP0)

## Introducción a los protocolos de comunicación inalámbrica

Hoy en día, muchas personas se refieren a Internet inalámbrico como Wi-Fi. **Wi-Fi** se refiere a un conjunto de estándares que definen la comunicación para las LAN inalámbricas. Wi-Fi es un término de marketing encargado por la Wireless Ethernet Compatibility Alliance (WECA). Desde entonces, WECA ha cambiado el nombre de su organización a Wi-Fi Alliance.

Los estándares y protocolos Wi-Fi se basan en la familia 802.11 de estándares de comunicación por Internet determinados por el Instituto de Ingenieros Eléctricos y Electrónicos (IEEE). Por lo tanto, como analista de seguridad, es posible que también vea que Wi-Fi se denomina IEEE 802.11.

Las comunicaciones Wi-Fi están protegidas por protocolos de red inalámbrica. Los protocolos de seguridad inalámbricos han evolucionado a lo largo de los años, ayudando a identificar y resolver vulnerabilidades con tecnologías inalámbricas más avanzadas.

En esta lectura, aprenderá sobre la evolución de los protocolos de seguridad inalámbricos de WEP a WPA, WPA2 y WPA3. También aprenderá cómo se utilizaba el Protocolo de aplicaciones inalámbricas para las comunicaciones por Internet móvil.

### **Privacidad equivalente por cable**

La privacidad equivalente por cable (WEP) es un protocolo de seguridad inalámbrico diseñado para proporcionar a los usuarios el mismo nivel de privacidad en las conexiones de red inalámbrica que en las conexiones de red por cable. WEP fue desarrollado en 1999 y es el más antiguo de los estándares de seguridad inalámbrica.

WEP está en gran medida fuera de uso hoy en día, pero los analistas de seguridad aún deben comprender WEP en caso de que lo encuentren. Por ejemplo, es posible que un enrutador de red haya utilizado WEP como protocolo de seguridad predeterminado y el administrador de red nunca lo haya cambiado. O bien, es posible que los dispositivos de una red sean demasiado antiguos para admitir los protocolos de seguridad Wi-Fi más recientes. Sin embargo, un actor malintencionado podría romper el cifrado WEP, por lo que ahora se considera un protocolo de seguridad de alto riesgo.

### **Acceso protegido por Wi-Fi**

Wi-Fi Protected Access (WPA) se desarrolló en 2003 para mejorar WEP, abordar los problemas de seguridad que presentaba y reemplazarlo. WPA siempre tuvo la intención de ser una medida de transición para que la compatibilidad con versiones anteriores pudiera establecerse con hardware más antiguo.

Los fallos de WEP estaban en el propio protocolo y en cómo se utilizaba el cifrado. WPA abordó esta debilidad mediante el uso de un protocolo llamado Protocolo de integridad de clave temporal (TKIP). El algoritmo de cifrado WPA utiliza claves secretas más grandes que los WEP, lo que dificulta la adivinación de la clave por ensayo y error.

WPA también incluye una verificación de integridad de mensajes que incluye una etiqueta de autenticación de mensajes con cada transmisión. Si un actor malintencionado intenta alterar la transmisión de alguna manera o reenviarla en otro momento, la verificación de integridad de mensajes de WPA identificará el ataque y rechazará la transmisión.

A pesar de las mejoras de seguridad de WPA, todavía tiene vulnerabilidades. Los actores malintencionados pueden utilizar un ataque de reinstalación de claves (o ataque KRACK) para descifrar las transmisiones mediante WPA. Los atacantes pueden insertarse en el proceso de protocolo de enlace de autenticación WPA e insertar una nueva clave de cifrado en lugar de la dinámica asignada por WPA. Si establecen la nueva clave en ceros, es como si la transmisión no estuviera encriptada en absoluto.

Debido a esta importante vulnerabilidad, WPA fue reemplazado por una versión actualizada del protocolo llamada WPA2.

### **WPA2 y WPA3**

#### **WPA2**

La segunda versión de Wi-Fi Protected Access, conocida como WPA2, se lanzó en 2004. WPA2 mejora WPA mediante el uso del Estándar de cifrado avanzado (AES). WPA2 también mejora el uso de TKIP por parte de WPA. WPA2 utiliza el protocolo de código de autenticación de mensajes (CCMP) de cadena de bloques de cifrado en modo contador, que proporciona encapsulación y garantiza la autenticación y la integridad de los mensajes. Debido a la fuerza de WPA2, se considera el estándar de seguridad para todas las transmisiones Wi-Fi en la actualidad. WPA2, al igual que su predecesor, es vulnerable a los ataques KRACK. Esto llevó al desarrollo de WPA3 en 2018.

#### **Personal**

El modo personal WPA2 es el más adecuado para redes domésticas por una variedad de razones. Es fácil de implementar, la configuración inicial lleva menos tiempo para la versión personal que para la empresarial. La frase de contraseña global para la versión personal de WPA2 debe aplicarse a cada computadora individual y punto de acceso en una red. Esto lo hace ideal para redes domésticas, pero inmanejable para organizaciones.

#### **Empresa**

El modo empresarial WPA2 funciona mejor para las aplicaciones empresariales. Proporciona la seguridad necesaria para las redes inalámbricas en entornos empresariales. La configuración inicial es más complicada que el modo personal WPA2, pero el modo empresarial ofrece un control individualizado y centralizado sobre el acceso Wi-Fi a una red empresarial. Esto significa que los administradores de red pueden conceder o eliminar el acceso de los usuarios a una red en cualquier momento. Los usuarios nunca tienen acceso a las claves de cifrado, lo que evita que los posibles atacantes recuperen las claves de red en equipos individuales.

#### **WPA3**

WPA3 es un protocolo Wi-Fi seguro y su uso está creciendo a medida que se lanzan más dispositivos compatibles con WPA3. Estas son las diferencias clave entre WPA2 y WPA3:

- WPA3 aborda la vulnerabilidad del protocolo de enlace de autenticación a los ataques KRACK, que está presente en WPA2.
    
- WPA3 utiliza la autenticación simultánea de iguales (SAE), un acuerdo de uso compartido de claves cifradas y autenticado por contraseña. Esto evita que los atacantes descarguen datos de las conexiones de red inalámbrica a sus sistemas para intentar decodificarlos.
    
- WPA3 ha aumentado el cifrado para hacer que las contraseñas sean más seguras mediante el uso de cifrado de 128 bits, con el modo WPA3-Enterprise que ofrece cifrado opcional de 192 bits.
    

## Conclusiones clave

Como analista de seguridad, conocer el historial de cómo se desarrollaron los protocolos de seguridad de Wi-Fi le ayuda a comprender mejor qué debe tener en cuenta a la hora de proteger las redes inalámbricas. Es importante que comprenda las vulnerabilidades de cada protocolo y lo importante que es que los dispositivos de su red utilicen las tecnologías de seguridad más actualizadas.

